---
title: Metadatenschemata
description: Das Metadatenschema definiert das Layout der Eigenschaftsseite und die für Assets angezeigten Metadateneigenschaften. Erfahren Sie, wie Sie ein benutzerdefiniertes Metadatenschema erstellen, Metadatenschema bearbeiten und Metadatenschema auf Assets anwenden.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 82f42bb3-2c01-407c-a41b-9abe7be4660e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2560'
ht-degree: 56%

---

# Metadatenschemata   {#metadata-schemas}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

In [!DNL Experience Manager Assets], definiert ein Metadatenschema das Layout der Eigenschaftsseite und die für Assets angezeigten Metadateneigenschaften, die das betreffende Schema verwenden. Zu den Metadateneigenschaften zählen u. a. Titel, Beschreibung, MIME-Typen, Tags usw. Mit dem Editor für Metadaten-Schemaformulare können Sie vorhandene Schemata ändern oder benutzerdefinierte Metadatenschemata hinzufügen.

Gehen Sie wie folgt vor, um die Eigenschaftenseite für ein Asset anzuzeigen und zu bearbeiten:

1. Klicken oder tippen Sie auf **[!UICONTROL Eigenschaften anzeigen]** aus Schnellaktionen auf der Asset-Kachel in der Kartenansicht.

   ![chlimage_1-170](assets/chlimage_1-170.png)

   Alternativ können Sie ein Asset auswählen und dann auf die **[!UICONTROL Eigenschaften]** in der Symbolleiste.

   ![chlimage_1-171](assets/chlimage_1-171.png)

1. Sie können die verschiedenen bearbeitbaren Metadaten-Eigenschaften auf den verfügbaren Registerkarten bearbeiten. Den Asset-[!UICONTROL Typ] können Sie jedoch nicht auf der Registerkarte [!UICONTROL Standard] der Eigenschaftsseite ändern.

   ![chlimage_1-172](assets/chlimage_1-172.png)

   Verwenden Sie zum Ändern des MIME-Typs für ein Asset ein benutzerdefiniertes Metadatenschema-Formular oder ändern Sie ein vorhandenes Formular. Siehe [Bearbeiten von Metadatenschema-Forms](metadata-schemas.md#editing-metadata-schema-forms) für weitere Informationen. Wenn Sie das Metadatenschema für einen bestimmten MIME-Typ ändern, wird das Seitenlayout der Eigenschaften für Assets mit dem aktuellen MIME-Typ und allen Asset-Untertypen geändert. Ändern Sie beispielsweise eine `jpeg` Schema unter `default/image` ändert nur das Metadatenlayout (Asset-Eigenschaften) für Assets mit dem MIME-Typ `IMAGE/JPEG`. Wenn Sie allerdings das „default“-Schema ändern, wird dadurch das Metadaten-Layout für alle Asset-Typen geändert.

## Metadaten-Schemaformulare {#default-metadata-schema-forms}

Um eine Liste von Formularen/Vorlagen anzuzeigen, lesen Sie [!DNL Experience Manager] -Benutzeroberfläche navigieren zu **[!UICONTROL Instrumente]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenschemata]**.

[!DNL Experience Manager] stellt die folgenden Metadatenschema-Formularvorlagen bereit:

