
Vieles zum Thema *Azure-Speicherdienst* kannte ich noch nicht, weshalb ich die gelernten Themen zusammengefasst habe.

### Azure storage accounts

Ein Speicherkonto stellt einen eindeutigen Namespace für die Azure Storage-Daten bereit, auf welche man von überall auf der Welt per HTTP oder HTTPS zugreifen kann. Die Daten in diesem Account sind sicher, hochverfügbar, langlebig und skalierbar.

Beim Erstellen eines Speicherkontos muss man zunächst den Speicherkontotyp auswählen. Der Kontotyp bestimmt, welche Speicherdienste und Redundanzoptionen und hat Auswirkungen auf die Anwendungsfälle.
Hier sind die möglichen Redundanzoptionen aufgelistet:

- Lokal redundanter Speicher (LRS)
- Georedundanter Speicher (GRS)
- Georedundanter Speicher mit Lesezugriff (RA-GRS)
- Zonenredundanter Speicher (ZRS)
- Geozonenredundanter Speicher (GZRS)
- Geozonenredundanter Speicher mit Lesezugriff (RA-GZRS)

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

Daten in einem Azure Storage-Konto werden immer dreimal in der primären Region repliziert. Azure Storage bietet mit dem *locally redundant storage* (LRS) und dem *zone-redundant storage* (ZRS) zwei Optionen für die Replikation der Daten in der primären Region an.

#### Locally redundant storage

Bei der *locally redundant storage* (LRS) werden die Daten in einem einzelnen Rechenzentrum in der *primary region* repliziert. Dies ist die kostengünstigste Redundanzoption und bietet im Vergleich zu den anderen Optionen die geringste Dauerhaftigkeit. Jedoch ist besteht grosse Gefahr, dass bei einer Naturkatastrophe und Ausfall des gesamten RZ's, die ganzen Daten inkl. Replikationen verloren gehen.

Zur Veranschaulichung noch folgendes Bild

![Locally redunancy](../ressources/locally-redundant-storage.png)

[Quelle](../4_Anhang/Quellenangabe.md#Locally-redundancy)

#### Zone-redundant storage




## Inhaltsverzeichnis

[2. Hauptteil](./README.md)

[Titelseite (Hauptinhaltsverzeichnis)](../README.md)
