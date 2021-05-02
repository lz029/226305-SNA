---
title: "226305 Forschungsbericht der Gruppe Musikszene Indie"
author: "Silas Schwab | ss502@hdm-stuttgart.de, Fabienne Schackert | fs138@hdm-stuttgart.de, Lena Klasen | lk158@hdm-stuttgart.de, Lioba Zangenfeind | lz029@hdm-stuttgart.de, Selina Hellfritsch | sh308@hdm-stuttgart.de"
date: "Sommersemester 2021"
output:
  html_document:
    df_print: paged
    toc: yes
    toc_depth: 3
    number_sections: yes
  pdf_document:
    toc: yes
    toc_depth: '3'
  word_document:
    toc: yes
    toc_depth: '3'
subtitle: Analyse der Verbindungen von Indie-Bands von 2015 bis 2020
---

_Anmerkung 1_: Wir werden in unserem Forschungsbericht teilweise die Netzwerke neu erstellen und einlesen, damit die Datenbasis immer klar ist. Somit können wir in den einzelnen Teilnetzwerken sicherstellen, dass nur aktuelle Werte erfasst werden.


# 1. Einleitung
Im folgenden Forschungsbericht werden wir Verbindung deutscher Indie-Bands in den Jahren von 2015 bis 2020 untersuchen. 
Dabei haben wir in den letzten Jahren die fünf größten Festivals (Southside, Rock am Ring, Fusion, Juicy Beats), in denen auch die Musikrichtung Indie vertreten ist, genauer untersucht und anhand derer 35 Akteure ausgewählt. Bei der Festivalauswahl haben wir darauf geachtet, dass sie kostenpflichtig sind, um nicht im Nachhinein zu kleine Indie-Bands aussortieren zu müssen. Durch dieses Ausschlusskriterium ist beispielsweise das Festival Bochum Total nicht berücksichtigt worden.

Die ausgewählten 35 Akteur:innen haben wir daraufhin untersucht, ob zwei Künstler:innen gemeinsam bei einem Festival aufgetreten sind (relation=1), ein gemeinsames Musiklabel haben (relation=2), gemeinsam auf Tour gegangen sind oder Auftritte zusammen gehabt haben (relation=3) und ob sie ein gemeinsames Feature produziert haben (relation=4). 
Anhand der erhobenen Daten wollen wir nun die Vernetzung der einzelnen Akteur:innen genauer beleuchten. Dabei gehen wir auf die Fragen ein, ob es einen Zusammenhang zwischen gemeinsamen Features der Künstler:innen und den Auftritten auf Festivals gibt, ob das Musiklabel Einfluss auf Festivalauftritte hat, ob Künstler:innen mit mehr Spotify-Hörer:innen / Instagram-Follower:innen auch besser vernetzt sind und welche Ergebnisse die zeitliche Entwicklungen zeigen.


# 2. Vorarbeiten und vergleichbare Studien
## 2.1 Forschungsstand
noch einfügen


## 2.2 Arbeitshypothesen
Wir gehen von folgenden Arbeitshypothesen aus:

a) Auftritte: Akteur:innen, die oft auf den gleichen Festivals aufgetreten sind, haben eher ein gemeinsames Feature und haben eher gemeinsame Auftritte oder sind die Vorband des:r jeweils anderen Akteur:in.
b) Zusammenarbeit: Akteur:innen, die das gleiche Musiklabel haben (relation=2), haben auch öfter auf den gleichen Festivals gespielt (relation=1).
c) Vernetzung: Akteur:innen, die viele Instagram-Follower:innen und Spotify-Hörer:innen haben sind auch gut mit anderen Akteur:innen vernetzt.
d) Durch den zeitliche Verlauf wollen wir die Entwicklung der Vernetzung des Gesamtneztwerkes aufzeigen. Anhand dessen könnten auch einzelne Akteur:innen herausstechen, die sich über die Jahre besser vernetzt haben.
e) Wir wollen drei Bands auswählen, die an unserem Stichtag, dem 07.03.2021, die meisten Spotify-Hörer:innen hatten. Die Vermutung liegt nahe, dass die Vernetzung dieser Bands in den Jahren von 2015 bis 2020 gestiegen ist.

Diese Arbeitshypothesen werden im Folgenden durch die Analyse des Netzwerks untersucht und entweder bestätigt oder widerlegt.

# 3. Datenerhebung: Zugang, Bereinigung und Codebuch

