# Docker install

[Install Docker Desktop on Linux](https://docs.docker.com/desktop/install/linux-install/)

Zusammengefasst und angepasst auf Installation bei Ubuntu Server 22.04 LTS auf VMware ESXi 8.0

Am besten empfehle ich dir, dich mit SSH auf die Linux Maschiene zu verbinden. Ich empfehle dir dafür MobaXterm. Diese Installation wurde über SSH mit MobaXterm durchgeführt.

Zudem empfehle ich dir kurz mit folgenden Commands Linux zu aktualisieren

```
sudo apt update
sudo apt upgrade
```

Gnome Terminal muss bei Docker ebenfalls installiert werden! (Gemäss Docker.com) 

```
sudo apt install gnome-terminal
```

Die Installation mit „y“ bestätigen und durchlaufen lassen.

Nun müssen wir den Docker Repository einrichten. Für das benötigen ca-certificates gnupg. Folgendes nacheinander ausführen

```
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL [https://download.docker.com/linux/ubuntu/gpg](https://download.docker.com/linux/ubuntu/gpg) | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
	"deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) \
	"$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
	sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Jetzt können wir Docker installieren. Führe dazu nacheinander folgendes aus:

```
sudo apt-get install docker-ce docker-ce-cli [containerd.io](http://containerd.io/) docker-buildx-plugin docker-compose-plugin
sudo apt-get update
```

Falls aufgefordert müssen wir bei der Installation mit „y“ bestätigen.

Nun können wir einen Testcontainer starten und sehen dann, dass es funktioniert :)

```
 sudo docker run hello-world
```

Docker ist nun installiert.