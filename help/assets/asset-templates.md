---
title: Asset-Vorlagen
description: Informationen zu Asset-Vorlagen in [!DNL Experience Manager] Assets und Verwendung von Asset-Vorlagen zur Erstellung von Marketingmaterial.
uuid: 7ba87c1d-70cd-4b89-86f3-971b93885f1e
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 340b62f7-2405-4d2d-846d-2c444d6cc77b
feature: Asset Management,Developer Tools
role: User
exl-id: 9b4f16e6-dd91-4179-9629-576d801fcf43
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1610'
ht-degree: 32%

---

# Asset-Vorlagen {#asset-templates}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Bei Asset-Vorlagen handelt es sich um eine spezielle Klasse von Assets, die das schnelle Wiederverwenden von visuell reichhaltigen Inhalten für digitale Medien und Print-Medien ermöglichen. Eine Asset-Vorlage enthält zwei Teile: den unveränderlichen Messaging-Abschnitt und den bearbeitbaren Abschnitt.

Der unveränderliche Messaging-Abschnitt kann proprietären Inhalt enthalten, z. B. das Markenlogo und Copyright-Informationen, die nicht bearbeitet werden können. Der bearbeitbare Abschnitt kann visuelle Inhalte und Textinhalte in Feldern enthalten, die bearbeitet werden können, um das Messaging anzupassen.

Die Flexibilität, begrenzte Änderungen vorzunehmen und gleichzeitig globale Beschilderungen zu sichern, macht Asset-Vorlagen zu idealen Bausteinen für die schnelle Anpassung und Verteilung von Inhalten als Inhaltsartefakte für verschiedene Funktionen. Die Neuverwendung von Inhalten trägt dazu bei, die Kosten für die Verwaltung von Druck- und digitalen Kanälen zu senken und ganzheitliche und konsistente Erlebnisse über diese Kanäle hinweg bereitzustellen.

Marketer können Vorlagen in [!DNL Experience Manager] Assets und die Verwendung einer einzelnen Basisvorlage, um mühelos mehrere personalisierte Druckerlebnisse zu erstellen. Sie können verschiedene Arten von Marketingmaterial erstellen, z. B. Broschüren, Flyer, Postkarten, Visitenkarten usw., um Kunden Ihre Marketingbotschaft eindeutig und klar zu vermitteln. Sie können auch mehrseitige Druckausgaben aus vorhandenen oder neuen Druckausgaben zusammenstellen. Vor allem können Sie gleichzeitig digitale und gedruckte Erlebnisse bereitstellen, um den Benutzern ein konsistentes, integriertes Erlebnis zu bieten.

Während Asset-Vorlagen hauptsächlich InDesign-Dateien sind, ist die Kompetenz im InDesign kein Hindernis für die Erstellung von Sternartefakten. Sie müssen die Felder Ihrer InDesign-Vorlage nicht den Produktfeldern zuordnen, die Sie andernfalls beim Erstellen von Katalogen benötigen. Sie können die Vorlagen im WYSIWYG-Modus direkt auf der Web-Benutzeroberfläche bearbeiten. Damit InDesign Ihre Bearbeitungsänderungen jedoch verarbeiten kann, müssen Sie zunächst [!DNL Experience Manager] Assets zur Integration mit dem InDesign-Server.

Die Möglichkeit, InDesign-Vorlagen über die Web-Oberfläche zu bearbeiten, trägt dazu bei, die Zusammenarbeit zwischen Kreativ- und Marketingmitarbeitern zu verbessern und gleichzeitig die Markteinführungszeiten für lokale Werbemaßnahmen zu verkürzen.

Asset-Vorlagen bieten folgende Möglichkeiten:

* Ändern von bearbeitbaren Vorlagenfeldern über die Web-Benutzeroberfläche
* Steuern der grundlegenden Textformatierung, z. B. Schriftgröße, -stil und -typ auf Tag-Ebene
* Ändern von Bildern in der Vorlage per Inhaltsauswahl
* Anzeigen von Vorlagenbearbeitungen in der Vorschau
* Zusammenführen mehrerer Vorlagendateien zum Erstellen eines mehrseitigen Artefakts

Wenn Sie eine Vorlage für Ihr Marketingmaterial auswählen, erstellt [!DNL Assets] eine Kopie der Vorlage, die Sie bearbeiten können. Die ursprüngliche Vorlage wird beibehalten, um sicherzustellen, dass Ihre globalen Logos und Unternehmenskennzeichnungen intakt bleiben und wiederverwendet werden können, um für eine einheitliche Markendarstellung zu sorgen.

