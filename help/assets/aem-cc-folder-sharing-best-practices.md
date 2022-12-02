---
title: Experience Manager Assets-Ordner mit Creative Cloud freigeben
description: Konfiguration und Best Practices, damit Benutzer von Adobe Experience Manager Assets Asset-Ordner mit Adobe Creative Cloud-Benutzern austauschen können.
contentOwner: AG
feature: Collaboration
role: User,Admin
exl-id: 7e2adfcc-410d-4574-8f7e-39aceecfdd4b
source-git-commit: 1679bbab6390808a1988cb6fe9b7692c3db31ae4
workflow-type: tm+mt
source-wordcount: '1078'
ht-degree: 31%

---

# [!DNL Experience Manager] nach [!DNL Creative Cloud] Best Practices für die Ordnerfreigabe {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>Die Funktion &quot;Experience Manager zur Ordnerfreigabe in Creative Cloud&quot;wird nicht mehr unterstützt. Adobe empfiehlt dringend die Verwendung neuerer Funktionen wie [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/adobe-asset-link.ug.html) oder das [Experience Manager-Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de). Weitere Informationen finden Sie unter [Best Practices für die Integration von Experience Manager und Creative Cloud](/help/assets/aem-cc-integration-best-practices.md).

Adobe Experience Manager kann so konfiguriert werden, dass Benutzer in Experience Manager Assets Ordner für Creative Cloud-Benutzer freigeben können, sodass sie als freigegebene Ordner im Creative Cloud Assets-Dienst verfügbar sind. Die Funktion kann zum Austausch von Dateien zwischen Kreativ-Teams und Experience Manager Assets-Benutzern verwendet werden, insbesondere wenn kreative Benutzer keinen Zugriff auf die Experience Manager Assets-Instanz haben (sie befinden sich nicht im Unternehmensnetzwerk).

Diese Art der Integration kann in beiden Anwendungsfällen verwendet werden, insbesondere bei der Arbeit mit Benutzern, die keinen direkten Zugriff auf Experience Manager Assets haben:

* Freigeben einer Reihe bestimmter Assets aus Experience Manager Assets für Benutzer von Creative Cloud-Dateien (z. B. eine Kreativbeschreibung und eine Reihe genehmigter Assets für Designarbeiten für eine neue Marketingaktivität)
* Empfangen von neuen Dateien von Creative Cloud-Benutzern.

>[!NOTE]
>
>Bevor Sie dieses Dokument lesen, können Sie die [Best Practices für die Integration von Experience Managern und Creative Clouden](aem-cc-integration-best-practices.md) für eine allgemeine Übersicht über das Thema.

## Übersicht {#overview}

Die Ordnerfreigabe von Experience Managern in Creative Clouden beruht auf der serverseitigen Freigabe von Ordnern und Dateien zwischen Experience Manager Assets- und Creative Cloud-Konten. Kreativprofis, die das Creative Cloud-Desktop-Programm auf ihren Desktops verwenden, können die freigegebenen Ordner zusätzlich mithilfe der Adobe CreativeSync-Technologie direkt auf ihren Datenträgern verfügbar machen.

Das folgende Diagramm bietet einen Überblick über die Integration.

![chlimage_1-406](assets/chlimage_1-406.png)

Die Integration umfasst folgende Elemente:

