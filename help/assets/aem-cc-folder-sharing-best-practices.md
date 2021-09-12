---
title: AEM Assets-Ordner mit Creative Cloud freigeben
description: Konfiguration und Best Practices, damit Benutzer von Adobe Experience Manager Assets Asset-Ordner mit Adobe Creative Cloud-Benutzern austauschen können.
contentOwner: AG
feature: Collaboration
role: User,Admin
exl-id: 7e2adfcc-410d-4574-8f7e-39aceecfdd4b
source-git-commit: 0120fe1303aa3b7f5aa7db39eaf40ff127f2e338
workflow-type: tm+mt
source-wordcount: '1059'
ht-degree: 44%

---

# Best Practices für die Ordnerfreigabe aus AEM in Creative Cloud {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>Die Ordnerfreigabe von AEM in Creative Cloud wird nicht mehr unterstützt. Adobe empfiehlt dringend die Verwendung neuerer Funktionen wie [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/adobe-asset-link.ug.html) oder [AEM Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de). Weitere Informationen finden Sie unter [Best Practices für die AEM- und Creative Cloud-Integration](/help/assets/aem-cc-integration-best-practices.md).

Adobe Experience Manager (AEM) kann so konfiguriert werden, dass Benutzer in AEM Assets Ordner für Creative Cloud-Benutzer freigeben können, sodass sie als freigegebene Ordner im Creative Cloud Assets-Dienst verfügbar sind. Diese Funktion kann verwendet werden, um Dateien zwischen Kreativteams und AEM Assets-Benutzern auszutauschen, insbesondere wenn die kreativen Benutzer keinen Zugriff auf die AEM Assets-Instanz (d. h. keinen Zugriff auf das Unternehmensnetzwerk) haben.

Diese Art der Integration kann in beiden Fällen verwendet werden, insbesondere bei der Zusammenarbeit mit Benutzern, die keinen direkten Zugriff auf AEM Assets haben:

* Freigeben eines Satzes bestimmter Assets aus AEM Assets für Benutzer von Creative Cloud-Dateien (z. B. einen Überblick für das Kreativteam und einen Satz genehmigter Assets für das Design einer neuen Marketingaktivität)
* Empfangen von neuen Dateien von Creative Cloud-Benutzern.

>[!NOTE]
>
>Vor der Lektüre dieses Dokuments können Sie sich die allgemeinen [Best Practices zur AEM- und Creative Cloud-Integration](aem-cc-integration-best-practices.md) durchlesen, wenn Sie sich zunächst einen Überblick über dieses Thema verschaffen möchten.

## Übersicht {#overview}

Die Freigabe von Ordnern AEM Creative Cloud beruht auf der serverseitigen Freigabe von Ordnern und Dateien zwischen AEM Assets- und Creative Cloud-Konten. Kreativprofis, die das Creative Cloud-Desktop-Programm auf ihren Desktops verwenden, können die freigegebenen Ordner zusätzlich mithilfe der Adobe CreativeSync-Technologie direkt auf ihren Datenträgern verfügbar machen.

Das folgende Diagramm bietet einen Überblick über die Integration.

![chlimage_1-406](assets/chlimage_1-406.png)

Die Integration umfasst folgende Elemente:

