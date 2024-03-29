---
title: Bereitstellung von Inhalten per HTTP/2 – Häufig gestellte Fragen (FAQ)
description: Erfahren Sie mehr über die Bereitstellung von Inhalten per HTTP/2.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
exl-id: 2da4c0b3-119e-436e-9f03-f794283e9a37
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 77%

---

# Bereitstellung von Inhalten per HTTP/2 – Häufig gestellte Fragen (FAQ){#http-delivery-of-content-faq}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Adobe freut sich, die Verfügbarkeit der HTTP/2-Bereitstellung von Inhalten bekannt zu geben. Bei der Verwendung von HTTP/2 werden Sie eine allgemeine Leistungssteigerung feststellen.

## Was ist HTTP/2? {#what-is-http}

HTTP/2 verbessert die Kommunikation zwischen Browsern und Servern, ermöglicht eine schnellere Übertragung von Informationen und verringert den Verarbeitungsaufwand.

Auf der folgenden Website werden HTTP/2 und seine Vorteile kurz und einfach beschrieben:

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
* Sie verwenden das im Adobe-Bundle enthaltene CDN (Content Delivery Network) im Rahmen Ihrer Dynamic Media Classic-Lizenz.
* Verwenden Sie eine dedizierte Domäne (d. h. `images.company.com` oder `mycompany.scene7.com`), keine generische Dynamic Media Classic-Domäne (d. h. `s7d1.scene7.com`, `s7d2.scene7.com` oder `s7d13.scene7.com`).

   Um Ihre Domänen zu finden, melden Sie sich über das [Dynamic Media Classic-Desktop-Applikation](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html?lang=de#system-requirements-dmc-app). Tippen Sie auf **[!UICONTROL Einrichtung > Anwendungseinstellungen > Allgemeine Einstellungen]**. Suchen Sie nach dem Feld **Veröffentlichungs-Server-Name**. Wenn Sie derzeit eine generische Dynamic Media-Domain verwenden, können Sie im Zuge dieser Umstellung einen Wechsel zu Ihrer eigenen benutzerdefinierten Domain beantragen.

## Was verläuft der Prozess für die Aktivierung von HTTP/2 für mein Dynamic Media Classic-Konto? {#what-is-the-process-for-enabling-http-for-my-scene-account}

1. Sie müssen [über die Admin Console einen Support-Fall erstellen](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) und die Umstellung auf HTTP/2 anfordern. Dies wird nicht automatisch für Sie erledigt.
1. Geben Sie in Ihrem Support-Fall die folgenden Informationen an:

   * Name, E-Mail-Adresse und Telefonnummer des Primärkontakts
   * Alle Domains, die auf HTTP/2 umgestellt werden sollen. Das heißt, `images.company.com` oder `mycompany.scene7.com`.

      Um Ihre Domänen zu finden, melden Sie sich über das [Dynamic Media Classic-Desktop-Applikation](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html?lang=de#system-requirements-dmc-app). Tippen Sie auf **[!UICONTROL Einrichtung > Anwendungseinstellungen > Allgemeine Einstellungen]**. Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungs-Server-Name.]**
   Klicken Sie auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Allgemeine Einstellungen]**. Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungs-Server-Name]**.

   * Vergewissern Sie sich, dass Sie sicheres HTTPS für Rich Media-Anforderungen verwenden.
   * Stellen Sie sicher, dass Sie das CDN über Adobe und nicht über eine direkte Beziehung verwenden.
   * Stellen Sie sicher, dass Sie eine dedizierte Domain verwenden. Das heißt, `images.company.com` oder `mycompany.scene7.com`, nicht eine generische Dynamic Media-Domain wie `s7d1.scene7.com`, `s7d2.scene7.com`, `s7d13.scene7.com`.

      Um Ihre Domänen zu finden, melden Sie sich über das [Dynamic Media Classic-Desktop-Applikation](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html?lang=de#system-requirements-dmc-app). Tippen Sie auf **[!UICONTROL Einrichtung > Anwendungseinstellungen > Allgemeine Einstellungen]**. Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungs-Server-Name.]** Wenn Sie derzeit eine generische Dynamic Media-Domain verwenden, können Sie im Zuge dieser Umstellung einen Wechsel zu Ihrer eigenen benutzerdefinierten Domain beantragen.
   1. Der technische Support fügt Sie entsprechend der Reihenfolge der eingegangenen Anfragen der HTTP/2-Kundenwarteschlange hinzu.
   1. Wenn Adobe für die Bearbeitung Ihrer Anfrage bereit ist, kontaktiert Sie der Support, um die Umstellung zu koordinieren und ein Zieldatum festzulegen.
   1. Nach Abschluss werden Sie benachrichtigt, wonach Sie prüfen können, ob die Umstellung auf HTTP/2 erfolgreich durchgeführt wurde.



## Wann kann ich mit der Umstellung auf HTTP/2 rechnen? {#when-can-i-expect-to-be-transitioned-over-to-http}

Anfragen werden in der Reihenfolge verarbeitet, in der sie beim technischen Support eingehen.

>[!NOTE]
>
>Es kann eine lange Vorlaufzeit geben, da beim Übergang zu HTTP/2 der Cache geleert werden muss. Es können daher nur wenige Umstellungen zugleich durchgeführt werden.

## Welche Risiken sind mit der Umstellung auf HTTP/2 verbunden? {#what-are-the-risks-with-moving-to-http}

Durch die Umstellung auf HTTP/2 wird Ihr Cache im CDN gelöscht, da eine neue CDN-Konfiguration erforderlich ist.

Der nicht zwischengespeicherte Inhalt wird direkt an die ursprünglichen Server von Adobe übertragen, bis der Cache neu aufgebaut wird. Aus diesem Grund führt Adobe nur wenige Umstellungen zugleich durch, wodurch eine akzeptable Leistung aufrechterhalten werden kann, wenn Anforderungen aus unserer Quelle abgerufen werden.

## Wie kann festgestellt werden, ob eine URL oder eine Website mit HTTP/2 aktiviert wurde?  {#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

Sie müssen eine Erweiterung zur Verwendung mit Ihrem Webbrowser herunterladen. Für Firefox und Chrome gibt es eine Erweiterung namens **[!UICONTROL HTTP/2 and SPDY Indicator]**. Da Browser HTTP/2 nur bei sicheren Verbindungen unterstützen, muss für die Verifizierung eine URL mit HTTPS aufgerufen werden. Wenn HTTP/2 unterstützt wird, wird dies durch die Erweiterung in Form eines blauen Flash-Symbols und die Beschriftung „X-Firefox-Spdy“ : „h2“ angezeigt.
