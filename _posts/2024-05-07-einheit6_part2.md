---
title: "Einheit 06B: Metadaten modellieren und Schnittstellen nutzen - Schnittstellen"
date: 2024-05-07
---

In diesem Beitrag geht es um die restlichen Inhalte des sechsten Unterrichtsblocks vom Nachmittag des 07.Mai (15:00 - 16:30). 

## Ausgangsdaten
![Schaubild aus dem Unterricht](\Lerntagebuch_BAIN\images\unterricht_schaubild.png)  
*Abb. 1: Schaubild aus dem Unterricht*  

## Schnittstellen

### Austauschprotokolle für Metadaten
Es gibt zahlreiche  Protokolle für die Übertragung von Metadaten. Im Rahmen des Unterrichts befassen wir uns jedoch vorwiegend mit [OAI-PMH](https://www.openarchives.org/pmh/). OAI-PMH eignet sich insbesondere für grössere Anfragen, da damit keine Suche nach Parametern möglich ist (zu diesem Zweck würde man eher SRU - Search/Retrieve cia URL verwenden). Ein Vorteil von OAI-PMH ist die Angabe eines Timestamps, so dass nur die geänderten Daten ab Zeitpunkt X geharvestet werden und man so einfache Aktualisierungen der Daten vornehmen kann, ohne jeweils die gesamte Datenmenge erneut harvesten zu müssen. 

### VuFindHarvest
Für die Übungen mit VuFindHarvest arbeiten wir wieder mit einem Codespace auf GitHub auf dem alles vorbereitet ist (Hier bin ich wirklich kurz reingefallen, weshalb ich keinen starten kann, weil ich zuerst selbst nicht in meinen GitHub Account eingeloggt war). Bei der Übung laden wir Datensätze aus der entsprechenden Demo-installation herunter, dazu müssen wir die Prefixes finden, um die Daten in den richtigen Formaten herunterzuladen.  

Der Prefix für den Import aus KOHA: --metadataPrefix=marc21  
Der Prefix für den Import aus ArchivesSpace: --metadataPrefix=oai_ead  
Der Prefix für den Import aus DSpace: --metadataPrefix=oai_dc  

![Import Daten aus ArchivesSpace](\Lerntagebuch_BAIN\images\Screenshot_vufindharvest_archivesspace.jpg)  
*Abb. 2: Erfolgreicher Datenimport aus ArchivesSpace*  

Da ich diese Unterrichteinheit nicht live mitverfolgt habe, sondern die Inhalte selbstständig, mit Hilfe der Aufnahme erarbeite, bin ich froh, dass diese Übungen gut funktioniert hat. 

## Konvertierung
Mit den heruntergeladenen Beispieldaten arbeiten wir nun weiter. Das Ziel der Übung soll es sein, die Daten aus den unterschiedlichen Datenformaten einheitlich in das Datenformat MARC21-XML zu konvertieren. Dieser Prozess wird in der Branche auch gerne als *Crosswalk* bezeichnet. Dazu gibt es Regeln welche definieren, wie die Elemente zugeordnet werden sollen (sog. Mapping). 

Ein Beispiel für ein solches Mapping von der Library of Congress: 

![Mapping MARC to DC](\Lerntagebuch_BAIN\images\Screenshot_marc_dc_mapping.jpg)  
*Abb. 3: Mapping für die Konventierung von MARC nach Dublin Core*  
(Quelle: [Library of Congress](https://www.loc.gov/marc/marc2dc.html))  

### MarcEdit
MarcEdit ist eine kostenlos nutzbare Software für die Durchführung von Crosswalks. Gerade für die Arbeit mit MARC21 ist sie die meistgenutzte Software.
Allerdings wird sie seit 1999 von einer Einzelperson gewartet und somit kann man nie recht wissen, wie lange das "gut geht" / wie lange diese Person das weiterzieht. 
Das Best-Case Szenario wäre wohl, dass der Entwickler, bevor er mit der Wartung aufhört, die Lizenz anpasst, dass die Software Open Source weitergeführt und aktualisiert werden könnte. Denn Stand jetzt darf die Software nur unverändert benutzt werden.

![MarcEdit License Agreement](\Lerntagebuch_BAIN\images\Screenshot_lizenz_marcedit.jpg)  
*Abb. 4: Endnutzer Lizenzvereinbarung der Software MarcEdit*  
(Quelle: [MarcEdit](https://marcedit.reeset.net/marcedit-end-user-license-agreement))  


### ETL Prozess
ETL steht für Extract, Transform und Load und bezeichnet einen Prozess zur Datenintegration, welcher Quell- und Zielsysteme miteinander verbindet. Der Begriff ist nicht nur in der Bibliotheks- und Archivbranche, sondern auch darüber hinaus in der IT gebräuchlich. Er besteht, wie der Name schon sagt, aus 3 Schritten:  
1. Extraktion: Die Daten werden aus einer Quelle extrahiert (oder geharvestet)  
2. Transformation: Die Daten werden in ein einheitliches Format konvertiert  
3. Laden: Die einheitlich transformierten Daten werden in das Zielsystem überführt  
(Quelle: [IT in Bibliotheken](https://it-in-bibliotheken.de/metadaten.html#etl-prozess))