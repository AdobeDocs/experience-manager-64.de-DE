---
title: Bearbeiten der Seiteneigenschaften
seo-title: Editing Page Properties
description: Die Eigenschaften einer Seite können je nach Art der Seite variieren. Beispielsweise sind einige Seiten möglicherweise mit einer Live Copy verbunden, andere nicht und die Live Copy-Informationen sind entsprechend verfügbar.
seo-description: Properties of a page can vary depending on the nature of the page. For example some pages might be connected to a live copy while others are not and the live copy information will be available as appropriate.
uuid: 63d37d1b-52da-489d-b02b-e8b3d17571d1
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 23768c73-ac64-4727-8313-160c8c131b05
exl-id: 6969dc5e-f7fa-495e-8ddf-8123ca2bc9a6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 38%

---

# Bearbeiten der Seiteneigenschaften{#editing-page-properties}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können die erforderlichen Eigenschaften für eine Seite definieren. Diese können je nach Art der Seite variieren. Beispielsweise sind einige Seiten möglicherweise mit einer Live Copy verbunden, andere nicht und die Live Copy-Informationen sind entsprechend verfügbar.

## Seiteneigenschaften {#page-properties}

Die Eigenschaften sind auf verschiedene Registerkarten verteilt:

### Einfach {#basic}

* **Titel**

   Der Titel der Seite wird an verschiedenen Stellen angezeigt. Beispiel: die **Websites** und der **Sites** Karten-/Listenansichten.

   Dies ist ein Pflichtfeld.

* **Tags**

   Hier können Sie der Seite Tags hinzufügen (oder davon entfernen), indem Sie die Liste im Auswahlfeld aktualisieren:

   * Nachdem Sie ein Tag ausgewählt haben, wird es unter dem Auswahlfeld aufgeführt. Sie können ein Tag mit dem x aus dieser Liste entfernen.
   * Sie können ein völlig neues Tag eingeben, indem Sie den Namen in ein leeres Auswahlfeld eingeben.

      Das neue Tag wird erstellt, wenn Sie die Eingabetaste drücken. Das neue Tag wird dann in einem Feld angezeigt. Ein kleiner Stern auf der rechten Seite markiert es als neues Tag.

   * Mit der Dropdown-Funktion können Sie aus vorhandenen Tags auswählen.
   * Wenn Sie den Mauszeiger über einen Tag-Eintrag im Auswahlfeld bewegen, wird ein x angezeigt. kann verwendet werden, um dieses Tag für diese Seite zu entfernen.

* **In Navigation ausblenden**

   Ein Umschalter gibt an, ob die Seite in der Seitennavigation ein- oder ausgeblendet wird.

* **Seitentitel**

   Ein Titel, der auf der Seite verwendet werden soll.

* **Navigationstitel**

   Sie können einen separaten Titel für die Verwendung in der Navigation angeben (z. B. wenn Sie eine kürzere Alternative wählen möchten). Wenn leer, wird die **Titel** verwendet.

* **Untertitel**

   Ein Untertitel zur Verwendung auf der Seite.

* **Beschreibung**

   Ihre Beschreibung der Seite, ihr Zweck oder andere Details, die Sie hinzufügen möchten.

* **Einschaltzeit**

   Datum und Uhrzeit der Aktivierung der veröffentlichten Seite. Nach der Veröffentlichung ruht diese Seite bis zum angegebenen Zeitpunkt.

   Lassen Sie diese Felder für Seiten, die Sie sofort veröffentlichen möchten (im normalen Szenario), leer.

* **Ausschaltzeit**

   Der Zeitpunkt, zu dem die veröffentlichte Seite deaktiviert wird.

   Lassen Sie diese Felder für Seiten, die Sie sofort veröffentlichen möchten, wieder leer.

