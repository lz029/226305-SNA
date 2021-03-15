---
title: "226305 Netzwerkattribute und -selektion"
author: "Swaran Sandhu"
date: "4 12 2020"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = FALSE)
library(igraph)
```


# Beispiel Netzwerkselektion

## Datensatz Studierendennetzwerk
Codebuch: 
https://github.com/hdm-crpr/226305/blob/master/data/crpr2/codebuch.md
Edgelist:
https://github.com/hdm-crpr/226305/blob/master/data/crpr2/edges.csv
Nodelist:
https://github.com/hdm-crpr/226305/blob/master/data/crpr2/nodes.csv

## Fragestellung
Uns interessiert jetzt ein das weibliche Unterstützungsnetzwerk von Personen, sich sich stark unterstützen und die über 23 Jahre alt sind. Wie sieht die Beziehung zwischen diesen Personen aus?

## Schritt 1: Datensatz einlesen
```{r Datensatz einlesen, fig.height=6, fig.width=10}
# 0 Einlesen des Datensatzes

library(igraph)

el <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/edges.csv", header=T, as.is=T, sep = ",")
nodes <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/nodes.csv", header=T, as.is=T, sep = ",")
edgematrix <-as.matrix(el)
s <- graph_from_data_frame(d=edgematrix, vertices=nodes, directed=T)
s

list.vertex.attributes(s)

plot(s,
     main="Gesamtnetzwerk")

# Vertex-Attribute zur schöneren Visualisierung festlegen

V(s)$color <- "gold"
V(s)$frame.color <- "NA"
V(s)$vertex.size <- 2
E(s)$arrow.size <- .2
E(s)$color <- "black"

plot(s,
     main="Gesamtnetzwerk")

list.vertex.attributes(s)
```

## Schritt 2: Datensatz verstehen
```{r Attribute des Netzwerks anzeigen}
list.vertex.attributes(s)
list.edge.attributes(s)
```

## Schritt 3: Selektion nach Unterstützungsnetzwerk
```{r Selektion nach Edge-Attributen}
help <- subgraph.edges(s, E(s)[relation==2]) 
help
plot(help,
     main="Hilfsnetzwerk")
```

## Schritt 4: Selektion nach starken Unterstützern
```{r Selektion nach Edge-Attributen}
help_strong <- subgraph.edges(help, E(help)[weight==3])
help_strong
plot(help_strong,
     main="starke Unterstützung")
```

## Schritt 5: Selektion nach Geschlecht weiblich
```{r Selektion nach Vertex-Attribut}
list.vertex.attributes(help_strong)
vertex.attributes(help_strong)$sex

fem <- delete_vertices(help_strong, V(help_strong)[sex != "1"])
fem

plot(fem,
     layout=layout_with_kk,
     main="Unterstützungsnetzwerk weiblich",
     edge.color="grey80",
     edge.arrow.size=.3,
     vertex.color="pink",
     sub="weiblich, starke Beziehung")
