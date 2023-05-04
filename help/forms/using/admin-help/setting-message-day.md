---
title: Festlegen der Nachricht des Tages
seo-title: Setting the message of the day
description: Mit der Tagesmeldung können Sie eine Nachricht festlegen, die auf der Begrüßungsseite in der Workspace-Benutzeroberfläche angezeigt werden soll.
seo-description: The message of the day let you set a message to be displayed on the Welcome page in the Workspace user interface.
uuid: 9c664438-6fc0-498e-bb3f-4c6bcb9414a7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_workspace
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: c2b3a412-70c2-4257-bfb4-1430bb1f8891
exl-id: 7ddd5a4d-2b46-4408-b241-81e16cfead3c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 26%

---

# Festlegen der Nachricht des Tages {#setting-the-message-of-the-day}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können eine Nachricht festlegen, die auf der Begrüßungsseite in der Workspace-Benutzeroberfläche angezeigt wird.

Bei Bedarf können Sie die vom Adobe Flash® Player unterstützten HTML-Tags verwenden, um das Erscheinungsbild des Textes zu formatieren:

* &lt;a> Anker-Tag
* &lt;b> Fett-Tag
* &lt;br> Break-Tag
* &lt;font> Schriftart-Tag
* &lt;img> Bild-Tag
* &lt;i> Kursiv-Tag
* &lt;li> Element-Tag auflisten
* &lt;p> Absatz-Tag
* &lt;span> Span-Tag
* &lt;textformat> Textformat-Tag
* &lt;u> Tag unterstreichen

Weitere Informationen zu den unterstützten Tags finden Sie in der Definition der `htmlText`-Eigenschaft für die „TextField“-Klasse in der [Flex Language Reference](https://flex.apache.org/de/).

## Nachricht des Tages festlegen {#set-the-message-of-the-day}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Workspace&quot;> &quot;Nachricht des Tages&quot;.
1. Geben Sie im Feld &quot;Nachricht des Tages&quot;den Text ein, der auf dem Begrüßungsbildschirm angezeigt werden soll.
1. Klicken Sie auf Speichern.

>[!NOTE]
>
>Der Flex-Workspace wird für die AEM Forms-Version nicht mehr unterstützt.
