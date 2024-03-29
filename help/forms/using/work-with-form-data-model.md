---
title: Arbeiten mit einem Formulardatenmodell
seo-title: Work with form data model
description: Die Datenintegration bietet einen Editor für Formulardatenmodelle zum Konfigurieren und Verwenden von Formulardatenmodellen.
seo-description: Data Integration provides form data model editor to configure and work with form data models.
uuid: cd123d42-f7cf-489d-8182-f3a01a2a4799
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integration
discoiquuid: 2ee45ac0-bc15-403a-93fc-c8592afb967d
feature: Form Data Model
exl-id: 2dcbc459-5fa3-4712-a72e-159bdbad0a61
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3166'
ht-degree: 55%

---

# Arbeiten mit einem Formulardatenmodell {#work-with-form-data-model}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die Datenintegration bietet einen Editor für Formulardatenmodelle zum Konfigurieren und Verwenden von Formulardatenmodellen.

![](do-not-localize/data-integeration.png)

Der Formulardatenmodell-Editor bietet eine intuitive Benutzeroberfläche und Werkzeuge zum Bearbeiten und Konfigurieren eines Formulardatenmodells. Mithilfe des Editors können Sie Datenmodellobjekte, Eigenschaften und Services aus verknüpften Datenquellen im Formulardatenmodell hinzufügen und konfigurieren. Darüber hinaus können Sie Datenmodellobjekte und -eigenschaften ohne Datenquellen erstellen und später mit entsprechenden Datenmodellobjekten und -eigenschaften verbinden. Sie können auch Beispieldaten für Datenmodellobjekteigenschaften generieren und bearbeiten, mit denen Sie adaptive Formulare und interaktive Kommunikation bei der Vorschau vorbefüllen können. Sie können Datenmodellobjekte und Dienste testen, die in einem Formulardatenmodell konfiguriert sind, um sicherzustellen, dass es ordnungsgemäß in Datenquellen integriert ist.

Wenn Sie mit der Forms-Datenintegration noch nicht vertraut sind und keine Datenquelle konfiguriert oder kein Formulardatenmodell erstellt haben, lesen Sie folgende Themen:

* [Datenintegration für AEM Forms](/help/forms/using/data-integration.md)
* [Konfigurieren von Datenquellen](/help/forms/using/configure-data-sources.md)
* [Erstellen des Formulardatenmodells](/help/forms/using/create-form-data-models.md)

Erfahren Sie weitere Details zu verschiedenen Aufgaben und Konfigurationen, die Sie mit dem Formulardatenmodell-Editor durchführen können.

>[!NOTE]
>
>Sie müssen Mitglied der beiden Gruppen **fdm-author** und **forms-user** sein, um Formulardatenmodelle erstellen und verwenden zu können. Wenden Sie sich an Ihren AEM Administrator, um Mitglied der Gruppen zu werden.

## Hinzufügen von Datenmodellobjekten und Services {#add-data-model-objects-and-services}

Nachdem Sie ein Formulardatenmodell mit Datenquellen erstellt haben, können Sie mit dem Formulardatenmodell-Editor Datenmodellobjekte und -Services hinzufügen, ihre Eigenschaften konfigurieren, Verknüpfungen zwischen Datenmodellobjekten erstellen sowie das Formulardatenmodell und die Services testen.

Sie können Datenmodellobjekte und Services aus verfügbaren Datenquellen zum Formulardatenmodell hinzufügen. Dabei werden hinzugefügte Datenmodellobjekte auf der Registerkarte „Modell“ und hinzugefügte Services auf der Registerkarte „Services“ angezeigt.

Hinzufügen von Datenmodellobjekten und Services:

