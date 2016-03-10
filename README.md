# xMZ-Mod-Touch
## Eagle Dateien Bodenplatine


## Howto's
### Material Listen (BOM) erstellen

Die Material Listen werden aus den Eagle Zeichnungen gewonnen. Hierzu werden in
Eagle zunächst über den "design link" alle Bauteile in der Farnell Datenbank
gesucht. Anschließend wird diese Liste gespeicherti (Design Link Export).

* Dateiname: "Deckelplatine $VERSION-order.txt"

Danach wird das bom.ulp in Eagle ausgeführt. Folgende Einstellungen sind zu
wählen:

	Listen-Typ: Werte (Häckchen unter "Attribute auflisten" setzen)
	Ausgabeformat: CSV

Diese Datei wird ebenfalls gespeichert.

* Dateiname: "Deckelplatine $VERSION BOM.csv"


### Farnell BOM Import

Farnell bietet die Möglichkeit über eine Web GUI die BOM Daten in eine
Bestellung umzuwandeln.

Format der CSV Datei für den Import:
- 3 Spalten ("Anzahl;	Ordercode; Beschreibung")
- Dateiformat .xlsx oder .xls


#Produktionsdaten
## Dokumentation Boardlayout Dateien

Einige der wichtigsten Ebenen (Drill, Solder, Paste) wurden einzeln zusammen
mit der "Document" Ebene (Layer 48) als PDF gedruckt (Siehe Script generate_documentaiont.scr).
Dieses PDF kann mit dem Ghostscript tool `gs` in ein PDF gewandelt werden.

```
cd doc

gs -dBATCH -dNOPAUSE -q -sDEVICE=pdfwrite -sOutputFile=Deckelplatine.pdf \
Deckelplatine-DIMENSIONS.pdf \
Deckelplatine-BOM.pdf \
Deckelplatine-Placement_TOP.pdf \
Deckelplatine-TOP.pdf \
Deckelplatine-BOTTOM.pdf \
Deckelplatine-BOTTOM-Solder-Mask.pdf \
Deckelplatine-TOP-Paste-Mask.pdf \
Deckelplatine-Drill-Drawing.pdf \
```
