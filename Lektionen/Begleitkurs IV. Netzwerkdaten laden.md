# Netzwerkdaten laden und importieren
# Daten einlesen
# Beispiel Wohlleben-Datensatz

# Variante 1: mit lokalen Dateien arbeiten

# Laden Sie sich zunächst die Edgelist (wohl_edge_csv) und die Nodelist (wohl_node) von GitHub oder Moodle herunter und speichern Sie die Dateien in Ihrem Working Directory.

library(igraph)

edges <- read.csv("wohl_edge.csv", header=T, as.is=T) # Liest die Edgelist ein und ordnet sie der Variablen edges zu.
edges # Zeigt die Daten aus der CSV Datei in der Konsole an.
head(edges) # Zeigt lediglich die ersten Zeilen des Datensatzes an.

nodes <- read.csv("wohl_node.csv", header=T, as.is=T) # Liest die Nodelist ein und ordnet sie der Variablen nodes zu.
nodes # Zeigt die Daten aus der CSV Datei in der Konsole an.
head(nodes) # Zeigt lediglich die ersten Zeilen des Datensatzes an.

# Die Edgelist liegt als Data frame vor. Um ein igraph Objekt definieren zu können, muss die Edgelist jedoch als Matrix vorliegen.

ties <- as.matrix(edges) # Wandelt die Edgelist in eine Matrix um und ordnet sie der Variablen ties zu.

# Jetzt können wir ein igraph Objekt erstellen. Wenn wir die Nodelist nicht miteinbeziehen wollen, nutzen wir den folgenden Befehl.

wohled <- graph_from_edgelist(ties, directed=FALSE) # Das Wohlleben Netzwerk ist ungerichtet. Wäre es gerichtet, stünde nach directed TRUE. Der Variablenname setzt sich zur besseren Wiedererkennung aus wohl[leben] und ed[gelist] zusammen.

wohled # Zeigt das igraph Objekt wohled an.

# Wollen wir ein igraph Objekt erstellen, das die Daten der Nodelist integriert, nutzen wir den folgenden Befehl.

wohledno <- graph_from_data_frame(d=ties, vertices=nodes, directed=F) # Wohl[leben], ed[gelist] und no[delist]. Man kann den Namen der Variable natürlich frei wählen.

# Beide Netzwerke können visualisiert werden.

plot(wohled,
     vertex.size=degree(wohled),
     vertex.label=NA,
     edge.arrow.size=0.2,
     main="Netzwerk (nur Edgelist)")

plot(wohledno,
     vertex.size=degree(wohledno),
     vertex.label=NA,
     edge.arrow.size=0.2,
     main="Netzwerk mit Nodelist")

# Sie sehen genau gleich aus. Aber zwischen ihnen besteht ein Unterschied. Wir dürfen nicht vergessen, dass wohledno viel mehr Daten (aus der integrierten Nodelist) liefert. Das sieht man anhand des folgenden Befehls.

list.vertex.attributes(wohled)
list.vertex.attributes(wohledno)

# Lassen wir uns nämlich die Knotenattribute auflisten, sehen wir, dass wohledno natürlich viel mehr Attribute besitzt, da es überhaupt eine Nodelist gibt.

################################
# Variante 2: Daten auf github #
################################

# Wesentlich einfacher ist es, wenn die Dateien bereits auf einem github zur Verfügung stehen. Dann lassen Sie sich einfach aus den RAW-Daten einlesen.

library(igraph)

edges <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/wohlleben/wohl_edge.csv", header=T, as.is=T)
nodes <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/wohlleben/wohl_node.csv", header=T, as.is=T) # Liest die Nodelist
ties <- as.matrix(edges)
wohledno <- graph_from_data_frame(d=ties, vertices=nodes, directed=T)

plot(wohledno,
     vertex.size=degree(wohledno),
     vertex.label=NA,
     edge.arrow.size=0.2,
     main="Netzwerk mit Nodelist")


### Für Fortgeschrittene

# Mit dem Informationen der Nodelist können wir in wohledno die Personen und Organisationen unterschiedlich visualisieren.

V(wohledno)[V(wohledno)$type == 1]$shape <- "square" # Alle Knoten, die beim Attribut type den Wert 1 annehmen, werden als Quadrat dargestellt.

V(wohledno)[V(wohledno)$type == 0]$shape <- "circle" # Alle Knoten, die beim Attribut type den Wert 0 annehmen, werden als Kreis dargestellt.

plot(wohledno,
     vertex.size=degree(wohledno, mode="in"),
     vertex.label=NA,
     edge.arrow.size=0.2,
     main="Netzwerk: Wer verbindet die Knoten?",
     sub="Größe der Knoten Indegrees")

# Wie man sieht, lohnt es sich oft, eine Nodelist zu importieren, wenn die Daten einen Mehrwert bieten.

---
title: "226305 Datenimport Beispiel Wohlleben"
author: "Swaran Sandhu"
date: "24 11 2020"
output: html_document
---


```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
# diesen Chunk stehen lassen und ignorieren ;-)
```


# Netzwerkdaten laden und importieren
## Daten einlesen
## Beispiel Wohlleben-Datensatz