| Vorlagen |  | Beschreibung |
|---|---|---|
| [!UICONTROL default] |  | Dies ist das Basis-Metadatenschema-Formular für Assets. |
|  | Die folgenden untergeordneten Formulare übernehmen die Eigenschaften des [!UICONTROL Standard]-Formulars: |  |
|  | <ul><li> [!UICONTROL Dm_video]</li></ul> | Schemaformular für Dynamic Media-Videos. |
|  | <ul><li> [!UICONTROL image]</li></ul> | Schemaformular für Assets mit dem MIME-Typ &quot;image&quot;, z. B. image/jpeg, image/png usw. <br> Das Formular [!UICONTROL Bild] weist die folgenden untergeordneten Formularvorlagen auf: <ul><li> [!UICONTROL jpeg]: Schemaformular für Assets mit dem Untertyp [!UICONTROL jpeg].</li> <li>[!UICONTROL tiff]: Schemaformular für Assets mit Untertyp [!UICONTROL tiff].</li></ul> |
|  | <ul><li> [!UICONTROL Anwendung]</li></ul> | Schemaformular für Assets mit dem MIME-Typ &quot;application&quot;, z. B. application/ pdf, application/ zip usw. <br>[!UICONTROL pdf]: Schemaformular für Assets mit dem Untertyp &quot;pdf&quot;. |
|  | <ul><li>[!UICONTROL Video]</li></ul> | Schemaformular für Assets mit dem MIME-Typ &quot;Video&quot;, wie video/avi, video/mp4 usw. |
| [!UICONTROL collection] |  | Schemaformular für Sammlungen. |
| [!UICONTROL contentfragment] |  | Schemaformular für Inhaltsfragmente. |
| [!UICONTROL forms] |  | Dieses Schemaformular bezieht sich auf [Adobe Experience Manager Forms](/help/forms/home.md). |

>[!NOTE]
>
>Um die untergeordneten Formulare eines Schemaformulars anzuzeigen, klicken/tippen Sie auf den Namen des Schemaformulars.

## Hinzufügen von Metadatenschema-Formularen {#adding-a-metadata-schema-form}

1. Um eine benutzerdefinierte Vorlage zur Liste hinzuzufügen, klicken Sie in der Symbolleiste auf **[!UICONTROL Erstellen]**.

   >[!NOTE]
   >
   >Nicht bearbeitete Vorlagen weisen ihnen ein Sperrsymbol zu. Wenn Sie eine Vorlage anpassen, wird das Sperrsymbol vor der Vorlage ausgeblendet.

1. Geben Sie im Dialogfeld den Titel des Schemaformulars ein und klicken Sie auf **[!UICONTROL Erstellen]** , um den Formularerstellungsprozess abzuschließen.

   ![chlimage_1-174](assets/chlimage_1-174.png)

## Bearbeiten von Metadatenschema-Formularen {#editing-metadata-schema-forms}

Sie können ein neu hinzugefügtes oder vorhandenes Metadatenschema-Formular bearbeiten. Das Metadatenschema-Formular umfasst Folgendes:

* Registerkarten
* Formularelemente in Registerkarten.

Sie können diese Formularelemente einem Feld innerhalb eines Metdatenknotens im CRX-Repository zuordnen bzw. dafür konfigurieren.

Sie können dem Metadatenschema-Formular neue Registerkarten oder Formularelemente hinzufügen. Die vom übergeordneten Objekt abgeleiteten Registerkarten und Formularelemente sind gesperrt. Sie können auf untergeordneter Ebene nicht geändert werden.

1. Im **[!UICONTROL Schema Forms]** Seite, aktivieren Sie das Kontrollkästchen vor einem Formular und klicken Sie auf **[!UICONTROL Bearbeiten]** in der Symbolleiste.

   ![chlimage_1-175](assets/chlimage_1-175.png)

1. Passen Sie auf der Seite **[!UICONTROL Metadatenschema-Formular]** die Eigenschaftenseite des Assets an, indem Sie Komponenten aus der Komponentenliste auf der Registerkarte **[!UICONTROL Formular erstellen]** in die Registerkarte **[!UICONTROL Basis]** ziehen.

   ![chlimage_1-176](assets/chlimage_1-176.png)

1. Um eine Komponente zu konfigurieren, wählen Sie diese aus und ändern Sie ihre Eigenschaften auf der Registerkarte **[!UICONTROL Einstellungen]**.

### Komponenten auf der Registerkarte Formular erstellen {#components-within-the-build-form-tab}

Die Registerkarte **[!UICONTROL Formular erstellen]** enthält Formularelemente, die Sie im Schemaformular verwenden. Die Registerkarte **[!UICONTROL Einstellungen]** enthält die Attribute für jedes Element, das Sie auf der Registerkarte **[!UICONTROL Formular erstellen]** auswählen. Die folgende Tabelle enthält die auf der Registerkarte **[!UICONTROL Formular erstellen]** verfügbaren Formularelemente:

