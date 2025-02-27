---
title: 'Eine Failover-IP konfigurieren'
slug: failover-ip-konfigurieren-pci
excerpt: 'Erfahren Sie hier, wie Sie Failover-IPs in Ihre Instanzen einbinden'
section: Netzwerk und IP
order: 2
---

> [!primary]
> Diese Übersetzung wurde durch unseren Partner SYSTRAN automatisch erstellt. In manchen Fällen können ungenaue Formulierungen verwendet worden sein, z.B. bei der Beschriftung von Schaltflächen oder technischen Details. Bitte ziehen Sie beim geringsten Zweifel die englische oder französische Fassung der Anleitung zu Rate. Möchten Sie mithelfen, diese Übersetzung zu verbessern? Dann nutzen Sie dazu bitte den Button «Mitmachen» auf dieser Seite.
>

**Letzte Aktualisierung am 27.04.2021**

## Ziel

Es kann nowendig werden, Failover-IPs auf Ihren Instanzen konfigurieren, zum Beispiel, wenn Sie eine große Anzahl an Websites oder internationale Projekte hosten. Mit den Failover-IPs von OVHcloud können Sie mehrere IP-Adressen einem einzigen Netzwerkinterface zuweisen.

**In dieser Anleitung erfahren Sie, wie Sie Failover-IPs zu Ihrer Netzwerkkonfiguration hinzufügen.**

