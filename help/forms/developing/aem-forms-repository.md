---
title: Arbeiten mit AEM Forms Repository
seo-title: Working with AEM Forms Repository
description: Verwalten Sie das AEM Forms-Repository zum Erstellen von Ordnern, Schreiben, Auflisten, Lesen, Aktualisieren von Ressourcen und Suchen von Ressourcen mithilfe der Java-API und der Web Service-API. Erfahren Sie außerdem, wie Sie Ressourcenbeziehungen erstellen, Ressourcen sperren und löschen können.
seo-description: Manage AEM Forms repository to create folders, write, list, read, update resources, and search resources using the Java API and Web Service API. In addition, learn how to create resource relationships, lock and delete resources.
uuid: 6ead49f9-ca0d-4ee4-86a6-0a9ced6ec4f8
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: d2c95881-6c02-4e34-85af-84607df54287
role: Developer
exl-id: e006c32b-edff-40f2-8c0a-228008dcf03a
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '9110'
ht-degree: 2%

---

# Arbeiten mit AEM Forms Repository {#working-with-aem-forms-repository}

**Über den Repository-Dienst**

Der Repository-Dienst stellt Dienste zur Ressourcenspeicherung und -verwaltung für AEM Forms bereit. Wenn Entwickler eine *AEM Forms* -Anwendung können sie die Assets im Repository anstatt im Dateisystem bereitstellen. Die Elemente können alle Typen von Zusätzen umfassen, darunter XML-Formulare, PDF-Formulare (einschließlich Acrobat-Formularen), Formularfragmente, Bilder, Profile, Richtlinien, SWF-Dateien, DDX-Dateien, XML-Schemas, WSDL-Dateien und Testdaten.

Betrachten Sie beispielsweise die folgende Forms-Anwendung mit dem Namen *Anwendungen/FormsApplication*:

![ww_ww_formrepository](assets/ww_ww_formrepository.png)