```

## Schritt 6: Selektion nach Alter über 23

```{r Selektion nach Vertex-Attribut "age}
list.vertex.attributes(fem)
vertex.attributes(fem)$age

fem_old <- delete_vertices(fem, V(fem)[age < "3"])
fem_old

plot(fem_old, layout=layout_with_kk,
     main="Unterstützungsnetzwerk weiblich (fem_old)",
     edge.color="grey80",
     edge.arrow.size=.3,
     vertex.color="pink",
     sub="weiblich, Alter über 23, starke Beziehung")
```


# Interpretation
Es zeigt sich, dass nur eine (reziproke) Beziehung beim weiblichen Unterstützungsnetzwerk der über 23-jährigen übrig bleibt, nämlich zwischen Knoten 38 und 29. Um diese Dyade besser darzustellen können alle isolates, also Knoten, die nicht miteinander verbunden sind, gelöscht werden.

# Bessere Darstellung: Isolates löschen
Der Befehl delete.vertices löscht alle Knoten aus dem Netzwerk fem_old, die einen degree-Wert von 0 haben, also mit keinem anderen Knoten verbunden sind. 

```{r Isolates löschen}
fem_old2 <- delete.vertices(fem_old, degree(fem_old)==0)
fem_old2

plot(fem_old2, layout=layout_with_kk,
     main="Dyade ohne Isolates ",
     edge.arrow.size=.7,
     edge.width=E(s)$weight,
     edge.color="pink",
     vertex.size=30,
     vertex.color="pink",
     vertex.frame.color="black",
     vertex.frame.color="white",
     vertex.label.color="black",
     sub="Dyade zweier Frauen über 23, die sich gegenseitig stark unterstützen")
```
---
title: "226305 Netzwerkattribute und -selektion"
author: "Swaran Sandhu"
date: "4 12 2020"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = FALSE)
```

## Anleitung

**Worum geht es?**
In diesem Markdown-Dokument lernen Sie, wie man mit R und dem Paket igraph Netzwerkdaten einliest und bereits einfache Visualisierungen erstellt. Grundlagen dafür ist ein studentisches Netzwerk eines Semesters, das verschiedene Beziehungsmuster hat.

**Was brauche ich?**
- aktuelle Installation von R und RStudio  
- Datensatz mit Edge- und Nodelist  
- Codebuch des Datensatzes unter https://github.com/hdm-crpr/226305/blob/master/data/crpr2/codebuch.md 

**Wozu brauche ich das?**
Für jede Analyse ist es wichtig, den Datensatz und die entsprechenden Attribute genau zu verstehen.

**Konventionen**
Für jede Aufgabe erhalten Sie ein Beispiel. Der R-Code ist dabei *kursiv* dargestellt. Dann erhalten Sie eine **Übungsaufgabe**, die sie direkt im Terminal ausführen können. Manchmal ist der Code bereits voreingestellt und Sie nur ein paar Variablen austauschen. Bei anderen Aufgaben müssen Sie den Code selbst schreiben oder mehrere Teilschritte miteinander verbinden. Ab und an gibt es auch eine kleine Hilfestellung, die Sie abrufen können, wenn Sie nicht mehr weiterkommen. Bitte machen Sie die nächste Aufgabe nur dann, wenn Sie die vorherige verstanden und richtig abgeschlossen haben.

Wenn nachfolgend Befehle beschreiben werden, dann wird *g* als Platzhalter für das igraph-Objekt behandelt, *plot(g)* erstellt also den Plot des igraph-Objekts *g*. Achten Sie darauf, dass die Referenzierung immer sauber durchgeführt ist, v.a. wenn neue Teilnetzwerke erstellt wurden.

*Achtung*: 
R ist kontext-sensitiv, achten Sie deshalb bitte auf die korrekte Schreibweise der Befehle und Dateien, die Art der Klammern und deren Schließung und die entsprechenden Zeichen innerhalb eines Befehls.

Bitte achten Sie darauf, dass Sie immer einen richtigen Bezug zu Ihrem Objekt herstellen!


## 1 Netzwerk einlesen
In diesem Kapitel lernen Sie, wie man Datensätze für das Paket igraph einliest. 

**igraph-Objekt initialisieren (Beispieldatensatz)**

Denken Sie immmer daran, vor dem Einlesen die entsprechenden Programmpakete zu laden

*library(igraph)*

Die Dateien müssen im CSV-Format vorliegen und werden als Edgelist und Nodelist mit dem Befehl read.csv eingelesen. Achten Sie hierbei, dass die Parameter richtig gesetzt sind (Kopfziele und Trennzeichen)

*el <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/edges.csv", header=T, as.is=T, sep = ",")*

*nodes <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/nodes.csv", header=T, as.is=T, sep = ",")*

Mit dem Befehl as.matrix erzeugen wir aus der Edgelist eine Matrix. 

*edgematrix <-as.matrix(el)*

graph_from_data verbindet die Matrix mit der Nodelist und gibt ihr die Bezeichnung "s". Achten Sie hier auf darauf, ob das Netzwerk gerichtet oder ungerichtet ist.

*s <- graph_from_data_frame(d=edgematrix, vertices=nodes, directed=T)*

Das neu erstellte igraph-objekt "s"" verfügt über bestimmte Eigenschaften.

s

***

Lesen Sie nun ihr Netzwerk aus Ihrem github-Verzeichnis ein und geben dem igraph-Objekt einen sinnvollen Namen (nicht main_igraph):

```{r Eigenes_igraph-Objekt_erstellen, exercise=TRUE, exercise.lines = 10}
library(igraph)
el <- read.csv("XX", header=T, as.is=T, sep = ",")
nodes <- read.csv("XX", header=T, as.is=T, sep = ",")
edgematrix <-as.matrix(el)
mein_igraph <- graph_from_data_frame(d=edgematrix, vertices=nodes, directed=T)
mein_igraph
```

## 2 igraph-objekt verstehen
In diesem Kapitel lernen Sie, wie man ein igraph-Objekt schnell interpretiert. Jedes igraph Objekt verfügt über eine feste Konvention, mit der es interpretiert werden kann. Damit sieht man schnell, welche Edge- und Nodeattribute das Netzwerk aufweist.

```{r Netzwerkattribute_verstehen}
library(igraph)

el <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/edges.csv", header=T, as.is=T, sep = ",")

nodes <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/nodes.csv", header=T, as.is=T, sep = ",")

edgematrix <-as.matrix(el)
s <- graph_from_data_frame(d=edgematrix, vertices=nodes, directed=T)
s
```

In der ersten Zeile wird die "Class", also die Art des Objekts als igraph definiert. Der Code danach identifiziert das Objekt eindeutig. Danach kommen vier mögliche Ausprägungen des Netzwerks

1) gerichtet (D) oder ungerichtet (N)
2) mit Attributen (N) (named)
3) gewichtet (W) (weighted)
4) bipartite oder two-mode (B), d.h. muss das Vertex-Attribute type beinhalten.

Nicht jedes Feld muss belegt sein. 

Danach folgt zunächst die Anzahl der Knoten (V für vertices) und Kanten (E für edges)
  
Danach folgt eine Beschreibung der Attribute. Dabei wird der Name des Attributs zuerst genannt. In den Klammer werden zwei Eigenschaften präzisiert.
e/v Edge- oder Vertex-Attribut
n/c/l numerische (n), textliche (c) oder logische (l) Daten des Attributs.
  