| Komponentenname | Beschreibung |
|---|---|
| [!UICONTROL Bereichs-Kopfzeile] | Fügen Sie eine Abschnittsüberschrift für eine Liste allgemeiner Komponenten hinzu. |
| [!UICONTROL Einzeilentext] | Fügen Sie eine einzeilige Texteigenschaft hinzu. Diese wird als Zeichenfolge gespeichert. |
| [!UICONTROL Mehrfachwerttext] | Fügen Sie eine Texteigenschaft mit mehreren Werten hinzu. Diese wird als Zeichenfolgen-Array gespeichert. |
| [!UICONTROL Zahl] | Fügen Sie eine Zahlenkomponente hinzu. |
| [!UICONTROL Datum] | Fügen Sie eine Datumskomponente hinzu. |
| [!UICONTROL Dropdown] | Fügen Sie eine Dropdown-Liste hinzu. |
| [!UICONTROL Standard-Tags] | Fügen Sie ein Tag hinzu. |
| [!UICONTROL Smart-Tags] | Fügen Sie automatisch Metadaten-Tags hinzu, um Suchfunktionen zu ergänzen. |
| [!UICONTROL Ausgeblendetes Feld] | Fügen Sie ein ausgeblendetes Feld hinzu. Dieses wird beim Speichern des Assets als POST-Parameter gesendet. |
| [!UICONTROL Asset referenziert von] | Fügen Sie diese Komponente hinzu, um eine Liste der vom Asset referenzierten Assets anzuzeigen. |
| [!UICONTROL Asset-Verweise] | Fügen Sie dies hinzu, um eine Liste der Assets anzuzeigen, die das Asset referenzieren. |
| [!UICONTROL Produktverweise] | Fügen Sie dies hinzu, um die Liste der mit dem Asset verknüpften Produkte anzuzeigen. |
| [!UICONTROL Asset-Bewertung] | Fügen Sie dies hinzu, um Optionen zur Bewertung des Assets anzuzeigen. |
| [!UICONTROL Kontextuelle Metadaten] | Fügen Sie diese Komponente hinzu, um weitere Metadaten auf der Seite „Eigenschaften“ von Assets anzuzeigen. |

### Bearbeiten von Metadatenkomponenten {#editing-the-metadata-component}

Um die Eigenschaften einer Metadatenkomponente im Formular zu bearbeiten, klicken Sie auf die Komponente und bearbeiten Sie alle Eigenschaften oder einen Teil der folgenden Eigenschaften auf der Registerkarte **[!UICONTROL Einstellungen]**.

**Feldbezeichnung**: Der Name der Metadateneigenschaft, der auf der Eigenschaftenseite des Assets angezeigt wird.

**Zu Eigenschaft zuordnen**: Diese Eigenschaft gibt den relativen Pfad/Namen zum Asset-Knoten an, unter dem die Eigenschaft im CRX-Repository gespeichert ist. Sie beginnt mit `./`, um anzugeben, dass der Pfad sich unter dem Knoten des Assets befindet.

Im Folgenden finden Sie die gültigen Werte für diese Eigenschaft:

* `./jcr:content/metadata/dc:title`: Speichert den Wert im Metadatenknoten des Assets als die Eigenschaft `dc:title`.

* `./jcr:created`: Zeigt die JCR-Eigenschaft im Knoten des Assets an. Wenn Sie diese Eigenschaften für Ansichtseigenschaften konfigurieren, wird empfohlen, dass Sie sie mit „Bearbeitung deaktivieren“ markieren, da sie geschützt sind. Andernfalls wird der Fehler [!UICONTROL Asset(s) konnte(n) nicht geändert werden] Ergebnisse beim Speichern der Eigenschaften des Assets.

Um sicherzustellen, dass die Komponente ordnungsgemäß im Metadatenschema-Formular angezeigt wird, sollte der Eigenschaftspfad keine Leerzeichen enthalten.

**Platzhalter**: Verwenden Sie diese Eigenschaft, um relevanten Platzhaltertext für die Metadateneigenschaft anzugeben.

