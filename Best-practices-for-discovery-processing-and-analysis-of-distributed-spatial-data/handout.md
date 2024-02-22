erstellt von @MinoruAmaya

# Best practices for discovery, processing and analysis of distributed spatial data
## OGC-Standards vs. De-facto-Standards


### Was sind OGC-Standards?

OGC steht für das Open Geospatial Consortium, eine Organisation, die Standards für den Austausch und die Nutzung von geografischen Daten entwickelt. OGC-Standards sind offizielle Spezifikationen, die von der Gemeinschaft der Geoinformatiker erarbeitet und verabschiedet wurden. Im OGC-Kontext ist ein Standard eine vereinbarte Spezifikation von Regeln und Richtlinien für die Implementierung von Softwareschnittstellen und Datenkodierungen Diese Standards legen fest, wie räumliche Daten im Internet ausgetauscht und genutzt werden können, um die Zusammenarbeit zwischen verschiedenen geografischen Informationssystemen zu erleichtern. Beispiele für OGC-Standards sind WMS (Web Map Service), WFS (Web Feature Service), WMTS (Web Map Tiles Service) und OGC API-Features.


### Was sind De-facto-Standards?

De-facto-Standards sind Lösungen, Technologien, Produkte oder Protokolle, die sich in der Praxis weit verbreitet haben und allgemein akzeptiert sind. Obwohl es nicht von einer bestimmten Organisation formal standardisiert wurde, wird es weitgehend akzeptiert und genutzt, was es zu einem De-facto-Standard macht. Sie entstehen oft durch die weitreichende Nutzung und Akzeptanz bestimmter Technologien oder Lösungen in der Branche. De-facto-Standards können in verschiedenen Bereichen auftreten, einschließlich Softwareentwicklung, Datenverarbeitung und -analyse. Beispiele für De-facto-Standards sind QWERTZ-Tastaturformat, MPEG-4-Videoformat und die HTML-Websprache. Im Bereich räumlicher Daten sind GDAL (Geospatial Data Abstraction Library), SpatiaLite und STAC (SpatioTemporal Asset Catalog) ebenfalls De-facto-Standards.


### Warum brauchen wir Standards im Bereich räumlicher Daten?

Standards ermöglichen die Interoperabilität zwischen verschiedenen GIS-Systemen, Anwendungen und Datenquellen. Ohne klare Standards könnten räumliche Daten schwer miteinander kommunizieren, was den Datenaustausch und die Zusammenarbeit erschweren würde. Außerdem erleichtern sie die Integration verschiedener Datenquellen, sei es geografische Vektordaten, Rasterdaten, Aonaordaten oder Medaten. Ebenfalls können die Entwickler durch die Einhaltung von Standards sicherstellen, dass ihre Anwendungen und Dienste reibungslos mit anderen Systemen zusammenarbeiten können. Standards schaffen außerdem eine Grundlage für Innovationen, da sie Entwicklern ermöglichen, auf bewährten Technologien aufzubauen und neue Ideen zu entwickeln, ohne von Grund auf neu beginnen zu müssen.


### Vor- und Nachteile im Bereich räumlicher Daten
**Vorteile von OGC-Standards:**

OGC-Standards werden durch einen strukturierten Prozess entwickelt und bieten klare, formale Spezifikationen. Sie sind auf internationaler Ebene anerkannt und erleichtern die Interoperabilität auf globaler Ebene. Außerdem fördern sie die Interoperabilität zwischen verschiedenen GIS-Systemen und ermöglichen den reibungslosen Austausch von räumlichen Daten.

**Nachteile von OGC-Standards:**

Die formelle Entwicklung von OGC-Standards kann zeitaufwendig sein, da sie auf Konsens und Feedback vieler Interessengruppen basiert. Dazu können detaillierte Spetzifikationen komplex sein und erfordern einen gewisse Einarbeitungszeit für die Entwickler.

**Vorteile von De-facto-Standards:**

De-facto-Standards bieten untereinander einheitliche und weiterhin unterstütze Plattform für die Interaktion von Geräten und Technologien und ermöglichen somit eine schnellere Entwicklung eun effizientere Nutzung der Ressourcen. Sie entwickeln sich aufgrund ihrer praktischen Anwendbarkeit und Verbreitung weiter, was zu flexibleren Lösungen führen kann. Da sie oft auf praktischen Anwendungen basieren, können De-facto-Standards schneller angenommen werden und eine breitere Anwenderbasis haben. Des Weiteren neigen sie dazu, einfacher und weniger formal zu sein, was die Anwendung und Implementierung erleichtert.


**Nachteile von De-facto-Standards:**

De-facto-Standards haben nicht die offizielle Unterstüzung und Überwachung einer formellen Norm, was bedeutet, dass es keine Garantie für Qualität oder Zuverlässigkeit gibt und die Norm jederzeit veraltet oder durch eine neue Technologie ersetzt werden kann.

### Wann nutzt man OGC-Standards?
Wenn die Interoperabilität zwischen verschiedenen GIS-Systemen und Datenquellen von höchster Bedeutung ist, sind OGC-Standards die richtige Wahl. Diese bieten klare Spezifiktaionen und fördern einheitliche Standards für den Austausch räumlicher Daten. In Szenarien, in denen branchenübergreifende Zusammenarbeit und der Autausch von geografischen Informationen mit verschiedenen Organisationen erforderlich sind, bieten OGC-Standards eine solide Grundlage. Wenn zum Beispiel langfristige Stabilität und Planung wichtig sind, sind OGC-Standards die bevorzugte Wahl. Diese Standards werden von einer formellen Organisation verwaltet und haben einen etablierten Entwicklungsprozess. 

