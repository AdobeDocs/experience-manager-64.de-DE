---
title: Inhalt auf Seite Null in Designer ändern
seo-title: Changing Page Zero content in Designer
description: Wissen Sie, wie Sie die auf Seite Null einer XFA-PDF angezeigte Nachricht ändern können, wenn Sie sie in einem Nicht-Adobe PDF-Viewer anzeigen?
seo-description: Do you know how you can change the message displayed on Page Zero of an XFA PDF when viewing it in a non-Adobe PDF viewer?
uuid: 5697f203-bb24-437d-a692-bc4bc2609b88
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: f458054e-885c-4c7a-afcd-ad1e4465e0c1
feature: Adaptive Forms
exl-id: 0ae34ddd-9a8d-48df-af2d-80c3fe6abd62
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 39%

---

# Ändern des Inhalts auf Seite null im Designer {#changing-page-zero-content-in-designer}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Der Inhalt von Seite Null wird standardmäßig angezeigt, wenn ein Nicht-Adobe PDF-Viewer, z. B. der standardmäßige PDF-Viewer in Chrome oder Firefox, den Inhalt des PDF/XFA-Formulars nicht lesen kann. Nachfolgend finden Sie die standardmäßige Meldung auf Seite Null.

![defaultpage0message](assets/defaultpage0message.png)

Mit AEM Forms Feature Pack 1 von Designer können Sie die Meldung ändern, die auf Seite Null angezeigt wird. Zum Ändern der auf Seite Null angezeigten Meldung müssen Sie folgende Schritte ausführen:

1. Stellen Sie sicher, dass AEM Forms Feature Pack 1 von Designer installiert ist. Sie können die Version im Bildschirm „Info“ des Designers überprüfen.

1. Öffnen Sie das Formular, in dem der Inhalt auf Seite Null geändert werden soll.

1. Klicken Sie auf **Datei > Formulareigenschaften**.

1. Klicken Sie im Dialog Formulareigenschaften auf ![plus](assets/plus.png) (Plussymbol), um eine benutzerdefinierte Eigenschaft hinzuzufügen.

1. Angeben **_pagezerocontent** als Name der Eigenschaft.
1. Fügen Sie die neue Meldung &quot;Seite Null&quot;im Rich-Text-Format als Wert hinzu. Beispiel:

   `<body xmlns="https://www.w3.org/1999/xhtml" xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">You are seeing this message maybe because you are using a non Adobe PDF Viewer or an Old version of Adobe Reader. You can upgrade to the latest version of Adobe Reader for Windows, Mac, or Linux by visiting <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/reader_download.</p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">For more assistance with Adobe Reader visit <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/acrreader.</p></body>`

1. Speichern Sie das Formular als PDF-Datei.

1. Zeigen Sie das PDF-Formular im Browser an, um sicherzustellen, dass die Meldung aktualisiert wurde. Der obige Beispielwert wird wie folgt angezeigt:

   ![changedmessage](assets/changedmessage.png)

>[!NOTE]
>
>Die soeben erstellte benutzerdefinierte Eigenschaft wird möglicherweise nicht ordnungsgemäß im Dialogfeld &quot;Formulareigenschaften&quot;angezeigt, wenn Sie das Formular erneut öffnen. Es funktioniert jedoch einwandfrei und das Formular zeigt die aktualisierte Meldung auf Seite Null an.
