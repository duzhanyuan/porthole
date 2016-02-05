### Global Functions ###

#### initialize ####
> initialize(int port = 4080, string defaultPage = "index.html")

Initializes and starts the porthole web server
- `port` (optional): the port used by the web server. Default: 4080
- `defaultPage` (optional): the page to serve when no file is specified. Default: index.html

#### base64EncodeImage ####
> string base64EncodeImage( [PixelData](https://github.com/uic-evl/omegalib/wiki/PixelData) image, [ImageFormat](https://github.com/uic-evl/omegalib/wiki/PixelData#image-formats) format)

Converts an image to a base64 string.
- `image`: the image to be converted.
- `format`: encoding to be used in the conversion.

----------------------------------------------------------------------------------------------------
### PortholeService ###
The `PortholeService` class exposes all the basic methods offered by the porthole interface

#### setServerStartedCommand ####
> setServerStartedCommand(string cmd)

#### setConnectedCommand ####
#### setDisconnectedCommand ####
> - setDisconnectedCommand(string cmd) 
> - setConnectedCommand(string cmd)

Sets a command to be called when a client connects or disconnects.
- `cmd`: command to be called when a client connects or disconnected, the token `%id%` will be substituted by the client id.

#### sendjs ####
> sendjs(string js, string destination)

Sends javascript code to a client.
- `js`: the code to be executed.
- `destination` the client id of the destination.

#### broadcastjs ####
> broadcastjs(string js, string origin = "")

Broadcasts javascript to all clients, excluding an optional origin.
- `js`: the code to be executed
- `origin`: optional client id of an origin client. The origin will be excluded from the broadcast.

----------------------------------------------------------------------------------------------------
### Porthole.js ###
The `Porthole.js` interface is used in html files server by porthole to interface back with the server.

> *Example*
```html
<html>
<head>
    <script src="porthole/res/porthole.js"></script>
</head>
<body>
    <script>
        porthole.connected = function() {
            // Call the print function on the server, printing this client name
            porthole.call("print('%client_id%')")
        }
    </script>
</body>
</html>
```

#### connected ####
Stores a function that will be called when a connection with the server is established.

#### socket ####
The websocket object used for the server connection

#### call ####
> porthole.call(pythonCode, ...)

#### jscall ####
> porthole.jscall(jscode, ...)

#### mccall ####
> porthole.mccall(jscode, ...)

#### sendMouseMove ####
> porthole.sendMouseMove(event)

#### sendMouseUp ####
#### sendMouseDown ####
> porthole.sendMouseUp(event)

> porthole.sendMouseDown(event)

#### sendKeyUp ####
#### sendKeyDown ####
> porthole.sendKeyUp(event)

> porthole.sendKeyDown(event)


