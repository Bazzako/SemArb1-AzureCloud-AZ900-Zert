## Grundlegendes zu Azure-Speicherdiensten

Vieles zum Thema *Azure-Speicherdienst* kannte ich noch nicht, weshalb ich die gelernten Themen zusammengefasst habe.

### Azure storage accounts

Ein Speicherkonto stellt einen eindeutigen Namespace für die Azure Storage-Daten bereit, auf welche man von überall auf der Welt per HTTP oder HTTPS zugreifen kann. Die Daten in diesem Account sind sicher, hochverfügbar, langlebig und skalierbar.

Beim Erstellen eines Speicherkontos muss man zunächst den Speicherkontotyp auswählen. Der Kontotyp bestimmt, welche Speicherdienste und Redundanzoptionen und hat Auswirkungen auf die Anwendungsfälle.
Hier sind die möglichen Redundanzoptionen aufgelistet:

- Locally redundant storage (LRS)
- Zone-redundant storage (ZRS)
- Geo-redundant storage (GRS)
- Geo-zone-redundant storage (GZRS)
- Read-access geo-redundant storage (RA-GRS)
- Read-access geo-zone-redundant storage (RA-GZRS)

Diese Tabelle beschreibt diese Optionen noch etwas mehr:

| Typ                    | Unterstützte Dienste                                                                          | Redundanzoptionen                    | Verwendung                                                                                                                                                                                                                                                                             |
| ---------------------- | --------------------------------------------------------------------------------------------- | ------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Standard „Allgemein v2 | Blob Storage (einschließlich Data Lake Storage), Queue Storage, Table Storage und Azure Files | LRS, GRS, RA-GRS, ZRS, GZRS, RA-GZRS | Standard-Speicherkontotyp für Blobs, Dateifreigaben, Warteschlangen und Tabellen. Empfohlen für die meisten Azure Storage-Szenarien. Wenn Sie Unterstützung für NFS-Dateifreigaben (Network File System) in Azure Files wünschen, verwenden Sie den Kontotyp „Premium-Dateifreigaben“. |
| Premium-Blockblobs     | Blob Storage (einschließlich Data Lake Storage)                                               | LRS, ZRS                             | Kontotyp „Premium Storage“ für Block- und Anfügeblobs. Empfohlen für Szenarien mit hohen Transaktionsraten, die kleinere Objekte verwenden oder aber eine gleichbleibend geringe Speicherlatenz erfordern.                                                                             |
| Premium-Dateifreigaben | Azure Files                                                                                   | LRS, ZRS                             | Kontotyp „Premium Storage“ nur für Dateifreigaben. Empfohlen für Unternehmens- oder Hochleistungsanwendungen. Verwenden Sie diesen Kontotyp, wenn Ihr Speicherkonto sowohl SMB- (Server Message Block) als auch NFS-Dateifreigaben unterstützen soll.                                  |
|Premium-Seitenblobs|Nur Seiten-BLOBs|LRS|Storage Premium-Kontotyp nur für Seitenblobs.|

