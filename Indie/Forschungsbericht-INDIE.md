---
title: "226305 Forschungsbericht der Gruppe Musikszene Indie"
author: "Silas Schwab | ss502@hdm-stuttgart.de, Fabienne Schackert | fs138@hdm-stuttgart.de, Lena Klasen | lk158@hdm-stuttgart.de, Lioba Zangenfeind | lz029@hdm-stuttgart.de, Selina Hellfritsch | sh308@hdm-stuttgart.de
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
editor_options: 
  markdown: 
    wrap: sentence
---

*Anmerkung*: Wir werden in unserem Forschungsbericht teilweise die Netzwerke neu erstellen und einlesen, damit die Datenbasis immer klar ist. Somit können wir in den einzelnen Teilnetzwerken sicherstellen, dass nur aktuelle Werte erfasst werden.

**Abstract und Keywords**

Gegenstand dieser Forschungsarbeit ist ein ungerichtetes One-Mode-Netzwerk, das die Beziehungen von 35 Akteuren in Form von Musiker:innen und Bands aus der Indie-Szene illustriert und in Zusammenhang stellt. Dabei untersucht wurden die Beziehungen dieser Akteure hinsichtlich gemeinsamer Auftritte auf Festivals, gemeinsamer Labels, gemeinsamer Tour- und Support-Auftritte sowie gemeinsamer Feature-Songs in den Jahren 2015 bis 2020. Darüber hinaus wurde das Netzwerk auf die einzelnen Arten der Beziehungen geprüft, alle sechs berücksichtigten Jahre wurden miteinander verglichen und der besonders auffällige Akteur Von Wegen Lisbeth wurde gesondert analysiert. \
Auffällig geworden ist nicht nur die schier unüberschaubare Anzahl an Festival-Verbindungen, sondern auch das „Coronajahr" 2020, das sich in Anzahl der Verbindungen stark von den anderen untersuchten Jahren unterscheidet. Eine weitere Auffälligkeit stellt das 2020 erschienene Feature „Sanifair Millionär" dar, das ungewöhnlich viele Akteure miteinander in Verbindung bringt.

Keywords: Netzwerkanalyse, Indie-Bands, Kollaborationen, Festivals, Labels

# 1. Einleitung

Im folgenden Forschungsbericht werden wir Verbindung deutscher Indie-Bands in den Jahren von 2015 bis 2020 untersuchen. Dabei haben wir die in den letzten Jahren größten Festivals (Southside, Rock am Ring, Fusion, Juicy Beats), in denen auch die Musikrichtung Indie vertreten ist, genauer untersucht und anhand derer 35 Akteure ausgewählt. Bei der Festivalauswahl haben wir darauf geachtet, dass sie kostenpflichtig sind, um nicht im Nachhinein zu kleine Indie-Bands aussortieren zu müssen. Durch dieses Ausschlusskriterium ist beispielsweise das Festival „Bochum Total" nicht berücksichtigt worden.

Die ausgewählten 35 Akteure haben wir daraufhin untersucht, ob zwei Künstler:innen gemeinsam bei einem Festival aufgetreten sind (relation=1), ein gemeinsames Musiklabel haben (relation=2), gemeinsam auf Tour gegangen sind oder Auftritte zusammen gehabt haben (relation=3) und ob sie ein gemeinsames Feature produziert haben (relation=4). Anhand der erhobenen Daten wollen wir nun die Vernetzung der einzelnen Akteure genauer beleuchten. Dabei gehen wir auf die Fragen ein, ob es einen Zusammenhang zwischen gemeinsamen Features der Künstler:innen und den Auftritten auf Festivals gibt, ob das Musiklabel Einfluss auf Festivalauftritte hat, ob Künstler:innen mit mehr Spotify-Hörer:innen / Instagram-Follower:innen auch besser vernetzt sind und welche Ergebnisse die zeitliche Entwicklungen zeigen.

# 2. Vorarbeiten und vergleichbare Studien

## 2.1 Forschungsstand

In Deutschland gehört die Musikwirtschaft mit zu den größten Wirtschaftsbranchen. Die Bruttowertschöpfung der Musikwirtschaftsbranche ist höher als die der Filmwirtschaft, Hörfunkveranstalter, der Buchverlage, Zeitschriftenverlage oder Zeitungsverlage. Nur die Fernsehveranstalter verzeichnen eine höhere Wertschöpfung (vgl. Bundesverband der Konzert und Veranstaltungswirtschaft, 2020).

Im Jahr 2020 sah das allerdings anders aus, da wegen der Corona-Pandemie alle Festivals und die meisten Konzerte abgesagt wurden. Statt aber diesen nachzutrauern, ruft die Chemnitzer Band Blond eine „virtuelle Cypher" (vgl. Musik3000, 2020, Abs. 1) mit dem Song „Sanifair Millionär" ins Leben. Die Band interpretiert ihren eigenen Hit neu und lädt bekannte Feature-Gäste ein. Mit dabei sind vor allem Künstler:innen aus der deutschen Indie Szene wie Kummer, Drangsal und Von Wegen Lisbeth. Der Song wurde am 17.07.2020 veröffentlicht und bringt 17 Indie-Bands zusammen (vgl. Musik3000, 2020). Inspiriert durch diesen Feature-Song wollten wir uns die deutsche Indie-Szene und die Verknüpfung der Künstler:innen genauer anschauen.

Genres verschmelzen auch in Deutschland immer mehr. Verschiedene Künstler:innen produzieren Genre-übergreifende Features und so entstehen wiederum neue Genres wie „Indie-Pop" oder „Indie-Rock" (Winkler, 2020). Uns stellt sich die Frage: Gibt es auch innerhalb eines Genres, in unserem Fall des Indie-Genres, viele Kollaborationen?

Eine weitere Frage, die sich bei Kollaborationen aufdrängt: Wie kommt es überhaupt dazu, dass gewisse Künstler:innen gemeinsame Features aufnehmen? Showcase Festivals bieten beispielsweise für neue Bands und Musiker:innen die Möglichkeit, vor fachkundigem Publikum aufzutreten und so den Bekanntheitsgrad zu erhöhen. Diese Art von Festivals verbindet Musikfestival und Branchentreff. Durch die Anwesenheit von Veranstalter:innen, Plattenlabels, Journalist:innen und anderen Musikschaffenden ist es leicht, neue Kontakte zu knüpfen (vgl. Nagel, 2019). Somit können Festivals die Grundlage für spätere gemeinsame Songs oder das Begleiten der jeweiligen anderen Musiker:innen als Vorband sein.

Soziale Netzwerke wie Instagram schaffen eine exklusive Nähe -- auf der einen Seite zu den Follower:innen und auf der anderen Seite zu anderen Musikschaffenden. Sie sind wie eine weitere Bühne, auf denen sich Musiker:innen präsentieren, um ihre Bekanntheit zu steigern (vgl. Noka, 2019). Musiker:innen können durch die sozialen Netzwerke unabhängiger von Labels agieren, eine eigene Fangemeinde aufbauen, sich mit anderen Künstler:innen vernetzen und über digitale Medien gemeinsam Musik machen (vgl. Schöbel, 2016). Vor allem Instagram eignet sich, um mit Fans und anderen Musiker:innen in Kontakt zu treten, neue Musik anzukündigen, eigene Musik zu verkaufen, auf Festivals aufmerksam zu machen und insgesamt an Bekanntheit zu gewinnen (vgl. Seawood, 2016). Somit liegt auch die Vermutung nahe, dass Musiker:innen, die besonders aktiv in den sozialen Netzwerken sind, auch gute Vernetzungen zu anderen Musikschaffenden haben.

In Deutschland haben sich sogenannte Independent Labels (kurz: Indie-Labels) auf dem Musikmarkt etabliert. Der Verband unabhängiger Musikunternehmer:innen e. V. vertritt die Interessen unabhängiger Unternehmer:innen der deutschen Musikwirtschaft und zählt mittlerweile rund 1.200 selbstvermarktende Künstler:innen, Labels, Verlage, Vertriebe und Produzent:innen (vgl. VUT, 2021). Bereits 2017 konnte man in der Indie-Branche einen Wachstum verzeichnen. Im Vergleich: Zu Beginn des Jahres 2017 zählte der VUT 1.146 Mitglieder (vgl. Wischmeyer, 2018).

Viele Indie-Labels entstehen, da Bands ihre Selbstbestimmung behalten wollen und große Labels meist an Nischenpublikum kein Interesse haben. So nehmen viele Musiker:innen ihr Anliegen selbst in die Hand und gründen eigenen Labels (vgl. Goethe Institut, 2016). Bei unserer Netzwerkanalyse wollen wir auch untersuchen, ob es unter den Akteuren gleiche Labels gibt und somit eine Vernetzung besteht, oder ob innerhalb des Indie-Genres die einzelnen Musiker:innen dazu tendieren, ihre eigenen Labels zu haben.

Bei unserer Recherche ist uns kein ähnliches oder vergleichbares Netzwerk aufgefallen, mit dem wir unsere Forschung hätten vergleichen oder an das wir hätten anknüpfen können.

Im Zuge dieser Netzwerkanalyse werden wir die Verbindungen von Indie-Bands aus dem deutschsprachigen Raum in den Jahren 2015 bis 2020 untersuchen und auf verschiedene Forschungsfragen eingehen. All diesen wollen wir aber eine Forschungsfrage überordnen:

*Wie sind deutsche Indie-Bands miteinander vernetzt?*

## 2.2 Arbeitshypothesen

Wir gehen von folgenden Arbeitshypothesen aus:

a)  Auftritte: Akteure, die oft auf den gleichen Festivals aufgetreten sind, haben eher ein gemeinsames Feature und haben eher gemeinsame Auftritte oder sind die Vorband des jeweils anderen Akteurs.
b)  Vernetzung: Akteure, die viele Instagram-Follower:innen und Spotify-Hörer:innen haben, sind auch gut mit anderen Akteure vernetzt.
c)  Durch den zeitlichen Verlauf wollen wir die Entwicklung der Vernetzung des Gesamtnetzwerkes aufzeigen. Anhand dessen könnten auch einzelne Akteure herausstechen, die sich über die Jahre besser vernetzt haben.
d)  Die Band mit dem höchsten Degree-Wert ist auch mit allen anderne Bands bzw. Künstler:innen vernetzt.

