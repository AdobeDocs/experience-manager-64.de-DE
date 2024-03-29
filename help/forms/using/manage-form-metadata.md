---
title: Verwalten von Formularmetadaten
seo-title: Manage form metadata
description: Metadaten ermöglichen eine einfachere Kategorisierung und Organisation der Assets und erleichtern Benutzern die Suche nach einem bestimmten Asset.
seo-description: Metadata allows for easier categorization and organization of assets and helps users who are looking for a specific asset.
uuid: cdb5cb52-5b93-4d99-bd97-fba017406316
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: 28549db2-e2f2-4a25-b0b1-785237d9d941
role: Admin
exl-id: d10bc3e9-66a6-4cb2-b484-da338259f1c8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2009'
ht-degree: 65%

---

# Verwalten von Formularmetadaten {#manage-form-metadata}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht  {#overview-nbsp}

Metadaten ermöglichen eine einfachere Kategorisierung und Organisation der Assets und erleichtern Benutzern die Suche nach einem bestimmten Asset.

AEM Forms stellt standardmäßig einen definierten Metadatensatz für jeden Asset-Typ bereit. Neben den Standardmetadaten können Sie auch benutzerdefinierte Metadaten zu den einzelnen Asset-Typen hinzufügen. AEM Forms bietet Ihnen außerdem die richtigen Mittel, um alle Metadaten effizient für Ihre Formulare zu erstellen, zu verwalten und auszutauschen.

Wenn Sie Entwickler oder Site-Eigentümer sind, können Sie Forms Portal (die Endbenutzeroberfläche für AEM Forms) so anpassen, dass die in Ihrem Unternehmen verwendeten Metadaten widergespiegelt werden. Weitere Informationen zu Forms Portal finden Sie unter [Einführung in das Veröffentlichen von Formularen in einem Portal](/help/forms/using/introduction-publishing-forms.md).

## Metadaten in AEM Forms  {#metadata-in-aem-forms-nbsp}

In AEM Forms ist die Liste der mit einem Asset verknüpften Metadateneigenschaften von dessen Typ abhängig. Wenn Sie außerdem eine benutzerdefinierte Metadateneigenschaft hinzufügen, wird diese für alle Assets des Typs hinzugefügt, für den die benutzerdefinierten Metadaten hinzugefügt wurden.

### Asset-Typen  {#asset-types-nbsp}

Die folgenden Asset-Typen werden in AEM Forms unterstützt:

* Formularvorlagen (XFA-Formulare)
* PDF forms
* Dokument (flach PDF)
* Adaptive Formulare
* Ressourcen
* XFS

### Umfassende Liste der Metadaten {#extensive-list-of-metadata-nbsp}