Der Wohlleben-Datensatz beschreibt das Netzwerk von Ralf Wohlleben. Wohlleben ist bekennender Neonazi aus Tühringen, der mit dem NSU verbunden ist (https://de.wikipedia.org/wiki/Ralf_Wohlleben)


############################################
# Variante 1: mit lokalen Dateien arbeiten #
############################################

Laden Sie sich zunächst die Edgelist (wohl_edge_csv) und die Nodelist (wohl_node) von GitHub oder Moodle herunter und speichern Sie die Dateien in Ihrem Working Directory.

Die Dateien liegen unter
https://github.com/hdm-crpr/226305/tree/master/data/wohlleben

Bitte beachten Sie, dass Sie jeweils die raw-Dateien speichern müssen
1) Edgelist
https://raw.githubusercontent.com/hdm-crpr/226305/master/data/wohlleben/wohl_edge.csv
2) Nodelist
https://raw.githubusercontent.com/hdm-crpr/226305/master/data/wohlleben/wohl_node.csv

Die Edgelist beschreibt die Beziehungen von Wohlleben zu Personen und Organisationen, die Edgelist ist codiert nach 
id = eindeutige ID
label = Bezeichnung für die ID
art = Person oder Organisation
geschlecht = female, male, NA
zweck = ARt der Beziehung 
type = identisch zu art für two-mode Netzwerke 

Sie müssen die Dateien als 


```{r Datensatz lokal einlesen}
library(igraph)

# WICHTIG: Die Dateien müssen zuvor heruntergeladen und in der Working-Directory abgelegt werden: einfacher ist der Link auf die RAW-Dateien

edges <- read.csv("wohl_edge.csv", header=T, as.is=T) 
# Liest die Edgelist ein und ordnet sie der Variablen edges zu.

edges # Zeigt die Daten aus der CSV Datei in der Konsole an.
head(edges) # Zeigt lediglich die ersten Zeilen des Datensatzes an.

# Liest die Nodelist ein und ordnet sie der Variablen nodes zu.
nodes <- read.csv("wohl_node.csv", header=T, as.is=T) 
nodes # Zeigt die Daten aus der CSV Datei in der Konsole an.
head(nodes) # Zeigt lediglich die ersten Zeilen des Datensatzes an.

# Die Edgelist liegt als Data frame vor. Um ein igraph Objekt definieren zu können, muss die Edgelist jedoch als Matrix vorliegen.

ties <- as.matrix(edges) 
# Wandelt die Edgelist in eine Matrix um und ordnet sie der Variablen ties zu.

# Jetzt können wir ein igraph Objekt erstellen. Wenn wir die Nodelist nicht miteinbeziehen wollen, nutzen wir den folgenden Befehl.

wohled <- graph_from_edgelist(ties, directed=FALSE) 
# Das Wohlleben Netzwerk ist ungerichtet. Wäre es gerichtet, stünde nach directed TRUE. Der Variablenname setzt sich zur besseren Wiedererkennung aus wohl[leben] und ed[gelist] zusammen.

wohled 
# Zeigt das igraph Objekt wohled an.
# Hier werden noch keine Informationen aus der Nodelist verarbeitet.

# Wollen wir ein igraph Objekt erstellen, das die Daten der Nodelist integriert, nutzen wir den folgenden Befehl.

wohledno <- graph_from_data_frame(d=ties, vertices=nodes, directed=F) 
# Wohl[leben], ed[gelist] und no[delist]. 
# Man kann den Namen der Variable natürlich frei wählen.

```



################################
# Variante 2: Daten auf github #
################################

Wesentlich einfacher ist es, wenn die Dateien bereits auf einem github zur Verfügung stehen. Dann lassen Sie sich einfach aus den RAW-Daten einlesen.

```{r Einlesen aus github-Account, fig.height=6, fig.width=10}

library(igraph)

edges <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/wohlleben/wohl_edge.csv", header=T, as.is=T)

nodes <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/wohlleben/wohl_node.csv", header=T, as.is=T) 

ties <- as.matrix(edges)

# erstellt das igraph-Objekt aus Edge- und Nodelist
wohledno <- graph_from_data_frame(d=ties, vertices=nodes, directed=T)

plot(wohledno,
     layout=layout_with_kk,
     vertex.size=degree(wohledno), # berechnet die Knotengröße
     vertex.label=NA,
     edge.arrow.size=0.2,
     main="Wohlleben Netzwerk",
     sub="Knotengröße nach Zentralität der Knoten")
```



## Details visualisieren

Mit dem Informationen der Nodelist können wir in wohledno die Personen und Organisationen unterschiedlich visualisieren.

```{r Two-Mode Netzwerk visualisieren, fig.height=6, fig.width=10}

# Alle Knoten, die beim Attribut type den Wert 1 annehmen, werden als Quadrat dargestellt.
V(wohledno)[V(wohledno)$type == 1]$shape <- "square" 

# Alle Knoten, die beim Attribut type den Wert 0 annehmen, werden als Kreis dargestellt.
V(wohledno)[V(wohledno)$type == 0]$shape <- "circle" 

plot(wohledno,
     layout=layout_with_kk,
     vertex.size=degree(wohledno, mode="in"),
     vertex.label=NA,
     edge.arrow.size=0.2,
     main="Netzwerk: Welche Organisationen verbinden die Knoten?",
     sub="Größe der Knoten nach Indegrees")

# Wie man sieht, lohnt es sich oft, eine Nodelist zu importieren, wenn die Daten einen Mehrwert bieten.
```




