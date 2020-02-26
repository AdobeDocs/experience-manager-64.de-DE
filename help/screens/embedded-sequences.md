---
title: Eingebettete Sequenzen
seo-title: Eingebettete Sequenzen
description: Folgen Sie dieser Seite, um sich über eingebettete Sequenzen für Kanäle zu informieren. Sie erfahren, wie auf diese Weise Komponenten im übergeordneten Kanal hinzugefügt sowie Inhalte von einem anderen Kanal wiederverwendet und in den übergeordneten Kanal eingebettet werden können.
seo-description: Folgen Sie dieser Seite, um sich über eingebettete Sequenzen für Kanäle zu informieren. Sie erfahren, wie auf diese Weise Komponenten im übergeordneten Kanal hinzugefügt sowie Inhalte von einem anderen Kanal wiederverwendet und in den übergeordneten Kanal eingebettet werden können.
uuid: 3ffbe937-6b60-4eea-acfb-633270b4ded3
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: authoring
discoiquuid: 76be4cc1-4b34-4f1d-b2d3-754a84105dec
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939

---


# Eingebettete Sequenzen{#embedded-sequences}

Mithilfe ***eingebetteter Sequenzen*** für Kanäle können Benutzer Komponenten im übergeordneten Kanal hinzufügen sowie Inhalte von einem anderen Kanal wiederverwenden und in den übergeordneten Kanal einbetten.

## Hinzufügen von eingebetteten Sequenzen {#adding-embedded-sequences}

Sie haben die Möglichkeit, die folgenden Komponenten zu Ihrem Sequenz-Kanal hinzuzufügen:

* Eingebettete Sequenz
* Dynamische eingebettete Sequenz

>[!NOTE]
>
>Weitere Informationen zum Verwenden anderer Komponenten in Ihrem Screens-Projekt finden Sie unter [Hinzufügen von Komponenten zu einem Kanal](/help/screens/adding-components-to-a-channel.md).

### Hinzufügen einer eingebetteten Sequenz    {#adding-an-embedded-sequence}

Sie können Ihrem Kanal eine eingebettete Sequenz hinzufügen. Bei einer eingebetteten Sequenz handelt es sich um einen weiteren Kanal mit Assets wie Bildern oder Videos. Durch Hinzufügen einer eingebetteten Sequenz können Benutzer die Sequenz über den ***Kanalpfad*** in einen Kanal aufnehmen.

>[!NOTE]
>
>Der Kanalpfad definiert einen expliziten Verweis zum Kanal.
>
>Weitere Informationen zum *Kanalpfad* finden Sie in „Inhaltserstellung in Screens“ unter [Kanalzuweisung](/help/screens/channel-assignment.md).

Gehen Sie wie folgt vor, um eine eingebettete Sequenz zu Ihrem Kanal hinzuzufügen:

1. Wählen Sie den Kanal aus, in dem eine Seite eingebettet werden soll. Beispiel: **We.Retail In-Store** > **Kanäle** > „Idle Channel“.

1. Klicken Sie in der Aktionsleiste auf **Bearbeiten**, um den Kanal im Editormodus zu öffnen.
1. Klicken Sie in der linken Seitenleiste auf das Symbol „Komponenten“, um die eingebettete Seite hinzuzufügen. Ziehen Sie die **eingebettete Sequenz** in den Editor.
1. Doppelklicken Sie auf die Komponente **Eingebettete Sequenz**, um den Kanal Ihrem ursprünglichen Sequenzkanal hinzuzufügen.
1. Wählen Sie den **Kanalpfad** des Kanals aus.
1. Wählen Sie die **Dauer (ms)** für Ihren eingebetteten Kanal auf der Registerkarte **Sequenz** aus. Standardmäßig ist die Dauer auf **-1** eingestellt. Dies bedeutet, dass der eingebettete Kanal vollständig ausgeführt wird. Wenn der Benutzer eine Dauer angibt, wird die Teilsequenz zur angegebenen Zeit unterbrochen (abgeschnitten).

1. Legen Sie die **gemessene Wiedergabestrategie** auf **normal** fest.

Standardmäßig ist diese auf **normal** eingestellt. Ist der Wert auf **normal** (Alle Elemente abspielen) eingestellt, wird die Teilsequenz bei jedem Zyklus der übergeordneten Sequenz vollständig ausgeführt. Der andere mögliche Wert lautet **Einzelnes Element abspielen** (Einzelnes Element abspielen). Hierbei wird nur ein Element der Teilsequenz bei jeder Ausführung angezeigt (beispielsweise das erste Element bei der ersten Schleife, das zweite Element bei der zweiten Schleife usw.).

Im folgenden Beispiel sehen Sie, wie eine eingebettete Sequenz (**Idle Channel – Night**) einem bereits vorhandenen Kanal (**Idle Channel**) hinzugefügt wird.

![new2](assets/new2.gif)

### Hinzufügen einer dynamischen eingebetteten Sequenz {#adding-a-dynamic-embedded-sequence}

Sie können Ihrem Kanal eine dynamische eingebettete Sequenz hinzufügen. Eine dynamische eingebettete Sequenz ist mit einer eingebetteten Sequenz vergleichbar. Sie unterscheidet sich allerdings dahingehend, dass der Benutzer einer Hierarchie folgen kann, bei der Änderungen/Aktualisierungen an einem Kanal auf einen anderen, in Bezug stehenden Kanal übertragen werden. Sie folgt einer Hierarchie und umfasst zudem Assets wie Bilder und Videos. Durch Aufnahme einer dynamischen Sequenz kann der Benutzer einen Kanal anhand der Kanalrolle hinzufügen.

>[!NOTE]
>
>Die ***Kanalrolle*** definiert den Kontext der Anzeige.
>
>Weitere Informationen zur *Kanalrolle* finden Sie in „Inhaltserstellung in Screens“ unter [Kanalzuweisung](/help/screens/channel-assignment.md).

Gehen Sie wie folgt vor, um eine eingebettete Sequenz zu Ihrem Kanal hinzuzufügen:

1. Wählen Sie den Kanal aus, in dem eine dynamische Sequenz eingebettet werden soll. Beispiel: **We.Retail In-Store** > **Kanäle** > **Idle Channel**.

1. Klicken Sie in der Aktionsleiste auf **Bearbeiten**, um den Kanal im Editormodus zu öffnen.
1. Klicken Sie in der linken Seitenleiste auf das Symbol „Komponenten“, um die dynamische eingebettete Sequenz hinzuzufügen. Drag and drop the **Dynamic Embedded Sequence** to the editor.

1. Double-click the **Dynamic Embedded Sequence** component to add the page to your sequence channel.

1. Geben Sie die **Kanalzuordnungsrolle** ein.
1. Legen Sie die **gemessene Wiedergabestrategie** auf **normal** fest. Standardmäßig ist diese auf **normal** eingestellt. Ist der Wert auf **normal** (Alle Elemente abspielen) eingestellt, wird die Teilsequenz bei jedem Zyklus der übergeordneten Sequenz vollständig ausgeführt. The other possible value is **Play a single item** *(Play a single item)* and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)

1. Wählen Sie die **Dauer (ms)** für Ihren eingebetteten Kanal auf der Registerkarte **Sequenz** aus.

![latest](assets/latest.gif)

