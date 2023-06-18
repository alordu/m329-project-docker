# Homebridge auf Portainer aufsetzen

Nun gehen wir wieder auf die Web-Oberfläche von Portainer und gehen in das Menü Stacks und klicken dort auf “Add stack”

![Untitled](Homebridge%20auf%20Portainer%20aufsetzen%20d3666fc222114371ae9e62a039217f4b/Untitled.png)

Nun geben wir unter Name den gewünschten Namen ein. Ich habe hier jetzt einfach “homebridge” genommen.

![Untitled](Homebridge%20auf%20Portainer%20aufsetzen%20d3666fc222114371ae9e62a039217f4b/Untitled%201.png)

Unter Web Editor geben wir folgendes ein:

```jsx
version: '2'
services:
  homebridge:
    image: homebridge/homebridge:latest
    restart: always
    network_mode: host
    volumes:
      - ./volumes/homebridge:/homebridge
    logging:
      driver: json-file
      options:
        max-size: "10mb"
        max-file: "1"
```

Zum Schluss klicken wir untern auf “Deploy Stack”

![Untitled](Homebridge%20auf%20Portainer%20aufsetzen%20d3666fc222114371ae9e62a039217f4b/Untitled%202.png)

Nach kurzer Zeit sollte sich der Stack deployen und automtisch starten. Öffne nun deinen Webbrowser und gibt folgendes ein: `http://IP_ADDRESS:8581`

Nun sollte sich ein Fenster öffnen wo man Homebridge einrichten kann. Klicke auf “Los gehts”

![Untitled](Homebridge%20auf%20Portainer%20aufsetzen%20d3666fc222114371ae9e62a039217f4b/Untitled%203.png)

Gib nun den gewünschten Username ein und zweimal das Passwort. Verwende bitte ein sicheres Passwort. Anschliessend klickst du auf “Weiter”

![Untitled](Homebridge%20auf%20Portainer%20aufsetzen%20d3666fc222114371ae9e62a039217f4b/Untitled%204.png)

Klicke danach auf “Dashboard öffnen”. Nun solltest du folgende Ansicht sehen:

![Untitled](Homebridge%20auf%20Portainer%20aufsetzen%20d3666fc222114371ae9e62a039217f4b/Untitled%205.png)

Ich beschreibe kurz die wichtigsten Menüs, was du wo findest:

1. Hier kannst du den Homebridge Gateway (Container) mit der Home-App koppeln. Dadurch kannst du danach die Geräte welche über den Homebridge laufen, direkt einbinden, auch wenn sie von Apple eigentlich nicht unterstützt werden.
2. Hier findest du das gleiche wie im Punkt 1 einfach in Form eines Codes.
3. Unter Plugins kannst du diverse Erweiterungen installieren: Zum Beispiel ein Connector für Unifi Protect (dass du deine Kameras von Ubiquiti in der Home-App siehst) oder eine Erweiterung wo du die Waschmaschiene von Miele ins Home einbinden kannst
4. Hier kannst du die Konfiguration von Homebridge anpassen
5. Hier siehst du alle verbundenen IOT Geräte welche mit Homebridge verbunden sind.