Diese Arbeitshypothesen werden im Folgenden durch die Analyse des Netzwerks untersucht und entweder bestätigt oder widerlegt.

# 3. Datenerhebung: Zugang, Bereinigung und Codebuch

## 3.1 Datenzugang

Die Daten haben wir über verschiedene Websites erfasst, die die Festivalauftritte der Akteure in den Jahren von 2015 bis 2020 aufzeigen (Beispiel: <https://www.festivalhopper.de>). Außerdem haben wir die Website der jeweiligen Akteuren und deren Spotify- sowie Instagram-Auftritt untersucht. Das Ganze haben wir mit einer freien Recherche über Ticket-Websites, Wikipedia, Musikmagazine & Co. ergänzt. Eine vollständige Liste aller Websites, die bei der Recherche genutzt wurden, finden sich unter Kapitel 6.2 in diesem Dokument. Welche Quelle für welche Verbindung zurate gezogen wurde, ist zudem in der Edge-List hinterlegt, die in diesem Dokument verlinkt ist.

## 3.2 Bereinigung des Datensatzes

Der Datensatz wurde nicht anonymisiert, da die Informationen ohnehin schon öffentlich zugänglich sind.

## 3.3 Codebuch

Das [Codebuch](https://github.com/lz029/226305-SNA-WS-21-22/blob/main/Indie/INDIE-Codebuch.md) beschreibt die Variablen, Relationen und Gewichte des Netzwerks und ist ebenfalls auf Github hinterlegt.

# 4. Analyse und Interpretation

Im Folgenden wird zuerst das Gesamtnetzwerk und somit alle Verbindungen der 35 Indie-Bands betrachtet. Danach folgt eine Selektion in einzelne Teilnetzwerke, um unsere Arbeitshypothesen zu untersuchen.

## 4.1 Das Gesamtnetzwerk

Das Gesamtnetzwerk umfasst 35 Knoten und 1.078 Beziehungen. Es handelt sich um ein ungerichtetes und gewichtetes One-Mode-Netzwerk. Dieses werden wir zu Beginn in RStudio einlesen, um eine einfache Visualisierung darzustellen und einen ersten Überblick zu erhalten.

```{r Gesamnetzwerk erstellen, echo=FALSE, message=FALSE, warning=FALSE, paged.print=TRUE}

library(igraph)

# Einlesen der Edge- und Nodelist
el <- read.csv("https://raw.githubusercontent.com/lz029/226305-SNA-WS-21-22/main/Indie/INDIE-Edgelist.csv", header=T, as.is=T, sep = ",")
nodes <- read.csv("https://raw.githubusercontent.com/lz029/226305-SNA-WS-21-22/main/Indie/INDIE-Nodelist.csv", header=T, as.is=T, sep = ",")

# Matrix erstellen
edgematrix <-as.matrix(el)

# Zusammenführen von Edge- und Nodelist als igraph-Objekt
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

Das Hauptnetzwerk besteht aus einem Komponenten mit 35 Knoten, die alle miteinander verbunden sind. Die Dichte im Netzwerk beträgt 181,18 Prozent von allen möglichen Verbindungen. Somit ist das Indie-Netzwerk der 35 Akteure stark miteinander vernetzt. Die maximale Pfaddistanz beträgt 2 Schritte zwischen den zwei Akteuren „Amilli" und „Bilderbuch".

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

In dieser Darstellung lassen sich keine genauen Zusammenhänge erklären, weshalb wir das Netzwerk weiter unterteilen müssen. Was sich allerdings klar zeigt: Es gibt keine:n Musiker:in, der:die keine Verbindung zu einem:r anderen Musiker:in hat.

Das gesamte Netzwerk wird jetzt so visualisiert, dass man die Verbindungen durch Label, Feature und gemeinsame Auftritte stärker und individuell erkennen kann. Dafür werden alle Beziehungsstärken 1, also die gemeinsamen Auftritte bei Festivals, transparent geschalten.

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

Bei dieser Visualiserung kann man erkennen, dass es einige Verbindungen der Beziehungsstärke 2 gibt. Es gibt also mehrere Künstler:innen, die den gleichen Musiklabels angehören. Allerdings ist bei dieser Darstellung des Gesamtnetzwerkes nicht die zeitliche Komponente berücksichtigt und so lässt sich nur die Aussage treffen, dass einige Künstler:innen bei den gleichen Musiklabels innerhalb der letzten fünf Jahre waren. Die Verbindungen der Beziehungsstärken 3 und 4 scheinen ungefähr gleich oft aufzutreten.

Nun sollen nur die Verbindungen mit Beziehungsstärke 1 angezeigt werden. Also alle Verbindungen, bei denen die Akteure auf dem gleichen Festival gespielt haben. Dafür werden alle anderen Beziehungsstärken transparent gesetzt.

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

Durch die hohe Anzahl an Kanten lässt sich hier nichts genauer erkennen. Die Musiker:innen haben also auf vielen Festivals gemeinsam gespielt.

Nun sollen nur die Verbindungen mit Beziehungsstärke 2 angezeigt werden. Also alle Verbindungen über die Jahre, in denen die Akteure das gleiche Musiklabel hatten. Dafür werden alle anderen Beziehungsstärken transparent gesetzt.

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

In dieser Visualisierung wird nochmal sichtbar, welche Musiker:innen innerhalb der letzten fünf Jahre bei den gleichen Musiklabels waren. Wie oben bereits erwähnt, wird hier nicht die zeitliche Komponente berücksichtigt und somit kann man nicht sagen, ob die Musiker:innen auch zur gleichen Zeit bei demselben Musiklabel angestellt waren. Wie unsere Recherche bestätigt hat, ist es im Bereich Indie nicht selten, dass Musiker:innen kleinen Labels angehören oder sogar eigene Labels gründen und somit nicht viele Gemeinsamkeiten entstehen.

Nun sollen nur die Verbindungen mit Beziehungsstärke 3 angezeigt werden. Also alle Verbindungen, bei denen die Akteure gemeinsam auf Tour waren und/oder sich bei Auftritten gegenseitig als Vorband supported haben. Dafür werden alle anderen Beziehungsstärken transparent gesetzt.

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

Nun sollen nur die Verbindungen mit Beziehungsstärke 4 angezeigt werden. Also alle Verbindungen bei denen die Akteure gemeinsam ein Feature haben. Dafür werden alle anderen Beziehungsstärken transparent gesetzt.

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

Hier wird deutlich, dass es bei den 35 Akteuren innerhalb der letzten fünf Jahre nicht viele gemeinsame Feature-Songs gab. In der Mitte ist eine starke Vernetzung mehrerer Bands zu sehen. Das liegt unter anderem an dem Feature-Song „Sanifair Millionär", bei dem die Band Blond 2020 insgesamt 17 Indie-Bands zusammengebracht hat. Davon haben wir fünf Bands in unsere Netzwerkanalyse miteinbezogen. Abgesehen von diesem großen Feature-Song hat die Band AnneMayKantereit mit vier Kanten vergleichsweise viele Features.

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

Die Analyse zeigt: das Netzwerk besteht aus 4 miteinander verbundenen Clustern, die aus 35 Knoten bestehen. In unserem Gesamtnetzwerk sind die Cluster sehr eng miteinander verwoben und es hebt sich keine bestimmte Gruppierung davon ab. Somit lohnt es sich nicht, eine der Cluster-Gruppen genauer zu analysieren.

## 4.2 Teilnetzwerke

Im Folgenden werden die Verbindungen aller Bands nach Jahren aufgeteilt. Dadurch sollen Unterschiede besser zur Geltung kommen. In welchem Jahr waren die meisten Bands aktiv? Wie wirkt sich das Corona-Jahr 2020 auf unsere Musiker:innen aus? Um Unterschiede direkt sichtbarer zu machen, wird hier der Befehl "layout_with_kk", mit dem die Netzwerke normalerweise geplottet werden, durch den Befehl "layout_in_circle" ersetzt. So bleiben alle Bands an gleicher Stelle und die sieben Teilnetzwerke können besser miteinander verglichen werden.

```{r Teilnetzwerke nach Jahren,fig.height=10, fig.width=14, message=FALSE, warning=FALSE, paged.print=FALSE}

list.edge.attributes(indie)
edge.attributes(indie)$time

# Knoten und Kanten speziell einfärben
E(indie)[ (E(indie)$relation == 1) ]$color <- "gray85"
E(indie)[ (E(indie)$relation == 2) ]$color <- "cyan4"
E(indie)[ (E(indie)$relation == 3) ]$color <- "coral3"
E(indie)[ (E(indie)$relation == 4) ]$color <- "darkgoldenrod1"

#Gesamtnetzwerk
plot(indie, layout=layout_in_circle, main="Gesamt",
     vertex.frame.color="transparent", 
     vertex.label.family = "Arial",
     vertex.label.color = "black",
     vertex.color="lightblue",
      layout = layout_components,
     asp=0,
     vertex.size=10)

# Teilnetzwerk 2015 erstellen
y2015 <- subgraph.edges(indie, E(indie)[time=="2015"])
# Teilnetzwerk 2015 visualisieren
plot(y2015, layout=layout_in_circle, main="2015",
     vertex.frame.color="transparent", 
     vertex.label.family = "Arial",
     vertex.label.color = "black",
     vertex.color="lightblue",
      layout = layout_components,
     asp=0,
     vertex.size=10)

# Teilnetzwerk 2016 erstellen
y2016 <- subgraph.edges(indie, E(indie)[time=="2016"])
# Teilnetzwerk 2016 visualisieren
plot(y2016, layout=layout_in_circle, main="2016",
     vertex.frame.color="transparent", 
     vertex.label.family = "Arial",
     vertex.label.color = "black",
     vertex.color="lightblue",
      layout = layout_components,
     asp=0,
     vertex.size=10)

# Teilnetzwerk 2017 erstellen
y2017 <- subgraph.edges(indie, E(indie)[time=="2017"])
# Teilnetzwerk 2017 visualisieren
plot(y2017, layout=layout_in_circle, main="2017",
     vertex.frame.color="transparent", 
     vertex.label.family = "Arial",
     vertex.label.color = "black",
     vertex.color="lightblue",
      layout = layout_components,
     asp=0,
     vertex.size=10)

# Teilnetzwerk 2018 erstellen
y2018 <- subgraph.edges(indie, E(indie)[time=="2018"])
# Teilnetzwerk 2018 visualisieren
plot(y2018, layout=layout_in_circle, main="2018",
     vertex.frame.color="transparent", 
     vertex.label.family = "Arial",
     vertex.label.color = "black",
     vertex.color="lightblue",
      layout = layout_components,
     asp=0,
     vertex.size=10)

# Teilnetzwerk 2019 erstellen
y2019 <- subgraph.edges(indie, E(indie)[time=="2019"])
# Teilnetzwerk 2019 visualisieren
plot(y2019, layout=layout_in_circle, main="2019" ,
     vertex.frame.color="transparent", 
     vertex.label.family = "Arial",
     vertex.label.color = "black",
     vertex.color="lightblue",
      layout = layout_components,
     asp=0,
     vertex.size=10)

# Teilnetzwerk 2020 erstellen
y2020 <- subgraph.edges(indie, E(indie)[time=="2020"])
# Teilnetzwerk 2020 visualisieren
plot(y2020, layout=layout_in_circle, main="2020",
     vertex.frame.color="transparent", 
     vertex.label.family = "Arial",
     vertex.label.color = "black",
     vertex.color="lightblue",
      layout = layout_components,
     asp=0,
     vertex.size=10)

# Alle sieben Netzwerke nebeneinander visualisieren
par(mfrow=c(4,4), mar=c(1,1,1,1))
```

Deutlich zu erkennen ist, dass das Zerlegen der Verbindungen in Teilnetzwerke nach Jahren eine deutliche Entzerrung mit sich gebracht hat. Sofort ins Auge springt wohl das Teilnetzwerk des Jahres 2020, das durch im Vergleich deutlich weniger Kanten auffällt. Grund hierfür sind die fehlenden Festivals, die aufgrund der Covid-19-Pandemie in diesem Jahr ausblieben. Gleichzeitig sind die sonst nur sporadisch verteilten gelben Kanten, die die Verbindung zweier Knoten durch ein gemeinsames Feature (relation=4) kennzeichnet, ein Merkmal des Teilnetzwerkes 2020. Diese sind größtenteils dem „Mammut-Feature" „Sanifair Millionär" zuzuschreiben, das fünf der untersuchten Bands miteinander verbindet.

Eine weiter Auffälligkeit bringt das Teilnetzwerk des Jahres 2015 mit sich, denn auch hier gehen von einigen Bands im Vergleich zu den anderen Jahren (mit Ausnahme von 2020) deutlich weniger Kanten aus. Die Ursache hierfür findet sich vermutlich in der Tatsache, dass viele der in unserer Netzwerkanalyse untersuchten Bands im Jahr 2015 noch nicht aktiv waren oder erst im Laufe der untersuchten Jahre „groß" genug wurden, um auf vielen Festivals Auftritte zu ergattern.

Nun sollen Degree-Wert und Dichte aller Teilnetzwerke miteinander und mit denen des Gesamtnetzwerkes verglichen werden.

```{r Netzwerkmaße der Teilnetzwerke nach Jahren,fig.height=10, fig.width=14, message=FALSE, warning=FALSE, paged.print=FALSE}

# Degree-Werte der Teilnetzwerke
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

# Dichte der Teilnetzwerke
edge_density(indie, loops=FALSE)
edge_density(y2015, loops=FALSE)
edge_density(y2016, loops=FALSE)
edge_density(y2017, loops=FALSE)
edge_density(y2018, loops=FALSE)
edge_density(y2019, loops=FALSE)
edge_density(y2020, loops=FALSE)
```

Betrachtet man die Dichten der sechs Teilnetzwerke, liegt die höchste bei 2017 mit 66,13 Prozent, dicht gefolgt von 2018 mit 64,53 Prozent. Wenig verwunderlich ist das Jahr 2020, das sich wie im vorherigen Abschnitt bereits beschrieben vor allem durch die fehlenden Festival-Verbindungen auszeichnet. Insofern ist die bei lediglich 18,97 Prozent liegende Dichte in diesem Jahr keine Überraschung.

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

Um die Verteilung nach Relations besser veranschaulichen zu können, werden unsere Künstler:innen nun nach den unterschiedlichen Verbindungen (1-4) sortiert und anschließend auf ihre Netzwerkmaße überprüft.

```{r Teilnetzwerke nach Relations}

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
      main="Teilnetzwerk Relation 1",
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
      main="Teilnetzwerk Relation 4",
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

Bei der Betrachtung der Teilnetzwerke nach Relations bestätigt sich, was sich bereits bei der Visualisierung des Gesamtnetzwerkes angedeutet hat. Je stärker die Verbindung, also enger die Zusammenarbeit zwischen den Künstler:innen, desto kleiner werden die Teilnetzwerke. Daraus ergibt sich auch die abfallende Netzwerkdichte mit aufsteigender Verbindungsstärke. Während auf den Festivals noch sehr viele Bands aufeinandertreffen, haben nur wenige ein Feature oder eine gemeinsame Tour. Ein gemeinsamer Festivalauftritt ist auch nicht mit einer bewusst gewählten Vernetzung gleichzusetzen; hier kann allenfalls davon ausgegangen werden, dass die Künstler:innen sich gegenseitig kennen. Bei einem Feature oder der Wahl einer Vorband ist eine bewusst gewählte Vernetzung anzunehmen. Auch bilden sich Gruppen, die keine Verbindungen zueinander aufweisen, oder Gruppen, in denen die Künstler:innen untereinander gut vernetzt sind. Das lässt sich in dem Sinne interpretieren, dass nach einer engen Zusammenarbeit weitere Verbindungen zu dem/der Künstler:in nahestehenden Dritten entsteht. Zu beachten gilt es dabei aber, dass bei einem gemeinsamen Feature mehr als zwei Künstler:innen beteiligt sein können. Bei den Beziehungen 2-4 lassen sich ebenfalls einzelne Gruppierungen erkennen.

## 4.3 Analyse eines herausgehobenen Akteurs in Egonetzwerken

Da unser Netzwerk sehr viele Akteure und sehr viele Verbindungen zeigt, wollen wir uns im Folgenden auf einen Akteur fixieren. Hierfür wählen wir die Band mit der stärksten Vernetzung, also dem höchsten Degree-Wert, um anschließend nach Jahren geordnete Egonetzwerke zu erstellen, die die Kollaborationen deutlicher und übersichtlicher darstellen sollen.

```{r Analyse eines herausgehobenen Akteurs in Egonetzwerken}
# Im Folgenden sollen die Kollaborationen einer Band explizit analysiert werden. Hierfür wählen wir die Band mit dem höchsten Degree-Wert.

# Degree-Werte bestimmen
i_deg <- degree(indie)
i_deg

# höchster Degree-Wert auslesen
which.max(degree(indie))

# Von wegen Lisbeth ist die Band mit dem höchsten Degree-Wert, wie man auch schon oben auslesen konnte.

# Um die Kollaborationen von Von wegen Lisbeth übersichtlicher zu zeigen, teilen wir sie nach Jahren ein und erstellen Egonetzwerke, die die Entwicklung der Von wegen Lisbeth-Zusammenarbeiten über die Jahre hinweg anzeigen.

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

Wie sich herausgestellt hat, ist die Band Von Wegen Lisbeth am stärksten mit den anderen untersuchten Indie-Bands vernetzt. Über die sechsjährige Zeitspanne hat sie einen Degree-Wert von 154 erreicht. Dies geht besonders auf viele Festivalauftritte, aber auch sonstige Kollaborationen mit fast allen Bands aus dem Netzwerk zurück. Schaut man sich nun zusätzlich die Zusammenarbeiten verteilt über die einzelnen Jahre an, kann mann man feststellen, dass sich die 2006 gegründete Band in den Jahren 2015-2018 immer stärker vernetzt hat. Und in der Tat hat die Erfolgsgeschichte von Von Wegen Lisbeth mit der engen Zusammenarbeit mit AnnenMayKantereit ab 2014 begonnen. Diese Zusammenarbeit lässt sich somit auch hier als eine der einzigen im Jahr 2015 erkennen. In diesem Jahr war Von Wegen Lisbeth bei 18 Konzerten einer AnnenMayKantereit-Tour Vorband (vgl. Von Wegen Lisbeth, 2021). AnnenMayKantereit bleiben auch in den nächsten Jahren ein steter Begleiter von Von Wegen Lisbeth. Diese beginnen sich dennoch auch mit anderen Bands stark zu vernetzen. So sind 2016 schon viel mehr Kollaborationen erkennbar, die insbesondere von gemeinsamen Festivalauftritten herrühren. Besonders auffällig eng vernetzt sind Von Wegen Lisbeth 2016 mit Giant Rooks. 2017 sind diese ebenfalls am engsten an Von Wegen Lisbeth, gemeinsam mit Milliarden, Kraftklub und Fil Bo Riva. 2018 wird selbst dieses aufgedröselte Teilnetzwerk wieder sehr unübersichtlich, da Von Wegen Lisbeth äußerst aktiv ist. Neben den genannten Akteuren werden nun auch Leoniden und Bosse häufig auf den selben Bühnen gesehen. 2019 nehmen die Kollaborationen dann wieder ab. Insbesondere sind Von Wegen Lisbeth jetzt mit ihrer neuen Platte unterwegs und kollaborieren in dieser Zeit fast nur mit Vorbands (vgl. Von Wegen Lisbeth, 2021). Aus unserer Untersuchung sind das insbesondere Milliarden und Blond. Blond prägt auch unsere Untersuchung für das Jahr 2020 am stärksten. Dort erscheint das von Blond initiierte Feature „Sanifair Millionär", bei dem unter anderem Von Wegen Lisbeth, Drangsal, Rikas, Leoniden und Fibel mitwirken. Ansonsten hat Von Wegen Lisbeth 2020 aufgrund der Pandemie kaum Kollaborationen vorzuweisen. Es scheint, dass eine Band wie Von Wegen Lisbeth in den ersten Jahren des Erfolgs (2015-2018) viele Verbindungen zu ähnlichen Bands aufbaut, viel spielt und viel unterwegs ist. Mit dem größeren Erfolg, den die Band 2019 erreicht, kann sie sich leisten, eigene Vorbands dazuzuholen, weniger Festivals zu spielen und musikalische Projekte mit anderen Bands einzugehen. Die bloße Masse an Kollaborationen nimmt hierdurch aber ab.

## 4.4 Zusammenhang zwischen Degree-Wert und Spotify/Instagram

Im folgenden werden die einzelnen Künstler:innen und Bands hinsichtlich Degree-Wert, Spotify-Hörer:innen und Instagram-Follower:innen miteinander verglichen. Zudem wird überprüft, ob ein Zusammenhang zwischen den einzelnen Kategorien besteht.

```{r Zusammenhang höchster Degree-Wert mit Spotify-Hörer:innen bzw. Instagram Follower:innen}

# Degree-Wert Gesamtnetzwerk berechnen

dindie <- degree(indie)
dindie
plot(dindie)
```

+-------+-----------------------+-----------------------+--------------------------+
| Platz | Degree                | Spotify-Hörer:innen   | Instagram-Follower:innen |
+=======+=======================+=======================+==========================+
| 1     | Von wegen Lisbeth     | Milky Chance          | AnnenMayKantereit        |
+-------+-----------------------+-----------------------+--------------------------+
| 2     | AnnenMayKantereit     | AnnenMayKantereit     | Olli Schulz              |
+-------+-----------------------+-----------------------+--------------------------+
| 3     | Leoniden              | Giant Rooks           | Milky Chance             |
+-------+-----------------------+-----------------------+--------------------------+
| 4     | Razz                  | Bosse                 | Kraftklub                |
+-------+-----------------------+-----------------------+--------------------------+
| 5     | Wanda                 | Kraftklub             | Bosse                    |
+-------+-----------------------+-----------------------+--------------------------+
| 6     | Faber                 | Ätna                  | Faber                    |
+-------+-----------------------+-----------------------+--------------------------+
| 7     | Fil Bo Riva           | Provinz               | Giant Rooks              |
+-------+-----------------------+-----------------------+--------------------------+
| 8     | Giant Rooks           | Avec                  | Bilderbuch               |
+-------+-----------------------+-----------------------+--------------------------+
| 9     | Drangsal              | Fil Bo Riva           | Von wegen Lisbeth        |
+-------+-----------------------+-----------------------+--------------------------+
| 10    | Kraftklub             | Von wegen Lisbeth     | Provinz                  |
+-------+-----------------------+-----------------------+--------------------------+
| 11    | Schmutzki             | Bilderbuch            | Leoniden                 |
+-------+-----------------------+-----------------------+--------------------------+
| 12    | Bilderbuch            | Faber                 | Wanda                    |
+-------+-----------------------+-----------------------+--------------------------+
| 13    | Milliarden            | Wanda                 | Blond                    |
+-------+-----------------------+-----------------------+--------------------------+
| 14    | Bosse                 | Leoniden              | Black Sea Dahu           |
+-------+-----------------------+-----------------------+--------------------------+
| 15    | Milky Chance          | Olli Schulz           | Drangsal                 |
+-------+-----------------------+-----------------------+--------------------------+
| 16    | Frittenbude           | Bonaparte             | Mine                     |
+-------+-----------------------+-----------------------+--------------------------+
| 17    | Rikas                 | Mine                  | Fil Bo Riva              |
+-------+-----------------------+-----------------------+--------------------------+
| 18    | Olli Schulz           | Bruckner              | Amilli                   |
+-------+-----------------------+-----------------------+--------------------------+
| 19    | Tonbandgerät          | Black Sea Dahu        | Bruckner                 |
+-------+-----------------------+-----------------------+--------------------------+
| 20    | Schnipo Schranke      | Razz                  | Bonaparte                |
+-------+-----------------------+-----------------------+--------------------------+
| 21    | Blond                 | Amilli                | Razz                     |
+-------+-----------------------+-----------------------+--------------------------+
| 22    | Die Höchste Eisenbahn | Milliarden            | Tonbandgerät             |
+-------+-----------------------+-----------------------+--------------------------+
| 23    | Mine                  | Frittenbude           | Milliarden               |
+-------+-----------------------+-----------------------+--------------------------+
| 24    | Bonaparte             | Stereo Total          | Frittenbude              |
+-------+-----------------------+-----------------------+--------------------------+
| 255   | Kettcar               | Rikas                 | Kettcar                  |
+-------+-----------------------+-----------------------+--------------------------+
| 26    | Amilli                | Kettcar               | Rikas                    |
+-------+-----------------------+-----------------------+--------------------------+
| 27    | Lisa Morgenstern      | Lisa Morgenstern      | Die Höchste Eisenbahn    |
+-------+-----------------------+-----------------------+--------------------------+
| 28    | Fibel                 | Die Höchste Eisenbahn | Ätna                     |
+-------+-----------------------+-----------------------+--------------------------+
| 29    | Provinz               | Lion Sphere           | Schmutzki                |
+-------+-----------------------+-----------------------+--------------------------+
| 30    | Lion Sphere           | Tonbandgerät          | Schnipo Schranke         |
+-------+-----------------------+-----------------------+--------------------------+
| 31    | Ätna                  | Schnipo Schranke      | AVEC                     |
+-------+-----------------------+-----------------------+--------------------------+
| 32    | Bruckner              | Schmutzki             | Stereo Total             |
+-------+-----------------------+-----------------------+--------------------------+
| 33    | Black Sea Dahu        | Drangsal              | Lionsphere               |
+-------+-----------------------+-----------------------+--------------------------+
| 34    | Avec                  | Blond                 | Fibel                    |
+-------+-----------------------+-----------------------+--------------------------+
| 35    | Stereo Total          | Fibel                 | Lisa Morgenstern         |
+-------+-----------------------+-----------------------+--------------------------+

Den höchsten Degree-Wert hat wie bereits festgestellt die Band Von Wegen Lisbeth mit einem Wert von 154, gefolgt von AnnenMayKantereit mit 117 und Leoniden mit 107. Vergleicht man alle Bands und Künstler:innen anhand ihres Degree-Werts, den Spotify-Hörer:innen sowie Instagram-Follower:innen, ergeben sich unter anderem folgende Auffälligkeiten:

-   AnnenMayKantereit befindet sich bei allen drei Kategorien auf Platz 1 oder 2
-   viele Bands spielen sich komplett im unteren Drittel der Tabelle ab, was einen Zusammenhang bedeuten kann
-   vielen Bands befinden sich ausschließlich im oberen Drittel
-   Faktoren wie internationale Bekanntheit führen dazu, dass manche Bands einen eher niedrigen Degree-Wert im Vergleich zu ihren Follower:innen und Hörer:innen haben (Beispiel hierfür ist die Band Milky Chance, die mit ihrem Song „Stolen Dance" 2013 internationale Bekanntheit erlangte)
-   andere Bekanntheitsfaktoren neben der Musik führen dazu, dass die Anzahl an Follower:innen viel höher ist als der Rest (Beispiel hierfür ist Olli Schulz, der neben seiner Musiker-Karriere in erster Linie für den Podcast „Fest und Flauschig" bekannt ist, welchen er mit dem bekannten Satiriker Jan Böhmermann moderiert)
-   Bands wie Provinz, die erst in Coronazeiten wirklich bekannt wurden, haben einen vergleichsweise niedrigen Degree-Wert trotz hoher Anzahl an Spotify-Hörer:innen und Instagram-Follower:innen
-   es gibt scheinbare „Festivalbands", die weder besonders hohe Follower:innen- noch Hörer:innenzahlen haben und dennoch einen vergleichsweise hohen Degree-Wert besitzen

# 5. Diskussion, Fazit und Ausblick

## Fazit

Die hier vorgenommene Netzwerkanalyse erschließt sich nur, wenn Teilaspekte betrachtet werden. Der Blick auf das große Ganze eröffnet bei 1.078 Verbindungen zwischen Indie-Künstler:innen kaum Erkenntnisse. Dies liegt auch an der sehr engen Vernetzung und einer Dichte von rund 181 Prozent. Deutlich ersichtlich wird bei der Vernetzung aber die große Bedeutung von Festivals in der Indie-Szene. Hier begegneten sich Indie-Künstler:innen am häufigsten. Labels teilen sie sich hingegen eher wenige, da auch viele kleine Labels in der Szene zu finden sind. Auch Features und gemeinsame Songs spielen in der Szene eine untergeordnete Rolle, wie sich aus unserer Forschung ergibt. Insbesondere deshalb ist das Feature „Sanifair Millionär" mit ganzen 17 Künstler:innen hervorzuheben. Unsere Forschung lässt eine mit den Jahren zunehmende Vernetzung erkennen, die 2017 ihren Höhepunkt findet und 2020 durch die Corona-Pandemie drastisch nach unten gedrückt wird.

Die zunehmende und zum Jahr 2020 wieder abnehmende Vernetzung zeigte sich besonders übersichtlich am Beispiel der Band Von Wegen Lisbeth. Sie hatte sich besonders im von uns beschriebenen Zeitraum entwickelt und damit die stärkste Vernetzung aufgebaut. Es gibt in der Indie-Szene offensichtlich sehr zentrale, populäre Akteure wie Von Wegen Lisbeth und AnnenMayKantereit, die die Bands und Künstler:innen der Szene entscheidend miteinander vernetzen. AnnenMayKantereit ist nämlich auch in den Kennzahlen auf Spotify und Instagram eine führende Band und könnte damit als ein führender Akteur der Indie-Szene bezeichnet werden.

Im Folgenden werden unsere anfangs aufgestellten Thesen überprüft:

a)  Auftritte: Akteure, die oft auf den gleichen Festivals aufgetreten sind, haben eher ein gemeinsames Feature und haben eher gemeinsame Auftritte oder sind die Vorband des jeweils anderen Akteurs.

Die erste Hypothese lässt sich weder bewahrheiten noch verneinen. Durch unsere riesige Menge an Daten haben wir uns entschieden, bei einem One-Mode-Netzwerk zu bleiben und die Festivals nicht als Knoten einzuführen. Daher sind zwar Festivalverbindungen an sich erkennbar, diese lassen sich jedoch nicht auf einzelne Festivals zurückführen, weshalb nicht überprüfbar ist, ob Bands, die auf demselben Festival waren, auch eher gemeinsame Aufritte haben.

b)  Vernetzung: Akteure, die viele Instagram-Follower:innen und Spotify-Hörer:innen haben, sind auch gut mit anderen Akteuren vernetzt.

Unsere zweite Hypothese über den Zusammenhang zwischen Degree-Wert und Instagram-Follower:innen bzw. Spotify-Hörer:innen lässt sich bestätigen. Mit einigen Ausnahmen kann man sagen, dass die Künstler:innen, die sich im oberen bzw. unteren Drittel der Degree-Werte aufhalten, sich auch gleichermaßen bei den Spotify- und Instagram-Zahlen im jeweiligen Drittel einordnen.

c)  Durch den zeitliche Verlauf wollen wir die Entwicklung der Vernetzung des Gesamtneztwerkes aufzeigen. Anhand dessen könnten auch einzelne Akteure herausstechen, die sich über die Jahre besser vernetzt haben.

Durch das Aufteilen des Gesamtnetzwerkes nach Jahren lassen sich wie erwartet spannende Entwicklungen beobachten, besonders wenn man die Künstler:innen im einzelnen betrachtet. Die Band Kraftklub zum Beispiel hatte 2017-2018 ein Hoch und spielte auf beachtlich vielen Festivals, zog sich die Jahre danach dann aber komplett zurück.

d)  Die Band mit dem höchsten Degree-Wert ist auch mit allen anderne Bands bzw. Künstler:innen vernetzt.

Die letzte Hypothese hat sich als richtig herausgestellt. Von Wegen Lisbeth ist die Band mit dem höchsten Degree-Wert und gleichzeitig mit allen anderen vernetzt.

## Limitationen

Unsere Forschung muss aus unterschiedlichen Gründen mit deutlichen Einschränkungen analysiert werden. Zur Erfassung von Zusammenarbeiten in Form von Festivals, Labels, gemeinsamen Auftritten und Features stand uns nur eine lückenhafte Datenbasis zur Verfügung. Unsere Quellen waren die Webseiten der Bands, Künstler:innen, Festivals und Labels, lokale Berichterstattung, Musikmagazine und Übersichtsseiten für Festival-Line-Ups. Eine professionelle und sichere Plattform, die alle benötigten Informationen bereitstellt, gab es nicht. Es ist also nicht auszuschließen, dass Akteure und Verbindungen in unserem Netzwerk fehlen. Außerdem haben wir nur Bands und Künstler:innen untersucht, die in den vergangenen fünf Jahren auf den größten deutschen Festivals vertreten waren. Theoretisch wäre aber denkbar, dass es Bands oder Künstler:innen gibt, die gut in der Indie-Szene vernetzt sind, aber gar nicht auf großen Festivals auftreten. Auch diese würden in unserer Netzwerkforschung nicht erfasst. Zudem sind unsere Erkenntnisse dadurch beschränkt, dass nur die vergangenen fünf Jahre untersucht wurden. Indie-Bands oder Künstler:innen, die für die Szene von großer Bedeutung sein könnten, aber nur davor auf Festivals auftraten, wurden nicht erfasst. Darüber hinaus ist die Abgrenzung der Indie-Szene unklar. Zwar haben wir hierzu Einschätzungen aus Musikmagazinen herangezogen und so Bands und Künstler:innen der Szene zugeordnet, mangels klarer Definition gibt es aber auch hier Spielraum für andere Auslegungen. Zuletzt stellt das Ausnahmejahr 2020 eine Einschränkung dieser Netzwerkforschung dar. Erkenntnisse aus unserem Netzwerk lassen sich kaum auf andere Sechs-Jahres-Zyklen übertragen. 2020 fanden kaum Veranstaltungen statt - auch Kollaborationen wurden hierdurch stark eingeschränkt und unser Netzwerk beschreibt im letzten Jahr eine Ausnahmesituation, die so mit den Vorjahren nicht vergleichbar ist.

## Ausblick

Bei der Vorrecherche ist aufgefallen, dass Netzwerke in der Musikszene kaum erforscht werden. Um die Fragen: Wie werden Bands erfolgreich? Welche Synergien können Bands nutzen? Wie hat sich die Struktur von Musikszenen entwickelt? zu klären, wäre die Netzwerkforschung aber durchaus ein probates Mittel. Die Forschung über Zusammenarbeiten in der Musik könnte auf andere Genres und Zeiträume übertragen werden. Hier bieten sich auch Vergleiche zur Indie-Szene an. Auch im kleineren, weniger kommerziellen Rahmen wäre eine tiefere Forschung möglich, um festzustellen wo Künstler:innen auftreten müssen und mit wem sie zusammenarbeiten müssen um erfolgreich zu sein.

# 6. Literatur und Quellen

## 6.1 Literatur

Bundesverband der Konzert und Veranstaltungswirtschaft. (2020). Musikwirtschaft in Deutschland 2020. Abgerufen von <https://bdkv.de/marktstudien/>

Goethe Institut. (2016). Indie-Musiklabels in Deutschland - Alternative zum Mainstream. Abgerufen von <https://www.goethe.de/de/kul/mus/20805417.html>

Musik3000. (2020). Blond feiern „Sanifair Millionär Cypher" mit vielen bekannten Features. Abgerufen von <http://musik3000.de/blond-feiern-sanifair-millionaer-cypher-mit-vielen-bekannten-features/>

Nagel, D. (2019). Die fünf wichtigsten Showcase Festivals---Tipps für Musiker und Bands---Backstage PRO. Abgerufen von <http://www.backstagepro.de/thema/die-fuenf-wichtigsten-showcase-festivals-2019-03-28-1FXjg47yQr>

Noka, J. (9. Juli 2019). Das Geschäft mit Social Media: Die Musikbranche passt sich an!. Media Bubble. Abgerufen von <https://media-bubble.de/das-geschaeft-mit-social-media-die-musikbranche-passt-sich-an/>

Schöbel, N. (23. August 2016) Social Media für Musiker: 23 Fragen zum Erfolg \| MUSIK MARKETING. MUSIK-MARKETING.NET. Abgerufen von <https://musik-marketing.net/schildhauer-social-media-musiker/>

Seawood, L. W. (2016). What Instagram Discovered in Our First Nielsen Music Study. Medium. Abgerufen von: <https://medium.com/cuepoint/what-instagram-discovered-in-our-first-nielsen-music-study-de1a2740c005>

Von Wegen Lisbeth (2021). Konzerte. Abgerufen von <https://www.vonwegenlisbeth.de/konzerte/>

VUT (2021). Über den VUT: VUT - Verband unabhängiger Musikunternehmer\*innen e. V. Abgerufen von <https://www.vut.de/vut/ueber-den-vut/>

Winkler, S. (2. März 2020). Wie Genres immer diffuser werden -- außer im deutschen Pop. DIE WELT. Abgerufen von <https://www.welt.de/kmpkt/article206099115/Wie-Genres-immer-diffuser-werden-ausser-im-deutschen-Pop.html>

Wischmeyer, N. (2018). Inside Indie -- nicht das Ende vom Lied. brand eins online. Abgerufen von <https://www.brandeins.de/magazine/brand-eins-wirtschaftsmagazin/2018/personal/independent-label-inside-indie-nicht-das-ende-vom-lied>

## 6.2 Vollständige Liste unserer Quellen bei der Datenerhebung

<http://bis-2018.kulturzelt-kassel.de/archives/4916.html>

<http://bochum-total.de/>

<http://haldernpop.com/>

<http://happiness-festival.de/>

<http://hdiyl.de/konzertbericht-nuernberg-pop-2016/>

<http://magazin.shout-loud.de/livereview-open-ohr-festival-2-06-5-06-17/>

<http://modular-festival.de/>

<http://musik3000.de/blond-feiern-sanifair-millionaer-cypher-mit-vielen-bekannten-features/>

<http://triggerfish.de/hurricane-festival-2018/>

<http://www.appletreegarden.de/>

<http://www.blankit.de/>

<http://www.chiemsee-summer.de/>

<http://www.das-sommerfestival.de/>

<http://www.dasfest.net/>

<http://www.deichbrand.de/>

<http://www.dieneuendeutschpoeten.com/>

<http://www.fusion-festival.de/>

<http://www.helene-beach-festival.de/>

<http://www.highfield.de/>

<http://www.immergutrocken.de/>

<http://www.juicybeats.net/de>

<http://www.juicybeats.net/de/news/line-up-2018/90>

<http://www.kosmonaut-festival.de/>

<http://www.lollapaloozade.com/>

<http://www.msdockville.de/>

<http://www.open-flair.de/>

<http://www.openairgampel.ch/>

<http://www.pfingstopenair.de/>

<http://www.puch-openair.de/>

<http://www.pureandcrafted.com/>

<http://www.rebstock-festival.de/>

<http://www.reeperbahnfestival.com/>

<http://www.rocco-del-schlacko.de/>

<http://www.rock-am-ring.com/>

<http://www.rocken-am-brocken.de/>

<http://www.sigmaringen.de/>

<http://www.southside.de/>

<http://www.taubertal-festival.de/>

<http://www.traumzeit-festival.de/>

<http://www.ubben-events.de/>

<http://www.wattenschlick.de/>

<https://allgood.de/features/interviews/die-sehen-mich-als-kleine-suesse-saengerin-die-keine-ahnung-hat/>

<https://archiv.fusion-festival.de/2016/de/2016/programm/band/index.html>

<https://archiv.fusion-festival.de/2018/2018/programm/band/index.html>

<https://archiv.fusion-festival.de/2019/de/2019/programm/band.html>

<https://asta.hhu.de/kultur/goldmucke-die-sommer-open-air-konzertreihe-2019/>

<https://blog.ticketmaster.de/musik/c-o-pop-koeln-2020-line-up-6229/>

<https://de-de.facebook.com/RockenAmBrocken/photos/ist-denn-schon-weihnachten-rocken-am-brocken-pr%C3%A4sentiert-die-ersten-12-acts-die-/1645879572139120/>

[https://de.wikipedia.org/wiki/Frequency\_(Musikfestival)](https://de.wikipedia.org/wiki/Frequency_(Musikfestival)){.uri}

<https://de.wikipedia.org/wiki/Modular_Festival>

<https://de.wikipedia.org/wiki/Open_Air_St._Gallen>

[https://de.wikipedia.org/wiki/Razz\_(Band)](https://de.wikipedia.org/wiki/Razz_(Band)){.uri}

<https://de.wikipedia.org/wiki/Rock_am_Ring>

<https://de.wikipedia.org/wiki/Rocken_am_Brocken>

<https://de.wikipedia.org/wiki/Rolling_Stone_Weekender>

<https://de.wikipedia.org/wiki/Schmutzki>

[https://de.wikipedia.org/wiki/Southside\_(Festival)](https://de.wikipedia.org/wiki/Southside_(Festival)){.uri}

<https://der.orf.at/unternehmen/aktuell/fm4_geburtstagsfest100.html>

<https://desc-photography.com/2019/05/27/lisa-morgenstern-fil-bo-riva-2019-fzw-dortmund/#>

<https://diffusmag.de/p/neue-bands-fuers-kosmonaut-festival/>

<https://engelsburg.club/program-punkt/rikas-live/>

<https://fastforward-magazine.de/sziget-festival-2019-bosse-leoniden-sophie-hunger-hearts-hearts-und-viele-weitere-fuer-die-europe-stage-bestaetigt/>

<https://feel-festival.de/timetable-2016/>

<https://festivalisten.de/77330-highfield-2016-veroeffentlicht-zeitplan/>

<https://freizeitparknewsnrw.de/news/2018/neue-bands-fuer-rolling-stone-park-im-europa-park/>

<https://hb-people.de/bilder/fil-bo-riva-im-modernes/>

<https://herzmukke.de/magazin/malzwiese/>

<https://herzmukke.de/magazin/nuernberg-pop-festival/>

<https://images.app.goo.gl/DraDTtv8rCQED5jz9>

<https://images.app.goo.gl/NWaSVLRvaD1tSjXC9>

<https://kerstinmusl.com/blog/day-one-auf-dem-kosmonaut-festival-mit-den-geheimen-headlinern-drangsal-feine-sahne-fischfilet/>

<https://m.facebook.com/kulturinselwoehrmuehle/photos/a.131980284911011/279376410171397/?type=3&source=48&__tn__=EHH-R>

<https://m.facebook.com/RockenAmBrocken/photos/a.301143283279429/1783143288412747/?type=3&locale2=de_DE>

<https://m.facebook.com/RockimPark/photos/a.263334004479/10154569426834480/?type=3>

<https://m.facebook.com/summernightssigmaringen/photos/a.1578322969077065/1736052216637472/?type=3&__tn__=-R>

<https://mediadb.nordbayern.de/live/npop18/sites/bands.html>

<https://minutenmusik.de/vorbericht/ein-festival-fuer-liebhaber-das-way-back-when-geht-in-die-naechste-runde>

<https://musikmussmit.de/review-kosmonaut-festival/>

<https://nuernberg-pop.com/history/>

<https://schallgefluester.de/2018/08/fotos-gamescom-city-festival-2018-mit-fortuna-ehrenfeld-tonbandgeraet-kettcar/>

<https://schallgefluester.de/tag/tonbandgeraet/>

<https://sensor-magazin.de/summer-in-the-city-olli-schulz-am-17-august-auf-der-zitadelle/>

<https://sound-of-the-forest.de/history/>

<https://themellowmusic.com/amilli-singt-mit-annenmaykantereit-bang-bang/>

<https://themellowmusic.com/fil-bo-riva-in-koeln/>

<https://tvnoir.de/video/bosse-landungsbruecken-raus-kettcar-cover/>

<https://www.be-subjective.de/events/vorberichte/pre-nah-am-wasser-open-air-2018/>

<https://www.br.de/presse/inhalt/pressemitteilungen/puls-open-air-headliner-100.html>

<https://www.br.de/puls/musik/aktuell/puls-festival-2017-100.html>

<https://www.br.de/puls/musik/aktuell/puls-open-air-2018-1-welle-100.html>

<https://www.br.de/puls/musik/aktuell/puls-open-air-2019-zweite-bandwelle-100.html>

<https://www.br.de/puls/musik/bands/interview-drangsal-harieschaim-100.html>

<https://www.chilli-freiburg.de/stadtgeplauder/kultur/cd-rezi-crucchi-gang-von-crucchi-gang/>

<https://www.duesseldorf-tonight.de/events/e-werk-koeln/25-jahre-intro.442918.html>

<https://www.egofm.de/musik/entdecken/die-egofm-privataudienz-mit-crucchi-gang>

<https://www.events.at/e/wanda-w-truemmer-und-schnipo-schranke-the-second-waltz>

<https://www.facebook.com/ahoiifestival/>

<https://www.facebook.com/bossemusik/photos/a.176406435706418/2792300080783694/?type=3&comment_id=2792412754105760>

<https://www.facebook.com/BrucknerMusik/photos/a.452722924770709/3033783803331262/?type=3>

<https://www.facebook.com/events/2066716783644368/>

<https://www.facebook.com/events/419139765193087/>

<https://www.facebook.com/events/kulturzentrum-engelsburg/rikas-i-fibel-i-erfurt-i-engelsburg/205050916915857/>

<https://www.facebook.com/fabermusik/posts/hei%C3%9Ft-unseren-support-willkommen-fil-bo-rivaer-ist-bei-folgenden-dates-der-tour-/1098167723537238/>

<https://www.facebook.com/kraftklub/photos/a.10151629984224754.1073741826.270836039753/10155959111799754/?type=3>

<https://www.facebook.com/kulturzentrum.ewerk/photos/gm.1937256903227751/10154455672445732>

<https://www.facebook.com/outofthewoodsfestival/posts/drangsal-milky-chance-acoda-wenzlpichler/2859126350777072/>

<https://www.facebook.com/pulsopenair/photos/ihr-wollt-leoniden-bosse-oder-annenmaykantereit-sehen-aber-das-konzert-in-eurer-/1019371828263507/>

<https://www.festivalhopper.de/bands/karten/bonaparte.php>

<https://www.festivalhopper.de/bands/karten/bosse.php>

<https://www.festivalhopper.de/bands/karten/faber.php>

<https://www.festivalhopper.de/bands/karten/milliarden.php>

<https://www.festivalhopper.de/bands/karten/olli-schulz.php>

<https://www.festivalhopper.de/festival/tickets/a-summers-tale-2019.php#lineup>

<https://www.festivalhopper.de/festival/tickets/appletree-garden-festival-2017.php>

<https://www.festivalhopper.de/festival/tickets/appletree-garden-festival-2018.php#lineup>

<https://www.festivalhopper.de/festival/tickets/appletree-garden-festival-2019.php>

<https://www.festivalhopper.de/festival/tickets/asta-sommerfestival-2016.php#lineup>

<https://www.festivalhopper.de/festival/tickets/berlin-independent-night-2015.php#lineup>

<https://www.festivalhopper.de/festival/tickets/blank-it-open-air-2017.php#lineup>

<https://www.festivalhopper.de/festival/tickets/bochum-total-2016.php#lineup>

<https://www.festivalhopper.de/festival/tickets/campusfest-leipzig-2015.php#lineup>

<https://www.festivalhopper.de/festival/tickets/chiemsee-summer-2015.php>

<https://www.festivalhopper.de/festival/tickets/chiemsee-summer-2017.php>

<https://www.festivalhopper.de/festival/tickets/co-pop-2015.php>

<https://www.festivalhopper.de/festival/tickets/das-fest-karlsruhe-2016.php#lineup>

<https://www.festivalhopper.de/festival/tickets/deichbrand-rockfestival-am-meer-2015.php>

<https://www.festivalhopper.de/festival/tickets/deichbrand-rockfestival-am-meer-2016.php#lineup>

<https://www.festivalhopper.de/festival/tickets/deichbrand-rockfestival-am-meer-2017.php>

<https://www.festivalhopper.de/festival/tickets/deichbrand-rockfestival-am-meer-2018.php#lineup>

<https://www.festivalhopper.de/festival/tickets/deichbrand-rockfestival-am-meer-2019.php>

<https://www.festivalhopper.de/festival/tickets/dockville-2018.php#lineup>

<https://www.festivalhopper.de/festival/tickets/dockville-2019.php#lineup>

<https://www.festivalhopper.de/festival/tickets/eurosonic-noorderslag-2017.php>

<https://www.festivalhopper.de/festival/tickets/feel-festival-2015.php#lineup>

<https://www.festivalhopper.de/festival/tickets/fm-4-frequency-festival-2019.php>

<https://www.festivalhopper.de/festival/tickets/fritz-die-neuen-deutschpoeten-2017.php#lineup>

<https://www.festivalhopper.de/festival/tickets/fusion-festival-2018.php#lineup>

<https://www.festivalhopper.de/festival/tickets/gurten-festival-2017.php>

<https://www.festivalhopper.de/festival/tickets/gurten-festival-2018.php>

<https://www.festivalhopper.de/festival/tickets/haldern-pop-festival-2017.php>

<https://www.festivalhopper.de/festival/tickets/happiness-festival-2017.php>

<https://www.festivalhopper.de/festival/tickets/helene-beach-festival-2017.php#lineup>

<https://www.festivalhopper.de/festival/tickets/hessentag-2017.php#lineup>

<https://www.festivalhopper.de/festival/tickets/highfield-2015.php>

<https://www.festivalhopper.de/festival/tickets/highfield-2016.php#lineup>

<https://www.festivalhopper.de/festival/tickets/highfield-2017.php>

<https://www.festivalhopper.de/festival/tickets/highfield-2019.php>

<https://www.festivalhopper.de/festival/tickets/horn-to-be-wild-festival-2019.php#lineup>

<https://www.festivalhopper.de/festival/tickets/hurricane-festival-2015.php#lineup>

<https://www.festivalhopper.de/festival/tickets/hurricane-festival-2019.php#lineup>

<https://www.festivalhopper.de/festival/tickets/immergut-festival-2018.php>

<https://www.festivalhopper.de/festival/tickets/immergut-festival-2019.php>

<https://www.festivalhopper.de/festival/tickets/in.die.musik-open-air-2019.php>

<https://www.festivalhopper.de/festival/tickets/juicy-beats-2019.php>

<https://www.festivalhopper.de/festival/tickets/kieler-woche-2015.php#lineup>

<https://www.festivalhopper.de/festival/tickets/kosmonaut-festival-2015.php>

<https://www.festivalhopper.de/festival/tickets/kosmonaut-festival-2016.php>

<https://www.festivalhopper.de/festival/tickets/kosmonaut-festival-2017.php>

<https://www.festivalhopper.de/festival/tickets/kosmonaut-festival-2018.php#lineup>

<https://www.festivalhopper.de/festival/tickets/kosmonaut-festival-2019.php>

<https://www.festivalhopper.de/festival/tickets/lollapalooza-berlin-2018.php>

<https://www.festivalhopper.de/festival/tickets/lollapalooza-berlin-2019.php>

<https://www.festivalhopper.de/festival/tickets/mini-rock-festival-2017.php#lineup>

<https://www.festivalhopper.de/festival/tickets/musikschutzgebiet-festival-2017.php#lineup>

<https://www.festivalhopper.de/festival/tickets/new-fall-festival-2015.php#lineup>

<https://www.festivalhopper.de/festival/tickets/new-fall-festival-2017.php>

<https://www.festivalhopper.de/festival/tickets/open-flair-festival-2015.php>

<https://www.festivalhopper.de/festival/tickets/open-flair-festival-2018.php>

<https://www.festivalhopper.de/festival/tickets/open-flair-festival-2019.php>

<https://www.festivalhopper.de/festival/tickets/openair-st-gallen-2019.php>

<https://www.festivalhopper.de/festival/tickets/pfingst-open-air-2015.php#lineup>

<https://www.festivalhopper.de/festival/tickets/puls-open-air-2016.php#lineup>

<https://www.festivalhopper.de/festival/tickets/puls-open-air-2017.php>

<https://www.festivalhopper.de/festival/tickets/puls-open-air-2019.php#lineup>

<https://www.festivalhopper.de/festival/tickets/reeperbahn-festival-2015.php#lineup>

<https://www.festivalhopper.de/festival/tickets/rocco-del-schlacko-2015.php>

<https://www.festivalhopper.de/festival/tickets/rocco-del-schlacko-2018.php>

<https://www.festivalhopper.de/festival/tickets/rock-am-ring-2016.php#lineup>

<https://www.festivalhopper.de/festival/tickets/rock-am-ring-2017.php>

<https://www.festivalhopper.de/festival/tickets/rock-am-ring-2018.php#lineup>

<https://www.festivalhopper.de/festival/tickets/rock-im-park-2016.php#lineup>

<https://www.festivalhopper.de/festival/tickets/rock-im-park-2018.php#lineup>

<https://www.festivalhopper.de/festival/tickets/rocken-am-brocken-2017.php#lineup>

<https://www.festivalhopper.de/festival/tickets/rocken-am-brocken-2018.php#lineup>

<https://www.festivalhopper.de/festival/tickets/sound-of-the-forest-2016.php>

<https://www.festivalhopper.de/festival/tickets/southside-festival-2015.php#lineup>

<https://www.festivalhopper.de/festival/tickets/southside-festival-2019.php#lineup>

<https://www.festivalhopper.de/festival/tickets/szene-open-air-2018.php>

<https://www.festivalhopper.de/festival/tickets/szene-open-air-2019.php#lineup>

<https://www.festivalhopper.de/festival/tickets/sziget-festival-2015.php>

<https://www.festivalhopper.de/festival/tickets/sziget-festival-2018.php>

<https://www.festivalhopper.de/festival/tickets/taubertal-festival-2015.php>

<https://www.festivalhopper.de/festival/tickets/taubertal-festival-2018.php>

<https://www.festivalhopper.de/festival/tickets/taubertal-festival-2019.php#lineup>

<https://www.festivalhopper.de/festival/tickets/traumzeit-festival-2015.php#lineup>

<https://www.festivalhopper.de/festival/tickets/traumzeit-festival-2016.php#lineup>

<https://www.festivalhopper.de/festival/tickets/traumzeit-festival-2017.php>

<https://www.festivalhopper.de/festival/tickets/trebur-open-air-2019.php#lineup>

<https://www.festivalhopper.de/festival/tickets/utopia-island-festival-2016.php>

<https://www.festivalhopper.de/festival/tickets/way-back-when-festival-2017.php#lineup>

<https://www.festivalhopper.de/festival/tickets/winterthurer-musikfestwochen-2017.php>

<https://www.festivalhopper.de/festival/tickets/zusammen-leuchten-festival-2018.php#lineup>

<https://www.festivalsunited.com/festivals.php?op=showf&bergfunk-open-air-2019&fid=6537>

<https://www.festivalsunited.com/festivals.php?op=showf&campus-festival-bielefeld-2019&fid=6321>

<https://www.festivalsunited.com/festivals.php?op=showf&juicy-beats-2017&fid=4034>

<https://www.festivalsunited.com/festivals.php?op=showf&juicy-beats-2019&fid=6465>

<https://www.festivalsunited.com/festivals.php?op=showf&maifeld-derby-2015&fid=1841>

<https://www.festivalsunited.com/festivals.php?op=showf&modular-festival-2017&fid=4221>

<https://www.festivalsunited.com/festivals.php?op=showf&pop-kultur-festival-berlin-2018&fid=5546>

<https://www.festivalsunited.com/festivals.php?op=showf&popsalon-osnabrueck-2017&fid=3805>

<https://www.festivalsunited.com/festivals.php?op=showf&popsalon-osnabrueck-2018&fid=4874>

<https://www.festivalsunited.com/festivals.php?op=showf&reeperbahn-festival-2016&fid=2999>

<https://www.festivalsunited.com/festivals.php?op=showf&reeperbahn-festival-2019&fid=6638>

<https://www.festivalsunited.com/festivals.php?op=showf&reeperbahn-festival-2019&fid=6641>

<https://www.festivalsunited.com/festivals.php?op=showf&reeperbahn-festival-2019&fid=6642>

<https://www.festivalsunited.com/festivals.php?op=showf&reeperbahn-festival-2019&fid=6645>

<https://www.festivalsunited.com/festivals.php?op=showf&reeperbahn-festival-2019&fid=6646>

<https://www.festivalsunited.com/festivals.php?op=showf&rocken-am-brocken-2018&fid=5431>

<https://www.festivalsunited.com/festivals.php?op=showf&rocken-am-brocken-2019&fid=6495>

<https://www.festivalsunited.com/festivals.php?op=showf&skandalos-festival-2017&fid=4699>

<https://www.festivalsunited.com/festivals.php?op=showf&stuttgart-festival-2015&fid=2299>

<https://www.festivalsunited.com/festivals.php?op=showf&talge-open-air-2018&fid=5241>

<https://www.festivalsunited.com/festivals.php?op=showf&watt-en-schlick-fest-2018&fid=5347>

<https://www.festivalsunited.com/festivals.php?op=showf&watt-en-schlick-fest-2019&fid=6510>

<https://www.festivalsunited.com/festivals.php?op=showf&watt-en-schlick-fest-2019&fid=6512>

<https://www.festivalsunited.com/festivals.php?op=showf&watt-en-schlick-fest-2019&fid=6515>

<https://www.festivalticker.de/2016/festivals/campusfestival_konstanz/>

<https://www.festivalticker.de/2016/festivals/im_gruenen_festival/>

<https://www.festivalticker.de/2018/festivals/st_katharina_open_air/>

<https://www.festivalticker.de/festivals/blank_it_open_air/archiv/>

<https://www.festivalticker.de/festivals/feel_festival/archiv/>

<https://www.festivalticker.de/festivals/kosmonaut_festival/archiv/>

<https://www.fusion-festival.de/de/x/home>

<https://www.giga.de/events/rock-am-ring/news/rock-am-ring-2016-line-up-bands-termin-tickets-und-infos/>

<https://www.google.com/search?client=firefox-b-d&sxsrf=ALeKk005ternXavKlUnA3ZvrsJ-wMfzYrw%3A1615060208679&ei=8NxDYJKHKYqAkwWPvIPgCw&q=kosmonaut+2018+lineup&oq=kosmonaut+2018+lineup&gs_lcp=Cgdnd3Mtd2l6EAMyBAgAEA06BwgAELADEEM6BwgAEEcQsAM6AggAOgYIABAWEB5Q4xhY8yZguS5oAXACeACAAbYDiAGxCZIBBzIuNS40LTGYAQCgAQGqAQdnd3Mtd2l6yAEKwAEB&sclient=gws-wiz&ved=0ahUKEwiSv52QuJzvAhUKwKQKHQ_eALwQ4dUDCAw&uact=5>

<https://www.google.com/search?client=firefox-b-d&sxsrf=ALeKk02ss2vNxQj_Me_EY31mPZLUxPR9EA%3A1615061420415&ei=rOFDYOXwGMylkwXQsYCQCA&q=immergut+2018+lineup&oq=immergut+2018+lineup&gs_lcp=Cgdnd3Mtd2l6EAMyBggAEBYQHjoHCCMQ6gIQJzoECCMQJzoICAAQsQMQgwE6DggAELEDEIMBEMcBEKMCOgIIADoFCAAQsQM6CAguELEDEIMBOgQILhBDOgUILhCTAjoFCC4QsQM6CwguELEDEIMBEJMCOggIABDHARCjAjoICAAQxwEQrwE6BwgAEIcCEBRQu8wJWMrnCWCT6gloAXAAeACAAZEBiAHEEJIBBTExLjEwmAEAoAEBqgEHZ3dzLXdperABCsABAQ&sclient=gws-wiz&ved=0ahUKEwjl9oPSvJzvAhXM0qQKHdAYAIIQ4dUDCAw&uact=5>

<https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwihvYWKhZnvAhURCWMBHSnHBYI4ChAWMAB6BAgBEAM&url=https%3A%2F%2Fwww.duisburglive.de%2Ffileadmin%2Fcontent%2Fuser_upload%2FPI_Kettcar.pdf&usg=AOvVaw3HJW7P9uou6C1cdFqJ2TiF>

<https://www.green-juice.de/history/>

<https://www.handwritten-mag.de/festival-sommer-2019-alternative-indie/>

<https://www.hurricane.de/de/infos/news/bandwelle-2-ist-am-start1/>

<https://www.instagram.com/socialsofafestival/>

<https://www.intro.de/popmusik/unter-einem-dach-festival-2017-mit-hanna-leess-schmutzki-fil-bo-riva-u-v-m>

<https://www.jazzclub-leipzig.de/kategorie-jazzkalender/jazzkalender-termine/campusfest-10/>

<https://www.kassablanca.de/programm/details/event/fil-bo-riva-support-rikas-2196/>

<https://www.kingstar-music.com/portfolio-items/nah-am-wasser-open-air/>

<https://www.kosmonaut-festival.de/acts/>

<https://www.landstreicher-konzerte.de/dates/razz-17-dresden/>

<https://www.landstreicher-konzerte.de/dates/razz/>

<https://www.maifeld-derby.de/line-up/history>

<https://www.mojo.de/program/termindetails/event/mojo/special-reeperbahnfestival-2016/show/>

<https://www.msdockville.de/festival/2016/>

<https://www.msdockville.de/festival/2018/>

<https://www.msdockville.de/festival/2019/>

<https://www.munichmag.de/events/social-sofa-festival-mit-faber-mine-ok-kid-rikas-uvm/>

<https://www.musikblog.de/2018/06/puls-open-air-2018/>

<https://www.musikblog.de/2019/09/reeperbahn-festival-2019/>

<https://www.musikexpress.de/co-pop-xoxo-mit-the-screenshots-blond-das-digitale-festival-findet-vom-21-bis-24-oktober-statt-1625205/>

<https://www.musikexpress.de/deichbrand-festival-2018-seht-bilderbuch-editors-kettcar-und-co-im-livestream-1087137/>

<https://www.musikexpress.de/hurricane-festival-2019-was-ihr-jetzt-noch-wissen-muesst-1298657/>

<https://www.musikexpress.de/kettcar-scheine-in-den-graben-stream-1203719/>

<https://www.musikexpress.de/klubtour-2017-wir-bringen-dj-hell-drangsal-bonaparte-und-co-in-eure-stadt-831037/>

<https://www.musikexpress.de/kosmonaut-die-auftritte-584473/>

<https://www.musikexpress.de/me-praesentiert-das-festival-fuer-junge-menschen-hat-nicht-nur-einen-guten-namen-694151/>

<https://www.musikexpress.de/mit-nura-bosse-shame-und-serious-klein-kosmonaut-festival-2019-verkuendet-erste-bands-1168771/>

<https://www.musikexpress.de/wanda-und-olli-schulz-in-berlin-sympathisch-wie-ein-ganzer-monat-ohne-facebook-1115594/>

<https://www.musikexpress.de/zeitgleich-festival-live-streaming-event-mit-bosse-und-aetna-1584145/>

<https://www.ndr.de/nachrichten/niedersachsen/hurricane_festival/Hurricane-2020-virtuell-mit-Abstand-Musik-ohne-Fans,hurricane4104.html>

<https://www.nord24.de/zeven/Hurricane-Festival-Bilder-vom-ersten-Tag-28568.html>

<https://www.nordkurier.de/kultur-und-freizeit/olli-schulz-und-schnipo-schranke-auf-dem-fusion-festival-2032365906.html>

<https://www.open-flair.de/2018/artists>

<https://www.open-flair.de/news/656-beatsteaks-faber-drangsal-fatoni-mr-hurley-die-pulveraffen-blackout-problems>

<https://www.openairguide.net/festivals/schweiz/open-air/_history/2018/_bands>

<https://www.phonostar.de/radio/milliarden-und-drangsal/v/176258/2021-02-15>

<https://www.rbb-online.de/unternehmen/presse/presseinformationen/programm/2016/05/20160517_fritz_deutschpoeten_2016.html>

<https://www.regioactive.de/news/2017/05/08/rocken-am-brocken-im-august-2017-mit-bosse-drangsal-milliarden-uvm-pVB6hb9yJd.html>

<https://www.rheinpfalz.de/kultur_artikel,-rock-am-ring-zur%C3%BCck-zu-alter-form-_arid,1185054.html>

<https://www.rollingstone-park.de/public/event/das-war-2018/>

<https://www.schwaebische.de/landkreis/landkreis-sigmaringen/sigmaringen_artikel,-bosse-und-wanda-kommen-zum-open-air-_arid,10409057.html>

<https://www.seatsounds-kioskkonzerte.de/>

<https://www.singoldsand-festival.de>

<https://www.soundprojekt.de/galerie-leser/casper-bosse-wanda-elbufer-dresden-2015.html>

<https://www.southside.de/de/infos/news/das-war-das-southside-festival-2019/>

<https://www.stop-kohle.de/ablauf-2/>

<https://www.swp.de/unterhaltung/musik/bonaparte_-viagra-boys-und-15-weitere-bands-bekannt-30591319.html>

<https://www.swr3.de/das-fest/mando-diao-olli-schulz-marteria--gloria-strmen-den-hgel-100.html>

<https://www.technocity.berlin/fusion-festival-line-up-2018/>

<https://www.theclubmap.com/2017/11/09/48297>

<https://www.tonspion.de/news/malzwiese-festival-2018-berlin-mit-bonaparte-die-hoechste-eisenbahn-und-leyya>

<https://www.urbanite.net/de/dresden/artikel/campus-festival-unirocks>

<https://www.vonwegenlisbeth.de/alte-konzerte/>

<https://www.vonwegenlisbeth.de/das-fest/>

<https://www.wa.de/hamm/band-giant-rooks-hamm-begeistert-support-kraftklub-auftritte-luxemburg-belgien-6099048.html>

<https://www.wandamusik.com/2015/02/22/wanda-mit-kraftklub-auf-grosser-tour/>

<https://www.waybackwhen.de/lineup/lineup-2016/>

<https://www.weser-kurier.de/bremen/breminale_artikel,-breminale-gibt-bandpaket-bekannt-_arid,1590050.html>

<https://www.weser-kurier.de/region/achimer-kurier_artikel,-Unplugged-in-der-Kantine-_arid,1244853.html>

<https://www.youtube.com/watch?v=N0SyR3hFBVw>

<https://www.youtube.com/watch?v=STww9lKQXTg>

<https://zipser.at/blog/donaukanaltreiben/>

# 7. Codebuch

```{r Übersicht Netzwerkattribute}
list.vertex.attributes(indie)
# vertex.attributes(s)
list.edge.attributes(indie)
# edge.attributes(s)
```

Das Netzwerk hat nach dem [Codebuch](https://github.com/lz029/226305-SNA-WS-21-22/blob/main/Indie/INDIE-Codebuch.md) folgende Attribute:

*EDGE-Attribute*

**id**\
(eindeutige Codierung des Knoten)\
codiert nach den ersten vier Buchstaben der Künstler:innen und Bands, jede ID entspricht einem/einer Künstler:in bzw . Ban d

**weight**\
Beziehungsstärke\
4 = Feature (Gemeinsamer Song)\
3 = Gemeinsam auf Tour / gemeinsame Auftritte / Support\
2 = gemeinsames Musiklabel\
1 = Selbes Fest ival

**time**\
Jahreszahl der Kooperation als YYYY

**source**\
Informationsquelle zu der Kooperation

**what**\
Art der Kooperation

*NODE-Attribute*

**id**\
Identische ID wie aus der Edgelist zur Identifikation der Knoten

**name**\
Name des/der Künstler:in bzw.Band

**personen**\
Anzahl der Mitglieder

**musiklabel**\
Aktuelles und frühere Musiklabel der Band bzw.Künstler:in

**instagram**\
Anzahl der Instagram-Follower:innen zum Stichtag 07.03.2021 in Tausend

**spotify**\
Monatliche Hörer:innen auf Spotify zum Stichtag 07.03.2021 in Tausend

Die Vertex-Attribute treffen auf alle Knoten zu.

## Datenmaterial und Skript

[Datensatz](https://github.com/lz029/226305-SNA-WS-21-22/tree/main/Indie)

## Team, Arbeitsaufwand und Lessons Learned

### Teammitglieder

Silas Schwab (ss502)\
Fabienne Schackert (fs138)\
Lena Klasen (lk158)\
Lioba Zangenfeind (lz029)\
Selina Hellfritsch (sh3 08)

### Arbeitsaufwand und Rollen im Team

In unserem Team gab es keine klare Rollenverteilung. Wir haben alle an allem gearbeitet und die Aufgaben immer gerecht untereinander aufgeteilt. Hierzu haben wir uns seit Beginn des vierten Semesters wöchentlich getroffen, um in einer Co-Working-Atmosphäre miteinander zu arbeiten und uns bei Problemen direkt austauschen zu können. Neben diesen wöchtentlichen Treffen hat jede:r von uns mehrere Tage in die Datenerhebung gesteckt. Generell wurde seit Beginn des Jahres, also auch schon vor dem vierten Semester, regelmäßig Zeit in das Projekt gesteckt.

Wir haben unsere Zeiten nie protokolliert, weshalb wir keine Stundenzahl aufschreiben könnten, die verlässlich wäre. Wir haben viel Zeit investiert und waren gefordert, haben aber sehr gut im Team zusammengearbeitet und alle gleich viel Aufwand in das Projekt gesteckt.

### Lessons Learned

Wir haben besonders am Anfang die Arbeit sehr unterschätzt. Wir haben nicht lange genug über das enorme Ausmaß unserer Datenerhebung nachgedacht und viel zu viele Daten erhoben. Die Datenerhebung werden wir somit beim nächsten Mal gut überlegt angehen und uns im Voraus mehr Gedanken darüber machen, in welcher Dimension wir die Daten erheben. Ansonsten haben wir gelernt, dass gute Arbeitsaufteilung und Strukturierung wichtig sind. Jede:r hatte von Anfang an sein:ihr Aufgabengebiet, was ideal war. Durch wöchentliche Treffen konnten wir uns im Co-Working-Space gegenseitig unterstützen, blieben kontinuierlich am Ball und konnten uns ein stressiges Ende bewahren, da wir im Voraus bereits viel gearbeitet hatten. Was R angeht hatten wir unsere Schwierigkeiten, haben aber gelernt, uns nicht abschrecken zu lassen und sind so zu einem für uns zufriedenstellenden Ergebnis gekommen.