## 3.1 Datenzugang
Die Daten haben wir über verschiedene Websites erfasst, die die Festivalauftritte der Akteur:innen in den Jahren von 2015 bis 2020 aufzeigen (Beispiel: https://www.festivalhopper.de). Außerdem haben wir die Website der jeweiligen Akteur:innen und deren Spotify, sowie Instagram Auftritt untersucht. Das Ganze haben wir mit einer freien Recherche über Ticket-Websites, Wikipedia, Musikmagazine & Co. ergänzt.

## 3.2 Bereinigung des Datensatzes
Der Datensatz wurde nicht anonymisiert, da die Informationen ohnehin schon öffentlich zugänglich sind. Der Datensatz ist unter [Github](https://github.com/hdm-crpr/226305/tree/master/data/crpr2) verfügbar.

## 3.3 Codebuch
Das [Codebuch](https://github.com/lz029/226305-SNA-WS-21-22/blob/main/Indie/INDIE-Codebuch.md) beschreibt die Variablen, Relationen und Gewichte des Netzwerks und ist ebenfalls auf Github hinterlegt.

# 4. Analyse und Interpretation
Im Folgenden wird zuerst das Gesamtnetzwerk und somit alle Verbindungen der 35 Indie-Bands, betrachtet. Danach folgt eine Selektion in einzelne Teilnetzwerke, um unsere Arbeitshypothesen zu untersuchen. 

## 4.1 Das Gesamtnetzwerk

Das Gesamtnetzwerk umfasst 35 Knoten und 1078 Beziehungen. Es handelt sich um ein ungerichtet und gewichtet One-Mode-Netzwerk. Dieses werden wir zu Beginn in R-Studio einlesen, um eine einfache Visaulisierung darzustellen und einen ersten Überblick zu erhalten.

```{r Gesamnetzwerk erstellen, echo=FALSE, message=FALSE, warning=FALSE, paged.print=TRUE}

library(igraph)

# Einlesen der Edge- und Nodelist
el <- read.csv("https://raw.githubusercontent.com/lz029/226305-SNA-WS-21-22/main/Indie/INDIE-Edgelist.csv", header=T, as.is=T, sep = ",")
nodes <- read.csv("https://raw.githubusercontent.com/lz029/226305-SNA-WS-21-22/main/Indie/INDIE-Nodelist.csv", header=T, as.is=T, sep = ",")

# Matrix erstellen
edgematrix <-as.matrix(el)

# Zusammenführen von Edge- und Nodelist als igraph-Objekt s
indie <- graph_from_data_frame(d=edgematrix, vertices=nodes, directed=F)
indie
```

```{r Beschreibung des Netzwerks, message=FALSE, warning=FALSE, paged.print=TRUE}
# Parameter zu Beschreibung des Netzwerks
## ist das Netzwerk bereits vereinfacht?
is.simple(indie)

## besteht das Netzwerk aus Komponenten?
## wenn ja, wie vielen?
is.connected(indie)
components(indie)

## Dichte des Netzwerks
edge_density(indie, loops=FALSE)

## Umfang des Netzwerks
diameter(indie)

## Pfaddistanzen (Distance)
farthest_vertices(indie)
```
Das Hauptnetzwerk besteht aus einem Komponenten mit 35 Knoten, die alle miteinander verbunden sind. Die Dichte im Netzwerk beträgt 181,18 Prozent von allen möglichen Verbindungen. Somit ist das Inide-Netzwerk der 35 Akteure stark miteinander vernetzt. Die maximale Pfaddistanz beträgt 2 Schritte zwischen den zwei Akteuren "Amilli" und "Bilderbuch". 


Im Folgenden wird das Gesamtnetzwerk mit allen Verbindungen der 35 Indie-Bands zwischen den Jahren 2015 und 2020 angezeigt.
```{r Einfache Visualisierung des erstellten Objekt, fig.height=10, fig.width=14, message=TRUE, warning=TRUE, paged.print=TRUE}

plot(indie,
     vertex.frame.color="transparent", 
     vertex.label.family = "Arial",
     vertex.label.color = "black",
     vertex.color="lightblue",
      edge.color="grey50",
      layout = layout_components,
      main="Verbindungen von Indie-Bands 2015-2020",
     asp=0, 
     layout=layout_with_kk,
     edge.arrow.size=.5,
     vertex.size=10,)
```
In dieser Darstellung lassen sich keine genauen Zusammenhänge erklären, weshalb wir das Netzwer weiter unterteilen müssen. Was sich allerdings klar zeigt: Es gibt keine:n Musiker:in, der:die keine Verbindung zu einem:r anderen Musiker:in hat.


Das gesamte Netzwerk wird jetzt so visualisiert, dass man die Verbindungen durch Label, Feature und gemeinsame Auftritte stärker und individuell erkennen kann. Dafür werden alle Beziehungsstärke = 1, also die gemeinsamen Auftritte bei Festiavls, "transpernt" geschalten.
```{r sortiertere Visualisierung des Gesamtnetzwerks ohne Beziehungsstärke 1}

E(indie)[ (E(indie)$relation == 1) ]$color <- "transparent"
E(indie)[ (E(indie)$relation == 2) ]$color <- "cyan4"
E(indie)[ (E(indie)$relation == 3) ]$color <- "coral3"
E(indie)[ (E(indie)$relation == 4) ]$color <- "darkgoldenrod1"
      
plot(indie,
     vertex.frame.color="transparent", 
     vertex.label.family = "Arial",
     vertex.label.color = "black",
     vertex.color="lightblue",
      layout = layout_components,
      main="Verbindungen der Indie-Bands 2015-2020 - ohne Beziehungsstärke 1",
     layout=layout_with_kk,
     asp=0,
     vertex.size=10)
```
Bei dieser Visualiserung kann man erkennen, dass es einige Verbindungen der Beziehungsstärke = 2 gibt. Es gibt also mehrere Künstler:innen, die den gleichen Musiklabels angehören. Allerdings ist bei dieser Darstellung des Gesamtnetzwerkes nicht die zeitliche Komponente berücksichtigt und so lässt sich nur die Aussage treffen, dass einige Künstler:innen bei den gleichen Musiklabels innerhalb der letzten fünf Jahre waren. Die Verbindungen der Beziehungsstärke = 3 und 4 scheinen ungefähr gleich oft aufzutreten.  


Nun sollen nur die Verbindungen mit Beziehungsstärke = 1 angezeigt werden. Also alle Verbindungen, bei denen die Akteure auf dem gleichen Festival gespielt haben. Dafür werden alle anderen Beziehungsstärken auf "transparent" gesetzt.
```{r sortiertere Visualisierung des Gesamtnetzwerks nur mit Beziehungsstärke 1}

E(indie)[ (E(indie)$relation == 1) ]$color <- "gray85"
E(indie)[ (E(indie)$relation == 2) ]$color <- "transparent"
E(indie)[ (E(indie)$relation == 3) ]$color <- "transparent"
E(indie)[ (E(indie)$relation == 4) ]$color <- "transparent"
      
plot(indie,
     vertex.frame.color="transparent", 
     vertex.label.family = "Arial",
     vertex.label.color = "black",
     vertex.color="lightblue",
      layout = layout_components,
      main="Verbindungen der Indie-Bands 2015-2020 - nur Beziehungsstärke 1",
     layout=layout_with_kk,
     asp=0,
     vertex.size=10)

```
Durch die hohe Anzahl an Kanten, lässt sich hier nichts genauer erkennen. Die Musiker:innen haben also auf vielen Festivals gemeinsam gespielt.


Nun sollen nur die Verbindungen mit Beziehungsstärke = 2 angezeigt werden. Also alle Verbindungen über die Jahre, in denen die Akteure das gleiche Musiklabel hatten. Dafür werden alle anderen Beziehungsstärken auf "transparent" gesetzt. 
```{r sortiertere Visualisierung des Gesamtnetzwerks nur mit Beziehungsstärke 2}

E(indie)[ (E(indie)$relation == 1) ]$color <- "transparent"
E(indie)[ (E(indie)$relation == 2) ]$color <- "cyan4"
E(indie)[ (E(indie)$relation == 3) ]$color <- "transparent"
E(indie)[ (E(indie)$relation == 4) ]$color <- "transparent"
      
plot(indie,
     vertex.frame.color="transparent", 
     vertex.label.family = "Arial",
     vertex.label.color = "black",
     vertex.color="lightblue",
      layout = layout_components,
      main="Verbindungen der Indie-Bands 2015-2020 - nur Beziehungsstärke 2",
     layout=layout_with_kk,
     asp=0,
     vertex.size=10)

```
In dieser Visualisierung wird nochmal sichtbar, welche Musiker:innen innerhalb der letzten fünf Jahre bei den gleichen Musiklabels waren. Wie oben bereits erwähnt, wird hier nicht die zeitliche Komponente berücksichtigt und somit kann man nicht sagen, ob die Musiker:innen auch zur gleichen Zeit bei demselben Musiklabel angestellt waren. Wie unsere Recherche bestätigt hat, ist es im Bereich Indie nicht selten, dass sie Musiker:innen kleinen Labels angehören oder sogar eigene Labels gründen und somit nicht viele Gemeinsamkeiten entstehen. 


Nun sollen nur die Verbindungen mit Beziehungsstärke = 3 angezeigt werden. Also alle Verbindungen bei denen die Akteure gemeinsam auf Tour waren und/oder sich bei Auftritten gegenseitig als Vorband supported haben. Dafür werden alle anderen Beziehungsstärken auf "transparent" gesetzt.
```{r sortiertere Visualisierung des Gesamtnetzwerks nur mit Beziehungsstärke 3}

E(indie)[ (E(indie)$relation == 1) ]$color <- "transparent"
E(indie)[ (E(indie)$relation == 2) ]$color <- "transparent"
E(indie)[ (E(indie)$relation == 3) ]$color <- "coral3"
E(indie)[ (E(indie)$relation == 4) ]$color <- "transparent"
      
plot(indie,
     vertex.frame.color="transparent",
     vertex.label.family = "Arial",
     vertex.label.color = "black",
     vertex.color="lightblue",
      layout = layout_components,
      main="Verbindungen der Indie-Bands 2015-2020 - nur Beziehungsstärke 3",
     layout=layout_with_kk,
     asp=0,
     vertex.size=10)

```
Mit dieser Visualisierung wird verdeutlicht, welche Bands sich innerhalb der letzten fünf Jahre supported haben. Bei Musiker:innen wie Kraftklub, Giant Rooks, Leoniden und Fil Bo Riva sind mehrere Kanten zu sehen. Das bedeutet, dass diese Künstler:innen sich vermehrt mit anderen Musikschaffenden vernetzt haben und gemeinsam auf Tour waren und/oder sich bei Auftritten gegenseitig als Vorband supported haben. 


Nun sollen nur die Verbindungen mit Beziehungsstärke = 4 angezeigt werden. Also alle Verbindungen bei denen die Akteure gemeinsam ein Feature haben. Dafür werden alle anderen Beziehungsstärken auf "transparent" gesetzt. 
```{r sortiertere Visualisierung des Gesamtnetzwerks nur mit Beziehungsstärke 4}

E(indie)[ (E(indie)$relation == 1) ]$color <- "transparent"
E(indie)[ (E(indie)$relation == 2) ]$color <- "transparent"
E(indie)[ (E(indie)$relation == 3) ]$color <- "transparent"
E(indie)[ (E(indie)$relation == 4) ]$color <- "darkgoldenrod1"
      
plot(indie,
     vertex.frame.color="transparent",
     vertex.label.family = "Arial",
     vertex.label.color = "black",
     vertex.color="lightblue",
      layout = layout_components,
      main="Verbindungen der Indie-Bands 2015-2020 - nur Beziehungsstärke 4",
     layout=layout_with_kk,
     asp=0,
     vertex.size=10)

```
Hier wird deutlich, dass es bei den 35 Akteur:innen innerhalb der letzten fünf Jahre nicht viele gemeinsame Feature Songs gab. In der Mitte ist eine starke Vernetzung mehrer Bands zu sehen. Das liegt unter anderem an dem Feature Song „Sanifair Millionär“, bei dem die Band Blond 2020 insgesamt 17 Indie-Bands zusammengebracht hat. Davon haben wir fünf Bands in unsere Netzwerkanalyse miteinbezogen. Abgesehen von diesem großen Feature Song hat die Band AnneMayKantereit mit vier Kanten vergleichsweise viele Features.


Im Folgenden werden wir das Gesamtnetzwerk auf Cluster untersuchen.
```{r Prüfung verbundener Cluster im Gesamtnetzwerk}
# Anzahl der Clusters
clusters(indie)

# Sind die Cluster miteinander verbunden?
is_connected(indie)

# wendet die Clusterung auf das Netzwerk an
cw <- cluster_walktrap(indie)
cw

# berechnet den Modularitätswert
modularity(cw) 
membership(cw)

plot (cw, indie)
plot(cw, indie, 
     layout=layout_with_kk,
     asp=0,
     #edge.arrow.size=0.1,
     vertex.size=10,
     main="Communities im Indie Netzwerk")
```

Die Analyse zeigt: das Netzwerk besteht aus 4 miteinander verbundenen Clustern, die aus 35 Knoten bestehen. In unserem Gesamtnetzwerk sind die Cluster sehr eng miteinander verwoben und es hebt sich keine bestimmte Gruppierung davon ab. Somit lohnt es sich nicht eine der Cluster Gruppen genauer zu analysieren.


## 4.2 Teilnetzwerke 

Im Folgenden werden die Verbindungen aller Bands nach Jahren aufgeteilt. Dadurch sollen Unterschiede besser zur Gelung kommen. In welchem Jahr waren die meisten Bands aktiv? Wie wirkt sich das Corona-Jahr 2020 auf unsere Bands aus? Um Unterschiede direkt sichtbarer zu machen, wird hier der normale Befehl "layout_with_kk" durch den Befehl "layout_in_circle" ersetzt. So bleiben alle Bands an gleicher Stelle und die sechs Teilnetzwerke können besser miteinander verglichen werden.

```{r Teilnetzwerke nach Jahren,fig.height=10, fig.width=14, message=FALSE, warning=FALSE, paged.print=FALSE}

list.edge.attributes(indie)
edge.attributes(indie)$time

# Teilnetzwerke nach Jahren erstellen
y2015 <- subgraph.edges(indie, E(indie)[time=="2015"])
y2016 <- subgraph.edges(indie, E(indie)[time=="2016"])
y2017 <- subgraph.edges(indie, E(indie)[time=="2017"])
y2018 <- subgraph.edges(indie, E(indie)[time=="2018"])
y2019 <- subgraph.edges(indie, E(indie)[time=="2019"])
y2020 <- subgraph.edges(indie, E(indie)[time=="2020"])

# Visualisierung: Vergleichen aller Jahre mit dem Gesamtnetzwerk
E(indie)[ (E(indie)$relation == 1) ]$color <- "gray85"
E(indie)[ (E(indie)$relation == 2) ]$color <- "cyan4"
E(indie)[ (E(indie)$relation == 3) ]$color <- "coral3"
E(indie)[ (E(indie)$relation == 4) ]$color <- "darkgoldenrod1"

plot(indie, layout=layout_in_circle, main="Gesamt",
     vertex.frame.color="transparent", 
     vertex.label.family = "Arial",
     vertex.label.color = "black",
     vertex.color="lightblue",
      layout = layout_components,
     asp=0,
     vertex.size=10)

plot(y2015, layout=layout_in_circle, main="2015",
     vertex.frame.color="transparent", 
     vertex.label.family = "Arial",
     vertex.label.color = "black",
     vertex.color="lightblue",
      layout = layout_components,
     asp=0,
     vertex.size=10)

plot(y2016, layout=layout_in_circle, main="2016",
     vertex.frame.color="transparent", 
     vertex.label.family = "Arial",
     vertex.label.color = "black",
     vertex.color="lightblue",
      layout = layout_components,
     asp=0,
     vertex.size=10)

plot(y2017, layout=layout_in_circle, main="2017",
     vertex.frame.color="transparent", 
     vertex.label.family = "Arial",
     vertex.label.color = "black",
     vertex.color="lightblue",
      layout = layout_components,
     asp=0,
     vertex.size=10)

plot(y2018, layout=layout_in_circle, main="2018",
     vertex.frame.color="transparent", 
     vertex.label.family = "Arial",
     vertex.label.color = "black",
     vertex.color="lightblue",
      layout = layout_components,
     asp=0,
     vertex.size=10)

plot(y2019, layout=layout_in_circle, main="2019" ,
     vertex.frame.color="transparent", 
     vertex.label.family = "Arial",
     vertex.label.color = "black",
     vertex.color="lightblue",
      layout = layout_components,
     asp=0,
     vertex.size=10)

plot(y2020, layout=layout_in_circle, main="2020",
     vertex.frame.color="transparent", 
     vertex.label.family = "Arial",
     vertex.label.color = "black",
     vertex.color="lightblue",
      layout = layout_components,
     asp=0,
     vertex.size=10)

par(mfrow=c(1,1), mar=c(1,1,1,1))
```
Deutlich zu erkennen ist, dass das Zerlegen der Verbindungen in Teilnetzwerke nach Jahren eine deutliche Entzerrung mit sich gebracht hat. Sofort ins Auge springt wohl das Teilnetzwerk des Jahres 2020, das durch im Vergleich deutlich weniger Kanten auffällt. Grund hierfür sind die fehlenden Festivals, die aufgrund der Covid-19-Pandemie in diesem Jahr ausblieben. Gleichzeitig sind die sonst nur sporadisch verteilten gelben Kanten, die die Verbindung zweier Knoten durch ein gemeinsames Feature (relation=4) kennzeichnet, ein Merkmal des Teilnetzwerkes 2020. Diese sind größtenteils dem "Mammut-Feature" Sanifair Millionaire zuzuschreiben, das 5 der untersuchten Bands miteinander verbindet.
Eine weiter Auffälligkeit bringt das Teilnetzwerk des Jahres 2015 mit sich, denn auch hier gehen von einigen Bands im Vergleich zu den anderen Jahren (mit Ausnahme von 2020) deutlich weniger Kanten aus. Die Ursache hierfür findet sich vermutlich in der Tatsache, dass viele der in unserer Netzwerkanalyse untersuchten Bands im Jahr 2015 noch nicht aktiv waren oder erst im Laufe der Jahre "groß" genug wurden, um auf vielen Festivals Auftritte zu ergattern.

```{r Netzwerkmaße der Teilnetzwerke nach Jahren,fig.height=10, fig.width=14, message=FALSE, warning=FALSE, paged.print=FALSE}
#Degree-Werte der Teilnetzwerke
d_indie <- degree(indie)
d_indie
which.max(d_indie)
d_y2015 <- degree(y2015)
d_y2015
which.max(d_y2015)
d_y2016 <- degree(y2016)
d_y2016
which.max(d_y2016)
d_y2017 <- degree(y2017)
which.max(d_y2017)
d_y2018 <- degree(y2018)
which.max(d_y2018)
d_y2019 <- degree(y2019)
which.max(d_y2019)
d_y2020 <- degree(y2020)
which.max(d_y2020)

# Dichte
edge_density(indie, loops=FALSE)
edge_density(y2015, loops=FALSE)
edge_density(y2016, loops=FALSE)
edge_density(y2017, loops=FALSE)
edge_density(y2018, loops=FALSE)
edge_density(y2019, loops=FALSE)
edge_density(y2020, loops=FALSE)
```

Betrachtet man die Dichten der sechs Teilnetzwerke, liegt die höchste Dichte bei 2017 mit 66,13 Prozent, dicht gefolgt von 2018 mit 64,53 Prozent. Wenig verwunderlich ist das Jahr 2020, das sich wie im vorherigen Abschnitt bereits beschrieben vor allem durch die fehlenden Festival-Verbindungen auszeichnet. Insofern ist die bei lediglich 18,97 Prozent liegende Dichte in diesem Jahr keine Überraschung.

```{r Erneutes einlesen des Gesamnetzwerk, echo=FALSE, message=FALSE, warning=FALSE, paged.print=TRUE}
library(igraph)
# Einlesen der Edge- und Nodelist
el <- read.csv("https://raw.githubusercontent.com/lz029/226305-SNA-WS-21-22/main/Indie/INDIE-Edgelist.csv", header=T, as.is=T, sep = ",")
nodes <- read.csv("https://raw.githubusercontent.com/lz029/226305-SNA-WS-21-22/main/Indie/INDIE-Nodelist.csv", header=T, as.is=T, sep = ",")
# Matrix erstellen
edgematrix <-as.matrix(el)
# Zusammenführen von Edge- und Nodelist als igraph-Objekt s
indie <- graph_from_data_frame(d=edgematrix, vertices=nodes, directed=F)
indie
```

```{r Teilnetzwerke nach Relations}

# Um die Verteilung nach Relations besser veranschaulichen zu können, werden Teilnetzwerke nach den unterschiedlichen Verbindungen (1-4) sortiert und anschließend auf ihre Netzwerkmaße überprüft

E(indie)[ (E(indie)$relation == 1) ]$color <- "gray85"
E(indie)[ (E(indie)$relation == 2) ]$color <- "cyan4"
E(indie)[ (E(indie)$relation == 3) ]$color <- "coral3"
E(indie)[ (E(indie)$relation == 4) ]$color <- "darkgoldenrod1"
      

indie1 <- subgraph.edges(indie, E(indie)[relation=="1"])
plot(indie1,
     vertex.frame.color="transparent", 
     vertex.label.family = "Arial",
     vertex.label.color = "black",
     vertex.color="lightblue",
      layout = layout_components,
      main="Teilnetzwerk Relation 2",
     layout=layout_with_kk,
     asp=0,
     vertex.size=10)

indie2 <- subgraph.edges(indie, E(indie)[relation=="2"])
plot(indie2,
     vertex.frame.color="transparent", 
     vertex.label.family = "Arial",
     vertex.label.color = "black",
     vertex.color="lightblue",
      layout = layout_components,
      main="Teilnetzwerk Relation 2",
     layout=layout_with_kk,
     asp=0,
     vertex.size=10)

indie3 <- subgraph.edges(indie, E(indie)[relation=="3"])
plot(indie3,
     vertex.frame.color="transparent",
     vertex.label.family = "Arial",
     vertex.label.color = "black",
     vertex.color="lightblue",
      layout = layout_components,
      main="Teilnetzwerk Relation 3",
     layout=layout_with_kk,
     asp=0,
     vertex.size=10)

indie4 <- subgraph.edges(indie, E(indie)[relation=="4"])
plot(indie4,
     vertex.frame.color="transparent",
     vertex.label.family = "Arial",
     vertex.label.color = "black",
     vertex.color="lightblue",
      layout = layout_components,
      main="Teilnetzwerk Relation 3",
     layout=layout_with_kk,
     asp=0,
     vertex.size=10)

```

```{r Teilnetzwerke nach Relations und ihre Netzwerkmaße}

# Netzwerkmaße Teilnetzwerk Relation 1 

edge_density(indie1)
degree(indie1)

# Netzwerkmaße Teilnetzwerk Relation 2 

edge_density(indie2)
degree(indie2)

# Netzwerkmaße Teilnetzwerk Relation 3 

edge_density(indie3)
degree(indie3)

# Netzwerkmaße Teilnetzwerk Relation 4

edge_density(indie4)
degree(indie4)

```
Bei der Betrachtung der Teilnetzwerke nach Relations bestätigt sich, was sich bereits bei der Visualisierung des Gesamtnetzwerkes angedeutet hat.Umso stärker die Verbindung, also enger die Zusammenarbeit zwischen den Künstler:innen, desto kleiner werden die Teilnetzwerke. Daraus ergibt sich auch die abfallende Netzwerkdichte mit aufsteigender Verbindungsstärke. Während auf den Festivals noch sehr viele Bands aufeinander treffen, haben nur wenige ein Feature oder eine gemeinsame Tour. Ein gemeinsamer Festival Auftritt ist auch nicht mit einer bewusst gewählten Vernetzung gleichzusetzten, hier kann allenfalls davon ausgegangen werden, dass die Künstler:innen sich gegenseitig kennen. Bei einem Feature oder der Wahl einer Vorband ist eine bewusst gewählte Vernetzung anzunehmen. Auch bilden sich Gruppen die keine Verbindungen zueinander aufweisen. Oder Gruppen in denen die Künstler:innen untereinander gut vernetzt sind. Das lässt sich in dem Sinne interpretieren, dass nach einer engen Zusammenarbeit weitere Verbindungen zu der dem Künstler oder der Künstlerin nahestehenden Dritten entsteht. Zu beachten gilt es aber dabei, dass bei einem gemeinsamen Feature mehr als zwei Künstler:innen beteiligt sein können. Bei den Beziehungen 2-4 lassen sich ebenfalls einzelne Gruppierungen erkennen.

##4.3 Analyse eines herausgehobenen Akteurs in Egonetzwerken 
Da unser Netzwerk sehr viele Akteure und sehr viele Verbindungen zeigt, wollen wir uns im Folgenden auf einen Akteur fixieren. Hierfür wählen wir die Band mit der stärksten Vernetzung, also dem höchsten Degreewert, um anschließend nach Jahren geordnete Egonetzwerke zu erstellen die die Kollaborationen deutlicher und übersichtlicher darstellen sollen.

```{r Analyse eines herausgehobenen Akteurs in Egonetzwerken}
# Im Folgenden sollen die Kollaborationen einer Band explizit analysiert werden. Hierfür wählen wir die Band mit dem höchsten Degreewert.

# degree-Werte bestimmen
i_deg <- degree(indie)
i_deg

#höchster degree-Wert auslesen
which.max(degree(indie))
# Von wegen Lisbeth ist die Band mit dem höchsten Degreewert, wie man auch schon oben auslesen konnte.

#Um die Kollaborationen von Von wegen Lisbeth übersichtlicher zu zeigen, teilen wir sie nach Jahren ein und erstellen Egonetzwerke, die die Entwicklung der Von wegen Lisbeth-Zusammenarbeiten über die Jahre hinweg anzeigen.

# In Jahre einteilen
vwl2015 <- subgraph.edges(indie, E(indie)[time=="2015"])
vwl2016 <- subgraph.edges(indie, E(indie)[time=="2016"])
vwl2017 <- subgraph.edges(indie, E(indie)[time=="2017"])
vwl2018 <- subgraph.edges(indie, E(indie)[time=="2018"])
vwl2019 <- subgraph.edges(indie, E(indie)[time=="2019"])
vwl2020 <- subgraph.edges(indie, E(indie)[time=="2020"])

# Egonetzwerk von Von wegen Lisbeth zu den einzelnen Jahren erstellen
## 2015
ego2015 <- make_ego_graph(vwl2015, order = 1, nodes = V(vwl2015)$name == "Von wegen Lisbeth", mode ="all")
ego2015 <- ego2015[[1]]
ego2015

# Egonetzwerk von Von wegen Lisbeth zu den einzelnen Jahren erstellen
## 2016
ego2016 <- make_ego_graph(vwl2016, order = 1, nodes = V(vwl2016)$name == "Von wegen Lisbeth", mode ="all")
ego2016 <- ego2016[[1]]
ego2016

# Egonetzwerk von Von wegen Lisbeth zu den einzelnen Jahren erstellen
## 2017
ego2017 <- make_ego_graph(vwl2017, order = 1, nodes = V(vwl2017)$name == "Von wegen Lisbeth", mode ="all")
ego2017 <- ego2017[[1]]
ego2017

# Egonetzwerk von Von wegen Lisbeth zu den einzelnen Jahren erstellen
## 2018
ego2018 <- make_ego_graph(vwl2018, order = 1, nodes = V(vwl2018)$name == "Von wegen Lisbeth", mode ="all")
ego2018 <- ego2018[[1]]
ego2018

# Egonetzwerk von Von wegen Lisbeth zu den einzelnen Jahren erstellen
## 2019
ego2019 <- make_ego_graph(vwl2019, order = 1, nodes = V(vwl2019)$name == "Von wegen Lisbeth", mode ="all")
ego2019 <- ego2019[[1]]
ego2019

# Egonetzwerk von Von wegen Lisbeth zu den einzelnen Jahren erstellen
## 2020
ego2020 <- make_ego_graph(vwl2020, order = 1, nodes = V(vwl2020)$name == "Von wegen Lisbeth", mode ="all")
ego2020 <- ego2020[[1]]
ego2020

# Zuletzt werden alle Egonetzwerke neben- und übereinander visualisiert um sie vergleichen zu können.

par(mfrow=c(2,3), mar=c(1,1,1,1))

## Jahr 2015

# Netzwerk entzerren
l <- layout_with_kk(ego2015)
l <- norm_coords(l, ymin=-1, ymax=1, xmin=-1, xmax=1)

# Verbindungen erster Ordnung hervorheben
inc.edges <- incident(ego2015,  V(ego2015)[name=="Von wegen Lisbeth"], mode="all")

# Knoten und Kanten speziell einfärben
ecol <- rep("transparent", ecount(ego2015))
ecol[inc.edges] <- "gray50"
vcol <- rep("lightblue", vcount(ego2015))
vcol[V(ego2015)$name=="Von wegen Lisbeth"] <- "gold"
plot(ego2015, 
     vertex.label.family = "Arial",
     vertex.color=vcol, 
     edge.color=ecol,
     vertex.label.color="black",
     vertex.frame.color="transparent",
     rescale=F, layout=l*1,
     main="'Von wegen Lisbeth' 2015")

## Jahr 2016

# Netzwerk entzerren
l <- layout_with_kk(ego2016)
l <- norm_coords(l, ymin=-1, ymax=1, xmin=-1, xmax=1)

# Verbindungen erster Ordnung hervorheben
inc.edges <- incident(ego2016,  V(ego2016)[name=="Von wegen Lisbeth"], mode="all")

# Knoten und Kanten speziell einfärben
ecol <- rep("transparent", ecount(ego2016))
ecol[inc.edges] <- "gray50"
vcol <- rep("lightblue", vcount(ego2016))
vcol[V(ego2016)$name=="Von wegen Lisbeth"] <- "gold"
plot(ego2016, 
     vertex.label.family = "Arial",
     vertex.color=vcol, 
     edge.color=ecol,
     vertex.label.color="black",
     vertex.frame.color="transparent",
     rescale=F, layout=l*1,
     main="'Von wegen Lisbeth' 2016")


## Jahr 2017

# Netzwerk entzerren
l <- layout_with_kk(ego2017)
l <- norm_coords(l, ymin=-1, ymax=1, xmin=-1, xmax=1)

# Verbindungen erster Ordnung hervorheben
inc.edges <- incident(ego2017,  V(ego2017)[name=="Von wegen Lisbeth"], mode="all")

# Knoten und Kanten speziell einfärben
ecol <- rep("transparent", ecount(ego2017))
ecol[inc.edges] <- "gray50"
vcol <- rep("lightblue", vcount(ego2017))
vcol[V(ego2017)$name=="Von wegen Lisbeth"] <- "gold"
plot(ego2017, 
     vertex.label.family = "Arial",
     vertex.color=vcol, 
     edge.color=ecol,
     vertex.label.color="black",
     vertex.frame.color="transparent",
     rescale=F, layout=l*1,
     main="'Von wegen Lisbeth' 2017")


## Jahr 2018

# Netzwerk entzerren
l <- layout_with_kk(ego2018)
l <- norm_coords(l, ymin=-1, ymax=1, xmin=-1, xmax=1)

# Verbindungen erster Ordnung hervorheben
inc.edges <- incident(ego2018,  V(ego2018)[name=="Von wegen Lisbeth"], mode="all")

# Knoten und Kanten speziell einfärben
ecol <- rep("transparent", ecount(ego2018))
ecol[inc.edges] <- "gray50"
vcol <- rep("lightblue", vcount(ego2018))
vcol[V(ego2018)$name=="Von wegen Lisbeth"] <- "gold"
plot(ego2018, 
     vertex.label.family = "Arial",
     vertex.color=vcol, 
     edge.color=ecol,
     vertex.label.color="black",
     vertex.frame.color="transparent",
     rescale=F, layout=l*1,
     main="'Von wegen Lisbeth' 2018")


## Jahr 2019

# Netzwerk entzerren
l <- layout_with_kk(ego2019)
l <- norm_coords(l, ymin=-1, ymax=1, xmin=-1, xmax=1)

# Verbindungen erster Ordnung hervorheben
inc.edges <- incident(ego2019,  V(ego2019)[name=="Von wegen Lisbeth"], mode="all")

# Knoten und Kanten speziell einfärben
ecol <- rep("transparent", ecount(ego2019))
ecol[inc.edges] <- "gray50"
vcol <- rep("lightblue", vcount(ego2019))
vcol[V(ego2019)$name=="Von wegen Lisbeth"] <- "gold"
plot(ego2019, 
     vertex.label.family = "Arial",
     vertex.color=vcol, 
     edge.color=ecol,
     vertex.label.color="black",
     vertex.frame.color="transparent",
     rescale=F, layout=l*1,
     main="'Von wegen Lisbeth' 2019")

## Jahr 2020

# Netzwerk entzerren
l <- layout_with_kk(ego2020)
l <- norm_coords(l, ymin=-1, ymax=1, xmin=-1, xmax=1)

# Verbindungen erster Ordnung hervorheben
inc.edges <- incident(ego2020,  V(ego2020)[name=="Von wegen Lisbeth"], mode="all")

# Knoten und Kanten speziell einfärben
ecol <- rep("transparent", ecount(ego2020))
ecol[inc.edges] <- "gray50"
vcol <- rep("lightblue", vcount(ego2020))
vcol[V(ego2020)$name=="Von wegen Lisbeth"] <- "gold"
plot(ego2020, 
     vertex.label.family = "Arial",
     vertex.color=vcol, 
     edge.color=ecol,
     vertex.label.color="black",
     vertex.frame.color="transparent",
     rescale=F, layout=l*1,
     main="'Von wegen Lisbeth' 2020")


par(mfrow=c(1,1), mar=c(1,1,1,1))
```
Wie sich herausgestellt hat, ist die Band Von wegen Lisbeth am stärksten mit den anderen untersuchten Indie-Bands vernetzt. Über die sechsjährige Zeitspanne hat sie einen Degreewert von 154 erreicht. Dies geht besonders auf viele Festivalauftritte, aber auch sonstige Kollaborationen mit fast allen Bands aus dem Netzwerk zurück. 
Schaut man sich nun zusätzlich die Zusammenarbeiten verteilt über die einzelnen Jahre an, kann mann man feststellen, dass sich die 2006 gegründete Band in den Jahren 2015-2018 immer stärker vernetzt hat. Und in der Tat hat die Erfolgsgeschichte von Von wegen Lisbeth mit der engen Zusammenarbeit mit AnnenMayKantereit ab 2014 begonnen. Diese Zusammenarbeit lässt sich somit auch hier als eine der einzigen im Jahr 2015 erkennen. In diesem Jahr war Von wegen Lisbeth bei 18 Konzerten einer AnnenMayKantereit-Tour Vorband (vgl. Von wegen Lisbeth, 2021). Annenmaykantereit bleiben auch in den nächsten Jahren ein steter Begleiter von Von wegen Lisbeth. Diese beginnen sich dennoch auch mit anderen Bands stark zu vernetzen. So sind 2016 schon viel mehr Kollaborationen erkennbar, die insbesondere von gemeinsamen Festivalauftritten her rühren. 
Besonders auffällig eng vernetzt sind Von wegen Lisbeth 2016 mit Giant Rooks. 2017 sind diese ebenfalls am engsten an Von wegen Lisbeth, gemeinsam mit Milliarden, Kraftklub und Fil Bo Riva. 2018 wird selbst dieses aufgedröselte Teilnetzwerk wieder sehr unübersichtlich, da Von wegen Lisbeth äußerst aktiv ist. Neben den genannten Akteuren werden nun auch Leoniden und Bosse häufig auf den selben Bühnen gesehen. 2019 nehmen die Kollaborationen dann wieder ab. Insbesondere sind Von wegen Lisbeth jetzt mit ihrer neuen Platte unterwegs und kollaborieren in dieser Zeit fast nur mit Vorbands (vgl. Von wegen Lisbeth, 2021). Aus unserer Untersuchung sind das insbesondere Milliarden und Blond.
Blond prägt auch unsere Untersuchung für das Jahr 2020 am stärksten. Dort erscheint nämlich das von Blond initiierte Feature "Sanifair-Millionär" wo unter anderem Von wegen Lisbeth, Drangsal, Rikas, Leoniden und Fibel mitwirken. Ansonsten hat Von wegen Lisbeth 2020 aufgrund der Pandemie kaum Kollaborationen vorzuweisen.
Es scheint, dass eine Band wie Von wegen Lisbeth in den ersten Jahren des Erfolgs (2015-2018) viele Verbindungen zu ähnlichen Bands aufbaut, viel spielt und viel unterwegs ist. Mit dem größeren Erfolg, den die Band 2019 erreicht, kann sie sich leisten eigene Vorbands dazuzuholen, weniger Festivals zu spielen und musikalische Projekte mit anderen Bands einzugehen. Die bloße Masse an Kollaborationen nimmt hierdurch aber ab

## 4.4 Zusammenhang zwischen Degree-Wert und Spotify/Instagram
Im folgenden werden die einzelnen Künstler:innen und Bands hinsichtlich degree-Wert, Spotify-Hörer:innen und Instagram-Folloer:innen miteinander verglichen. Zudem wird überprüft ob ein Zusammenhang zwischen den einzelnen Kategorien besteht.

```{r Zusammenhang höchster Degree mit Spotify-Hörer:innen bzw. Instagram Follower:innen} 
setwd("~/Schicht im Schacht")
tabelle_csv <- read.csv2("tabelle.csv")
tabelle_csv

# degree Gesamtnetzwerk berechnen

dindie <- degree(indie)
dindie
plot(dindie)


```     
Den höchsten degree-Wert hat wie bereits festgestellt die Band Von Wegen Lisbeth mit einem Wert von 154, gefolgt von Annenmaykantereit mit 117 und Leoniden mit 107. Vergleicht man alle Bands und Künstler:innen anhand ihres degree-Wert, den Spotify-Hörer:innen sowie Instagram-Follower:innen ergeben sich unter anderem folgende Auffälligkeiten:

- Annenmaykantereit bei allen drei Kategorien unter den Top 2
- viele Bands spielen sich komplett im unteren Drittel der Tabelle hab, was einen Zusammenhang bedeuten kann
- vielen Bands komplett im oberen Drittel
- Faktoren wie internationale Bekanntheit führen dazu das manche Bands einen eher niedrigen degree im Vergleich zu ihren Follower*innen und Hörer:innen haben (Milky Chance)
- andere Bekanntheitsfaktoren neben der Musik führen dazu das Follower*innenzahl viel höher ist als der Rest (Olli Schulz - fest und flauschig)
- Bands wie Provinz, die erst in Coronazeiten wirklich bekannt wurden haben einen vergleichsweise niedrigen degree trotz hoher Hörer:innen - und Follower:innenanzahl
- es gibt scheinbare "Festivalbands" die weder besonders hohe Follower:innen- noch Hörer:innenanzahl haben und dennoch einen vergleichsweise hohen degree

# 5. Disskussion, Fazit und Ausblick 

## Fazit
Die zunehmende und zum Jahr 2020 wieder abnehmende Vernetzung zeigte sich besonders übersichtlich am Beispiel der Band Von wegen Lisbeth. Sie hatte sich besonders im von uns beschriebenen Zeitraum entwickelt und damit die stärkste Vernetzung aufgebaut. Es gibt in der Indie-Szene offensichtlich sehr zentrale, populäre Akteure wie Von wegen Lisbeth und AnnenMayKantereit, die die Bands und Künster:innen der Szene entscheidend miteinander vernetzen.

a) Auftritte: Akteur:innen, die oft auf den gleichen Festivals aufgetreten sind, haben eher ein gemeinsames Feature und haben eher gemeinsame Auftritte oder sind die Vorband des:r jeweils anderen Akteur:in.
b) Zusammenarbeit: Akteur:innen, die das gleiche Musiklabel haben (relation=2), haben auch öfter auf den gleichen Festivals gespielt (relation=1).
c) Vernetzung: Akteur:innen, die viele Instagram-Follower:innen und Spotify-Hoerer:innen haben sind auch gut mit anderen Akteur:innen vernetzt.
Unsere dritte Hypothese über den Zusammenhang zwischen degree und Instagram- Follower:innen bzw. Spotify-Hoerer:innen laesst sich bestätigen. Mit einigen Ausnahmen kann man sagen, dass die Kuenstler:innen, die sich im oberen bzw unteren Drittel der degree-Werte aufhalten, sich auch gleichermaßen bei den Spotify und Instagram-Werten im jeweiligen Drittel einordnen.
d) Durch den zeitliche Verlauf wollen wir die Entwicklung der Vernetzung des Gesamtneztwerkes aufzeigen. Anhand dessen könnten auch einzelne Akteur:innen herausstechen, die sich über die Jahre besser vernetzt haben.
Durch das Aufteilen des Gesamtnetzwerkes nach Jahren lassen sich wie erwartet spannende Entwicklungen beobachte, besonders wenn man die Kuenstler:innen im einzelnen betrachtet. Die Band Kraftklub zum Beispiel, hatte 2017-2018 ein Hoch und hat auf ganz vielen Festivals gepsielt, sich die Jahre danach dann aber komplett zurückgezogen.
e) Wir wollen drei Bands auswählen, die an unserem Stichtag, dem 07.03.2021, die meisten Spotify-Hörer:innen hatten. Die Vermutung liegt nahe, dass die Vernetzung dieser Bands in den Jahren von 2015 bis 2020 gestiegen ist.

