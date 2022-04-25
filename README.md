# Druckdatenübertragung Dokumentation v. 1.0 (15.04.2021) 

([english version](english.md))

- [Druckdatenübertragung Dokumentation v. 1.0 (15.04.2021)](#druckdatenübertragung-dokumentation-v-10-15042021)
- [Übertragung der Druckdaten](#übertragung-der-druckdaten)
	- [Ablauf](#ablauf)
- [Bestellung](#bestellung)
	- [Felder](#felder)
		- [ReceiverAddress](#receiveraddress)
		- [SenderAddress](#senderaddress)
		- [Order](#order)
	- [Werte](#werte)
		- [Project](#project)
		- [Kind](#kind)
		- [DeliveryDate](#deliverydate)
		- [Delivery](#delivery)
		- [Technique](#technique)
		- [Lamination](#lamination)
		- [Binding](#binding)
		- [Format](#format)
		- [PaperTypeCover](#papertypecover)
		- [PaperTypeInside](#papertypeinside)
		- [ColorCover](#colorcover)
		- [FinishingOutside](#finishingoutside)
		- [FinishingInside](#finishinginside)
		- [Specials](#specials)
	- [Beispiel](#beispiel)
- [Rückmeldung](#rückmeldung)
	- [Felder](#felder-1)
	- [Werte](#werte-1)
		- [Date](#date)
		- [Status](#status)
	- [Beispiel](#beispiel-1)
- [Versandbestätigung](#versandbestätigung)
	- [Felder](#felder-2)
	- [Werte](#werte-2)
		- [Versanddatum](#versanddatum)
		- [Trackingnummern](#trackingnummern)
	- [Beispiel](#beispiel-2)
# Übertragung der Druckdaten

Die Auftragsdaten werden von Abihome über einen SFTP Server, im XML Format übertragen.

Auf dem Server gibt es folgende Ordnerstruktur

| Ordner    | Verwendung                            | XML Beschreibung                |
| --------- | ------------------------------------- | ------------------------------- |
| /Feedback | Rückmeldung der Druckerei             | [feedback](#rückmeldung)        |
| /Orders   | Übertragung der Auftragsdaten         | [order](#bestellung)            |
| /Shipping | Übertragung der Trackinginformationen | [shipping](#versandbestätigung) |


## Ablauf
- Abihome legt einen Auftrag in den Ordner "Orders" ab
- Die Druckerei lädt den Auftrag herunter
- Die Druckerei löscht die Auftragsdaten aus dem Ordner
- Die Druckerei hinterlegt die Rückmeldung im Ordner "Feedback"
- Die Druckerei hinterlegt die Versandinformationen im Ordner "Shipping"

# Bestellung

Bestellungen werden durch Abihome im Ordner "Orders" im XML Format hinterlegt. Die Druckerei löscht nach dem Download eines Auftrags die XML Datei. 

## Felder

Ein Auftrag enthält folgende Felder:

### ReceiverAddress

Adresse des Empfängers

| Name              | Beschreibung                                                                           |
| ----------------- | -------------------------------------------------------------------------------------- |
| Name              | Vor- und Zuname                                                                        |
| AdditionalAddress | Adresszusatz                                                                           |
| Company           | Firma                                                                                  |
| Street            | Straße und Hausnummer                                                                  |
| Zip               | Postleitzahl                                                                           |
| City              | Stadt                                                                                  |
| Phone1            | Telefonnummer                                                                          |
| Country           | Land nach [ISO-3166-1 (ALPHA-2)](https://de.wikipedia.org/wiki/ISO-3166-1-Kodierliste) |

### SenderAddress

Adresse des Absenders

| Name              | Beschreibung                                                                           |
| ----------------- | -------------------------------------------------------------------------------------- |
| Name              | Vor- und Zuname                                                                        |
| AdditionalAddress | Adresszusatz                                                                           |
| Company           | Firma                                                                                  |
| Street            | Straße und Hausnummer                                                                  |
| Zip               | Postleitzahl                                                                           |
| City              | Stadt                                                                                  |
| Phone1            | Telefonnummer                                                                          |
| Country           | Land nach [ISO-3166-1 (ALPHA-2)](https://de.wikipedia.org/wiki/ISO-3166-1-Kodierliste) |


### Order
| Name              | Beschreibung                                     | Mehrfachauswahl | Erforderlich |
| ----------------- | ------------------------------------------------ | --------------- | ------------ |
| Project           | [Projekttyp](#Project)                           |                 | ja           |
| OrderNumber       | Auftragsnummer                                   |                 | ja           |
| Kind              | [Auftragsart](###Kind)                           |                 | ja           |
| Edition           | Auflage                                          |                 | ja           |
| PageCount         | Seitenzahl gesamt                                |                 | ja           |
| PageCountColor    | Seitenzahl farbig                                |                 | ja           |
| PageCountBW       | Seitenzahl Schwarz/Weiß                          |                 | ja           |
| DeliveryDate      | [Lieferdatum](#DeliveryDate)                     |                 | ja           |
| LinkCover         | Link zum Umschlag                                |                 | ja           |
| LinkContent       | Link zum Inhalt                                  |                 | ja           |
| LinkDeliveryNote  | Link zum Lieferschein                            |                 | ja           |
| ProductionComment | Kommentar                                        |                 | nein         |
| Price             | Preis (Fließkommazahlen mit . getrennt)          |                 | ja           |
| Delivery          | [Lieferart](#Delivery)                           |                 | ja           |
| Technique         | [Druckverfahren](#Technique)                     |                 | ja           |
| Lamination        | [Kaschierung](#Lamination)                       |                 | ja           |
| Binding           | [Bindung](#Binding)                              |                 | ja           |
| Format            | [Format](#Format)                                |                 | ja           |
| PaperTypeCover    | [Papiersorte Umschlag](#PaperTypeCover)          |                 | ja           |
| PaperTypeInside   | [Papiersorte Inhalt](#PaperTypeInside)           |                 | ja           |
| ColorCover        | [Farbigkeit Umschlag](#ColorCover)               |                 | ja           |
| FinishingOutside  | [Veredelungen des Umschlags](#FinishingOutside)  | ja              | nein         |
| FinishingInside   | [Veredelungen der Innenseiten](#FinishingInside) | ja              | nein         |
| Specials          | [Extras](#Specials)                              | ja              | nein         |


## Werte

### Project
- Abizeitung 
- Premium Abizeitung 
- Skript 
- Schülerzeitung 
- B2B Broschüre 
- Flyer 
- Faltblatt 
- Sticker 
- Karten 
- Anderes

### Kind
| Name | Beschreibung   |
| ---- | -------------- |
| RZ   | Reinzeichnung  |
| KA   | Korrekturabzug |

### DeliveryDate

Das Lieferdatum wird im Format YYYY-MM-DD angegeben (z.B. 2021-11-30).

### Delivery

- Normal
- Express
- Direktfahrt
- Einzelversand

### Technique

- Offset
- Indigo
- Inkjet
- OCE
- ColorStream
- VarioPrint

### Lamination

- Cellophanierung matt
- Cellophanierung matt kratzfest
- Cellophanierung glänzend
- Cellophanierung softtouch
- Dispersionslack matt
- Dispersionslack seidenmatt
- Dispersionslack glänzend

### Binding

- SC
- HC
- SC PUR
- HC PUR
- SC HOTMELT
- HC HOTMELT
- SC Fadenheftbindung
- HC Fadenheftbindung
- HC Leinenbezug
- Wire-O
- Klammerheftbindung 2fach
- Klammerheftbindung 4fach
- Offen
- Spirale (Kunststoff)

### Format

- DIN A4 Hochformat
- DIN A4 Querformat
- DIN A5 Hochformat
- DIN A5 Querformat
- 21x21cm Quadratisch
- 24x24cm Quadratisch
- 29x29cm Quadratisch

### PaperTypeCover

- 350g Bilderdruckpapier matt
- 350g Bilderdruckpapier glänzend
- 250g Bilderdruckpapier matt
- 250g Bilderdruckpapier glänzend
- 200g Bilderdruckpapier matt
- 200g Bilderdruckpapier glänzend
- 150g Bilderdruckpapier matt
- 150g Bilderdruckpapier glänzend
- 135g Bilderdruckpapier matt
- 135g Bilderdruckpapier glänzend
- 170g Bilderdruckpapier matt
- 170g Bilderdruckpapier glänzend
- 200g Chromopapier
- Goldkarton
- Silberkarton
- Folie klar
- Folie opak
- 400g Karton

### PaperTypeInside

- 80g Offsetpapier
- 90g Offsetpapier
- 100g Bilderdruckpapier matt
- 100g Bilderdruckpapier glänzend
- 115g Bilderdruckpapier matt
- 115g Bilderdruckpapier glänzend
- 120g Offsetpapier
- 135g Bilderdruckpapier matt
- 135g Bilderdruckpapier glänzend
- 140g Bilderdruckpapier matt
- 140g vorbehandeltes Papier
- 170g Bilderdruckpapier matt
- 170g Bilderdruckpapier glänzend

### ColorCover

- 1/1c
- 1/0c
- 1/4c
- 4/0c
- 4/1c
- 4/4c
- 5/0c
- 5/1c
- 5/4c

### FinishingOutside

Bei den Veredelungen ist eine Mehrfachauswahl möglich, mehrere Optionen werden durch ein Semikolon getrennt (z.B. Stanzung;Sonderfarbe).

- Scodix Gold glänzend
- Scodix Silber glänzend
- Scodix Gold matt
- Scodix Silber matt
- Scodix Klarlack
- Scodix Gold Laser
- Scodix Silber Laser
- Heißfolienprägung Gold
- Heißfoleinprägung Silber
- Blindprägung
- Partieller UV Lack
- Stanzung
- Sonderfarbe

### FinishingInside

Bei den Veredelungen ist eine Mehrfachauswahl möglich, mehrere Optionen werden durch ein Semikolon getrennt (z.B. Stanzung;Sonderfarbe).

- Dispersionslack vollflächig matt
- Dispersionslack vollflächig seidenmatt
- Dispersionslack vollflächig glänzend
- UV-Lack vollflächig
- Perforation
- Sonderfarbe
- Heißfolienprägung Silber
- Heißfolienprägung Gold
- Stanzung

### Specials

Bei den Extras ist eine Mehrfachauswahl möglich, mehrere Optionen werden durch ein Semikolon getrennt (z.B. Leseband;Klarsichthülle A4).

- Leseband
- Fälzeln
- Kapitalband
- Klarsichthülle A5
- Klarsichthülle A4


## Beispiel
```xml
<?xml version="1.0" encoding="utf-8"?>
<Xml xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
	<ReceiverAddress>
		<Name>Max Mustermann</Name>
		<AdditionalAddress>Hintereingang</AdditionalAddress>
		<Company>Musterfirma</Company>
		<Street>Musterstraße 1</Street>
		<Zip>12345</Zip>
		<City>Musterstadt</City>
		<Phone1/>
		<Country>DE</Country>
	</ReceiverAddress>
    <SenderAddress>
		<Name></Name>
		<AdditionalAddress></AdditionalAddress>
		<Company>abihome GmbH</Company>
		<Street>Max-Keith-Str. 29</Street>
		<Zip>45136</Zip>
		<City>Essen</City>
		<Phone1/>
		<Country>DE</Country>
	</SenderAddress>
	<Order>
		<Project>Abizeitung</Project>
		<OrderNumber>AUF-17011-RZ</OrderNumber>
		<Kind>RZ</Kind>
		<Edition>134</Edition>
		<PageCount>100</PageCount>
		<PageCountColor>100</PageCountColor>
		<PageCountBW>0</PageCountBW>
		<DeliveryDate>2021-04-23</DeliveryDate>
		<LinkCover>https://test1.de/download</LinkCover>
		<LinkContent>https://test2.de/download</LinkContent>
		<LinkDeliveryNote>http://api.prodman.staging.abihome.space:8000/media/AUF-17011-RZ_81441c54cf7348e68f73b64117c83139.pdf</LinkDeliveryNote>
		<ProductionComment/>
		<Price>456.1</Price>
		<Delivery>Normal</Delivery>
		<Technique>Inkjet</Technique>
		<Lamination>Cellophanierung matt kratzfest</Lamination>
		<Binding>HC PUR</Binding>
		<Format>DIN A4 Hochformat</Format>
		<PaperTypeCover>150g Bilderdruckpapier matt</PaperTypeCover>
		<PaperTypeInside>135g Bilderdruckpapier matt</PaperTypeInside>
		<ColorCover>4/0c</ColorCover>
        <FinishingOutside>Blindprägung</FinishingOutside>
		<Specials>Fälzeln</Specials>
		<FinishingInside>Dispersionslack vollflächig matt</FinishingInside>
	</Order>
</Xml>
```



# Rückmeldung

Nachdem ein Auftrag von der Druckerei abgeholt wurde, legt die Druckerei eine Empfangsbestätigung als XML Datei im Ordner "Feedback" ab.   

## Felder

Die Rückmeldung enthält folgende Felder:


| Name        | Beschreibung               |
| ----------- | -------------------------- |
| OrderNumber | Auftragsnummer             |
| Date        | [Datum der Meldung](#Date) |
| Status      | [Auftragsstatus](#Status)  |

## Werte
### Date

Das Datum wird im Format YYYY-MM-DD angegeben.

### Status

| Name     | Beschreibung                                   |
| -------- | ---------------------------------------------- |
| ACCEPTED | Der Auftrag wurde von der Druckerei angenommen |
| REJECTED | Der Auftrag wurde von der Druckerei abgelehnt  |


## Beispiel
```xml
<?xml version="1.0" encoding="utf-8"?>
<Xml xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
	<Order>
		<OrderNumber>AUF-12560-RZ</OrderNumber>
		<Date>2019-06-11</Date>
		<Status>ACCEPTED</Status>
	</Order>
</Xml>
```



# Versandbestätigung

Nachdem ein Auftrag versandt wird, legt die Druckerei eine Versandbestätigung als XML Datei im Ordner "Shipping" ab.   

## Felder

Die Versandbestätigung enthält folgende Felder:


| Name         | Beschreibung                        |
| ------------ | ----------------------------------- |
| OrderNumber  | Auftragsnummer                      |
| ShippingDate | [Versanddatum](#Versanddatum)       |
| Carrier      | Versandunternehmen                  |
| TrackingNo   | [Trackingnummern](#Trackingnummern) |

## Werte 

### Versanddatum

Das Versanddatum wird im Format YYYY-MM-DD angegeben.

### Trackingnummern

Bei einem Versand in mehreren Paketen, werden die Trackingnummern durch ein Semikolon ( ; ) getrennt.

## Beispiel
```xml
<?xml version="1.0" encoding="utf-8"?>
<Xml xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
	<Order>
		<OrderNumber>AUF-12560-RZ</OrderNumber>
		<ShippingDate>2019-06-11</ShippingDate>
		<Carrier>DHL Standard</Carrier>
		<TrackingNo>315282148611;315282148627;315282148633;315282148649;315282148655;315282148661;315282148677;315282148683;315282148699;315282148706</TrackingNo>
	</Order>
</Xml>
```