### Wann nutzt man De-facto-Standards?
Wenn eine schnelle Entwicklung und Implementierung erforderlich sind, können De-facto-Standards wie GDAL oder GeoJSON effizienter sein. Diese Lösungen sind oft durch Bedürfnisse, Erfahrungen und Beiträgen aus der Praxis gewachsen und werden von Entwicklern gut angenommen. Wenn eine Lösung bereits weit verbreitet und von der Entwicklergemeinschaft aktzeptiert ist, kann die Nutzung eines De-facto-Standards Zeit sparen und eine breitere Anwenderbasis haben. In Fällen, in denen spezifische Anforderungen oder Anwendungsfälle flexiblere Lösungen erfordern, können De-facto-Standards besser geeignet sein. Sie neigen dazu, einfacher und anpassungsfähiger zu sein.

In einigen Fällen kann eine Kombination beider Standards die beste lösung sein.






### Gegenüberstellung der beliebten Arten der beiden Standardsformen

**OGC-Standards:**

WMS (Web Map Service): 
+ Ein OGC-Standard, der die Bereitstellung von Kartenbildern über das Internet ermöglicht. Es spezifiziert, wie Karten in verschiedenen Formaten abgerufen und angezeigt werden können.
+ Die Datenart ist in Form von Rasterdaten (Kartenbilder).
+ Die Interaktion verläuft über die einfache Darstellung von Karten für den Nutzer.

WFS (Web Feature Services): 
+ Diese ermöglicht den Zugriff auf geografische Vektordaten über das Internet. WFS definiert, wie Features (Objekte wie Punkte, Linien und Polygone) abgefragt und manipuliert werden können.
+ Die Datenart ist in Form von Vektordaten (Features wie Punkte, Linien, Polygone).
+ Die Interaktion verläuft über eine Abfrage und Manipulation von Vektordaten.

**De-facto-Standards:**
GDAL (Geospatial data abstraction library): 
+ Eine Bibliothek für die Übersetzung und Manipulation von räumlichen Datenformaten. GDAL hat sich als weit verbreiteter Standard für die Arbeit mit geografischen Daten etabliert.
+ Die Datenart ist in Form von Rasterdaten und Vektordaten.
+ Die Interaktion verläuft über die Verwendung für Datenzugriff und -verarbeitung von dem Entwickler.

GeoJSON: 
+ Ein offenes, textbasiertes Datenformat für die Repräsentation von geografischen Datenobjekten. GeoJSON ist einfach zu verwenden und hat sich als De-facto-Standard für den Austausch von räumlichen Daten in Webanwendungen durchgesetzt.
+ Die Datenart ist in Form von Vektordaten in JSON-Format.
+ Die Interaktion verläuft über den einfachen Austausch von geografischen Daten zwischen Webanwendungen.

STAC (Spatio Temporal Asset Catalog): 
+ Obwohl es sich in der Entwicklung befindet, könnte STAC bald als De-facto-Standard für die Katalogisierung von räumlichen und zeitlichen Vermögenswerten (Datensätze, die in einem STAC-Katalog katalogisiert und beschrieben werden), insbesondere Satellitenbildern, fungieren.
+ Die Datenart ist in Form von Metadaten über räumliche und zeitliche Vermögenswerte.
+ Die Interaktion vereinfacht den Austausch und die Suche nach Satellitendaten.


### Zusammenfassung der Gegenüberstellung

In Betracht der Nutzung und des Zweckes sind WMS und WFS ideal für die Bereitstellung und Abfrage von geografischen Daten in GIS-Anwendungen. GeoJSON dient als einfacher Datenaustauschformat für Vektordaten, gut geeignet für Webanwendungen. Darüber hinaus fokussiert sich STAC auf die Katalogisierung und Beschreibung von räumlichen und zeitlichen Vermögenswerte, vorallem Satellitenbilder. GDAL ist dagegen eine Bibliothek für Datenübersetzung und -manipulation, weit verbreitet in der räumlichen Datenverarbeitung, welches ebenfalls sich gut eignet für webbasierte Anwendungen und Datenverarbeitungen.






### Literaturverzeichnis

Arten von OGC-Standards:https://opengeospatial.github.io/e-learning/ogc-standards/text/services-ogc.html#types-of-standards

Wie kann man OGC-Standards besser verwenden: https://www.linkedin.com/advice/0/how-can-you-use-ogc-standards-better-7nl6f

Definition OGC-Standards: 
https://opengeospatial.github.io/e-learning/ogc-standards/text/services-ogc.html
https://www.ogc.org/standards/
https://opengeospatial.github.io/e-learning/ogc-standards/text/services-ogc.html#types-of-standards

Definition De-facto-Standards: 
https://wirtschaftslexikon.gabler.de/definition/de-facto-standard-31199
https://datei.wiki/definition/verstaendnis-von-de-facto-normen/

GIS-Standards: https://www.gistandards.eu/de/gis-standards/

Build interoperable, geospatial, solutions with OGC standards: https://developer.ogc.org/#learn

OGC-Api: https://ogcapi.ogc.org/

Geodienste-Standards des OGC: https://www.geodaten.niedersachsen.de/startseite/gdi_standards/ogc_dienste_in_der_praxis/ogc-dienste-in-der-praxis-108069.html















