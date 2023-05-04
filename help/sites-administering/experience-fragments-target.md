---
title: Target-Integration mit Experience Fragments
seo-title: Target Integration with Experience Fragments
description: Target-Integration mit Experience Fragments
seo-description: Target Integration with Experience Fragments
uuid: 621f57d4-3b8d-49ea-b193-8530c8fbd74e
contentOwner: carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 6911c8e3-b12c-466e-8255-5dcd09557d35
exl-id: dbde3cb6-4132-4462-bd4c-0e4439110e2e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 31%

---

# Target-Integration mit Experience Fragments{#target-integration-with-experience-fragments}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!NOTE]
>
>Diese Funktion erfordert die Anwendung von [AEM 6.4 Service Pack 2 (6.4.2.0)](/help/release-notes/sp-release-notes.md) oder höher.

Sie können exportieren [Experience Fragments](/help/sites-authoring/experience-fragments.md), erstellt in Adobe Experience Manager (AEM), in Adobe Target. Diese können dann als Angebote in Target-Aktivitäten verwendet werden, um Erlebnisse in großem Maßstab zu testen und zu personalisieren. Auf diese Weise können Sie die Benutzerfreundlichkeit und Leistungsfähigkeit von AEM mit den leistungsstarken Funktionen der automatisierten Intelligenz (AI) und des maschinellen Lernens (ML) in Target kombinieren.

## Voraussetzungen {#prerequisites}

Verschiedene Aktionen sind erforderlich:

1. Sie müssen AEM mit Target integrieren. Siehe [Integration mit Adobe Target](/help/sites-administering/target.md) für weitere Informationen.
1. Experience Fragments werden aus der Autoreninstanz exportiert. Daher müssen Sie [Link Externalizer konfigurieren](/help/sites-developing/externalizer.md) auf der Autoreninstanz, um sicherzustellen, dass alle Links für die Veröffentlichungsinstanz externalisiert sind.

## Hinzufügen der Cloud-Konfiguration {#add-the-cloud-configuration}

Bevor Sie ein Fragment exportieren, müssen Sie die **Cloud-Konfiguration** für **Adobe Target** zum Fragment oder Ordner hinzufügen:

1. Navigieren Sie zur **Experience Fragment**-Konsole.
1. Öffnen Sie die **Seiteneigenschaften** für den entsprechenden Ordner oder das Fragment.

   >[!NOTE]
   >
   >Wenn Sie die Cloud-Konfiguration zum übergeordneten Ordner &quot;Experience Fragment&quot;hinzufügen, wird die Konfiguration von allen untergeordneten Elementen übernommen.
   >
   >Wenn Sie die Cloud-Konfiguration zum Experience Fragment selbst hinzufügen, wird die Konfiguration von allen Varianten übernommen.

1. Wählen Sie die Registerkarte **Cloud-Services** aus.

1. under **Cloud Service-Konfiguration** auswählen **Adobe Target** aus der Dropdown-Liste aus.
1. under **Adobe Target**, wählen Sie die entsprechende Konfiguration aus.

1. **Speichern und schließen**.

## Ein Experience Fragment nach Target exportieren {#exporting-an-experience-fragment-to-target}

>[!NOTE]
>
>Für Medien-Assets wie Bilder wird nur ein Verweis nach Target exportiert. Das Asset selbst bleibt in AEM Assets gespeichert und wird von der AEM Veröffentlichungsinstanz bereitgestellt.
>
>Daher muss das Experience Fragment mit allen zugehörigen Assets vor dem Export in Target veröffentlicht werden.

So exportieren Sie ein Experience Fragment von AEM nach Target (nach Angabe der Cloud-Konfiguration):

1. Navigieren Sie zur Konsole Experience Fragment .
1. Wählen Sie das Experience Fragment aus, das Sie in die Zielgruppe exportieren möchten.

   >[!NOTE]
   >
   >Es muss sich um eine Experience Fragment-Webvariante handeln.

1. Tippen/klicken **Exportieren in Adobe Target**.

   >[!NOTE]
   >
   >Wenn das Experience Fragment bereits exportiert wurde, wählen Sie **Aktualisierung in Adobe Target**.

1. Tippen/klicken **Exportieren ohne Veröffentlichung** oder **Veröffentlichen** nach Bedarf.

   >[!NOTE]
   >
   >Wenn Sie &quot;Veröffentlichen&quot;auswählen, wird das Experience Fragment sofort veröffentlicht und an Target gesendet.

1. Tippen/klicken Sie im Bestätigungsdialogfeld auf **OK**.

   Ihr Experience Fragment sollte jetzt in Target enthalten sein.

>[!NOTE]
>
>Alternativ können Sie den Export über den Seiteneditor mit vergleichbaren Befehlen im [Seiteninformationen](/help/sites-authoring/author-environment-tools.md#page-information) Menü.

## Ihre Experience Fragments in Target verwenden {#using-your-experience-fragments-in-target}

Nach dem Ausführen der zuvor genannten Aufgaben wird das Experience Fragment auf der Seite „Angebote“ in Target angezeigt. Bitte schauen Sie sich die [spezifische Target-Dokumentation](https://experiencecloud.adobe.com/resources/help/de_DE/target/target/aem-experience-fragments.html) um zu erfahren, was man dort erreichen kann.

## Löschen eines bereits nach Target exportierten Experience Fragments {#deleting-an-experience-fragment-already-exported-to-target}

Das Löschen eines Experience Fragment, das bereits in Target exportiert wurde, kann Probleme verursachen, wenn das Fragment bereits in einem Angebot in Target verwendet wird. Durch das Löschen des Fragments wird das Angebot unbrauchbar, da der Fragmentinhalt von AEM bereitgestellt wird.

So vermeiden Sie solche Situationen:

* Wenn das Experience Fragment derzeit nicht in einer Aktivität verwendet wird, ermöglicht AEM dem Benutzer das Löschen des Fragments ohne Warnmeldung.
* Wenn das Experience Fragment derzeit von einer Aktivität in Target verwendet wird, wird der AEM Benutzer durch eine Fehlermeldung über mögliche Konsequenzen des Löschens des Fragments für die Aktivität gewarnt.

   Die Fehlermeldung in AEM verhindert nicht, dass der Benutzer das Experience Fragment (erzwungen) löscht. Wenn das Experience Fragment gelöscht wurde, gilt Folgendes:

   * Das Target-Angebot mit dem AEM Experience Fragment kann unerwünschtes Verhalten zeigen

      * Das Angebot wird wahrscheinlich noch gerendert, da das Experience Fragment-HTML nach Target verschoben wurde
      * Verweise im Experience Fragment funktionieren möglicherweise nicht ordnungsgemäß, wenn referenzierte Assets auch in AEM gelöscht wurden.
   * Natürlich sind keine weiteren Änderungen am Experience Fragment möglich, da es nicht mehr in AEM vorhanden ist.
