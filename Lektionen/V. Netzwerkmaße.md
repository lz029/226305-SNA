---
title: "226305 Tutorial 4"
subtitle: "Netzwerkmaße: Gesamtnetzwerk"
author: "Swaran Sandhu"
output: html_notebook
---

**Worum geht es?**
In diesem Tutorial lernen Sie, wie sich *Netzwerkmaße* aus einem generellen Netzwerk erstellen lassen. Wir verwenden wieder das Beispielnetzwerk von Studierenden mit den Codebuch https://github.com/hdm-crpr/226305/blob/master/data/crpr2/codebuch.md

*Netzwerkmaße*
sind generelle Berechnungen des Netzwerks. Die wichtigsten sind Dichte (density) und Umfang (diameter). Netzwerkmaße lassen sich erst im Vergleich von Teilnetzwerken sinnvoll interpretieren.

**igraph-Objekt initialisieren (Studierende)**

```{r Netzwerk erstellen}
library(igraph)
el <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/edges.csv", header=T, as.is=T, sep = ",")
nodes <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/nodes.csv", header=T, as.is=T, sep = ",")
edgematrix <-as.matrix(el)
s <- graph_from_data_frame(d=edgematrix, vertices=nodes, directed=T)
# Pfeilstpitzen auf .2 dauerhaft gesetzt
E(s)$arrow.size <- .2
```

## 1 Dichte (density)
Die Dichte in unserem Netzwerk beträg 0.1251778, das bedeutet, dass 12,53 % (gerundet), von allen möglichen Beziehungen zwischen den Knoten realisiert wurde. Dies bedeutet auch, dass zwischen knapp 90% der Knoten keine Beziehungen bestehen. Wir gehen zu leicht davon aus, dass Netzwerke eine hohe Dichte haben. Das würde aber voraussetzen, dass jeder Knoten mit allen anderen Knoten verbunden ist, wie dies etwa in Cliquen der Fall ist.


```{r Dichte berechnen}
# Berechnung der Dichte des Netzwerks s
library(igraph)
el <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/edges.csv", header=T, as.is=T, sep = ",")
nodes <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/nodes.csv", header=T, as.is=T, sep = ",")
edgematrix <-as.matrix(el)
s <- graph_from_data_frame(d=edgematrix, vertices=nodes, directed=T)

edge_density(s)

```

Aussagekräftig werden die Dichtewerte besonders dann, wenn Netzwerke miteinander verglichen werden. Dazu können wir z.B. das CRPR Netzwerk in drei Teilnetzwerke (work, help, love) zerlegen

```{r Dichte in Teilnetzwerken vergleichen}
# Berechnung der Dichte des Netzwerks s
library(igraph)
el <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/edges.csv", header=T, as.is=T, sep = ",")
nodes <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/nodes.csv", header=T, as.is=T, sep = ",")
edgematrix <-as.matrix(el)
s <- graph_from_data_frame(d=edgematrix, vertices=nodes, directed=T)
E(s)$arrow.size <- .2

# Teilnetzwerke erstellen
work <- subgraph.edges(s, E(s)[relation==1]) 
help <- subgraph.edges(s, E(s)[relation==2]) 
love <- subgraph.edges(s, E(s)[relation==3])

# Visualisierung
par(mfrow=c(1,4), mar=c(0,0,2,1)) 
plot(s, main="Gesamt")
plot(work, vertex.color="blue", main="Work")
plot(help, vertex.color="green", main="Help")
plot(love, vertex.color="red", main="Love")
par(mfrow=c(1,1), mar=c(0,0,1,1)) 

# Berechnung der Dichte für die Netzwerke
edge_density(s)
edge_density(work)
edge_density(help)
edge_density(love)

```