Danach folgt ein Auszug der Beziehungen aus der Edgelist, die grafisch dargestellt sind. Um einen schnellen Überblick über die Anzahl der Knoten und Kanten zu erhalten, helfen uns die ecount(g) für die Anzahl der Edges und vcount(g) für die Anzahl der Kanten (Vertices).

## 3 Netzwerkattribute 
Die Netzwerkattribute lassen sich mit dem Befehl list.vertex.attributes(g) anzeigen für die Node-Atttribute, gleiches gilt für list.edge.attributes(g) für die Kantenattribute. 
  
Sollen die Werte eines bestimmten Attributes ausgewählt werden, dann wird das enstprechende Attribut mit *$* selektiert und mit dem Befehl *edge.attributes(g)* oder *vertex.attributes(g)* gekoppelt. Liegt z.B. das Edge-Attribut "weight", dann lassen sich diese Werte mit dem Befehl *edge.attributes(g)$weight* auslesen.

*Aufgabe*
- Wie viele Vertices und Edges hat das Netzwerk s?  
- Erstellen Sie eine Liste aller Kanten- und Knotenattribute.  
- Zeigen Sie die Werte für das Attribut "relation"" und das Attribut "sex" an.  

```{r Netzwerkattribute_lesen, exercise=TRUE, exercise.lines = 15}
library(igraph)
el <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/edges.csv", header=T, as.is=T, sep = ",")
nodes <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/nodes.csv", header=T, as.is=T, sep = ",")
edgematrix <-as.matrix(el)
s <- graph_from_data_frame(d=edgematrix, vertices=nodes, directed=T)
s

# Hier kommen Ihre Ergänzungen



```

## 4 Einfache Visualisierung
Mit  *plot(g)* lassen sich einfache Visualisierungen durchführen. Der plot() Befehl überschreibt alle vorher erstellten Parameter und definiert diese nur für diesen plot. Sollen bestimmte Eigenschaften des Netzwerks dauerhaft festgelegt werden, dann ist es einfacher, diese Eigenschaften vorab dauerhaft zu definieren.

Der Layout-Befehl layout_with_kk verwendet den Kamada-Kawai Algorithmus. Sein Vorteil ist, dass die Knoten immer an auf der gleichen Position festgelegt werden. Die Funktion *main=* legt den Titel des Abbildung fest, die Funktion *sub=* den entsprechenden Untertitel.

*Aufgabe*  
- Ändern Sie den Titel der Abbildung.  
- Ändern Sie das verwendete Layout mit dem Fruchterman-Rheingold-Algorithmen (layout_with_fr) 

```{r Visualisierung, exercise=TRUE, exercise.lines = 6}
plot(s,
     layout=layout_with_kk,
     main ="out-of-the-box Visualisierung des Netzwerks")
```


## 5 Attribute festlegen
Netzwerkattribute sind hilfreich, um Netzwerke besser zu verstehen. Sie sind wichtige Parameter für die spätere Visualisierung von Netzwerken. Jedes Netzwerk hat zusätzlich zu den erhobenen Attributen feststehende Visualisierungsparameter. Diese lassen sich beliebig manipulieren. Werden die Daten ein Mal festgeschrieben, dann gelten sie für alle weiteren Netzwerke. 

Merke: Die Befehle **V(g)** und **E(g)** erstellen dauerhaft neue Vertex bzw. Edge-Attribute, die mit bestimmten Eigenschaften versehen werden können. Mit $ wird auf die entsprechenden Attribute zugegriffen.Die Attribute lassen sich auch durch "NA" komplett löschen oder durch ein bestehendes Attribut wieder ergänzen. 

Beispielsweise wird hier die Füllfarbe eines Knotens auf dunkelorange definiert V(s)$color<-"darkorange". Mit vertex.attributes(g)$color kann dieser Wert angezeigt werden. Der Rahmen eines Knoten kann durch die Zuweisung des Wert "NA" ausgeblendet werden V(g)$frame.color<-"NA". Dies gilt auch für Kantenattribute. Beispielsweise lassen sich die Pfeilspitzen auf den Wert .2 setzen E(s)$arrow.size<-.2 oder die Farbe der Kanten entsprechend festlegen E(s)$color<-"darkorange"

Manchmal ist es hilfreich die Labels auszublenden V(s)$label<-NA. Um diese wieder herzustellen das Vertex-Attribut "Label" mit dem Wert des Vertex-Attributs "Name" wieder überschrieben: V(s)$label<-V(s)$name. 
Eine Übersicht aller Edge- und Vertex-Attribute, die mit diesen Befehlen verändert werden können liefert die Hilfefunktion ?igraph.plotting

**Aufgabe**  
- Die Visualisierung des Netzwerks soll dauerhaft folgende Farben haben:
- Die Knoten in "darkblue"" mit einem Rand in "lightblue""
- Die Kanten in "lightblue"" mir einer Pfeilspitze von .3
- Eine neue, passende Hauptüberschrift und Unterüberschrift

