---
title: Always On-Verfügbarkeitsgruppen für SQL Server-Container
description: In diesem Artikel werden Verfügbarkeitsgruppen in SQL Server-Containern
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: fc1a0529482b9c976ca13ce3015352e2f8578fca
ms.sourcegitcommit: df21af652d0906ade8cc9ca3985a7ba5569f0db6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "47049700"
---
# <a name="always-on-availability-groups-for-sql-server-containers"></a>Always On-Verfügbarkeitsgruppen für SQL Server-Container

SQL Server-2019 unterstützt Verfügbarkeitsgruppen für in einem Kubernetes-Container. Bereitstellen von SQL Server für Verfügbarkeitsgruppen [Kubernetes-Operator](http://coreos.com/blog/introducing-operators.html) in Ihrem Kubernetes-Cluster. Der Operator packen, bereitstellen und verwalten die verfügbarkeitsgruppe in einem Cluster.

![Verfügbarkeitsgruppe im Kubernetes-Container](media/tutorial-sql-server-ag-containers-kubernetes/KubernetesCluster.png)

In der Abbildung oben hosten eine vier-Knoten-Kubernetes-Cluster eine verfügbarkeitsgruppe mit drei Replikaten. Die Lösung umfasst die folgenden Komponenten:

* Eine Kubernetes [ *Bereitstellung*](http://kubernetes.io/docs/concepts/workloads/controllers/deployment/). Die Bereitstellung umfasst auch den Operator und einer Zuordnung für die Konfiguration. Diese bieten die Container-Abbild, Software und Anweisungen zur Bereitstellung von SQL Server-Instanzen für die verfügbarkeitsgruppe erforderlich.

* Drei Knoten, die jede Hosten einer [ *StatefulSet*](http://kubernetes.io/docs/concepts/workloads/controllers/statefulset/). Die StatefulSet enthält eine [ *Pod*](http://kubernetes.io/docs/concepts/workloads/pods/pod-overview/). Jedem Pod enthält:
  * Ein SQL Server-Container mit einer Instanz von SQL Server.
  * Ein Availability Group-Agent. 

* Zwei [ *ConfigMaps* ](http://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/) im Zusammenhang mit der verfügbarkeitsgruppe. Die ConfigMaps enthalten Informationen über:
  * Die Bereitstellung für den Operator.
  * Die Verfügbarkeitsgruppe.

 * [*Persistente Volumes* ](http://kubernetes.io/docs/concepts/storage/persistent-volumes/) sind Teile des Speichers. Ein *permanenter volumeanspruch* (PVC) ist eine Anforderung für die Speicherung von einem Benutzer. Jeder Container ist ein PVC für die Speicherung von Daten- und Protokolldateien zugeordnet. In Azure Kubernetes Service (AKS), Sie [erstellen Sie einen persistenten volumeanspruch](http://docs.microsoft.com/azure/aks/azure-disks-dynamic-pv) in den Speicher automatisch bereitstellen basierend auf einer Speicherklasse.


Der Cluster darüber hinaus speichert [ *Geheimnisse* ](http://kubernetes.io/docs/concepts/configuration/secret/) für die Kennwörter, Zertifikate, Schlüssel und andere vertrauliche Informationen.

## <a name="deploy-the-availability-group-in-kubernetes"></a>Bereitstellen der verfügbarkeitsgruppe in Kubernetes

Um eine verfügbarkeitsgruppe in Kubernetes bereitzustellen:

1. Erstellen des Kubernetes-Clusters

   Erstellen Sie mindestens drei Knoten für eine verfügbarkeitsgruppe für SQL Server sowie einen Knoten für den Master.

1. Den Operator bereitstellen

1. Konfigurieren des Speichers

1. Bereitstellen der StatefulSet

   Der Operator Lauscht auf Anweisungen, um die StatefulSet bereitzustellen. Automatisch Instanzen von SQL Server auf drei separaten Knoten erstellt und konfiguriert die verfügbarkeitsgruppe mit einem externen Cluster-Manager.

1. Erstellen Sie die Datenbanken aus, und fügen Sie sie mit der verfügbarkeitsgruppe

Ausführliche Schritte finden Sie unter [konfigurieren eine SQL Server Always On-verfügbarkeitsgruppe in Kubernetes für hochverfügbarkeit](tutorial-sql-server-ag-kubernetes.md).

## <a name="sql-server-kubernetes-operator"></a>SQL Server-Kubernetes-operator

Nachdem Sie den Operator bereitgestellt haben, registriert er eine benutzerdefinierte SQL Server-Ressource. Verwenden Sie den Operator, um diese Ressource bereitzustellen.  Jede Ressource entspricht einer Instanz von SQL Server und enthält die spezifische Eigenschaften wie `sapassword` und `monitoring policy`. Der Operator analysiert die Ressource und einem Kubernetes StatefulSet bereitgestellt.

Die StatfulSet enthält:

* MSSQL-Server-container

* MSSQL-ha-Supervisor-container

Der Code für den Operator, hohe Verfügbarkeit Supervisor und SQL Server wird in ein Docker-Image namens verpackt `mcr.microsoft.com/mssql/ha`. Dieses Image enthält folgende Binärdateien:

* `mssql-operator`

    Dieser Prozess wird als eine separate Kubernetes-Bereitstellung bereitgestellt. Registriert die [benutzerdefinierten Kubernetes-Ressource](http://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/) namens `SqlServer` (sqlservers.mssql.microsoft.com). Klicken Sie dann überwacht für diese Ressourcen, die erstellt oder aktualisiert im Kubernetes-Cluster. Für jedes Ereignis, erstellt oder aktualisiert die Kubernetes-Ressourcen für die entsprechende Instanz (z. B. die StatefulSet, oder `mssql-server-k8s-init-sql` Auftrag).

* `mssql-server-k8s-health-agent`

    Dieser Webserver dient Kubernetes [Verfügbarkeitseigenschaften Prüfpunkte](http://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-probes/) zum Ermitteln der Integrität von SQL Server-Instanz. Überwacht die Integrität der lokalen SQL Server-Instanz durch den Aufruf `sp_server_diagnostics` und Vergleichen der Ergebnisse mit Ihrem für die Überwachung.

* `mssql-ha-supervisor`

   Verwaltet den ag-Zertifikat und den Endpunkt an. 

* `mssql-server-k8s-ag-agent`
  
    Dieser Prozess überwacht die Integrität eines Replikats der Verfügbarkeitsgruppe auf einer einzelnen SQL Server-Instanz und Failover ausführt.

    Er verwaltet auch die Auswahl einer übergeordneten Instanz.

* `mssql-server-k8s-init-sql`
  
    Dieser Kubernetes [Auftrag](http://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/) gilt eine Konfiguration des gewünschten Zustands auf eine SQL Server-Instanz. Jedes Mal, wenn eine SqlServer-Ressource erstellt oder aktualisiert wird, wird der Auftrag durch den Operator erstellt. Es wird sichergestellt, dass die Ziel SQL Server-Instanz, die für die benutzerdefinierte Ressource die gewünschte Konfiguration in der Ressource beschrieben.

    Z. B. wenn die folgenden Einstellungen erforderlich sind, führt es diese:
  * Aktualisieren Sie das SA-Kennwort
  * Erstellt die SQL-Anmeldung für die agents
  * Den DBM-Endpunkt erstellt

* `mssql-server-k8s-rotate-creds`
  
    Dieser Kubernetes-Auftrag implementiert die Rotieren von Anmeldeinformationen-Aufgabe. Erstellen Sie diesen Auftrag aus, um Updates für das SA-Kennwort, Anmeldekennwort für SQL-Agent, DBM Cert usw. anzufordern. Das SA-Kennwort wird als die Auftragsparameter angegeben. Die anderen sind automatisch generiert.

* `mssql-server-k8s-failover`

   Eine Kubernetes-Auftrag, der der Workflow für manuelles Failover implementiert.

### <a name="notes"></a>Hinweise

Unabhängig von der AG-Konfiguration wird der Operator immer den Supervisor hohe Verfügbarkeit bereitstellen. Wenn die SqlServer-Ressource nicht mit keiner verfügbarkeitsgruppe befinden aufgelistet wird, wird der Operator noch diese Container bereitgestellt.

Die Version für das Operator-Image ist identisch mit der Version für das SQL Server-Image.

## <a name="next-steps"></a>Nächste Schritte

> [SQL Server-Containers in Kubernetes](tutorial-sql-server-containers-kubernetes.md)