1. Melden Sie sich bei der AEM-Autorinstanz an, navigieren Sie zu **[!UICONTROL Formulare > Datenintegrationen]** und öffnen Sie das Formulardatenmodell, in dem Sie Datenmodellobjekte hinzufügen möchten.
1. Erweitern Sie im Bereich „Data Sources“ die Datenquellen, um verfügbare Datenmodellobjekte und Services anzuzeigen.
1. Wählen Sie Datenmodellobjekte und Dienste aus, die Sie dem Formulardatenmodell hinzufügen möchten, und tippen Sie auf **[!UICONTROL Ausgewählte hinzufügen]**.

   ![selected-objects](assets/selected-objects.png)

   Auf der Registerkarte Modell wird eine grafische Darstellung aller Datenmodellobjekte und ihrer Eigenschaften angezeigt, die zum Formulardatenmodell hinzugefügt wurden. Jedes Datenmodellobjekt wird durch ein Feld im Formulardatenmodell dargestellt.

   ![model-tab](assets/model-tab.png)

   >[!NOTE]
   >
   >Sie können die Datenmodellobjektfelder durch Ziehen im Inhaltsbereich anordnen. Alle im Formulardatenmodell hinzugefügten Datenmodellobjekte werden im Bereich „Datenquellen“ ausgegraut.

   Auf der Registerkarte Services wird eine Liste der hinzugefügten Services angezeigt.

   ![services-tab](assets/services-tab.png)

   >[!NOTE]
   >
   >Das OData-Service-Metadatendokument enthält außer den Datenmodellobjekten und Services Navigationseigenschaften, die die Verknüpfung zwischen zwei Datenmodellobjekten definieren. Weitere Informationen finden Sie unter [Arbeiten mit Navigationseigenschaften von OData-Services](#work-with-navigation-properties-of-odata-services).

1. Tippen **[!UICONTROL Speichern]** , um das Formularmodellobjekt zu speichern.

   >[!NOTE]
   >
   >Sie können Dienste aufrufen, die Sie mithilfe der Regeln für adaptive Formulare auf der Registerkarte &quot;Dienste&quot;eines Formulardatenmodells konfiguriert haben. Die konfigurierten Dienste sind in der Aktion Dienste aufrufen des Regeleditors verfügbar. Weitere Informationen zur Verwendung dieser Dienste in Regeln für adaptive Formulare finden Sie unter Aufrufen von Diensten und Festlegen des Werts von Regeln in [Regeleditor](/help/forms/using/rule-editor.md).

## Erstellen von Datenmodellobjekten und untergeordneten Eigenschaften {#create-data-model-objects-and-child-properties}

### Erstellen von Datenmodellobjekten {#create-data-model-objects}

Sie können zwar Datenmodellobjekte aus konfigurierten Datenquellen hinzufügen, aber auch Datenmodellobjekte oder Entitäten ohne Datenquellen erstellen. Dies ist insbesondere dann hilfreich, wenn Sie im Formulardatenmodell keine Datenquellen konfiguriert haben.

So erstellen Sie ein Datenmodellobjekt ohne Datenquellen:

1. Melden Sie sich bei der AEM-Autoreninstanz an und navigieren Sie zu **[!UICONTROL Forms > Datenintegrationen]** und öffnen Sie das Formulardatenmodell, in dem Sie ein Datenmodellobjekt oder eine Entität erstellen möchten.
1. Tippen Sie auf **[!UICONTROL Entität erstellen]**.
1. Geben Sie im Dialog Datenmodell erstellen einen Namen für das Datenmodell ein und tippen Sie auf **[!UICONTROL Hinzufügen]**. Ein Datenmodellobjekt wird dem Formulardatenmodell hinzugefügt. Beachten Sie, dass das neu hinzugefügte Datenmodellobjekt nicht an eine Datenquelle gebunden ist und keine Eigenschaften aufweist, wie in der folgenden Abbildung dargestellt.

   ![new-entity](assets/new-entity.png)

Als Nächstes können Sie untergeordnete Eigenschaften in ungebundenen Datenmodellobjekten hinzufügen.

### Hinzufügen von untergeordneten Eigenschaften {#child-properties}

Mit dem Formulardatenmodell-Editor können Sie untergeordnete Eigenschaften in einem Datenmodellobjekt erstellen. Die Eigenschaft ist bei der Erstellung an keine Eigenschaft in einer Datenquelle gebunden. Sie können die untergeordnete Eigenschaft später mit einer anderen Eigenschaft im übergeordneten Datenmodellobjekt verknüpfen.

Erstellen einer untergeordneten Eigenschaft:

1. Wählen Sie in einem Formulardatenmodell ein Datenmodellobjekt aus und tippen Sie auf **[!UICONTROL Untergeordnete Eigenschaft erstellen]**.
1. Im **[!UICONTROL Untergeordnete Eigenschaft erstellen]** Geben Sie einen Namen und einen Datentyp für die Eigenschaft in der **[!UICONTROL Name]** und **[!UICONTROL Typ]** angegeben. Sie können optional einen Titel und eine Beschreibung für die Eigenschaft angeben.
1. Aktivieren Sie &quot;Berechnet&quot;, wenn die Eigenschaft eine berechnete Eigenschaft ist. Der Wert einer berechneten Eigenschaft wird basierend auf einer Regel oder einem Ausdruck ausgewertet. Weitere Informationen finden Sie unter [Eigenschaften bearbeiten](#edit-properties).
1. Wenn das Datenmodellobjekt an eine Datenquelle gebunden ist, wird die hinzugefügte untergeordnete Eigenschaft automatisch an die Eigenschaft des übergeordneten Datenmodellobjekts mit demselben Namen und Datentyp gebunden.

   Um eine untergeordnete Eigenschaft manuell mit einer Datenmodellobjekteigenschaft zu verknüpfen, tippen Sie auf das Symbol &quot;Durchsuchen&quot;neben dem **[!UICONTROL Bindungsverweis]** -Feld. Die **[!UICONTROL Objekt auswählen]** enthält alle Eigenschaften des übergeordneten Datenmodellobjekts. Wählen Sie eine Eigenschaft aus, an die gebunden werden soll, und tippen Sie auf das Häkchen-Symbol. Beachten Sie, dass Sie nur eine Eigenschaft des gleichen Datentyps wie die untergeordnete Eigenschaft auswählen können.

1. Tippen Sie auf **[!UICONTROL Fertig]**, um die untergeordnete Eigenschaft zu speichern, und dann auf **[!UICONTROL Speichern]**, um das Formulardatenmodell zu speichern. Die untergeordnete Eigenschaft wird jetzt dem Datenmodellobjekt hinzugefügt.

Nachdem Sie Datenmodellobjekte und -eigenschaften erstellt haben, können Sie weiterhin adaptive Formulare und interaktive Kommunikation basierend auf dem Formulardatenmodell erstellen. Wenn später Datenquellen verfügbar und konfiguriert sind, können Sie das Formulardatenmodell mit Datenquellen verknüpfen. Die Bindung wird automatisch in zugeordneten adaptiven Formularen und interaktiver Kommunikation aktualisiert. Weitere Informationen zum Erstellen adaptiver Formulare und interaktiver Kommunikationen mithilfe des Formulardatenmodells finden Sie unter [Verwenden des Formulardatenmodells](/help/forms/using/using-form-data-model.md).

### Binden von Datenmodellobjekten und -eigenschaften {#bind-data-model-objects-and-properties}

Wenn die Datenquellen, die Sie in das Formulardatenmodell integrieren möchten, verfügbar sind, können Sie sie dem Formulardatenmodell hinzufügen, wie in [Aktualisieren von Datenquellen](/help/forms/using/create-form-data-models.md#update) beschrieben. Führen Sie dann die folgenden Schritte aus, um die ungebundenen Datenmodellobjekte und -eigenschaften zu binden:

1. Wählen Sie im Formulardatenmodell die ungebundene Datenquelle aus, die Sie an eine Datenquelle binden möchten.
1. Tippen Sie auf **[!UICONTROL Eigenschaften bearbeiten]**.
1. Tippen Sie im Bedienfeld **[!UICONTROL Eigenschaften bearbeiten]** auf das Suchsymbol neben dem Feld **[!UICONTROL Bindung]**. Er öffnet die **[!UICONTROL Objekt auswählen]** -Dialogfeld, das Datenquellen auflistet, die im Formulardatenmodell hinzugefügt wurden.

   ![select-object](assets/select-object.png)

1. Erweitern Sie die Datenquellenstruktur, wählen Sie ein Datenmodellobjekt aus, an das Sie eine Bindung herstellen möchten, und tippen Sie auf das Häkchen-Symbol.
1. Tippen Sie auf **[!UICONTROL Fertig]**, um die Eigenschaften zu speichern, und dann auf **[!UICONTROL Speichern]**, um das Formulardatenmodell zu speichern. Das Datenmodellobjekt ist jetzt an eine Datenquelle gebunden. Beachten Sie, dass das Datenmodellobjekt nicht mehr als ungebunden markiert ist.

   ![bound-model-object](assets/bound-model-object.png)

## Konfigurieren von Services {#configure-services}

Um Daten für ein Datenmodellobjekt zu lesen und zu schreiben, gehen Sie folgendermaßen vor, um Lese- und Schreib-Services zu konfigurieren:

1. Aktivieren Sie das Kontrollkästchen oben in einem Datenmodellobjekt, um es auszuwählen, und tippen Sie auf **[!UICONTROL Eigenschaften bearbeiten]**.

   ![edit-properties](assets/edit-properties.png)

   Bearbeiten von Eigenschaften, um Lese- und Schreib-Services für Datenmodellobjekte zu konfigurieren

   Der Dialog Eigenschaften bearbeiten wird geöffnet.

   ![edit-properties-2](assets/edit-properties-2.png)

   Dialog „Eigenschaften bearbeiten“

   >[!NOTE]
   >
   >Das OData-Service-Metadatendokument enthält außer den Datenmodellobjekten und Services Navigationseigenschaften, die die Verknüpfung zwischen zwei Datenmodellobjekten definieren. Wenn Sie eine OData-Dienst-Datenquelle zu einem Formulardatenmodell hinzufügen, steht im Formulardatenmodell ein Dienst für alle Navigationseigenschaften in einem Datenmodellobjekt zur Verfügung. Mithilfe dieses Service können Sie die Navigationseigenschaften des entsprechenden Datenmodellobjekts lesen.
   >
   >Weitere Informationen zur Verwendung des Service finden Sie unter [Arbeiten mit Navigationseigenschaften von OData-Services](#work-with-navigation-properties-of-odata-services).

1. Umschalten **[!UICONTROL Objekt auf oberster Ebene]** , um anzugeben, ob das Datenmodellobjekt ein Modellobjekt der obersten Ebene ist.

   Datenmodellobjekte, die in einem Formulardatenmodell konfiguriert sind, stehen im Inhaltsbrowser eines adaptiven Formulars auf der Registerkarte Datenmodellobjekte zur Verwendung auf der Registerkarte Datenmodellobjekte zur Verfügung, die auf dem Formulardatenmodell basiert. Wenn Sie eine Verknüpfung zwischen zwei Datenmodellobjekten hinzufügen, wird das Ziel-Datenmodellobjekt auf der Registerkarte Datenmodellobjekte unter dem Ausgangs-Datenmodellobjekt geschachtelt. Wenn das verschachtelte Datenmodell ein Objekt der obersten Ebene ist, wird es auch separat auf der Registerkarte Datenmodellobjekte angezeigt. Daher werden Ihnen zwei Einträge angezeigt, eine innerhalb und eine andere außerhalb der verschachtelten Hierarchie, was Formularautoren verwirren könnte. Damit das zugeordnete Datenmodellobjekt nur in der verschachtelten Hierarchie angezeigt wird, deaktivieren Sie die Eigenschaft „Top Level Object“. 

1. Wählen Sie Lese- und Schreib-Services für die ausgewählten Datenmodellobjekte aus. Die Argumente für die Services werden angezeigt.

   ![read-write-services](assets/read-write-services.png)

   Für die Mitarbeiterdatenquelle konfigurierte Lese- und Schreib-Services

1. Tippen Sie auf ![aem_6_3_edit](assets/aem_6_3_edit.png) für das Argument des Lese-Service, um dieses an ein Benutzerprofilattribut, ein Anforderungsattribut oder einen Literalwert zu binden, und geben Sie den Bindungswert an. Er bindet das Dienstargument an das angegebene Bindungsattribut oder den angegebenen Literalwert, der an den Dienst als Argument übergeben wird, um mit dem angegebenen Wert verknüpfte Details aus der Datenquelle abzurufen.

   In diesem Beispiel wird die `id` Das -Argument nimmt den Wert der `empid` -Attribut des Benutzerprofils und übergeben Sie es als Argument an den Lesedienst. Sie liest Werte der zugehörigen Eigenschaften aus der `employee` Datenmodellobjekt für das angegebene `empid`. Wenn Sie also 00250 im `empid` im Formular lesen, liest der Lesedienst Details zum Mitarbeiter mit der Mitarbeiter-ID 00250.

   Darüber hinaus können Sie ein Argument als obligatorisch oder optional festlegen.

   ![edit-argument](assets/edit-argument.png)

   Binden des id-Arguments an das empid-Attribut AEM Benutzerprofils

1. Tippen Sie auf **[!UICONTROL Fertig]**, um das Argument zu speichern, dann auf **[!UICONTROL Fertig]**, um die Eigenschaften zu speichern, und schließlich auf **[!UICONTROL Speichern]**, um das Formulardatenmodell zu speichern.

## Hinzufügen von Verknüpfungen {#add-associations}

In der Regel gibt es Verbindungen, die zwischen Datenmodellobjekten in einer Datenquelle erstellt werden. Die Zuordnung kann 1:1 oder 1:n sein. Beispielsweise kann einem Mitarbeiter mehrere abhängige Elemente zugeordnet sein. Dies wird als Eins-zu-Viele-Verknüpfung bezeichnet und in der Form `1:n` auf der Linie dargestellt, die die zugeordneten Datenmodellobjekte verbindet. Wenn jedoch eine Verknüpfung einen eindeutigen Mitarbeiternamen für eine gegebene Mitarbeiter-ID zurückgibt, wird dies als Eins-zu-Eins-Verknüpfung bezeichnet.

Wenn Sie verknüpfte Datenmodellobjekte in einer Datenquelle einem Formulardatenmodell hinzufügen, werden ihre Verknüpfungen beibehalten und mit Pfeillinien verbunden angezeigt. In einem Formulardatenmodell können Sie Verknüpfungen zwischen Datenmodellobjekten über unterschiedliche Datenquellen hinweg hinzufügen.

>[!NOTE]
>
>Vordefinierte Verknüpfungen in einer JDBC-Datenquelle werden im Formulardatenmodell nicht beibehalten. Sie müssen sie manuell erstellen.

So fügen Sie eine Verknüpfung hinzu:

1. Aktivieren Sie das Kontrollkästchen oben in einem Datenmodellobjekt, um es auszuwählen, und tippen Sie auf **[!UICONTROL Verknüpfung hinzufügen]**. Das Dialogfeld „Verknüpfung hinzufügen“ wird geöffnet.

   ![add-associated](assets/add-association.png)

   >[!NOTE]
   >
   >Das OData-Service-Metadatendokument enthält außer den Datenmodellobjekten und Services Navigationseigenschaften, die die Verknüpfung zwischen zwei Datenmodellobjekten definieren. Sie können diese Navigationseigenschaften verwenden, wenn Sie Verknüpfungen im Formulardatenmodell hinzufügen. Weitere Informationen finden Sie unter [Arbeiten mit Navigationseigenschaften von OData-Services](#work-with-navigation-properties-of-odata-services).

   Das Dialogfeld „Verknüpfung hinzufügen“ wird geöffnet.

   ![add-associated-2](assets/add-association-2.png)

   Dialogfeld &quot;Verknüpfung hinzufügen&quot;

1. Im Bereich Zuordnung hinzufügen :

   * Geben Sie einen Titel für die Verknüpfung an.
   * Wählen Sie den Verknüpfungstyp: Eins-zu-Eins oder Eins-zu-Viele.
   * Wählen Sie das Datenmodellobjekt aus, mit dem verknüpft werden soll.
   * Wählen Sie den Lese-Service, der die Daten aus dem ausgewählten Modellobjekt lesen soll. Das Argument des Lese-Service wird angezeigt. Bearbeiten Sie, um das Argument bei Bedarf zu ändern und es an die Eigenschaft des zu verknüpfenden Datenmodellobjekts zu binden.

   Im folgenden Beispiel ist `dependentid` das Standardargument für den Lese-Service des Datenmodellobjekts „Angehörige“.

   ![add-associated-example](assets/add-association-example.png)

   Standardargument für den Lese-Service für „Angehörige“ ist „dependentid“

   Das Argument muss allerdings eine mit dem verknüpfenden Datenmodellobjekt gemeinsame Eigenschaft sein, in diesem Beispiel `Employeeid`. Daher muss das Argument `Employeeid` an die Eigenschaft `id` des Mitarbeiter-Datenmodellobjekts gebunden sein, damit die verknüpften Informationen zu Angehörigen aus dem Datenmodellobjekt für Angehörige abgerufen werden können.

   ![add-associated-example-2](assets/add-association-example-2.png)

   Aktualisiertes Argument und Bindung

   Tippen **[!UICONTROL Fertig]** , um das -Argument zu speichern.

1. Tippen **[!UICONTROL Fertig]** , um die Zuordnung zu speichern, und dann **[!UICONTROL Speichern]** , um das Formulardatenmodell zu speichern.
1. Wiederholen Sie die Schritte, um nach Bedarf weitere Zuordnungen zu erstellen.

>[!NOTE]
>
>Die hinzugefügte Verknüpfung wird im Objektfeld des Datenmodells mit dem angegebenen Titel und einer Linie angezeigt, die die verknüpften Datenmodellobjekte verbindet.
>
>Sie können eine Verknüpfung bearbeiten, indem Sie das Kontrollkästchen neben der Verknüpfung auswählen und auf **[!UICONTROL Verknüpfung bearbeiten]** tippen.

![added-association](assets/added-association.png)

## Bearbeiten von Eigenschaften {#properties}

Sie können Eigenschaften von Datenmodellobjekten, Eigenschaften sowie m Formulardatenmodell hinzugefügte Services bearbeiten.

So bearbeiten Sie Eigenschaften:

1. Aktivieren Sie im Formulardatenmodell das Kontrollkästchen neben einem Datenmodellobjekt, einer Eigenschaft oder einem Service.
1. Tippen Sie auf **[!UICONTROL Eigenschaften bearbeiten]**. Der Bereich **[!UICONTROL Eigenschaften bearbeiten]** für das Modellobjekt, die Eigenschaft oder den Service in der Auswahl wird geöffnet.

   * **Datenmodellobjekt**: Geben Sie die Lese- und Schreib-Services an und bearbeiten Sie Argumente.
   * **Eigenschaft**: Geben Sie den Typ, den Untertyp und das Format für die Eigenschaft an. Sie können auch angeben, ob die ausgewählte Eigenschaft der Primärschlüssel für das Datenmodellobjekt ist.
   * **Service**: Geben Sie das Eingabemodellobjekt, den Ausgabetyp und Argumente für den Service an. Bei einem Get-Service können Sie angeben, ob ein Array als Rückgabe erwartet wird.

   ![edit-properties-service](assets/edit-properties-service.png)

   Dialog „Eigenschaften bearbeiten“ für einen Get-Service

1. Tippen **[!UICONTROL Fertig]** zum Speichern von Eigenschaften und dann **[!UICONTROL Speichern]** , um das Formulardatenmodell zu speichern.

### Erstellen berechneter Eigenschaften {#computed}

Eine berechnete Eigenschaft ist diejenige, deren Wert anhand einer Regel oder eines Ausdrucks berechnet wird. Mithilfe einer Regel können Sie den Wert einer berechneten Eigenschaft auf eine Zeichenfolge in Textform, eine Zahl, ein Ergebnis eines mathematischen Ausdrucks oder den Wert einer anderen Eigenschaft im Formulardatenmodell festlegen.

Beispielsweise können Sie eine berechnete Eigenschaft **FullName** erstellen, deren Wert ein Ergebnis der Verkettung der vorhandenen Eigenschaften **FirstName** und **LastName** ist. Gehen Sie dazu wie folgt vor:

1. Erstellen Sie eine neue Eigenschaft mit dem Namen `FullName`, deren Datentyp „Zeichenfolge“ ist.
1. Aktivieren Sie **[!UICONTROL Berechnet]** und tippen Sie auf **[!UICONTROL Fertig]**, um die Eigenschaft zu erstellen.

   ![computed](assets/computed.png)

   Die berechnete FullName-Eigenschaft wird erstellt. Beachten Sie, dass das Symbol neben der Eigenschaft eine berechnete Eigenschaft darstellt.

   ![calculate-prop](assets/computed-prop.png)

1. Wählen Sie die FullName-Eigenschaft aus und tippen Sie auf **[!UICONTROL Regel bearbeiten]**. Ein Fenster des Regeleditors wird geöffnet.
1. Tippen Sie im Fenster des Regeleditors auf **[!UICONTROL Erstellen]**. A **[!UICONTROL Wert einstellen]** Regelfenster geöffnet.

   Wählen Sie in der Dropdownliste **[!UICONTROL Mathematischer Ausdruck]**. Weitere verfügbare Optionen sind **[!UICONTROL Formulardatenmodell-Objekt]** und **[!UICONTROL Zeichenfolge]**.

1. Wählen Sie im mathematischen Ausdruck **[!UICONTROL FirstName]** und **[!UICONTROL LastName]** in den ersten bzw. zweiten Objekten. Wählen Sie **[!UICONTROL plus]** als Operator.

   Tippen Sie auf **[!UICONTROL Fertig]** und dann auf **[!UICONTROL Schließen]**, um das Regeleditorfenster zu schließen. Die Regel sieht ähnlich der Folgenden aus:

   ![rule](assets/rule.png)

1. Tippen Sie im Formulardatenmodell auf **[!UICONTROL Speichern]**. Die berechnete Eigenschaft ist konfiguriert.

## Arbeiten mit Navigationseigenschaften von OData-Services {#work-with-navigation-properties-of-odata-services}

In OData-Services werden Navigationseigenschaften verwendet, um Zuordnungen zwischen zwei Datenmodellobjekten zu definieren. Diese Eigenschaften werden für einen Entitätstyp oder einen komplexen Typ definiert. So enthält beispielsweise im folgenden Extract aus der Metadatendatei der [TripPin](https://www.odata.org/blog/trippin-new-odata-v4-sample-service/)-OData-Beispiel-Services die Entität „Person“ drei Navigationseigenschaften: „Friends“, „BestFriend“ und „Trips“.

Weitere Informationen zu Navigationseigenschaften finden Sie unter [OData-Dokumentation](https://docs.oasis-open.org/odata/odata/v4.0/errata03/os/complete/part3-csdl/odata-v4.0-errata03-os-part3-csdl-complete.html#_Toc453752536).

```xml
<edmx:Edmx xmlns:edmx="https://docs.oasis-open.org/odata/ns/edmx" Version="4.0">
<script/>
<edmx:DataServices>
<Schema xmlns="https://docs.oasis-open.org/odata/ns/edm" Namespace="Microsoft.OData.Service.Sample.TrippinInMemory.Models">
<EntityType Name="Person">
<Key>
<PropertyRef Name="UserName"/>
</Key>
<Property Name="UserName" Type="Edm.String" Nullable="false"/>
<Property Name="FirstName" Type="Edm.String" Nullable="false"/>
<Property Name="LastName" Type="Edm.String"/>
<Property Name="MiddleName" Type="Edm.String"/>
<Property Name="Gender" Type="Microsoft.OData.Service.Sample.TrippinInMemory.Models.PersonGender" Nullable="false"/>
<Property Name="Age" Type="Edm.Int64"/>
<Property Name="Emails" Type="Collection(Edm.String)"/>
<Property Name="AddressInfo" Type="Collection(Microsoft.OData.Service.Sample.TrippinInMemory.Models.Location)"/>
<Property Name="HomeAddress" Type="Microsoft.OData.Service.Sample.TrippinInMemory.Models.Location"/>
<Property Name="FavoriteFeature" Type="Microsoft.OData.Service.Sample.TrippinInMemory.Models.Feature" Nullable="false"/>
<Property Name="Features" Type="Collection(Microsoft.OData.Service.Sample.TrippinInMemory.Models.Feature)" Nullable="false"/>
<NavigationProperty Name="Friends" Type="Collection(Microsoft.OData.Service.Sample.TrippinInMemory.Models.Person)"/>
<NavigationProperty Name="BestFriend" Type="Microsoft.OData.Service.Sample.TrippinInMemory.Models.Person"/>
<NavigationProperty Name="Trips" Type="Collection(Microsoft.OData.Service.Sample.TrippinInMemory.Models.Trip)"/>
</EntityType>
```

Wenn Sie einen OData-Service in einem Formulardatenmodell konfigurieren, werden alle Navigationseigenschaften in einem Entitäten-Container über einen Service im Formulardatenmodell bereitgestellt. In diesem Beispiel können im OData-Service „TripPin“ die drei Navigationseigenschaften des Entitäten-Containers `Person` über ein und denselben `GET LINK`-Service im Formulardatenmodell gelesen werden.

Im Folgenden wird der Service `GET LINK of Person /People` im Formulardatenmodell hervorgehoben. Dies ist ein kombinierter Service für die drei Navigationseigenschaften in der Entität `Person` des OData-Service „TripPin“.

![nav-prop-service](assets/nav-prop-service.png)

Sobald Sie den `GET LINK`-Service auf der Registerkarte „Services“ im Formulardatenmodell hinzufügen, können Sie die Eigenschaften bearbeiten, um das Modellobjekt für die Ausgabe und die im Service zu verwendende Navigationseigenschaft zu wählen. Im folgenden Beispiel nutzt der Service `GET LINK of Person /People` die Angabe „Trip“ als Ausgabemodellobjekt und die Navigationseigenschaft als „Trips“.

![edit-prop-nav-prop](assets/edit-prop-nav-prop.png)

>[!NOTE]
>
>Die im Feld **[!UICONTROL Standardwert]** des Arguments **NavigationPropertyName** verfügbaren Werte hängen vom Status des Schalters **[!UICONTROL Rückgabe-Array?]** ab. Wenn sie aktiviert ist, werden die Navigationseigenschaften des Sammlungstyps angezeigt.

In diesem Beispiel können Sie auch „Person“ als Ausgabemodellobjekt und als Argument für die Navigationseigenschaft „Friends“ oder „BestFriend“ wählen (abhängig davon, ob **[!UICONTROL Rückgabe-Array?]** aktiviert oder deaktiviert ist).

![edit-prop-nav-prop2](assets/edit-prop-nav-prop2.png)

Darüber hinaus können Sie beim Hinzufügen von Verknüpfungen im Formulardatenmodell einen `GET LINK`-Service auswählen und die entsprechenden Navigationseigenschaften konfigurieren. Damit eine Navigationseigenschaft ausgewählt werden kann, müssen Sie jedoch darauf achten, dass im Feld **[!UICONTROL Bindung an]** der Wert **[!UICONTROL Literal]** eingestellt ist.

![add-associated-nav-prop](assets/add-association-nav-prop.png)

## Generieren und Bearbeiten von Beispieldaten {#sample}

Mit dem Formulardatenmodell-Editor können Sie Beispieldaten für alle Datenmodellobjekteigenschaften, einschließlich berechneter Eigenschaften, in einem Formulardatenmodell generieren. Es handelt sich um einen Satz zufälliger Werte, die dem für jede Eigenschaft konfigurierten Datentyp entsprechen. Sie können auch Daten bearbeiten und speichern, die auch dann beibehalten werden, wenn Sie die Beispieldaten neu generieren.

Gehen Sie wie folgt vor, um Beispieldaten zu generieren und zu bearbeiten:

1. Öffnen Sie ein Formulardatenmodell und tippen Sie auf **[!UICONTROL Beispieldaten bearbeiten]**. Es werden Beispieldaten im Fenster „Beispieldaten bearbeiten“ generiert und angezeigt.

   ![sample-data](assets/sample-data.png)

1. Bearbeiten Sie im Fenster **[!UICONTROL Beispieldaten bearbeiten]** die Daten nach Bedarf und tippen Sie auf **[!UICONTROL Speichern]**.

Als Nächstes können Sie die Beispieldaten verwenden, um interaktive Kommunikation basierend auf dem Formulardatenmodell vorab auszufüllen und zu testen. Weitere Informationen finden Sie unter [Verwenden eines Formulardatenmodells](/help/forms/using/using-form-data-model.md).

## Testen von Datenmodellobjekten und Services {#test-data-model-objects-and-services}

Ihr Formulardatenmodell ist konfiguriert. Bevor Sie es jedoch verwenden, sollten Sie testen, ob die konfigurierten Datenmodellobjekte und Dienste erwartungsgemäß funktionieren. Testen von Datenmodellobjekten und Services

1. Wählen Sie ein Datenmodellobjekt oder einen Dienst im Formulardatenmodell aus und tippen Sie auf **[!UICONTROL Testmodell-Objekt]** oder **[!UICONTROL Testdienst]** zurück.

   Das Fenster „Formulardatenmodell testen“ wird geöffnet.

   ![test-data-model](assets/test-data-model.png)

1. Wählen Sie im Fenster Formulardatenmodell testen unter „Eingabe“ das zu testende Datenmodellobjekt bzw. den Service.

1. Geben Sie einen Argumentwert im Testcode an und tippen Sie auf **[!UICONTROL Test]**. Bei einem erfolgreichen Test wird die Ausgabe im Bereich Ausgabe zurückgegeben.

   ![test-data-model-2](assets/test-data-model-2.png)

Auf ähnliche Weise können Sie andere Datenmodellobjekte und Service im Formulardatenmodell testen.

## Nächste Schritte {#next-steps}

Sie verfügen über ein funktionierendes Formulardatenmodell, das jetzt für die Verwendung in adaptiven Formularen und interaktiven Kommunikations-Workflows bereit ist. Weitere Informationen finden Sie unter [Verwenden eines Formulardatenmodells](/help/forms/using/using-form-data-model.md).