Beachten Sie, dass sich im FormsFolder eine Datei mit dem Namen &quot;Loan.xdp&quot;befindet. Um auf diesen Formularentwurf zuzugreifen, geben Sie den vollständigen Pfad an (einschließlich der Version): `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.

>[!NOTE]
>
>Informationen zum Erstellen einer Forms-Anwendung mit Workbench finden Sie unter [Workbench-Hilfe](https://www.adobe.com/go/learn_aemforms_workbench_63).

Der Pfad zu einer Ressource im AEM Forms-Repository lautet:

`Applications/Application-name/Application-version/Folder.../Filename`

Die folgenden Werte zeigen einige Beispiele für URI-Werte:

* Applications/AppraisalReport/1.0/Forms/FullForm.xdp
* Applications/AnotherApp/1.1/Assets/picture.jpg
* Applications/SomeApp/2.0/Resources/Data/XSDs/MyData.xsd

>[!NOTE]
>
>Sie können das AEM Forms-Repository mithilfe eines Webbrowsers durchsuchen. Um das Repository zu durchsuchen, geben Sie die folgende URL in einen Webbrowser ein https://[Servername]:[Serverport]/repository. Mithilfe eines Webbrowsers können Sie die Schnellstartergebnisse überprüfen, die mit dem Abschnitt Arbeiten mit dem AEM Forms-Repository verknüpft sind. Wenn Sie beispielsweise Inhalte zum AEM Forms-Repository hinzufügen, können Sie den Inhalt in einem Webbrowser anzeigen. (Siehe [Schnellstart (SOAP-Modus): Ressource mit der Java-API schreiben](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-writing-a-resource-using-the-java-api).

Die Repository-API bietet eine Reihe von Vorgängen, mit denen Sie Informationen aus dem Repository speichern und abrufen können. Beispielsweise können Sie eine Liste von Ressourcen abrufen oder spezifische Ressourcen abrufen, die im Repository gespeichert sind, wenn eine Ressource im Rahmen der Verarbeitung einer Anwendung benötigt wird.

>[!NOTE]
>
>Die Repository-API kann nicht für die Interaktion mit Content Services (nicht mehr unterstützt) verwendet werden. Um mit Content Services (nicht mehr unterstützt) zu interagieren, verwenden Sie die Document Management-API.

Mithilfe der Repository-Dienst-API können Sie die folgenden Aufgaben ausführen:

* Erstellen von Ordnern. Siehe [Erstellen von Ordnern](aem-forms-repository.md#creating-folders).
* Schreiben Sie Ressourcen und ihre Eigenschaften. Siehe [Schreiben von Ressourcen](aem-forms-repository.md#writing-resources).
* Auflisten von Ressourcen in einer bestimmten Sammlung oder im Zusammenhang mit anderen Ressourcen Siehe [Auflisten von Ressourcen](aem-forms-repository.md#listing-resources).
* Lesen Sie Ressourcen und ihre Eigenschaften. Siehe [Lesen von Ressourcen](aem-forms-repository.md#reading-resources).
* Aktualisieren Sie die Ressourcen und ihre Eigenschaften. Siehe [Aktualisieren von Ressourcen](aem-forms-repository.md#updating-resources).
* Suchen Sie nach Ressourcen, einschließlich ihres Verlaufs, der zugehörigen Ressourcen und Eigenschaften. Siehe [Suchen nach Ressourcen](aem-forms-repository.md#searching-for-resources).
* Geben Sie Beziehungen zwischen Ressourcen an. Siehe [Erstellen von Ressourcenbeziehungen](aem-forms-repository.md#creating-resource-relationships).
* Verwalten Sie die Zugriffskontrolle für Ressourcen, einschließlich Sperren und Entsperren von Ressourcen sowie Lesen und Schreiben von Zugriffssteuerungslisten (ACLs). Siehe [Ressourcen sperren](aem-forms-repository.md#locking-resources).
* Löschen Sie Ressourcen und ihre Eigenschaften. Siehe [Löschen von Ressourcen](aem-forms-repository.md#deleting-resources).

>[!NOTE]
>
>Mithilfe der Repository-API können Sie die Zugriffskontrolle auf Ressourcen nicht verwalten, nach Ressourcen suchen oder mithilfe eines ECM-Repositorys Ressourcenbeziehungen angeben.

>[!NOTE]
>
>Wenn eine verschlüsselte PDF in das Repository geschrieben wird, kann die automatisierte Beziehungsextraktionsfunktion nicht verwendet werden. Andernfalls kann eine verschlüsselte PDF im Repository gespeichert und später abgerufen werden. Der Abruf kann wählen, ob die PDF entschlüsselt werden soll, nachdem sie aus dem Repository abgerufen wurde.

>[!NOTE]
>
>Weitere Informationen zum Repository-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Erstellen von Ordnern {#creating-folders}

Ordner (Ressourcensammlungen) werden zum Speichern von Objekten (Dateien oder Ressourcen) in organisierten Gruppierungen verwendet. Ordner können Ressourcen und andere Ordner enthalten, die auch als Unterordner bezeichnet werden. Ressourcen können jeweils nur in einem Ordner gespeichert werden.

Dateien erben Zugriffssteuerungslisten (ACLs) aus Ordnern, und Unterordner erben ACLs von ihren übergeordneten Ordnern. Daher müssen die übergeordneten Ordner vorhanden sein, bevor Sie untergeordnete Ordner erstellen können. Mit der IDE können Sie nur auf Ordner-für-Ordner-Basis interagieren, nicht auf Datei-für-Datei-Basis. Sie können keine Versionsordner verändern, und dies ist nicht erforderlich. ein Ordner selbst keine Daten enthält. Stattdessen handelt es sich lediglich um einen Container für Ressourcen, die Daten enthalten. Die standardmäßige ACL ist eine Berechtigung auf Systemebene. Das bedeutet, dass Benutzer über Berechtigungen auf Systemebene (Lesen, Schreiben, Durchlaufen, Verwalten von ACLs) verfügen müssen, bis ihnen jemand Berechtigungen für einen bestimmten Ordner erteilt. ACLs funktionieren nur in der IDE.

>[!NOTE]
>
>Weitere Informationen zum Repository-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Gehen Sie wie folgt vor, um einen Ordner zu erstellen:

1. Projektdateien einschließen.
1. Erstellen Sie den Service-Client.
1. Erstellen Sie den Ordner.
1. Schreiben Sie den Ordner in das Repository.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxy-Dateien ein.

**Dienstclient erstellen**

Bevor Sie eine Ressourcensammlung programmgesteuert erstellen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch Erstellen eines Service-Clients erreicht.

**Erstellen Sie den Ordner**

Rufen Sie die Methode des Repository-Dienstes auf, um die Ressourcenerfassung zu erstellen und die Ressourcenerfassung mit identifizierenden Informationen, einschließlich UUID, Ordnername und Beschreibung, zu füllen.

**Den Ordner in das Repository schreiben**

Rufen Sie die Methode des Repository-Dienstes auf, um die Ressourcenerfassung zu schreiben und den URI des Zielordners anzugeben.

**Siehe auch**

[Erstellen von Ordnern mit der Java-API](aem-forms-repository.md#create-folders-using-the-java-api)

[Erstellen von Ordnern mit der Webdienst-API](aem-forms-repository.md#create-folders-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service-API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Erstellen von Ordnern mit der Java-API {#create-folders-using-the-java-api}

Erstellen Sie mithilfe der Repository Service-API (Java) einen Ordner:

1. Projektdateien einschließen

   Fügen Sie Projektdateien in den Klassenpfad Ihres Java-Projekts ein.

1. Dienstclient erstellen

   Erstellen Sie eine `ResourceRepositoryClient` -Objekt mithilfe des -Konstruktors und Übergeben eines `ServiceClientFactory` -Objekt, das Verbindungseigenschaften enthält.

1. Erstellen Sie den Ordner

   Um eine Ressourcensammlung zu erstellen, müssen Sie zunächst eine `com.adobe.repository.infomodel.bean.RepositoryInfomodelFactoryBean` -Objekt.

   Rufen Sie die `repositoryInfomodelFactoryBean` -Objekt `newResourceCollection` und übergeben Sie die folgenden Parameter:

   * A `com.adobe.repository.infomodel.Id` UUID-Kennung, die der Ressource zugewiesen werden soll.
   * A `com.adobe.repository.infomodel.Lid` UUID-Kennung, die der Ressource zugewiesen werden soll.
   * A `java.lang.String` mit dem Namen der Ressourcensammlung. Beispiel: `FormsFolder`.

   Die Methode gibt eine `com.adobe.repository.infomodel.bean.ResourceCollection` -Objekt, das den neuen Ordner darstellt.

   Legen Sie die Beschreibung des Ordners mithilfe der `setDescription` -Methode verwenden und den folgenden Parameter übergeben:

   * A `String` beschreibt die Ressourcenkollektion. In diesem Beispiel `"test Folder"` verwendet wird `.`


1. Den Ordner in das Repository schreiben

   Rufen Sie die `ResourceRepositoryClient` -Objekt `writeResource` -Methode verwenden und den URI des Ordners und die `ResourceCollection` -Objekt. Der URI zum Ordner kann beispielsweise der folgende Wert sein: `/Applications/FormsApplication/1.0/`.

   Die Methode gibt eine Instanz der neu erstellten zurück `com.adobe.repository.infomodel.bean.Resource` -Objekt. Sie können beispielsweise den Kennungswert der neuen Ressource abrufen, indem Sie die `com.adobe.repository.infomodel.bean.Resource` -Objekt `getId` -Methode.

**Siehe auch**

[Erstellen von Ordnern](aem-forms-repository.md#creating-folders)

[Schnellstart (SOAP-Modus): Erstellen eines Ordners mit der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-creating-a-folder-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Erstellen von Ordnern mit der Webdienst-API {#create-folders-using-the-web-service-api}

Erstellen Sie mithilfe der Repository Service-API (Webdienst) einen Ordner:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Repository-WSDL mit base64 verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Dienstclient erstellen

   Erstellen Sie mithilfe der Microsoft .NET-Client-Assembly eine `RepositoryServiceService` -Objekt durch Aufrufen des Standardkonstruktors. Festlegen der `Credentials` -Eigenschaft mithilfe einer `System.Net.NetworkCredential` -Objekt, das den Benutzernamen und das Kennwort enthält.

1. Erstellen Sie den Ordner

   Erstellen Sie den Ordner mit dem Standardkonstruktor für `ResourceCollection` -Klasse und übergeben Sie die folgenden Parameter:

   * Ein `Id` -Objekt, das durch Aufrufen des Standardkonstruktors für die `Id` -Klasse und den `Resource` -Objekt `id` -Feld.
   * Ein `Lid` -Objekt, das durch Aufrufen des Standardkonstruktors für die `Lid` -Klasse und den `Resource` -Objekt `lid` -Feld.
   * Eine Zeichenfolge, die den Namen der Ressourcensammlung enthält, die der `Resource` -Objekt `name` -Feld. Der in diesem Beispiel verwendete Name lautet `"testfolder"`.
   * Eine Zeichenfolge, die die Beschreibung der Ressourcensammlung enthält, die der `Resource` -Objekt `description` -Feld. Die in diesem Beispiel verwendete Beschreibung lautet `"test folder"`.

1. Den Ordner in das Repository schreiben

   Rufen Sie die `RepositoryServiceService` -Objekt `writeResource` -Methode verwenden und die folgenden Parameter übergeben:

   * Der Pfad, in dem der Ordner erstellt werden soll.
   * Die `ResourceCollection` -Objekt, das den Ordner darstellt.
   * Pass `null` für die beiden anderen Parameter.

**Siehe auch**

[Erstellen von Ordnern](aem-forms-repository.md#creating-folders)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Schreiben von Ressourcen {#writing-resources}

Sie können Ressourcen an einem bestimmten Speicherort im Repository erstellen. Die natürliche Dateigröße unterliegt Datenbankbeschränkungen und Sitzungszeitlimit. Für die Standardkonfiguration sind Dateien auf 25 MB beschränkt. Um die maximale Dateigröße zu erhöhen oder zu verringern, müssen Sie die Datenbankkonfiguration ändern.

Das Schreiben von Ressourcen entspricht dem Speichern von Daten im Repository. Nachdem Sie eine Ressource in das Repository geschrieben haben, wird sie für alle Clients im Repository-Ökosystem zugänglich. Wenn Sie Ressourcen wie XML-Schemata, XDP-Dateien und XSD-Dateien in das Repository schreiben, werden die Inhalte basierend auf dem MIME-Typ analysiert. Wenn der MIME-Typ unterstützt wird, bestimmt der Parser, ob eine implizite Beziehung zu anderen Inhalten besteht. Wenn beispielsweise ein kaskadierendes Stylesheet (CSS) über eine relative URL verfügt, die auf eine allgemeine CSS verweist, wird erwartet, dass Sie die allgemeine CSS auch in das Repository senden. Die Beziehung zwischen den beiden Ressourcen wird als ausstehende Beziehung für einen nicht anpassbaren Zeitraum von 30 Tagen gespeichert. Wenn Sie die allgemeine CSS innerhalb des Zeitraums von 30 Tagen an das Repository senden, wird die Beziehung gebildet.

Wenn Sie eine Ressource erstellen, wird die Zugriffssteuerungsliste (ACL) vom übergeordneten Ordner übernommen. Der Stammordner verfügt über Berechtigungen auf Systemebene, bis eine erste Ressource oder ein anfänglicher Ordner erstellt wird. Ab diesem Zeitpunkt erhält die Ressource oder der Ordner standardmäßige ACL-Berechtigungen.

Sie können Ressourcen programmgesteuert schreiben, indem Sie die Java-API des Repository-Dienstes oder die Webdienst-API verwenden.

>[!NOTE]
>
>Weitere Informationen zum Repository-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Gehen Sie wie folgt vor, um eine Ressource zu schreiben:

1. Projektdateien einschließen.
1. Erstellen Sie einen Repository-Dienst-Client.
1. Geben Sie den URI der zu lesenden Ressource an.
1. Lesen Sie die Ressource.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxy-Dateien ein.

**Dienstclient erstellen**

Bevor Sie eine Ressource programmgesteuert lesen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch Erstellen eines Service-Clients erreicht.

**Geben Sie den URI des Zielordners für die Ressource an**

Erstellen Sie eine Zeichenfolge, die den URI der zu lesenden Ressource enthält. Die Syntax enthält Schrägstriche, wie in diesem Beispiel gezeigt: &quot;/*path*/*Ordner*&quot;.

**Ressource erstellen**

Rufen Sie die Methode des Repository-Dienstes auf, um die Ressource zu erstellen, und geben Sie in die Ressource identifizierende Informationen ein, einschließlich UUID, Ressourcenname und Beschreibung.

**Ressourceninhalt angeben**

Rufen Sie die Methode des Repository-Dienstes auf, um Ressourceninhalte zu erstellen und diesen Inhalt in der Ressource zu speichern.

**Die Ressource in den Zielordner schreiben**

Rufen Sie die Methode des Repository-Dienstes auf, um die Ressource zu schreiben, und geben Sie den URI des Zielordners an.

**Siehe auch**

[Schreiben von Ressourcen mit der Java-API](aem-forms-repository.md#write-resources-using-the-java-api)

[Schreiben von Ressourcen mithilfe der Web-Dienst-API](aem-forms-repository.md#write-resources-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service-API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Schreiben von Ressourcen mit der Java-API {#write-resources-using-the-java-api}

Schreiben Sie eine Ressource mithilfe der Repository Service API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien in den Klassenpfad Ihres Java-Projekts ein.

1. Dienstclient erstellen

   Erstellen Sie eine `ResourceRepositoryClient` -Objekt mithilfe des -Konstruktors und Übergeben eines `ServiceClientFactory` -Objekt, das Verbindungseigenschaften enthält.

1. Geben Sie den URI des Zielordners für die Ressource an

   Geben Sie den URI des Zielordners für die Ressource an. In diesem Fall, weil die Ressource `testResource` im Ordner mit dem Namen `testFolder`, lautet der URI des Ordners . `"/testFolder"`. Der URI wird als `java.lang.String` -Objekt.

1. Ressource erstellen

   Um eine Ressource zu erstellen, müssen Sie zunächst eine `com.adobe.repository.infomodel.bean.RepositoryInfomodelFactoryBean` -Objekt.

   Rufen Sie die `RepositoryInfomodelFactoryBean` -Objekt `newResource` -Methode, die eine `com.adobe.repository.infomodel.bean.Resource` -Objekt. In diesem Beispiel werden die folgenden Parameter bereitgestellt:

   * A `com.adobe.repository.infomodel.Id` -Objekt, das durch Aufrufen des Standardkonstruktors für die `Id` -Klasse.
   * A `com.adobe.repository.infomodel.Lid` -Objekt, das durch Aufrufen des Standardkonstruktors für die `Lid` -Klasse.
   * A `java.lang.String` enthält den Dateinamen der Ressource.

   Um die Beschreibung der Ressource anzugeben, rufen Sie die `Resource` -Objekt `setDescription` -Methode verwenden und eine Zeichenfolge übergeben, die die Beschreibung enthält. In diesem Beispiel lautet die Beschreibung `"test resource"`.

1. Ressourceninhalt angeben

   Um Inhalte für die Ressource zu erstellen, rufen Sie die `RepositoryInfomodelFactoryBean` -Objekt `newResourceContent` -Methode, die eine `com.adobe.repository.infomodel.bean.ResourceContent` -Objekt. Hinzufügen von Inhalten zu `ResourceContent` -Objekt. In diesem Beispiel wird dies durch die folgenden Schritte erreicht:

   * Aufrufen der `ResourceContent` -Objekt `setDataDocument` -Methode und Übergabe einer `com.adobe.idp.Document` Objekt
   * Aufrufen der `ResourceContent` -Objekt `setSize` -Methode und Übergabe der Größe in Byte der `Document` Objekt

   Fügen Sie der Ressource den Inhalt hinzu, indem Sie die `Resource` -Objekt `setContent` -Methode und Übergabe der `ResourceContent` -Objekt. Weitere Informationen finden Sie unter [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Die Ressource in den Zielordner schreiben

   Rufen Sie die `ResourceRepositoryClient` -Objekt `writeResource` -Methode verwenden und den URI des Ordners sowie die `Resource` -Objekt.

**Siehe auch**

[Schreiben von Ressourcen](aem-forms-repository.md#writing-resources)

[Schnellstart (SOAP-Modus): Ressource mit der Java-API schreiben](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-writing-a-resource-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Schreiben von Ressourcen mithilfe der Web-Dienst-API {#write-resources-using-the-web-service-api}

Schreiben Sie eine Ressource mithilfe der Repository Service-API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Repository-WSDL mit base64 verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Dienstclient erstellen

   Erstellen Sie mithilfe der Microsoft .NET-Client-Assembly eine `RepositoryServiceService` -Objekt durch Aufrufen des Standardkonstruktors. Festlegen der `Credentials` -Eigenschaft mithilfe einer `System.Net.NetworkCredential` -Objekt, das den Benutzernamen und das Kennwort enthält.

1. Geben Sie den URI des Zielordners für die Ressource an

   Geben Sie den URI des Zielordners für die Ressource an. In diesem Fall, weil die Ressource `testResource` im Ordner mit dem Namen `testFolder`, lautet der URI des Ordners . `"/testFolder"`. Wenn Sie eine mit Microsoft .NET Framework kompatible Sprache verwenden (z. B. C#), speichern Sie den URI in einer `System.String` -Objekt.

1. Ressource erstellen

   Um eine Ressource zu erstellen, rufen Sie den Standardkonstruktor für die `Resource` -Klasse. In diesem Beispiel werden die folgenden Informationen im `Resource` -Objekt:

   * A `com.adobe.repository.infomodel.Id` -Objekt, das durch Aufrufen des Standardkonstruktors für die `Id` -Klasse und den `Resource` -Objekt `id` -Feld.
   * A `com.adobe.repository.infomodel.Lid` -Objekt, das durch Aufrufen des Standardkonstruktors für die `Lid` -Klasse und den `Resource` -Objekt `lid` -Feld.
   * Eine Zeichenfolge, die den Dateinamen der Ressource enthält, die dem `Resource` -Objekt `name` -Feld. Der in diesem Beispiel verwendete Name lautet `"testResource"`.
   * Eine Zeichenfolge, die die Beschreibung der Ressource enthält, die dem `Resource` -Objekt `description` -Feld. Die in diesem Beispiel verwendete Beschreibung lautet `"test resource"`.

1. Ressourceninhalt angeben

   Um Inhalte für die Ressource zu erstellen, rufen Sie den Standardkonstruktor für die `ResourceContent` -Klasse. Fügen Sie dann Inhalt zum `ResourceContent` -Objekt. In diesem Beispiel wird dies durch die folgenden Schritte erreicht:

   * Zuweisen einer `BLOB` -Objekt, das ein Dokument enthält `ResourceContent` -Objekt `dataDocument` -Feld.
   * Zuweisen der Größe in Byte der `BLOB` -Objekt `ResourceContent` -Objekt `size` -Feld.

   Fügen Sie der Ressource den Inhalt hinzu, indem Sie die `ResourceContent` -Objekt `Resource` -Objekt `content` -Feld.

1. Die Ressource in den Zielordner schreiben

   Rufen Sie die `RepositoryServiceService` -Objekt `writeResource` -Methode verwenden und den URI des Ordners sowie die `Resource` -Objekt. Pass `null` für die beiden anderen Parameter.

**Siehe auch**

[Schreiben von Ressourcen](aem-forms-repository.md#writing-resources)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Auflisten von Ressourcen {#listing-resources}

Sie können Ressourcen durch Auflistung von Ressourcen aufdecken. Für das Repository wird eine Abfrage durchgeführt, um alle Ressourcen zu finden, die mit einer bestimmten Ressourcensammlung verbunden sind.

Nachdem Sie Ihre Ressourcen organisiert haben, können Sie die von Ihnen erstellte Struktur überprüfen, indem Sie einen bestimmten Zweig der Struktur sehen, ähnlich wie bei einem Betriebssystem.

Auflisten von Ressourcen funktioniert nach Beziehung: -Ressourcen sind Mitglieder von Ordnern. Die Mitgliedschaft wird durch eine Beziehung des Typs &quot;Mitglied von&quot;repräsentiert. Wenn Sie Ressourcen in einem bestimmten Ordner auflisten, fragen Sie nach Ressourcen, die mit einem bestimmten Ordner durch die Beziehung &quot;Mitglied von&quot;verbunden sind. Beziehungen sind in die Richtung gerichtet: Ein Mitglied einer Beziehung hat eine Quelle, die Mitglied der Zielgruppe ist. Die Quelle ist die Ressource. das Ziel der übergeordnete Ordner ist.

>[!NOTE]
>
>Weitere Informationen zum Repository-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-2}

Gehen Sie wie folgt vor, um Ressourcen aufzulisten:

1. Projektdateien einschließen.
1. Erstellen Sie den Service-Client.
1. Geben Sie den Ordnerpfad an.
1. Rufen Sie die Liste der Ressourcen ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxy-Dateien ein.

**Dienstclient erstellen**

Bevor Sie eine Ressourcensammlung programmgesteuert erstellen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch Erstellen eines Service-Clients erreicht.

**Geben Sie den Ordnerpfad an**

Erstellen Sie eine Zeichenfolge, die den Pfad des Ordners mit den Ressourcen enthält. Die Syntax enthält Schrägstriche, wie in diesem Beispiel gezeigt: &quot;/*path*/*Ordner*&quot;.

**Liste der Ressourcen abrufen**

Rufen Sie die Methode des Repository-Dienstes auf, um die Liste der Ressourcen abzurufen, und geben Sie den Pfad des Zielordners an.

**Siehe auch**

[Auflisten von Ressourcen mit der Java-API](aem-forms-repository.md#list-resources-using-the-java-api)

[Auflisten von Ressourcen mithilfe der Webdienst-API](aem-forms-repository.md#list-resources-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service-API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Auflisten von Ressourcen mit der Java-API {#list-resources-using-the-java-api}

Auflisten von Ressourcen mithilfe der Repository Service API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien in den Klassenpfad Ihres Java-Projekts ein.

1. Dienstclient erstellen

   Erstellen Sie eine `ResourceRepositoryClient` -Objekt mithilfe des -Konstruktors und Übergeben eines `ServiceClientFactory` -Objekt, das Verbindungseigenschaften enthält.

1. Geben Sie den Ordnerpfad an

   Geben Sie den URI der zu abgefragenden Ressourcensammlung an. In diesem Fall lautet der URI `"/testFolder"`. Der URI wird als `java.lang.String` -Objekt.

1. Liste der Ressourcen abrufen

   Rufen Sie die `ResourceRepositoryClient` -Objekt `listMembers` -Methode verwenden und den URI des Ordners übergeben.

   Die Methode gibt eine `java.util.List` von `com.adobe.repository.infomodel.bean.Resource` Objekte, die die Quelle eines `com.adobe.repository.infomodel.bean.Relation` des Typs `Relation.TYPE_MEMBER_OF` und weisen den URI für die Ressourcenerfassung als Ziel auf. Sie können dies durchlaufen `List` , um die einzelnen Ressourcen abzurufen. In diesem Beispiel werden der Name und die Beschreibung jeder Ressource angezeigt.

**Siehe auch**

[Auflisten von Ressourcen](aem-forms-repository.md#listing-resources).

[Schnellstart (SOAP-Modus): Auflisten von Ressourcen mit der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-listing-resources-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Auflisten von Ressourcen mithilfe der Webdienst-API {#list-resources-using-the-web-service-api}

Auflisten von Ressourcen mithilfe der Repository Service-API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Repository-WSDL verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Dienstclient erstellen

   Erstellen Sie mithilfe der Microsoft .NET-Client-Assembly eine `RepositoryServiceService` -Objekt durch Aufrufen des Standardkonstruktors. Festlegen der `Credentials` -Eigenschaft mithilfe einer `System.Net.NetworkCredential` -Objekt, das den Benutzernamen und das Kennwort enthält.

1. Geben Sie den Ordnerpfad an

   Geben Sie eine Zeichenfolge an, die den URI des zu abgefragenden Ordners enthält. In diesem Fall lautet der URI `"/testFolder"`. Wenn Sie eine mit Microsoft .NET Framework kompatible Sprache verwenden (z. B. C#), speichern Sie den URI in einer `System.String` -Objekt.

1. Liste der Ressourcen abrufen

   Rufen Sie die `RepositoryServiceService` -Objekt `listMembers` -Methode verwenden und den URI des Ordners als ersten Parameter übergeben. Pass `null` für die beiden anderen Parameter.

   Die -Methode gibt ein Array von Objekten zurück, die in umgewandelt werden können `Resource` Objekte. Sie können durch das Objekt-Array navigieren, um jede der zugehörigen Ressourcen abzurufen. In diesem Beispiel werden der Name und die Beschreibung jeder Ressource angezeigt.

**Siehe auch**

[Auflisten von Ressourcen](aem-forms-repository.md#listing-resources).

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Lesen von Ressourcen {#reading-resources}

Sie können Ressourcen von einem bestimmten Speicherort im Repository abrufen, um ihren Inhalt und ihre Metadaten zu lesen. Der Workflow wird durch ein Initialisierungsformular voran beendet. Der Prozess verfügt über alle Berechtigungen, die zum Lesen des Formulars erforderlich sind. Das System ruft das Datenformular ab und liest den Inhalt aus dem Repository. Das Repository gewährt Zugriff auf den Inhalt und die Metadaten (die Möglichkeit, auch zu wissen, ob die Ressource vorhanden ist).

Das Repository verfügt über die folgenden vier Berechtigungstypen:

* **traverse**: ermöglicht die Auflistung von Ressourcen; das heißt, um Ressourcenmetadaten zu lesen, jedoch keine Ressourceninhalte
* **lesen**: ermöglicht das Lesen des Ressourceninhalts
* **schreiben**: ermöglicht Ihnen das Schreiben von Ressourceninhalten
* **Verwalten von Zugriffssteuerungslisten (ACLs)**: ermöglicht die Bearbeitung von ACLs für Ressourcen

Benutzer können Prozesse nur ausführen, wenn sie über die Berechtigung zum Ausführen des Prozesses verfügen. IDE-Benutzer benötigen Berechtigungen zum Durchlaufen und Lesen, um mit dem Repository synchronisiert zu werden. ACLs gelten nur zur Entwurfszeit, da die Laufzeit im Systemkontext erfolgt.

Sie können Ressourcen programmgesteuert lesen, indem Sie die Java-API des Repository-Dienstes oder die Webdienst-API verwenden.

>[!NOTE]
>
>Weitere Informationen zum Repository-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-3}

Gehen Sie wie folgt vor, um eine Ressource zu lesen:

1. Projektdateien einschließen.
1. Erstellen Sie einen Repository-Dienst-Client.
1. Geben Sie den URI der zu lesenden Ressource an.
1. Lesen Sie die Ressource.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxy-Dateien ein.

**Dienstclient erstellen**

Bevor Sie eine Ressource programmgesteuert lesen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch Erstellen eines Service-Clients erreicht.

**Geben Sie den URI der zu lesenden Ressource an**

Erstellen Sie eine Zeichenfolge, die den URI der zu lesenden Ressource enthält. Die Syntax enthält Schrägstriche, wie in diesem Beispiel gezeigt: &quot;/*path*/*resource*&quot;.

**Ressource lesen**

Rufen Sie die Methode des Repository-Dienstes auf, um die Ressource zu lesen, und geben Sie den URI an.

**Siehe auch**

[Lesen von Ressourcen mithilfe der Java-API](aem-forms-repository.md#read-resources-using-the-java-api)

[Lesen von Ressourcen mit der Web-Dienst-API](aem-forms-repository.md#reading-resources-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service-API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Lesen von Ressourcen mithilfe der Java-API {#read-resources-using-the-java-api}

Lesen Sie eine Ressource mithilfe der Repository Service API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien in den Klassenpfad Ihres Java-Projekts ein.

1. Dienstclient erstellen

   Erstellen Sie eine `ResourceRepositoryClient` -Objekt mithilfe des -Konstruktors und Übergeben eines `ServiceClientFactory` -Objekt, das Verbindungseigenschaften enthält.

1. Geben Sie den URI der zu lesenden Ressource an

   Geben Sie einen string -Wert an, der den URI der abzurufenden Ressource darstellt. Angenommen, die Ressource heißt *testResource* , der sich in einem Ordner mit dem Namen *testFolder*, um `/testFolder/testResource`.

1. Ressource lesen

   Rufen Sie die `ResourceRepositoryClient` -Objekt `readResource` -Methode verwenden und den URI der Ressource als Parameter übergeben. Diese Methode gibt eine `Resource` -Instanz, die die Ressource darstellt.

**Siehe auch**

[Lesen von Ressourcen](aem-forms-repository.md#reading-resources)

[Schnellstart (SOAP-Modus): Ressource mit der Java-API lesen](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-reading-a-resource-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Lesen von Ressourcen mit der Web-Dienst-API {#reading-resources-using-the-web-service-api}

Lesen einer Ressource mithilfe der Repository Service-API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Repository-WSDL verwendet. (Siehe [Erstellen einer .NET-Client-Assembly, die die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding).
   * Verweisen Sie auf die Microsoft .NET-Clientassembly. (Siehe [Erstellen einer .NET-Client-Assembly, die die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding).

1. Dienstclient erstellen

   Erstellen Sie mithilfe der Microsoft .NET-Client-Assembly eine `RepositoryServiceService` -Objekt durch Aufrufen des Standardkonstruktors. Festlegen der `Credentials` -Eigenschaft mithilfe einer `System.Net.NetworkCredential` -Objekt, das den Benutzernamen und das Kennwort enthält.

1. Geben Sie den URI der zu lesenden Ressource an

   Geben Sie eine Zeichenfolge an, die den URI der abzurufenden Ressource enthält. In diesem Fall, weil die Ressource `testResource` sich im Ordner mit dem Namen `testFolder`, lautet der URI `"/testFolder/testResource"`. Wenn Sie eine mit Microsoft .NET Framework kompatible Sprache verwenden (z. B. C#), speichern Sie den URI in einer `System.String` -Objekt.

1. Ressource lesen

   Rufen Sie die `RepositoryServiceService` -Objekt `readResource` -Methode verwenden und den URI der Ressource als ersten Parameter übergeben. Pass `null` für die beiden anderen Parameter.

**Siehe auch**

[Lesen von Ressourcen](aem-forms-repository.md#reading-resources)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Aktualisieren von Ressourcen {#updating-resources}

Sie können den Inhalt der Ressourcen im Repository abrufen und aktualisieren. Wenn Sie Ressourcen aktualisieren, bleibt die Zugriffskontrolle auf diese Ressourcen zwischen den Versionen unverändert. Bei einer Aktualisierung haben Sie die Möglichkeit, die Hauptversion zu erhöhen. Wenn Sie die Hauptversion nicht inkrementieren, wird die Nebenversion automatisch aktualisiert.

Wenn Sie eine Ressource aktualisieren, wird die neue Version basierend auf den angegebenen Ressourcenattributen erstellt. Beim Aktualisieren einer Ressource geben Sie zwei wichtige Parameter an: den Ziel-URI und eine Ressourceninstanz, die alle aktualisierten Metadaten enthält. Wenn Sie ein bestimmtes Attribut (z. B. den Namen) nicht ändern, ist das Attribut in der übergebenen Instanz weiterhin erforderlich. Die Beziehungen, die beim Analysieren des Inhalts erstellt werden, werden der jeweiligen Version hinzugefügt und nur weitergeleitet, wenn sie spezifiziert sind.

Wenn Sie beispielsweise eine XDP-Datei aktualisieren, die Verweise auf andere Ressourcen enthält, werden diese zusätzlichen Verweise ebenfalls aufgezeichnet. Angenommen, die Datei &quot;form.xdp&quot;, Version 1.0, enthält zwei externe Verweise: ein Logo und ein Stylesheet, und Sie aktualisieren anschließend form.xdp, sodass es jetzt drei Verweise enthält: ein Logo, ein Stylesheet und eine Schemadatei. Während der Aktualisierung fügt das Repository die dritte Beziehung (zur Schemadatei) zu seiner ausstehenden Beziehungstabelle hinzu. Sobald die Schemadatei im Repository vorhanden ist, wird die Beziehung automatisch gebildet. Wenn jedoch die form.xdp-Version 2.0 das -Logo nicht mehr verwendet, weist die form.xdp-Version 2.0 keine Beziehung zum -Logo auf.

Alle Aktualisierungsvorgänge sind atomisch und transaktional. Wenn beispielsweise zwei Benutzer dieselbe Ressource lesen und beide Version 1.0 auf Version 2.0 aktualisieren möchten, wird einer von ihnen erfolgreich sein und einer von ihnen schlägt fehl, wird die Integrität des Repositorys gewahrt und beide erhalten eine Meldung, die den Erfolg oder Fehler bestätigt. Wenn die Transaktion nicht übertragen wird, wird sie im Fall eines Datenbankfehlers zurückgesetzt und abhängig vom Anwendungsserver eine Zeitüberschreitung oder ein Rollback durchgeführt.

Sie können Ressourcen programmgesteuert aktualisieren, indem Sie die Java-API des Repository-Dienstes oder die Webdienst-API verwenden.

>[!NOTE]
>
>Weitere Informationen zum Repository-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-4}

Gehen Sie wie folgt vor, um eine Ressource zu aktualisieren:

1. Projektdateien einschließen.
1. Erstellen Sie einen Repository-Dienst-Client.
1. Rufen Sie die zu aktualisierende Ressource ab.
1. Aktualisieren Sie die Ressource.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxy-Dateien ein.

**Dienstclient erstellen**

Bevor Sie eine Ressource programmgesteuert lesen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch Erstellen eines Service-Clients erreicht.

**Zu aktualisierende Ressource abrufen**

Lesen Sie die Ressource. Weitere Informationen finden Sie unter [Lesen von Ressourcen](aem-forms-repository.md#reading-resources).

**Aktualisieren der Ressource**

Legen Sie die neuen Informationen in der Ressource fest und rufen Sie die Methode des Repository-Dienstes auf, um die Ressource zu aktualisieren. Geben Sie dabei den URI, die aktualisierte Ressource und die Art und Weise an, wie die Versionsinformationen aktualisiert werden sollen.

**Siehe auch**

[Aktualisieren von Ressourcen mithilfe der Java-API](aem-forms-repository.md#update-resources-using-the-java-api)

[Aktualisieren von Ressourcen mithilfe der Webdienst-API](aem-forms-repository.md#update-resources-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service-API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Aktualisieren von Ressourcen mithilfe der Java-API {#update-resources-using-the-java-api}

Aktualisieren Sie eine Ressource mithilfe der Repository Service API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien in den Klassenpfad Ihres Java-Projekts ein.

1. Dienstclient erstellen

   Erstellen Sie eine `ResourceRepositoryClient` -Objekt mithilfe des -Konstruktors und Übergeben eines `ServiceClientFactory` -Objekt, das Verbindungseigenschaften enthält.

1. Zu aktualisierende Ressource abrufen

   Geben Sie den URI der Ressource an, die abgerufen und gelesen werden soll. In diesem Beispiel lautet der URI der Ressource `"/testFolder/testResource"`.

1. Aktualisieren der Ressource

   Aktualisieren Sie die `Resource` -Objektinformationen. In diesem Beispiel rufen Sie zum Aktualisieren der Beschreibung die `Resource` -Objekt `setDescription` -Methode verwenden und die neue Beschreibungszeichenfolge als Parameter übergeben.

   Rufen Sie dann die `ServiceClientFactory` -Objekt `updateResource` und übergeben Sie die folgenden Parameter:

   * A `java.lang.String` -Objekt, das den URI der Ressource enthält.
   * Die `Resource` -Objekt, das die aktualisierten Ressourceninformationen enthält.
   * A `boolean` -Wert, der angibt, ob die Haupt- oder Nebenversion aktualisiert werden soll. In diesem Beispiel wurde der Wert `true` wird übergeben, um anzugeben, dass die Hauptversion inkrementiert werden soll.

**Siehe auch**

[Aktualisieren von Ressourcen](aem-forms-repository.md#updating-resources)

[Schnellstart (SOAP-Modus): Aktualisieren einer Ressource mit der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-updating-a-resource-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Aktualisieren von Ressourcen mithilfe der Webdienst-API {#update-resources-using-the-web-service-api}

Aktualisieren Sie eine Ressource mithilfe der Repository-API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Repository-WSDL verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Dienstclient erstellen

   Erstellen Sie mithilfe der Microsoft .NET-Client-Assembly eine `RepositoryServiceService` -Objekt durch Aufrufen des Standardkonstruktors. Festlegen der `Credentials` -Eigenschaft mithilfe einer `System.Net.NetworkCredential` -Objekt, das den Benutzernamen und das Kennwort enthält.

1. Zu aktualisierende Ressource abrufen

   Geben Sie den URI der abzurufenden Ressource an und lesen Sie die Ressource. In diesem Beispiel lautet der URI der Ressource `"/testFolder/testResource"`. Weitere Informationen finden Sie unter [Lesen von Ressourcen](aem-forms-repository.md#reading-resources).

1. Aktualisieren der Ressource

   Aktualisieren Sie die `Resource` -Objektinformationen. Um die Beschreibung zu aktualisieren, weisen Sie in diesem Beispiel dem `Resource` -Objekt `description` -Feld.

1. Rufen Sie die `RepositoryServiceService` -Objekt `updateResource` und übergeben Sie die folgenden Parameter:

   * A `System.String` -Objekt, das den URI der Ressource enthält.
   * Die `Resource` -Objekt, das die aktualisierten Ressourceninformationen enthält.
   * A `boolean` -Wert, der angibt, ob die Haupt- oder Nebenversion aktualisiert werden soll. In diesem Beispiel wurde der Wert `true` wird übergeben, um anzugeben, dass die Hauptversion inkrementiert werden soll.
   * Pass `null` für die beiden verbleibenden Parameter.

**Siehe auch**

[Aktualisieren von Ressourcen](aem-forms-repository.md#updating-resources)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Suchen nach Ressourcen {#searching-for-resources}

Sie können Abfragen erstellen, die verwendet werden, um im Repository nach Ressourcen zu suchen, einschließlich Verlauf, zugehörige Ressourcen und Eigenschaften.

Sie können verwandte Ressourcen abrufen, um Abhängigkeiten zwischen einem Formular und seinen Fragmenten zu ermitteln. Wenn Sie beispielsweise über ein Formular verfügen, können Sie bestimmen, welche Fragmente oder externen Ressourcen es verwendet. Wenn Sie ein Bild haben, können Sie auch herausfinden, welche Formulare das Bild verwenden. Sie können auch anhand von Eigenschaften nach verwandten Ressourcen suchen. Sie können beispielsweise nach allen Formularen suchen, die ein Bild mit einem angegebenen Namen verwenden, oder nach jedem Bild suchen, das von einem Formular mit einem bestimmten Namen verwendet wird. Sie können auch mithilfe von Ressourceneigenschaften suchen. Sie können beispielsweise eine Abfrage durchführen, um alle Formulare oder Ressourcen zu finden, deren Name mit einer bestimmten Zeichenfolge beginnt, die die Platzhalter &quot;%&quot;und &quot;_&quot;enthalten kann. Beachten Sie, dass auf Eigenschaften basierende Suchen nicht auf Beziehungen basieren. bei solchen Suchen wird davon ausgegangen, dass Sie über spezifische Kenntnisse zu einer bestimmten Ressource verfügen.

**Abfrageanweisungen**

A *Abfrage* enthält eine oder mehrere Anweisungen, die logisch mit Bedingungen verbunden sind. A *statement* besteht aus einem linken Operand, einem Operator und einem rechten Operand. Darüber hinaus können Sie die Sortierreihenfolge für die Suchergebnisse festlegen. Die *Sortierreihenfolge* enthält Informationen, die SQL entsprechen `ORDER BY` -Klausel und besteht aus Elementen, die die Attribute enthalten, auf denen die Suche basiert, sowie einem Wert, der angibt, ob eine aufsteigende oder absteigende Reihenfolge verwendet werden soll.

Sie können mithilfe der Java-API des Repository-Dienstes programmgesteuert nach Ressourcen suchen. Derzeit ist es nicht möglich, die Webdienst-API für die Suche nach Ressourcen zu verwenden.

**Sortierverhalten**

Die Sortierreihenfolge wird beim Aufrufen der `ResourceRepositoryClient` -Objekt `searchProperties` -Methode und die Angabe einer Sortierreihenfolge. Angenommen, Sie erstellen eine Ressource mit drei benutzerdefinierten Eigenschaften, wobei Attributnamen `name`, `secondName`und `asecondName`. Als Nächstes erstellen Sie ein Sortierreihenfolgen-Element für den Attributnamen und legen die `ascending` Wert zu `true`.

Dann rufen Sie die `ResourceRepositoryClient` -Objekt `searchProperties` -Methode verwenden und die Sortierreihenfolge übergeben. Die Suche gibt die richtige Ressource mit den drei Eigenschaften zurück. Die Eigenschaften werden jedoch nicht nach Attributnamen sortiert. Sie werden in der Reihenfolge zurückgegeben, in der sie hinzugefügt wurden: `name`, `secondName`und `asecondName`.

>[!NOTE]
>
>Weitere Informationen zum Repository-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-5}

Gehen Sie wie folgt vor, um nach Ressourcen zu suchen:

1. Projektdateien einschließen.
1. Erstellen Sie einen Repository-Dienst-Client.
1. Geben Sie den Zielordner für die Suche an.
1. Geben Sie die bei der Suche verwendeten Attribute an.
1. Erstellen Sie die bei der Suche verwendete Abfrage.
1. Erstellen Sie die Sortierreihenfolge für die Suchergebnisse.
1. Suchen Sie nach den Ressourcen.
1. Rufen Sie die Ressourcen aus dem Suchergebnis ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxy-Dateien ein.

**Dienstclient erstellen**

Bevor Sie eine Ressource programmgesteuert lesen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch Erstellen eines Service-Clients erreicht.

**Geben Sie den Zielordner für die Suche an**

Erstellen Sie eine Zeichenfolge, die den Basispfad enthält, von dem aus die Suche durchgeführt werden soll. Die Syntax enthält Schrägstriche, wie in diesem Beispiel gezeigt: &quot;/*path*/*Ordner*&quot;.

**Geben Sie die bei der Suche verwendeten Attribute an**

Sie können Ihre Suche auf den Attributen in Ressourcen basieren. Geben Sie die Werte der Attribute an, mit denen die Suche durchgeführt werden soll.

**Erstellen der bei der Suche verwendeten Abfrage**

Erstellen Sie eine Abfrage mithilfe von Anweisungen und Bedingungen. Jede Anweisung gibt das Attribut an, auf dem die Suche basieren soll, die zu verwendende Bedingung und den bei der Suche zu verwendenden Attributwert.

**Erstellen der Sortierreihenfolge für die Suchergebnisse**

Die Sortierreihenfolge besteht aus Elementen, von denen jedes eines der bei der Suche verwendeten Attribute enthält, und einem Wert, der angibt, ob eine aufsteigende oder absteigende Reihenfolge verwendet werden soll.

**Suche nach Ressourcen**

Suchen Sie mithilfe des Ordners, der Abfrage und der Sortierreihenfolge nach den Ressourcen. Geben Sie außerdem die Suchtiefe und eine Obergrenze für die Anzahl der zurückzugebenden Ergebnisse an.

**Abrufen der Ressourcen aus dem Suchergebnis**

Durchsuchen Sie die zurückgegebene Liste der Ressourcen und extrahieren Sie die Informationen zur weiteren Verarbeitung.

**Siehe auch**

[Suche nach Ressourcen mithilfe der Java-API](aem-forms-repository.md#search-for-resources-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service-API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Suche nach Ressourcen mithilfe der Java-API {#search-for-resources-using-the-java-api}

Suchen Sie mithilfe der Repository Service-API (Java) nach einer Ressource:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien in den Klassenpfad Ihres Java-Projekts ein.

1. Dienstclient erstellen

   Erstellen Sie eine `ResourceRepositoryClient` -Objekt mithilfe des -Konstruktors und Übergeben eines `ServiceClientFactory` -Objekt, das Verbindungseigenschaften enthält.

1. Geben Sie den Zielordner für die Suche an

   Geben Sie den URI des Basispfads an, aus dem die Suche ausgeführt werden soll. In diesem Beispiel lautet der URI der Ressource `/testFolder`.

1. Geben Sie die bei der Suche verwendeten Attribute an

   Geben Sie die Werte für die Attribute an, nach denen die Suche durchgeführt werden soll. Die Attribute befinden sich in einer `com.adobe.repository.infomodel.bean.Resource` -Objekt. In diesem Beispiel wird die Suche mit dem Attribut name durchgeführt. Daher `java.lang.String` enthält `Resource` Der Name des Objekts wird verwendet, d. h. `testResource` in diesem Fall.

1. Erstellen der bei der Suche verwendeten Abfrage

   Um eine Abfrage zu erstellen, erstellen Sie eine `com.adobe.repository.query.Query` -Objekt durch Aufrufen des Standardkonstruktors für `Query` -Klasse und fügen der Abfrage -Anweisungen hinzu.

   Um eine Anweisung zu erstellen, rufen Sie den Konstruktor für die `com.adobe.repository.query.Query.Statement` -Klasse und übergeben Sie die folgenden Parameter:

   * Ein linker Operand, der die Ressourcenattributkonstante enthält. Da in diesem Beispiel der Name der Ressource als Grundlage für die Suche verwendet wird, wird der statische Wert `Resource.ATTRIBUTE_NAME` verwendet.
   * Ein Operator, der die bei der Suche nach dem Attribut verwendete Bedingung enthält. Der Operator muss eine der statischen Konstanten im `Query.Statement` -Klasse. In diesem Beispiel wird der statische Wert `Query.Statement.OPERATOR_BEGINS_WITH` verwendet.
   * Ein rechter Operand, der den Attributwert enthält, für den die Suche durchgeführt werden soll. In diesem Beispiel wird das Attribut name `String` enthält den Wert `"testResource"`verwendet wird.

   Geben Sie den Namespace des linken Operanden an, indem Sie die `Query.Statement` -Objekt `setNamespace` -Methode verwenden und einen der im `com.adobe.repository.infomodel.bean.ResourceProperty` -Klasse. In diesem Beispiel `ResourceProperty.RESERVED_NAMESPACE_REPOSITORY` verwendet.

   Fügen Sie jede Anweisung zur Abfrage hinzu, indem Sie die `Query` -Objekt `addStatement` -Methode und Übergabe der `Query.Statement` -Objekt.

1. Erstellen der Sortierreihenfolge für die Suchergebnisse

   Um die in den Suchergebnissen verwendete Sortierreihenfolge festzulegen, erstellen Sie eine `com.adobe.repository.query.sort.SortOrder` -Objekt durch Aufrufen des Standardkonstruktors für `SortOrder` und fügen Sie der Sortierreihenfolge Elemente hinzu.

   Um ein Element für die Sortierreihenfolge zu erstellen, rufen Sie einen der Konstruktoren für die `com.adobe.repository.query.sort.SortOrder.Element` -Klasse. Da in diesem Beispiel der Name der Ressource als Grundlage für die Suche verwendet wird, wird der statische Wert `Resource.ATTRIBUTE_NAME` wird als erster Parameter und aufsteigende Reihenfolge verwendet (a `boolean` Wert von `true`) wird als zweiter Parameter angegeben.

   Fügen Sie jedes Element zur Sortierreihenfolge hinzu, indem Sie die `SortOrder` -Objekt `addSortElement` -Methode und Übergabe der `SortOrder.Element` -Objekt.

1. Suche nach Ressourcen

   Suchen nach `resources` Rufen Sie basierend auf den Attributeigenschaften die `ResourceRepositoryClient` -Objekt `searchProperties` -Methode verwenden und die folgenden Parameter übergeben:

   * A `String` enthält den Basispfad, von dem aus die Suche ausgeführt werden soll. In diesem Fall `"/testFolder"` verwendet.
   * Die bei der Suche verwendete Abfrage.
   * Die Tiefe der Suche. In diesem Fall `com.adobe.repository.infomodel.bean.ResourceCollection.DEPTH_INFINITE` wird verwendet, um anzugeben, dass der Basispfad und alle zugehörigen Ordner verwendet werden sollen.
   * Ein `int` -Wert, der die erste Zeile angibt, aus der die nicht paginierte Ergebnismenge ausgewählt werden soll. In diesem Beispiel `0` festgelegt ist.
   * Ein `int` -Wert, der die maximale Anzahl der zurückzugebenden Ergebnisse angibt. In diesem Beispiel `10` festgelegt ist.
   * Die bei der Suche verwendete Sortierreihenfolge.

   Die Methode gibt eine `java.util.List` von `Resource` -Objekte in der angegebenen Sortierreihenfolge.

1. Abrufen der Ressourcen aus dem Suchergebnis

   Um die im Suchergebnis enthaltenen Ressourcen abzurufen, navigieren Sie durch die `List` und jedes Objekt in eine `Resource` , um seine Informationen zu extrahieren. In diesem Beispiel wird der Name jeder Ressource angezeigt.

**Siehe auch**

[Suchen nach Ressourcen](aem-forms-repository.md#searching-for-resources)

[Schnellstart (SOAP-Modus): Suchen nach Ressourcen mithilfe der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-searching-for-resources-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Erstellen von Ressourcenbeziehungen {#creating-resource-relationships}

Sie können Beziehungen zwischen Ressourcen im Repository angeben. Es gibt drei Arten von Beziehungen:

* **Abhängigkeit**: eine Beziehung, in der eine Ressource von anderen Ressourcen abhängig ist, d. h. alle zugehörigen Ressourcen im Repository benötigt werden.
* **Mitgliedschaft (Dateisystem)**: eine Beziehung, in der sich eine Ressource in einem bestimmten Ordner befindet.
* **Benutzerdefiniert**: eine Beziehung, die Sie zwischen Ressourcen angeben. Wenn beispielsweise eine Ressource veraltet ist und eine andere in das Repository eingefügt wird, können Sie Ihre eigene Ersatzbeziehung festlegen.

Sie können Ihre eigenen benutzerspezifischen Beziehungen erstellen. Wenn Sie beispielsweise eine HTML-Datei im Repository speichern und sie ein Bild verwendet, können Sie eine benutzerdefinierte Beziehung festlegen, um die HTML-Datei mit dem Bild zu verknüpfen (da normalerweise nur XML-Dateien mit Bildern verknüpft sind, die eine repository-definierte Abhängigkeitsbeziehung verwenden). Ein weiteres Beispiel für eine benutzerdefinierte Beziehung wäre, wenn Sie eine andere Ansicht des Repositorys mit einer zyklischen Diagrammstruktur anstatt einer Baumstruktur erstellen möchten. Sie können ein Kreisdiagramm zusammen mit einem Viewer definieren, um diese Beziehungen zu durchlaufen. Schließlich könnten Sie darauf hinweisen, dass eine Ressource eine andere Ressource ersetzt, obwohl die beiden Ressourcen völlig verschieden sind. In diesem Fall können Sie einen Beziehungstyp außerhalb des reservierten Bereichs definieren und eine Beziehung zwischen diesen beiden Ressourcen erstellen. Ihre Anwendung wäre der einzige Client, der die Beziehung erkennen und verarbeiten könnte, und könnte zur Durchführung von Suchvorgängen zu dieser Beziehung verwendet werden.

Sie können Beziehungen zwischen Ressourcen programmgesteuert angeben, indem Sie die Java-API des Repository-Dienstes oder die Webdienst-API verwenden.

>[!NOTE]
>
>Weitere Informationen zum Repository-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-6}

Gehen Sie wie folgt vor, um eine Beziehung zwischen zwei Ressourcen anzugeben:

1. Projektdateien einschließen.
1. Erstellen Sie einen Repository-Dienst-Client.
1. Geben Sie die URIs der Ressourcen an, die verknüpft werden sollen.
1. Erstellen Sie die Beziehung.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxy-Dateien ein.

**Dienstclient erstellen**

Bevor Sie eine Ressource programmgesteuert lesen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch Erstellen eines Service-Clients erreicht.

**Geben Sie die URIs der Ressourcen an, die verknüpft werden sollen**

Erstellen Sie Strings, die die URIs der Ressource enthalten, die zugeordnet werden soll. Die Syntax enthält Schrägstriche, wie in diesem Beispiel gezeigt: &quot;/*path*/*resource*&quot;.

**Erstellen der Beziehung**

Rufen Sie die Methode des Repository-Dienstes auf, um den Beziehungstyp zu erstellen und anzugeben.

**Siehe auch**

[Erstellen von Beziehungsressourcen mit der Java-API](aem-forms-repository.md#create-relationship-resources-using-the-java-api)

[Erstellen von Beziehungsressourcen mithilfe der Webdienst-API](aem-forms-repository.md#create-relationship-resources-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service-API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Erstellen von Beziehungsressourcen mit der Java-API {#create-relationship-resources-using-the-java-api}

Erstellen Sie Beziehungsressourcen mithilfe der Java-API des Repository-Diensts und führen Sie die folgenden Aufgaben aus:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien in den Klassenpfad Ihres Java-Projekts ein.

1. Dienstclient erstellen

   Erstellen Sie eine `ResourceRepositoryClient` -Objekt mithilfe des -Konstruktors und Übergeben eines `ServiceClientFactory` -Objekt, das Verbindungseigenschaften enthält.

1. Geben Sie die URIs der Ressourcen an, die verknüpft werden sollen

   Geben Sie die URIs der Ressourcen an, die verknüpft werden sollen. In diesem Fall, weil die Ressourcen `testResource1` und `testResource2` und sich im Ordner mit dem Namen `testFolder`, sind ihre URIs `"/testFolder/testResource1"` und `"/testFolder/testResource2"`. Die URIs werden als `java.lang.String` Objekte. In diesem Beispiel werden die Ressourcen zuerst in das Repository geschrieben und ihre URIs abgerufen. Weitere Informationen zum Schreiben einer Ressource finden Sie unter [Schreiben von Ressourcen](aem-forms-repository.md#writing-resources).

1. Erstellen der Beziehung

   Rufen Sie die `ResourceRepositoryClient` -Objekt `createRelationship` -Methode verwenden und die folgenden Parameter übergeben:

   * Der URI der Quellressource.
   * Der URI der Zielressource.
   * Der Typ der Beziehung, der eine der statischen Konstanten in der `com.adobe.repository.infomodel.bean.Relation` -Klasse. In diesem Beispiel wird eine Abhängigkeitsbeziehung durch Angabe des Werts `Relation.TYPE_DEPENDANT_OF`.
   * A `boolean` Wert, der angibt, ob die Zielressource automatisch auf die `com.adobe.repository.infomodel.Id`-basierte Kennung der neuen Kopfressource. In diesem Beispiel wird aufgrund der Abhängigkeitsbeziehung der Wert `true` festgelegt ist.

   Sie können auch eine Liste verwandter Ressourcen für eine bestimmte Ressource abrufen, indem Sie die `ResourceRepositoryClient` -Objekt `getRelated` -Methode verwenden und die folgenden Parameter übergeben:

   * Der URI der Ressource, für die verwandte Ressourcen abgerufen werden sollen. In diesem Beispiel wird die Quellressource ( `"/testFolder/testResource1"`) angegeben ist.
   * A `boolean` -Wert, der angibt, ob die angegebene Ressource die Quellressource in der Beziehung ist. In diesem Beispiel wird der Wert `true` festgelegt ist, da dies der Fall ist.
   * Der Beziehungstyp, der eine der statischen Konstanten im `Relation` -Klasse. In diesem Beispiel wird eine Abhängigkeitsbeziehung anhand des zuvor verwendeten Werts angegeben: `Relation.TYPE_DEPENDANT_OF`.

   Die `getRelated` -Methode gibt eine `java.util.List` von `Resource` Objekte, durch die Sie die einzelnen zugehörigen Ressourcen abrufen können, wobei die in der `List` nach `Resource` wie Sie es tun. In diesem Beispiel `testResource2` wird in der Liste der zurückgegebenen Ressourcen erwartet.

**Siehe auch**

[Erstellen von Ressourcenbeziehungen](aem-forms-repository.md#creating-resource-relationships)

[Schnellstart (SOAP-Modus): Erstellen von Beziehungen zwischen Ressourcen mithilfe der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-creating-relationships-between-resources-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Erstellen von Beziehungsressourcen mithilfe der Webdienst-API {#create-relationship-resources-using-the-web-service-api}

Erstellen Sie Beziehungsressourcen mithilfe der Repository-API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Repository-WSDL verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Dienstclient erstellen

   Erstellen Sie mithilfe der Microsoft .NET-Client-Assembly eine `RepositoryServiceService` -Objekt durch Aufrufen des Standardkonstruktors. Festlegen der `Credentials` -Eigenschaft mithilfe einer `System.Net.NetworkCredential` -Objekt, das den Benutzernamen und das Kennwort enthält.

1. Geben Sie die URIs der Ressourcen an, die verknüpft werden sollen

   Geben Sie die URIs der Ressourcen an, die verknüpft werden sollen. In diesem Fall, weil die Ressourcen `testResource1` und `testResource2` und sich im Ordner mit dem Namen `testFolder`, sind ihre URIs `"/testFolder/testResource1"` und `"/testFolder/testResource2"`. Bei Verwendung einer mit Microsoft .NET Framework kompatiblen Sprache (z. B. C#) werden die URIs als `System.String` Objekte. In diesem Beispiel werden die Ressourcen zuerst in das Repository geschrieben und ihre URIs abgerufen. Weitere Informationen zum Schreiben einer Ressource finden Sie unter [Schreiben von Ressourcen](aem-forms-repository.md#writing-resources).

1. Erstellen der Beziehung

   Rufen Sie die `RepositoryServiceService` -Objekt `createRelationship` -Methode verwenden und die folgenden Parameter übergeben:

   * Der URI der Quellressource.
   * Der URI der Zielressource.
   * Die Art der Beziehung. In diesem Beispiel wird eine Abhängigkeitsbeziehung durch Angabe des Werts `3`.
   * A `boolean` -Wert, der angibt, ob der Beziehungstyp angegeben wurde. In diesem Beispiel wird der Wert `true` festgelegt ist.
   * A `boolean` Wert, der angibt, ob die Zielressource automatisch auf die `Id`-basierte Kennung der neuen Kopfressource. In diesem Beispiel wird aufgrund der Abhängigkeitsbeziehung der Wert `true` festgelegt ist.
   * A `boolean` -Wert, der angibt, ob die Zielkopfzeile angegeben wurde. In diesem Beispiel wird der Wert `true` festgelegt ist.
   * Pass `null` für den letzten Parameter.

   Sie können auch eine Liste verwandter Ressourcen für eine bestimmte Ressource abrufen, indem Sie die `RepositoryServiceService` -Objekt `getRelated` -Methode verwenden und die folgenden Parameter übergeben:

   * Der URI der Ressource, für die verwandte Ressourcen abgerufen werden sollen. In diesem Beispiel wird die Quellressource ( `"/testFolder/testResource1"`) angegeben ist.
   * A `boolean` -Wert, der angibt, ob die angegebene Ressource die Quellressource in der Beziehung ist. In diesem Beispiel wird der Wert `true` festgelegt ist, da dies der Fall ist.
   * A `boolean` -Wert, der angibt, ob die Quellressource angegeben wurde. In diesem Beispiel wird der Wert `true` bereitgestellt wird.
   * Ein Array von Ganzzahlen, die die Beziehungstypen enthalten. In diesem Beispiel wird eine Abhängigkeitsbeziehung angegeben, indem der gleiche Wert im Array wie zuvor verwendet wird: `3`.
   * Pass `null` für die beiden verbleibenden Parameter.

   Die `getRelated` -Methode gibt ein Array von Objekten zurück, die in umgewandelt werden können `Resource` -Objekte, über die Sie die einzelnen zugehörigen Ressourcen abrufen können. In diesem Beispiel `testResource2` wird in der Liste der zurückgegebenen Ressourcen erwartet.

**Siehe auch**

[Erstellen von Ressourcenbeziehungen](aem-forms-repository.md#creating-resource-relationships)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Ressourcen sperren {#locking-resources}

Sie können eine Ressource oder einen Satz von Ressourcen sperren, die ausschließlich von einem bestimmten Benutzer verwendet oder von mehreren Benutzern gemeinsam genutzt werden können. Ein freigegebenes Schloss ist ein Hinweis darauf, dass mit der Ressource etwas passieren wird, aber es hindert niemanden daran, mit dieser Ressource zu handeln. Ein freigegebenes Schloss sollte als Signalmechanismus betrachtet werden. Eine exklusive Sperre bedeutet, dass der Benutzer, der die Ressource gesperrt hat, die Ressource ändern wird. Die Sperre stellt sicher, dass niemand anders dies tun kann, bis der Benutzer keinen Zugriff mehr auf die Ressource benötigt und die Sperre aufgehoben hat. Wenn ein Repository-Administrator eine Ressource entsperrt, werden alle exklusiven und freigegebenen Sperren für diese Ressource automatisch entfernt. Dieser Aktionstyp ist für Situationen gedacht, in denen ein Benutzer nicht mehr verfügbar ist und die Ressource nicht entsperrt hat.

Wenn eine Ressource gesperrt ist, wird ein Sperrsymbol angezeigt, wenn Sie die Registerkarte &quot;Ressourcen&quot;in Workbench anzeigen, wie in der folgenden Abbildung dargestellt.

![lr_lr_lockrepository](assets/lr_lr_lockrepository.png)

Sie können den Zugriff auf Ressourcen programmgesteuert steuern, indem Sie die Java-API des Repository-Dienstes oder die Webdienst-API verwenden.

>[!NOTE]
>
>Weitere Informationen zum Repository-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-7}

Gehen Sie wie folgt vor, um Ressourcen zu sperren und zu entsperren:

1. Projektdateien einschließen.
1. Erstellen Sie einen Repository-Dienst-Client.
1. Geben Sie den URI der Ressource an, die gesperrt werden soll.
1. Ressource sperren.
1. Rufen Sie die Sperren für die Ressource ab.
1. Ressource entsperren

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxy-Dateien ein.

**Dienstclient erstellen**

Bevor Sie eine Ressource programmgesteuert lesen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch Erstellen eines Service-Clients erreicht.

**Geben Sie den URI der Ressource an, die gesperrt werden soll**

Erstellen Sie eine Zeichenfolge, die den URI der Ressource enthält, die gesperrt werden soll. Die Syntax enthält Schrägstriche, wie in diesem Beispiel gezeigt: &quot;/*path*/*resource*&quot;.

**Ressource sperren**

Rufen Sie die Methode des Repository-Dienstes auf, um die Ressource zu sperren, und geben Sie den URI, den Typ der Sperre und die Sperrtiefe an.

**Sperren für die Ressource abrufen**

Rufen Sie die Methode des Repository-Dienstes auf, um die Sperren für die Ressource abzurufen, und geben Sie den URI an.

**Ressource entsperren**

Rufen Sie die Methode des Repository-Dienstes auf, um die Ressource zu entsperren und den URI anzugeben.

**Siehe auch**

[Ressourcen mithilfe der Java-API sperren](aem-forms-repository.md#lock-resources-using-the-java-api)

[Sperren von Ressourcen mithilfe der Webdienst-API](aem-forms-repository.md#lock-resources-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service-API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Ressourcen mithilfe der Java-API sperren {#lock-resources-using-the-java-api}

Ressourcen mithilfe der Repository Service-API (Java) sperren:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien in den Klassenpfad Ihres Java-Projekts ein.

1. Dienstclient erstellen

   Erstellen Sie eine `ResourceRepositoryClient` -Objekt mithilfe des -Konstruktors und Übergeben eines `ServiceClientFactory` -Objekt, das Verbindungseigenschaften enthält.

1. Geben Sie den URI der Ressource an, die gesperrt werden soll

   Geben Sie den URI der Ressource an, die gesperrt werden soll. In diesem Fall, weil die Ressource `testResource` sich im Ordner mit dem Namen `testFolder`, lautet der URI `"/testFolder/testResource"`. Der URI wird als `java.lang.String` -Objekt.

1. Ressource sperren

   Rufen Sie die `ResourceRepositoryClient` -Objekt `lockResource` -Methode verwenden und die folgenden Parameter übergeben:

   * Der URI der Ressource.
   * Der Sperrbereich. In diesem Beispiel wird der Sperrbereich als `com.adobe.repository.infomodel.bean.Lock.SCOPE_EXCLUSIVE`.
   * Die Schlosstiefe. In diesem Beispiel wird die Sperrtiefe als `Lock.DEPTH_ZERO`.

   >[!NOTE]
   >
   >Die überladene Version der `lockResource` -Methode, die vier Parameter erfordert, gibt eine Ausnahme aus. Stellen Sie sicher, dass die `lockResource` -Methode, die drei Parameter erfordert, wie in dieser exemplarischen Vorgehensweise dargestellt.

1. Sperren für die Ressource abrufen

   Rufen Sie die `ResourceRepositoryClient` -Objekt `getLocks` -Methode verwenden und den URI der Ressource als Parameter übergeben. Die Methode gibt eine Liste von Sperrobjekten zurück, durch die Sie iterieren können. In diesem Beispiel werden der Sperrinhaber, die Tiefe und der Umfang für jedes Objekt gedruckt, indem die `getOwnerUserId`, `getDepth`und `getType` -Methoden.

1. Ressource entsperren

   Rufen Sie die `ResourceRepositoryClient` -Objekt `unlockResource` -Methode verwenden und den URI der Ressource als Parameter übergeben. Weitere Informationen finden Sie unter [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Siehe auch**

[Ressourcen sperren](aem-forms-repository.md#locking-resources)

[Schnellstart (SOAP-Modus): Ressourcen mithilfe der Java-API sperren](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-locking-a-resource-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Sperren von Ressourcen mithilfe der Webdienst-API {#lock-resources-using-the-web-service-api}

Ressourcen mithilfe der Repository Service-API (Webdienst) sperren:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Repository-WSDL mit Base64 verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Dienstclient erstellen

   Erstellen Sie mithilfe der Microsoft .NET-Client-Assembly eine `RepositoryServiceService` -Objekt durch Aufrufen des Standardkonstruktors. Festlegen der `Credentials` -Eigenschaft mithilfe einer `System.Net.NetworkCredential` -Objekt, das den Benutzernamen und das Kennwort enthält.

1. Geben Sie den URI der Ressource an, die gesperrt werden soll

   Geben Sie eine Zeichenfolge an, die den URI der Ressource enthält, die gesperrt werden soll. In diesem Fall, weil die Ressource `testResource` sich im Ordner befindet `testFolder`, lautet der URI `"/testFolder/testResource"`. Wenn Sie eine mit Microsoft .NET Framework kompatible Sprache verwenden (z. B. C#), speichern Sie den URI in einer `System.String` -Objekt.

1. Ressource sperren

   Rufen Sie die `RepositoryServiceService` -Objekt `lockResource` -Methode verwenden und die folgenden Parameter übergeben:

   * Der URI der Ressource.
   * Der Sperrbereich. In diesem Beispiel wird der Sperrbereich als `11`.
   * Die Schlosstiefe. In diesem Beispiel wird die Sperrtiefe als `2`.
   * Ein `int` -Wert, der die Anzahl der Sekunden angibt, bis die Sperre abläuft. In diesem Beispiel wird der Wert von `1000` verwendet.
   * Pass `null` für den letzten Parameter.

1. Sperren für die Ressource abrufen

   Rufen Sie die `RepositoryServiceService` -Objekt `getLocks` -Methode verwenden und den URI der Ressource als ersten Parameter übergeben und `null` für den zweiten Parameter. Die Methode gibt eine `object` Array, das `Lock` Objekte, durch die Sie iterieren können. In diesem Beispiel werden der Sperrinhaber, die Tiefe und der Umfang für jedes Objekt gedruckt, indem auf die einzelnen Objekte zugegriffen wird `Lock` -Objekt `ownerUserId`, `depth`und `type` angegeben.

1. Ressource entsperren

   Rufen Sie die `RepositoryServiceService` -Objekt `unlockResource` -Methode verwenden und den URI der Ressource als ersten Parameter übergeben und `null` für den zweiten Parameter.

**Siehe auch**

[Ressourcen sperren](aem-forms-repository.md#locking-resources)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Löschen von Ressourcen {#deleting-resources}

Sie können Ressourcen programmgesteuert von einem bestimmten Speicherort im Repository löschen, indem Sie die Java-API (SOAP) des Repository-Dienstes verwenden.

Wenn Sie eine Ressource löschen, ist der Löschvorgang normalerweise dauerhaft. In einigen Fällen können ECM-Repositorys die Versionen der Ressource jedoch gemäß ihren Verlaufsmechanismen speichern. Daher müssen Sie beim Löschen einer Ressource sicherstellen, dass Sie diese Ressource nie mehr benötigen. Zu den häufigen Gründen für das Löschen einer Ressource gehört die Notwendigkeit, den verfügbaren Speicherplatz in der Datenbank zu erhöhen. Sie können eine Version einer Ressource löschen. Wenn Sie dies jedoch tun, müssen Sie die Kennung der Ressource und nicht die logische Kennung (LID) oder den Pfad angeben. Wenn Sie einen Ordner löschen, werden alle Inhalte in diesem Ordner, einschließlich Unterordnern und Ressourcen, automatisch gelöscht.

Zugehörige Ressourcen werden nicht gelöscht. Wenn Sie beispielsweise über ein Formular verfügen, das die Datei logo.gif verwendet, und logo.gif löschen, wird eine Beziehung in der Tabelle für ausstehende Beziehungen gespeichert. Alternativ können Sie für die veraltete Version den Objektstatus der neuesten Version auf veraltet setzen.

Ein Löschvorgang ist in ECM-Systemen nicht transaktionssicher. Wenn Sie beispielsweise versuchen, 100 Ressourcen zu löschen und der Vorgang für die 50. Ressource fehlschlägt, werden die ersten 49 Instanzen gelöscht, der Rest jedoch nicht. Andernfalls ist das Standardverhalten das Rollback (Nicht-Zusage).

>[!NOTE]
>
>Bei Verwendung von `com.adobe.repository.bindings.dsc.client.ResourceRepositoryClient.deleteResources()` -Methode mit dem ECM-Repository (EMC Documentum Content Server und IBM FileNet P8 Content Manager) verwendet wird, wird die Transaktion nicht zurückgesetzt, wenn der Löschvorgang für eine der angegebenen Ressourcen fehlschlägt. Dies bedeutet, dass gelöschte Dateien nicht rückgängig gemacht werden können.

>[!NOTE]
>
>Weitere Informationen zum Repository-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-8}

Gehen Sie wie folgt vor, um eine Ressource zu löschen:

1. Projektdateien einschließen.
1. Erstellen Sie einen Repository-Dienst-Client.
1. Geben Sie den URI der Ressource an, die gelöscht werden soll.
1. Löschen Sie die Ressource.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxy-Dateien ein.

**Dienstclient erstellen**

Bevor Sie eine Ressource programmgesteuert lesen können, müssen Sie eine Verbindung herstellen und Anmeldeinformationen angeben. Dies wird durch Erstellen eines Service-Clients erreicht.

**Geben Sie den URI der Ressource an, die gelöscht werden soll**

Erstellen Sie eine Zeichenfolge, die den URI der zu löschenden Ressource enthält. Die Syntax enthält Schrägstriche, wie in diesem Beispiel gezeigt: &quot;/*path*/*resource*&quot;. Wenn es sich bei der zu löschenden Ressource um einen Ordner handelt, wird der Löschvorgang rekursiv ausgeführt.

**Ressource löschen**

Rufen Sie die Methode des Repository-Dienstes auf, um die Ressource zu löschen, und geben Sie den URI an.

**Siehe auch**

[Löschen von Ressourcen mithilfe der Java-API](aem-forms-repository.md#delete-resources-using-the-java-api-soap)

[Löschen von Ressourcen mithilfe der Webdienst-API](aem-forms-repository.md#delete-resources-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Repository Service-API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Löschen von Ressourcen mithilfe der Java-API (SOAP) {#delete-resources-using-the-java-api-soap}

Löschen Sie eine Ressource mithilfe der Repository-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien in den Klassenpfad Ihres Java-Projekts ein.

1. Dienstclient erstellen

   Erstellen Sie eine `ResourceRepositoryClient` -Objekt mithilfe des -Konstruktors und Übergeben eines `ServiceClientFactory` -Objekt, das Verbindungseigenschaften enthält.

1. Geben Sie den URI der Ressource an, die gelöscht werden soll

   Geben Sie den URI der abzurufenden Ressource an. Da sich die Ressource testResourceToBeDeleted in dem Ordner testFolder befindet, lautet ihr URI in diesem Fall `/testFolder/testResourceToBeDeleted`. Der URI wird als `java.lang.String` -Objekt. In diesem Beispiel wird die Ressource zuerst in das Repository geschrieben und ihr URI abgerufen. Weitere Informationen zum Schreiben einer Ressource finden Sie unter [Schreiben von Ressourcen](aem-forms-repository.md#writing-resources).

1. Ressource löschen

   Rufen Sie die `ResourceRepositoryClient` -Objekt `deleteResource` -Methode verwenden und den URI der Ressource als Parameter übergeben.

**Siehe auch**

[Löschen von Ressourcen](aem-forms-repository.md#deleting-resources)

[Schnellstart (SOAP-Modus): Suchen nach Ressourcen mithilfe der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-searching-for-resources-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Löschen von Ressourcen mithilfe der Webdienst-API {#delete-resources-using-the-web-service-api}

Löschen Sie eine Ressource mithilfe der Repository-API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Repository-WSDL mit Base64 verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Dienstclient erstellen

   Erstellen Sie mithilfe der Microsoft .NET-Client-Assembly eine `RepositoryServiceService` -Objekt durch Aufrufen des Standardkonstruktors. Festlegen der `Credentials` -Eigenschaft mithilfe einer `System.Net.NetworkCredential` -Objekt, das den Benutzernamen und das Kennwort enthält.

1. Geben Sie den URI der Ressource an, die gelöscht werden soll

   Geben Sie den URI der abzurufenden Ressource an. In diesem Fall, weil die Ressource `testResourceToBeDeleted` sich im Ordner mit dem Namen `testFolder`, lautet der URI `"/testFolder/testResourceToBeDeleted"`. In diesem Beispiel wird die Ressource zuerst in das Repository geschrieben und ihr URI abgerufen. Weitere Informationen zum Schreiben einer Ressource finden Sie unter [Schreiben von Ressourcen](aem-forms-repository.md#writing-resources).

1. Ressource löschen

   Rufen Sie die `RepositoryServiceService` -Objekt `deleteResources` -Methode und übergeben Sie eine `System.String` -Array, das den URI der Ressource als ersten Parameter enthält. Pass `null` für den zweiten Parameter.

**Siehe auch**

[Löschen von Ressourcen](aem-forms-repository.md#deleting-resources)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