Im Folgenden sehen Sie eine umfassende Liste der Metadateneigenschaften, die in AEM Forms unterstützt werden:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Eigenschaftsname</strong></td> 
   <td><strong>Asset-Typ</strong></td> 
   <td><strong>Beschreibung</strong><br /> </td> 
  </tr> 
  <tr> 
   <td>Titel</td> 
   <td>Alle außer Ressource</td> 
   <td>Anzeigename des Formulars.<br /> </td> 
  </tr> 
  <tr> 
   <td>Beschreibung</td> 
   <td>Alle außer Ressource</td> 
   <td>Beschreibung des Formulars. Der Benutzer kann diesen Wert angeben.<br /> </td> 
  </tr> 
  <tr> 
   <td>Typ</td> 
   <td>Alle</td> 
   <td><p>Ein schreibgeschützter Wert, der den Asset-Typ angibt. Er kann einen der folgenden Werte aufweisen:</p> 
    <ul> 
     <li>Formularvorlage</li> 
     <li>PDF-Formular, PDF-Formular (Acroform) oder PDF-Formular (Signiert)</li> 
     <li>Dokument, Dokument (signiert)</li> 
     <li>Adaptives Formular</li> 
     <li>Ressource</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Erstellt</td> 
   <td>Alle</td> 
   <td>Ein schreibgeschützter Wert, der den Zeitpunkt der Asset-Erstellung angibt.</td> 
  </tr> 
  <tr> 
   <td>Datum der letzten Änderung</td> 
   <td>Alle</td> 
   <td>Ein schreibgeschützter Wert, der angibt, wann das Asset zuletzt geändert wurde.</td> 
  </tr> 
  <tr> 
   <td>Autor</td> 
   <td>Alle außer Ressource</td> 
   <td><p>Ein schreibgeschützter Wert, der automatisch basierend auf dem Formulartyp berechnet wird.</p> 
    <ul> 
     <li>PDF/Formularvorlage/Dokument – von der hochgeladenen Binärdatei abgerufen.</li> 
     <li>Adaptives Formular – Angemeldeter Benutzer zum Zeitpunkt der Formularerstellung.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Status</td> 
   <td>Alle außer Ressource</td> 
   <td><p> Ein schreibgeschützter Wert, der einen der folgenden Status eines Formulars definiert:</p> 
    <ul> 
     <li>Kein Wert: Wenn ein Formular noch nie veröffentlicht wurde.</li> 
     <li>Veröffentlicht: Wenn ein Formular veröffentlicht wird.</li> 
     <li>Geändert: Wenn ein Formular nach seiner Veröffentlichung geändert wurde.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Letztes Veröffentlichungsdatum</td> 
   <td>Alle außer Ressource</td> 
   <td>Ein schreibgeschützter Wert, der angibt, wann das Formular zuletzt veröffentlicht wurde.</td> 
  </tr> 
  <tr> 
   <td>Ein-/Ausschaltzeit veröffentlichen</td> 
   <td>Alle außer Ressource</td> 
   <td><p>Zeitpunkt, zu dem die automatische Veröffentlichung/Aufhebung der Veröffentlichung des Formulars geplant ist. Der Benutzer legt diesen Wert beim Bearbeiten von Metadaten fest.</p> 
    <ul> 
     <li>Die Zeiten "Publish On"und "Off"sollten über das aktuelle Datum hinausgehen. </li> 
     <li>Die Zeit für die Deaktivierung der Veröffentlichung muss nach der Aktivierungszeit liegen. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Übermittlungs-URL</td> 
   <td><p>Formularvorlage</p> <p>PDF-Formular</p> </td> 
   <td><p>Zum Konfigurieren einer benutzerspezifizierten URL zum Übermitteln von Formulardaten an ein Servlet.</p> <p>Die Übermittlungs-URL kann mit einer der folgenden Methoden konfiguriert werden, die nach Priorität sortiert aufgeführt werden:</p> 
    <ul> 
     <li>Geben Sie über die Schaltfläche zum Übermitteln von HTTP beim Erstellen eines XFA-Formulars in AEM Forms Designer eine Übermittlungs-URL direkt in einer Formularvorlage an.</li> 
     <li>Wählen Sie in der AEM Forms-Benutzeroberfläche ein Formular aus und geben Sie eine Übermittlungs-URL bei der Bearbeitung der Metadateneigenschaften an.</li> 
     <li>Bearbeiten Sie in Forms Portal die Komponente "Search &amp; Lister"und geben Sie auf der Registerkarte "Formularlink"eine Sende-URL an.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>HTML-Renderprofil</td> 
   <td>Formularvorlage</td> 
   <td>Das HTML-Renderprofil, das beim Rendern einer Formularvorlage im HTML-Format verwendet wird.</td> 
  </tr> 
  <tr> 
   <td>Renderformat</td> 
   <td><p>Formularvorlage</p> <p>Adaptives Formular</p> </td> 
   <td><p>Mit dieser Option kann der Benutzer das Renderformat des Formulars bei der Veröffentlichung der Formulare angeben:</p> 
    <ul> 
     <li>HTML</li> 
     <li>PDF</li> 
     <li>Beide</li> 
    </ul> <p>Mit dieser Option wird das Renderformat der Formulare nur im Forms Portal eingeschränkt, wo sie für den Endbenutzer sichtbar sind.</p> </td> 
  </tr> 
  <tr> 
   <td>Tags</td> 
   <td>Alle außer Ressource</td> 
   <td>Mit dem Formular verknüpfte Beschriftungen, um eine schnelle und einfache Suche zu ermöglichen.</td> 
  </tr> 
  <tr> 
   <td>Verweise</td> 
   <td><p>Adaptives Formular</p> <p>Formularvorlage</p> <p>Ressource</p> </td> 
   <td><p>Liste der Assets (andere Formulare oder Ressourcen), mit denen dieses Formular verknüpft ist. Diese Assets können in die folgenden beiden Kategorien unterteilt werden:</p> 
    <ul> 
     <li>Verweist auf: Assets, auf die sich das aktuelle Formular bezieht.</li> 
     <li>Verwiesen von: Assets, die auf das aktuelle Asset verweisen.</li> 
    </ul> <p>Diese Assets werden als Links angezeigt und der Zugriff auf ihre Metadaten erfolgt direkt durch Klicken auf sie.<br /> </p> </td> 
  </tr> 
  <tr> 
   <td>Auswahl des Formularmodells (XDP/XSD)</td> 
   <td>Adaptives Formular</td> 
   <td><p>Gibt an, welches Formularmodell beim Authoring des adaptiven Formulars verwendet wird. Diese Eigenschaft kann folgende Werte haben:</p> 
    <ul> 
     <li>Formularvorlage: Eine Formularvorlage wird aus den im Repository vorhandenen ausgewählt. Dieser Wert kann aktualisiert werden.</li> 
     <li>XML-Schema: Eine XSD-Datei wird hochgeladen. Dieser Wert kann aktualisiert werden.</li> 
     <li>Ohne</li> 
    </ul> 
    <div>
      Ein ausgewähltes Formularmodell kann aktualisiert, aber nicht entfernt werden. 
    </div> </td> 
  </tr> 
 </tbody> 