Bei der Analyse wird deutlich, dass die Teilnetzwerke work und help genau die gleiche Dichte haben, nämlich 5.40 Prozent. Dies lässt sich aus dem Setting erklären, dass jeder der 38 Knoten genau zwei Beziehungen angeben konnte. Das Liebesnetzwerk hat eine geringe Dichte von 0.47%. Auch das ist naheliegend, da ja viele Studierende Sozialbeziehungen außer des Netzwerks pflegen können.

**Aufgabe**
Vergleichen Sie die Dichte zwischen den männlichen und weiblichen Teilnetzwerken zur Zusammenarbeit. Dazu brauchen Sie die Kenntnisse der vorhergehenden Tutorials zur Selektion von Teilnetzwerken nach Vertex- und Edge-Attributen.

```{r Übung Dichte zwischen Männer und Frauennetzwerken}
# Dichte Männer- und Frauen

```

Doch Achtung: wir haben gerade die Dichte des gesamten Netzwerks berechnet. Das Netzwerk hat aber zwei Komponenten. Um eine genauere Aussage über das Netzwerk zu treffen, schauen wir uns nun nur die Dichte der Hauptkomponente an. Dazu müssen wir zunächst das Netzwerk in die Hauptkomponente zerlegen, dann in Frauen- und Männernetzwerke zerlegen und daraus dann die Unternetzwerke help und work entwickeln.

```{r Dichte im Vergleich}
# Berechnung der Dichte des Netzwerks s
library(igraph)
el <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/edges.csv", header=T, as.is=T, sep = ",")
nodes <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/nodes.csv", header=T, as.is=T, sep = ",")
edgematrix <-as.matrix(el)
s <- graph_from_data_frame(d=edgematrix, vertices=nodes, directed=T)
E(s)$arrow.size <- .2

# Teilnetzwerke erstellen
work <- subgraph.edges(s, E(s)[relation==1]) 
help <- subgraph.edges(s, E(s)[relation==2]) 
love <- subgraph.edges(s, E(s)[relation==3])

# Visualisierung
par(mfrow=c(1,4), mar=c(0,0,2,1)) 
plot(s, main="Gesamt")
plot(work, vertex.color="blue", main="Work")
plot(help, vertex.color="green", main="Help")
plot(love, vertex.color="red", main="Love")
par(mfrow=c(1,1), mar=c(0,0,1,1)) 

# Berechnung der Dichte für die Netzwerke
edge_density(s)
edge_density(work)
edge_density(help)
edge_density(love)

```


## 2 Durchmesser und Pfaddistanz
Diameter beschreibt den längsten Pfad innerhalb eines Netzwerks, also die maximal mögliche Distanz zwischen zwei Knoten innerhalb des Netzwerks. 

Pfadistanz ist ein Maß für die Anzahl der Schritte, dies es braucht, um ein Netzwerk zu "durchschreiten". Dabei sind die kürzesten und längsten Pfaddistanzen wichtige Aussagen.

Mit dem Befehl farthest_vertices(g) lassen sich die am weitesten voneinander entfernten Knoten anzeigen (allerdings ohne möglichen Pfad durch das Netzwerk)

```{r Maximale Distanz}
# Was ist die maximale Distanz zwischen zwei Knoten im Netzwerk?
library(igraph)
el <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/edges.csv", header=T, as.is=T, sep = ",")
nodes <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/nodes.csv", header=T, as.is=T, sep = ",")
edgematrix <-as.matrix(el)
s <- graph_from_data_frame(d=edgematrix, vertices=nodes, directed=T)
E(s)$arrow.size <- .2

# Achtung: bei Netzwerken mit Kantengewicht müssen die Kantengewichte ausgeschaltet werden! 
diameter(s, weights = NA)

# Welche Knoten sind am weitesten voneinander entfernt, also haben die längsten Schritte??
farthest_vertices(s) 
```
---
title: "226305 Tutorial 5"
subtitle: "Netzwerkmaße: Zentralitätsmaße/positionale Maße"
author: "Swaran Sandhu"
output: html_notebook
---
**Worum geht es?**
In diesem Tutorial lernen Sie, wie sich *Zentralitaetsmaße* aus einem generellen Netzwerk berechnen lassen. Wir verwenden wieder das Beispielnetzwerk von Studierenden mit den Codebuch https://github.com/hdm-crpr/226305/blob/master/data/crpr2/codebuch.md