Sie können die aktualisierte Datei im übergeordneten Ordner in den folgenden Formaten exportieren:

* INDD
* PDF
* JPG

Sie können die Ausgabe in diesen Formaten auch auf Ihr lokales System herunterladen.

## Erstellen von Sicherheiten {#creating-a-collateral}

Stellen Sie sich ein Szenario vor, in dem Sie digitale druckbare Materialien wie Broschüren, Flyer und Anzeigen für eine bevorstehende Kampagne erstellen und für eine globale Freigabe mit Verkaufsstellen verwenden möchten. Das Erstellen von Begleitmaterial basierend auf einer Vorlage hilft, kanalübergreifend ein einheitliches Kundenerlebnis zu bieten. Designer können die Kampagnenvorlagen (einseitige oder mehrseitige) mithilfe einer kreativen Lösung wie InDesign erstellen und die Vorlagen in [!DNL Assets] für Sie. Bevor Sie ein Material erstellen, lassen Sie eine oder mehrere INDD-Vorlagen im Voraus in den Experience Manager hochladen und verfügbar.

1. Klicken Sie auf [!DNL Experience Manager] und klicken Sie auf **[!UICONTROL Assets]** auf der Navigationsseite.
1. Wählen Sie in den Optionen die Option **[!UICONTROL Vorlagen]** aus.

   ![chlimage_1-306](assets/chlimage_1-306.png)

1. Klicken/Tippen **[!UICONTROL Erstellen]** und wählen Sie dann im Menü das zu erstellende Material aus. Wählen Sie beispielsweise die Option **[!UICONTROL Broschüre]** aus.

   ![chlimage_1-307](assets/chlimage_1-307.png)

1. Lassen Sie eine oder mehrere INDD-Vorlagen im Voraus in den Experience Manager hochgeladen und verfügbar. Wählen Sie eine Vorlage für Ihre Broschüre aus und klicken/tippen Sie auf **[!UICONTROL Nächste]**.

   ![chlimage_1-308](assets/chlimage_1-308.png)

1. Geben Sie einen Namen und eine optionale Beschreibung für die Broschüre an.

   ![chlimage_1-309](assets/chlimage_1-309.png)

1. (Optional) Klicken/tippen Sie auf die **[!UICONTROL Tags]** Symbol neben **[!UICONTROL Tags]** und wählen Sie einen oder mehrere Tags für die Broschüre aus. Klicken/Tippen **[!UICONTROL Bestätigen]** um Ihre Auswahl zu bestätigen.

   ![chlimage_1-310](assets/chlimage_1-310.png)

1. Klicken Sie auf **[!UICONTROL Erstellen]**. Ein Dialogfeld bestätigt, dass eine neue Broschüre erstellt wurde. Klicken/Tippen **[!UICONTROL Öffnen]** um die Broschüre im Bearbeitungsmodus zu öffnen.

   ![chlimage_1-311](assets/chlimage_1-311.png)

   Alternativ können Sie das Dialogfeld schließen und auf der Seite &quot;Vorlagen&quot;zu dem Ordner navigieren, mit dem Sie begonnen haben, um die erstellte Broschüre anzuzeigen. Der Typ des Materials wird in der Kartenansicht auf der Miniaturansicht angezeigt. In diesem Fall wird beispielsweise die Broschüre auf der Miniaturansicht angezeigt.

   ![chlimage_1-312](assets/chlimage_1-312.png)

## Bearbeiten von Sicherheiten {#editing-a-collateral}

Sie können Marketingmaterial sofort nach dem Erstellen bearbeiten. Alternativ hierzu können Sie es über die Seite Vorlagen oder die Asset-Seite öffnen.