## Limitationen
Unsere Forschung muss aus unterschiedlichen Gründen mit deutlichen Einschränkungen analysiert werden. Zur Erfassung von Zusammenarbeiten in Form von Festivals, Labels, gemeinsamen Auftritten und Features, stand uns nur eine lückenhafte Datenbasis zur Verfügung. Unsere Quellen waren die Webseiten der Bands, Künstler:innen Festivals und Labels, lokale Berichterstattung, Musikmagazine und Übersichtsseiten für Festival-Line-Ups. Eine professionelle und sichere Plattform, die alle benötigten Informationen bereitstellte gab es nicht. Es ist also nicht auszuschließen, dass Akteure und Verbindungen in unserem Netzwerk fehlen.
Außerdem haben wir nur Bands und Künstler:innen untersucht, die in den vergangenen fünf Jahren auf den größten deutschen Festivals vertreten waren. Theoretisch wäre aber denkbar, dass es Bands oder Künstler:innen gibt, die gut in der Indie-Szene vernetzt sind, aber gar nicht auf großen Festivals auftreten. Auch diese würden in dieser Netzwerkforschung nicht erfasst.
Außerdem sind unsere Erkenntnisse dadurch beschränkt, dass nur die vergangenen fünf Jahre untersucht wurden. Indie-Bands oder Künstler:innen die für die Szene von großer Bedeutung sein könnten, aber nur davor auf Festivals auftraten, wurden nicht erfasst. 
Darüber hinaus ist die Abgrenzung der Indie-Szene unklar. Zwar haben wir hierzu Einschätzungen aus Musikmagazinen herangezogen und so Bands und Künstler:innen der Szene zugeordnet, mangels klarer Definition gibt es aber auch hier Spielraum für andere Auslegungen.
Zuletzt stellt das Ausnahmejahr 2020 eine Einschränkung dieser Netzwerkforschung dar. Erkenntnisse aus unserem Netzwerk lassen sich kaum auf andere Sechs-Jahres-Zyklen übertragen. 2020 fanden kaum Veranstaltungen statt - auch Kollaborationen wurden hierdurch stark eingeschränkt und unser Netzwerk beschreibt im letzten Jahr eine Ausnahmesituation die so mit den Vorjahren nicht vergleichbar ist.