</table>

## Anzeigen von Formularmetadaten {#view-form-metadata-nbsp}

Assets verfügen über vorhandene Eigenschaftswerte, die im schreibgeschützten Modus angezeigt werden können. Diese Metadaten stammen zum Zeitpunkt des Formular-Uploads oder der Formularerstellung.

1. Navigieren Sie zum Speicherort des Assets, für das Sie Metadaten anzeigen möchten.

1. Öffnen Sie die Eigenschaftsseite mit einer der folgenden Methoden:

   1. Klicken Sie in den Schnellaktionen auf das Symbol „Eigenschaften anzeigen“ ![e_reviewmode_properties_n](assets/e_reviewmode_properties_n.png).

      >[!NOTE]
      >
      >Schnellaktionen sind die Aktionselemente, die beim Zeigen mit der Maus auf eine Miniaturansicht angezeigt werden.

   1. Wählen Sie das Formular aus und klicken Sie auf das Symbol „Eigenschaften anzeigen“ ![e_reviewmode_properties_n](assets/e_reviewmode_properties_n.png), das in der Symbolleiste erscheint.
   1. Navigieren Sie zur Seite mit den Formulardetails, indem Sie auf die Formularminiaturansicht klicken, während Sie sich nicht im Auswahlmodus befinden. Klicken Sie nun oben rechts auf das Augensymbol ![aem6forms_eye_viewon](assets/aem6forms_eye_viewon.png) und anschließend in der Liste darunter auf „Eigenschaften“.

1. Auf der daraufhin geöffneten Eigenschaftsseite wird ein Schema angezeigt, das nur die Metadateneigenschaften mit einem Wert enthält.

   Die Eigenschaftenseite verfügt über eine Symbolleiste mit zwei Aktionssymbolen:

   * Bearbeiten: ![aem6forms_edit](assets/aem6forms_edit.png) Bearbeiten der Metadateneigenschaftswerte
   * Anzeigen: ![aem6forms_eye_viewon](assets/aem6forms_eye_viewon.png) Navigieren Sie zur Seite mit den Formulardetails, auf der das Formular im Vorschaumodus geöffnet wird.

   Der Inhaltsbereich ist in zwei Abschnitte unterteilt:

   * Das linke Bedienfeld enthält die Miniaturansicht des Formulars.
   * Das rechte Bedienfeld enthält Metadateneigenschaften im schreibgeschützten Modus, die über verschiedene Registerkarten verteilt sind.


## Hinzufügen/Aktualisieren von Formularmetadatenwerten {#add-update-form-metadata-values-nbsp}

Sie können den Wert vorhandener Metadateneigenschaften bearbeiten oder einem vorhandenen Metadateneigenschaftsfeld neue Werte hinzufügen (zum Beispiel wenn ein Metadatenfeld leer ist).

### Aktualisieren von Metadateneigenschaftswerten {#update-metadata-property-values}

1. Befolgen Sie die im vorherigen Abschnitt angegebenen Schritte, um die Eigenschaftsseite zu öffnen, auf der vorhandene Metadaten das ausgewählten Formulars angezeigt werden können.

1. Klicken Sie in der Symbolleiste auf das Bearbeitungssymbol ![aem6forms_edit](assets/aem6forms_edit.png), um den Modus der Seite von „schreibgeschützt“ in „Lesen/Schreiben“ zu ändern.

1. Die daraufhin geöffnete Eigenschaftsseite enthält ein Schema, das aus einer Mischung aus bearbeitbaren Eingabefelder und statischem Text enthält.

1. Die im statischen Text angezeigten Eigenschaften sind diejenigen, die Sie nicht bearbeiten können.

