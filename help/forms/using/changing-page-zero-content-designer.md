---
title: Inhalt auf Seite Null in Designer ändern
seo-title: Inhalt auf Seite Null in Designer ändern
description: Wissen Sie, wie Sie die Meldung ändern können, die auf der Seite Null einer XFA-PDF-Datei angezeigt wird, wenn diese in einem PDF-Viewer angezeigt wird, der nicht von Adobe stammt?
seo-description: Wissen Sie, wie Sie die Meldung ändern können, die auf der Seite Null einer XFA-PDF-Datei angezeigt wird, wenn diese in einem PDF-Viewer angezeigt wird, der nicht von Adobe stammt?
uuid: 5697f203-bb24-437d-a692-bc4bc2609b88
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: f458054e-885c-4c7a-afcd-ad1e4465e0c1
feature: Adaptive Formulare
exl-id: 0ae34ddd-9a8d-48df-af2d-80c3fe6abd62
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 83%

---

# Inhalt auf Seite Null in Designer ändern {#changing-page-zero-content-in-designer}

Der Inhalt von Seite Null wird standardmäßig angezeigt, wenn ein Nicht-Adobe PDF-Viewer, z. B. der standardmäßige PDF-Viewer in Chrome oder Firefox, den Inhalt des PDF/XFA-Formulars nicht lesen kann. Nachfolgend finden Sie die standardmäßige Meldung auf Seite Null.

![defaultpage0message](assets/defaultpage0message.png)

Mit AEM Forms Feature Pack 1 von Designer können Sie die auf Seite Null angezeigte Meldung ändern. Zum Ändern der auf Seite Null angezeigten Meldung müssen Sie folgende Schritte ausführen:

1. Stellen Sie sicher, dass AEM Forms Feature Pack 1 von Designer auf Ihrem Computer installiert ist. Sie können die Version im Bildschirm „Info“ des Designers überprüfen.

1. Öffnen Sie das Formular, in dem der Inhalt der Seite Null geändert werden soll.

1. Klicken Sie auf **„Datei“ > „Formulareigenschaften“.**

1. Klicken Sie im Dialogfeld &quot;Formulareigenschaften&quot;auf ![plus](assets/plus.png) (Plus-Symbol), um eine benutzerdefinierte Eigenschaft hinzuzufügen.

1. Legen Sie **_pagezerocontent** als den Namen der Eigenschaft fest.
1. Fügen Sie die Meldung auf Seite Null als Wert im Rich Text-Format hinzu. Beispiel:

   `<body xmlns="https://www.w3.org/1999/xhtml" xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">You are seeing this message maybe because you are using a non Adobe PDF Viewer or an Old version of Adobe Reader. You can upgrade to the latest version of Adobe Reader for Windows, Mac, or Linux by visiting <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/reader_download.</p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">For more assistance with Adobe Reader visit <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/acrreader.</p></body>`

1. Speichern Sie das Formular als PDF-Datei.

1. Zeigen Sie das PDF-Formular im Browser an, um sicherzustellen, dass die Meldung aktualisiert wurde. Der obige Beispielwert wird wie folgt angezeigt:

   ![changeMessage](assets/changedmessage.png)

>[!NOTE]
>
>Die gerade von Ihnen erstellte benutzerdefinierte Eigenschaft wird möglicherweise nicht korrekt im Dialogfenster „Formulareigenschaften“ angezeigt, wenn Sie das Formular erneut öffnen. Sie funktioniert jedoch problemlos und das Formular zeigt die aktualisierte Meldung auf Seite Null an.