* **Vanity-URL**

   Ermöglicht die Eingabe einer Vanity-URL für diese Seite. Dadurch können Sie eine kürzere und ausdrucksstärkere URL verwenden.

   Beispiel: Wenn die Vanity-URL w`elcome` für die Seite mit dem Pfad /`v1.0/startpage` auf der Website h`ttp://example.com,` verwendet wird, wäre h`ttp://example.com/welcome` die Vanity-URL von h`ttp://example.com/content/v1.0/startpage`.

   >[!CAUTION]
   >
   >Vanity-URLs:
   >
   >* muss eindeutig sein. Daher sollten Sie darauf achten, dass der Wert nicht bereits von einer anderen Seite verwendet wird.
   >* unterstützen keine Regex-Muster.


* **Vanity-URL umleiten**

   Gibt an, ob für die Seite eine Vanity-URL verwendet werden soll.

### Erweitert {#advanced}

* **Sprache**

   Die Seitensprache.

* **Umleiten**

   Geben Sie die Seite an, zu der diese Seite automatisch umgeleitet werden soll.

* **Design**

   Geben Sie die [Design](/help/sites-developing/designer.md) für diese Seite verwendet werden.

* **Alias**

   Geben Sie einen Alias an, der für diese Seite verwendet werden soll.

* **Geschlossene Benutzergruppe aktivieren**

   Aktiviert (oder deaktiviert) die Verwendung von [geschlossene Benutzergruppen](/help/sites-administering/cug.md) (CUGs).

* **Anmeldeseite**

   Die für die Anmeldung zu verwendende Seite.

* **Zugelassene Gruppen**

   Gruppen, die für die Anmeldung bei der CUG berechtigt sind.

* **Bereich**

   Bereichsname für die CUG.

* **Konfiguration exportieren**

   Geben Sie eine Exportkonfiguration an.

### Miniaturansicht  {#thumbnail}

* **Seitenminiatur**

   Zeigt das Miniaturbild der Seite an. Sie haben folgende Möglichkeiten:

   * **Vorschau generieren**

      Erstellen Sie eine Vorschau der Seite, die als Miniaturansicht verwendet werden soll.

   * **Bild hochladen**

      Laden Sie ein Bild hoch, das als Miniaturansicht verwendet werden soll.

### Cloud-Services {#cloud-services}

* **Cloud Services**

   Definieren von Eigenschaften für [Cloud Services](/help/sites-developing/extending-cloud-config.md).

### Personalisierung  {#personalization}

* **Personalisierung**

   Wählen Sie eine [Marke, um einen Bereich für das Targeting anzugeben](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md).

### Berechtigungen {#permissions}

* **Berechtigungen** (Touch-optimierte Benutzeroberfläche)

   Zeigen Sie die [effektiven Berechtigungen an und fügen Sie neue Berechtigungen hinzu](/help/sites-administering/user-group-ac-admin.md).

### Blueprint {#blueprint}

* **Blueprint**

   Definieren Sie Eigenschaften für eine Blueprint-Seite in [Multi-Site-Management](/help/sites-administering/msm.md). Steuert die Umstände, unter denen Änderungen an die Live Copy propagiert werden.

### Live Copy  {#live-copy}

* **Live Copy**

   Legen Sie Eigenschaften für eine Live Copy-Seite fest in [Multi-Site-Management](/help/sites-administering/msm.md). Steuert die Umstände, unter denen Änderungen von der Blueprint-Seite propagiert werden.

### Site-Struktur  {#site-structure}

* Geben Sie Links zu Seiten an, die Site-übergreifende Funktionalität bieten, z. B. **Anmeldungsseite**, **Offline-Seite** und andere.

## Bearbeiten der Seiteneigenschaften {#editing-page-properties-2}

### Bearbeiten der Seiteneigenschaften für eine bestimmte Seite {#editing-page-properties-for-a-specific-page}

Seiteneigenschaften definieren die verschiedenen Eigenschaften der Seite, z. B. Titel, wenn sie auf der Website und anderen angezeigt werden.

1. Öffnen Sie die Seite, die Sie bearbeiten möchten.

1. Öffnen Sie im Sidekick die Registerkarte **Seite** und wählen Sie anschließend **Seiteneigenschaften...** aus.

   Ein Dialogfeld mit mehreren Registerkarten wird geöffnet.

1. Nehmen Sie die erforderlichen Änderungen vor und klicken Sie dann auf **OK**, um zu speichern.