* **[!DNL Assets]server** im Unternehmensnetzwerk (Managed Services oder On-Premise) bereitgestellt werden: Die Ordnerfreigabe wird hier initiiert.
* **Adobe Marketing Cloud Assets Core Service**: fungiert als Vermittler zwischen Experience Manager- und Creative Cloud-Speicherdiensten. Der Administrator des Unternehmens, das die Integration verwendet, muss eine Vertrauensbeziehung zwischen der Marketing Cloud-Organisation und der Experience Manager Assets-Instanz herstellen. Um für zusätzliche Sicherheit zu sorgen, wird [eine Liste von zugelassenen Creative Cloud-Mitwirkenden definiert](https://experienceleague.adobe.com/docs/core-services/interface/assets/t-admin-add-cc-user.html?lang=de#Assets), mit denen  Assets-Benutzer freigegebene Ordner gemeinsam nutzen können.
* **Creative Cloud Assets-Webdienste** (Web-Benutzeroberfläche für Speicher- und Creative Cloud-Dateien): Hier können bestimmte Creative Cloud-Benutzer, für die ein Assets-Ordner freigegeben wurde, die Einladung annehmen und den Ordner in ihrem Creative Cloud-Kontospeicher anzeigen.
* **Creative Cloud-Desktop-Applikation**: (Optional) Ermöglicht den direkten Zugriff auf freigegebene Ordner/Dateien vom Desktop des kreativen Benutzers über die Synchronisierung mit dem Creative Cloud Assets-Speicher.

## Funktionen und Einschränkungen {#characteristics-and-limitations}

* **Einwegübertragung von Änderungen:** Dateiänderungen werden nur in eine Richtung übertragen - aus dem System (Experience Manager- oder Creative Cloud-Assets), in dem das Asset ursprünglich erstellt (hochgeladen) wurde. Die Integration bietet keine vollautomatische Zweiwegsynchronisierung zwischen beiden Systemen.

* **Versionierung:**

   * Experience Manager erstellt bei Aktualisierungen nur Versionen eines Assets, wenn die Datei aus Experience Manager stammt und dort aktualisiert wird.
   * Creative Cloud Assets bietet eine eigene [Versionierungsfunktion](https://helpx.adobe.com/de/creative-cloud/help/versioning-faq.html), die für laufende Aktualisierungen vorgesehen ist (Aktualisierungen werden bis zu zehn Tage gespeichert).

* **Speicherplatzbeschränkungen:** Die Größe und Menge der ausgetauschten Dateien ist für Kreativprofis (je nach Stufe des Abonnements) durch die [Creative Cloud Assets-Quote](https://helpx.adobe.com/de/creative-cloud/kb/file-storage-quota.html) und eine Beschränkung der Dateigröße auf maximal 5 GB beschränkt. Darüber hinaus wird der Speicherplatz durch das Assets-Kontingent beschränkt, die das Unternehmen im zentralen Assets-Dienst von Adobe Marketing Cloud festgelegt hat.

* **Raumbedarf:** Die Dateien in freigegebenen Ordnern müssen auch physisch in Experience Manager und dann im Creative Cloud-Konto mit einer zwischengespeicherten Kopie im Marketing Cloud Assets Core Service gespeichert werden.
* **Netzwerk und Bandbreite:** Die Dateien in freigegebenen Ordnern und alle Aktualisierungen müssen über das Netzwerk zwischen den Systemen transportiert werden. Sie sollten sicherstellen, dass nur relevante Dateien und Aktualisierungen freigegeben werden.
* **Ordnertyp**: Die Freigabe von Assets-Ordnern des Typs `sling:OrderedFolder` wird nicht unterstützt. Wenn Sie einen Ordner beim Erstellen in Experience Manager Assets freigeben möchten, wählen Sie nicht die Option &quot;Geordnet&quot;aus.

## Best Practices {#best-practices}

Best Practices zur Nutzung der Ordnerfreigabe von Experience Managern in Creative Clouden:

* **Überlegungen zum Volumen:** Experience Manager und Creative Cloud-Ordnerfreigabe sollten verwendet werden, um eine kleinere Anzahl von  freizugeben, z. B. für eine bestimmte Kampagne oder Aktivität. Verwenden Sie andere Verteilungsmethoden (z. B. Experience Manager Assets Brand Portal) oder das Experience Manager-Desktop-Programm, um größere Asset-Sets wie alle genehmigten Assets in der Organisation freizugeben.
* **Vermeiden Sie die Freigabe tiefer Hierarchien:** Die Freigabe erfolgt rekursiv und lässt keine selektive Aufhebung der Freigabe zu. Normalerweise sollten nur Ordner ohne Unterordner oder mit einer sehr einfachen Hierarchie, z. B. eine Ebene für Unterordner, für die Freigabe in Erwägung gezogen werden.
* **Separate Ordner für die unidirektionale Freigabe:** Separate Ordner sollten verwendet werden, um endgültige Assets von Experience Manager Assets in Creative Cloud-Dateien freizugeben und um kreative Assets wieder von Creative Cloud-Dateien in freizugeben. [!DNL Assets]. Zusammen mit einer guten Benennungskonvention für diese Ordner wird eine besser verständliche Arbeitsumgebung für Experience Manager Assets- und Creative Cloud-Benutzer erstellt.
* **Vermeidung von laufenden Arbeiten in einem freigegebenen Ordner:** Freigegebene Ordner sollten nicht für laufende Arbeiten verwendet werden. Verwenden Sie einen separaten Ordner in Creative Cloud Files, um Arbeiten zu erledigen, die häufige Änderungen an der Datei erfordern.
* **Starten Sie neue Arbeit außerhalb des freigegebenen Ordners:** Neue Designs (Kreativdateien) sollten im separaten WIP-Ordner in Creative Cloud Files gestartet werden. Sobald sie für Experience Manager Assets-Benutzer freigegeben werden können, sollten sie verschoben oder im freigegebenen Ordner gespeichert werden.
* **Vereinfachung der Freigabestruktur:** Zur besseren Verwaltbarkeit der Konfiguration sollten Sie die Freigabestruktur möglichst einfach gestalten. Anstatt alle Kreativbenutzer freizugeben, sollten Experience Manager Assets-Ordner nur für Teamvertreter wie Kreativdirektor oder Teammanager freigegeben werden. Auf diese Weise kann der Leiter des Kreativbereichs endgültige Assets erhalten, über die Arbeitsaufteilung entscheiden und dann die Designer in ihren eigenen Creative Cloud-Konten an den unfertigen Assets arbeiten lassen. Sie können Funktionen für die Zusammenarbeit mit Creative Clouden verwenden, um die Arbeit zu koordinieren, Assets, die für die Freigabe in Experience Manager Assets bereit sind, auszuwählen und schließlich in ihren Ordner zu verschieben, der für kreative Zwecke freigegeben wurde.

Das folgende Diagramm zeigt eine Beispielkonfiguration zum Erstellen neuer Designs basierend auf vorhandenen endgültigen Assets aus Experience Manager Assets.

![chlimage_1-407](assets/chlimage_1-407.png)
