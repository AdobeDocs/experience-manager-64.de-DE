---
title: Einrichten der Website-Struktur
seo-title: Setup Website Structure
description: Einrichten von Ordnern
seo-description: Set up directories
uuid: a31edcd5-dab8-4a42-953b-1d076c2182b2
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: d18c0ece-4c4f-499c-ac94-a9aaa7f883c4
exl-id: 6d2226da-f691-4e8b-9494-a25e1c3d4b85
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 3%

---

# Einrichten der Website-Struktur {#setup-website-structure}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die folgenden Anweisungen beschreiben die Ordner, die an den folgenden Orten erstellt werden sollen, um Ihre Website einzurichten:

* `/apps/an-scf-sandbox`
Hier befinden sich benutzerdefinierte Anwendungen und Vorlagen

* `/etc/designs/an-scf-sandbox`
Hier befinden sich herunterladbare Design-Elemente

* `/content/an-scf-sandbox`
Hier befinden sich die herunterladbaren Webseiten

Der Code in diesem Tutorial setzt voraus, dass der Hauptordnername für Anwendung, Design und Inhalt identisch ist. Wenn Sie einen anderen Namen für Ihre Website wählen, ersetzen Sie immer `an-scf-sandbox` mit dem Namen, den Sie gewählt haben.

>[!NOTE]
>
>Über Namen:
>
>* Die in CRXDE angezeigten Namen sind Knotennamen, die den Pfad zu adressierbaren Inhalten bilden.
>* Knotennamen können Leerzeichen enthalten. Bei Verwendung in einem URI muss das Leerzeichen jedoch entweder als &#39;%20&#39; oder als &#39;+&#39; kodiert werden
>* Knotennamen können Bindestriche und Unterstriche enthalten, müssen jedoch kodiert werden, wenn sie in einer Java-Datei als Paketname referenziert werden. Sowohl Bindestriche als auch Unterstriche sind mit einem Unterstrich gefolgt von ihrem Unicode-Wert maskiert:
   >
   >   * Bindestrich wird zu &quot;_002d&quot;
   >   * Unterstrich wird zu &#39;_005f&#39;


## Einrichten des Anwendungsverzeichnisses (/apps) {#setup-the-application-directory-apps}

Das Verzeichnis /apps im Repository enthält den Code mit implementiert das Verhalten und Rendering der Seiten, die aus dem Verzeichnis /content bereitgestellt werden.

Der Ordner /apps ist geschützt und nicht öffentlich zugänglich wie die Ordner /content und /etc/designs.

1. Erstellen `/apps/an-scf-sandbox` Ordner.

   Verwenden **[!UICONTROL CRXDE Lite]** im Explorer-Bereich

   1. Wählen Sie die `/apps` Ordner
   1. Rechtsklick **[!UICONTROL Erstellen]**... oder ziehen Sie die **[!UICONTROL Erstellen...]** Menü
   1. Auswählen **[!UICONTROL Ordner erstellen...]** .
   1. Im **[!UICONTROL Ordner erstellen]** dialog, enter `an-scf-sandbox`
   1. Klicken Sie auf **[!UICONTROL OK]**

1. Erstellen **[!UICONTROL Komponenten]** Unterordner.

   1. Wählen Sie die `/apps/an-scf-sandbox` Ordner
   1. Klicken **[!UICONTROL Erstellen > Ordner erstellen]**
   1. Im **[!UICONTROL Ordner erstellen]** dialog, enter **[!UICONTROL Komponenten]**
   1. Klicken Sie auf **[!UICONTROL OK]**

1. Erstellen **[!UICONTROL templates]** Unterordner.

   1. Wählen Sie die `/apps/an-scf-sandbox` Ordner
   1. Klicken **[!UICONTROL Erstellen > Ordner erstellen]**
   1. Im **[!UICONTROL Ordner erstellen]** dialog, enter **[!UICONTROL templates]**
   1. Klicken Sie auf **[!UICONTROL OK]**
   1. Neu auswählen `/apps/an-scf-sandbox`
   1. Klicken Sie auf **[!UICONTROL Alle speichern]**

   Speichern Sie wie bei jedem Bearbeitungsprozess häufig. Wenn Probleme bei der Dateneingabe auftreten, kann dies entweder daran liegen, dass Ihre Anmeldung abgelaufen ist, oder Sie müssen frühere Bearbeitungen speichern.

1. Die Struktur im Explorer-Bereich der CRXDE Lite sollte jetzt etwa so aussehen:

   ![chlimage_1-44](assets/chlimage_1-44.png)

## Einrichten des Designverzeichnisses (/etc/designs) {#setup-the-design-directory-etc-designs}

Der Ordner /etc/designs enthält die Bilder, Skripte und Stylesheets, die zusammen mit dem Seiteninhalt heruntergeladen werden sollen.

1. Um das Designer-Tool in der klassischen Benutzeroberfläche zu verwenden, navigieren Sie zu [https://&lt;server>:&lt;port>/miscadmin](http://localhost:4502/miscadmin).

   Hinweis: Wenn Sie CRXDE Lite verwenden, um einen Knoten vom Typ `cq:Page`festgelegt ist, würden die Zugriffssteuerung und Replikation nicht auf Standardeinstellungen für eine Seite festgelegt.

1. Wählen Sie im Explorer-Bereich die **[!UICONTROL Designs]** Ordner und klicken Sie dann auf **[!UICONTROL Neu > Neue Seite]**.

   Geben Sie ein:

   * Titel: **Eine SCF-Sandbox**
   * Name: **an-scf-sandbox**
   * Auswählen **Design Page Template**

   Klicken Sie auf **[!UICONTROL Erstellen]**.

   ![chlimage_1-45](assets/chlimage_1-45.png)

1. Aktualisieren Sie den Explorer-Bereich, wenn der Ordner &quot;An SCF Sandbox&quot;nicht angezeigt wird.

1. Kehren Sie zur CRXDE Lite zurück (http:// localhost:4502/crx/de) und erweitern Sie /etc/designs, um den Knoten &quot;an-scf-sandbox&quot;anzuzeigen.

   Im rechten unteren Bereich von CRXDE können Sie die Registerkarte Eigenschaften , die Registerkarte Zugriffssteuerung und die Registerkarte Replikation anzeigen, um zu sehen, was mithilfe der Vorlage Design-Seite definiert wurde.

   ![chlimage_1-46](assets/chlimage_1-46.png)

## Einrichten des Inhaltsverzeichnisses (/content) {#setup-the-content-directory-content}

Das Verzeichnis /content im Repository befindet sich dort, wo sich der Website-Inhalt befindet. Die Pfade unter /content umfassen die Pfade der URL für Browseranforderungen.

*Nachher* die [Seitenvorlage](initial-app.md#createthepagetemplate) als Teil der ursprünglichen Anwendung erstellt wurde, kann der anfängliche Seiteninhalt basierend auf der Vorlage erstellt werden.... [**imetrisch**](initial-app.md)