*Zentralitaetsmaße*
oder positionale Maße geben uns eine Auskunft über die Position und Bedeutung des einzelnen Knoten im Netzwerk im Vergleich zu den anderen Knoten. Wichtig: es geht dabei nicht um generelle Netzwerkmaße, sondern immer um die Position von einzelnen Knoten im Netzwerk.

*Achtung* Wenn Sie ein Netzwerk mit mehreren Komponenten haben, verzerrt die Berechnung die "echten" Werte, d.h. es werden automatisch die positionalen Werte für alle Komponenten **innerhalb** der Komponente berechnet. Wenn Sie eine genauere Aussage über die Zentralität von Knoten benötigen, sollten Sie dies berücksichtigen.

Die wichtigsten Zentralitätsmaße sind
*1) Degree* (mit wie vielen Kanten ist ein Knoten verbunden?)
bei gerichteten Netzwerken unterscheiden wir zwischen Indegree und Outdegree. Bei ungerichteten Netzwerken spielt das keine Rolle.
Indegree: Wie viele eingehende Beziehungen treffen auf einen Knoten zu (z.B. Popularität, Hilfesuche, Fragen, etc.)
Outdegree: Wie viele Beziehungen gehen von dem Knoten ab (z.B. Weitergabe, Transfer, etc.)

*2) Betweenness* (welche Bedeutung hat der Knoten für das Erreichen anderer Knoten?)
Im Vergleich zum Degree-Wert werden nicht die direkten Verbindungen eines Knoten berechnet, sondern die Frage, welche Bedeutung der Knoten für die Erreichbarkeit aller anderen Knoten hat. Es geht also um eine klassische Broker-Funktion.

Es gibt noch weitere Zentralitätsmaße, aber mit diesen vier Werten können sie die wichtigsten positionalen Maße abdecken.

*Zentralisierung* Viele Zentralitätswerte berechnen absolute Zahlen. Mit der sogenannten Zentralisierung werden die absoluten Zahlen in Beziehung zu einem Gesamtwert gesetzt und bilden deshalb relative Zahlen von 0 bis 1. Wenn diese mit 100 multipliziert werden, wird der Prozentanteil gebildet. Die Zentralitätsberechnung erlaubt einen schnelleren Vergleich der Netzwerke.


**igraph-Objekt initialisieren (Studierende)**

```{r igraph Objekt erstellen}
library(igraph)
el <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/edges.csv", header=T, as.is=T, sep = ",")
nodes <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/nodes.csv", header=T, as.is=T, sep = ",")
edgematrix <-as.matrix(el)
s <- graph_from_data_frame(d=edgematrix, vertices=nodes, directed=T)
E(s)$arrow.size <- .2 
```

## Degree allgemein
Mit dem Degree-Wert lassen sich die Werte für alle Degrees, Outdegrees und Indegrees berechnen. Dabei werden immer die absoluten Zahlen der Knoten angegeben.


```{r Allgemeiner Degree-Wert}
# Netzwerk einlesen
el <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/edges.csv", header=T, as.is=T, sep = ",")
nodes <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/nodes.csv", header=T, as.is=T, sep = ",")
edgematrix <-as.matrix(el)
s <- graph_from_data_frame(d=edgematrix, vertices=nodes, directed=T)
E(s)$arrow.size <- .2 


# Einfache Berechnung des Degree als Gesamtwert
ds <- degree(s)
ds

# Die Darstellung ist etwas irritierend: in der oberen Zeile stehen die IDs und in der unteren Zeile die Anzahl der Kanten des jeweiligen Knotens.

# Dieser Wert lässt sich auch für die Visualisierung des Netzwerks verwenden, in dem wir dem Wert vertex.size die berechneten Werte der Degrees zuweisen (ds).

plot(s,
     layout=layout_with_kk,
     vertex.size=ds,
     vertex.label=NA,
     vertex.frame.color=NA,
     edge.color="grey20",
     main = "Visualisierung Gesamtnetzwerk",
     sub = "n=38, Größe der Knoten nach degree-Wert")

```

