
Infinite Monitoring Tool
====================================
Pflichtenheft
---

Fachhochschule Bielefeld

Campus Minden

Studiengang Informatik

---

Beteiligte Personen:

Name                   | Matrikelnummer
---------------------- | ---------------
Devin-Alexander Meier  | 1087170
Daniel Nagel           | 1085754

24.April 2018

---


Softwarespeziﬁkation
====================

Softwareanforderungen
---------------------
Skalierbares Monitoring Tool zur Überwachung von Servern über eine Weboberfläche.

Im Rahmen des Projektes soll eine Webanwendung entwickelt werden, welche relevante Informationen zu einem oder mehreren Servern darstellt. Eine Rich-Client-Webanwendung dient hier als Benutzerschnittstelle, eine Anwendung auf den zu überwachenden Servern liest alle nötigen Informationen aus und sendet diese an einen Webserver, welcher als Schnittstelle zwischen den überwachten Servern und der Webanwendung dient.

**Rich-Client-Webanwendung**

Die Rich-Client-Webanwendung soll alle Daten eines Servers möglichst detailliert darstellen, aber gleichzeitig die Zustände aller anderen verbundenen Server in einfacher Weise darstellen, etwa mittels eines Farbcodes (Grün ist Gut, Rot ist schlecht).

![Rich-Client-Webanwendung](rich-client-app.png "Rich-Client-Webanwendung")

**Datensammler**

Der Datensammler ist eine Anwendung welche auf einem zu überwachenden System zum Einsatz kommt. Dieser sammelt alle Relevanten Daten und sendet diese in regelmäßigen Zeitabständen an den Webserver.

**Webserver**

Der Webserver registriert neue Server und teilt dies dem Frontend mit. Neue Daten von bereits registrierten Servern werden an das Frontend zur Darstellung  weitergeleitet.

**Optionale Anforderungen**

 Die detaillierte Darstellung soll jederzeit an die eigenen Bedürfnisse angepasst werden können. Weiterhin sollen über die Weboberfläche die Datensammler erweitert werden könne, z.B. um Skripts welche Informationen spezieller Hardware auslesen, etwa ein Temperatursensor.

Funktionale Anforderungen | Nichtfunktionale Anforderungen
------------------------- | -------------------------------
**Rich-Client-Webanwendung** |
Konﬁgurierbarkeit der Anwendung. (o) | Selbsterklärende GUI der Anwendung.
Neu registrierte Server sollen ohne weiteres zu tun des Nutzers hinzugefügt werden. | Intuitive Darstellung der Informationen für einen schnellen Überblick für das wesentliche.
**Datensammler** |
Möglichst Ressourcenschonend. | Daten sollen in normalisierter Form weitergegeben werden.
Erweiterbarkeit (o) |
**Webserver** |
Registrieren neuer Server. |
Weiterleiten neuer Informationen an das Frontend. |

(o) - optional

----------

User Stories
------------
### Rich-Client-Webanwendung

* Als Benutzer möchte ich eine intuitive Oberfläche der Anwendung angezeigt bekommen, um keine Dokumentation lesen zu müssen.
* Als Benutzer möchte ich ein optisches Feedback zum Zustand der registrierten Server bekommen.
* Als Benutzer möchte ich Vorkonfigurierte Datensammler und Webanwendungen angeboten bekommen, um Zeit zu sparen.
* Als Benutzer möchte ich die Oberfläche verändern können, um diese an meine speziellen Bedürfnisse anzupassen.

### Datensammler

* Als Benutzer möchte ich den Datensammler direkt starten können, ohne diesen vorher noch konfigurieren zu müssen, um Zeit zu sparen.
* Als Benutzer möchte ich sicherstellen können das alle Informationen die ich brauche gesammelt werden, um keine interessanten Informationen zu verpassen.
* Als Benutzer möchte ich den Datensammler erweitern können, um spezielle Informationen sammeln zu können.
* Als überwachtes System möchte ich einen möglichst schlanken Datensammler haben, um keine wichtigen Ressourcen zu verlieren.

### Webserver

* Als Benutzer möchte ich eine automatische Verbindung zwischen Sammlern und Rich-Client-Webanwendung haben, um kein Zeit bei der Konfiguration zu verlieren.


----------

Use-Cases
---------

![Use-Case System](UseCases/Usecase_webanwendung.png "Use-Case System")

----------

Architekturdiagramm
-------------------

![Systemarchitektur](Systemarchitektur/Systemarchitektur.png "Systemarchitektur")

Das obige Diagramm stellt die Systemarchitektur dar. Auf der linken Seite des Diagramms wird die Rich-Client-Webanwendung über einen Webbrowser aufgerufen. Über das Netzwerk wird eine Verbindung mit dem Webserver hergestellt. Auf der rechten Seite befinden sich beliebig viele Server welche einen Datensammel Prozess laufen lassen. Der Webserver erkennt jeden Datensammel Prozess und gibt die Daten an die Rich-Client-Webanwendung zur Darstellung weiter.

Datenbankmodel
-------------------

### Webserver

![Datenbankmodel](ERD_Diagramme/WEB_DB.png "Datenbankmodel Web Service")

Das obige Diagramm zeigt das Schema der NoSQL Datenbank auf dem Webserver. Die Datenbank hält alte Daten zu je einem registrierten Server bereit für Analytische Zwecke und zum vergleichen der Daten über einen gewissen Zeitraum hinweg.