```{r Netzwerkattribute_manipulieren, exercise=TRUE, exercise.lines = 15}

?igraph.plotting

V(s)$color <- "darkorange"
V(s)$frame.color <- "NA"
E(s)$arrow.size <- .2
E(s)$color <- "darkorange"

plot(s,
     layout=layout_with_kk,
     main ="Visualisierung mit geänderten Attributen")

```
# Teilnetzwerke erstellen

**Worum geht es?**
In diesem Tutorial lernen Sie, wie sich *Teilnetzwerke* nach Vertex- und Edge-Attributene erstellen lassen. Diese Fähigkeit ist zentral, um Netzwerke miteinander vergleichen zu können. Wir verwenden wieder das Beispielnetzwerk von Studierenden mit den Codebuch https://github.com/hdm-crpr/226305/blob/master/data/crpr2/codebuch.md

**Logische Operatoren**
Generell sind logische Operatoren hilfreich, um bestimmte Parameter des Netzwerks auswählen zu können. Siehe dazu https://methodenlehre.github.io/einfuehrung-in-R/die-r-sprache.html

**igraph-Objekt initialisieren (Studierende)**

```{r Netzwerkattribute_verstehen}
library(igraph)
el <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/edges.csv", header=T, as.is=T, sep = ",")
nodes <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/nodes.csv", header=T, as.is=T, sep = ",")
edgematrix <-as.matrix(el)
s <- graph_from_data_frame(d=edgematrix, vertices=nodes, directed=T)
```

## 1 Teilnetzwerk nach Edge-Attributen
Verfügt das Netzwerk über entsprechende Edge-Attribute list.edge.attributes() lässt sich das Netzwerk durch die Auswahl spezifischer Edge-Attribute und dem Befehl subgraph.edges() erstellen. Der Befehl erstellt ein komplettes Unternetzwerk mit allen Node-Attributen. 

Der Befehl subgraph.edges ist wie folgt aufgebaut:
subgraph.edges(g, E(g)[Selektion des Attributs]) und liest sich wie folgt: Erstelle ein neues Netzwerk aus dem Netzwerk g, indem das Netzwerk basierend auf dem logischen Operator aus dem Edge-Attribut von g gewählt wird.

Wichtig ist es hier, das Netzwerk neu zu benennen.

```{r subgraph_edges, exercise=TRUE, exercise.lines = 15}
list.edge.attributes(s)
edge.attributes(s)$relation

work <- subgraph.edges(s, E(s)[relation==1]) 
work

plot(work,
     edge.arrow.size=.3,
     layout=layout_with_kk,
     edge.color="blue",
     edge.curved=.2,
     edge.curved=curve_multiple(work),
     main="Teilnetzwerk Zusammenarbeit",
     sub="n=38, KK-Algorithmus")
```

**Aufgabe**
Erstellen Sie ein Teilnetzwerk "help"" mit der Kantenfarbe "green" und ein Teilnetzwerk "love" mit der Kantenfarbe "red". Benennen Sie das Netzwerk entsprechend. Erstellen Sie dann ein Teilnetzwerk von Studierenden, die eine Paarbeziehung haben und nennen dieses Teilnetzwerk "relationship" (Tipp: Sie müssen dafür ins Codebuch des Datensatzes schauen und die Edge-Attribute entsprechend analysieren).


```{r subgraph_edges_ex, exercise=TRUE, exercise.lines = 30}



```


## 2 Multiplexe Netzwerke visualisieren
Multiplexe Netzwerke haben mehr als nur eine Kantenart, d.h. es werden mehrere Beziehungsarten im gleichen Graphen visualisiert. Dazu gibt es zwei Möglichkeiten (die sich auch kombinieren lassen): Farben und Formen. Achtung: multiplexe Netzwerke werden leicht unübersichtlich, deshalb sollte die Visualisierung immer mit Bedacht vorgenommen werden.

*Kantenfarben* verwenden: wir haben in dem Edge-Attribut "relation" zwei Werte angebgeben, nämlich "1" (work) und "2" (help), die unterschiedliche Beziehungen beschreiben. Die Kanten lassen sich entsprechend einfärben.

```{r multiplexes Netzwerk, exercise=TRUE, exercise.lines = 20}

E(s)[E(s)$relation == 1]$color <- "blue" 
E(s)[E(s)$relation == 2]$color <- "green"
E(s)[E(s)$relation == 3]$color <- "red"

plot(s,
     edge.arrow.size=.1,
     vertex.color="gray90",
     vertex.frame.color="white",
     layout=layout_with_kk,
     edge.curved=curve_multiple(s),
     main="Multiplexes Netzwerk, d.h. verschiedene Formen der Beziehung",
     sub="n=38, blau=Zusammenarbeit, grün=Ratsuche, rot=Beziehung")
```

**Aufgabe**
Visualisieren Sie nur das Zusammenarbeitsnetzwerk work in "lightblue". Visualisieren Sie nur das Beziehungsnetzwerk love in "red". Alle weiteren Beziehungen werden im Farbwert "grey20" dargestellt.  

```{r multiplex_ex, exercise=TRUE, exercise.lines = 20}

E(s)[E(s)$relation == 1]$color 

plot(s,
     edge.arrow.size=.1,
     vertex.color="gray90",
     vertex.frame.color="white",
     layout=layout_with_kk,
     edge.curved=curve_multiple(s),
     main="XX",
     sub="XX")
```


