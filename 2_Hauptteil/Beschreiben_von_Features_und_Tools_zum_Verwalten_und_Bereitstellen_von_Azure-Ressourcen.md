## Beschreiben von Features und Tools zum Verwalten und Bereitstellen von Azure-Ressourcen

Einige beschriebene Tools kenne ich bereits, da ich mit diesen täglich arbeite. Die Tools, welche ich noch nicht kannte, werde ich wieder kurz zusammenfassen.

## Azure Arc

Mit *Azure Arc* und *Azure Resource Manager* (ARM) können Azure-Compliance und monitoring auf die Hybrid und Multi Cloud Konfigurationen erweitert werden. Somit kann z.B. Governance auf Multicloudumgebungen verteilt werden, um Firmenstandards einhalten zu können.

Mit *Azure Arc* können folgende, ausserhalb von Azure gehostete, Ressourcentypen verwalten und überwacht werden:

- Server
- Kubernetes-Cluster
- Azure-Datendienste
- SQL Server
- VMs

## Azure Resource Manager and Azure ARM templates

*Azure Resource Manager* (ARM) ist für die Bereitstellung, Verwaltung und Überwachung von *Recources* in Azure zuständig. Durch ARM wird ermöglicht, dass automatisiert *Recources* in einer konsistenten und wiederholbaren Art und Weise bereitgestellt und konfiguriert wird. Vorteile von ARM sind z.B. dass man das Bereitstellen, Verwalten und Überwachen aller Ressourcen als Gruppe, anstatt einzeln ausführen kann. Zugriffssteuerung können auf alle Dienste angewendet werden, da *RBAC* in der Verwaltungsplattform integriert ist.

### ARM templates

Mit *ARM templates* können Vorlagen für *Recources* mittels *Infractructure as Code* (IaC) erstellt werden. Dieser Code wird in Form eines JSON-Formats abgelegt. Der Code dann von *Azure templates* nochmals überprüft befor diese ausgeführt wird, damit sichergestellt wird, ob die *Recources* ordnungsgemäss erstellt und verbunden werden.

Hier werden einige Vorteile von *Azure templates* aufgelistet:

- Deklarative Syntax: Es wird bestimmt, was bereits gestellt wird, ohne aber die Programmierbefehle und Sequenz für die Bereitstellung der *Recource* kennen oder schreiben zu müssen.
- Wiederholbare Bereitstellung: Durch die Verwendung von *ARM templates* wird die Bereitstellung von *Recources* wiederholbar. Die gleiche Vorlage kann mehrmals verwendet werden, um eine konsistente Konfiguration über verschiedene Umgebungen hinweg zu erreichen. Dies erleichtert die automatisierte Bereitstellung und verringert Fehlerquelle.
- Versionskontrolle: *ARM templates* können in einem Versionskontrollsystem wie Git oder OneDrive verwaltet werden. Dadurch können Änderungen an den *templates* nachverfolgt werden. Es besteht auch die Möglichkeit, frühere Versionen der Vorlagen wiederherzustellen, falls erforderlich.



## Inhaltsverzeichnis

[2. Hauptteil](./README.md)

[Titelseite (Hauptinhaltsverzeichnis)](../README.md)