1. Sie können zu anderen Registerkarten navigieren, um Eingabefelder für die Metadateneigenschaften zu suchen, die darunter platziert werden.

   Diese Seite enthält eine Symbolleiste mit zwei Aktionssymbolen, die sich von denen im Ansichtsmodus unterscheiden:

   * Abbrechen: ![aem6forms_close](assets/aem6forms_close.svg_w24.png) Machen Sie alle Änderungen rückgängig, die bis jetzt an den Metadateneigenschaftswerten vorgenommen wurden
   * Fertig: ![aem6forms_check](assets/aem6forms_check.png) Speichern Sie alle Änderungen, die bis jetzt an den Metadateneigenschaftswerten vorgenommen wurden

   Bei beiden Aktionen wird der Benutzer zurück zum schreibgeschützten Modus der Eigenschaftsseite mit den aktualisierten Werten geleitet.

### Aktualisieren der Formularminiaturansicht  {#update-the-form-thumbnail-nbsp}

Im linken Bedienfeld der Eigenschaftsseite wird die Miniaturansicht des Formulars angezeigt. Standardmäßig wird die angezeigte Miniaturansicht zum Zeitpunkt der Formularerstellung (adaptives Formular) oder des Formular-Uploads generiert.

Für alle Formulartypen haben Sie die Möglichkeit, ein Bild hochzuladen, indem Sie auf **[!UICONTROL Bild hochladen]** und suchen Sie nach einer Bilddatei aus dem lokalen Verzeichnis. Das ausgewählte Bild wird anstelle des Standardbilds als Miniaturansicht verwendet.

Für adaptive Formulare stehen zusätzliche Funktionen zur Verfügung, mit denen der Benutzer eine Miniaturansicht als Momentaufnahme der aktuellen Vorschau des adaptiven Formulars generieren kann. Da AEM Forms auch das Authoring adaptiver Formulare unterstützt, kann sich die Vorschau des adaptiven Formulars ändern, wenn Sie das adaptive Formular ändern. Diese Funktion zum Generieren einer Miniaturansicht hilft Ihnen beim Abrufen einer neuen Miniaturansicht für das adaptive Formular, die auf dem aktuellen Vorschaustatus basiert. Klicken **[!UICONTROL Vorschau generieren]** um diese Maßnahme durchzuführen.

>[!NOTE]
>
>* Verwenden Sie ein quadratisches Bild für die Miniaturansicht. Wenn Sie ein nicht quadratisches Bild verwenden und die Miniaturansicht in der Listenansicht anzeigen, ist die Miniaturansicht abgeschnitten.
>* Sobald ein neues Bild hochgeladen oder generiert wurde, wird die Miniaturansicht durch dieses Bild ersetzt und kann nicht auf das vorherige Bild zurückgesetzt werden.
>


## Hinzufügen benutzerdefinierter Metadaten  {#add-custom-metadata-nbsp}

Zusätzlich zu den standardmäßig bereitgestellten Metadaten unterstützt AEM Forms auch neue benutzerdefinierte Metadaten.

Ein Tool (Metadatenschema-Editor) wird bereitgestellt, um das Schema für das Metadaten-Layout zu definieren (also das Layout des Inhalts der Seite **[!UICONTROL Eigenschaften]** eines Formulars). Mit dem Metadatenschema-Editor können Sie ein benutzerdefiniertes Schema für Ihre Assets hinzufügen oder ändern.

AEM Forms stellt die Metadatenschemata der unterstützten Formulartypen in diesem Tool dar. Auf diese Weise können Sie auf diese Schemas zugreifen und die Funktion des Metadatenschema-Editors verwenden, um benutzerdefinierte Eigenschaften hinzuzufügen.

### Navigieren im Metadatenschema-Editor  {#navigate-the-metadata-schema-editor-nbsp}

1. Navigieren Sie zu **[!UICONTROL Tools > Assets > Metadatenschemas]**.

1. Klicken Sie in den aufgeführten Schemaformularen auf **[!UICONTROL Formulare]**.

1. Klicken Sie in der Liste, die geöffnet wird, auf den Asset-Typ, für den Sie benutzerdefinierte Metadaten hinzufügen möchten.

   >[!NOTE]
   >
   >Diese Schemas enthalten Metadateneigenschaften, die standardmäßig bereitgestellt werden und nicht geändert/bearbeitet werden dürfen (Kontrollkästchen aktivieren und in der Symbolleiste auf „Bearbeiten“ klicken), um Funktionsprobleme zu vermeiden.

1. Wenn Sie auf einen Asset-Typ klicken, wird eine Liste mit der Option `extendedmetadata` geöffnet. Bearbeiten Sie dieses Schema.