**Erforderlich**: Verwenden Sie diese Eigenschaft, um eine Metadateneigenschaft auf der Eigenschaftsseite als obligatorisch zu markieren.

**Bearbeiten deaktivieren**: Verwenden Sie diese Eigenschaft, um eine Metadateneigenschaft auf der Eigenschaftenseite nicht zu bearbeiten.

**Leeres Feld schreibgeschützt anzeigen**: Markieren Sie diese Eigenschaft, um eine Metadateneigenschaft auch dann auf der Eigenschaftenseite anzuzeigen, wenn sie keinen Wert aufweist. Standardmäßig werden Metadateneigenschaften ohne Werte nicht auf der Eigenschaftenseite aufgeführt.

**Liste geordnet anzeigen**: Mit dieser Eigenschaft zeigen Sie eine geordnete Liste von Optionen an.

**Wahlen**: Mit dieser Eigenschaft legen Sie Optionen in einer Liste fest

**Beschreibung**: Mit dieser Eigenschaft können Sie eine kurze Beschreibung für die Metadatenkomponente hinzufügen.

**Klasse**: Objektklasse, mit der die Eigenschaft verknüpft ist.

**Löschsymbol** Klicken Sie auf dieses Symbol, um eine Komponente aus dem Schemaformular zu löschen.

>[!NOTE]
>
>Die Komponente Ausgeblendetes Feld enthält diese Attribute nicht. Stattdessen enthält es Eigenschaften wie Attributname, Wert, Feldbezeichnung und Beschreibung. Die Werte für die Komponente &quot;Ausgeblendetes Feld&quot;werden beim Speichern des Assets als POST-Parameter gesendet. Sie wird nicht als Metadaten für das Asset gespeichert.

Wenn Sie die Option **[!UICONTROL Erforderlich]** auswählen, können Sie nach Assets suchen, denen obligatorische Metadaten fehlen. Erweitern Sie im Bedienfeld **[!UICONTROL Filter]** die Eigenschaft **[!UICONTROL Metadatenvalidierung]** und wählen Sie die Option **[!UICONTROL Ungültig]**. Die Suchergebnisse zeigen Assets an, denen erforderliche Metadaten fehlen, die Sie über das Schemaformular konfiguriert haben.

![chlimage_1-178](assets/chlimage_1-178.png)

Wenn Sie die Komponente &quot;Kontextuelle Metadaten&quot;zu einer Registerkarte eines Schemaformulars hinzufügen, wird die Komponente auf der Eigenschaftenseite von Assets, auf die das bestimmte Schema angewendet wird, als Liste angezeigt. Die Liste enthält alle anderen Registerkarten außer der Registerkarte, auf die Sie die Komponente „Kontextuelle Metadaten“ angewendet haben. Derzeit bietet diese Funktion grundlegende Funktionalität zur Steuerung der Anzeige von Metadaten, die auf dem Kontext basieren.

![chlimage_1-179](assets/chlimage_1-179.png)

Um eine beliebige Registerkarte auf der Eigenschaftenseite zusätzlich zur Registerkarte einzubeziehen, auf die die Komponente &quot;Kontextuelle Metadaten&quot;angewendet wird, wählen Sie die Registerkarte aus der Liste aus. Die Registerkarte wird der Eigenschaftenseite hinzugefügt.

![chlimage_1-180](assets/chlimage_1-180.png)

### Festlegen von Eigenschaften in einer JSON-Datei {#specifying-properties-in-json-file}

Anstatt die Eigenschaften für die Optionen auf der Registerkarte **[!UICONTROL Einstellungen]** anzugeben, können Sie die Optionen in einer JSON-Datei definieren, indem Sie die entsprechenden Schlüssel/Wert-Paare angeben. Geben Sie den Pfad der JSON-Datei im Feld **[!UICONTROL JSON-Pfad]** an.

### Hinzufügen oder Löschen von Registerkarten im Schemaformular {#adding-deleting-a-tab-in-the-schema-form}

