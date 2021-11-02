# Werkstattauftrag W08 OwnCloud

## Autoren, Versionierung des Dokumentes

   • Autoren: Altin Maliqaj & Patrik Pribela
   
   • Mail: altin.maliqaj@edu.tbz.ch | patrik.pribela@edu.tbz.ch

   • Version: 2.0 (Didaktisch reduzierte Edition)
   ---
## Einführung
In der folgenden Dokumentation ist die Installation, sowie Konfiguration samt allen Anforderungen von OwnCloud dokumentiert.

   ### Beschreibung: Welche Funktionen wird der Service erfuellen
   OwnCloud ist Ihre eine eigene private Cloud zum Austausch von Dateien. Die wichtigsten Features und Funktionen von OwnCloud sind die Bereitstellung von Clients, Synchronisation, ActiveDirectory-Anbindung, Verschlüsselung und viele andere. Es wird angestrebt diese auf allen Plattformen betreiben zu können.

   #### OwnCloud Infinite Scale
   Das Ziel bei der Entwicklung der neuen OwnCloud Instanz ist die **unendliche Skalierung**, daher der Name.
   **Unendliche Skalierung** bedeutet eine unendliche Anzahl von Dateien, Benutzern und Maschinen sowie unendliche Dateigrößen. Diese wird in Go geschreiben, was OwnCloud plattformunabhängig macht. OwnCloud Infinite Scale benötigt weder Apache noch eine PHP-Infrastruktur und ist damit die am einfachsten zu bedienende und am leichtesten zu implementierbare OwnCloud aller Zeiten. Diese ist natürlich Open Source, lizenziert unter Apache 2.0. Es werden Microservices verwendet und eine dreistufige Architektur, was OwnCloud zu einer sicheren, cloud-nativen Lösung für Dateizugriffsanforderungen macht. Einige weltweit bekannte Forschungsinstitute sind an der Entwicklung von OwnCloud Infinite Scale beteiligt und stellen sicher, dass es ihre und Ihre Möglichkeiten erweitert, indem es eine beispiellose Skalierung bietet.

   ### Vorgesehener Zeitaufwand für die Realisierung
   Der Zeitaufwand beträgt unserer Schätzung nach 60 Minuten im Durchschnitt. Die Schätzung kann wegen Hardware-Build, Software-Version und Netzwerkanbindung abweichen.

   ### Stolpersteine
   Bei folgendem Projekt können mehrere **Stolpersteine** aufkommen, welche uns, sowie anschliessend Sie an einer erfolgreichen Umsetzung hindern können oder diese zumindest erschweren können. Um den gägnigsten **Stolpersteinen** aus dem Weg gehen zu können, wurden diese aufgelistet.<br><br>
   **• Veraltete Version des Raspberry Pi**<br>
   Falls sich der Raspberry Pi nicht aktualisieren lässt und/oder die Hardware veraltet ist, kann (muss nicht!) es vorkommen, dass es zu Problemen bezüglich Kompatibilität führt. Wir empfehlen in einem solchen Fall eine virtuelle Maschine zu erstellen und das Raspbian OS aufzusetzen.<br>
   **• Restriktionen des (TBZ) Netzwerks**<br>
   Da öffentliche Netzwerke oft viele Sicherheitsmassnahmen eingepflegt erhalten, besteht die Möglichkeit, dass immer wieder Ports, welche essentiell für eine Anwendung sind, blockiert werden. Es gilt die Empfehlung bei Home Office Möglichkeit diese zu nutzen und aus dem Heimnetzwerk aus zu arbeiten.<br>
   - - -
## Benötigte Hard- und Software
   ### Hardware (Materialliste, Funktionalitaet)
   • Raspberry Pi<br>
   • Monitor + Peripherie (Maus und Tastatur)<br>
   • ggf. Netzwerkperipherie (Kabel, Switch)
   ### Software (Anforderungen, Firmware, OS-Image, ergaenzende SW-Packages, Abhängigkeiten, Funktionalitaet)
   • Neuste OS Version von Raspberry Pi inkl. Updates<br>
- - -
## Installationsanleitung (Didaktisch reduzierte Anleitung. Lernende sollen eigene Lösungswege realisieren)
### Raspberry Pi Betriebssystem updatend <br>
• Nach dem Erhalt der SD Karte von der Lehrperson muss als erstes die Paketliste aktualisiert werden<br>

### etcd installieren
• Vorraussetzung für die Installation vom OwnCloud Dienst ist der etcd. Finden Sie im Internet heraus, warum dieser so wichtig ist und wie man ihn korrekt installiert.<br>
• Nach der Installation kommt man zur Konfiguration. Fügen Sie folgende Zeile in der Konfigurationsdatei, welche unter `/etc/default/etcd` zu finden ist: `ETCD_UNSUPPORTED_ARCH=arm`<br>
• Zu guter letzt muss nur noch der Service gestartet werden: `sudo service etcd start` 

### Owncloud Infinite Scale Binary herunterladen und ausführen

Als erstes muss man den Build vom Downloadserver herunterladen:<br>
`curl https://download.owncloud.com/ocis/ocis/1.1.0/ocis-1.1.0-linux-arm --output ocis-1.1.0-linux-arm`<br>

Anschliessend muss der Build ausgeführt werden. Bei Bedarf von Hilfe im Abschnitt Hilfestellung nachschauen.

Nun muss man ein Skript erstellen, welches die OwnCloud Instanz startet. Dem Skript muss mitgegeben werden, dass etcd verwendet werden muss.

![startocis.sh](/img/startocis.png)

Das eben erstellt Skript ist noch ein normales Textdokument und muss ausführbar gemacht werden. Finden Sie im Internet heraus, wie Sie ein Textdokument ausfürhbar machen können.

Zum Schluss muss nur noch das Skript gestartet werden.

## Zugreifen

Die Installation und Konfiguration ist abgeschlossen. Sie können nun wie folgt auf das Web-Interface zugreifen: `https://<hostname>:9200`



### Hilfestellung (Tipps, Quellen...)

Um den Build auszuführen gibt man folgenden Befehl ein: `chmod 755` und das gewünschte Programm (in unserem Fall `./ocis-1.1.0-linux-arm`)

Tipp um Skripts ausführbar zu machen: `sudo chmod 755`

Skripts können ausgeführt werden, indem man sudo und den Skriptnamen im Terminal eingibt.

## Qualitätskontrolle (Prüfen der Funktionalität mit Ablauf von Kommandos und entsprechenden Outputs)
- - -
## Error-Handling
Falls die Installation am Ende nicht ordnungsgemäss funktioniert, kann dies mehrere Gründe haben. Weiter unten finden Sie die gängigsten Fehler aufgelistet.
### Allgemeine Schritte vor weiterem Debugging zwingend ausführen
• Raspberry Pi neu starten<br>
• Prüfen, ob der Dienst der Anwendung läuft<br>
• Netzwerkverbindung prüfen<br>
• Restriktionen im Netzwerk ausschliessen
- - -
## Quellen
• [Offizielle Installationsanleitung von OwnCloud](https://owncloud.com/de/news/howto-owncloud-infinite-scale-on-a-raspberry-pi/)<br>
• 
- - -
