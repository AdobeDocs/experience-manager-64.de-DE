---
title: Erste Sandbox-Anwendung
seo-title: Erste Sandbox-Anwendung
description: Erstellen von Vorlagen, Komponenten und Skripten
seo-description: Erstellen von Vorlagen, Komponenten und Skripten
uuid: b0d03376-d8bc-4e98-aea2-a01744c64ccd
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: f74d225e-0245-4d5a-bb93-0ee3f31557aa
exl-id: 3da30cb4-39b2-4495-9e8b-93567b73b644
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 13%

---

# Initial Sandbox Application {#initial-sandbox-application}

In diesem Abschnitt erstellen Sie Folgendes:

* Die **[template](#createthepagetemplate)** , die zum Erstellen von Inhaltsseiten auf der Beispiel-Website verwendet wird
* Die **[Komponente und das Skript](#create-the-template-s-rendering-component)**, die zum Rendern der Website-Seiten verwendet werden

## Erstellen Sie die Inhaltsvorlage {#create-the-content-template} .

Eine Vorlage definiert den Standardinhalt einer neuen Seite. Bei komplexen Websites werden ggf. auch mehrere Vorlagen für die Erstellung der verschiedenen Seitentypen der Website verwendet. Darüber hinaus kann der Vorlagensatz zu einem Blueprint werden, der zum Rollout von Änderungen an einem Servercluster verwendet wird.

Bei dieser Übung basieren jedoch alle Seiten auf einer einfachen Vorlage.

1. Im Explorer-Bereich der CRXDE Lite

   * auswählen `/apps/an-scf-sandbox/templates`
   * **[!UICONTROL Erstellen > Vorlage erstellen]**

1. Geben Sie im Dialogfeld „Vorlage erstellen“ die folgenden Werte ein und klicken Sie anschließend auf **[!UICONTROL Weiter]**:

   * Bezeichnung: `playpage`
   * Titel: `An SCF Sandbox Play Template`
   * Beschreibung: `An SCF Sandbox template for play pages`
   * Ressourcentyp: `an-scf-sandbox/components/playpage`
   * Ranking: &lt;Als Standard beibehalten>

   Der Titel wird für den Knotennamen verwendet.

   Der Ressourcentyp wird im Knoten jcr:content von `playpage` als Eigenschaft `sling:resourceType` angezeigt. Er identifiziert die Komponente (Ressource), die den Inhalt rendert, wenn sie von einem Browser angefordert wird.

   In diesem Fall werden alle Seiten, die mit der Vorlage `playpage`erstellt wurden, von der Komponente `an-scf-sandbox/components/playpage` gerendert. Standardmäßig ist der Pfad zur Komponente relativ, sodass Sling zuerst im Ordner `/apps` und, falls nicht vorhanden, im Ordner `/libs` nach der Ressource suchen kann.

   ![chlimage_1-75](assets/chlimage_1-75.png)

1. Stellen Sie bei Verwendung von &quot;Kopieren/Einfügen&quot;sicher, dass der Wert &quot;Ressourcentyp&quot;keine führenden oder nachfolgenden Leerzeichen aufweist.

   Klicken Sie auf **[!UICONTROL Weiter]**.

1. &quot;Zulässige Pfade&quot;bezieht sich auf die Pfade von Seiten, die diese Vorlage verwenden, sodass die Vorlage für das Dialogfeld **[!UICONTROL Neue Seite]** aufgelistet wird.

   Um einen Pfad hinzuzufügen, klicken Sie auf die Plusschaltfläche `+` und geben Sie `/content(/.&ast;)?` in das angezeigte Textfeld ein. Wenn Sie Kopieren/Einfügen verwenden, stellen Sie sicher, dass keine führenden oder nachfolgenden Leerzeichen vorhanden sind.

   Hinweis: Der Wert der zulässigen Pfadeigenschaft ist ein *regulärer Ausdruck.* Inhaltsseiten mit einem Pfad, der dem Ausdruck entspricht, können die Vorlage verwenden. In diesem Fall entspricht der reguläre Ausdruck dem Pfad des Ordners **/content** und allen zugehörigen Unterseiten.

   Wenn ein Autor eine Seite unter `/content` erstellt, wird die Vorlage `playpage`mit dem Titel &quot;Eine SCF-Sandbox-Seitenvorlage&quot;in einer Liste der zu verwendenden Vorlagen angezeigt.

   Nachdem die Stammseite aus der Vorlage erstellt wurde, kann der Zugriff auf die Vorlage auf diese Website beschränkt werden, indem die Eigenschaft so geändert wird, dass der Stammpfad in den regulären Ausdruck aufgenommen wird, d. h..

   `/content/an-scf-sandbox(/.&ast;)?`

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. Klicken Sie auf **[!UICONTROL Weiter]**.

   Klicken Sie auf **[!UICONTROL Weiter]** im Bereich **[!UICONTROL Zulässige übergeordnete Elemente]** .

   Klicken Sie in den Bedienfeldern **[!UICONTROL Zulässige untergeordnete Elemente]** auf **[!UICONTROL Weiter]**.

   Klicken Sie auf **[!UICONTROL OK]**.

1. Nachdem Sie auf OK geklickt haben und die Erstellung der Vorlage abgeschlossen haben, werden rote Dreiecke in den Ecken der Eigenschaften -Tab-Werte für die neue Vorlage `playpage`angezeigt. Diese roten Dreiecke zeigen Bearbeitungen an, die nicht gespeichert wurden.

   Klicken Sie auf **[!UICONTROL Alle speichern]** , um die neue Vorlage im Repository zu speichern.

   ![chlimage_1-77](assets/chlimage_1-77.png)

### Erstellen der Rendering-Komponente der Vorlage {#create-the-template-s-rendering-component}

Erstellen Sie die *component*, die den Inhalt definiert und alle Seiten rendert, die basierend auf der [Player-Vorlage](#createthepagetemplate) erstellt wurden.

1. Klicken Sie in CRXDE Lite mit der rechten Maustaste auf **`/apps/an-scf-sandbox/components`** und klicken Sie auf **[!UICONTROL Erstellen > Komponente]**.
1. Durch Festlegen des Knotennamens (Beschriftung) auf *playpage* lautet der Pfad zur Komponente

   `/apps/an-scf-sandbox/components/playpage`

   entspricht dem Ressourcentyp der Paketvorlage (optional abzüglich des anfänglichen Teils **`/apps/`** des Pfads).

   Geben Sie im Dialogfeld **[!UICONTROL Komponente erstellen]** die folgenden Eigenschaftswerte ein:

   * Titel: **playpage**
   * Titel: **Eine SCF-Sandbox-Abspielkomponente**
   * Beschreibung: **Dies ist die Komponente, die Inhalte für eine SCF-Sandbox-Seite rendert.**
   * Super Type: *&lt;leer lassen>*
   * Gruppe:

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. Klicken Sie auf **[!UICONTROL Weiter]**, bis das Bedienfeld **[!UICONTROL Zulässige Kinder]** des Dialogfelds angezeigt wird.

   * Klicken Sie auf **[!UICONTROL OK]**
   * Klicken Sie auf **[!UICONTROL Alle speichern]**

1. Überprüfen Sie, ob der Pfad zur Komponente und der resourceType für die Vorlage übereinstimmen.

   >[!CAUTION]
   >
   >Die Korrespondenz zwischen dem Pfad zur PayPage-Komponente und der sling:resourceType-Eigenschaft der PayPal-Vorlage ist für die korrekte Funktionsweise der Website von entscheidender Bedeutung.

   ![chlimage_1-79](assets/chlimage_1-79.png)