* **Im Unternehmensnetzwerk bereitgestellter AEM Assets-** Server (Managed Services oder On-Premise): Die Ordnerfreigabe wird hier initiiert.
* **Zentraler Assets-Dienst in Adobe Marketing Cloud**: Vermittelnder Dienst zwischen AEM und Creative Cloud-Speicherdiensten. Die Verwaltung des Unternehmens, das die Integration nutzt, muss auf einem Vertrauensverhältnis zwischen dem Marketing Cloud-Unternehmen und der AEM Assets-Instanz basieren. Um für zusätzliche Sicherheit zu sorgen, wird [eine Liste von zugelassenen Creative Cloud-Mitwirkenden definiert](https://experienceleague.adobe.com/docs/core-services/interface/assets/t-admin-add-cc-user.html#assets), mit denen AEM Assets-Benutzer freigegebene Ordner gemeinsam nutzen können.
* **Creative Cloud Assets-Webdienste**  (Web-Benutzeroberfläche für Speicher- und Creative Cloud-Dateien): Hier können bestimmte Creative Cloud-Benutzer, für die ein AEM Assets-Ordner freigegeben wurde, die Einladung annehmen und den Ordner in ihrem Creative Cloud-Kontospeicher anzeigen.
* **Creative Cloud-Desktop-Programm**: (Optional) Ermöglicht den direkten Zugriff auf freigegebene Ordner/Dateien vom Desktop des kreativen Benutzers über die Synchronisierung mit dem Creative Cloud Assets-Speicher.

## Funktionen und Einschränkungen {#characteristics-and-limitations}

* **unidirektionale Übertragung von Änderungen:**  Dateiänderungen werden nur in eine Richtung übertragen - aus dem System (AEM oder Creative Cloud-Assets), in dem das Asset ursprünglich erstellt (hochgeladen) wurde. Die Integration bietet keine vollautomatische Zweiwegsynchronisierung zwischen beiden Systemen.

* **Versionierung:**

   * AEM erstellt bei Aktualisierungen nur dann Versionen eines Assets, wenn die Datei von AEM stammt und dort aktualisiert wird.
   * Creative Cloud Assets bietet eine eigene [Versionierungsfunktion](https://helpx.adobe.com/de/creative-cloud/help/versioning-faq.html), die für laufende Aktualisierungen vorgesehen ist (Aktualisierungen werden bis zu zehn Tage gespeichert).

* **Speicherplatzbeschränkungen:** Die Größe und die Menge der ausgetauschten Dateien ist durch die für kreative Benutzer  [angegebenen Asset-](https://helpx.adobe.com/de/creative-cloud/kb/file-storage-quota.html) Creative Cloud (abhängig von der Abonnementebene) und eine Beschränkung der Dateigröße auf maximal 5 GB beschränkt. Darüber hinaus wird der Speicherplatz durch das Assets-Kontingent beschränkt, die das Unternehmen im zentralen Assets-Dienst von Adobe Marketing Cloud festgelegt hat.

* **Speicherplatzanforderungen:**  Die Dateien in freigegebenen Ordnern müssen ebenfalls physisch in AEM und dann im Creative Cloud-Konto gespeichert werden, wobei eine Kopie im Marketing Cloud Assets Core Service zwischengespeichert werden muss.
* **Netzwerke und Bandbreite:** Die Dateien in freigegebenen Ordnern und alle Updates müssen über das Netzwerk zwischen den Systemen übertragen werden. Sie sollten sicherstellen, dass nur relevante Dateien und Aktualisierungen freigegeben werden.
* **Ordnertyp**: Die Freigabe von Assets-Ordnern des Typs `sling:OrderedFolder` wird nicht unterstützt. Wenn Sie einen Ordner bei seiner Erstellung in AEM Assets freigeben möchten, wählen Sie nicht die Option „Geordnet“ aus.

## Best Practices {#best-practices}

Best Practices für die Verwendung der Ordnerfreigabe von AEM in Creative Cloud:

* **Überlegungen zum Volumen:** AEM/Creative Cloud-Ordnerfreigabe sollte verwendet werden, um eine kleinere Anzahl von Dateien freizugeben, z. B. für eine bestimmte Kampagne oder Aktivität. Greifen Sie für das Freigeben größerer Mengen von Assets, z. B. aller genehmigten Assets in der Organisation, besser auf andere Methoden zurück (z. B. AEM Assets Brand Portal) oder die AEM Desktop App.
* **Vermeiden Sie die Freigabe tiefer Hierarchien:**  Die Freigabe funktioniert rekursiv und lässt keine selektive Aufhebung der Freigabe zu. Normalerweise sollten nur Ordner ohne Unterordner oder mit einer sehr einfachen Hierarchie, z. B. eine Ebene für Unterordner, für die Freigabe in Erwägung gezogen werden.
* **Separate Ordner für die unidirektionale Freigabe:** Separate Ordner sollten verwendet werden, um endgültige Assets von AEM Assets in Creative Cloud-Dateien freizugeben und für die Freigabe von kreativen Assets aus Creative Cloud-Dateien in AEM Assets. Zusammen mit einer guten Benennungskonvention für diese Ordner wird eine besser verständliche Arbeitsumgebung für AEM Assets- und Creative Cloud-Benutzer erstellt.
* **Vermeiden Sie WIP im freigegebenen Ordner:** Der freigegebene Ordner sollte nicht für laufende Arbeiten verwendet werden. Verwenden Sie einen separaten Ordner in Creative Cloud Files , um Arbeiten durchzuführen, die häufige Dateiänderungen erfordern.
* **Starten Sie neue Arbeit außerhalb des freigegebenen Ordners:** Neue Designs (Kreativdateien) sollten im separaten WIP-Ordner in Creative Cloud Files gestartet werden. Sobald sie für AEM Assets-Benutzer freigegeben werden können, sollten sie verschoben oder in den freigegebenen Ordner gespeichert werden.
* **Vereinfachung der Freigabestruktur:** Für eine besser verwaltbare Funktionsweise sollten Sie über eine Vereinfachung der Freigabestruktur nachdenken. Anstatt alle Kreativbenutzer freizugeben, sollten AEM Assets-Ordner nur für Teamvertreter wie Kreativdirektor oder Teammanager freigegeben werden. Auf diese Weise kann der Leiter des Kreativbereichs endgültige Assets erhalten, über die Arbeitsaufteilung entscheiden und dann die Designer in ihren eigenen Creative Cloud-Konten an den unfertigen Assets arbeiten lassen. Sie können Funktionen für die Zusammenarbeit mit Creative Clouden verwenden, um die Arbeit zu koordinieren, Assets, die für die Freigabe in AEM Assets bereit sind, auszuwählen und schließlich in ihren Ordner zu verschieben, der für kreative Zwecke freigegeben wurde.

Das folgende Diagramm veranschaulicht eine Beispielkonfiguration zum Erstellen neuer Designs auf der Basis bestehender endgültiger Assets von AEM Assets.

![chlimage_1-407](assets/chlimage_1-407.png)