1. Sie haben folgende Möglichkeiten, um das Marketingmaterial zur Bearbeitung zu öffnen:

   * Öffnen Sie das Material (in diesem Fall die Broschüre), das Sie in Schritt 7 von erstellt haben. [Erstellen von Sicherheiten](asset-templates.md#creating-a-collateral).
   * Navigieren Sie auf der Seite &quot;Vorlagen&quot;zu einem Ordner, in dem Sie das Material erstellt haben, und klicken/tippen Sie in der Miniaturansicht eines Materials auf die Schnellaktion Bearbeiten .
   * Klicken/tippen Sie auf der Asset-Seite für das Material in der Symbolleiste auf das Symbol Bearbeiten .
   * Wählen Sie das Material aus und klicken/tippen Sie in der Symbolleiste auf das Symbol Bearbeiten .

   ![chlimage_1-313](assets/chlimage_1-313.png)

   Links auf der Seite werden die Asset-Suche und der Text-Editor angezeigt. Der Text-Editor ist standardmäßig geöffnet.

   Sie können den Texteditor verwenden, um den Text zu ändern, der im Textfeld angezeigt werden soll. Sie können Schriftgröße, Stil, Farbe und Typ auf Tag-Ebene ändern.

   Mithilfe der Asset-Suche können Sie in [!DNL Assets] nach Bildern suchen und die bearbeitbaren Bilder in der Vorlage durch Bilder Ihrer Wahl ersetzen.

   ![chlimage_1-314](assets/chlimage_1-314.png)

   Die bearbeitbaren Bilder werden rechts angezeigt. Damit ein Feld bearbeitet werden kann in [!DNL Assets], muss das entsprechende Feld in der Vorlage in InDesign getaggt werden. Mit anderen Worten, sie sollten als bearbeitbar im InDesign markiert werden.

   ![chlimage_1-315](assets/chlimage_1-315.png)

   >[!NOTE]
   >
   >Stellen Sie sicher, dass [!DNL Experience Manager] -Instanz ist mit einem InDesign-Server integriert, um [!DNL Assets] , um Daten aus der InDesign-Vorlage zu extrahieren und sie zur Bearbeitung verfügbar zu machen. Weitere Informationen finden Sie unter [Integration [!DNL Assets] mit InDesign Server](indesign.md).

1. Um den Text in einem bearbeitbaren Feld zu ändern, klicken/tippen Sie in der Liste der bearbeitbaren Felder auf das Textfeld und bearbeiten Sie den Text im Feld.

   ![chlimage_1-316](assets/chlimage_1-316.png)

   Sie können die Texteigenschaften, z. B. Schriftstil, Farbe und Größe, mithilfe der bereitgestellten Optionen bearbeiten.

1. Klicken/tippen Sie auf **[!UICONTROL Vorschau]** -Symbol, um eine Vorschau der Textänderungen anzuzeigen.

   ![chlimage_1-317](assets/chlimage_1-317.png)

1. Um ein Bild auszutauschen, klicken/tippen Sie auf die **[!UICONTROL Asset Finder]** Symbol.

   ![chlimage_1-318](assets/chlimage_1-318.png)

1. Wählen Sie in der Liste mit den bearbeitbaren Feldern das Bildfeld aus und ziehen Sie das gewünschte Bild dann aus der Asset-Auswahl in das bearbeitbare Feld.

   ![chlimage_1-319](assets/chlimage_1-319.png)

   Sie können auch nach Bildern suchen, indem Sie Schlüsselwörter, Tags und den Veröffentlichungsstatus angeben. Sie können das [!DNL Assets]-Repository durchsuchen und zum Speicherort des gewünschten Bildes navigieren.

   ![chlimage_1-320](assets/chlimage_1-320.png)

1. Klicken/tippen Sie auf **[!UICONTROL Vorschau]** -Symbol, um eine Vorschau des Bildes anzuzeigen.

   ![chlimage_1-321](assets/chlimage_1-321.png)

1. Um eine bestimmte Seite in einem mehrseitigen Material zu bearbeiten, verwenden Sie den Seitennavigator am unteren Rand.

   ![chlimage_1-322](assets/chlimage_1-322.png)

1. Klicken/tippen Sie auf **[!UICONTROL Vorschau]** in der Symbolleiste, um eine Vorschau aller Änderungen anzuzeigen. Klicken/Tippen **[!UICONTROL Fertig]** , um die Bearbeitungsänderungen am Material zu speichern.

   >[!NOTE]
   >
   >Die Symbole Vorschau und Fertig sind nur aktiviert, wenn die bearbeitbaren Bildfelder im Material keine fehlenden Symbole aufweisen. Wenn in Ihrem Material Symbole fehlen, liegt dies daran, dass [!DNL Experience Manager] kann die Bilder in der InDesign-Vorlage nicht auflösen. Normalerweise können Bilder von [!DNL Experience Manager] in den folgenden Fällen nicht aufgelöst werden:
   >
   >* Bilder werden nicht in die zugrunde liegende InDesign-Vorlage eingebettet
   >* Bilder verfügen über Verknüpfungen mit dem lokalen Dateisystem

   >
   >Gehen Sie wie folgt vor, um für [!DNL Experience Manager] das Auflösen von Bildern zu ermöglichen:
   >
   >* Bilder beim Erstellen von InDesign-Vorlagen einbetten (siehe [Über Links und eingebettete Grafiken](https://helpx.adobe.com/de/indesign/using/graphics-links.html)).
   >* Berg [!DNL Experience Manager] Ihrem lokalen Dateisystem und ordnen Sie dann fehlende Symbole vorhandenen zu [!DNL Experience Manager] Assets.

   >
   >Weitere Informationen zum Arbeiten mit InDesign-Dokumenten finden Sie unter [Best Practices für die Arbeit mit InDesign-Dokumenten in [!DNL Experience Manager]](https://helpx.adobe.com/de/experience-manager/kb/best-practices-idd-docs-aem.html).

1. Um eine PDF-Ausgabedarstellung für die Broschüre zu generieren, wählen Sie die Option Acrobat im Dialogfeld aus und klicken Sie dann auf **[!UICONTROL Weiter]**.
1. Das Material wird in dem Ordner erstellt, mit dem Sie begonnen haben. Um die Ausgabedarstellungen anzuzeigen, öffnen Sie das Material und wählen Sie **[!UICONTROL Ausgabeformate]** aus der GlobalNav-Liste.

   ![chlimage_1-323](assets/chlimage_1-323.png)

1. Klicken/tippen Sie in der Ausgabedarstellungsliste auf die PDF-Ausgabedarstellung , um die PDF-Datei herunterzuladen. Öffnen Sie die PDF-Datei, um das Marketingmaterial zu überprüfen.

   ![chlimage_1-324](assets/chlimage_1-324.png)

## Zusammenführen von Sicherheiten {#merge-collateral}


1. Klicken oder tippen Sie auf **[!UICONTROL Tools > Assets]**.
1. Wählen Sie in den Optionen die Option **[!UICONTROL Vorlagen]** aus.
1. Klicken/Tippen **[!UICONTROL Erstellen]** und wählen Sie **[!UICONTROL Zusammenführen]** aus dem Menü.

   ![chlimage_1-325](assets/chlimage_1-325.png)

1. Klicken/tippen Sie auf der Seite Vorlagenzusammenführung auf das Symbol Zusammenführen .

   ![chlimage_1-326](assets/chlimage_1-326.png)

1. Navigieren Sie zum Speicherort des Assets, das Sie zusammenführen möchten, und klicken/tippen Sie auf die Miniaturansichten des Assets, das Sie zusammenführen möchten, um es auszuwählen.

   ![chlimage_1-327](assets/chlimage_1-327.png)

   Sie können sogar im OmniSearch-Feld nach Vorlagen suchen.

   ![chlimage_1-328](assets/chlimage_1-328.png)

   Sie können das [!DNL Assets]-Repository bzw. die Sammlungen durchsuchen, zum Speicherort der gewünschten Vorlagen navigieren und sie dann für die Zusammenführung auswählen.

   ![chlimage_1-329](assets/chlimage_1-329.png)

   Sie können verschiedene Filter anwenden, um die gewünschten Vorlagen zu durchsuchen. Sie können beispielsweise nach Vorlagen suchen, die auf dem Dateityp oder den Tags basieren.

   ![chlimage_1-330](assets/chlimage_1-330.png)

1. Klicken/Tippen **[!UICONTROL Nächste]** aus der Symbolleiste.
1. Ordnen Sie die Vorlagen bei Bedarf auf dem Bildschirm **[!UICONTROL Vorschau anzeigen und neu anordnen]** neu an und zeigen Sie eine Vorschau für die ausgewählten Vorlagen für die Zusammenführung an. Klicken/tippen Sie dann auf **[!UICONTROL Nächste]** aus der Symbolleiste.

   ![chlimage_1-331](assets/chlimage_1-331.png)

1. Geben Sie auf dem Bildschirm Vorlage konfigurieren einen Namen für das Marketingmaterial an. Geben Sie optional Tags an, die jeweils geeignet sind. Wenn Sie die Ausgabe im PDF-Format exportieren möchten, wählen Sie die **[!UICONTROL Acrobat (.PDF)]** -Option. Standardmäßig wird das Material im JPG- und InDesign-Format exportiert. Um die Miniaturansicht für das mehrseitige Material zu ändern, klicken/tippen Sie auf **[!UICONTROL Miniatur ändern]**.

   ![chlimage_1-332](assets/chlimage_1-332.png)

1. Klicken/Tippen **[!UICONTROL Speichern]** und dann auf **[!UICONTROL OK]** im Dialogfeld, um das Dialogfeld zu schließen. Das mehrseitige Material wird in dem Ordner erstellt, mit dem Sie begonnen haben.

   >[!NOTE]
   >
   >Es ist nicht möglich, zusammengeführtes Material später zu ändern oder zum Erstellen von anderem Material zu verwenden.