Mit dem Schema-Editor können Sie Registerkarten hinzufügen oder löschen. Das Standard-Schemaformular umfasst standardmäßig die Registerkarten **[!UICONTROL Standard]**, **[!UICONTROL Erweitert]**, **[!UICONTROL IPTC]** und **[!UICONTROL IPTC-Erweiterung]**.

![chlimage_1-181](assets/chlimage_1-181.png)

Klicken Sie auf `+`, um einem Schemaformular eine neue Registerkarte hinzuzufügen. Standardmäßig hat die neue Registerkarte den Namen `Unnamed-1`. Sie können den Namen auf der Registerkarte **[!UICONTROL Einstellungen]** ändern. Klicken Sie auf `X`, um eine Registerkarte zu löschen.

![chlimage_1-182](assets/chlimage_1-182.png)

## Löschen von Metadatenschema-Formularen {#deleting-metadata-schema-forms}

In [!DNL Experience Manager] können Sie nur benutzerdefinierte Schemaformulare löschen. Die Standardschemaformulare/-vorlagen können nicht gelöscht werden. Sie können jedoch alle benutzerdefinierten Änderungen in diesen Formularen löschen.

Um ein Formular zu löschen, wählen Sie das Formular aus und klicken Sie auf das Symbol **[!UICONTROL Löschen]**.

>[!NOTE]
>
>Nachdem Sie benutzerdefinierte Änderungen an einem Standardformular gelöscht haben, wird das Sperrsymbol erneut auf der Benutzeroberfläche des Metadatenschemas angezeigt, um anzugeben, dass das Formular wieder in den Standardzustand versetzt wurde.

>[!NOTE]
>
>Sie können die nativen Metadatenschema-Formulare nicht löschen in [!DNL Experience Manager] Assets.

## Schemaformulare für MIME-Typen {#schema-forms-for-mime-types}

[!DNL Experience Manager] Assets bietet standardmäßig Standardformulare für verschiedene MIME-Typen. Sie können jedoch benutzerdefinierte Formulare für verschiedene MIME-Typen hinzufügen.

### Hinzufügen neuer Formulare für MIME-Typen {#adding-new-forms-for-mime-types}

Erstellen Sie ein neues Formular unter dem entsprechenden Formulartyp. Um beispielsweise eine neue Vorlage für die `image/png` subtype erstellen Sie das Formular unter dem `image` Formulare. Der Titel für das Schemaformular ist der Name des Untertyps. In diesem Fall ist der Titel `png`.

### Verwenden einer vorhandenen Schemavorlage für verschiedene MIME-Typen {#using-an-existing-schema-template-for-various-mime-types}

Sie können eine vorhandene Vorlage für einen anderen MIME-Typ verwenden. Nutzen Sie beispielsweise das Formular `image/jpeg` für Assets mit dem MIME-Typ `image/png`.

Erstellen Sie in diesem Fall einen neuen Knoten unter `/etc/dam/metadataeditor/mimetypemappings` im CRX-Repository. Geben Sie einen Namen für den Knoten an und definieren Sie die folgenden Eigenschaften:

| Name | Beschreibung | Typ | Wert |
|---|---|---|---|
| `exposedmimetype` | Name des vorhandenen Formulars, das zugeordnet werden soll | `String` | `image/jpeg` |
| `mimetypes` | Liste der MIME-Typen, die das im Attribut `exposedmimetype` definierte Formular verwenden | `String` | `image/png` |

[!DNL Experience Manager] Assets ordnet die folgenden MIME-Typen und Schemaformulare zu:

| Schemaformular | MIME-Typen |
|---|---|
| image/jpeg | image/pjpeg |
| image/tiff | image/x-tiff |
| application/pdf | application/postscript |
| application/x-ImageSet | Multipart/Related; type=application/x-ImageSet |
| application/x-SpinSet | Multipart/Related; type=application/x-SpinSet |
| application/x-MixedMediaSet | Multipart/Related; type=application/x-MixedMediaSet |
| video/quicktime | video/x-quicktime |
| video/mpeg4 | video/mp4 |
| video/avi | video/avi, video/msvideo, video/x-msvideo |
| video/wmv | video/x-ms-wmv |
| video/flv | video/x-flv |

