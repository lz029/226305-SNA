# Datensatz zu Verbindungen von Vorstand und Aufsichtsrat bei VfB #
Codebuch Stand 2021-02-22   
erstellt von Lioba Zangenfeind (lz029@hdm-stuttgart.de)

## Inhalt
- PV-VfB-Edgelist.csv (Edgelist)
- PV-VfB-Nodelist (Nodelist)
- PV-VfB-Codebuch.rm (Codierung der Datensätze)

## Ursprung und Datenerhebung
Der Datensatz wurde durch Recherche der VfB-Vorstands- und Aufsichtsrats-Mitglieder und deren Verbindungen zu anderen Organisationen erhoben. Primäre Quelle dafür war https://www.vfb.de/de/1893/club/vfb-ag/organe-der-vfb-ag/

Das Netzwerk ist ein *ungerichtetes two-mode Netzwerk*, denn es geht sowohl um Personen als auch Organisationen.

**Netzwerk VfB**  
Alle aktiven Mitgliedschaften der Personen im Netzwerk


# EDGE-Attribute

**id**  
(eindeutige Codierung des Knoten)   
Codiert nach dem ersten Buchstaben des Vor- und Nachnamens bzw. den Anfangsbuchstaben jedes Wortes der Organisaton;   
jede ID entspricht einem Akteur im VfB-Netzwerk bzw. einer Organisation, in der mindestens einer der Akteure aktuell aktives Mitglied ist.

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

**role**    
Gibt die Funktion der Personen bei VfB an.     
V = Vorstand     
AR = Aufsichtsrat  
  
**representation**    
Gibt das Arbeitsfeld innerhalb der VfB-Gremien an, soweit bekannt. Jeweils die ersten drei Buchstaben der Arbeitsfelder stehen für das ganze Wort:     
spo = Sport     
fin = Finanzen   
kom = Kommunikation   
pol = Politik   
  
**position**    
Gibt die Position innerhalb der VfB-Organisation an.
vors = Vorsitz     
mitgl = Mitglied     
stellv = Stellvertreter
##
