# Datensatz zu Verbindungen von Vorstand und Aufsichtsrat bei VfB #
Codebuch Stand 2021-02-22   
erstellt von Lioba Zangenfeind (lz029@hdm-stuttgart.de)

## Inhalt
- Edges.csv (Edgelist)
- Nodes.csv (Nodelist)
- Codebuch.rm (Codierung der Datensätze)

## Ursprung und Datenerhebung
Der Datensatz wurde durch Recherche der VfB-Vorstands- und Aufsichtsrats-Mitglieder und deren Verbindungen zu anderen Organisationen erhoben. Primäre Quelle dafür war https://www.vfb.de/de/1893/club/vfb-ag/organe-der-vfb-ag/

Das Netzwerk ist ein *ungerichtetes two-mode Netzwerk*, denn es geht sowohl um Personen als auch Organisationen.

**Netzwerk vfb**  
Alle aktiven Mitgliedschaften der Personen im Netzwerk


# EDGE-Attribute

**id**  
(eindeutige Codierung des Knoten)   
Codiert nach dem ersten Buchstaben des Vor- und Nachnamens bzw den Anfangsbuchstaben der Organisaton, jede ID entspricht einem Akteur im VfB-Netzwerk bzw. einer Organisation, in der mindestens einer der Akteure aktuell aktives Mitglied ist.

Da das Netzwerk ungerichtet ist, erübrigen sich Kategorien wie *weight* etc.

# NODE-Attribute  
  
**id**  
Identische ID wie aus der edgelist zur Identifikation der Knoten.

**name**    
Namen der Personen und Organisationen, die im Netwerk vorkommen.
  
**type**    
Gibt an, ob es sich um eine Person oder eine Organisation handelt.   
0 = person    
1 = organization    


**age**   
Gibt das Alter der Personen (soweit bekannt) in natürlichen Zahlen an.     
Stand: 19.02.2021

**function**    
Gibt an, welche Funktion die Personen bei VfB haben.     
V = Vorstand     
AR = Aufsichtsrat  
  
**representation**    
Gibt die Funktion innerhalb der VfB-Gremien an.
- Mitglied Geschäftsleitung
- Vorsitz Aufsichtsrat
- Stellvertreter Vorsitz Aufsichtsrat
- Mitgleid Präsidium
- Mitglied Aufsichtsrat  

##
