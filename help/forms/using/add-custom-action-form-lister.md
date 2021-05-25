---
title: Hinzufügen benutzerdefinierter Aktionen zu Elementen im Formularauflister
seo-title: Hinzufügen benutzerdefinierter Aktionen zu Elementen im Formularauflister
description: Formularentwickler können der Auflistung von Formularen auf der Forms Portal-Seite weitere Aktionen hinzufügen. Standardmäßig können Sie über die Formularauflistung auf das Formular zugreifen, es ausfüllen und versenden.
seo-description: Formularentwickler können der Auflistung von Formularen auf der Forms Portal-Seite weitere Aktionen hinzufügen. Standardmäßig können Sie über die Formularauflistung auf das Formular zugreifen, es ausfüllen und versenden.
uuid: 02c64f7d-f726-4a5b-a303-ec96934e9c01
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: 0e0a9b6b-fd2f-4cec-b233-500c940ee4d5
exl-id: d8f60be3-474a-4dd1-aaa5-7b6a97e1a9bd
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 100%

---

# Hinzufügen benutzerdefinierter Aktionen zu Elementen im Formularauflister  {#adding-custom-action-on-form-lister-items}

In AEM Forms können Sie eine Portalseite erstellen, in der die verfügbaren Formulare aufgelistet werden. Standardmäßig können Sie auf einer Portalseite nach Formularen suchen und sie auflisten. Sie können Formulare öffnen, um ihre Daten einzutragen und zu versenden. Bei Formularen, die auf einer Portalseite gelistet sind, stehen für den sofortigen Einsatz nur Render-Aktionen zur Verfügung. Weitere Informationen über die verfügbaren Aktionen auf einer Portalseite finden Sie unter [Erstellen einer Forms Portal-Seite](/help/forms/using/creating-form-portal-page.md).

Sie können der Portalseite auch andere Optionen hinzufügen. Diese Optionen bzw. Aktionen können angepasst werden, indem die Forms Portal-Vorlage angepasst wird.

In diesem Artikel wird erläutert, wie eine Schaltfläche erstellt wird, um die Verknüpfung eines Formulars direkt von einer Forms Portal-Seite zu senden. Für diese Anpassung muss die Vorlage für die Komponente „ Lister“ aktualisiert werden.

Der erforderliche Code, um die Aktion der Vorlage hinzuzufügen, ist nachfolgend dargestellt. Das `onclick`-Attribut im Codebeispiel enthält ein Skript, um die Verknüpfung eines Formulars per E-Mail zu senden.

```mxml
<div class="__FP_boxes-container __FP_single-color">
    <div class="boxes __FP_boxes __FP_single-color" data-repeatable="true">
  <div class="__FP_boxes-thumbnail">
            <img src ="${contextPath}${path}/jcr:content/renditions/cq5dam.thumbnail.319.319.png">
        </div>
        <h3 class="__FP_single-color" title="${name}" tabindex="0">${name}</h3>
        <p>${description}</p>
        <div class="boxes-icon-cont __FP_boxes-icon-cont">
            <div class="op-dow">
                <a href="${formUrl}" target="_blank" class="__FP_button ${htmlStyle}" title="${config-htmlLinkText}">Apply</a>
                <a class="__FP_button" title="Email a friend" href="#" onclick="javascript:window.location=&apos;mailto:?subject=Interesting information&body=I thought you might find {name} form helpful :  &apos;+window.location.protocol+window.location.host+&apos;${formUrl}&apos; ;">Email</a>
                <a href="${pdfUrl}" class="__FP_button ${pdfStyle}" title="${config-pdfLinkText}">Download</a>
            </div>
        </div>
    </div>
</div>
```

Sie können Ihrer benutzerdefinierten Vorlage ähnliche Aktionen hinzufügen. Wenn Sie eine JavaScript-Funktion definieren möchten, fügen Sie die Funktion einem Skript auf Seitenebene hinzu und verknüpfen Sie es mit dem benötigten HTML-Element. Im Beispiel oben ist der `onclick`-Ausdruck die verknüpfte Funktion.

Nachdem Sie die Änderungen an der Vorlage vorgenommen haben, enthält die Portal-Beispielseite, wie nachfolgend in der Abbildung dargestellt, eine Schaltfläche, um die Verknüpfung des Formulars per E-Mail zu senden.

![email](assets/email.png)