## Zugriff auf Metadatenschemata gewähren {#granting-access-to-metadata-schemas}

Die Metadatenschema-Funktion steht nur Administratoren zur Verfügung. Administratoren können Benutzern ohne Administratorrechte jedoch Zugriff gewähren, indem sie **[!UICONTROL Erstellen]**, **[!UICONTROL Ändern]** und **[!UICONTROL Löschen]** Berechtigungen für `/conf` Ordner.

## Anwenden von ordnerspezifischen Metadaten {#applying-folder-specific-metadata}

[!DNL Experience Manager] Mit Assets können Sie eine Variante eines Metadatenschemas definieren und auf einen bestimmten Ordner anwenden.

Sie können beispielsweise eine Variante des Standard-Metadatenschemas definieren und auf einen Ordner anwenden. Wenn Sie das geänderte Schema anwenden, überschreibt es das ursprüngliche standardmäßige Metadatenschema, das auf Assets im Ordner angewendet wird.

Nur Assets, die in den Ordner hochgeladen wurden, auf den dieses Schema angewendet wird, entsprechen den modifizierten Metadaten, die im Varianten-Metadatenschema definiert sind.

Assets in anderen Ordnern, auf die das ursprüngliche Schema angewendet wird, entsprechen weiterhin den im ursprünglichen Schema definierten Metadaten.

Die Vererbung von Metadaten durch Assets basiert auf dem Schema, das auf den Ordner der ersten Ebene in der Hierarchie angewendet wird. Wenn also ein Ordner keine Unterordner enthält, übernehmen die Assets im Ordner die Metadaten aus dem Schema, das auf den Ordner angewendet wird.

Wenn der Ordner über einen Unterordner verfügt, erben die Assets im Unterordner die Metadaten aus dem Schema, das auf die Unterordnerebene angewendet wird, wenn ein anderes Schema auf Unterordnerebene angewendet wird. Wenn jedoch kein Schema oder dasselbe Schema auf Unterordnerebene angewendet wird, erben die Assets des Unterordners die Metadaten aus dem Schema, das auf der Ebene des übergeordneten Ordners angewendet wird.

1. Klicken Sie auf [!DNL Experience Manager] -Logo und navigieren Sie dann zu **[!UICONTROL Tools > Assets > Metadatenschemata]**. Die Seite **[!UICONTROL Metadatenschema-Formulare]** wird angezeigt.
1. Aktivieren Sie das Kontrollkästchen vor einem Formular, z. B. dem Standard-Metadatenformular, und klicken oder tippen Sie auf das **[!UICONTROL Kopieren]** und speichern Sie es als benutzerdefiniertes Formular. Geben Sie einen benutzerdefinierten Namen für das Formular an, beispielsweise `my_default`. Alternativ können Sie ein benutzerdefiniertes Formular erstellen.

   ![chlimage_1-184](assets/chlimage_1-184.png)

1. Wählen Sie auf der Seite **[!UICONTROL Metadatenschema-Formulare]** das Formular `my_default` und klicken Sie dann auf **[!UICONTROL Bearbeiten]**.

