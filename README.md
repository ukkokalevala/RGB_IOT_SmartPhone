This code creates a web server on an ESP8266 that lets users control the brightness and color of an RGB LED through a web interface with sliders. Here’s how it works step-by-step:

Libraries
ESP8266WiFi.h: Manages Wi-Fi connection.
ESPAsyncWebServer.h: Creates an asynchronous web server to handle HTTP requests.
 WebSocketsServer.h: Manages a WebSocket server to handle real-time data communication with the client.

Pin Setup

RGB LED Pins: Pins D1, D2, and D3 are used to control the red, green, and blue components of an RGB LED, respectively.

HTML Page (index_html)

This embedded HTML code with CSS, creates a webpage where users can adjust the RGB color values with sliders:

    Three sliders for Red, Green, and Blue, each with a range from 0 to 1023.
    JavaScript listens for slider changes and sends values to the ESP8266 using WebSocket messages.

WebSocket Communication

The JavaScript section opens a WebSocket connection to the ESP8266. When the slider is adjusted:

    JavaScript sends a message in the format rvalue, gvalue, or bvalue to indicate the color and brightness value.
    The ESP8266 reads these messages to adjust the LED brightness.

onWebSocketEvent Function

Handles incoming WebSocket messages:

    Parse Messages: Reads the color indicator (r, g, or b) and the brightness value.
    Adjust LED Brightness: Uses analogWrite to set the LED brightness according to the received value.

Wi-Fi and Server Setup (setup function)

    Wi-Fi Connection: Connects to the specified SSID and password.
    Web Server: Hosts the HTML page to control the LED.
    WebSocket Server: Opens WebSocket communication on port 81 and links to onWebSocketEvent for handling messages.

Main Loop (loop function)

Keeps the WebSocket server active to handle incoming connections and data updates.

In summary:

    The webpage provides sliders to control RGB LED brightness levels.
    WebSocket communication instantly sends slider values to the ESP8266.
    The ESP8266 reads values and updates the LED brightness accordingly.
Code:
