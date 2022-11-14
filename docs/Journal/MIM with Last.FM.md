# Reverse engineering a HTTP based app or man-in-the-middle HTTP level proxy

Most of the web-applications know how to work via proxy server. Classical man-in-the-middle (MIM) schema is much easier when there is only one channel to work against. It is even better, when you don’t need to hook into the operating system sockets or traffic sniff.

Considering you have a proxy server you are connecting through (or you are ready to setup one, something like 3proxy should works just fine), the whole application behaviour is already man-in-the-middle: application sends a request to the proxy server on the port specified at the settings, GET/POST-ing against the resource required and then it is a proxy server task to fetch the response (usually – the page) and return it back to the application.

The task, then, is to put the program, acting like a proxy server, logging and saving all of the traffic – something you can name a HTTP level sniffer. That is how [HTTP-MIM-proxy.pl](https://gist.github.com/10bees/45ee1a29a6a06d775bf6), a multi-threaded Perl script, comes into life. It’s solely task is to bind to the local machine port and forward all of the requests to the actual proxy server, forwarding the proxy server replies back. Since HTTP traffic is a plain-text, the script is capable to “decipher” all of the requests it is forwarding and save they content.

Here is the way it’s output looks like for a simple Google search page request:  

```
1: Server bind on port 2101 done.
2: -6820 serving request from port 58890.
3: -6820 starts catching 'storage/_-6820_1300361050.com' (source: 'http://google.com/').
4: -6820  301 [Moved Permanently]
5: -1584 serving request from port 58892.
6: -1584 starts catching 'storage/_-1584_1300361050.com' (source: 'http://www.google.com/').
7: -1584  200 [OK]
8: +4760: killed -6820 idle children.
9: -6416 serving request from port 58894.
10: -1584 starts catching 'storage/tia_png_-1584_1300361050.png' (source: 'http://www.google.com/textinputassistant/tia.png').
11: -1584 < GET 'http://www.google.com/textinputassistant/tia.png'
12: -6416 starts catching 'storage/nav_logo37_png_-6416_1300361050.png' (source: 'http://www.google.com/images/srpr/nav_logo37.png').
13: -6416  200 [OK]
14: -1584 starts catching 'storage/gen_204_atyp_i_ghp_fbg_-1584_1300361050.com' (source: 'http://www.google.com/gen_204?atyp=i&ghp=fbg').
15: -1584  200 [OK]
16: -1584 > 204 [No Content]
17: -1584 starts catching 'storage/logo1w_png_-1584_1300361050.png' (source: 'http://www.google.com/intl/en_com/images/srpr/logo1w.png').
18: -1584  200 [OK]
19: -1584 starts catching 'storage/BizPqKM7TCU_js_-1584_1300361051.js' (source: 'http://www.google.com/extern_js/f/CgJydSswRTgALCswWjgALCswDjgALCswFzgALCswPDgALCswUTgALCswCjgAQB0sKzAWOAAsKzAZOAAsKzAlOM-IASwrMDU4ACwrMEA4ACwrMEE4ACwrME04ACwrME44ACwrMFQ4ACwrMGk4ACwrMBg4ACwrMCY4ACyAAjaQAjQ/BizPqKM7TCU.js').
20: -1584 < GET 'http://www.google.com/extern_js/f/CgJydSswRTgALCswWjgALCswDjgALCswFzgALCswPDgALCswUTgALCswCjgAQB0sKzAWOAAsKzAZOAAsKzAlOM-IASwrMDU4ACwrMEA4ACwrMEE4ACwrME04ACwrME44ACwrMFQ4ACwrMGk4ACwrMBg4ACwrMCY4ACyAAjaQAjQ/BizPqKM7TCU.js'
21: -6416 starts catching 'storage/favicon_ico_-6416_1300361051.ico' (source: 'http://www.google.com/favicon.ico').
22: -6416  200 [OK]
23: -6416 > 200 [OK]
24: -1584 starts catching 'storage/generate_204_-1584_1300361051.com' (source: 'http://clients1.google.com/generate_204').
25: -1584 < GET 'http://clients1.google.com/generate_204'
26: -6416 starts catching 'storage/csi_v_3_s_webhp_action__e_17259,18168,28501,28561,29014,29095,29266,229389_ei_Wu-BTbS9Jcu4hQeBpsW1Cw_expi_17259,18168,28501,28561,29014,29095,29266,22_-6416_1300361051.641' (source: 'http://www.google.com/csi?v=3&s=webhp&action=&e=17259,18168,28501,28561,29014,29095,29266,229389&ei=Wu-BTbS9Jcu4hQeBpsW1Cw&expi=17259,18168,28501,28561,29014,29095,29266,229389&imc=1&imn=1&imp=1&rt=xjsls.31,prt.47,ol.500,iml.141,xjses.609,xjsee.625,xjs.641').
27: -6416  204 [No Content]
28: -6416 > 204 [No Content]
```

A few words on what does it mean:

-   #1: MIM proxy server dispatching thread binded itself and is listening at the local port 2101 (meaning the browser proxy server to be setup as  127.0.0.1:2101) and is ready to serve the requests;
-   #2: I requested ‘google.com’ page to be opened from my browser and  it sends the request to the proxy server;
-   #3-4: MIM have got the request, prepared itself to dump the proxy reply (#3); forwarded, received and respond back to the client (#4) the ‘official’ answer – the page is available at another address;
-   #5: new URL request send by my browser;
-   #6-7: the new request is much more successful – proxy server returns and MIM proxy saves the desired content to the browser;
-   #8: MIM proxy server’s dispatching thread found idle baby and freed the resources, by killing the thread;
-   #9-11: browser have found some content on the HTML received (at the line #7) to be requested and goes for it;
-   #11-28: browser keeps two internal threads, operating on the local ports 58894 (served by 6416 MIM thread) and 58892 (served by a 6820 MIM thread), fetching all of the objects from the web page.
-   and so on.

All of the web application activities are clear to see and all of the files (noted with ‘starts catching …’) transferred from the web server are available at the ‘storage’ directory.

## Last.FM  

Last.FM is the case of a little bit more complicated, but still a web application, communicating with the server by using the XML-over-HTTP protocol. Passing the application traffic through the MIM gives an  idea on how it works exactly.

Skipping an authorization steps, tracks playlist is the very first thing Last.FM client is requesting:  
-3820 < GET 'http://ws.audioscrobbler.com/radio/xspf.php?sk=6c798ad66c6ef93089b17c45a1d12200&discovery=0&desktop=1.5.4.27091&api_key=9d1bbaef3b443eb97973d44181d04e4b  
  
  

xspf.php is the script, returning an XML with the next five tracks to be played by the client, and here is the first track location request:  
-6420 < GET 'http://play.last.fm/user/d4519167a7e34e81759df59e212bd692.mp3'  
  
  
No, we are not done yet – follow the white rabbit into a rabbit hole:  
  
-6420 > 302 [Moved Temporarily]  
  

Yes, that was not an actual file location, but here it goes next:  
-4512 < GET 'http://s18.last.fm/user/10493405/d4519167a7e34e81759df59e212bd692/339/0065831427/48d1c2cbc4674c99fc5b039498db67e6/1300362820/65/114325424/9d1bbaef3b443eb97973d44181d04e4b/1/0/128.mp3'  
  

xspf.php’s playlist gives only the links, which later on requires to be “resolved” by the the client, to let it fetch from the  the actual (load-balanced) server (that checks client’s session and, probably, some other stuff).

Looking into the files saved by the proxy at this stage shows that an MP3′s IDv3 information is at the xspf.php XML reply, meaning there is map to be constructed: HTTP fake URL, file IDv3 information, HTTP real URL and a saved file filesystem location.

The protocol might be changed already (the original Last.FM investigation was happening a few years ago), but this should give the clue.