1. Aktivieren Sie das Kontrollkästchen neben `extendedmetadata` und klicken Sie dann auf das Bearbeitungssymbol ![aem6forms_edit](assets/aem6forms_edit.png), das in der Symbolleiste angezeigt wird.

1. AEM Forms öffnet den Metadatenschema-Editor/Formularersteller des ausgewählten Asset-Typs (in diesem Fall „adaptives Formular“).

   ![Metadatenschema-Editor für den Typ „Adaptives Formular“](assets/metadata-schema-editor-for-adaptive-form-type.png)

[Klicken Sie zum Vergrößern auf](assets/metadata-schema-editor-for-adaptive-form-type.png)

   1. Das linke Bedienfeld enthält Abschnitte in Registerkarten mit den Feldern und im rechten Bedienfeld werden alle verfügbaren Benutzeroberflächen-Komponenten sowie die Eigenschaften des im linken Bedienfeld ausgewählten Feldes angezeigt.

   1. Der gesperrte Abschnitt kann nicht bearbeitet werden und enthält Felder für alle Metadateneigenschaften, die standardmäßig bereitgestellt werden.

   1. Sie können weitere Registerkarten hinzufügen, indem Sie auf + klicken.

   1. Sie können ein benutzerdefiniertes Feld des gewünschten Typs hinzufügen, indem Sie die Feldkomponente aus dem Abschnitt **[!UICONTROL Formular erstellen]** auf die Schemaseite ziehen.
   1. Die Spezifikationen für dieses Feld können im Abschnitt **[!UICONTROL Einstellungen]** angegeben werden, nachdem Sie auf das Feld geklickt haben.

### Hinzufügen benutzerdefinierter Metadateneigenschaften im Schemaeditor  {#add-custom-metadata-property-in-schema-editor-nbsp}

1. Navigieren Sie zur Registerkarte (vorhanden oder neu), der Sie die benutzerdefinierte Eigenschaft hinzufügen möchten.

1. Ziehen Sie eine Komponente des gewünschten Typs aus dem Abschnitt **[!UICONTROL Formular erstellen]** in das linke Bedienfeld und platzieren Sie sie an der gewünschten Stelle.

   >[!NOTE]
   >
   >Sie können gesperrte Abschnitte nicht verschieben, aber Sie können die Komponente in einem der leeren Bereiche platzieren.

1. Klicken Sie auf eine Komponente, die Sie gerade verschoben haben. Geben Sie in der Registerkarte „Einstellungen“, die im rechten Bedienfeld geöffnet wird, die Informationen für folgende Felder ein:

   1. Geben Sie eine Feldbezeichnung an, die als Anzeigename über dem im Schema platzierten Feld verwendet wird (z. B.: Abteilung)
   1. Unter dem Feld „Zu Eigenschaft zuordnen“ wird ein bereits befüllter Wert angezeigt **„./jcr:content/metadata/default&#39;**. Ändern Sie „**default**“ in einen gewünschten Eigenschaftsnamen, mit dem die Eigenschaft im CRX-Repository gespeichert wird (zum Beispiel „./jcr:content/metadata/department“)

      >[!NOTE]
      >
      >Ändern Sie nicht das Präfix „./jcr:content/metadata/&quot;, da es den Pfad definiert, in dem die Eigenschaft gespeichert ist.
      >
      >
      >Außerdem muss der Eigenschaftsname eindeutig sein, um zu vermeiden, dass Werte für zwei oder mehr Eigenschaften am selben Speicherort im Repository geschrieben werden. Daher wird empfohlen, den Wert &quot;default&quot;zu ändern.

   1. Füllen Sie andere Einstellungen nach Bedarf aus. Beispiel: Wählen Sie die Option „Erforderlich“, um das Feld zu einem Pflichtfeld zu machen.

   1. Um ein hinzugefügtes Feld zu löschen, wählen Sie das Feld aus und klicken Sie dann auf das Symbol zum Löschen ![delete-1](assets/delete-1.png).

1. Bei Bedarf können Sie die Schritte 1 bis 3 wiederholen, um eine weitere Eigenschaft hinzuzufügen.
1. Klicken Sie auf **Fertig**, nachdem Sie alle Änderungen vorgenommen haben.

   Sie haben erfolgreich eine benutzerdefinierte Metadateneigenschaft hinzugefügt.

Alle adaptiven Formulare in AEM Forms enthalten jetzt diese zusätzliche Metadateneigenschaft. Sie können sie über die Eigenschaftsseite bearbeiten.