*Kantenformen* verwenden: Neben den Vertex-Formaten lassen sich auch die Kanten visuell anpassen. Hier stehen verschiedene Formen zur Verfügung: 0 or “blank”, 1 or “solid”, 2 or “dashed”, 3 or “dotted”, 4 or “dotdash”, 5 or “longdash”, 6 or “twodash”. Die Codierung ist vorgegeben und als edge.lty definiert. lty steht für Linetype, also die Art der Linie, die verwendet wird.

```{r multiplex_form, exercise=TRUE, exercise.lines = 20}
E(s)[E(s)$relation == 1]$lty <-2 # dashed (work)
E(s)[E(s)$relation == 2]$lty <-3 # dotted (help)
E(s)[E(s)$relation == 3]$lty <-4 # dotdash (love)

# Visualisierung des multiplexen Netzwerks
plot(s,
     edge.arrow.size=.1,
     edge.color="black",
     vertex.color="gray90",
     vertex.frame.color="white",
     layout=layout_with_kk,
     edge.curved=curve_multiple(s),
     main="Multiplexes Netzwerk, Format der Kanten",
     sub="n=38, work=dashed, help=dotted, love=dotdash")
```

**Aufgabe**
Visualisieren Sie aus dem Hauptnetzwerk s das Zusammenarbeitsnetzwerks in roter Farbe und gepunktet.

```{r multiplex_task, exercise=TRUE, exercise.lines = 20}
library(igraph)
el <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/edges.csv", header=T, as.is=T, sep = ",")
nodes <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/nodes.csv", header=T, as.is=T, sep = ",")
edgematrix <-as.matrix(el)
s <- graph_from_data_frame(d=edgematrix, vertices=nodes, directed=T)


```

## 3 Teilnetzwerke nach Vertex-Attributen
Teilnetzwerke lassen sich auch nach Vertex-Attributen erstellen. Dabei wird der Befehl delete_vertices(g). Damit werden Knoten gelöscht, die eine bestimmtes Vertex-Attribut aufweisen. Das bedeutet, dass die Auswahl des Netzwerks immer aufgrund der gelöschten Attribute erfolgt. Sollen z.B. das Netzwerk nur aus Männern bestehen, müssen alle Knoten mit den Attributen, die nicht Männer sind, gelöscht werden. Dazu helfen die logischen Operatoren. Wie im Beispiel unten werden z.B. alle Werte ausgewählt, die größer 1 sind. Alternativ könnte man auch auch den logischen Operator ist nicht != verwenden, der alle Werte ausser dem angegebenen löscht.

Wichtig ist es hier, das Netzwerk neu zu benennen.

```{r delete_vertices, exercise=TRUE, exercise.lines = 15}
library(igraph)
el <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/edges.csv", header=T, as.is=T, sep = ",")
nodes <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/nodes.csv", header=T, as.is=T, sep = ",")
edgematrix <-as.matrix(el)
s <- graph_from_data_frame(d=edgematrix, vertices=nodes, directed=T)

list.vertex.attributes(s)
vertex_attr(s)$sex

s_fem <- delete_vertices(s, V(s)[sex > "1"]) 
s_fem
plot(s_fem, layout=layout_with_kk,
     main="Netzwerk, nur weiblich",
     edge.color="grey80",
     edge.arrow.size=.3,
     vertex.color="pink",
     sub="n=29, 110 Kanten")
```

**Aufgabe**
Erstellen Sie ein männliches Unternetzwerk, färben die Knoten in "lightblue" und fügen passende Überschriften hinzu mit der Anzahl der Knoten und Kanten.

```{r delete_vertices_ex, exercise=TRUE, exercise.lines = 30}



```

*Verknüpfte Bedingungen*
In diesem Beispiel wollen wir nur Knoten haben, die weiblich sind und PR vertiefen. Im Codebuch ist der Wert für weiblich für das Vertex-Attribut sex mit 1 codiert, die Variable PR ist als Vertex-Attribut crpr mit dem Wert 2 codiert. 

Achten Sie darauf, dass zunächst ein Unternetzwerk s_fem erstellt wird und aus diesem Unternetzwerk ein zweites Netzwerk der Vertiefer erstellt wird!


```{r delete_vertices_combined, exercise=TRUE, exercise.lines = 15}
list.vertex.attributes(s)

# Zunächst werden alle Werte gelöscht, die nicht weiblich sind.
s_fem <- delete_vertices(s, V(s)[sex>"1"]) 

# Dann werden die Journalisten mit dem Wert ein 1 aus dem Netzwerk s_fem gelöscht (in dem nur Frauen sind.)
s_fem_pr <- delete_vertices(s_fem, V(s_fem)[crpr=="1"]) 
s_fem_pr

# Der plot verwendet nur wenig Anpassungen.
plot(s_fem_pr, 
     layout=layout_with_kk,
     main="Netzwerk der PR-Vertieferinnen",
     edge.color="grey80",
     edge.arrow.size=.3,
     vertex.label.color="white",
     vertex.color="darkred",
     sub="n=12, 32 Kanten")
```

