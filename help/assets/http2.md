---
title: Bereitstellung von Inhalt über HTTP/2
seo-title: HTTP2 Delivery of Content
description: HTTP/2 verbessert die Kommunikation zwischen Browsern und Servern, ermöglicht eine schnellere Übertragung von Informationen und verringert den Verarbeitungsaufwand.
seo-description: HTTP/2 improves the way browsers and servers communicate, allowing for faster transfer of information while reducing the amount of needed processing power.
uuid: d9deb945-bdf5-4d6b-95c8-8bae4442e618
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: c8e145ad-f021-4043-8190-62151775e296
exl-id: 59cd9f8c-6d01-448d-bf57-bdc9fd2e381b
feature: Asset Management
role: Admin,User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 60%

---

# Bereitstellung von Inhalt über HTTP/2  {#http-delivery-of-content}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Adobe freut sich, die Bereitstellung von Inhalt über HTTP/2 zu präsentieren, die eine Verbesserung der Leistung mit sich bringt.

## Was ist HTTP/2? {#what-is-http}

HTTP/2 verbessert die Kommunikation zwischen Browsern und Servern, ermöglicht eine schnellere Übertragung von Informationen und verringert den Verarbeitungsaufwand.

Auf der folgenden Website werden HTTP/2 und die damit verbundenen Vorteile kurz und einfach beschrieben:

[https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/](https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/)

## Was sind die wichtigsten Vorteile der Umstellung auf die Bereitstellung von Inhalt über HTTP/2? {#what-are-the-key-benefits-of-moving-to-http-for-content-delivery}

Die Leistungsverbesserung variiert stark je nach Faktoren wie dem Code Ihrer Website, der Verwendung von Dynamic Media, dem Gerät, dem Bildschirm und dem Standort des Verbrauchers usw.

Von Adobe durchgeführte Prüfungen führten zu folgenden Ergebnissen:

* Bei Bildern wurde die Reaktionszeit je nach Gerät und Browser um 7–28 % verbessert. Die bedeutendste Leistungssteigerung war bei iOS-Geräten zu beobachten.
* Die Ladezeitleistung für Viewer wurde um 15 % verbessert.

Die folgende Demonstration zeigt den Unterschied zwischen Laden mit HTTP/1 und Laden mit HTTP/2:

[https://http2.akamai.com/demo](https://http2.akamai.com/demo)

## Bin ich berechtigt, auf HTTP/2 umzustellen? {#am-i-eligible-to-switch-over-to-http}

Um HTTP/2 verwenden zu können, müssen Sie die folgenden Voraussetzungen erfüllen:

* Sie verwenden sicheres HTTPS für Ihre Rich Media-Anforderungen.
* Verwenden Sie das im Adobe-Bundle enthaltene CDN (Content Delivery Network) als Teil Ihrer Dynamic Media-Lizenz.
* Sie verwenden eine dedizierte (non- company-h.assetsadobe#.com) Domain.

   Wenn Sie bereits über eine dedizierte Domäne verfügen, können Sie sich über den technischen Support anmelden.

   Wenn Sie nicht über eine dedizierte Domäne verfügen, wird Adobe Ihre Umstellung auf HTTP/2 für 2018 einplanen.

## Wie verläuft der Prozess für die Aktivierung von HTTP/2 für mein Dynamic Media-Konto? {#what-is-the-process-for-enabling-http-for-my-dynamic-media-account}

Sie müssen den Wechsel auf HTTP/2 beantragen, da er nicht automatisch erfolgt.

1. Starten Sie eine Anfrage an den technischen Support, um zu HTTP2 zu wechseln. Siehe [Zugriff auf das Support-Portal](https://helpx.adobe.com/de/experience-manager/kb/accessing-aem-support-portal.html).

   1. In der Anfrage geben Sie folgende Informationen an:

      1. Name des Hauptansprechpartners, E-Mail, Telefon.
      1. Alle Domains, die auf HTTP/2 umgestellt werden sollen.
      1. Stellen Sie sicher, dass Sie sichere HTTPS für Rich-Media-Anforderungen verwenden.
      1. Vergewissern Sie sich, dass Sie das CDN über Adobe verwenden und nicht mit einer direkten Beziehung verwaltet werden.
      1. Stellen Sie sicher, dass Sie eine dedizierte Domain verwenden. Wenn Sie Dynamic Media verwenden, verwenden Sie bereits eine dedizierte Domäne.
   1. Der technische Support fügt Sie zur HTTP/2-Kundenwarteschlange hinzu, basierend auf der Reihenfolge, in der die Anfragen eingereicht wurden.
   1. Wenn Adobe für die Bearbeitung Ihrer Anfrage bereit ist, kontaktiert Sie der Support, um die Umstellung zu koordinieren und ein Zieldatum festzulegen.
   1. Sie werden nach Abschluss benachrichtigt und können den erfolgreichen Übergang zu HTTP2 überprüfen.

      Da der Browser nicht auf diese Tatsache hinweist, muss eine Erweiterung heruntergeladen werden.

      Für Firefox und Chrome gibt es eine Erweiterung namens &quot;HTTP/2 and SPDY Indicator&quot;. Da Browser HTTP/2 nur bei sicheren Verbindungen unterstützen, muss für die Verifizierung eine URL mit https aufgerufen werden. Wenn http/2 unterstützt wird, wird dies durch die Erweiterung in Form eines blauen Flash-Symbols und der Kopfzeile &quot;X-Firefox-Spdy&quot;angezeigt: &quot;h2&quot;.


## Wann kann ich mit der Umstellung auf HTTP/2 rechnen? {#when-can-i-expect-to-be-transitioned-over-to-http}

Die Anfragen werden in der Reihenfolge ihres Eingangs beim technischen Support bearbeitet.

>[!NOTE]
>
>Es kann eine lange Vorlaufzeit geben, da beim Übergang zu HTTP/2 der Cache geleert werden muss. Es können daher nur wenige Umstellungen zugleich durchgeführt werden.

## Welche Risiken sind mit der Umstellung auf HTTP/2 verbunden? {#what-are-the-risks-with-moving-to-http}

Durch die Umstellung auf HTTP/2 wird Ihr Cache im CDN gelöscht, da eine neue CDN-Konfiguration erforderlich ist.

Der nicht zwischengespeicherte Inhalt wird direkt an die ursprünglichen Server von Adobe übertragen, bis der Cache neu aufgebaut wird. Aus diesem Grund führt Adobe nur wenige Umstellungen zugleich durch, wodurch eine akzeptable Leistung aufrechterhalten werden kann, wenn Anforderungen aus unserer Quelle abgerufen werden.

## Wie kann festgestellt werden, ob eine URL oder eine Website mit HTTP/2 aktiviert wurde? {#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

Da der Browser nicht auf diese Tatsache hinweist, muss eine Erweiterung heruntergeladen werden.

Für Firefox und Chrome gibt es eine Erweiterung namens &quot;HTTP/2 and SPDY Indicator&quot;. Da Browser HTTP/2 nur bei sicheren Verbindungen unterstützen, muss für die Verifizierung eine URL mit https aufgerufen werden. Wenn http/2 unterstützt wird, wird dies durch die Erweiterung in Form eines blauen Flash-Symbols und der Kopfzeile &quot;X-Firefox-Spdy&quot;angezeigt: &quot;h2&quot;.