> [!warning]
> OVHcloud stellt Ihnen Dienstleistungen zur Verfügung, für die Sie die alleinige Verantwortung tragen. Da wir keinen Zugriff auf diese Dienste haben, können wir hierfür keinerlei Administrator-Aufgaben übernehmen oder sonstige Hilfeleistung anbieten. Es liegt daher in Ihrer Verantwortung, das Softwaremanagement und die tägliche Sicherheit zu gewährleisten.
>
> Wir stellen Ihnen diese Anleitung zur Verfügung, um Ihnen bei der Bewältigung alltäglicher Verwaltungsaufgaben zu helfen. Wir empfehlen Ihnen jedoch, sich an einen spezialisierten Dienstleister zu wenden, wenn Sie Schwierigkeiten oder Zweifel hinsichtlich der Verwaltung, Nutzung oder Sicherheit eines Dienstes haben. Sie können sich auch jederzeit an unsere [Community](https://community.ovh.com/en/) wenden, um sich mit anderen Benutzern auszutauschen.
>

## Voraussetzungen

- Sie haben eine [Public Cloud Instanz](https://www.ovhcloud.com/de/public-cloud/) in Ihrem OVHcloud Account.
- Sie verfügen über eine [Failover-IP](https://www.ovhcloud.com/de/bare-metal/ip/)-Adresse oder einen Failover-IP-Block.
- Sie haben administrativen Zugriff (Root) auf Ihre Instanz über SSH oder GUI. 
- Sie haben Grundkenntnisse in Administration und Netzwerkkonfiguration.

## In der praktischen Anwendung

Die folgenden Abschnitte enthalten die Konfigurationen für die am häufigsten verwendeten Distributionen/Betriebssysteme. Der erste Schritt ist immer die Anmeldung auf Ihrer Instanz über SSH oder einen GUI-Login (VNC für eine Windows-Instanz). Die folgenden Beispiele setzen voraus, dass Sie als Benutzer mit erhöhten Berechtigungen (Administrator/sudo) angemeldet sind.

> [!primary]
>
Bitte beachten Sie, dass sich bei unterschiedlichen Distributionen die korrekte Vorgehensweise zur Konfiguration Ihrer Netzwerkschnittstelle sowie die Dateinamen geändert haben können. Wir empfehlen Ihnen, bei Problemen die Dokumentationen und Wissensressourcen der jeweiligen Betriebssystemversionen zu konsultieren. 
>

**Bitte beachten Sie die Terminologie, die in den nachfolgenden Codebeispielen und Anweisungen dieser Anleitung verwendet wird:**

|Bezeichnung|Beschreibung|Beispiele|
|---|---|---|
|IP_FAILOVER|Ihrem Dienst zugewiesene Failover-IP|169.254.10.254|
|NETWORK_INTERFACE|Name des Netzwerkinterfaces|*eth*, *ens3*|
|ID|ID der Failover-IP, beginnend mit *0* (abhängig von der Anzahl der zu konfigurierenden zusätzlichen IP-Adressen)|*0*, *1*|

### Debian 10

#### Schritt 1: Automatische Netzwerkkonfiguration deaktivieren

Öffnen Sie diesen Dateipfad mit einem Texteditor:

```bash
sudo nano /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg
```

Fügen Sie die folgende Zeile ein, speichern Sie und schließen Sie dann den Editor.

```bash
network: {config: disabled}
```

Die Erstellung dieser Konfigurationsdatei verhindert die automatische Ausführung von Änderungen an der Konfiguration Ihres Netzwerks.

#### Schritt 2: Netzwerkkonfigurationsdatei bearbeiten

Um den Namen Ihres Netzwerkinterfaces zu überprüfen, verwenden Sie folgenden Befehl:

```bash
ip a
```

Öffnen Sie die Netzwerkkonfigurationsdatei zur Bearbeitung:

```bash
sudo nano /etc/network/interfaces.d/50-cloud-init
```

Fügen Sie folgende Zeilen hinzu:

```bash
auto NETWORK_INTERFACE:ID
iface NETWORK_INTERFACE:ID inet static
address IP_FAILOVER
netmask 255.255.255.255
```

#### Schritt 3: Interface neu starten

Wenden Sie die Änderungen mit folgendem Befehl an:

```bash
sudo systemctl restart networking
```

### Ubuntu 20.04

Die Konfigurationsdatei für Ihre Failover-IPs befindet sich in `/etc/netplan/`. In diesem Beispiel heißt sie "50-cloud-init.yaml". Bevor Sie Änderungen vornehmen, überprüfen Sie am besten den tatsächlichen Dateinamen in diesem Ordner. Jede Failover-IP benötigt in der Datei eine eigene Zeile.

#### Schritt 1: Automatische Netzwerkkonfiguration deaktivieren

Öffnen Sie diesen Dateipfad mit einem Texteditor:

```bash
sudo nano /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg
```

Fügen Sie die folgende Zeile ein, speichern Sie und schließen Sie dann den Editor.

```bash
network: {config: disabled}
```

Die Erstellung dieser Konfigurationsdatei verhindert die automatische Ausführung von Änderungen an der Konfiguration Ihres Netzwerks.

#### Schritt 2: Konfigurationsdatei bearbeiten

Um den Namen Ihres Netzwerkinterfaces zu überprüfen, verwenden Sie folgenden Befehl:

```bash
ip a
```

Öffnen Sie die Netzwerkkonfigurationsdatei zur Bearbeitung:

```bash
sudo nano /etc/netplan/50-cloud-init.yaml
```

Ändern Sie nicht die vorhandenen Zeilen in der Datei; fügen Sie Ihre Failover-IP wie folgt hinzu:

```yaml
network:
    version: 2
    ethernets:
        NETWORK_INTERFACE:
            dhcp4: true
            match:
                macaddress: fa:xx:xx:xx:xx:63
            set-name: NETWORK_INTERFACE
            addresses:
            - IP_FAILOVER/32
```

> [!warning]
>
> Es ist wichtig, dass die Zeilenausrichtung jedes Elements dieser Datei, wie im Beispiel dargestellt, eingehalten wird. Verwenden Sie nicht die Tabulationstaste, um den Abstand zu erzeugen.
>

Speichern und schließen Sie die Datei.

#### Schritt 3: Neue Netzwerkkonfiguration anwenden

Sie können Ihre Konfiguration mit folgendem Befehl testen:

```bash
sudo netplan try
```

Ist die Änderung korrekt, verwenden Sie folgenden Befehl, um sie anzuwenden:

```bash
sudo netplan apply
```

Wiederholen Sie diesen Vorgang für jede Failover-IP.

### Windows Server (2016)

Loggen Sie sich in Ihrem [OVHcloud Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de) ein. Gehen Sie zum Bereich  `Public Cloud`{.action} und wählen Sie Ihr Projekt aus.

Öffnen Sie im linken Menü `Instances`{.action} und klicken Sie dann auf den Namen der betreffenden Instanz. Wechseln Sie zum Tab `VNC Konsole`{.action}.

#### Schritt 1: Netzwerkkonfiguration überprüfen

Klicken Sie mit der rechten Maustaste auf das `Startmenü`{.action} und öffnen Sie `Ausführen`{.action}.

Geben Sie `cmd` ein und klicken Sie auf `OK`{.action}, um die Kommandozeilenanwendung zu öffnen.

![cmdprompt](images/pci_win07.png){.thumbnail}

Um die aktuelle IP-Konfiguration anzuzeigen, geben Sie `ipconfig` in der Eingabeaufforderung ein.

![IP-Konfiguration überprüfen](images/image1-1.png){.thumbnail}

#### Schritt 2: IPv4 Eigenschaften ändern

Die IP-Eigenschaften müssen nun zu einer statischen Konfiguration geändert werden.

Öffnen Sie die Adaptereinstellungen in der Windows-Systemsteuerung und öffnen Sie die `Eigenschaften`{.action} von `Internet Protocol Version 4 (TCP/IPv4)`{.action}.

![IP-Konfiguration ändern](images/image2.png){.thumbnail}

Wählen Sie in den IPv4-Eigenschaften `Folgende IP-Adresse verwenden`{.action}. Geben Sie die IP-Adresse ein, die Sie im ersten Schritt ausgelesen haben, und klicken Sie dann auf `Erweitert`{.action}.

#### Schritt 3: Die Failover-IP in "Erweiterte TCP/IP Einstellungen" hinzufügen

Klicken Sie im neuen Fenster auf `Hinzufügen...`{.action} unter "IP-Adressen". Geben Sie Ihre Failover-IP und die Subnetzmaske (255.255.255.255) ein.

![Konfiguration](images/image4-4.png){.thumbnail}

Bestätigen Sie, indem Sie auf `Hinzufügen`{.action} klicken.

![Konfiguration Failover-IP](images/image5-5.png){.thumbnail}

#### Schritt 4: Netzwerk-Interface neu starten

Wieder in der Systemsteuerung (`Netzwerkverbindungen`{.action}), klicken Sie mit der rechten Maustaste auf Ihr Netzwerkinterface und wählen Sie `Deaktivieren`{.action}.

![Netzwerkdeaktivierung](images/image6.png){.thumbnail}

Um es neu zu starten klicken Sie mit der rechten Maustaste darauf und wählen Sie `Aktivieren`{.action}.

![Netzwerkaktivierung](images/image7.png){.thumbnail}

#### Schritt 5: Überprüfung der neuen Netzwerkkonfiguration

Öffnen Sie die Eingabeaufforderung (cmd) und geben Sie `ipconfig` ein. Die Konfiguration sollte nun die neue Failover-IP enthalten.

![Aktuelle Netzwerkkonfiguration überprüfen](images/image8-8.png){.thumbnail}

### cPanel (CentOS 7) / RedHat Derivate

#### Schritt 1: Netzwerkkonfigurationsdatei bearbeiten

Um den Namen Ihres Netzwerkinterfaces zu überprüfen, verwenden Sie folgenden Befehl:

```bash
ip a
```

Öffnen Sie die Netzwerkkonfigurationsdatei zur Bearbeitung:

```bash
sudo nano /etc/sysconfig/network-scripts/ifcfg-NETWORK_INTERFACE:ID
```

Fügen Sie folgende Zeilen hinzu:

```bash
DEVICE=NETWORK_INTERFACE:ID
BOOTPROTO=static
IPADDR=IP_FAILOVER
NETMASK=255.255.255.255
BROADCAST=IP_FAILOVER
ONBOOT=yes
```

#### Schritt 2: Interface neu starten

Wenden Sie die Änderungen mit folgendem Befehl an:

```bash
sudo systemctl restart networking
```

### Plesk

#### Schritt 1: Auf die IP-Verwaltung von Plesk zugreifen

Wählen Sie im Plesk Konfigurationspanel `Tools & Settings`{.action} im linken Menü aus.

![Zugang zur Verwaltung der IP-Adressen](images/pleskip1.png){.thumbnail}

Klicken Sie auf `IP Addresses`{.action} unter **Tools & Resources**.

#### Schritt 2: Die zusätzliche IP-Information hinzufügen

Klicken Sie in diesem Abschnitt auf den Button `Add IP Address`{.action}.

![IP-Informationen hinzufügen](images/pleskip2-2.png){.thumbnail}

Geben Sie Ihre Failover-IP in der Form `xxx.xxx.xxx.xxx/32` in das Feld "IP address and subnet mask" ein und klicken Sie dann auf `OK`{.action}.

![IP-Informationen hinzufügen](images/pleskip3-3.png){.thumbnail}

#### Schritt 3: Aktuelle IP-Konfiguration überprüfen

Überprüfen Sie im Bereich "IP Addresses" ob die Failover-IP korrekt hinzugefügt wurde.

![aktuelle IP-Konfiguration](images/pleskip4-4.png){.thumbnail}

### Diagnose

Starten Sie zunächst Ihre Instanz neu, über das Betriebssystem oder im [OVHcloud Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de). Wenn Sie dann immer noch keine Verbindung zwischen dem öffentlichen Netzwerk und Ihrer Failover-IP-Adresse herstellen können und ein Netzwerkproblem vermuten, ist es notwendig, die Instanz im [Rescue-Modus neu zu starten](../umstellung_einer_instanz_auf_den_rescue-modus/). Anschließend können Sie die Failover-IP direkt auf der Instanz konfigurieren.

Wenn Sie über SSH im Rescue-Modus eingeloggt sind, geben Sie folgenden Befehl ein:

```bash
ifconfig ens3:0 IP_FAILOVER netmask 255.255.255.255 broadcast IP_FAILOVER up
```

Um die Verbindung zu testen senden Sie einfach von außerhalb einen Ping an Ihre Failover-IP. Wenn sie im Rescue-Modus antwortet, bedeutet dies wahrscheinlich, dass ein Konfigurationsfehler vorliegt. Wenn die IP jedoch noch nach wie vor nicht funktioniert, informieren Sie bitte unsere Support-Teams, indem Sie ein Support-Ticket über Ihr [OVHcloud Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de) erstellen.

## Weiterführende Informationen

[Failover-IP importieren](../import_einer_failover-ip/)

[Wechsel einer Failover-IP](../umzug_einer_failover-ip/)

Für den Austausch mit unserer User Community gehen Sie auf <https://community.ovh.com/en/>
