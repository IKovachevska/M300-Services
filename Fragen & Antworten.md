M300  - Fragen & Antworten

<!-- TOC -->

- 20 [- Infrastruktur Automatisierung](#--infrastruktur-automatisierung)
- [Fragen & Antworten](#fragen--antworten)
    - [Cloud Computing](#cloud-computing)
    - [Infrastructure as Code](#infrastructure-as-code)
    - [Vagrant](#vagrant)

- 25 [- Sicherheit](#--sicherheit)
- [Fragen & Antworten](#fragen--antworten)
    - [Firewall und Reverse Proxy](#firewall-und-reverse-proxy)
    - [SSH](#ssh)
  
- 30 [- Container](#--container)
- [Fragen & Antworten](#fragen--antworten)
    - [Container](#container)
    - [Docker](#docker)
    - [Docker Hub](#docker-hub)

- 35 [- Sicherheit](#--sicherheit)
- [Fragen & Antworten](#fragen--antworten)
    - [Protokollieren & Überwachen](#protokollieren--%C3%9Cberwachen)
    - [Container sichern & beschränken](#container-sichern--beschr%C3%A4nken)
    - [Kontinuierliche Integration](#kontinuierliche-integration)
  
- 40 [- Kubernetes](#--kubernetes)
- [Fragen & Antworten](#fragen--antworten)
    - [Kubernetes](#kubernetes)
    - [Objekte Ressourcen](#objekte-ressourcen)

<!-- /TOC -->


##
20 - Infrastruktur Automatisierung
===================
 
Fragen & Antworten
===

> [⇧ **Nach oben**](#inhaltsverzeichnis)

## Cloud Computing

<strong>Was versteht man unter Cloud-Computing?</strong>

- Darunter versteht man die Ausführung von Programmen, die nicht auf dem lokalen Rechner installiert sind, sondern auf einem anderen Rechner, der aus der Ferne aufgerufen wird (bspw. über das Internet).
  
---

<strong>Was versteht man unter Infrastructure as a Service - IaaS?</strong>

- Die Infrastruktur stellt die unterste Schicht im Cloud Computing dar. Der Benutzer greift hier auf bestehende Dienste innerhalb des Systems zu, verwaltet seine Recheninstanzen (virtuelle Maschinen) allerdings weitestgehend selbst.


## Infrastructure as Code

<strong>Was ist der Unterschied zur manuellen Installation der VM</strong>

- Automation, Wiederholbarkeit, Dokumentation


## Vagrant

<strong>Was wird mit Vagrant erzeugt?</strong>

- Virtuelle Maschinen

---

<strong>Welche der Aussagen treffen zu:</strong>

a) Vagrant ist ein HyperVisor

b) Vagrant erzeugt virtuelle Maschinen, dabei werden mehrere HyperVisor und Cloud Umgebungen (z.B. AWS) unterstützt.

c) Vagrant erzeugt Container

- b

---

<strong>In welchen Bereich des Cloud-Computings ist Vagrant einzuordnen: IaaS, PaaS, SaaS?</strong>

- IaaS

---

<strong>Welche Alternativen zu Vagrant bestehen?</strong>

- https://alternativeto.net/software/vagrant/

---

<strong>Wo Speichert Vagrant seine Konfiguration?</strong>

- Vagrantfile

---

<strong>Was bedeutet die Fehlermeldung "A Vagrant environment or target machine is required to run this command."?</strong>

- Sie befinden im falschen Verzeichnis, wo keine Vagrantfile vorhanden ist.

---

<strong>Bei welcher LPI Zertifizierung nützt mir das Vagrant Wissen?</strong>

- [DevOps Tools Engineer](https://www.lpi.org/our-certifications/devops-overview)


##
25 - Sicherheit
===================

Fragen & Antworten
===

> [⇧ **Nach oben**](#inhaltsverzeichnis)

## Firewall und Reverse Proxy

<strong>Was ist der Unterschied zwischen eineam Web Server und einem Reverse Proxy?</strong>

- Web Server handelt HTML Seiten direkt ab, Reverse Proxy dient als Stellvertretter für einen Web Server o.ä.
  
--- 

<strong>Was verstehen wir unter einer „White List“?</strong>

- Eine White List, fasst im Gegensatz zu einer Black List, Vertrauenswürdige Elemente, z.B. Server zusammen.

---

<strong>Was wäre die Alternative zum Absichern der einzelnen Server mit einer Firewall?</strong>

- Eine Zentrale Firewall


## SSH

<strong>Was ist der Unterschied zwischen der Datei id_rsa und id_rsa.pub?</strong>

- Private und Public Key

---

<strong>Wo darf ein SSH-Tunnel nicht angewendet werden?</strong>

- In der Firma

---

<strong>Für was dient die Datei authorized_keys?</strong>

- Beinhaltet die Public Key von allen wo ohne Password auf System dürfen

---

<strong>Für was dient die Datei known_hosts?</strong>

- Liste der Systeme wo ich mich via ssh Verbunden habe - steht nicht in Doku -> Googeln


##
30 - Container
===================

Fragen & Antworten
===

> [⇧ **Nach oben**](#inhaltsverzeichnis)

## Container

<strong>Was ist der Unterschied zwischen Vagrant und Docker?</strong>

- Vagrant ist für IaaS (Virtuelle Maschinen) und Docker für PaaS bzw. CaaS (Container)

--- 

<strong>Was welches Tools aus dem Docker Universum ist Vergleichbar mit Vagrant?</strong>

- docker machine

---

<strong>Was macht der Docker Provisioner von Vagrant?</strong>

- Installiert Docker in einer VM

---

<strong>Welche Linux Kernel Funktionalität verwenden Container?</strong>

- Linux Namespaces, siehe auch [The Missing Introduction To Containerization]

---

<strong>Welches Architekturmuster verwendet der Entwickler wenn er Container einsetzt?</strong>

- Microservices

---

<strong>Welches sind die drei Hauptmerkmale (abgeleitet vom Ur-Unix) von Microservices?</strong>

- Ein Programm soll nur eine Aufgabe erledigen, und das soll es gut machen. Programme sollen zusammenarbeiten können. Nutze eine universelle Schnittstelle. In UNIX sind das Textströme. Bei Microservices das Internet (REST).


## Docker

<strong>Was ist der Unterschied zwischen einem Docker Image und einem Container?</strong>

- Image = gebuildet und readonly, Container Image + aktuelle Änderungen im Filesystem

---

<strong>Was ist der Unterschied zwischen einer Virtuellen Maschine und einem Docker Container?</strong>

- VM hat Betriebssystem mit am laufen, Docker nur die eigenen Prozesse

---

<strong>Was ist der Unterschied zwischen einem Docker Image und einem Container?</strong>

- Image = gebuildet und readonly, Container Image + aktuelle Änderungen im Filesystem

---

<strong>Wie bekomme ich Informationen zu einem laufenden Docker Container?</strong>

- docker logs, docker inspect

---

<strong>Was ist der Unterschied zwischen einer Docker Registry und einem Repository</strong>

- In der Docker Registry werden die Container Images gespeichert. Ein Repository speichert pro Container Image verschiedene Versionen von Images.

---

<strong>Wie erstelle ich ein Container Image</strong>

- docker build

---

<strong>In welcher Datei steht welche Inhalte sich im Container Image befinden?</strong>

- Dockerfile

---

<strong>Der erste Prozess im Container bekommt die Nummer?</strong>

- 1


## Docker Hub

<strong>Was ist Docker Hub?</strong>

- Ein Container Registry, wo Container Image gespeichert werden. Docker Hub wird durch die Firma Docker zur Verfügung gestellt wird.

---

<strong>Welches sind die Alternativen?</strong>

- Praktisch jeder Cloud Anbieter stellt eine Container Registry zur Verfügung. Auch die Anbieter für die Verwaltung von Build Artefakten (z.B. Sonatype Nexus) stellen Docker Registries zur Verfügung oder haben deren Funktionalität integriert.

---

<strong>Warum sollte eine eigene Docker Registry im Unternehmen verwendet werden?</strong>

- Sicherheit, bzw. das mögliche Fehlen davon. Es kann nicht Sichergestellt werden, dass alle Container Images auf Docker Hub sicher sind.

---

<strong>Warum sollten Versionen tag von Images immer angegeben werden?</strong>

- Ansonsten wird latest verwendet und so nicht sicher welche Version wirklich verwendet wird.

---

<strong>Was ist der Unterschied zwischen `docker save`/`docker load` und `docker export`/`docker import`?</strong>

- `save/load` ist für Images, `export/import` für Container. So ist es möglich auch ohne Docker Registry Container Images auszutauschen, z.B. in einer Bank.


##
35 - Sicherheit
===================

Fragen & Antworten
===

> [⇧ **Nach oben**](#inhaltsverzeichnis)

## Protokollieren & Überwachen

<strong>Warum sollten Container überwacht werden?</strong>

- Um Fehler oder grosse Ressourcenbelastungen frühzeitig zu erkennen und einzugreifen

--- 

<strong>Was ist das syslog und wo ist es zu finden?</strong>

- Das Systemweite Log eines Linux Hosts. Verzeichnis /var/log.

---

<strong>Was ist stdout, stderr, stdin?</strong>

- Standard Output, Standard Error Ausgabe und Standard Input Eingabe.


## Container sichern & beschränken

<strong>Wie kann `docker run -v /:/homeroot -it ubuntu bash` durch Normale User verhindert werden?</strong>

- nur `root` darf Container starten

---

<strong>Wie können verschiedene Mandanten getrennt werden?</strong>

- Mittels VM's

---

<strong>Wie kann der Ressourcenverbrauch von Containern eingeschränkt werden?</strong>

- https://docs.docker.com/config/containers/resource_constraints/#configure-the-default-cfs-scheduler


## Kontinuierliche Integration

<strong>Welche Funktionen kann Jenkins übernehmen?</strong>

- CI, Modultests, Software bauen, Batch Jobs ausführen - z.B. Logs überprüfen

---

<strong>Wie baut man Modultests?</strong>

- Via Bash Scripts

---

<strong>Wie anders, als Manuell oder Zeitgesteuert könnten Jenkins Jobs auch gestartet werden?</strong>

- Durch Änderungen in einem Git Repository


##
40 - Kubernetes
===================

Fragen & Antworten
===

> [⇧ **Nach oben**](#inhaltsverzeichnis)

## Kubernetes

<strong>Was ist Kubernetes?</strong>

- Das im Juli 2014 gestartete Kubernetes (griechisch: Steuermann) stellt die derzeit populärste Container-Cluster-/Orchestrierungs-Lösung dar.

--- 

<strong>Was ist die Hauptaufgabe von Kubernetes?</strong>

- Kubernetes Hauptaufgabe ist die Verwaltung und Orchestrierung der Container innerhalb eines Clusters, der üblicherweise aus mindestens einem Kubernetes Master und multiplen Worker Nodes besteht.

---

<strong>Wer ist der Eigentümer von Kubernetes?</strong>

- Kubernetes ist mittlerweile bei der Cloud Native Computing Foundation (http://cncf.io) gehostet.

---

<strong>Was für eine Netzwerkstruktur verwendet Kubernetes?</strong>

- Kubernetes verwendet im Unterschied zu Docker eine flache Netzwerkstruktur. * Jeder Container kann mit jedem anderen ohne NAT kommunizieren. * Alle Kubernetes Nodes können mit allen Containern (und in die andere Richtung) ohne NAT kommunizieren. * Die IP, die ein Container von sich selbst sieht, ist auch die, die jeder andere Node oder Container im Netz von ihm sieht.

---

<strong>Über was Kommunizieren die Services von Nodes zu Nodes</strong>

- Über ein Overlay Netzwerk, welches auf jeder Node ein Subnetz zur Verfügung stellt.


## Objekte (Ressourcen)

<strong>Kubernetes Objekte (Ressourcen) werden im welchen Dateiformat beschrieben?</strong>

- YAML

---

<strong>Kubernetes Objekte (Ressourcen) können mittels Dashboard und welche CLI Tool verwaltet werden?</strong>

- kubectl

---

<strong>Mit was lassen sich Kubernetes Objekte (Ressourcen) gruppieren?</strong>

- Labels

---

<strong>Was sind Pods?</strong>

- Kleine Gruppe von Containern welche eng verbunden sind. Kleinste Einheit für Replikation und Platzierung (auf Node). “Logischer” Host für Container. Jeder Pods erhält genau eine IP-Adresse

---

<strong>Was sind Services?</strong>

- Eine Gruppe von Pods die zusammenarbeiten, Gruppiert mittels Label Selector. Erlaubt mittels unterschiedlichen Methoden auf den Service zuzugreifen, z.B. DNS Name. Definieren Zugriffsrichtlinien, z.B. Port Remapping für den Zugriff von ausserhalb des Clusters.

---

<strong>Was ein Ingress?</strong>

- Ein API-Objekt, das den externen Zugriff auf die Dienste in einem Cluster verwaltet, in der Regel mittels HTTP. Grob entspricht der Ingress Dienst dem Reverse Proxy Muster.

---

<strong>Was sind Namespaces bzw. deren Aufgabe?</strong>

- Sie Unterteilen den gesamten K8s Cluster in logische Partitionen bzw. Bereiche. Vergleichbar mit Subdomains.

---

<strong>Was ist die Aufgabe eines ReplicaSets?</strong>

- Stellt sicher, dass N Pods laufen sind es zu wenig, werden neue gestartet, sind es zu viele werden Pods beendet, gruppiert durch den Label Selector

---

<strong>Für was können Deployments verwendet werden?</strong>

- Ermöglichen Deklarative Updates von Container Images in Pods.