## Ausblick
Bei der Vorrecherche ist aufgefallen, dass Netzwerke in der Musikszene kaum erforscht werden. Um die Fragen: Wie werden Bands erfolgreich? Welche Synergien können Bands nutzen? Wie hat sich die Struktur von Musikszenen entwickelt? zu klären wäre die Netzwerkforschung aber durchaus ein probates Mittel.
Die Forschung über Zusammenarbeiten in der Musik könnte auf andere Genre und Zeiträume übertragen werden. Hier bieten sich  auch Vergleiche zur Indie-Szene an. Auch im kleineren, weniger kommerziellen Rahmen wäre eine tiefere Forschung möglich, um festzustellen wo Künstler:innen auftreten müssen und mit wem sie zusammenarbeiten müssen um erfolgreich zu sein.
  
# 6. Literatur 

Bundesverband der Konzert und Veranstaltungswirtschaft. (2020). Musikwirtschaft in Deutschland 2020. Abgerufen von https://bdkv.de/marktstudien/

Goethe Institut. (2016). Indie-Musiklabels in Deutschland - Alternative zum Mainstream. Abgerufen von https://www.goethe.de/de/kul/mus/20805417.html

Musik3000. (2020). Blond feiern „Sanifair Millionär Cypher“ mit vielen bekannten Features. Abgerufen von http://musik3000.de/blond-feiern-sanifair-millionaer-cypher-mit-vielen-bekannten-features/

