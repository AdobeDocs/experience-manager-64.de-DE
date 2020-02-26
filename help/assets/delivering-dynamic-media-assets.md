---
title: Bereitstellen von Assets aus dynamischen Medien
seo-title: Bereitstellen von Dynamic Media Assets
description: Informationen zum Bereitstellen von Dynamic Media Assets
seo-description: Informationen zum Bereitstellen von Dynamic Media Assets
uuid: e87754a9-4c34-4658-9971-cd7ceb26523f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: ec394bd3-2fa6-4f50-b974-bc10f643ecac
translation-type: tm+mt
source-git-commit: 15d933a2e71a44e84cdcc9ae28f60c67b43bd8f4

---


# Bereitstellen von Dynamic Media Assets {#delivering-dynamic-media-assets}

Wie Sie Dynamic Media Assets (sowohl Videos als auch Bilder) bereitstellen können, ist davon abhängig, wie Ihre Website implementiert ist.

Mit Dynamic Media haben Sie mehrere Optionen:

* Wenn Ihre Website auf AEM gehostet ist, können Sie die Dynamic Media Assets direkt zu Ihrer Seite hinzufügen.
* Wenn sich Ihre Website nicht auf AEM befindet, können Sie eine der folgenden Aktionen ausführen:

   * Betten Sie Ihr Video oder Bild auf Ihrer Website ein.
   * Verknüpfen Sie URLs mit Ihrer Webanwendung. Verwenden Sie die Verknüpfung, wenn Sie einen Videoplayer als Popup- oder modales Fenster bereitstellen möchten.
   * Wenn Ihre Website dynamisch ist, können Sie [optimierte Bilder bereitstellen](responsive-site.md).

>[!NOTE]
>
>Die intelligente Bildbearbeitung arbeitet mit bestehenden Bildvorgaben und reduziert in der letzten Sekunde abhängig vom Browser oder der Geschwindigkeit der Netzverbindung die Größe der Bilddatei intelligent noch weiter. See [Smart Imaging](imaging-faq.md) for more information.

Weitere Informationen finden Sie in den folgenden Themen:

* [Hinzufügen dynamischer Medienelemente zu Webseiten](adding-dynamic-media-assets-to-pages.md)
* [Einbetten des Video- oder Bild-Viewers in eine Website](embed-code.md)
* [Aktivieren des Hotlink-Schutzes in Dynamic Media](https://helpx.adobe.com/experience-manager/6-4/assets/using/hotlink-protection.html)
* Integration digitaler nicht sichtbarer Wasserzeichen (Digimarc) in dynamische Medien (demnächst)
* [Verknüpfen von URLs mit einer Web-Anwendung](linking-urls-to-yourwebapplication.md)
* [Bereitstellen von optimierten Bildern für eine responsive Website](responsive-site.md)
* [Bereitstellung von Inhalten per HTTP/2](http2.md)
* [Ungültigmachen von Inhalten im CDN-Cache](invalidate-cdn-cached-content.md)
* [Verwenden von Regelsätzen zum Konvertieren von URLs](using-rulesets-to-transform-urls.md)

## Bereitstellung von Dynamic Media-Assets über HTTP/2 {#http-delivery-of-dynamic-media-assets}

AEM unterstützt jetzt die Bereitstellung aller Dynamic Media-Inhalte (Bilder und Videos) über HTTP/2. Das heißt, dass eine veröffentlichte URL oder ein eingebetteter Code für ein Bild oder Video verfügbar ist und in beliebige Anwendungen integriert werden kann, die gehostete Assets akzeptiert. Dieses veröffentlichte Asset wird dann über das HTTP/2-Protokoll bereitgestellt. Dieses Bereitstellungsverfahren verbessert die Kommunikation zwischen Browser und Server und verbessert die Antwort- und Ladezeiten aller Dynamic Media-Assets.

Weitere Informationen finden Sie in den [Häufig gestellten Fragen zur Bereitstellung von Inhalten über HTTP/2](/help/sites-administering/scene7-http2faq.md).
