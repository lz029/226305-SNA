# Netzwerk Indie-Kollaborationen #
Codebuch Stand 2021-03-08   
erstellt von Gruppe Indie (ss502@hdm-stuttgart.de)

**Titel des Netzwerks:**
Verbindungen von Indie-Bands 2015-2020

## Inhalt
- INDIE-Edgelist.csv (Edgelist)
- INDIE-Nodelist.csv (Nodelist)
- INDIE-Codebuch.rm (Codierung der Datensätze)

## Ursprung und Datenerhebung

Es werden Kollaborationen vom 01.01.2015 bis 31.12.2020 erfasst.

Das Netzwerk ist ein *ungerichtetes one-mode Akteursnetzwerk*.

# EDGE-Attribute

**id**  
(eindeutige Codierung des Knoten)   
codiert nach den ersten vier Buchstaben der Künstler:innen und Bands, jede ID entspricht einem/einer Künstler:in bzw. Band

**weight**  
Beziehungsstärke   
4 = Feature (Gemeinsamer Song)  
3 = Gemeinsam auf Tour / gemeinsame Auftritte / Support  
2 = gemeinsames Musiklabel  
1 = Selbes Festival  

**time**  
Jahreszahl der Kooperation als YYYY

**source**  
Informationsquelle zu der Kooperation

**what**  
Art der Kooperation 

# NODE-Attribute  
  
**id**  
Identische ID wie aus der Edgelist zur Identifikation der Knoten

**name**  
Name des/der Künstler:in bzw. Band

**personen**  
Anzahl der Mitglieder

**musiklabel**  
Aktuelles und frühere Musiklabel der Band bzw. Künster:in

**instagram**  
Anzahl der Instagram-Follower:innen zum Stichtag 07.03.2021 in Tausend

**spotify**  
Monatliche Hörer:innen auf Spotify zum Stichtag 07.03.2021 in Tausend

##

