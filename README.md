# M300-Plattformübergreifende-Dienste-in-ein-Netzwerk-integrieren
Toolumgebung für Modul 300

Git Hub,Git Bash, Virtualbox, Vagrant & Apache

#### Inhaltsverzeichnis

* 10 - [Toolumgebung aufsetzen](#10---Toolumgebung-aufsetzen)
  * 01 - [GitHub Account](#01---github-account)
  * 02 - [Git Client](#02---git-client)
  * 03 - [VirtualBox](#03---virtualbox)
  * 04 - [Vagrant](#04---vagrant)
  * 05 - [Visual Studio Code](#05---visual-studio-code)

* 20 - [Infrastruktur-Automatisierung](#20---infrastruktur-automatisierung)
  * 01 - [Cloud Computing](#01---cloud-computing)
  * 02 - [Infrastructure as Code (IaC)](#02---infrastructure-as-code-iac)
  * 03 - [Vagrant](#03---vagrant)
  * 04 - [Packer](#04---packer)
  * 05 - [AWS Cloud](#05---aws-cloud)
  * LB2 - [LB2 hands-on](#lb2-hands-on)

* 25 - [Sicherheit](#25---sicherheit)

* 30 - [Container](#30---container)

* 35 - [Sicherheit](#35---sicherheit)

* 40 - [Kubernetes (k8s)](#40---kubernetes-k8s)

* 80 - [Ergänzungen zu den Unterlagen](#80---erganzungen-zu-den-unterlagen)

---

10 - Toolumgebung aufsetzen
===================

Hier wird die Installation von GitHub, VirtualBox, Vagrant und Visual Studio Code durchgeführt.


01 - GitHub Account
===

> [⇧ **Nach oben**](#inhaltsverzeichnis)

## Account erstellen

Zunächst wurde ein GitHub-Account auf https://www.github.com erstellt.

Folgende Angaben wurden gemacht:

- Benutzername: IKovachevska
- E-Mail-Adresse: kovacevskai11@gmail.com
- Passwort: ...

Nach der Registrierung wurde die E-Mail zur Verifizierung des Kontos bestätigt und anschliessend auf GitHub angemeldet.

## Repository erstellen

Nach der Anmeldung wurde ein neues Repository <strong>M300 -Services</strong> erstellt.

Vorgehen:

1. Klick auf **Start a project**
2. Repository Name: `M300-Services`
3. Sichtbarkeit: **Public**
4. Option **Initialize this repository with a README** aktiviert
5. Klick auf **Create repository**

Das Repository wurde erfolgreich erstellt.

## SSH-Key erstellen und dem SSH-Agent hinzufügen

Vorgehen

1.  Terminal (*Bash*) öffnen
2.  Folgenden Befehl mit der Account-E-Mail von GitHub einfügen:
    ```Shell
      $  ssh-keygen -t rsa -b 4096 -C "kovacevskai11@gmail.com"
    ```
3. Neuer SSH-Key wird erstellt:
    ```Shell
      Generating public/private rsa key pair.
    ```
4. Bei der Abfrage, unter welchem Namen der Schlüssel gespeichert werden soll, die Enter-Taste drücken (für Standard):
    ```Shell
      Enter a file in which to save the key (~/.ssh/id_rsa): [Press enter]
    ```
5. Nun kann ein Passwort für den Key festgelegt werden. 
    ```Shell
      Enter passphrase (empty for no passphrase): [Passwort]
      Enter same passphrase again: [Passwort wiederholen]
    ```


1. Auf Benutzerkonto klicken (oben rechts) und den Punkt <strong>Settings</strong> aufrufen
2. Unter den Menübereichen auf der linken Seite zum Abschnitt <strong>SSH und GPG keys</strong> wechseln
3.  Auf <strong>New SSH key</strong> klicken
4.  Im Formular unter <strong>Title</strong> eine Bezeichnung vergeben (MB SSH-Key)
5.  Den zuvor kopierten Key mit <i>CTRL + V</i> einfügen und auf <strong>Add SSH key</strong> klicken
6.  Der SSH-Key wurde erfolgreich hinzugefügt.


02 - Git Client
===

> [⇧ **Nach oben**](#inhaltsverzeichnis)

1. Git Client installiert und befähigt.
2. Client wie folgt konfiguriert:

    ```Shell
      $ git config --global user.name "<IKovachevska>"
    ```

    ```Shell
      $ git config --global user.email "<kovacevskai11@gmail.com>"
    ```

## Repository clonen

Repository mit SSH klonen:

    ```Shell
      $ git clone git@github.com:IKovachevska/M300-Services.git
      $ cd M300-Services
      $ git pull
      $ git status
    ```

![Abbildung 2](images/Abbildung-2.png)

Ergebnis:

```
Your branch is up to date with 'origin/main'.
nothing to commit, working tree clean
```

Git konfigurieren:

```bash
git config --global user.name "IKovachevska"
git config --global user.email "kovacevskai11@gmail.com"
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

![alt text](images/Abbildung 2.png)

!!!

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
