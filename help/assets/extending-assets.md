---
title: Anpassen und Erweitern von Assets
description: Informieren Sie sich, wie Sie die Asset-Freigabe und den Asset-Editor anpassen und erweitern können, um Benutzern eine maßgeschneiderte Oberfläche und passende Funktionen zur Verfügung zu stellen.
contentOwner: AG
feature: Developer Tools
role: Developer
exl-id: 0291690b-874a-483d-901f-f02cb6d8ab28
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 45%

---

# Anpassen und Erweitern von Assets {#customizing-and-extending-assets}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Der Asset-Editor ist der primäre Zugangspunkt, den Benutzer einer Adobe Enterprise Manager-Website verwenden, um die digitalen Assets in Ihrem Repository zu suchen, anzuzeigen und zu bearbeiten.

Als [!DNL Experience Manager]-Entwickler können Sie den Asset-Editor auf mehrere Arten anpassen und erweitern und Benutzern eine maßgeschneiderte Oberfläche und passende Funktionen zur Verfügung stellen.

Die folgenden Funktionen können angepasst bzw. verbessert werden:

* [Erweitern des Asset-Editors](asseteditorx.md)
* [Erweitern der Asset-Suche](searchx.md)
* [Verarbeitung von Assets mithilfe von Medien-Handlern und Workflows](media-handlers.md)
* [Integrieren von Assets in den Aktivitäts-Stream](extending-activity-stream.md)
* [Asset-Proxy-Entwicklung](proxy.md)
* [Best Practices für die Konfiguration von ImageMagick](best-practices-for-imagemagick.md)

## Anpassen des Erscheinungsbilds {#customizing-the-look-and-feel}

Die folgenden Aspekte des Erscheinungsbilds des Asset-Editors sind anpassbar:

* Logo: Sie können das Logo Ihrer eigenen Organisation zur Benutzeroberfläche hinzufügen.
* Farben und Schriftarten: Sie können die in der Benutzeroberfläche verwendeten Farben und Schriftarten ändern.
* HTML-Code: Für eine gründlichere Anpassung können Sie den zugrunde liegenden HTML-Code ändern, der die Schnittstellen definiert.

## Anpassen von Ausgabedarstellungen {#customizing-renditions}

In der [!DNL Experience Manager Assets]-Terminologie ist ein Ausgabeformat die Form, in der ein Asset dargestellt wird. Im Allgemeinen kann ein bestimmtes Asset mehrere Ausgabedarstellungen aufweisen. Beispielsweise kann ein Vollfarbbild eine Darstellung in der Originalgröße aufweisen, eine andere in einer herunterskalierten Größe und eine andere, die sowohl herunterskaliert als auch in Graustufen konvertiert wird.

Die Ausgabedarstellungen, in denen ein bestimmtes Asset verfügbar ist, können angepasst und neue Ausgabedarstellungen erstellt werden.