**Aufgabe**
Erstellen Sie ein Netzwerk der männlichen Journalismus-Vertiefer, die noch eine weitere Bedingung umfasst und benennen Sie das Netzwerk entsprechend.

```{r delete_vertices_combined2, exercise=TRUE, exercise.lines = 15}
list.vertex.attributes(s)

```


## 4 Kombination von Edge- und Vertex-Attributen
Natürlich lassen sich alle Varianten auch gemeinsam kombinieren zu einem Grand Finale:

Uns interessiert jetzt ein das weibliche Unterstützungsnetzwerk von Personen, sich sich stark unterstützen und die über 23 Jahre alt sind. Wie sieht die Beziehung zwischen diesen Personen aus?


```{r grand_finale_1, exercise=TRUE, exercise.lines = 15}
list.vertex.attributes(s)
el <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/edges.csv", header=T, as.is=T, sep = ",")
nodes <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/nodes.csv", header=T, as.is=T, sep = ",")
edgematrix <-as.matrix(el)
s <- graph_from_data_frame(d=edgematrix, vertices=nodes, directed=T)
s

# Schritt 1: Trennung in das Unterstützungsnetzwerk
help <- subgraph.edges(s, E(s)[relation==2]) 
help

# Schritt 2: Selektion weight=3 
help_strong <- subgraph.edges(help, E(help)[weight==3])

# Wir wollen nun wissen, wie das Ratsuche-Netzwerk unter Frauen aussieht:
fem <- delete_vertices(help_strong, V(help_strong)[sex != "1"]) # löscht alle nicht weiblichen Knoten

plot(fem,
     layout=layout_with_kk,
     main="Unterstützungsnetzwerk weiblich",
     edge.color="grey80",
     edge.arrow.size=.3,
     vertex.color="pink",
     sub="weiblich, starke Beziehung")


fem_old <- delete_vertices(fem, V(fem)[age < "3"])
fem_old
plot(fem_old, layout=layout_with_kk,
     main="Unterstützungsnetzwerk weiblich (fem_old)",
     edge.color="grey80",
     edge.arrow.size=.3,
     vertex.color="pink",
     sub="weiblich, Alter über 23, starke Beziehung")

# Es zeigt sich, dass nur eine (reziproke) Beziehung beim weiblichen Unterstützungsnetzwerk der über 23-jährigen übrig bleibt, nämlich zwischen Knoten 38 und 29. Um diese Dyade besser darzustellen können alle isolates, also Knoten, die nicht miteinander verbunden sind, gelöscht werden.

# der Befehl delete.vertices löscht alle Knoten aus dem Netzwerk fem_old, die einen degree-Wert von 0 haben, also mit keinem anderen Knoten verbunden sind. 
fem_old2 <- delete.vertices(fem_old, degree(fem_old)==0)
fem_old2

plot(fem_old2, layout=layout_with_kk,
     main="Dyade ohne Isolates ",
     edge.arrow.size=.7,
     edge.width=E(s)$weight,
     edge.color="pink",
     vertex.size=30,
     vertex.color="pink",
     vertex.frame.color="black",
     vertex.frame.color="white",
     vertex.label.color="black",
     sub="Dyade zweier Frauen über 23, die sich gegenseitig stark unterstützen")
```

**Abschlussaufgabe**
Erstellen Sie ein Teilnetzwerk mit folgenden Bedingungen: Gesucht werden männliche Journalisten, die überwiegend zusammenarbeiten und auf Tinder aktiv sind.

Überlegen Sie zuerst anhand des Codebuchs, welche Schritte notwendig sind, damit Sie zunächst Teilnetzwerke selektieren und dann visualisieren können.


```{r grand_finale_ex, exercise=TRUE, exercise.lines = 15}
list.vertex.attributes(s)
el <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/edges.csv", header=T, as.is=T, sep = ",")
nodes <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/nodes.csv", header=T, as.is=T, sep = ",")
edgematrix <-as.matrix(el)
s <- graph_from_data_frame(d=edgematrix, vertices=nodes, directed=T)
s


```

---
title: "226305 Tutorial"
subtitle: "3 Ego-Netzwerke"
author: "Swaran Sandhu"
output: learnr::tutorial
runtime: shiny_prerendered
---

```{r setup, include=FALSE}
library(learnr)
knitr::opts_chunk$set(echo = FALSE)
```

## Anleitung

**Worum geht es?**
In diesem Tutorial lernen Sie, wie sich *Ego-Netzwerke* aus einem generellen Netzwerk erstellen lassen. Wir verwenden wieder das Beispielnetzwerk von Studierenden mit den Codebuch https://github.com/hdm-crpr/226305/blob/master/data/crpr2/codebuch.md

**Ego-Netzwerke**
Ego-Netzwerke sind Netzwerke, die sich auf einen Knoten innerhalb des Netzwerks fokussieren. Sie lassen sich mit dem Befehl make_ego_graph(g) leicht erstellen.

**igraph-Objekt initialisieren (Studierende)**

