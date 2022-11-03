# CloudSigma API

Python library: [https://github.com/cloudsigma/pycloudsigma:](https://github.com/cloudsigma/pycloudsigma:)

 `vi ~/.cloudsigma.conf` to:

```
api_endpoint = <https://zrh.cloudsigma.com/api/2.0/>
ws_endpoint = wss://direct.zrh.cloudsigma.com/websocket
username = user@domain.com
password = secret
```

```bash
sudo apt -y install python3-pip
pip install cloudsigma
wget https://raw.githubusercontent.com/cloudsigma/pycloudsigma/master/samples/snapshot.py
vi ~/.cloudsigma.conf
python3 ~/scripts/snapshot.py
```

# Firewall API example


 ```
# First you will need you user and password in base64:  
echo -n '<user>:<password>' | base 64  
  
# Then you can make API calls, for example listing locatiions and formating with jq:  
  
curl -H "Authorization: Basic <here goes your base 64 access> -H "Content-Type: application/json" [https://zrh.cloudsigma.com/api/2.0/locations/?limit=0](https://zrh.cloudsigma.com/api/2.0/locations/?limit=0 "https://zrh.cloudsigma.com/api/2.0/locations/?limit=0") | jq  
  
# With this you can list your virtual routers and get the uuid for the next step:  
curl -H "Authorization: Basic ########" -H "Content-Type: application/json" [https://zrh.cloudsigma.com/api/2.0/virtualrouters/?limit=0](https://zrh.cloudsigma.com/api/2.0/virtualrouters/?limit=0 "https://zrh.cloudsigma.com/api/2.0/virtualrouters/?limit=0") | jq  
  
# An then enable firewall with a POST:  
curl -X POST -H "Authorization: Basic ########" [https://zrh.cloudsigma.com/api/2.0/virtualrouters/<uuid_of_the_router](https://zrh.cloudsigma.com/api/2.0/virtualrouters/%3Cuuid_of_the_router "https://zrh.cloudsigma.com/api/2.0/virtualrouters/<uuid_of_the_router")>/action/?do=enable_firewall
```