Nagel, D. (2019). Die fünf wichtigsten Showcase Festivals—Tipps für Musiker und Bands—Backstage PRO. Abgerufen von http://www.backstagepro.de/thema/die-fuenf-wichtigsten-showcase-festivals-2019-03-28-1FXjg47yQr

Noka, J. (9. Juli 2019). Das Geschäft mit Social Media: Die Musikbranche passt sich an!. Media Bubble. Abgerufen von https://media-bubble.de/das-geschaeft-mit-social-media-die-musikbranche-passt-sich-an/

Schöbel, N. (23. August 2016)  Social Media für Musiker: 23 Fragen zum Erfolg | MUSIK MARKETING. MUSIK-MARKETING.NET. Abgerufen von https://musik-marketing.net/schildhauer-social-media-musiker/

Seawood, L. W. (2016). What Instagram Discovered in Our First Nielsen Music Study. Medium. Abgerufen von: https://medium.com/cuepoint/what-instagram-discovered-in-our-first-nielsen-music-study-de1a2740c005

Von Wegen Lisbeth (2021). Konzerte. Abgerufen von https://www.vonwegenlisbeth.de/konzerte/

Winkler, S. (2. März 2020). Wie Genres immer diffuser werden – außer im deutschen Pop. DIE WELT. Abgerufen von https://www.welt.de/kmpkt/article206099115/Wie-Genres-immer-diffuser-werden-ausser-im-deutschen-Pop.html   

