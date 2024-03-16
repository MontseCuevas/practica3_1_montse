# Práctica 3 parte 1

## Código original:

      #include <WiFi.h>
      #include <WebServer.h>
      // SSID & Password
      const char* ssid = "*****"; // Enter your SSID here
      const char* password = "*****"; //Enter your Password here
      WebServer server(80); // Object of WebServer(HTTP port, 80 is defult)
      void setup() {
      Serial.begin(115200);
      Serial.println("Try Connecting to ");
      Serial.println(ssid);
      // Connect to your wi-fi modem
      WiFi.begin(ssid, password);
      // Check wi-fi is connected to wi-fi network
      while (WiFi.status() != WL_CONNECTED) {
      delay(1000);
      Serial.print(".");
      }
     Serial.println("");
     Serial.println("WiFi connected successfully");
     Serial.print("Got IP: ");
     Serial.println(WiFi.localIP()); //Show ESP32 IP on serial
     server.on("/", handle_root);
     server.begin();
     Serial.println("HTTP server started");
     delay(100);
     }
     void loop() {
     server.handleClient();
     }
     // HTML & CSS contents which display on web server
     String HTML = "<!DOCTYPE html>\
     <html>\
     <body>\
     <h1>My Primera Pagina con ESP32 - Station Mode &#128522;</h1>\
     </body>\
     </html>";
     // Handle root url (/)
     void handle_root() {
     server.send(200, "text/html", HTML);
     }



En este código se configura el ESP32 para poder actuar como un servidor web.
Este se conecta a una red Wi-Fi que es declarada con su nombre y contraseña y se ejecuta en el puerto 80.

En la función **setup()**, se inicia la comunicación serial, se intenta conectar al Wi-Fi usando el nombre y contraseña proporcionados. Luego, espera hasta que se conecte y muestra la dirección IP asignada al ESP32. Después, se define una función de controlador para la ruta y se inicia el servidor HTTP.

Se manejan las solicitudes de los clientes en un bucle continuo en la función **loop()**.

Una vez es configurado y muestra por mensaje la dirección IP, se podrá acceder a esta y al acceder se va a una página HTML simple que muestra el título "My Primera Pagina con ESP32 - Station Mode &#128522;".

## Libreria LittleFS añadida en el código original

Hemos cogido este codigo y le hemos añadido la libreria LittleFS.

**Funciones de Operaciones del Sistema de Archivos:**
Se definen funciones para realizar diversas operaciones en el sistema de archivos LittleFS, como listar directorios, crear y eliminar archivos y directorios, leer y escribir archivos, etc.

Usamos la función **test_file()**, como función de prueba del sistema de archivos. Esta realiza pruebas en el sistema de archivos LittleFS, realizando operaciones de creación, lectura, escritura, renombrado y eliminación de archivos y directorios.

En resumen, el código nuevo configura un ESP32 como un servidor web y realiza operaciones básicas en el sistema de archivos LittleFS.
"# practica3_1_montse" 
"# practica3_montse" 