## Höchster Degree-Wert in einem Netzwerk darstellen

```{r Höchster Degree Wert}

# Wir können auch gleich fragen, welcher Knoten den höchsten Degree-Wert aufweist:
which.max(ds)

# Dauerhafte Markierung des Knoten 18 (in diesem Fall wir die Rahmenfarbe rot gesetzt)
V(s)[V(s)$name == 18]$frame.color <- "red"
plot(s,
     layout=layout_with_kk,
     vertex.size=ds,
     vertex.label=NA,
     vertex.color="grey75",
     edge.color="grey80",
     main = "Visualisierung Gesamtnetzwerk",
     sub = "n=38, höchster indegree-Wert in rot umrandet")

```

In der Darstellung aller Degrees sehen wir, welche Knoten am meisten Kontakte haben. In diesem Fall haben wir mit dem Befehl which.max() herausgefunden, dass Knoten 18 die meisten degrees hat. In diesem Beispiel haben wir *alle* degrees betrachtet.

## Ego-Netzwerks des am stärksten vernetzten Knotens


```{r Ego-Netzwerk des höchsten Indegree-Werts}
# Uns interessiert das Ego-Netzwerk vom Indegree-King
library(igraph)

el <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/edges.csv", header=T, as.is=T, sep = ",")
nodes <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/nodes.csv", header=T, as.is=T, sep = ",")
edgematrix <-as.matrix(el)
s <- graph_from_data_frame(d=edgematrix, vertices=nodes, directed=T)
E(s)$arrow.size <- .2 


# ego_size() zeigt uns den Wert mit den höchsten Verbindungen (degrees)
V(s)$egos <- ego_size(s)
vertex.attributes(s)$egos
which.max(vertex.attributes(s)$egos)

# erzeugt ein Egonetzwerk
ego_g <- make_ego_graph(s, order = 1, nodes = V(s)$name == 18, mode ="all")
ego_net <- ego_g[[1]]
ego_net



V(ego_net)[V(ego_net)$name == 18]$frame.color <- "red"

plot(ego_net,
     vertex.size=degree(ego_net), # falls die Knotengröße nach Degree-Wert angezeigt werden soll
     layout=layout_with_fr,
     main="Ego-Netzwerk von Knoten 18",
     vertex.color=NA,
     vertex.label.color="black",
     vertex.frame.size="5",
     vertex.label.size="8",
     edge.color="grey40",
     edge.arrow.size=.3,
     sub="Alle Degrees")

# vereinfachen des Ego-Netzwerks (addieren )

# prüft, ob das Netzwerk vereinfacht wurde
is_simple(ego_net)


#zunächst müssen alle Edge-Attribute gelöscht werden bis auf weight gelöschtwerde
list.edge.attributes(ego_net)


# löscht die einzelnen Attribute heraus (Achtung: es wird als zwischenschritt immer ein neues Netzwerk angelegt)
egonet_clean1 <- delete_edge_attr(ego_net, "relation")
egonet_clean2 <- delete_edge_attr(egonet_clean1, "complicated")
egonet_clean <- delete_edge_attr(egonet_clean2, "arrow.size")
list.edge.attributes(egonet_clean)
edge.attributes(egonet_clean)$weight

# es werden noch doppelte Beziehungen angezeigt
plot(egonet_clean, main="Ego-Net not simple")

# simplify Befehl anwenden (addiert die Gewichte auf und reduziert dadurch die Anzahl der Kanten)

egoc <- simplify(egonet_clean, edge.attr.comb=list(weight="sum"))
egoc
list.edge.attributes(egoc)

# hier wird jetzt sichtbar, dass die Kanten miteiander aufaddiert wurden!
edge.attributes(egoc)$weight

# Abbildung mit der Kantenstärke visualisiert
plot(egoc,
      vertex.size=degree(egoc), # falls die Knotengröße nach Degree-Wert angezeigt werden soll
     layout=layout_with_fr,
     main="Ego-Netzwerk von Knoten 18 (simplified)",
     vertex.color=NA,
     vertex.label.color="black",
     vertex.frame.size="5",
     vertex.label.size="8",
     edge.color="grey40",
     edge.width=E(s)$weight,
     edge.curved=.2,
     edge.arrow.size=.3,
     sub="Alle Degrees, simplified")

```

