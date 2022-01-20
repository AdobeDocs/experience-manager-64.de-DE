---
title: Benutzerdefinierte Sonderzeichen in Correspondence Management
seo-title: Custom special characters in Correspondence Management
description: Erfahren Sie, wie Sie benutzerdefinierte Sonderzeichen in Correspondence Management hinzufügen.
seo-description: Learn how to add custom special characters in Correspondence Management.
uuid: ac4f1353-f1ef-43b7-8e80-aba56a155e3f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: 1b5e6746-3618-46fe-ba2d-ec76bb79de1d
feature: Correspondence Management
exl-id: a6206ae1-b71b-4066-b7a0-ce39a60d6dd0
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 69%

---

# Benutzerdefinierte Sonderzeichen in Correspondence Management {#custom-special-characters-in-correspondence-management}

## Übersicht {#overview}

Correspondence Management umfasst einen integrierten Standard-Support für 210 Sonderzeichen, die Sie mühelos in Briefen einfügen können.

Sie können beispielsweise die folgenden Sonderzeichen einfügen:

* Währungssymbole wie €,¥ und £
* Mathematische Symbole wie, Ö, % und ^
* Satzzeichen als ‟ und&quot;

Sie können Sonderzeichen in Briefe einfügen:

* Im [Texteditor](/help/forms/using/document-fragments.md#createtext)
* In einer [editierbares Inline-Modul in einer Korrespondenz](/help/forms/using/create-correspondence.md#managecontent)

![specialcharaktersinlinemodul](assets/specialcharactersinlinemodule.png)

Der Administrator kann Unterstützung für mehr/benutzerdefinierte Sonderzeichen durch Anpassung hinzufügen. In diesem Artikel finden Sie Anweisungen dazu, wie Sie Unterstützung für zusätzliche benutzerdefinierte Sonderzeichen hinzufügen können.

## Hinzufügen oder Ändern von Unterstützung für benutzerdefinierte Sonderzeichen in Correspondence Management {#creatingfolderstructure}

Führen Sie die folgenden Schritte aus, um Unterstützung für benutzerdefinierte Sonderzeichen hinzuzufügen:

1. Navigieren Sie zu `https://[server]:[port]/[ContextPath]/crx/de` und melden Sie sich als Administrator an.
1. Erstellen Sie im Ordner &quot;apps&quot;einen Ordner mit dem Namen **[!UICONTROL Sonderzeichen]** mit einem ähnlichen Pfad/einer ähnlichen Struktur zum Ordner &quot;Sonderzeichen&quot;(im Ordner textEditorConfig unter libs):

   1. Klicken Sie mit der rechten Maustaste auf die **Sonderzeichen** Ordner unter folgendem Pfad und wählen Sie **Überlagerungsknoten**:

      `/libs/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters`

   1. Stellen Sie sicher, dass das Dialogfeld „Überlagerungsknoten“ die folgenden Werte enthält:

      **Pfad:** /libs/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters

      **Überlagerungsspeicherort:** /apps/

      **Knotentypen abgleichen:** Aktiviert

      >[!NOTE]
      >
      >Nehmen Sie keine Änderungen in der Verzweigung /libs vor. Alle Änderungen, die Sie vornehmen, gehen möglicherweise verloren, da diese Verzweigung sich ändern kann, wenn Sie:
      >
      >* Ihre Instanz aktualisieren
      >* Ein Hotfix anwenden
      >* Ein Feature Pack installieren


   1. Klicken Sie auf **OK** und dann auf **Alle speichern**. Der Ordner &quot;Sonderzeichen&quot;wird im angegebenen Pfad erstellt.

      Nach dem Erstellen des Überlagerungsknotens, überprüfen Sie die Knotenstrukturtags. Jeder Knoten, der in /Apps mit der Überlagerung erstellt wurde, sollte dieselbe Klasse und dieselben Eigenschaften haben, wie es in /libs für diesen Knoten definiert ist. Wenn eine Eigenschaft oder ein Tag in der Knotenstruktur unter /Apps fehlt, synchronisieren sie die Tags mit dem entsprechenden Knoten in /libs.

1. Stellen Sie sicher, dass der Knoten **[!UICONTROL textEditorConfig]** folgende Eigenschaften und Werte aufweist:

   | Name | Typ | Wert |
   |---|---|---|
   | cmConfigurationType | Zeichenfolge | cmTextEditorConfiguration |
   | cssPath | Zeichenfolge | /libs/fd/cm/ma/gui/components/admin/createasset/textcontrol/clientlibs/textcontrol |

1. Klicken Sie mit der rechten Maustaste auf die **[!UICONTROL Sonderzeichen]** Ordner unter folgendem Pfad und wählen Sie **Erstellen > Untergeordneter Knoten** und klicken Sie anschließend auf **Alle speichern**:

   /apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters/&lt;YourChildNode>

1. Aktualisieren Sie den Texteditor\Benutzeroberfläche „Korrespondenz erstellen“. Der Knoten, den Sie hinzugefügt haben, ist der letzte in der Liste der Sonderzeichen in der Benutzeroberfläche.
1. Klicken Sie auf **Alle speichern**.
1. Nehmen Sie die Änderungen in den Sonderzeichen wie gewünscht vor:

<table> 
 <tbody> 
  <tr> 
   <td><strong>To...</strong></td> 
   <td><strong>Führen Sie nun die folgenden Schritte durch</strong></td> 
  </tr> 
  <tr> 
   <td>Fügen Sie ein benutzerdefiniertes Sonderzeichen hinzu</td> 
   <td> 
    <ol> 
     <li>Fügen Sie einen untergeordneten Knoten unter "/apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters"mit obligatorischen Eigenschaften hinzu.</li> 
     <li>Klicken Sie auf Alle speichern</li> 
     <li>Aktualisieren Sie den Texteditor/Benutzeroberfläche „Korrespondenz erstellen“, um die Änderungen anzuzeigen.</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>Aktualisieren Sie die Eigenschaften der vorhandenen Sonderzeichen</td> 
   <td> 
    <ol> 
     <li>Überlagern den Knoten, der aktualisiert werden soll, wie oben erläutert und überprüfen Sie Tags und Klassen.</li> 
     <li>Ändern Sie alle Werte wie Beschriftung, Wert, endValue und multipleCaption. </li> 
     <li>Klicken Sie auf Alle speichern. </li> 
     <li>Aktualisieren Sie den Texteditor/Benutzeroberfläche „Korrespondenz erstellen“, um die Änderungen anzuzeigen.</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>Ausblenden von Sonderzeichen</td> 
   <td> 
    <ol> 
     <li>Überlagern Sie den Knoten, der unter "/apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters"ausgeblendet werden soll.</li> 
     <li>Fügen Sie die Eigenschaft sling:hideResource (Boolesch) zum Knoten (unter Apps) hinzu, der ausgeblendet werden soll. </li> 
     <li>Klicken Sie auf Alle speichern. </li> 
     <li>Aktualisieren Sie den Texteditor/Benutzeroberfläche „Korrespondenz erstellen“, um die Änderungen anzuzeigen.<br /> </li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>Ausblenden mehrerer Sonderzeichen</td> 
   <td> 
    <ol> 
     <li>Fügen Sie die Eigenschaft "sling:hideChildren (String oder String[])"zu "/apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters"hinzu. </li> 
     <li>Fügen Sie Knotennamen (Sonderzeichen, die ausgeblendet werden sollen) als Werte für die Eigenschaft „sling:hideChildren“ hinzu. </li> 
     <li>Klicken Sie auf Alle speichern. </li> 
     <li>Aktualisieren Sie den Texteditor/Benutzeroberfläche „Korrespondenz erstellen“, um die Änderungen anzuzeigen.<br />  </li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>Sonderzeichen anordnen</td> 
   <td> 
    <ol> 
     <li>Fügen Sie einen untergeordneten Knoten unter "/apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters"mit obligatorischen Eigenschaften hinzu. </li> 
     <li>Fügen Sie die Eigenschaft „sling:orderBefore (String)“ zum neu erstellten untergeordneten Knoten hinzu. </li> 
     <li>Fügen Sie den Knotennamen als Wert vor dem neu hinzugefügten Sonderzeichen hinzu, das angezeigt werden soll. </li> 
     <li>Klicken Sie auf Alle speichern. </li> 
     <li>Aktualisieren Sie den Texteditor/Benutzeroberfläche „Korrespondenz erstellen“, um die Änderungen anzuzeigen.<br /> </li> 
    </ol> </td> 
  </tr> 
 </tbody> 
</table>
