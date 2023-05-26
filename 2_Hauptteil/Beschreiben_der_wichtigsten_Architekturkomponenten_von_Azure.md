## Beschreiben der wichtigsten Architekturkomponenten von Azure

Was Microsoft Azure ist, habe ich bereits in der [hier](../../1_Einleitung/Microsoft_Azure.md) in der Einleitung beschrieben. Das ganze Thema *Architekturkomponenten von Azure* kannte ich noch nicht, weshalb ich die gelernten Themen hier aufliste: 

-  Azure regions, region pairs, and sovereign regions
-  Availability Zones
-  Azure datacenters
-  Azure resources and Resource Groups
-  subscriptions
-  management groups
-  the hierarchy of resource groups, subscriptions, and management groups

Die Fachbegriffe habe ich jetzt Englisch dokumentiert, damit ich es an der Zertifizierung einfacher habe.

### Azure regions, region pairs, and sovereign regions

#### Azure physical infrastructure

Die physische Infrastruktur von Azure ist konzeptionell vergleichbar mit einem Unternehmensrechenzentrum. Die Ressourcen sind in Racks angeordnet und verfügen über dedizierte Energie, Kühl - und Netzwerkinfrastrukturen. Azure hat Rechenzentren auf der ganzen Welt. Auf diese einzelnen Rechenzentren haben wir aber keinen direkten Zugriff. Die Rechenzentren werden in *Azure Regions oder Azure Availability Zones* gruppiert. Diese helfen dem Konsumenten, die Resilienz und Zuverlässigkeit für kritische Workload's zu erreichen.

#### Regions

In einer Region, welche ein geografischer Bereich auf der Erde ist, befindet sich mindestens ein, möglicherweise jedoch mehrere, Rechenzenter. Diese sind nicht weit voneinander entfernt über ein Netzwerk mit geringer Latenz miteinander verbunden. Ressourcen werden von Azure innerhalb jeder Region intelligent zugewiesen und kontrolliert. Somit wird gewährleistet, dass die Workload's gleichmässig verteilt werden.


#### Availability Zones


## Inhaltsverzeichnis

[2. Hauptteil](./README.md)

[Titelseite (Hauptinhaltsverzeichnis)](../README.md)
