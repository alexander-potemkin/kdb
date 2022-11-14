# OpenRPA & OpenFlow queues

# HowTo use OpenFlow queues

## Abstract

OpenFlow - is a midddleware and web GUI that, among other things, provide an interface to the RabbitMQ queue system under the hood.

In case if queue processing is required (e.g. to do a web scraping without getting blocked) an OpenFlow feature 'work item queues' shall be used.

On a high level, the idea is that you create and configure the queue on OpenFlow and then you use it through the Node-Red special nodes, that push things to be processed to the queue and pick them up from the queue, with respect to the queue settings.

## How To

Go to your OpenFlow - the URL is provided for the cloud version of the OpenFlow: [https://app.openiap.io/#/WorkitemQueues](https://app.openiap.io/#/WorkitemQueues)

Create your Node-Red workflow:

1.  Create new flow
2.  Drag & drop flows.json to the screen


**flows.json**

```
[
    {
        "id": "bf28ac2e8d1a039b",
        "type": "tab",
        "label": "Flow 2",
        "disabled": false,
        "info": "",
        "env": []
    },
    {
        "id": "0b70677bdf79a2f6",
        "type": "amqp consumer",
        "z": "bf28ac2e8d1a039b",
        "queue": "ExampleConsumer",
        "name": "",
        "config": "",
        "x": 120,
        "y": 420,
        "wires": [
            [
                "12934d253ab2cd38",
                "dc2956d45bdbe3da"
            ]
        ]
    },
    {
        "id": "12934d253ab2cd38",
        "type": "workitem popworkitem",
        "z": "bf28ac2e8d1a039b",
        "name": "",
        "download": true,
        "config": "602e936b1a66635f",
        "workitem": "payload",
        "workitemtype": "msg",
        "files": "files",
        "filestype": "msg",
        "x": 330,
        "y": 380,
        "wires": [
            [
                "ff0ebbd9f0333445"
            ],
            []
        ]
    },
    {
        "id": "ff0ebbd9f0333445",
        "type": "workitem updateworkitem",
        "z": "bf28ac2e8d1a039b",
        "name": "",
        "workitem": "payload",
        "workitemtype": "msg",
        "ignoremaxretries": "ignoremaxretries",
        "ignoremaxretriestype": "msg",
        "files": "newfiles",
        "filestype": "msg",
        "error": "error",
        "errortype": "msg",
        "state": "processing",
        "success_wiq": "ok",
        "success_wiqtype": "msg",
        "failed_wiq": "ok",
        "failed_wiqtype": "msg",
        "x": 560,
        "y": 380,
        "wires": [
            [
                "932e4a392dc00d8f"
            ]
        ]
    },
    {
        "id": "4afad22c0deb0332",
        "type": "inject",
        "z": "bf28ac2e8d1a039b",
        "name": "add one",
        "props": [
            {
                "p": "payload"
            },
            {
                "p": "topic",
                "vt": "str"
            },
            {
                "p": "files",
                "v": "[]",
                "vt": "json"
            }
        ],
        "repeat": "",
        "crontab": "",
        "once": false,
        "onceDelay": 0.1,
        "topic": "Find me",
        "payload": "",
        "payloadType": "date",
        "x": 100,
        "y": 160,
        "wires": [
            [
                "1917acebabd1f212"
            ]
        ]
    },
    {
        "id": "6648745214f82e86",
        "type": "debug",
        "z": "bf28ac2e8d1a039b",
        "name": "",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "",
        "statusType": "auto",
        "x": 790,
        "y": 160,
        "wires": []
    },
    {
        "id": "8f35e0047b764ada",
        "type": "workitem addworkitem",
        "z": "bf28ac2e8d1a039b",
        "name": "",
        "config": "602e936b1a66635f",
        "payload": "payload",
        "payloadtype": "msg",
        "topic": "topic",
        "topictype": "msg",
        "nextrun": "nextrun",
        "nextruntype": "msg",
        "priority": "3",
        "prioritytype": "msg",
        "files": "files",
        "filestype": "msg",
        "success_wiq": "ok",
        "success_wiqtype": "msg",
        "failed_wiq": "ok",
        "failed_wiqtype": "msg",
        "x": 610,
        "y": 160,
        "wires": [
            [
                "6648745214f82e86"
            ]
        ]
    },
    {
        "id": "1917acebabd1f212",
        "type": "http request",
        "z": "bf28ac2e8d1a039b",
        "name": "",
        "method": "GET",
        "ret": "bin",
        "paytoqs": "ignore",
        "url": "https://as1.ftcdn.net/v2/jpg/01/25/63/94/1000_F_125639489_JWy8LEJzjIDMWes5UL0XLWUZQQPBidxs.jpg",
        "tls": "",
        "persist": false,
        "proxy": "",
        "authType": "",
        "senderr": false,
        "x": 270,
        "y": 160,
        "wires": [
            [
                "40e0da21f054c529"
            ]
        ]
    },
    {
        "id": "40e0da21f054c529",
        "type": "function",
        "z": "bf28ac2e8d1a039b",
        "name": "",
        "func": "msg.files = [];\nmsg.files.push( {\n    file: msg.payload,\n    filename: \"kitten.jpg\"\n})\nmsg.payload = {\"name\": \"hi mom\"}\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 440,
        "y": 160,
        "wires": [
            [
                "8f35e0047b764ada"
            ]
        ]
    },
    {
        "id": "dc2956d45bdbe3da",
        "type": "amqp acknowledgment",
        "z": "bf28ac2e8d1a039b",
        "name": "",
        "x": 330,
        "y": 500,
        "wires": [
            []
        ]
    },
    {
        "id": "677ba3e1a244ff44",
        "type": "catch",
        "z": "bf28ac2e8d1a039b",
        "d": true,
        "name": "",
        "scope": null,
        "uncaught": false,
        "x": 720,
        "y": 260,
        "wires": [
            [
                "46c3a83a0f9d092f",
                "d41561e1802fee9a"
            ]
        ]
    },
    {
        "id": "46c3a83a0f9d092f",
        "type": "workitem updateworkitem",
        "z": "bf28ac2e8d1a039b",
        "name": "",
        "workitem": "payload",
        "workitemtype": "msg",
        "ignoremaxretries": "ignoremaxretries",
        "ignoremaxretriestype": "msg",
        "files": "newfiles",
        "filestype": "msg",
        "error": "error",
        "errortype": "msg",
        "state": "successful",
        "success_wiq": "go",
        "success_wiqtype": "msg",
        "failed_wiq": "go",
        "failed_wiqtype": "msg",
        "x": 920,
        "y": 280,
        "wires": [
            []
        ]
    },
    {
        "id": "932e4a392dc00d8f",
        "type": "debug",
        "z": "bf28ac2e8d1a039b",
        "name": "",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "",
        "statusType": "auto",
        "x": 770,
        "y": 380,
        "wires": []
    },
    {
        "id": "d41561e1802fee9a",
        "type": "debug",
        "z": "bf28ac2e8d1a039b",
        "name": "ERROR",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "error",
        "targetType": "msg",
        "statusVal": "",
        "statusType": "auto",
        "x": 900,
        "y": 240,
        "wires": []
    },
    {
        "id": "602e936b1a66635f",
        "type": "iworkitemqueue-config",
        "wiq": "ExampleQueue",
        "wiqid": "",
        "name": ""
    }
]
```

1.  Verify your 'Add Workitem' node has config 'ExampleQueue' -> that's a name of the queue at OpenFlow side (Edit Add Workitem node -> Properties -> Config -> ExampleQueue)
2.  On 'ampq consumer' make sure the queue name is 'ExampleConsumer' -> that's a name of the RabbitMQ queue under the hood (Edit amqp consumer node -> Properties -> Queue name -> ExampleConsumer)
3.  Click 'Deploy'
4.  Go the queue creation at OpenFlow

Create your queue: Work item queues -> ExampleQueue)

1.  Fill in 'Name' - ideally with a name without spaces, you will need it later at the Node-Red node configuration
2.  Choose project, workflow & robot (fetches from the one created at OpenRPA)
3.  choose 'amqpqueue' (comes from Node-Red nodes configuration)

Go back to Node-Red and verify that all of the nodes configuration is in order

Start your flow and go immediately to [https://app.openiap.io/#/Workitems](https://app.openiap.io/#/Workitems) - you shall find 'Find me' item with status 'Processing' which shall change to 'successful' after a few seconds, which means, that the item has been pushed to the queue by the first flow, then picked up by a second flow and a status has been changed to 'successful'.

Feel free to modify the logic as you see fit!

More information could be found at [https://github.com/open-rpa/openrpa/wiki/Workitems](https://github.com/open-rpa/openrpa/wiki/Workitems)