[Quelle Tabelle: Speicherkontotypen](../4_Anhang/Quellenangabe.md#Tabelle-der-Kontospeichertypen)

### Azure storage redundancy

*Azure Storage* speichert immer mehrere Kopien der Daten, damit diese vor geplanten und ungeplanten Ereignissen geschützt sind. Diese *redundancy* ist nicht gratis. Man muss sich also überlegen, welche Redundanzoption man auswählt, um zwischen geringen Kosten und höhere Verfügbarkeit einen guten Kompromiss zu finden.

### Redundancy in the primary region

Daten in einem Azure Storage-Konto werden immer dreimal in der primären Region repliziert. Azure Storage bietet mit dem *locally redundant storage* (LRS) und dem *zone-redundant storage* (ZRS) zwei Optionen für die Replikation der Daten in der *primary region* an.

#### Locally redundant storage (LRS)

Bei der *locally redundant storage* (LRS) werden die Daten in einem einzelnen Rechenzentrum in der *primary region* repliziert. Dies ist die kostengünstigste Redundanzoption und bietet im Vergleich zu den anderen Optionen die geringste Dauerhaftigkeit, diese beträgt mindestens elf Neunen -> 99,999999999% für Azure Storage-Datenobjekte in einem Zeitraum von einem Jahr. Es besteht jedoch grosse Gefahr, dass bei einer Naturkatastrophe und Ausfall des gesamten RZ's, die ganzen Daten inkl. Replikationen verloren gehen.

Zur Veranschaulichung noch folgendes Bild

![Locally redunancy](../ressources/locally-redundant-storage.png)

[Quelle](../4_Anhang/Quellenangabe.md#Locally-redundancy)

#### Zone-redundant storage (ZRS)

Bei Availability Zone-verfügbaren Region's repliziert der *zone-redundant storage* (ZRS) die Azure Storage-Daten synchron in drei Azure Availability Zone's in der *primary region*. Der ZRS bietet somit eine Dauerhaftigkeit von mindestens zwölf Neunen -> 99,9999999999 % für Azure Storage-Datenobjekte in einem Zeitraum von einem Jahr an. Durch ZRS kann bei einem Ausfall von einer Availability Zone weiterhin mit Lese- und Schreibvoränge zugegriffen werden.

Zur Veranschaulichung noch folgendes Bild

![Zone redunancy](../ressources/zone-redundant-storage.png)

[Quelle](../4_Anhang/Quellenangabe.md#Zone-redundancy)

### Redundancy in a secondary region

Fall der Bedarf da ist, Anwendungen oder Daten mit hoher Dauerhaftigkeit ablegen zu können, bietet Azure zusätzlich noch die Möglichkeit diese in eine *secondary region* zu kopieren. Wenn ein Speicherkonto erstellt wird, wählt man erst die *primary region* aus. Die gekoppelte *secondary region* basiert auf Azure-Regionspaaren und kann nicht geändert werden.

Azure bietet zwei Möglichkeiten zum Kopieren der Anwendungen und Daten in die *secondary region*, *geo-redundant storage* (GRS) und *geo-zone-redundant storage* (GZRS).
GRS ähnelt der Nutzung des LRS in zwei Regionen, und der GZRS ähnelt der Nutzung des ZRS in der primären und des LRS in der sekundären Region.
Die Daten in der *secondary region* sind standardmässig für Lese- oder Schreibzugriff erst dann verfügbar, wenn ein Failover in die *secondary region* erfolgt. Nachdem das Failover abgeschlosse ist, wird aus der *secundary region* die *primary region*

### Geo-redundant storage (GRS)

GRS erstellt mit der Verwendung von *locally redundant storage* (LRS) drei synchrone Kopien der Daten an einem einzigen physischen Standort in der *primary region*. Anschliessend werden diese Daten dann mithilfe von LRS asynchron an einen einzelnen phyischen Standort in der *secondary region* (Region pair) kopiert. Somit kann GRS eine Dauerhaftigkeit von mindestens 16 Neunen -> 99,99999999999999 % für Azure Storage-Datenobjekte in einem Zeitraum von einem Jahr bieten.

Zur Veranschaulichung noch folgendes Bild

![Geo-redundant storage](../ressources/geo-redundant-storage.png)

[Quelle](../4_Anhang/Quellenangabe.md#Geo-redundant-storage)

### Geo-zone-redundant storage (GZRS)

Der *geo-zone-redundant storage* (GZRS) in eine Kombination aus *zone-redundant storage* (ZRS) und *geo-redundant storage (GRS)*. GZRS kombiniert somit die Hochverfügbarkeit durch die verfügbarkeitszonenübergreifende Redundanz mit dem Schutz vor regionalen Ausfällen. Somit kann GZRS eine Dauerhaftigkeit von mindestens 16 Neunen -> 99,99999999999999 % für Azure Storage-Datenobjekte in einem Zeitraum von einem Jahr bieten.

Zur Veranschaulichung noch folgendes Bild

![Geo-zone-redundant storage](../ressources/geo-zone-redundant-storage.png)

[Quelle](../4_Anhang/Quellenangabe.md#Geo-zone-redundant-storage)

### Lesezugriff auf Daten in der secundary region

Standardmässig kann man auf die Daten in der *secondary region* erst dann zugreifen, wenn diese als Failover aktiv wird. Man kann diese Lesezugriff aber schon vorher mittels *read-access geo-redundant storage* (RA-GRS) oder *read-access geo-zone-redundant storage* (RA-GZRS) freischalten. Wichtig ist aber zu beachten, dass die Daten möglicherweise nicht den gleichen Datenstand durch die *Recovery Point Objectiv* (RPO) aufweisen. Die RPO gibt den Zeitpunkt an, auf den Daten wiederhergestellt werden können. Azure Storage weist normalerweise einen RPO-Wert von weniger als 15 Minuten auf.

## Azure storage services

Azure bietet folgende Storage-Plattformen als Datendienste:

- Azure-Blobs
- Azure Files
- Azure-Queues
- Azure-Disks

### Blob storage

*Azure Blob storage* ist ein cloudbasierter Speicherdienst, der für die Speicherung grosser Mengen, unstrukturierter Daten wie Bilder, Videos, Dokumente und Backups verwendet wird. *Blobs* sind nicht auf gängige Dateiformate beschränkt.

Hier sind einige Beispiele für die Verwendung von *Azure Blob storage*:

- Speichern von Bildern oder Dokumenten direkt für einen Browser
- Speichern von Dateien für verteilten Zugriff
- Video- und Audio-Streaming
- Speichern von Daten für Sicherung und Wiederherstellung, Notfallwiederherstellung und Archivierung
- Speichern von Daten für Analysen durch einen lokalen oder von Azure gehosteten Dienst

### Zugreifen auf Blob storage

Über die Protokolle HTTP und HTTPS kann man von überall auf der Welt auf die Daten, welche sich auf dem Blobspeicher befinden, zugreifen. Benutzer oder Clientanwendungen können über die Azure Storage-REST-API, URL's, Azure PowerShell, Azure CLI oder eine Azure Storage-Clientbibliothek auf den Blob's zugreifen.

### Blob storage tiers

Azure Storage bietet verschiedene Zugriffsebenen für den Blobspeicher an, welche es ermöglichen, Objektdaten auf kostengünstige Weise zu speichern.

Azure bietet folgende *access tier's*:

- Hot: Optimiert für das Speichern von Daten, auf die häufig zugegriffen wird (z. B. Bilder für Ihre Website).
- Cool: Optimiert für Daten, auf die selten zugegriffen wird und die mindestens 30 Tage lang gespeichert werden (z. B. Rechnungen für Ihre Kunden).
- Archive: Daten optimiert, auf die selten zugegriffen wird und die bei flexiblen Latenzanforderungen mindestens 180 Tage lang gespeichert werden (z. B. langfristige Sicherungen oder Jahressicherrungen.

## Inhaltsverzeichnis

[2. Hauptteil](./README.md)

[Titelseite (Hauptinhaltsverzeichnis)](../README.md)
