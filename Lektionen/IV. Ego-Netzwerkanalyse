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
