---
title: Veröffentlichen von Dynamic Media-Assets
description: Anleitung zum Veröffentlichen von Dynamic Media-Assets einschließlich der HTTP/2-Bereitstellung dieser Assets.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: ebe30c07-1d76-4338-b301-49591f981688
feature: Asset Management
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 75%

---

# Veröffentlichen von Dynamic Media-Assets {#publishing-dynamic-media-assets}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie veröffentlichen Dynamic Media-Assets, indem Sie die Assets auswählen und auf das Symbol **[!UICONTROL Veröffentlichen]** tippen. Nachdem Dynamic Media-Assets veröffentlicht wurden, können Sie sie per URL oder Einbetten in eine Web-Seite aufnehmen.

Sie können hochgeladene Assets auch umgehend und ohne Benutzerinteraktion veröffentlichen. Siehe [Konfigurieren von Dynamic Media - Scene7-Modus](config-dms7.md).

In der **[!UICONTROL Kartenansicht]** erscheint ein kleines Globussymbol direkt unter dem Namen eines Assets, um anzugeben, dass es veröffentlicht ist. In der **[!UICONTROL Listenansicht]** gibt eine Spalte **[!UICONTROL Veröffentlicht]** an, welche Assets veröffentlicht sind.

>[!NOTE]
>
>Wenn Sie ein bereits veröffentlichtes Asset in AEM in einen anderen Ordner verschieben und anschließend aus dem neuen Speicherort erneut veröffentlichen, ist der ursprünglich veröffentlichte Asset-Speicherort weiterhin zusammen mit dem neu veröffentlichten Asset verfügbar. Das ursprünglich veröffentlichte Asset ist allerdings für AEM nicht mehr zugänglich. Daher kann dessen Veröffentlichung nicht rückgängig gemacht werden. Deshalb wird empfohlen, dass Sie die Veröffentlichung von Assets zunächst rückgängig machen, bevor Sie sie in einen anderen Ordner verschieben.

Wenn Sie Video-Assets sofort nach der Kodierung veröffentlichen möchten, achten Sie darauf, dass die Kodierung komplett abgeschlossen ist. Wenn Videos noch kodiert werden, erhalten Sie eine Systemmeldung, dass ein Videoverarbeitungs-Workflow aktiv ist. Nach Abschluss der Videokodierung sollte eine Vorschau der Videoausgabeformate möglich sein. Jetzt können Sie die Videos veröffentlichen, ohne dass Publishing-Fehler auftreten.

Siehe auch [Verknüpfen von URLs mit einer Web-Anwendung](linking-urls-to-yourwebapplication.md).

Informationen hierzu finden Sie unter [Einbetten des Video-Viewers auf einer Web-Seite.](embed-code.md)

>[!NOTE]
>
>* Assets müssen zunächst veröffentlicht werden, bevor Sie die URL verwenden können. Wenn die Assets nicht veröffentlicht werden, funktioniert das Kopieren und Einfügen der URL in einen Webbrowser nicht.
>* Bild- und Viewer-Vorgaben müssen für die Live-Bereitstellung aktiviert und veröffentlicht sein.
>


Ausführliche Informationen zum Veröffentlichen von Sets oder des Assets finden Sie unter [Veröffentlichen von Assets](managing-assets-touch-ui.md).

## Bereitstellung von Dynamic Media-Assets über HTTP/2  {#http-delivery-of-dynamic-media-assets}

AEM unterstützt jetzt die Bereitstellung aller Dynamic Media-Inhalte (Bilder und Videos) über HTTP/2. Das heißt, dass eine veröffentlichte URL oder ein eingebetteter Code für ein Bild oder Video verfügbar ist und in beliebige Programme integriert werden kann, die gehostete Assets akzeptiert. Das veröffentlichte Asset wird dann über das HTTP/2-Protokoll bereitgestellt. Diese Bereitstellungsmethode verbessert die Kommunikation von Browsern und Servern, sodass die Antwort- und Ladezeiten aller Dynamic Media-Assets verbessert werden.

Weitere Informationen finden Sie unter [Häufig gestellte Fragen zur Bereitstellung von Inhalten über HTTP/2](/help/sites-administering/scene7-http2faq.md).
