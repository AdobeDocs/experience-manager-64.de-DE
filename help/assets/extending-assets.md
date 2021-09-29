---
title: Anpassen und Erweitern von Assets
description: Informieren Sie sich, wie Sie die Asset-Freigabe und den Asset-Editor anpassen und erweitern können, um Benutzern eine maßgeschneiderte Oberfläche und passende Funktionen zur Verfügung zu stellen.
contentOwner: AG
feature: Developer Tools
role: Developer
exl-id: 0291690b-874a-483d-901f-f02cb6d8ab28
source-git-commit: cc9b6d147a93688e5f96620d50f8fc8b002e2d0d
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 72%

---

# Anpassen und Erweitern von Assets {#customizing-and-extending-assets}

Der Asset-Editor ist der primäre Zugriffspunkt, den Benutzer einer Adobe Enterprise Manager-Website verwenden, um die digitalen Assets in Ihrem Repository zu finden, anzuzeigen und zu bearbeiten.

Als Entwickler von [!DNL Experience Manager] können Sie den Asset-Editor auf verschiedene Arten anpassen und erweitern, indem Sie Benutzern eine speziell auf sie zugeschnittene Benutzeroberfläche und eine Reihe von Funktionen präsentieren.

Die folgenden Funktionen können angepasst bzw. verbessert werden:

* [Erweitern des Asset-Editors](asseteditorx.md)
* [Erweitern der Asset-Suche](searchx.md)
* [Verarbeitung von Assets mithilfe von Medien-Handlern und Workflows](media-handlers.md)
* [Integrieren von Assets in den Aktivitäts-Stream](extending-activity-stream.md)
* [Entwicklung von Asset-Proxys](proxy.md)
* [Best Practices für das Konfigurieren von ImageMagick](best-practices-for-imagemagick.md)

## Anpassen des Erscheinungsbilds {#customizing-the-look-and-feel}

Die folgenden Aspekte des Erscheinungsbilds des Asset-Editors sind anpassbar:

* Logo: Sie können das Logo Ihrer Organisation zur Benutzeroberfläche hinzufügen.
* Farben und Schriftarten: Sie können die Farben und Schriftarten ändern, die in der Benutzeroberfläche verwendet werden.
* HTML-Code: Zur besseren Anpassung können Sie den zugrunde liegenden HTML-Code ändern, der die Benutzeroberflächen definiert.

## Anpassen von Ausgabeformaten {#customizing-renditions}

In der [!DNL Experience Manager Assets]-Terminologie ist eine Ausgabedarstellung das Formular, in dem ein Asset angezeigt wird. Im Allgemeinen kann ein Asset mehrere Ausgabeformate haben. Z. B. kann ein Farbbild in seiner Originalgröße ausgegeben, verkleinert oder verkleinert und in Graustufen konvertiert sein.

Die Ausgabeformate, in denen ein bestimmtes Asset verfügbar ist, können angepasst werden und es können neue Ausgaben erstellt haben.
