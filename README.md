# nasa-chalenge
Developing a autonomous free-flyer to inspect a spacecraft for damage from Micro-Meteoroid and Orbital Debris 

Here it's presented the dasboard developed with node red, developed on NASA's International Space Apps Challenge.
Dashboard based on the:

https://openmct-demo.herokuapp.com/#/browse/demo:root/demo:2/demo:11?view=clock&tc.mode=local&tc.timeSystem=utc&tc.startDelta=900000&tc.endDelta=0

Where we display to the operators in a spacecraft key information about the status of the spacecraft.

the algoritms for autonomous fly and routes executionsis based on the bee fly aroud a target, it would be possible to make a autonomous and colaborative missions realised by the autonomous free-flyers, comunicating and make possible fast and efective decisions and procedures.

Anyone can copy and paste the code  below on a node red instance in import>clipboard

[
    {
        "id": "40707f16.bf526",
        "type": "debug",
        "z": "2ee3dee5.1d9a62",
        "name": "",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "false",
        "x": 570,
        "y": 240,
        "wires": []
    },
    {
        "id": "ac11f1e5.4af59",
        "type": "ui_template",
        "z": "2ee3dee5.1d9a62",
        "group": "afabbb9.e618a48",
        "name": "",
        "order": 0,
        "width": 0,
        "height": 0,
        "format": "<script>\nvar value = \"1\";\n// or overwrite value in your callback function ...\nthis.scope.action = function() { return value; }\n\nfunction updateF() {\n  var source = '/photo1.JPEG',\n  timestamp = (new Date()).getTime(),\n  newUrl = source + '?_=' + timestamp;\n  document.getElementById(\"photo\").src = newUrl;\n}\n</script>\n\n<md-button ng-click=\"send({payload:action()})\" onclick=\"setTimeout(updateF, 2500);\" style=\"padding:40px; margin-bottom: 40px;\" >\n <ui-icon icon=\"camera\"></ui-icon>\n Take a photo<br>\n</md-button>\n\n<div style=\"margin-bottom:40px;\">\n <img src=\"/photo1.JPEG\" id=\"photo\" width=\"100%\" height=\"100%\">\n</div>",
        "storeOutMessages": true,
        "fwdInMessages": true,
        "templateScope": "local",
        "x": 80,
        "y": 240,
        "wires": [
            [
                "2138b99d.639a36"
            ]
        ]
    },
    {
        "id": "2138b99d.639a36",
        "type": "template",
        "z": "2ee3dee5.1d9a62",
        "name": "Take photo python node",
        "field": "payload",
        "fieldType": "msg",
        "format": "handlebars",
        "syntax": "mustache",
        "template": "This is the payload: {{payload}} !",
        "output": "str",
        "x": 310,
        "y": 240,
        "wires": [
            [
                "40707f16.bf526"
            ]
        ]
    },
    {
        "id": "a21c72fe.0c02a",
        "type": "ui_chart",
        "z": "2ee3dee5.1d9a62",
        "name": "",
        "group": "afabbb9.e618a48",
        "order": 0,
        "width": "0",
        "height": "0",
        "label": "Batery State of Charge",
        "chartType": "bar",
        "legend": "false",
        "xformat": "HH:mm:ss",
        "interpolate": "linear",
        "nodata": "",
        "dot": false,
        "ymin": "",
        "ymax": "",
        "removeOlder": 1,
        "removeOlderPoints": "",
        "removeOlderUnit": "3600",
        "cutout": 0,
        "useOneColor": true,
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "useOldStyle": false,
        "x": 460,
        "y": 460,
        "wires": [
            [],
            []
        ]
    },
    {
        "id": "cbd2f72c.33fb58",
        "type": "inject",
        "z": "2ee3dee5.1d9a62",
        "name": "",
        "topic": "",
        "payload": "",
        "payloadType": "date",
        "repeat": "5",
        "crontab": "",
        "once": false,
        "onceDelay": 0.1,
        "x": 110,
        "y": 680,
        "wires": [
            [
                "6ccacdb1.b82b54"
            ]
        ]
    },
    {
        "id": "93afa2b1.51c7c",
        "type": "ui_chart",
        "z": "2ee3dee5.1d9a62",
        "name": "",
        "group": "afabbb9.e618a48",
        "order": 0,
        "width": 0,
        "height": 0,
        "label": "Wheel Motors",
        "chartType": "line",
        "legend": "false",
        "xformat": "HH:mm:ss",
        "interpolate": "linear",
        "nodata": "",
        "dot": false,
        "ymin": "",
        "ymax": "",
        "removeOlder": 1,
        "removeOlderPoints": "",
        "removeOlderUnit": "3600",
        "cutout": 0,
        "useOneColor": false,
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "useOldStyle": false,
        "x": 480,
        "y": 620,
        "wires": [
            [],
            []
        ]
    },
    {
        "id": "363c519b.d99f9e",
        "type": "ui_chart",
        "z": "2ee3dee5.1d9a62",
        "name": "",
        "group": "afabbb9.e618a48",
        "order": 0,
        "width": 0,
        "height": 0,
        "label": "Link Sent",
        "chartType": "line",
        "legend": "false",
        "xformat": "HH:mm:ss",
        "interpolate": "linear",
        "nodata": "",
        "dot": false,
        "ymin": "",
        "ymax": "",
        "removeOlder": 1,
        "removeOlderPoints": "",
        "removeOlderUnit": "3600",
        "cutout": 0,
        "useOneColor": false,
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "useOldStyle": false,
        "x": 460,
        "y": 720,
        "wires": [
            [],
            []
        ]
    },
    {
        "id": "27980caf.cb2124",
        "type": "ui_chart",
        "z": "2ee3dee5.1d9a62",
        "name": "",
        "group": "afabbb9.e618a48",
        "order": 0,
        "width": 0,
        "height": 0,
        "label": "Link Received",
        "chartType": "line",
        "legend": "false",
        "xformat": "HH:mm:ss",
        "interpolate": "linear",
        "nodata": "",
        "dot": false,
        "ymin": "",
        "ymax": "",
        "removeOlder": 1,
        "removeOlderPoints": "",
        "removeOlderUnit": "3600",
        "cutout": 0,
        "useOneColor": false,
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "useOldStyle": false,
        "x": 460,
        "y": 800,
        "wires": [
            [],
            []
        ]
    },
    {
        "id": "b17243c2.0e61f",
        "type": "ui_chart",
        "z": "2ee3dee5.1d9a62",
        "name": "",
        "group": "afabbb9.e618a48",
        "order": 0,
        "width": 0,
        "height": 0,
        "label": "Batery current Status",
        "chartType": "line",
        "legend": "false",
        "xformat": "HH:mm:ss",
        "interpolate": "linear",
        "nodata": "",
        "dot": false,
        "ymin": "",
        "ymax": "",
        "removeOlder": 1,
        "removeOlderPoints": "",
        "removeOlderUnit": "3600",
        "cutout": 0,
        "useOneColor": false,
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "useOldStyle": false,
        "x": 460,
        "y": 860,
        "wires": [
            [],
            []
        ]
    },
    {
        "id": "a5a06e0.ea39c9",
        "type": "ui_chart",
        "z": "2ee3dee5.1d9a62",
        "name": "",
        "group": "afabbb9.e618a48",
        "order": 0,
        "width": 0,
        "height": 0,
        "label": "Baterry Voltage",
        "chartType": "line",
        "legend": "false",
        "xformat": "HH:mm:ss",
        "interpolate": "linear",
        "nodata": "",
        "dot": false,
        "ymin": "",
        "ymax": "",
        "removeOlder": 1,
        "removeOlderPoints": "",
        "removeOlderUnit": "3600",
        "cutout": 0,
        "useOneColor": false,
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "useOldStyle": false,
        "x": 440,
        "y": 920,
        "wires": [
            [],
            []
        ]
    },
    {
        "id": "c1756beb.0f5d08",
        "type": "inject",
        "z": "2ee3dee5.1d9a62",
        "name": "Reset",
        "topic": "",
        "payload": "0",
        "payloadType": "num",
        "repeat": "",
        "crontab": "",
        "once": true,
        "onceDelay": "5",
        "x": 130,
        "y": 1040,
        "wires": [
            [
                "a21c72fe.0c02a",
                "93afa2b1.51c7c",
                "363c519b.d99f9e"
            ]
        ]
    },
    {
        "id": "6ccacdb1.b82b54",
        "type": "function",
        "z": "2ee3dee5.1d9a62",
        "name": "",
        "func": "var msg1 = {};\nvar msg2 = {};\nvar msg3 = {};\nvar msg4 = {};\nvar msg5 = {};\nvar msg6 = {};\nvar msg7 = {};\nvar msg8 = {};\nvar msg9 = {};\nvar msg10 = {};\n\nmsg1.payload = Math.round(Math.random()*100);\nmsg1.topic = 'Line1';\n\nmsg2.payload = Math.round(Math.random()*115);\nmsg2.topic = 'Line2';\n\nmsg3.payload = Math.round(Math.random()*100);\nmsg3.topic = 'Line3';\n\nmsg4.payload = Math.round(Math.random()*115);\nmsg4.topic = 'Line4';\n\nmsg5.payload = Math.round(Math.random()*100);\nmsg5.topic = 'Line5';\n\nmsg6.payload = Math.round(Math.random()*115);\nmsg6.topic = 'Line6';\n\nmsg7.payload = Math.round(Math.random()*100);\nmsg7.topic = 'Line7';\n\nmsg8.payload = Math.round(Math.random()*115);\nmsg8.topic = 'Line8';\n\nmsg9.payload = Math.round(Math.random()*100);\nmsg9.topic = 'Line9';\n\nmsg10.payload = Math.round(Math.random()*115);\nmsg10.topic = 'Line10';\n\n\nreturn [msg1,msg2,msg3,msg4,msg5,msg6,msg7,msg8,msg9,msg10];",
        "outputs": 10,
        "noerr": 0,
        "x": 170,
        "y": 460,
        "wires": [
            [
                "a21c72fe.0c02a",
                "e7860582.739298",
                "93afa2b1.51c7c",
                "363c519b.d99f9e"
            ],
            [
                "a21c72fe.0c02a",
                "e7860582.739298",
                "93afa2b1.51c7c",
                "363c519b.d99f9e"
            ],
            [
                "a21c72fe.0c02a",
                "93afa2b1.51c7c",
                "363c519b.d99f9e"
            ],
            [
                "a21c72fe.0c02a",
                "93afa2b1.51c7c",
                "363c519b.d99f9e"
            ],
            [
                "a21c72fe.0c02a",
                "93afa2b1.51c7c",
                "363c519b.d99f9e"
            ],
            [
                "a21c72fe.0c02a",
                "93afa2b1.51c7c",
                "363c519b.d99f9e"
            ],
            [
                "a21c72fe.0c02a",
                "93afa2b1.51c7c",
                "363c519b.d99f9e"
            ],
            [
                "a21c72fe.0c02a",
                "93afa2b1.51c7c",
                "363c519b.d99f9e"
            ],
            [
                "a21c72fe.0c02a",
                "93afa2b1.51c7c",
                "363c519b.d99f9e"
            ],
            [
                "a21c72fe.0c02a",
                "93afa2b1.51c7c",
                "363c519b.d99f9e"
            ]
        ]
    },
    {
        "id": "26a062a4.3769fe",
        "type": "function",
        "z": "2ee3dee5.1d9a62",
        "name": "",
        "func": "msg.payload = Math.round(Math.random()*115);\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 650,
        "y": 860,
        "wires": [
            []
        ]
    },
    {
        "id": "bf6210bf.12e6d",
        "type": "function",
        "z": "2ee3dee5.1d9a62",
        "name": "",
        "func": "msg.payload = Math.round(Math.random()*115);\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 650,
        "y": 940,
        "wires": [
            []
        ]
    },
    {
        "id": "4bdd0259.8f5f3c",
        "type": "function",
        "z": "2ee3dee5.1d9a62",
        "name": "",
        "func": "msg.payload = Math.round(Math.random()*115);\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 650,
        "y": 1000,
        "wires": [
            []
        ]
    },
    {
        "id": "e7860582.739298",
        "type": "debug",
        "z": "2ee3dee5.1d9a62",
        "name": "",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "false",
        "x": 430,
        "y": 360,
        "wires": []
    },
    {
        "id": "afabbb9.e618a48",
        "type": "ui_group",
        "z": "",
        "name": "Status",
        "tab": "344e1d4a.d7d492",
        "disp": true,
        "width": "12",
        "collapse": false
    },
    {
        "id": "344e1d4a.d7d492",
        "type": "ui_tab",
        "z": "",
        "name": "Sensors Monitor",
        "icon": "dashboard",
        "order": 2
    }
]
