# M300 – Plattformübergreifende Dienste in ein Netzwerk integrieren

## GitHub Account erstellen

Zunächst wurde ein GitHub-Account auf https://www.github.com erstellt.

Folgende Angaben wurden gemacht:

- Benutzername
- E-Mail-Adresse
- Passwort

Nach der Registrierung wurde die E-Mail-Adresse bestätigt und die Anmeldung erfolgreich durchgeführt.

## Repository erstellen

Nach der Anmeldung wurde ein neues Repository erstellt.

Vorgehen:

1. Klick auf **Start a project**
2. Repository Name: `M300-Services`
3. Beschreibung optional ergänzt
4. Sichtbarkeit: **Public**
5. Option **Initialize this repository with a README** aktiviert
6. Klick auf **Create repository**

Das Repository wurde erfolgreich erstellt.

## Repository clonen

Zur sicheren Verbindung zwischen lokalem PC und GitHub wurde ein SSH-Key generiert.

```bash
ssh-keygen -t rsa -b 4096 -C "besirberra@icloud.com"
```

Standard-Datei mit Enter bestätigen:

```
Enter a file in which to save the key (~/.ssh/id_rsa): [Enter]
```

Passphrase setzen und bestätigen.

Public Key anzeigen:

```bash
cat ~/.ssh/id_rsa.pub
```

Den Schlüssel kopieren und unter GitHub → Settings → SSH and GPG Keys → New SSH Key einfügen.

Repository mit SSH klonen:

```bash
git clone git@github.com:besirberra/M300-Services.git
cd M300-Services
git status
```

Ergebnis:

```
Your branch is up to date with 'origin/main'.
nothing to commit, working tree clean
```

Git konfigurieren:

```bash
git config --global user.name "besirberra"
git config --global user.email "besirberra@icloud.com"
```

## VirtualBox

VirtualBox wurde von der offiziellen Webseite heruntergeladen und installiert.

Neue VM erstellt mit folgenden Einstellungen:

- Name: M300_Ubuntu_22.04_Desktop
- Typ: Linux
- Version: Ubuntu (64-bit)
- RAM: 2048 MB
- CPU: 2 Kerne
- Festplatte: 25 GB
- Typ: VMDK
- Dynamisch alloziert

System aktualisieren:

```bash
sudo apt-get update
sudo apt-get upgrade
sudo reboot
```

Apache installieren:

```bash
sudo apt-get install apache2
```

Test im Browser:

```
http://127.0.0.1
```

Apache-Standardseite wurde angezeigt.

## Vagrant

Neue VM erstellen:

```bash
mkdir myVM
cd myVM
vagrant init ubuntu/xenial64
vagrant up --provider virtualbox
```

SSH Verbindung:

```bash
vagrant ssh
```

Portweiterleitung:

```ruby
config.vm.network "forwarded_port", guest:80, host:8080, auto_correct: true
```

Synchronisation:

```ruby
config.vm.synced_folder ".", "/var/www/html"
```

RAM-Zuweisung:

```ruby
config.vm.provider "virtualbox" do |vb|
  vb.memory = "512"
end
```

Apache automatisch installiert über Provisioning.

Test:

```
http://localhost:8080
```

## Visual Studio Code

Visual Studio Code wurde installiert.

Extensions:

- Markdown All in One
- Vagrant Extension
- vscode-pdf
- Auto Markdown TOC

Dateien exkludieren:

```json
"files.exclude": {
  "**/.git": true,
  "**/.svn": true,
  "**/.hg": true,
  "**/.vagrant": true,
  "**/.DS_Store": true
}
```

Repository Änderungen:

- Dateien angepasst
- Stage Changes
- Commit
- Push

## Theoriefragen – Cloud & Vagrant

### Cloud Computing

Cloud-Computing beschreibt die Bereitstellung von IT-Ressourcen (Server, Speicher, Netzwerke, Software) über das Internet.

### Infrastructure as a Service (IaaS)

Virtuelle Server, Speicher und Netzwerke werden als Dienst bereitgestellt.

Beispiele:

- AWS EC2
- Microsoft Azure VM
- Google Compute Engine

### Infrastructure as Code (IaC)

Infrastructure as Code beschreibt die automatisierte Bereitstellung von Infrastruktur über Code.

Vorteile:

- Reproduzierbar
- Versionierbar
- Schnell skalierbar

### Vagrant

Vagrant erzeugt automatisiert virtuelle Maschinen.

Aussagen:

- Vagrant ist ein Hypervisor → Falsch
- Unterstützt mehrere Hypervisor → Richtig
- Erzeugt Container → Falsch

Alternativen:

- Terraform
- Ansible
- Docker
- Kubernetes
- VMware vSphere
- VirtualBox

## LB2 – Hands-on Automatisierung mit Vagrant

Ziel: automatisierte Bereitstellung eines Serverdienstes.

Neue VM:

```bash
cd C:\Users\besir\M300
mkdir myVM
cd myVM
vagrant init ubuntu/xenial64
vagrant up
vagrant ssh
```

Installation:

```bash
sudo apt-get update
sudo apt-get install -y apache2
sudo apt-get install -y webalizer
```

Provisioning ins Vagrantfile übernommen.

Portweiterleitung und Synced Folder konfiguriert.

Traffic erzeugt:

```bash
curl http://localhost/ >/dev/null 2>&1
```

Log Rotation:

```bash
sudo logrotate -f /etc/logrotate.d/apache2
```

Webalizer Output korrigiert:

```bash
sudo sed -i -e"s:/var/www/webalizer:/var/www/html/webalizer:" /etc/webalizer/webalizer.conf
```

Firewall (UFW):

```bash
sudo apt-get install -y ufw
sudo ufw allow 22
sudo ufw allow 80
sudo ufw --force enable
```

## Mini-Helpdesk (Docker Projekt)

### Projektziel

Containerisierte Webanwendung mit SQL-Datenbank via Docker Compose.

### Architektur

- Web Container (PHP + Apache)
- MySQL Container
- Monitoring mit cAdvisor

### Ports

| Service | Interner Port | Host-Port |
|----------|---------------|-----------|
| Web | 80 | 8081 |
| MySQL | 3306 | 3307 |
| cAdvisor | 8080 | 8090 |

### Volumes

```
./web -> /var/www/html
dbdata -> /var/lib/mysql
```

### Start

```bash
docker compose up -d --build
```

Web:

```
http://localhost:8081
```

Monitoring:

```
http://localhost:8090
```

### Fehler

```
mysqli_sql_exception: Connection refused
```

Lösung:

```bash
docker compose down -v
docker compose up -d --build
```

### Fazit

- Dienst deployt
- Netzwerk eingerichtet
- Ports definiert
- Persistenz umgesetzt
- Monitoring integriert
- Fehler analysiert und behoben