1. Fügen Sie auf der Seite **[!UICONTROL Metadatenschema-Editor]** ein Textfeld in das Schemaformular ein. Fügen Sie beispielsweise ein Feld mit der Bezeichnung **[!UICONTROL Kategorie]** hinzu.

   ![chlimage_1-186](assets/chlimage_1-186.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**. Das geänderte Formular wird auf der Seite **[!UICONTROL Metadatenschema-Formulare]** aufgeführt.
1. Klicken/tippen Sie in der Symbolleiste auf **[!UICONTROL Auf Ordner anwenden]**, um die benutzerdefinierten Metadaten auf einen Ordner anzuwenden.

   ![chlimage_1-187](assets/chlimage_1-187.png)

1. Wählen Sie den Ordner aus, auf den Sie das bearbeitete Schema anwenden möchten, und klicken/tippen Sie auf **[!UICONTROL Anwenden]**.

   ![chlimage_1-188](assets/chlimage_1-188.png)

1. Wurde das andere Metadatenschema auf den Ordner angewendet, erhalten Sie eine Meldung mit der Warnung, dass Sie im Begriff sind, das vorhandene Metadatenschema zu überschreiben. Klicken Sie auf **[!UICONTROL Überschreiben]**.
1. Klicken Sie auf **[!UICONTROL OK]**, um die Erfolgsmeldung zu schließen.
1. Navigieren Sie zu dem Ordner, auf den Sie das geänderte Metadatenschema angewendet haben.

## Definieren erforderlicher Metadaten {#defining-mandatory-metadata}

Sie können Pflichtfelder auf Ordnerebene definieren, die für in den Ordner hochgeladene Assets erzwungen werden. Wenn Sie Assets mit fehlenden Metadaten für die zuvor definierten Pflichtfelder hochladen, wird in der Kartenansicht für die Assets eine visuelle Anzeige für fehlende Metadaten angezeigt.

>[!NOTE]
>
>Ein Metadatenfeld kann je nach dem Wert eines weiteren Felds als Pflichtfeld definiert werden. In der Kartenansicht [!DNL Experience Manager] zeigt keine Warnmeldung zu fehlenden Metadaten für solche obligatorischen Metadatenfelder an.

1. Klicken Sie auf [!DNL Experience Manager] -Logo und navigieren Sie dann zu **[!UICONTROL Tools > Assets > Metadatenschemata]**. Die Seite **[!UICONTROL Metadatenschema-Formulare]** wird angezeigt.
1. Speichern Sie die Standard-Metadatenformulare als benutzerdefiniertes Formular. Speichern Sie sie beispielsweise unter dem Namen `my_default`.

   ![chlimage_1-189](assets/chlimage_1-189.png)

1. Bearbeiten Sie das benutzerdefinierte Formular. Fügen Sie ein erforderliches Feld hinzu. Fügen Sie beispielsweise ein Feld mit der Bezeichnung **Kategorie** hinzu und definieren Sie es als Pflichtfeld.

   ![chlimage_1-190](assets/chlimage_1-190.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**. Das geänderte Formular wird auf der Seite **[!UICONTROL Metadatenschema-Formulare]** aufgeführt. Um die benutzerdefinierten Metadaten auf einen Ordner anzuwenden, wählen Sie das Formular aus und klicken/tippen Sie auf **[!UICONTROL Auf Ordner anwenden]** aus der Symbolleiste.

1. Navigieren Sie zum Ordner und laden Sie einige Assets mit fehlenden Metadaten für das Pflichtfeld, das Sie dem benutzerdefinierten Formular hinzugefügt haben. In der Kartenansicht für die Assets wird eine Meldung für die fehlenden Metadaten für das Pflichtfeld angezeigt.

   ![chlimage_1-192](assets/chlimage_1-192.png)

1. (Optional) Rufen Sie `http://[server]:[port]/system/console/components/` auf. Konfigurieren und aktivieren Sie die Komponente `com.day.cq.dam.core.impl.MissingMetadataNotificationJob`, die standardmäßig deaktiviert ist. Legen Sie fest, mit welcher Häufigkeit [!DNL Experience Manager] die Gültigkeit der Metadaten in den Assets überprüfen soll.
Diese Konfiguration fügt eine Eigenschaft hinzu `hasValidMetadata` in jcr:content der Assets. Verwenden dieser Eigenschaft, [!DNL Experience Manager] kann Ergebnisse in einer Suche filtern.

>[!NOTE]
>
>Wenn ein Asset nach der geplanten Prüfung hinzugefügt wird, wird das Asset erst bei der nächsten geplanten Prüfung mit `hasValidMetadata` gekennzeichnet. Die Assets werden nicht in den Zwischenergebnissen der Suche angezeigt.

>[!CAUTION]
>
>Die Überprüfung der Metadaten ist ressourcenintensiv und kann sich auf die Leistung Ihres Systems auswirken. Planen Sie die Prüfungen entsprechend. Wenn die Variable [!DNL Experience Manager] Bei der Implementierung treten Leistungsprobleme auf. Versuchen Sie, diesen Auftrag zu deaktivieren.
