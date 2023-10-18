# **Remote Sensing in R**
Autoren: [@starke01](https://github.com/starke01), [@kgalb01](https://github.com/kgalb01)<br/></br>

## **1. Motivation**
Warum wird R für Fernerkundung genutzt?
* Volle programmatische Kontrolle:
  * Anders als die üblichen Umgebungen zum Verarbeiten von Fernerkundungsdaten (z.B. QGIS), kann R völlig an spezifische Anforderungen und Workflows angepasst werden.
  * R ist bei den meisten Anwendungen und Funktionen skalierbar. Damit kann die Effizienz, mit der große Datenmengen analysiert oder verarbeitet werden, angepasst werden, indem Einfluss auf die Art und Weise genommen wird, wie Anwendungen und Funktionen mit den Datenmengen umgehen.
* Erweiterbarkeit durch Pakete:
  * Die R-Community entwickelt ständig neue Pakete zum Arbeiten mit Fernerkundungsdaten.
* Machine Learning-Integration:
  * R bietet eine große Menge an Paketen zum Thema "Machine Leaning", die überwachte oder automatisierte Klassifikationen der Fernerkundungsdaten ermöglichen
 <br/><br/>
 
## **2. Datenakquise**
Fernerkundungsdaten können von unterschiedlichen Plattformen bezogen werden. Einige davon sind Open Source und bieten ihre Daten kostenlos an, andere wiederum sind kostenpflichtig. Einige Beispiele für diese Plattformen sind die folgenden Websiten:
* Rasterdaten aus verschiedenen Quellen wie zum Beispiel einige Landsat Satelliten: [USGS Earth Explorer](https://earthexplorer.usgs.gov/) (Open Source)
* Rasterdaten von Sentinel-2 Satelliten: [Copernicus Data Space](https://dataspace.copernicus.eu/browser/) (Open Source)
* Verschiedene Raumbezogene Daten aus Münster: [Open Data Münster](https://opendata.stadt-muenster.de) (Open Source) 
<br/><br/>

## **3. Packages**
R bietet eine vielfältige Sammlung von Paketen, die speziell für die Verarbeitung und Analyse von Rasterdaten entwickelt wurden. Diese Pakete erweitern die Funktionalität von R und ermöglichen es den Anwendern, komplexe Analysen und Verarbeitungen durchzuführen. Im Folgenden werden einige der wichtigen Pakete vorgestellt, es gibt aber noch viele mehr:
* Intallation & Einbindung:
  * (Erstmalige) Installation erfolgt über den Befehl "install.packages("paket_name")"
  * Jede Einbindung danach funktioniert durch "library(paket_name)"
* Raster-Paket:
  * Ermöglicht Lesen, Schreiben, Analysieren und Visualisieren von räumlichen Daten
  * Fügt verschiedene Klassen, wie zum Beispiel "RasterLayer" und "RasterStack", zu R hinzu
  * Wichtige Funktionen des Pakets:
    * "raster()" - erzeugt ein neues RasterLayer-Objekt
    * "brick()" - erzeugt ein neues RasterBrick-Objekt
    * "stack()" - erzeugt ein neues RasterStack-Objekt
    * "crop()" - Schneidet Rasterdaten auf gewünschte Größe zu
    * "readRaster()", bzw. "writeRaster()" - Einlesen und Schreiben von Rasterdaten
    * "cellStats()" - Zeigt gewüschte statistische Werte (z.B. "mean", oder "sd") zu den Rasterdaten an
    * "plotRGB()" - Dient der Visualisierung von RasterBricks und RasterStacks
 * Mapview-Paket:
   * Ermöglicht die interaktive Visualisierung räumlicher Objekte in R
   * Baut auf leaflet-Bibliothek auf und ermöglicht die Darstellung der Rasterdaten auf interaktiven Karten
   * Wichtige Funktionen des Pakets:
     * "mapview()" - Interaktive Darstellung räumlicher Objekte
     * "addHomeButton()" - Ermöglicht das Einfügen eines Buttons, der beim Drücken die Karte auf eine eingestellte Höhe vergrößert
     * "viewRGB()" - Ähnlich wie "mapview()", legt aber ein Echtfarbkomposit über die interaktive Karte
     * "mapshot()" - Ermöglicht das Speichern von Mapviews (als .html-, .pdf-, .jpeg-Datei)
 * rgdal-Paket:
   * GDAL steht für "Geospatial Data Abstraction Library"
     * rgdal ist die Schnittstelle zwischen R und der GDAL-Bibliothek, wobei GDAL eine Programmierbibliothek ist, die die Arbeit mit räumlichen Daten zu verschiedenen Schnittstellen (wie R) ermöglicht
   * Wichtige Funktionen des Pakets:
     * "readGDAL()" - Liest Rasterdaten ein als Objekt der Klasse "SpatialGrid" (nur einzelne Kanäle!)
     * "writeGDAL()" - Schreibt Rasterdaten
     * "spTransform()" - Konvertiert Rasterdaten zu anderen Koordinatensystemen
     * "crs()" - Ermöglicht das Abfragen oder Setzen von Koordinatensystemen als Objekt anhand derer Rasterdaten konvertiert werden können
* leaflet-Paket:
  * Schnittstelle zur "leaflet" - Javascript Bibliothek, ermöglicht die Erstellung von interaktiven Webkarten und bietet grundlegende Funktion zur Darstellung von Geodaten
  * Wichtige Funktionen des Pakets:
    * "leaflet()" - Erstellt ein leeres Kartenobjekt
    * "addTiles()" - Fügt eine Basiskarte hinzu
    * "addMarkers()", "addPolygons()", "addCircles()" - ermöglicht es geographische Merkmale und Daten zur Karte hinzuzufügen
    * "setView()" - legt die Karte auf einen bestimmten Punkt und Zoomlevel fest
* Weitere interessante Pakete:
  * sp: Bietet Klassen und Methoden zur räumlichen Datenanalyse
  * terra: Der Nachfolger des "raster"-Pakets. Bietet schnellere und konsistentere Schnittstellen für Rasterdaten
<br/><br/>

## **4. Einbindung der Daten in R**
Die Einbindung von Rasterdaten in R erfolgt über Funktionen aus dem Raster-Paket. Dabei gibt es unterschiedliche Arten von Rasterdatenformaten, wie zum Beispiel *.TIF -*, *.JP2 -* oder *.grd -* Dateien, die teilweise unterschiedlich eingebuden werden müssen.
* Die Daten liegen oft als einzelne Dateien für die unterschiedlichen Kanäle (Rot, Grün, Blau, Nahesinfrarot, etc.) vor. Diese Kanäle können einzeln mit der *raster()*-Funktion eingebunden werden.
  * Beispiel: *nir <- raster("name_des_kanals")* würde einen Naheninfrarotkanal einbinden können. Dieser Kanal wird an die Variable *"nir"* gebunden und ist unter diesem Namen auch im Environment von R zu finden und kann darüber aufgerufen werden.
  * Beispiel: *red <- raster("Ordnerpfad/name_des_kanals)* hat den gleichen Effekt für den roten Kanal.
* Soll ein Komposit aus mehreren Kanälen erstellt werden oder die Arbeit an mehreren Kanälen ist aus anderen Gründen benötigt, kann ein *"RasterStack"* erstellt werden, der mehrere Kanäle gleichzeitig an einen Variablennamen bindet. Voraussetzung ist, dass die Metadaten, also zum Beispiel die Auflösung, die Referenzsysteme, die Ausdehnung usw. bei allen Kanälen gleich sind. Ist das der Fall, so können die gewünschten Kanäle mit der Funktion *"stack()"* zu einem *RasterStack* erstellt werden.
  * Beispiel: *data <- stack("blauer_kanal", "gruener_kanal", "roter_kanal")*, wobei die Kanalnamen entsprechend ersetzt werden müssen.
* *.grd* - Dateien beinhalten meistens direkt mehrere Kanäle in einem Dateiformat und können somit lediglich mit Hilfe der *stack()*-Funktion oder der *brick()*-Funktion eingebunden werden.
  * Beispiel: *grd_data <- stack("dateiname.grd")*
* Mit der Funktion *brick()* können so genannte *RasterBricks* erstellt werden. Diese Funktion kann sowohl einzelne als auch mehrere Kanäle einbinden und ist etwas schneller in der Verarbeitung als die bisher bekannten Funktionen. Dafür bieten *"RasterBricks"* etwas weniger Flexibilität.
  * Beispiel: *brick_grd <- brick("dateiname.grd")*
<br/><br/>

 
## **5. Datenanalyse**
Um sich über die vorliegenden Fernerkundungsdaten einen Überblick zu verschaffen, können die Variablennamen aufgerufen werden, mit dem die Daten eingebunden sind.
  + Beispiel: *"nir"* eingeben, um Informationen über den zuvor eingebundenen Naheninfrarotkanal zu erhalten 
<br/><br/>

Auf diese Art und Weise erhält man folgende Informationen:

* Klasse: Was für eine Art von Daten liegt vor?
* Dimension: Wie viele Daten liegen vor?
* Auflösung: Welche Auflösung besitzen meine Daten?
* Ausdehnung: Welche Fläche decken meine Daten ab?
* CRS: Welches Referenzsystem (Koordinaten, Datum, etc.) nutzen meine Daten?
* Quelle: Woher stammen die Fernerkundungsdaten? Vom Speicher in R eingebunden oder durch R aus dem Internet runtergeladen?
* Namen: Wie heißen die Dateien, die eingebunden sind?
<br/><br/>

Diese Informationen können bei der Ver- und Bearbeitung der Rasterdaten nützlich sein, da an den meisten Metadaten noch etwas verändert werden kann.

* Die Klasse kann zum Teil verändert werden, zum Beispiel indem die Daten durch eine andere Funktion eingebunden werden.
  * Beispiel: *"RasterStack"* und *"RasterBrick"* aus dem letzten Abschnitt.
* Die Auflösung der Daten kann geändert werden mit Hilfe der *resample()*-Funktion aus dem Raster Paket.
  * Beispiel: *resample_data <- (resolution_30_data, resolution_20_data)*
  * Die Beispielvariablen würden entsprechend eine Auflösung von 30 x 30 Metern, bzw. 20 x 20 Metern pro Pixel haben und die Funktion würde die Variable *resolution_30_data* konvertieren zu einer Auflösung von 20 x 20 Metern pro Pixel und das Ergebnis im Variablennamen *resample_data* speichern
* Die Ausdehnung der Fernerkundungsdaten kann mit der *crop()*-Funktion aus dem Raster Paket verändert werden. Dazu werden Koordinaten über die gewünschte Ausdehnung benötigt.
    * Beispiel: *cropped_raster <- crop(data, c(Koord-1, Koord-2, Koord-3, Koord-4))*
    * Die Koordinaten müssen dabei in folgender Reihenfolge eingefügt werden:
      * Stelle 1 und 4: Koordinaten vom Punkt in der oberen linken Ecke
      * Stelle 2 und 4: Koordinaten vom Punkt in der oberen rechten Ecke
      * Stelle 1 und 3: Koordinaten vom Punkt in der unteren linken Ecke
      * Stelle 2 und 3: Koordinaten vom Punkt in der unteren rechten Ecke
    * Beispiel: cropped_muenster <- crop(muenster_data, c(394861, 5746419, 5767397))
      * Genutzt werden hier Koordinaten der ungefähren Ausdehnung von Münster im UTM-Format
* Das Referenzsystem, bzw. CRS, von Rasterdaten kann wie folgt verändert werden:
  1. Definiere ein Ziel Referenzsystem, in dem das eigene konvertiert werden soll
      * *ziel_crs <- "+proj=utm +zone=32 +datum=WGS84 +units=m +no_defs"*
      * oder *ziel_crs <- CRS("+proj=utm +zone=32 +datum=WGS84 +units=m +no_defs"*
  2. Projiziere die Rasterdaten mit der *projectRaster()*-Funktion aus dem Raster Paket um:
      * proj_data <- projectRaster(proj_data, crs=ziel_crs), wobei "proj_data" die Beispielrasterdaten sind, die umprojiziert werden sollen
        
Darüber hinaus ist es mit *summary(data)* möglich alle wichtigen statistischen Informationen der Daten zu erhalten
<br/><br/>

## **6. Visualisierung der Fernerkundungsdaten**
Die Visualisierung der Rasterdaten ist auf mehreren Arten möglich:
* *plot()* ist eine Standardfunktion in R. Sie ist flexibel und kann leicht angepasst werden. Einen *RasterStack* plottet die Funktion allerdings nicht übereinander sondern nebeneinander. Somit ist es nicht möglich ein Echtfarb- oder Falschfarbkomposit auf diese Weise zu erstellen.
  * Beispiel: *plot(data)*, wobei *"data"* Beispielrasterdaten sind
* *mapview()* ist eine Funktion aus dem Mapview Paket. Sie legt die vorhandenen Rasterdaten (auch *RasterStack*) über eine Karte oder ein Luftbild, wie zum Beispiel von OpenStreetMaps.
  * Beispiel: *mapview(data)*
* *plotRGB()* ist eine Funktion aus dem Raster Paket und bietet die Möglichkeit ein Komposit aus Rasterdaten darzustellen, indem angegeben wird welcher Kanal der blaue, gründe und rote Kanal sind.
  * Beispiel: plotRGB(echtfarb_data, b=1, g=2, r=3, stretch="lin")
    * *stretch="lin"* bewirkt, dass die maximalen Werte der Rasterdaten gestreckt werden, was zu kontrastreicheren Bildern führen kann.
  * Beispiel: plotRGB(falschfarb_data, b=2, g=3, r=4, stretch="lin")
    * Hier wurde der rote Kanal mit dem Naheninfrarotkanal ausgetauscht, um ein Falschfarbkomposit zu erstellen.
* Eine Legende lässt sich mit dem Befehl *legend()* erstellen und konfigurieren.
  * Beispiel: Zuerst: *plostRGB(...)* und dann *legend("topleft", legend=c("Echtfarbkomposit von Münster"))*
<br/><br/>

## **7. Datenverarbeitung und Transformation**
Um mit den Rasterdaten zu arbeiten, kann man, je nachdem welches Ziel verfolgt wird und wie die Daten am Ende aussehen sollen, auf verschiedenen Arten vorgehen.
* Ein einfaches Beispiel ist die Multiplikation aller Werte eines bestimmten Kanals:
  * Beispiel: nir_2 <- nir * 2, wobei *"nir"* in diesem Beispiel der Naheinfrarotkanal ist, der zuvor bereits eingebunden wurde.
* Es ist auch möglich die Werte zweier Kanäle mit einander in einem Verhältnis zu setzen, indem zum Beispiel der NWDI (bzw. Wasserindex) oder der NDVI (bzw. Vegetationsindex) berechnet wird. Der NDVI wird zum Beispiel folgendermaßen berechnet: *((NIR - RED) / (NIR * RED))*.
  * Beispiel: data$NDVI <- ((nir - red)/(nir + red))
    * Wobei *"$"* bewirkt, dass die erstellte Variable *"NDVI"* an die bereits existierende Beispielvariable *"data"* angehängt wird und auch darüber abrufbar ist
* Der NDVI kann im Weiteren für die Eingrenzung bestimmter Landnutzungsklassen verwendet werden. Zum Beispiel haben Gewässer einen NDVI-Wert von 0 oder weniger. Indem wir alle anderen Werte ausschließen, können wir alle Gewässer in unserem Untersuchungsgebiet identifizieren.
  * Beispiel: *data$gewaesser <- NDVI <= 0*
* Glätten oder Filtern von Rasterdaten kann mit der *focal()*-Funktion aus dem Raster Paket erfolgen. Dabei wendet die Anwendung eine vom Nutzer bestimmte mathematische Funktion auf eine ausgewählte Nachbarschaft von jedem Punkt an.
  * Beispiel: Wir berechnen in einem Umkreis einer 3 x 3 Matrix um jeden Punkt herum jeweils den Median aller Werte und ersetzen den Punkt mit diesem Wert. Das führt dazu, dass das Bild duetlich geglättet wird, indem statistische Ausreißer entfernt werden.
  * Die Funktion nimmt folgende drei Parameter entgegen:
    * *x*: Die Eingangsrasterdaten, auf die die Operation angewendet werden soll.
    * *w*: Die definierte räumliche Nachbarschaft, also wie groß der Umkreis sein soll, in dem die Funktion angewendet werden soll. Größere Umkreise führen oft zu Verlust von Informationen und zu "glatteren" Ergebnissen.
    * *fun*: Die Funktion, die auf die ausgewählte Nachbarschaft angewendet werden soll, wie zum Beispiel die Bestimmung des Medians oder der Standardabweichung.
  * Beispiel: *NDVI_glatt <- focal(NDVI, fun = median, w = matrix(1, nrow = 3, ncol = 3))*
<br/><br/>

## **8. Speichern**
Um die Ergebnisse als PDF oder JPG zu speichern, gibt es in RStudio Knöpfe für den Export. Rasterdaten und andere kompliziertere Dateiformate müssen meistens per Befehl im Skript, bzw. Konsole, gespeichert werden.
* Das Speichern einer PDF-Datei wird eingeleitet durch den Befehl *pdf()*, der standardmäßig in R verfügbar ist. Auf dem Befehl folgt *was* gespeichert werden soll, also zum Beispiel die Anweisung *plott(data)*. Daraufhin kann das Speichern mit einem extra Befehl *dev.off()* beendet werden.
  1. *pdf("NDVI.pdf")*
  2. *plot(NDVI)*
  3. *legend("topleft", legend=c("Echtfarbkomposit von Münster"))*
  4. *dev.off()*
* Das Speichern der Rasterdaten im Environment ist möglich durch die Funktion *writeRaster()*, die das zu speichernde Raster, den Speicherort, den Speichernamen und das Dateiformat erwartet.
  * Beispiel: *writeRaster(raster_daten, "ordner_name/raster_daten.grd")*
 
## **9. Literaturverzeichnis**
* Vorlesungsfolien: Meyer, Hannah: Fernerkundung und maschinelle Lernverfahren zur flächendeckenden Erfassung von Umweltvariablen. Teil 2: Fernerkundungsdaten in R.
* [rspatial.org](https://rspatial.org/raster/rs/index.html)
* [YouTube.com](https://www.youtube.com/watch?v=_nCUUBKKHsg)
* [Wikipedia](https://de.wikipedia.org/wiki/Geospatial_Data_Abstraction_Library)
* [Dokumentation des Mapview-Pakets](https://www.rdocumentation.org/packages/mapview/versions/2.11.0)
* [Dokumentation des Raster-Pakets](https://www.rdocumentation.org/packages/raster/versions/3.6-23)
* [Dokumentation des leaflet-Pakets](https://cran.r-project.org/web/packages/leaflet/index.html)
* [Dokumentation des rgdal-Pakets](http://cran.nexr.com/web/packages/rgdal/index.html)
