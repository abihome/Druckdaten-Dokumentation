# Print Data Transfer Documentation v. 1.0 (04/15/2021) 

([german version](readme.md))


- [Print Data Transfer Documentation v. 1.0 (04/15/2021)](#print-data-transfer-documentation-v-10-04152021)
- [Transferring the print data](#transferring-the-print-data)
	- [Workflow](#workflow)
- [Order](#order)
	- [XML Fields](#xml-fields)
		- [ReceiverAddress](#receiveraddress)
		- [SenderAddress](#senderaddress)
		- [Order](#order-1)
	- [Values](#values)
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
	- [Example](#example)
- [Feedback](#feedback)
	- [XML Fields](#xml-fields-1)
	- [Values](#values-1)
		- [Date](#date)
		- [Status](#status)
	- [Example](#example-1)
- [Shipping confirmation](#shipping-confirmation)
	- [XML Fields](#xml-fields-2)
	- [Values](#values-2)
		- [Shipping date](#shipping-date)
		- [Tracking numbers](#tracking-numbers)
	- [Example](#example-2)

# Transferring the print data

Abihome transfers the order data via SFTP in xml format.

Using the following folder structure

| Folder    | Description                          | XML Documentation                  |
| --------- | ------------------------------------ | ---------------------------------- |
| /Feedback | Printer's feedback                   | [feedback](#feedback)              |
| /Orders   | Transmission of job data             | [order](#order)                    |
| /Shipping | Transmission of shipping information | [shipping](#shipping-confirmation) |


## Workflow
- Abihome places a job in "Orders" 
- The print shop downloads the order and deletes it
- The print shop stores their feedback in "Feedback"
- The print shop stores the shipping information in"Shipping"


# Order

Orders are placed by Abihome in "Orders" as XML file.


## XML Fields

An order contains the following fields:

### ReceiverAddress


| Name              | Description                                                                                   |
| ----------------- | --------------------------------------------------------------------------------------------- |
| Name              | first- and lastname                                                                           |
| AdditionalAddress | address addition                                                                              |
| Company           | company name                                                                                  |
| Street            | street and number                                                                             |
| Zip               | zip code                                                                                      |
| City              | city                                                                                          |
| Phone1            | phone number                                                                                  |
| Country           | country using  [ISO-3166-1 (ALPHA-2)](https://en.wikipedia.org/wiki/ISO_3166-1#Current_codes) |

### SenderAddress



| Name              | Beschreibung                                                                                 |
| ----------------- | -------------------------------------------------------------------------------------------- |
| Name              | first- and lastname                                                                          |
| AdditionalAddress | address addition                                                                             |
| Company           | company name                                                                                 |
| Street            | street and number                                                                            |
| Zip               | zip code                                                                                     |
| City              | city                                                                                         |
| Phone1            | phone number                                                                                 |
| Country           | country using [ISO-3166-1 (ALPHA-2)](https://en.wikipedia.org/wiki/ISO_3166-1#Current_codes) |


### Order
| Name              | Description                            | Multiselect | required |
| ----------------- | -------------------------------------- | ----------- | -------- |
| Project           | [project type](#project)               |             | yes      |
| OrderNumber       | order Number                           |             | yes      |
| Kind              | [order type](#kind)                    |             | yes      |
| Edition           | circulation                            |             | yes      |
| PageCount         | total page count                       |             | yes      |
| PageCountColor    | colored page count                     |             | yes      |
| PageCountBW       | black/white page count                 |             | yes      |
| DeliveryDate      | [delivery Date](#deliverydate)         |             | yes      |
| LinkCover         | link to cover file                     |             | yes      |
| LinkContent       | Link to content file                   |             | yes      |
| LinkDeliveryNote  | link to delivery note file             |             | yes      |
| ProductionComment | comment                                |             | no       |
| Price             | price (float value seperated with .)   |             | yes      |
| Delivery          | [Delivery method](#delivery)           |             | yes      |
| Technique         | [Printing method](#technique)          |             | yes      |
| Lamination        | [Lamination](#lamination)              |             | yes      |
| Binding           | [Binding](#binding)                    |             | yes      |
| Format            | [Format](#format)                      |             | yes      |
| PaperTypeCover    | [Paper type cover](#papertypecover)    |             | yes      |
| PaperTypeInside   | [Paper type content](#papertypeinside) |             | yes      |
| ColorCover        | [Coloring cover](#colorcover)          |             | yes      |
| FinishingOutside  | [Cover finishing](#finishingoutside)   | yes         | no       |
| FinishingInside   | [Content finishing ](#finishinginside) | yes         | no       |
| Specials          | [Specials](#specials)                  | yes         | no       |


## Values

### Project

| Value              | Description              |
| ------------------ | ------------------------ |
| Abizeitung         | yearbook                 |
| Premium Abizeitung | yearbook premium quality |
| Skript             | Lecture notes/script     |
| Schülerzeitung     | school newspaper         |
| B2B Broschüre      | B2B Brochure             |
| Flyer              | flyer                    |
| Faltblatt          | leaflet                  |
| Sticker            | sticker                  |
| Karten             | tickets/cards            |
| Anderes            | other                    |


### Kind
| Value | Description                |
| ----- | -------------------------- |
| RZ    | final artwork/finished art |
| KA    | hard proof                 |

### DeliveryDate

The deliverydate ist formatted as DD-MM-YYYY (e.g. 2021-11-30).

### Delivery

| Value         | Description         |
| ------------- | ------------------- |
| Normal        | standard shipping   |
| Express       | express shipping    |
| Direktfahrt   | courier shipment    |
| Einzelversand | Individual shipping |

### Technique

- Offset
- Indigo
- Inkjet
- OCE
- ColorStream
- VarioPrint

### Lamination

| Value                          | Description                         |
| ------------------------------ | ----------------------------------- |
| Cellophanierung matt           | cellophaning matt                   |
| Cellophanierung matt kratzfest | cellophaning matt scratch resistant |
| Cellophanierung glänzend       | cellophaning glossy                 |
| Cellophanierung softtouch      | cellophaning softtouch              |
| Dispersionslack matt           | dispersion coating matt             |
| Dispersionslack seidenmatt     | dispersion coating satin            |
| Dispersionslack glänzend       | dispersion coating glossy           |

### Binding


| Value                    | Description              |
| ------------------------ | ------------------------ |
| SC                       | softcover                |
| HC                       | hardcover                |
| SC PUR                   | softcover PUR            |
| HC PUR                   | harcover PUR             |
| SC HOTMELT               | softcover hotmelt        |
| HC HOTMELT               | harcover hotmelt         |
| SC Fadenheftbindung      | softcover thread sewn    |
| HC Fadenheftbindung      | harcover thread sewn     |
| HC Leinenbezug           | harcover                 |
| Wire-O                   | wire-o                   |
| Klammerheftbindung 2fach | saddle stitch 2x         |
| Klammerheftbindung 4fach | saddle stitch 4x         |
| Offen                    | loose paper              |
| Spirale (Kunststoff)     | Spiral binding (plastic) |

### Format

| Value               | Description      |
| ------------------- | ---------------- |
| DIN A4 Hochformat   | DIN A4 portrait  |
| DIN A4 Querformat   | DIN A4 landscape |
| DIN A5 Hochformat   | DIN A5 portrait  |
| DIN A5 Querformat   | DIN A5 landscape |
| 21x21cm Quadratisch | 21x21cm Square   |
| 24x24cm Quadratisch | 24x24cm Square   |
| 29x29cm Quadratisch | 29x29cm Square   |

### PaperTypeCover

| Value                           | Description                    |
| ------------------------------- | ------------------------------ |
| 350g Bilderdruckpapier matt     | 350 gsm art print paper matt   |
| 350g Bilderdruckpapier glänzend | 350 gsm art print paper glossy |
| 250g Bilderdruckpapier matt     | 250 gsm art print paper matt   |
| 250g Bilderdruckpapier glänzend | 250 gsm art print paper glossy |
| 200g Bilderdruckpapier matt     | 200 gsm art print paper matt   |
| 200g Bilderdruckpapier glänzend | 200 gsm art print paper glossy |
| 150g Bilderdruckpapier matt     | 150 gsm art print paper matt   |
| 150g Bilderdruckpapier glänzend | 150 gsm art print paper glossy |
| 135g Bilderdruckpapier matt     | 135 gsm art print paper matt   |
| 135g Bilderdruckpapier glänzend | 135 gsm art print paper glossy |
| 170g Bilderdruckpapier matt     | 170 gsm art print paper matt   |
| 170g Bilderdruckpapier glänzend | 170 gsm art print paper glossy |
| 200g Chromopapier               | 200 gsm chromo paper           |
| Goldkarton                      | golden cardboard               |
| Silberkarton                    | silver cardboard               |
| Folie klar                      | foil clear                     |
| Folie opak                      | foil opaque                    |
| 400g Karton                     | 400 gsm cardboard              |

### PaperTypeInside

| Value                           | Description                    |
| ------------------------------- | ------------------------------ |
| 80g Offsetpapier                | 80 gsm offset paper            |
| 90g Offsetpapier                | 90 gsm offset paper            |
| 100g Bilderdruckpapier matt     | 100 gsm art print paper matt   |
| 100g Bilderdruckpapier glänzend | 100 gsm art print paper glossy |
| 115g Bilderdruckpapier matt     | 115 gsm art print paper matt   |
| 115g Bilderdruckpapier glänzend | 115 gsm art print paper glossy |
| 120g Offsetpapier               | 120 gsm offset paper           |
| 135g Bilderdruckpapier matt     | 135 gsm art print paper matt   |
| 135g Bilderdruckpapier glänzend | 135 gsm art print paper glossy |
| 140g Bilderdruckpapier matt     | 140 gsm art print paper matt   |
| 140g vorbehandeltes Papier      | 140 gsm pre-treated paper      |
| 170g Bilderdruckpapier matt     | 170 gsm art print paper matt   |
| 170g Bilderdruckpapier glänzend | 170 gsm art print paper glossy |

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

Multiple selection is possible for the finishes, multiple options are separated by a semicolon (e.g. Stanzung;Sonderfarbe).

| Value                    | Description              |
| ------------------------ | ------------------------ |
| Scodix Gold glänzend     | scodix gold glossy       |
| Scodix Silber glänzend   | scodix silver glossy     |
| Scodix Gold matt         | scodix gold matt         |
| Scodix Silber matt       | scodix silver matt       |
| Scodix Klarlack          | scodix clear varnish     |
| Scodix Gold Laser        | scodix gold Laser        |
| Scodix Silber Laser      | scodix silver Laser      |
| Heißfolienprägung Gold   | hot foil stamping gold   |
| Heißfoleinprägung Silber | hot foil stamping silver |
| Blindprägung             | blind embossing          |
| Partieller UV Lack       | partial UV varnish       |
| Stanzung                 | die cutting              |
| Sonderfarbe              | spot color               |

### FinishingInside

Multiple selection is possible for the finishes, multiple options are separated by a semicolon (e.g. Stanzung;Sonderfarbe).

| Value                                  | Description               |
| -------------------------------------- | ------------------------- |
| Dispersionslack vollflächig matt       | dispersion coating matt   |
| Dispersionslack vollflächig seidenmatt | dispersion coating satin  |
| Dispersionslack vollflächig glänzend   | dispersion coating glossy |
| UV-Lack vollflächig                    | UV varnish                |
| Perforation                            | perforation               |
| Sonderfarbe                            | spot color                |
| Heißfolienprägung Silber               | hot foil stamping silver  |
| Heißfolienprägung Gold                 | hot foil stamping gold    |
| Stanzung                               | die cutting               |

### Specials

Multiple selection is possible for the specials, multiple options are separated by a semicolon (e.g. Leseband;Klarsichthülle A4).

| Value             | Description          |
| ----------------- | -------------------- |
| Leseband          | ribbon/bookmark      |
| Fälzeln           | folding              |
| Kapitalband       | endband              |
| Klarsichthülle A5 | Transparent cover A5 |
| Klarsichthülle A4 | Transparent cover A4 |


## Example
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



# Feedback

After fetching the order, the print shop stores their confirmation in "feedback"

## XML Fields

An order contains the following fields:


| Name        | Description             |
| ----------- | ----------------------- |
| OrderNumber | order number            |
| Date        | [feedback date](#date)  |
| Status      | [order status](#status) |

## Values

### Date

The date ist formatted as DD-MM-YYYY (e.g. 2021-11-30).

### Status

| Value    | Description                             |
| -------- | --------------------------------------- |
| ACCEPTED | the order is accepted by the print shop |
| REJECTED | the order is rejected by the print shop |


## Example
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



# Shipping confirmation

After an order is shipped, the print shop stores a shipping confirmation in "Shipping".    

## XML Fields

The shipping confirmation contains the following fields:


| Name         | Description                           |
| ------------ | ------------------------------------- |
| OrderNumber  | order number                          |
| ShippingDate | [shipping Date](#shipping-date)       |
| Carrier      | Versandunternehmen                    |
| TrackingNo   | [Tracking numbers](#Tracking numbers) |

## Values

### Shipping date

The shipping date ist formatted as DD-MM-YYYY (e.g. 2021-11-30).

### Tracking numbers

When shipping in multiple packages, the tracking numbers are separated by a semicolon ( ; ).

## Example
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