```{r Netzwerkattribute_verstehen}
library(igraph)
el <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/edges.csv", header=T, as.is=T, sep = ",")
nodes <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/nodes.csv", header=T, as.is=T, sep = ",")
edgematrix <-as.matrix(el)
s <- graph_from_data_frame(d=edgematrix, vertices=nodes, directed=T)
```

## 1 Einfaches Ego-Netzwerk erstellen
Manchmal ist es hilfreich, bestimmte Knoten aus dem Netzwerk zu extrahieren, um diese genauer zu untersuchen. Damit "zoomt" man auf einen Knoten im Netzwerk. Sie erinnern sich: jedes Netzwerk besteht aus Egos (einzelne Knoten) und deren Alteri. Diese Ego-Netzwerke lassen sich auch einzeln analyisieren. Wir verwenden dafür die Befehle ego_size() und make_ego_graph().

Uns interessiert, wer im Netzwerk s die meisten Beziehungen hat und dessen direktes Netzwerk. Deshalb selektieren wir zunächst den Knoten mit dem höchsten degree-Wert und erstellen danach das Ego-Netzwerk.


```{r ego_netzwerk, exercise=TRUE, exercise.lines = 15}
# zeigt die Knoten mit den meisten Verbindungen, ähnlich wie der degree Wert.
ego_size(s)

# Wir stellen fest, dass Knoten 18 die meisten degrees hat. Deshalb wollen wir ein Ego-Netzwerk aus diesem Graph generieren.
degree(s)

# selektiert aus dem Netzwerk h3 alle Knoten, die mit Knoten 18 über einen Schritt verbunden sind.
king <- make_ego_graph(s, order = 1, nodes = V(s)$name == 18, mode ="all")

# liefert eine Liste der Verbindungen (in diesem Falle alle out/indgree Beziehungen von 18)
king

# liefert einen (nicht besonders aufregenden) Plot des selektierten Ego-Netzwerks "king"

# man braucht diesen Zwischenschrit, damit das igraph-Objekt von king1 hergestellt ist
king1 <- king[[1]]
king1

plot(king1, 
     main="Ego-Netzwerk Knoten 18, erster Grad",
     vertex.color="gold",
     edge.color="grey80",
     edge.arrow.size=.3,
     sub="nur direkte Beziehungen des ersten Grads (15 alteri)")


```

**Aufgabe**
Erstellen Sie das Ego-Netzwerk des Knotens mit den zweithöchsten Verbindungungen. 

```{r ego_netzwerk_ex, exercise=TRUE, exercise.lines = 15}
# zeigt die Knoten mit den meisten Verbindungen, ähnlich wie der degree Wert.
ego_size(s)

```

## 2 Ego-Netzwerk zweiter Ordnung
Bei einem Ego-Netzwerk zweiter Ordnung werden all diejenigen Verbindungen der alteri erster Ordnung noch hinzugefügt. damit erweitert sich das Netzwerk entsprechend. Dazu wird das argument order im Befehl make_ego_graph() entsprechend verändert. 

```{r ego_netzwerk_2, exercise=TRUE, exercise.lines = 15}

king2 <- make_ego_graph(s, order = 2, nodes = V(s)$name == 18, mode ="all")
king2 <- king2[[1]]

plot(king2, 
     main="Ego-Netzwerk Knoten 18, 2. Grad",
     vertex.color="orange",
     edge.color="grey80",
     edge.arrow.size=.3,
     sub="Beziehungen des zweiten Grads (21 alteri)")

king3 <- make_ego_graph(s, order = 3, nodes = V(s)$name == 18, mode ="all")
king3 <- king3[[1]]

plot(king3, 
     main="Ego-Netzwerk Knoten 18, 3. Grad",
     vertex.color="red",
     edge.color="grey80",
     edge.arrow.size=.3,
     sub="Beziehungen des dritten Grads, 22 alteri")

# erst durch die Einbezierung der Beziehungen des zweiten Grads wird die Beziehungsstruktur innerhalb des Netzwerks sichtbar. 

# Darstellung als Vergleich:

par(mfrow=c(1,3), mar=c(0,0,1,2))
plot(king1, edge.arrow.size=.3, main="Erster Grad")
plot(king2, edge.arrow.size=.3,  main="Zweiter Grad")
plot(king3, edge.arrow.size=.3, main="Dritter Grad")

par(mfrow=c(1,1), mar=c(0,0,1,2))
```

**Aufgabe**
Erstellen Sie die Ego-Netzwerke des Knotens "36"" mit direkten und indirekten Verbindungen.

```{r ego_netzwerk_order, exercise=TRUE, exercise.lines = 15}
# zeigt die Knoten mit den meisten Verbindungen, ähnlich wie der degree Wert.
ego_size(s)

```
---
title: "226305 Tutorial"
subtitle: "3 Ego-Netzwerke"
author: "Swaran Sandhu"
output: learnr::tutorial
runtime: shiny_prerendered
---

```{r setup, include=FALSE}
library(learnr)
knitr::opts_chunk$set(echo = FALSE)
```

## Anleitung

**Worum geht es?**
In diesem Tutorial lernen Sie, wie sich *Ego-Netzwerke* aus einem generellen Netzwerk erstellen lassen. Wir verwenden wieder das Beispielnetzwerk von Studierenden mit den Codebuch https://github.com/hdm-crpr/226305/blob/master/data/crpr2/codebuch.md