## Vergleich Indegree- und Outdegree

```{r Vergleich Indegree-Outdegree}
el <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/edges.csv", header=T, as.is=T, sep = ",")
nodes <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/nodes.csv", header=T, as.is=T, sep = ",")
edgematrix <-as.matrix(el)
s <- graph_from_data_frame(d=edgematrix, vertices=nodes, directed=T)
E(s)$arrow.size <- .2 

# Indegree
degree(s, mode="in")
centr_degree(s, mode="in", normalized=T)

# Outdegree
degree(s, mode="out")
centr_degree(s, mode="out", normalized=T)

inds <- degree(s, mode="in")
inds
outds <- degree(s, mode="out")
outds

# Visualisierung der beiden In- und Outdegrees Zentralitätsmaße im Vergleich

par(mfrow=c(1,2), mar=c(0,0,2,2))

plot(s,
     layout=layout_with_kk,
     edge.arrow.size=.1,
     vertex.color="orange",
     vertex.frame.color="white",
     vertex.label=NA,
     vertex.size=inds*2,
     main="Indegree")

plot(s,
     layout=layout_with_kk,
     edge.arrow.size=.1,
     vertex.color="darkgreen",
     vertex.frame.color="white",
     vertex.label=NA,
     vertex.size=outds,
     main="Outdegree")

```

Frage: Warum sieht die Abbildung Outdegree so aus?
Bonusfrage: wie unterscheiden sich das Zusammenarbeits, Ratsuche und Liebesnetzwerk in den Degrees?

## Betweenness und Degree im Vergleich


```{r Vergleich Betweenness und Degree}
# Netzwerk einlesen
el <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/edges.csv", header=T, as.is=T, sep = ",")
nodes <- read.csv("https://raw.githubusercontent.com/hdm-crpr/226305/master/data/crpr2/nodes.csv", header=T, as.is=T, sep = ",")
edgematrix <-as.matrix(el)
s <- graph_from_data_frame(d=edgematrix, vertices=nodes, directed=T)
E(s)$arrow.size <- .1 


# Einfache Berechnung des Degree als Gesamtwert
ds <- degree(s, normalized=T)
ds

# Einfache Berechnung der Betweeness als Gesamtwert
bs <- betweenness(s, normalized=T)
bs

# Vergleich Degree und Betweenness-Zentralität
 
par(mfrow=c(1,2), mar=c(0,0,2,1)) 

plot(s,
     layout=layout_with_kk,
     vertex.size=ds*50,
     vertex.label=NA,
     vertex.color="gold",
     vertex.frame.color=NA,
     edge.color="grey90",
     main = "Degree-Verteilung",
     sub = "n=38, Größe der Knoten nach Closeness-Wert")

plot(s,
     layout=layout_with_kk,
     vertex.size=bs*50,
     vertex.label=NA,
     vertex.color="orange",
     vertex.frame.color=NA,
     edge.color="grey90",
     main = "Closeness",
     sub = "n=38, Größe der Knoten nach Closeness-Wert")

par(mfrow=c(1,2), mar=c(0,0,2,1)) 
par(mfrow=c(1,1), mar=c(0,0,2,1)) 

```