## 7. Codebuch
[Codebuch](https://github.com/hdm-crpr/226305/blob/master/data/crpr2/codebuch.md)

```{r Übersicht Netzwerkattribute}
list.vertex.attributes(indie)
# vertex.attributes(s)
list.edge.attributes(indie)
# edge.attributes(s)
```

Das Netzwerk hat nach dem [Codebuch](https://github.com/lz029/226305-SNA-WS-21-22/blob/main/Indie/INDIE-Codebuch.md) folgende Attribute:

*Vertex-Attribute*
id
Identische ID wie aus der Edgelist zur Identifikation der Knoten

name
Name des/der Künstler_in bzw. Band

personen
Anzahl der Mitglieder

musiklabel
Aktuelles und frühere Musiklabel der Band bzw. Künster_in

instagram
Anzahl der Instagram-Follower_innen zum Stichtag 07.03.2021 in Tausenden

spotify
Monatliche Hörer_innen auf Spotify zum Stichtag 07.03.2021 in Tausenden

Die Vertex-Attribute treffen auf alle Knoten zu.

*Edge-Attribute*
id
(eindeutige Codierung des Knoten)
codiert nach den ersten vier Buchstaben der Künstler_innen und Bands, jede ID entspricht einem/einer Künstler_in bzw. Band

weight
Beziehungsstärke
4 = Feature (Gemeinsamer Song)
3 = Gemeinsam auf Tour / gemeinsame Auftritte / Support
2 = gemeinsames Musiklabel
1 = Auf dem selben Festival

time
Jahreszahl der Kooperation als YYYY

source
Informationsquelle zu der Kooperation

what
Art der Kooperation

Die Edge-Attribute treffen auf alle Verbindungen zu.


## Datenmaterial und Skript
[Datensatz](https://github.com/lz029/226305-SNA-WS-21-22/tree/main/Indie)

## Team, Arbeitsaufwand und Lessons Learned

### Teammitglieder
Silas Schwab (ss502)
Fabienne Schackert (fs138)
Lena Klasen (lk158)
Lioba Zangenfeind (lz029)
Selina Hellfritsch (sh308)

### Arbeitsaufwand und Rollen im Team
NN: Projektleitung und Coding, ca. 80 Stunden
NN: Literaturrecherche und Auswertung, ca. 80 Stunden
NN: Endbericht und Visualiserung, ca. 80 Stunden


### Lessons learned
Wir haben besonders am Anfang die Arbeit sehr unterschätzt. Wir haben nicht lange genug über das enorme Ausmaß unserer Datenerhebung nachgedacht und viel zu viele Daten erhoben. Die Datenerhebung werden wir somit beim nächsten Mal gut überlegt angehen und uns im Voraus mehr Gedanken darüber machen, in welcher Dimension wir die Daten erheben.
Ansonsten haben wir gelernt, dass gute Arbeitsaufteilung und Strukturierung wichtig sind. Jede*r hatte von Anfang an ihr Aufgabengebiet, was ideal war und durch wöchentliche Treffen konnten wir uns vor einem stressigen Ende bewahren, da wir im Voraus bereits viel gearbeitet haben.
Was R angeht hatten wir unsere Schwierigkeiten, haben aber gelernt uns nicht abschrecken zu lassen und sind so zu einem für uns zufriedenstellenden Ergebnis gekommen.
```