**Ego-Netzwerke**
Ego-Netzwerke sind Netzwerke, die sich auf einen Knoten innerhalb des Netzwerks fokussieren. Sie lassen sich mit dem Befehl make_ego_graph(g) leicht erstellen.

**igraph-Objekt initialisieren (Studierende)**

```{r Netzwerkattribute_verstehen}
library(igraph)
el <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/edges.csv", header=T, as.is=T, sep = ",")
nodes <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/nodes.csv", header=T, as.is=T, sep = ",")
edgematrix <-as.matrix(el)
s <- graph_from_data_frame(d=edgematrix, vertices=nodes, directed=T)
```

## 1 Einfaches Ego-Netzwerk erstellen
Manchmal ist es hilfreich, bestimmte Knoten aus dem Netzwerk zu extrahieren, um diese genauer zu untersuchen. Damit "zoomt" man auf einen Knoten im Netzwerk. Sie erinnern sich: jedes Netzwerk besteht aus Egos (einzelne Knoten) und deren Alteri. Diese Ego-Netzwerke lassen sich auch einzeln analyisieren. Wir verwenden dafür die Befehle ego_size() und make_ego_graph().

Uns interessiert, wer im Netzwerk s die meisten Beziehungen hat und dessen direktes Netzwerk. Deshalb selektieren wir zunächst den Knoten mit dem höchsten degree-Wert und erstellen danach das Ego-Netzwerk.


```{r ego_netzwerk, exercise=TRUE, exercise.lines = 15}
# zeigt die Knoten mit den meisten Verbindungen, ähnlich wie der degree Wert.
ego_size(s)

# Wir stellen fest, dass Knoten 18 die meisten degrees hat. Deshalb wollen wir ein Ego-Netzwerk aus diesem Graph generieren.
degree(s)

# selektiert aus dem Netzwerk h3 alle Knoten, die mit Knoten 18 über einen Schritt verbunden sind.
king <- make_ego_graph(s, order = 1, nodes = V(s)$name == 18, mode ="all")

# liefert eine Liste der Verbindungen (in diesem Falle alle out/indgree Beziehungen von 18)
king

# liefert einen (nicht besonders aufregenden) Plot des selektierten Ego-Netzwerks "king"

# man braucht diesen Zwischenschrit, damit das igraph-Objekt von king1 hergestellt ist
king1 <- king[[1]]
king1

plot(king1, 
     main="Ego-Netzwerk Knoten 18, erster Grad",
     vertex.color="gold",
     edge.color="grey80",
     edge.arrow.size=.3,
     sub="nur direkte Beziehungen des ersten Grads (15 alteri)")


```

**Aufgabe**
Erstellen Sie das Ego-Netzwerk des Knotens mit den zweithöchsten Verbindungungen. 

```{r ego_netzwerk_ex, exercise=TRUE, exercise.lines = 15}
# zeigt die Knoten mit den meisten Verbindungen, ähnlich wie der degree Wert.
ego_size(s)

```

## 2 Ego-Netzwerk zweiter Ordnung
Bei einem Ego-Netzwerk zweiter Ordnung werden all diejenigen Verbindungen der alteri erster Ordnung noch hinzugefügt. damit erweitert sich das Netzwerk entsprechend. Dazu wird das argument order im Befehl make_ego_graph() entsprechend verändert. 

```{r ego_netzwerk_2, exercise=TRUE, exercise.lines = 15}

king2 <- make_ego_graph(s, order = 2, nodes = V(s)$name == 18, mode ="all")
king2 <- king2[[1]]

plot(king2, 
     main="Ego-Netzwerk Knoten 18, 2. Grad",
     vertex.color="orange",
     edge.color="grey80",
     edge.arrow.size=.3,
     sub="Beziehungen des zweiten Grads (21 alteri)")

king3 <- make_ego_graph(s, order = 3, nodes = V(s)$name == 18, mode ="all")
king3 <- king3[[1]]

plot(king3, 
     main="Ego-Netzwerk Knoten 18, 3. Grad",
     vertex.color="red",
     edge.color="grey80",
     edge.arrow.size=.3,
     sub="Beziehungen des dritten Grads, 22 alteri")

# erst durch die Einbezierung der Beziehungen des zweiten Grads wird die Beziehungsstruktur innerhalb des Netzwerks sichtbar. 

# Darstellung als Vergleich:

par(mfrow=c(1,3), mar=c(0,0,1,2))
plot(king1, edge.arrow.size=.3, main="Erster Grad")
plot(king2, edge.arrow.size=.3,  main="Zweiter Grad")
plot(king3, edge.arrow.size=.3, main="Dritter Grad")

par(mfrow=c(1,1), mar=c(0,0,1,2))
```

**Aufgabe**
Erstellen Sie die Ego-Netzwerke des Knotens "36"" mit direkten und indirekten Verbindungen.

```{r ego_netzwerk_order, exercise=TRUE, exercise.lines = 15}
# zeigt die Knoten mit den meisten Verbindungen, ähnlich wie der degree Wert.
ego_size(s)

```
