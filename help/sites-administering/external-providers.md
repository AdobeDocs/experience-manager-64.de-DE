---
title: Analyse mit externen Anbietern
seo-title: Analytics with External Providers
description: Erfahren Sie mehr über Analytics mit externen Anbietern.
seo-description: Learn about Analytics with External Providers.
uuid: bea8ec38-a190-46f9-a5fa-8d65321fdf20
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: bf8fd156-4be9-43f8-8948-cf7f91c25f1b
exl-id: 6d906c2b-c8bc-4d54-9887-8aaeb6cc83d3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 67%

---

# Analyse mit externen Anbietern{#analytics-with-external-providers}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Analysen können Ihnen wichtige und interessante Informationen darüber liefern, wie Ihre Website verwendet wird.

Verschiedene vordefinierte Konfigurationen stehen Ihnen zur Integration in den entsprechenden Dienst zur Verfügung, zum Beispiel:

* [Adobe Analytics](/help/sites-administering/adobeanalytics.md)
* [Adobe Target](/help/sites-administering/target.md)

Sie können auch Ihre eigene Instanz der **Allgemeine Analytics-Snippets** , um neue Dienstkonfigurationen zu definieren.

Die Informationen werden dann mithilfe kleiner Codefragmente erfasst, die den Webseiten hinzugefügt werden. Beispiel:

>[!CAUTION]
>
>Skripte dürfen nicht in `script`-Tags eingeschlossen werden.

```
var _gaq = _gaq || [];
_gaq.push(['_setAccount', 'UA-XXXXX-X']);
_gaq.push(['_trackPageview']);

(function() {
    var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
    ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'https://www') + '.google-analytics.com/ga.js';
    var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
})();
```

Diese Snippets ermöglichen die Erfassung von Daten und die Erstellung von Berichten. Die tatsächlichen erfassten Daten hängen vom Provider und dem tatsächlich verwendeten Codeausschnitt ab. Zu den Beispielstatistiken gehören:

* wie viele Besucher im Laufe der Zeit
* wie viele Seiten besucht wurden
* verwendete Suchbegriffe
* Landingpages

>[!CAUTION]
>
>Die Demo-Site von Geometrixx-Outdoors ist so konfiguriert, dass die in den Seiteneigenschaften bereitgestellten Attribute dem HTML-Quell-Code (direkt über dem `</html>`-End-Tag) im entsprechenden `js`-Skript angehängt werden.
>
>
>Wenn der eigene Ordner `/apps` nicht von der Standardseitenkomponente (`/libs/foundation/components/page`) übernommen wird, müssen Sie (oder Ihre Entwickler) sicherstellen, dass die entsprechenden `js`-Skripte enthalten sind, z. B. indem Sie `cq/cloudserviceconfigs/components/servicescomponents` einschließen oder einen ähnlichen Mechanismus verwenden.
>
>
>Ohne diese Komponente funktioniert keiner der Dienste (generisch, Analytics, Target usw.).

## Erstellen von neuen Diensten mit einem generischen Snippet {#creating-a-new-service-with-a-generic-snippet}

Für die Grundkonfiguration:

1. Öffnen Sie die **Tools-Konsole**.

1. Erweitern Sie im linken Bereich die Option **Cloud Service-Konfigurationen**.

1. Doppelklicken Sie auf **Generisches Analyse-Snippet**, um die Seite zu öffnen:

   ![analytics_genericoverview](assets/analytics_genericoverview.png)

1. Klicken Sie auf das Plussymbol (+), um eine neue Konfiguration mithilfe des Dialogfelds hinzuzufügen. Sie müssen mindestens einen Namen, z. B. Google Analytics, zuweisen:

   ![analytics_addconfig](assets/analytics_addconfig.png)

1. Klicken Sie auf **Erstellen**, woraufhin sofort das Snippet-Dialogfeld geöffnet wird, und fügen Sie das entsprechende Javascript-Snippet in das Feld ein.

   ![analytics_snippet](assets/analytics_snippet.png)

1. Klicken Sie zum Speichern auf **OK**.

## Verwenden des neuen Dienstes auf Seiten {#using-your-new-service-on-pages}

Nach der Erstellung der Dienstkonfiguration müssen Sie nun die erforderlichen Seiten konfigurieren, um sie zu nutzen:

1. Navigieren Sie zu der Seite.

1. Öffnen Sie die **Seiteneigenschaften** im Sidekick und wählen Sie dann die Registerkarte **Cloud-Services** aus.

1. Klicken Sie auf **Service hinzufügen** und wählen Sie dann den erforderlichen Dienst aus, zum Beispiel den Dienst **Generisches Analyse-Snippet**:

   ![analytics_selectservice](assets/analytics_selectservice.png)

1. Klicken Sie zum Speichern auf **OK**.

1. Sie werden zur Registerkarte **Cloud-Services** zurückgeleitet. Der Dienst **Generisches Analyse-Snippet** wird nun mit der Meldung `Configuration reference missing` angezeigt. Wählen Sie in der Dropdown-Liste die spezifische Dienstinstanz aus, zum Beispiel Google Analytics:

   ![analytics_selectspecificservice](assets/analytics_selectspecificservice.png)

1. Klicken Sie zum Speichern auf **OK**.

   Das Snippet kann jetzt angezeigt werden, wenn Sie die Seitenquelle für die Seite anzeigen.

   Nach Ablauf eines angemessenen Zeitraums können Sie die gesammelten Statistiken anzeigen.

   >[!NOTE]
   >
   >Wenn die Konfiguration an eine Seite mit untergeordneten Seiten angehängt wird, wird der Dienst von diesen ebenfalls übernommen.
