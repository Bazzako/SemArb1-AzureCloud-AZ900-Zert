## Beschreiben der wichtigsten Architekturkomponenten von Azure

Was Microsoft Azure ist, habe ich bereits [hier](../1_Einleitung/Microsoft_Azure.md) in der der Einleitung beschrieben. Das ganze Thema *Architekturkomponenten von Azure* kannte ich noch nicht, weshalb ich die gelernten Themen hier aufliste: 

- Azure physical infrastructure
-  Regions
-  Availability Zones
-  Region pairs
-  Sovereign regions
-  Azure management infrastructure
-  Azure resources and Resource
-  subscriptions
-  management groups
-  the hierarchy of resource groups, subscriptions, and management groups

Die Fachbegriffe habe ich jetzt Englisch dokumentiert, damit ich es an der Zertifizierung einfacher habe.
 
### Azure physical infrastructure

Die physische Infrastruktur von Azure ist konzeptionell vergleichbar mit einem Unternehmensrechenzentrum. Die Ressourcen sind in Racks angeordnet und verfügen über dedizierte Energie, Kühl - und Netzwerkinfrastrukturen. Azure hat Rechenzentren auf der ganzen Welt. Auf diese einzelnen Rechenzentren haben wir aber keinen direkten Zugriff. Die Rechenzentren werden in *Azure Regions oder Azure Availability Zones* gruppiert. Diese helfen dem Konsumenten, die Resilienz und Zuverlässigkeit für kritische Workload's zu erreichen.

#### Regions

In einer *Region*, welche ein geografischer Bereich auf der Erde ist, befindet sich mindestens ein, möglicherweise jedoch mehrere, Rechenzentren. Diese sind nicht weit voneinander entfernt über ein Netzwerk mit geringer Latenz miteinander verbunden. Ressourcen werden von Azure innerhalb jeder Region intelligent zugewiesen und kontrolliert, somit wird gewährleistet, dass die Workload's gleichmässig verteilt werden.


#### Availability Zones

*Availability Zones* sind in einer *Region* physisch getrennte Rechenzentren. Jede *Availability Zones* enthält meistens 1-3 Rechenzentren, mindestens jedoch ein Rechenzentrum, die über eine eigene Stromversorgung, Kühlung und Netzwerkbetriebe verfügen. Diese sind als Isolationsgrenzen eingerichtet. Falls eine *Availability Zones* aussteigt, sind die anderen immer noch verfügbar. *Availability Zones* sind mit privaten Glasfasernetzwerke miteinander verbunden. Momentan werden *Availability Zones* nicht in allen *Regions* unterstützt.

Zur Veranschaulichung folgendes Bild:
![Availability Zone](../ressources/availability-zones.png)
[Quelle](../4_Anhang/Quellenangabe#Availability-Zones)


#### Region Pairs

Die meisten *Regions* werden mit anderen *Regions* zu einem *Region Pair* zusammengeführt. Dafür müssen die *Regions* mindestens 300km voneinander entfernt und in der gleichen Geografie (z.B. USA, Europa, Asien) liegen. Die *Region Pairs* können gewissermassen als Georedundanz genutzt werden. Im Falle einer Naturkatastrophe in einer *Region* können die replizierten Ressourcen in der anderen *Region* des *Region Pairs* als Failover automatisch weiter betrieben werden. Wichtig ist hierbei aber zu beachten, dass Azure nicht automatisch alle Azure-Dienste oder Daten repliziert. Es liegt im Interesse des Konsumenten, seine Daten und Dienste über eine regionsübergreifende replizieren *Region* zu replizieren.

Folgendes Beispielbild zeigt eine solch mögliches *Region Pair*
![Region Pairs](../ressources/region-pairs.png)
[Quelle](../4_Anhang/Quellenangabe#Region-Pairs)

#### Sovereign Region

Azure bietet noch sogenannte *Sovereign Region* oder unabhängige Regionen, welche im Gegensatz zu herkömmlichen *Regions* von der Hauptinstanz von Azure isoliert sind. Diese werden meistens von Behörden oder ähnlichem verwendet, welches aus Gesetzes gründen isoliert werden müssen.

### Azure management infrastructure

*Azure management infrastructure*,  umfasst wie der Name schon sagt, alle Azure-Ressourcen sowie Ressourcengruppen, Abonnements und Konten.

#### Azure resources and Resource


## Inhaltsverzeichnis

[2. Hauptteil](./README.md)

[Titelseite (Hauptinhaltsverzeichnis)](../README.md)
