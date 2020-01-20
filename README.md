# phillipshue-
Linn, Ligia, Marius, Noah und Tara 

<p align="center"><img src= "logo.jpg" width="100" alt="Tara Logo"></a></p>


<h1 align="center">Dokumentation Tara Monheim</h1>

## Details

Technisches Grundlagenprojekt bei Martin Schneider.

**Erstes Projekt**: Verständnis und glitchen eines SVG Files.  
Mitglied der "Spaceinvader" Gruppe.  

**Zweites Projekt**: Verbinden des Phillip Hue mit dem Rasperry Pi  
sowie Steuerung der Helligkeit und Farbe.  
Mitglied der "Lampen" Gruppe. 

```json 
[{"id":"30ea3041.735c1","type":"tab","label":"Quote Example","disabled":false,"info":""},{"id":"b874d525.23b288","type":"tab","label":"Color Example","disabled":false,"info":""},{"id":"7ab6f02a.9cea8","type":"tab","label":"SVG Example","disabled":false,"info":""},{"id":"18cb2d06.dad4f3","type":"tab","label":"WebMidi","disabled":false,"info":""},{"id":"ae5462.de6feba","type":"ui_group","z":"","name":"SVG Control","tab":"a912ed46.76e6a","disp":true,"width":"6","collapse":false},{"id":"28d477b9.3c4c58","type":"ui_base","theme":{"name":"theme-light","lightTheme":{"default":"#0094CE","baseColor":"#0094CE","baseFont":"-apple-system,BlinkMacSystemFont,Segoe UI,Roboto,Oxygen-Sans,Ubuntu,Cantarell,Helvetica Neue,sans-serif","edited":true,"reset":false},"darkTheme":{"default":"#097479","baseColor":"#097479","baseFont":"-apple-system,BlinkMacSystemFont,Segoe UI,Roboto,Oxygen-Sans,Ubuntu,Cantarell,Helvetica Neue,sans-serif","edited":false},"customTheme":{"name":"Untitled Theme 1","default":"#4B7930","baseColor":"#4B7930","baseFont":"-apple-system,BlinkMacSystemFont,Segoe UI,Roboto,Oxygen-Sans,Ubuntu,Cantarell,Helvetica Neue,sans-serif"},"themeState":{"base-color":{"default":"#0094CE","value":"#0094CE","edited":false},"page-titlebar-backgroundColor":{"value":"#0094CE","edited":false},"page-backgroundColor":{"value":"#fafafa","edited":false},"page-sidebar-backgroundColor":{"value":"#ffffff","edited":false},"group-textColor":{"value":"#1bbfff","edited":false},"group-borderColor":{"value":"#ffffff","edited":false},"group-backgroundColor":{"value":"#ffffff","edited":false},"widget-textColor":{"value":"#111111","edited":false},"widget-backgroundColor":{"value":"#0094ce","edited":false},"widget-borderColor":{"value":"#ffffff","edited":false},"base-font":{"value":"-apple-system,BlinkMacSystemFont,Segoe UI,Roboto,Oxygen-Sans,Ubuntu,Cantarell,Helvetica Neue,sans-serif"}},"angularTheme":{"primary":"indigo","accents":"blue","warn":"red","background":"grey"}},"site":{"name":"Node-RED Dashboard","hideToolbar":"false","allowSwipe":"false","lockMenu":"false","allowTempTheme":"true","dateFormat":"DD/MM/YYYY","sizes":{"sx":48,"sy":48,"gx":6,"gy":6,"cx":6,"cy":6,"px":0,"py":0}}},{"id":"a912ed46.76e6a","type":"ui_tab","z":"","name":"Home","icon":"dashboard","disabled":false,"hidden":false},{"id":"79de89f3.5738b8","type":"ui_group","z":"","name":"Color Control","tab":"a912ed46.76e6a","disp":true,"width":"6","collapse":false},{"id":"bb91a486.af4708","type":"websocket-client","z":"","path":"ws://localhost:1880/ws/keyboard","tls":"","wholemsg":"false"},{"id":"6ed18661.702cc8","type":"websocket-listener","z":"","path":"/ws/keyboard","wholemsg":"false"},{"id":"2e02bffb.d6d55","type":"websocket-client","z":"","path":"ws://localhost:1880/ws/keyboard","tls":"","wholemsg":"false"},{"id":"2c6ea1a4.0c603e","type":"websocket-listener","z":"","path":"/ws/keyboard","wholemsg":"false"},{"id":"c655a56c.a89d48","type":"deconz-server","z":"","name":"Phoscon-GW","ip":"192.168.1.238","port":"80","apikey":"212017FBF2","ws_port":"443","secure":false,"polling":"15"},{"id":"c3097e5.951a18","type":"websocket-client","z":"","path":"ws://localhost:1880/ws/webmidi","tls":"","wholemsg":"false"},{"id":"70c930c8.f4377","type":"websocket-listener","z":"","path":"/ws/webmidi","wholemsg":"true"},{"id":"65c5028d.d4635c","type":"comment","z":"30ea3041.735c1","name":"uibuilder/Quote Example","info":"[Front-End](/uib_simple)\n\nThis flow gets a \"quote of the day\" from the Internet and passes it\nto uibuilder. It caches the result so that if you reload the page,\nyou get the last result back. The quote is updated every 30 minutes\nduring the day and evening.\n\n\"Simple\" refers to the front-end code. While the flow looks a little\ncomplex, it really isn't. A trigger (repeating), an Internet request,\na cache and uibuilder. The link nodes loop the control output from\nuibuilder back to the cache.\n\n## Configuration\n\nUpdate the files:\n\n* `index.html`\n* `index.js`\n* `index.css`\n\nAccording to the example(s) in the 3 other comment nodes in this example.\n\nPress the button on the trigger to start the flow.","x":190,"y":160,"wires":[]},{"id":"2c2db139.e5f60e","type":"comment","z":"30ea3041.735c1","name":"index.html","info":"<!doctype html>\n<html lang=\"en\"><head>\n    <meta charset=\"utf-8\">\n    <meta http-equiv=\"X-UA-Compatible\" content=\"IE=edge\">\n    <meta name=\"viewport\" content=\"width=device-width, minimum-scale=1, initial-scale=1, user-scalable=yes\">\n\n    <title>uibuilder simple example</title>\n    <meta name=\"description\" content=\"Node-RED uibuilder - Simple example using VueJS\">\n\n    <link rel=\"icon\" href=\"./images/node-blue.ico\">\n\n    <!-- Put your own custom styles in here -->\n    <link rel=\"stylesheet\" href=\"./index.css\" media=\"all\">\n\n</head><body>\n    <!-- The \"app\" element is where the code for dynamic updates is attached -->\n\t<div id=\"app\">\n\t    <h1>A simple uibuilder page</h1>\n\t    <p>\n\t        The elements below are dynamically updated when you send\n\t        a msg to your uibuilder node.\n\t    </p>\n\t    \n\t    <div v-if=\"msg.payload\">\n\t        <h2>Quote of the Day</h2>\n\t        <blockquote>\n\t            <i>{{ msg.payload.quote.body }}</i>\n    \t        <div>{{ msg.payload.quote.author }}</div>\n\t        </blockquote>\n\t    </div>\n\t    \n\t    <h2>The full msg object</h2>\n\t\t<code>{{ msg }}</code>\n\t\t\n\t</div>\n\n    <!-- Vendor Libraries - Load in the right order -->\n    <script src=\"../uibuilder/vendor/socket.io/socket.io.js\"></script>\n    <script src=\"../uibuilder/vendor/vue/dist/vue.min.js\"></script>\n\n    <!-- REQUIRED: Sets up Socket listeners, the uibuilder and msg objects -->\n    <script src=\"./uibuilderfe.min.js\"></script>\n\n    <!-- Put your own custom code in here -->\n    <script src=\"./index.js\"></script>\n\n</body></html>","x":380,"y":160,"wires":[],"icon":"node-red/parser-html.svg"},{"id":"780db664.523498","type":"comment","z":"30ea3041.735c1","name":"index.js","info":"/* jshint browser: true, esversion: 5, asi: true */\n/*globals uibuilder, Vue */\n// @ts-nocheck\n/*\n  Copyright (c) 2019 Julian Knight (Totally Information)\n\n  Licensed under the Apache License, Version 2.0 (the \"License\");\n  you may not use this file except in compliance with the License.\n  You may obtain a copy of the License at\n\n  http://www.apache.org/licenses/LICENSE-2.0\n\n  Unless required by applicable law or agreed to in writing, software\n  distributed under the License is distributed on an \"AS IS\" BASIS,\n  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.\n  See the License for the specific language governing permissions and\n  limitations under the License.\n*/\n'use strict'\n\n/** @see https://github.com/TotallyInformation/node-red-contrib-uibuilder/wiki/Front-End-Library---available-properties-and-methods */\n\nvar app1 = new Vue({\n    // The HTML element to attach to\n\tel: '#app',\n\t/** Pre-defined data\n\t *  Anything defined here can be used in the HTML\n\t *  if you update it, the HTML will automatically update\n\t */\n\tdata: {\n\t\tmsg: '[Nothing Recieved Yet]',\n\t},\n\n    // This is called when Vue is fully loaded\n\tmounted: function() {\n\t    // Start up uibuilder\n\t\tuibuilder.start()\n\t\t\n\t\t// Keep a convenient reference to the Vue app\n\t\tvar vueApp = this\n\n        /** Triggered when the node on the Node-RED server\n         *  recieves a (non-control) msg\n         */\n\t\tuibuilder.onChange('msg', function(msg) {\n\t\t\tvueApp.msg = msg\n\t\t})\n\n\t\t// Send message back to node-red\n\t\t// uibuilder.send({payload:'some message'})\n\n\t\t// Triggered on reciept of a control message from node-red\n\t\t//uibuilder.onChange('ctrlMsg', function(msg) {\n\t\t//    console.log(msg)\n\t\t//})\n\t},\n\t\n}) // --- End of the Vue app definition --- //\n\n// EOF","x":510,"y":160,"wires":[],"icon":"font-awesome/fa-code"},{"id":"662ebe64.b6f7a","type":"comment","z":"30ea3041.735c1","name":"index.css","info":"body {font-family: sans-serif; font-size: 120%;}\ndiv, p, code { margin:0.3em; padding: 0.3em;}\n\nblockquote i {\n    font-size: 1.5em; color:grey; font-style: italic;\n}","x":640,"y":160,"wires":[],"icon":"node-red/hash.svg"},{"id":"885de12d.756e6","type":"debug","z":"30ea3041.735c1","name":"simple-debug","active":false,"tosidebar":true,"console":false,"tostatus":false,"complete":"true","targetType":"full","x":700,"y":200,"wires":[]},{"id":"308375be.b0385a","type":"uibuilder","z":"30ea3041.735c1","name":"Simple Example","topic":"","url":"uib_simple","fwdInMessages":false,"allowScripts":false,"allowStyles":false,"copyIndex":true,"showfolder":false,"x":490,"y":220,"wires":[["885de12d.756e6"],["8fe3420.6ec7ec"]]},{"id":"37c6a11e.f90d2e","type":"inject","z":"30ea3041.735c1","name":"","topic":"","payload":"","payloadType":"str","repeat":"","crontab":"","once":false,"onceDelay":"","x":110,"y":220,"wires":[["c4f300ca.54975"]]},{"id":"8fe3420.6ec7ec","type":"debug","z":"30ea3041.735c1","name":"uib controls","active":false,"tosidebar":true,"console":false,"tostatus":false,"complete":"true","targetType":"full","x":690,"y":240,"wires":[]},{"id":"a901a12c.c955c","type":"debug","z":"30ea3041.735c1","name":"qod-debug","active":false,"tosidebar":true,"console":false,"tostatus":false,"complete":"true","targetType":"full","x":490,"y":300,"wires":[]},{"id":"c4f300ca.54975","type":"http request","z":"30ea3041.735c1","name":"Quote of the day","method":"GET","ret":"obj","paytoqs":false,"url":"https://favqs.com/api/qotd","tls":"","persist":false,"proxy":"","authType":"","x":270,"y":220,"wires":[["308375be.b0385a","a901a12c.c955c"]]},{"id":"358f1b7c.710a54","type":"debug","z":"b874d525.23b288","name":"simple-debug","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"true","targetType":"full","x":840,"y":180,"wires":[]},{"id":"1241df40.626d41","type":"uibuilder","z":"b874d525.23b288","name":"Simple Example","topic":"","url":"uib_color","fwdInMessages":false,"allowScripts":false,"allowStyles":false,"copyIndex":true,"showfolder":false,"x":580,"y":260,"wires":[["358f1b7c.710a54"],["76e29ea2.e1af6"]]},{"id":"76e29ea2.e1af6","type":"debug","z":"b874d525.23b288","name":"uib controls","active":false,"tosidebar":true,"console":false,"tostatus":false,"complete":"true","targetType":"full","x":830,"y":320,"wires":[]},{"id":"9524adc.d91fc5","type":"ui_colour_picker","z":"b874d525.23b288","name":"","label":"background","group":"79de89f3.5738b8","format":"hex","outformat":"string","showSwatch":true,"showPicker":false,"showValue":false,"showHue":false,"showAlpha":false,"showLightness":true,"square":"false","dynOutput":"false","order":0,"width":0,"height":0,"passthru":true,"topic":"","x":190,"y":260,"wires":[["77687a12.39bae4"]]},{"id":"77687a12.39bae4","type":"template","z":"b874d525.23b288","name":"","field":"payload","fieldType":"msg","format":"handlebars","syntax":"mustache","template":"#{{payload}}","output":"str","x":380,"y":260,"wires":[["1241df40.626d41"]]},{"id":"37c1da94.bfe8d6","type":"comment","z":"b874d525.23b288","name":"uibuilder/Color Example","info":"[Front-End](/uib_simple)\n\nThis flow takes a HTML color value, adds a hash prefix and passes it to uibuilder. It caches the result so that if you reload the page,\nyou get the last result back.\n\n## Configuration\n\nUpdate the files:\n\n* `index.html`\n* `index.js`\n* `index.css`\n\nAccording to the example(s) in the 3 other comment nodes in this example.\n\n## Usage\n\n* use the gui at <http://localhost:1880/ui>\n* view the result at <http://localhost:1880/uib_color> ","x":220,"y":80,"wires":[]},{"id":"9f5609c0.5fbcb8","type":"comment","z":"b874d525.23b288","name":"index.html","info":"<!doctype html>\n<html lang=\"en\"><head>\n    <meta charset=\"utf-8\">\n    <meta http-equiv=\"X-UA-Compatible\" content=\"IE=edge\">\n    <meta name=\"viewport\" content=\"width=device-width, minimum-scale=1, initial-scale=1, user-scalable=yes\">\n\n    <title>uibuilder color example</title>\n    <meta name=\"description\" content=\"Node-RED uibuilder - Simple example using VueJS\">\n\n    <link rel=\"icon\" href=\"./images/node-blue.ico\">\n\n    <!-- Put your own custom styles in here -->\n    <link rel=\"stylesheet\" href=\"./index.css\" media=\"all\">\n\n</head><body>\n    \n    <!-- The \"app\" element is where the code for dynamic updates is attached -->\n\t<div id=\"app\" :style=\"myStyle\">\n\t</div>\n\n    <!-- Vendor Libraries - Load in the right order -->\n    <script src=\"../uibuilder/vendor/socket.io/socket.io.js\"></script>\n    <script src=\"../uibuilder/vendor/vue/dist/vue.min.js\"></script>\n\n    <!-- REQUIRED: Sets up Socket listeners, the uibuilder and msg objects -->\n    <script src=\"./uibuilderfe.min.js\"></script>\n\n    <!-- Put your own custom code in here -->\n    <script src=\"./index.js\"></script>\n\n</body></html>","x":580,"y":80,"wires":[],"icon":"node-red/parser-html.svg"},{"id":"8e4c0a4e.28ce08","type":"comment","z":"b874d525.23b288","name":"index.js","info":"/* jshint browser: true, esversion: 5, asi: true */\n/*globals uibuilder, Vue */\n// @ts-nocheck\n/*\n  Copyright (c) 2019 Julian Knight (Totally Information)\n\n  Licensed under the Apache License, Version 2.0 (the \"License\");\n  you may not use this file except in compliance with the License.\n  You may obtain a copy of the License at\n\n  http://www.apache.org/licenses/LICENSE-2.0\n\n  Unless required by applicable law or agreed to in writing, software\n  distributed under the License is distributed on an \"AS IS\" BASIS,\n  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.\n  See the License for the specific language governing permissions and\n  limitations under the License.\n*/\n'use strict'\n\n/** @see https://github.com/TotallyInformation/node-red-contrib-uibuilder/wiki/Front-End-Library---available-properties-and-methods */\n\nvar app1 = new Vue({\n    // The HTML element to attach to\n\tel: '#app',\n\t/** Pre-defined data\n\t *  Anything defined here can be used in the HTML\n\t *  if you update it, the HTML will automatically update\n\t */\n\tdata: {\n\t\tmyStyle: {\n\t\t    backgroundColor: '#000000'\n\t\t}\n\t},\n\n    // This is called when Vue is fully loaded\n\tmounted: function() {\n\t    \n\t    // Start up uibuilder\n\t\tuibuilder.start()\n\t\t\n\t\t// Keep a convenient reference to the Vue app\n\t\tvar vueApp = this\n\n        /** Triggered when the node on the Node-RED server\n         *  recieves a (non-control) msg\n         */\n\t\tuibuilder.onChange('msg', function(msg) {\n\t\t\tvueApp.myStyle = {\n\t\t\t    backgroundColor: msg.payload\n\t\t\t}\n\t\t})\n\n\t\t// Send message back to node-red\n\t\t// uibuilder.send({payload:'some message'})\n\n\t\t// Triggered on reciept of a control message from node-red\n\t\t//uibuilder.onChange('ctrlMsg', function(msg) {\n\t\t//    console.log(msg)\n\t\t//})\n\t},\n\t\n}) // --- End of the Vue app definition --- //\n\n// EOF","x":570,"y":120,"wires":[],"icon":"font-awesome/fa-code"},{"id":"b4ea994c.2c3988","type":"comment","z":"b874d525.23b288","name":"index.css","info":"#app {\n    position: fixed;\n    width: 100%;\n    height: 100%;\n    left: 0;\n    top: 0;\n}","x":580,"y":160,"wires":[],"icon":"node-red/hash.svg"},{"id":"cebc8753.35f168","type":"debug","z":"7ab6f02a.9cea8","name":"simple-debug","active":false,"tosidebar":true,"console":false,"tostatus":false,"complete":"true","targetType":"full","x":800,"y":220,"wires":[]},{"id":"108ab01a.95776","type":"uibuilder","z":"7ab6f02a.9cea8","name":"Simple Example","topic":"","url":"uib_svg","fwdInMessages":false,"allowScripts":false,"allowStyles":false,"copyIndex":true,"showfolder":false,"x":580,"y":320,"wires":[["cebc8753.35f168"],["bba40ccb.69052"]]},{"id":"bba40ccb.69052","type":"debug","z":"7ab6f02a.9cea8","name":"uib controls","active":false,"tosidebar":true,"console":false,"tostatus":false,"complete":"true","targetType":"full","x":790,"y":360,"wires":[]},{"id":"7baba7a1.8ef1e8","type":"ui_colour_picker","z":"7ab6f02a.9cea8","name":"","label":"circle color","group":"ae5462.de6feba","format":"hex","outformat":"string","showSwatch":true,"showPicker":false,"showValue":false,"showHue":false,"showAlpha":false,"showLightness":true,"square":"false","dynOutput":"true","order":0,"width":0,"height":0,"passthru":true,"topic":"svg/circle","x":150,"y":260,"wires":[["4dedf91c.7676d8"]]},{"id":"4dedf91c.7676d8","type":"template","z":"7ab6f02a.9cea8","name":"","field":"payload","fieldType":"msg","format":"handlebars","syntax":"mustache","template":"#{{payload}}","output":"str","x":400,"y":320,"wires":[["108ab01a.95776"]]},{"id":"6121a4af.6ea09c","type":"comment","z":"7ab6f02a.9cea8","name":"uibuilder/SVG Example","info":"[Front-End](/uib_svg)\n\nThis flow passes HTML color values and numbers to UI-builder. This information is used to modify various elements in an SVG based on the topic\n\n## Configuration\n\nUpdate the files:\n\n* `index.html`\n* `index.js`\n* `index.css`\n\nAccording to the example(s) in the 3 other comment nodes in this example.\n\n## Usage\n\n* use the gui at <http://localhost:1880/ui>\n* view the result at <http://localhost:1880/uib_svg> ","x":180,"y":120,"wires":[]},{"id":"49081ecc.3fa1e","type":"comment","z":"7ab6f02a.9cea8","name":"index.html","info":"<!doctype html>\n<html lang=\"en\"><head>\n    <meta charset=\"utf-8\">\n    <meta http-equiv=\"X-UA-Compatible\" content=\"IE=edge\">\n    <meta name=\"viewport\" content=\"width=device-width, minimum-scale=1, initial-scale=1, user-scalable=yes\">\n\n    <title>uibuilder SVG example</title>\n    <meta name=\"description\" content=\"Node-RED uibuilder - Simple example using VueJS\">\n\n    <link rel=\"icon\" href=\"./images/node-blue.ico\">\n\n    <!-- Put your own custom styles in here -->\n    <link rel=\"stylesheet\" href=\"./index.css\" media=\"all\">\n\n</head><body>\n    \n    <!-- The \"app\" element is where the code for dynamic updates is attached -->\n\t<div id=\"app\" :style=\"appStyle\">\n\t  \n\t  <svg width=\"100%\" height=\"100%\" viewBox=\"0 0 1000 1000\">\n         <g>\n            <circle cx=\"333\" cy=\"500\" :r=\"circleRadius\" stroke=\"black\" \n            stroke-width=\"3\" :fill=\"circleFill\" />\n            <rect :style=\"squareStyle\"/>\n            <polygon transform='translate(500 400)' :style=\"triangleStyle\" points=\"0,200 100,0 200,200\" />\n         </g> \n      </svg>\n\t  \n\t</div>\n\n    <!-- Vendor Libraries - Load in the right order -->\n    <script src=\"../uibuilder/vendor/socket.io/socket.io.js\"></script>\n    <script src=\"../uibuilder/vendor/vue/dist/vue.min.js\"></script>\n\n    <!-- REQUIRED: Sets up Socket listeners, the uibuilder and msg objects -->\n    <script src=\"./uibuilderfe.min.js\"></script>\n\n    <!-- Put your own custom code in here -->\n    <script src=\"./index.js\"></script>\n\n</body></html>","x":540,"y":120,"wires":[],"icon":"node-red/parser-html.svg"},{"id":"9d68c16a.e5755","type":"comment","z":"7ab6f02a.9cea8","name":"index.js","info":"/* jshint browser: true, esversion: 5, asi: true */\n/*globals uibuilder, Vue */\n// @ts-nocheck\n/*\n  Copyright (c) 2019 Julian Knight (Totally Information)\n\n  Licensed under the Apache License, Version 2.0 (the \"License\");\n  you may not use this file except in compliance with the License.\n  You may obtain a copy of the License at\n\n  http://www.apache.org/licenses/LICENSE-2.0\n\n  Unless required by applicable law or agreed to in writing, software\n  distributed under the License is distributed on an \"AS IS\" BASIS,\n  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.\n  See the License for the specific language governing permissions and\n  limitations under the License.\n*/\n'use strict'\n\n/** @see https://github.com/TotallyInformation/node-red-contrib-uibuilder/wiki/Front-End-Library---available-properties-and-methods */\n\nvar app1 = new Vue({\n    // The HTML element to attach to\n\tel: '#app',\n\t/** Pre-defined data\n\t *  Anything defined here can be used in the HTML\n\t *  if you update it, the HTML will automatically update\n\t */\n\tdata: {\n\n\t\t// individual attributes\n\t\tcircleFill: '#ff0000',\n\t\tcircleRadius: 100,\n\t\t\n\t\t// attributes grouped into styles\n\t\tappStyle: {\n\t\t    backgroundColor: '#ffffff'\n\t\t},\n\t\tsquareStyle: {\n\t\t    fill: '#00ff00',\n\t\t    stroke: 'black',\n\t\t    strokeWidth: '3',\n\t\t    x:800,\n\t\t    y:400,\n\t\t    width: 200,\n\t\t    height:200,\n\t\t},\n\t\ttriangleStyle: {\n\t\t    fill: '#ffff00',\n\t\t    stroke: 'black',\n\t\t    strokeWidth: '3'\n\t\t}\n\t},\n\n    // This is called when Vue is fully loaded\n\tmounted: function() {\n\t    \n\t    // Start up uibuilder\n\t\tuibuilder.start()\n\t\t\n\t\t// Keep a convenient reference to the Vue app\n\t\tvar app = this\n\n        /** Triggered when the node on the Node-RED server\n         *  recieves a (non-control) msg\n         */\n\t\tuibuilder.onChange('msg', function(msg) {\n\t\t    \n\t\t    // change app style\n\t\t    if(msg.topic === 'svg/app') {\n    \t\t    app.appStyle.backgroundColor = msg.payload;\n\t\t    }\n\t\t   \n\t\t    // change circle attribute \n\t        if(msg.topic === 'svg/circle') {\n    \t\t\tapp.circleFill = msg.payload;\n\t        }\n    \t\t\t\n\t\t\t// change square style\n\t\t\tif(msg.topic === 'svg/square') {\n    \t\t\tapp.squareStyle.fill = msg.payload;\n\t\t\t}\n\t\t\t\n\t\t\t//change triangle style\n\t\t\tif(msg.topic === 'svg/triangle') {\n\t\t\t    app.triangleStyle.fill = msg.payload;\n\t\t\t}\n\t\t\t\n\t\t\t// change square size\n\t\t    if(msg.topic === 'svg/square/size') {\n\t\t\t    var d = msg.payload;\n    \t\t\tapp.squareStyle.width = d;\n    \t\t\tapp.squareStyle.height = d;\n    \t\t\tapp.squareStyle.x = 900 - d/2;\n    \t\t\tapp.squareStyle.y = 500 - d/2;\n\t\t\t}\n\t\t\t\n\t\t\t// change circle size\n\t\t    if(msg.topic === 'svg/circle/size') {\n    \t\t\tapp.circleRadius = msg.payload\n\t\t\t}\n\t\t\t\n\t\t\t\n\t\t})\n\n\t\t// Send message back to node-red\n\t\t// uibuilder.send({payload:'some message'})\n\n\t\t// Triggered on reciept of a control message from node-red\n\t\t//uibuilder.onChange('ctrlMsg', function(msg) {\n\t\t//    console.log(msg)\n\t\t//})\n\t},\n\t\n}) // --- End of the Vue app definition --- //\n\n// EOF","x":530,"y":160,"wires":[],"icon":"font-awesome/fa-code"},{"id":"dc413a10.66de08","type":"comment","z":"7ab6f02a.9cea8","name":"index.css","info":"#app {\n    position: fixed;\n    width: 100%;\n    height: 100%;\n    left: 0;\n    top: 0;\n}","x":540,"y":200,"wires":[],"icon":"node-red/hash.svg"},{"id":"6c814ae7.bf5364","type":"ui_colour_picker","z":"7ab6f02a.9cea8","name":"","label":"square color","group":"ae5462.de6feba","format":"hex","outformat":"string","showSwatch":true,"showPicker":false,"showValue":false,"showHue":false,"showAlpha":false,"showLightness":true,"square":"false","dynOutput":"true","order":0,"width":0,"height":0,"passthru":true,"topic":"svg/square","x":150,"y":340,"wires":[["4dedf91c.7676d8"]]},{"id":"6a9769db.2ef438","type":"ui_colour_picker","z":"7ab6f02a.9cea8","name":"","label":"triangle color","group":"ae5462.de6feba","format":"hex","outformat":"string","showSwatch":true,"showPicker":false,"showValue":false,"showHue":false,"showAlpha":false,"showLightness":true,"square":"false","dynOutput":"true","order":0,"width":0,"height":0,"passthru":true,"topic":"svg/triangle","x":150,"y":420,"wires":[["4dedf91c.7676d8"]]},{"id":"c8d04d3d.e8157","type":"ui_colour_picker","z":"7ab6f02a.9cea8","name":"","label":"background","group":"ae5462.de6feba","format":"hex","outformat":"string","showSwatch":true,"showPicker":false,"showValue":false,"showHue":false,"showAlpha":false,"showLightness":true,"square":"false","dynOutput":"true","order":0,"width":0,"height":0,"passthru":true,"topic":"svg/app","x":150,"y":180,"wires":[["4dedf91c.7676d8"]]},{"id":"e82fe0ed.1cc74","type":"ui_slider","z":"7ab6f02a.9cea8","name":"","label":"square size","tooltip":"","group":"ae5462.de6feba","order":4,"width":0,"height":0,"passthru":true,"outs":"all","topic":"svg/square/size","min":"50","max":"200","step":"1","x":150,"y":540,"wires":[["108ab01a.95776"]]},{"id":"5c5bb20d.47cf1c","type":"ui_slider","z":"7ab6f02a.9cea8","name":"","label":"circle size","tooltip":"","group":"ae5462.de6feba","order":4,"width":0,"height":0,"passthru":true,"outs":"all","topic":"svg/circle/size","min":"50","max":"200","step":1,"x":140,"y":600,"wires":[["108ab01a.95776"]]},{"id":"d2fa72db.6a053","type":"deconz-input","z":"30ea3041.735c1","name":"","server":"c655a56c.a89d48","device":"group_1","device_name":"○ Group 1","state":"0","output":"always","outputAtStartup":true,"x":160,"y":440,"wires":[["c55dc82.e062a38"],["c55dc82.e062a38"]]},{"id":"c55dc82.e062a38","type":"debug","z":"30ea3041.735c1","name":"","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"false","x":430,"y":440,"wires":[]},{"id":"7277b3ec.968f6c","type":"deconz-output","z":"30ea3041.735c1","name":"","server":"c655a56c.a89d48","device":"group_1","device_name":"○ Group 1","command":"bri","commandType":"deconz_cmd","payload":"payload","payloadType":"msg","transitionTime":"","x":320,"y":560,"wires":[]},{"id":"2b8abb21.df11e4","type":"ui_slider","z":"30ea3041.735c1","name":"","label":"slider","tooltip":"","group":"ae5462.de6feba","order":6,"width":0,"height":0,"passthru":true,"outs":"end","topic":"","min":0,"max":"250","step":"10","x":120,"y":560,"wires":[["7277b3ec.968f6c"]]},{"id":"b684c903.cb9e38","type":"ui_button","z":"30ea3041.735c1","name":"","group":"ae5462.de6feba","order":7,"width":0,"height":0,"passthru":false,"label":"button","tooltip":"","color":"","bgcolor":"","icon":"","payload":"","payloadType":"str","topic":"","x":240,"y":660,"wires":[["7277b3ec.968f6c"]]},{"id":"d6680955.4cb828","type":"inject","z":"18cb2d06.dad4f3","name":"","topic":"","payload":"{\"topic\":\"midi/test\",\"payload\":\"100\"}","payloadType":"str","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":130,"y":300,"wires":[["7b7a3214.38fe2c"]]},{"id":"65910586.fb4dec","type":"http response","z":"18cb2d06.dad4f3","name":"","statusCode":"200","headers":{},"x":860,"y":400,"wires":[]},{"id":"12f54743.052f99","type":"http in","z":"18cb2d06.dad4f3","name":"","url":"/webmidi","method":"get","upload":false,"swaggerDoc":"","x":130,"y":400,"wires":[["6055702f.01bd4"]],"info":"<http://localhost:1880/webmidi>"},{"id":"6055702f.01bd4","type":"template","z":"18cb2d06.dad4f3","name":"","field":"payload","fieldType":"msg","format":"html","syntax":"plain","template":"<html>\n    <head>\n        <script src=\"https://cdn.jsdelivr.net/npm/webmidi@2.0.0\"></script>\n    </head>\n    <body>\n        \n         <h1>Please connect your midi device</h1>\n         <ul id=\"log\"></ul>\n         \n         <script>\n         \n            var socket = new WebSocket(`ws://${document.location.host}/ws/webmidi`);\n            \n            function log(msg) {\n                document.getElementById(\"log\").insertAdjacentHTML('afterbegin', `<li>${msg}</li>`);\n            }\n            \n            function send(obj) {\n                socket.send(JSON.stringify(obj));\n            }\n             \n            socket.onopen = function () {\n                log(\"Websocket opened\");\n            };\n            \n            socket.onerror = function (errorEvent) {\n                log(\"Error! Websocket closed\");\n            };\n            \n            WebMidi.enable(function (err) {\n\n                if (err) {\n                    log(\"WebMidi could not be enabled.\");\n                    return;\n                } \n  \n                log(\"WebMidi enabled!\");\n                console.log(WebMidi.inputs);\n                console.log(WebMidi.outputs);\n                \n                //get the first midi input device\n                let input = WebMidi.inputs[1];\n                \n                input.addListener('noteon', 'all',\n                    function(e) {\n                        log(`Key Down: ${e.note.name} (Octave ${e.note.octave})`);\n                        send({ payload: e.note, topic: 'midi/noteon' });\n                    }\n                );\n                \n                input.addListener('noteoff', 'all',\n                    function (e) {\n                        log(`Key Up: ${e.note.name} (Octave ${e.note.octave})`);\n                        send({ payload: e.note, topic: 'midi/noteoff' });\n                    }\n                );\n       \n                input.addListener('controlchange', 'all',\n                    function (e) {\n                        log(`Controller ${e.controller.number}:  ${e.value} `);\n                        console.log(\"Received 'controlchange' message.\", e);\n                        send({ payload: {number: e.controller.number, value: e.value}, topic: 'midi/controlchange' });\n                    }\n                );\n                \n                         \n                input.addListener('pitchbend', 'all',\n                    function (e) {\n                        log(\"Received Pitch Bend ...\");\n                        console.log(\"Pitch Bend:\", e);\n                    }\n                );\n                \n  \n            });\n             \n         </script>\n         \n    </body>\n</html>","output":"str","x":540,"y":400,"wires":[["65910586.fb4dec"]]},{"id":"7b7a3214.38fe2c","type":"websocket out","z":"18cb2d06.dad4f3","name":"","server":"","client":"c3097e5.951a18","x":610,"y":300,"wires":[]},{"id":"c00791b6.91b47","type":"comment","z":"18cb2d06.dad4f3","name":"test the websocket connection","info":"","x":190,"y":260,"wires":[]},{"id":"cc62a4ee.7252d8","type":"comment","z":"18cb2d06.dad4f3","name":"website to send midi input to server","info":"<http://localhost:1880/webmidi>","x":200,"y":360,"wires":[]},{"id":"b05df578.c12e48","type":"websocket in","z":"18cb2d06.dad4f3","name":"","server":"70c930c8.f4377","client":"","x":140,"y":200,"wires":[["3de31dab.351cb2"]]},{"id":"36e06496.8735fc","type":"comment","z":"18cb2d06.dad4f3","name":"receive webmidi via websocket","info":"","x":190,"y":160,"wires":[]},{"id":"cb95fc9a.84c64","type":"debug","z":"18cb2d06.dad4f3","name":"","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"false","x":1030,"y":140,"wires":[]},{"id":"4a3c0322.80013c","type":"deconz-output","z":"18cb2d06.dad4f3","name":"","server":"c655a56c.a89d48","device":"group_1","device_name":"○ Group 1","command":"bri","commandType":"deconz_cmd","payload":"payload","payloadType":"msg","transitionTime":"","x":1440,"y":200,"wires":[]},{"id":"d64c4ecb.b732d","type":"ui_slider","z":"18cb2d06.dad4f3","name":"","label":"slider","tooltip":"","group":"ae5462.de6feba","order":6,"width":0,"height":0,"passthru":true,"outs":"end","topic":"","min":0,"max":"250","step":"10","x":100,"y":500,"wires":[[]]},{"id":"e37452fe.252de","type":"ui_button","z":"18cb2d06.dad4f3","name":"","group":"ae5462.de6feba","order":7,"width":0,"height":0,"passthru":false,"label":"button","tooltip":"","color":"","bgcolor":"","icon":"","payload":"","payloadType":"str","topic":"","x":220,"y":600,"wires":[[]]},{"id":"3de31dab.351cb2","type":"switch","z":"18cb2d06.dad4f3","name":"","property":"topic","propertyType":"msg","rules":[{"t":"eq","v":"midi/controlchange","vt":"str"}],"checkall":"true","repair":false,"outputs":1,"x":510,"y":240,"wires":[["86aed60b.9bc0d8","c48ea0bf.9a46f","86f33fae.dafaa"]]},{"id":"86aed60b.9bc0d8","type":"switch","z":"18cb2d06.dad4f3","name":"","property":"payload.number","propertyType":"msg","rules":[{"t":"eq","v":"57","vt":"num"}],"checkall":"true","repair":false,"outputs":1,"x":670,"y":180,"wires":[["798aa4fb.f26e0c"]]},{"id":"798aa4fb.f26e0c","type":"change","z":"18cb2d06.dad4f3","name":"","rules":[{"t":"set","p":"payload","pt":"msg","to":"payload.value","tot":"msg"}],"action":"","property":"","from":"","to":"","reg":false,"x":850,"y":220,"wires":[["cb95fc9a.84c64","1bf780ed.105e6f"]]},{"id":"1bf780ed.105e6f","type":"range","z":"18cb2d06.dad4f3","minin":"0","maxin":"127","minout":"0","maxout":"255","action":"scale","round":false,"property":"payload","name":"","x":1100,"y":240,"wires":[["9b7dbaa4.3415a8"]]},{"id":"9b7dbaa4.3415a8","type":"rbe","z":"18cb2d06.dad4f3","name":"","func":"rbe","gap":"","start":"","inout":"out","property":"payload","x":1290,"y":240,"wires":[["4a3c0322.80013c"]]},{"id":"9ee6251c.896448","type":"trigger","z":"18cb2d06.dad4f3","op1":"1","op2":"0","op1type":"val","op2type":"val","duration":"250","extend":"false","units":"ms","reset":"","bytopic":"all","name":"","x":1040,"y":420,"wires":[[]]},{"id":"c48ea0bf.9a46f","type":"switch","z":"18cb2d06.dad4f3","name":"","property":"payload.number","propertyType":"msg","rules":[{"t":"eq","v":"59","vt":"num"}],"checkall":"true","repair":false,"outputs":1,"x":870,"y":300,"wires":[["6ea703d9.1ec7dc"]]},{"id":"90f80677.7d76a8","type":"deconz-output","z":"18cb2d06.dad4f3","name":"","server":"c655a56c.a89d48","device":"f0:d1:b8:00:00:10:c8:60-01","device_name":"Extended color light 4 : Extended color light","command":"sat","commandType":"deconz_cmd","payload":"payload","payloadType":"msg","transitionTime":"","x":1550,"y":300,"wires":[]},{"id":"6ea703d9.1ec7dc","type":"change","z":"18cb2d06.dad4f3","name":"","rules":[{"t":"set","p":"payload","pt":"msg","to":"payload.value","tot":"msg"}],"action":"","property":"","from":"","to":"","reg":false,"x":1070,"y":320,"wires":[["cad18a8c.7a11c8","1a92a292.2cc44d"]]},{"id":"1a92a292.2cc44d","type":"range","z":"18cb2d06.dad4f3","minin":"1","maxin":"100","minout":"1","maxout":"250","action":"scale","round":false,"property":"payload","name":"","x":1320,"y":360,"wires":[["90f80677.7d76a8","5393195d.c67448"]]},{"id":"cad18a8c.7a11c8","type":"debug","z":"18cb2d06.dad4f3","name":"","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"false","x":1270,"y":440,"wires":[]},{"id":"11246f85.704ae","type":"deconz-output","z":"18cb2d06.dad4f3","name":"","server":"c655a56c.a89d48","device":"f0:d1:b8:00:00:10:c8:60-01","device_name":"Extended color light 4 : Extended color light","command":"bri","commandType":"deconz_cmd","payload":"payload","payloadType":"msg","transitionTime":"","x":1570,"y":500,"wires":[]},{"id":"5393195d.c67448","type":"deconz-output","z":"18cb2d06.dad4f3","name":"","server":"c655a56c.a89d48","device":"f0:d1:b8:00:00:10:c8:60-01","device_name":"Extended color light 4 : Extended color light","command":"colorloopspeed","commandType":"deconz_cmd","payload":"payload","payloadType":"msg","transitionTime":"","x":1610,"y":440,"wires":[]},{"id":"86f33fae.dafaa","type":"switch","z":"18cb2d06.dad4f3","name":"","property":"payload.number","propertyType":"msg","rules":[{"t":"eq","v":"63","vt":"num"}],"checkall":"true","repair":false,"outputs":1,"x":870,"y":340,"wires":[["5b70dc18.7e1674"]]},{"id":"5b70dc18.7e1674","type":"change","z":"18cb2d06.dad4f3","name":"","rules":[{"t":"set","p":"payload","pt":"msg","to":"payload.value","tot":"msg"}],"action":"","property":"","from":"","to":"","reg":false,"x":1050,"y":360,"wires":[["e0aad166.28882","91433348.ca36"]]},{"id":"e0aad166.28882","type":"range","z":"18cb2d06.dad4f3","minin":"1","maxin":"127","minout":"1","maxout":"250","action":"scale","round":false,"property":"payload","name":"","x":1220,"y":400,"wires":[["11246f85.704ae"]]},{"id":"91433348.ca36","type":"debug","z":"18cb2d06.dad4f3","name":"","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"false","x":1230,"y":500,"wires":[]}]
```
