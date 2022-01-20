---
title: Schützen von Dokumenten mit Richtlinien
seo-title: Protecting Documents with Policies
description: Verwenden Sie den Document Security-Dienst, um Vertraulichkeitseinstellungen dynamisch auf Adobe PDF-Dokumente anzuwenden und die Kontrolle über die Dokumente zu behalten. Der Document Security-Dienst ermöglicht es den Benutzern außerdem, die Kontrolle darüber zu behalten, wie Empfänger das richtliniengeschützte PDF-Dokument verwenden.
seo-description: Use the Document Security service to dynamically apply confidentiality settings to Adobe PDF documents and to maintain control over the documents. The Document Security service also enables the users to maintain control over how recipients use the policy-protected PDF document.
uuid: 6feb69ef-7b61-4d0b-8c87-d65d98bae9b5
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 9b1d2bf3-f28c-41b2-9026-1f3311556422
role: Developer
exl-id: 88065c4d-8ca9-4dfb-8663-ac8772e5e556
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '15500'
ht-degree: 4%

---

# Schützen von Dokumenten mit Richtlinien {#protecting-documents-with-policies}

**Informationen zum Document Security-Dienst**

Der Document Security-Dienst ermöglicht es Benutzern, Vertraulichkeitseinstellungen dynamisch auf Adobe PDF-Dokumente anzuwenden und die Kontrolle über die Dokumente zu behalten, unabhängig davon, wie weit sie verteilt sind.

Der Document Security-Dienst verhindert, dass Informationen über die Reichweite des Benutzers verteilt werden, indem er es Benutzern ermöglicht, die Kontrolle darüber zu behalten, wie Empfänger das richtliniengeschützte PDF-Dokument verwenden. Ein Benutzer kann angeben, wer ein Dokument öffnen, einschränken, wie es verwendet werden kann, und das Dokument nach seiner Verteilung überwachen. Ein Benutzer kann auch den Zugriff auf ein richtliniengeschütztes Dokument dynamisch steuern und sogar den Zugriff auf das Dokument dynamisch sperren.

Der Document Security-Dienst schützt auch andere Dateitypen wie Microsoft Word-Dateien (DOC-Dateien). Sie können die Document Security Client-API verwenden, um mit diesen Dateitypen zu arbeiten. Die folgenden Versionen werden unterstützt:

* Microsoft Office 2003-Dateien (DOC-, XLS-, PPT-Dateien)
* Microsoft Office 2007-Dateien (DOCX-, XLSX-, PPTX-Dateien)
* PTC Pro/E-Dateien

In den beiden folgenden Abschnitten wird die Verwendung von Word-Dokumenten erläutert:

* [Anwenden von Richtlinien auf Word-Dokumente](protecting-documents-policies.md#applying-policies-to-word-documents)
* [Entfernen von Richtlinien aus Word-Dokumenten](protecting-documents-policies.md#removing-policies-from-word-documents)

Sie können diese Aufgaben mithilfe des Document Security-Dienstes ausführen:

* Erstellen von Richtlinien. Weitere Informationen finden Sie unter [Erstellen von Richtlinien](protecting-documents-policies.md#creating-policies).
* Richtlinien ändern. Weitere Informationen finden Sie unter [Ändern von Richtlinien](protecting-documents-policies.md#modifying-policies).
* Richtlinien löschen Weitere Informationen finden Sie unter [Löschen von Richtlinien](protecting-documents-policies.md#deleting-policies).
* Anwenden von Richtlinien auf PDF-Dokumente. Weitere Informationen finden Sie unter [Anwenden von Richtlinien auf PDF-Dokumente](protecting-documents-policies.md#applying-policies-to-pdf-documents).
* Entfernen Sie Richtlinien aus PDF-Dokumenten. Weitere Informationen finden Sie unter [Entfernen von Richtlinien aus PDF-Dokumenten](protecting-documents-policies.md#removing-policies-from-pdf-documents).
* Richtliniengeschützte Inspect-Dokumente. Weitere Informationen finden Sie unter [Überprüfen von richtliniengeschützten PDF-Dokumenten](protecting-documents-policies.md#inspecting-policy-protected-pdf-documents).
* Sperren Sie den Zugriff auf PDF-Dokumente. Weitere Informationen finden Sie unter [Zugriff auf Dokumente sperren](protecting-documents-policies.md#revoking-access-to-documents).
* Neuer Zugriff auf gesperrte Dokumente. Weitere Informationen finden Sie unter [Neuer Zugriff auf gesperrte Dokumente](protecting-documents-policies.md#reinstating-access-to-revoked-documents).
* Erstellen Sie Wasserzeichen. Weitere Informationen finden Sie unter [Wasserzeichen erstellen](protecting-documents-policies.md#creating-watermarks).
* Suchen Sie nach Ereignissen. Weitere Informationen finden Sie unter [Suchen nach Ereignissen](protecting-documents-policies.md#searching-for-events).

>[!NOTE]
>
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Erstellen von Richtlinien {#creating-policies}

Sie können Richtlinien programmgesteuert mit der Document Security Java-API oder der Web Service-API erstellen. A *policy* ist eine Sammlung von Informationen, die Document Security-Einstellungen, autorisierte Benutzer und Verwendungsrechte umfasst. Sie können eine beliebige Anzahl von Richtlinien erstellen und speichern, indem Sie Sicherheitseinstellungen verwenden, die für unterschiedliche Situationen und Benutzer geeignet sind.

Richtlinien ermöglichen Ihnen die Durchführung folgender Aufgaben:

* Geben Sie die Personen an, die das Dokument öffnen können. Die Empfänger können entweder zu Ihrer Organisation gehören oder diese externe Person sein.
* Geben Sie an, wie Empfänger das Dokument verwenden können. Sie können den Zugriff auf verschiedene Acrobat- und Adobe Reader-Funktionen einschränken. Zu diesen Funktionen gehört die Möglichkeit, Text zu drucken und zu kopieren, Signaturen hinzuzufügen und einem Dokument Kommentare hinzuzufügen.
* Ändern Sie die Zugriffs- und Sicherheitseinstellungen jederzeit, auch nachdem Sie das richtliniengeschützte Dokument verteilt haben.
* Überwachen Sie die Verwendung des Dokuments nach seiner Verteilung. Sie können sehen, wie das Dokument verwendet wird und wer es verwendet. Sie können beispielsweise feststellen, wann ein Benutzer das Dokument geöffnet hat.

### Richtlinien mithilfe von Webdiensten erstellen {#creating-a-policy-using-web-services}

Wenn Sie eine Richtlinie mit der Webdienst-API erstellen, verweisen Sie auf eine vorhandene XML-Datei für Portable Document Rights Language (PDRL), die die Richtlinie beschreibt. Richtlinienberechtigungen und der Prinzipal werden im PDRL-Dokument definiert. Das folgende XML-Dokument ist ein Beispiel für ein PDRL-Dokument.

```as3
 <?xml version="1.0" encoding="UTF-8" standalone="yes"?> 
 <Policy PolicyInstanceVersion="1" PolicyID="5DA3F847-DE76-F9CC-63EA-49A8D59154DE" PolicyCreationTime="2004-08-30T00:02:28.294+00:00" PolicyType="1" PolicySchemaVersion="1.0" PolicyName="SDK Test Policy -4344050357301573237" PolicyDescription="An SDK Test policy" xmlns="https://www.adobe.com/schema/1.0/pdrl"> 
       <PolicyEntry> 
          <ns1:Permission PermissionName="com.adobe.aps.onlineOpen" Access="ALLOW" xmlns:ns1="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" /> 
  
          <ns2:Permission PermissionName="com.adobe.aps.offlineOpen" Access="ALLOW" xmlns:ns2="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" /> 
  
          <ns3:Permission PermissionName="com.adobe.aps.pdf.editNotes" Access="ALLOW" xmlns:ns3="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" /> 
  
          <ns4:Permission PermissionName="com.adobe.aps.pdf.fillAndSign" Access="ALLOW" xmlns:ns4="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" /> 
          <Principal PrincipalNameType="SYSTEM"> 
             <PrincipalDomain>EDC_SPECIAL</PrincipalDomain> 
  
             <PrincipalName>all_internal_users</PrincipalName> 
          </Principal> 
       </PolicyEntry> 
       <PolicyEntry> 
          <ns5:Permission PermissionName="com.adobe.aps.onlineOpen" Access="ALLOW" xmlns:ns5="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" /> 
  
          <ns6:Permission PermissionName="com.adobe.aps.offlineOpen" Access="ALLOW" xmlns:ns6="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" /> 
  
          <ns7:Permission PermissionName="com.adobe.aps.pdf.copy" Access="ALLOW" xmlns:ns7="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" /> 
  
          <ns8:Permission PermissionName="com.adobe.aps.pdf.printLow" Access="ALLOW" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" xmlns:ns8="https://www.adobe.com/schema/1.0/pdrl" /> 
  
          <ns9:Permission PermissionName="com.adobe.aps.policySwitch" Access="ALLOW" xmlns:ns9="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" /> 
  
          <ns10:Permission PermissionName="com.adobe.aps.revoke" Access="ALLOW" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" xmlns:ns10="https://www.adobe.com/schema/1.0/pdrl" /> 
  
          <ns11:Permission PermissionName="com.adobe.aps.pdf.edit" Access="ALLOW" xmlns:ns11="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" /> 
  
          <ns12:Permission PermissionName="com.adobe.aps.pdf.editNotes" Access="ALLOW" xmlns:ns12="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" /> 
  
          <ns13:Permission PermissionName="com.adobe.aps.pdf.fillAndSign" Access="ALLOW" xmlns:ns13="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" /> 
  
          <ns14:Permission PermissionName="com.adobe.aps.pdf.printHigh" Access="ALLOW" xmlns:ns14="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" /> 
  
          <Principal PrincipalNameType="SYSTEM"> 
             <PrincipalDomain>EDC_SPECIAL</PrincipalDomain> 
  
             <PrincipalName>publisher</PrincipalName> 
          </Principal> 
       </PolicyEntry> 
  
       <OfflineLeasePeriod> 
          <Duration>P31D</Duration> 
       </OfflineLeasePeriod> 
  
       <AuditSettings isTracked="true" /> 
  
       <PolicyValidityPeriod isAbsoluteTime="false"> 
          <ValidityPeriodRelative> 
             <NotBeforeRelative>PT0S</NotBeforeRelative> 
  
             <NotAfterRelative>P20D</NotAfterRelative> 
          </ValidityPeriodRelative> 
       </PolicyValidityPeriod> 
 </Policy> 
 
```

>[!NOTE]
>
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Um eine Richtlinie zu erstellen, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Legen Sie die Attribute der Richtlinie fest.
1. Erstellen Sie einen Richtlinieneintrag.
1. Registrieren Sie die Richtlinie.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-rightsmanagement-client.jar
* namespace.jar (wenn AEM Forms auf JBoss bereitgestellt wird)
* jaxb-api.jar (wenn AEM Forms auf JBoss bereitgestellt wird)
* jaxb-impl.jar (wenn AEM Forms auf JBoss bereitgestellt wird)
* jaxb-libs.jar (wenn AEM Forms auf JBoss bereitgestellt wird)
* jaxb-xjc.jar (wenn AEM Forms auf JBoss bereitgestellt wird)
* relaxngDatatype.jar (wenn AEM Forms auf JBoss bereitgestellt wird)
* xsdlib.jar (wenn AEM Forms auf JBoss bereitgestellt wird)
* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar
* jbossall-client.jar (verwenden Sie eine andere JAR-Datei, wenn AEM Forms nicht auf JBoss bereitgestellt ist)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert durchführen können, erstellen Sie ein Client-Objekt des Document Security-Dienstes.

**Festlegen der Richtlinienattribute**

Legen Sie zum Erstellen einer Richtlinie Richtlinienattribute fest. Ein obligatorisches Attribut ist der Richtlinienname. Richtliniennamen müssen für jeden Richtliniensatz eindeutig sein. Ein Richtliniensatz ist lediglich eine Sammlung von Richtlinien. Es kann zwei Richtlinien mit demselben Namen geben, wenn die Richtlinien zu separaten Richtliniensätzen gehören. Zwei Richtlinien in einem einzigen Richtliniensatz dürfen jedoch nicht denselben Richtliniennamen haben.

Ein weiteres nützliches Attribut, das festgelegt werden kann, ist der Gültigkeitszeitraum. Ein Gültigkeitszeitraum ist der Zeitraum, in dem autorisierte Empfänger auf ein richtliniengeschütztes Dokument zugreifen können. Wenn Sie dieses Attribut nicht festlegen, ist die Richtlinie immer gültig.

Für einen Gültigkeitszeitraum kann eine der folgenden Optionen festgelegt werden:

* Eine bestimmte Anzahl von Tagen, an denen das Dokument ab der Veröffentlichung des Dokuments verfügbar ist
* Enddatum, nach dem das Dokument nicht mehr verfügbar ist
* Ein bestimmter Datumsbereich, auf den das Dokument zugreifen kann
* Immer gültig

Sie können nur ein Startdatum angeben, was dazu führt, dass die Richtlinie nach dem Startdatum gültig ist. Wenn Sie nur ein Enddatum angeben, ist die Richtlinie bis zum Enddatum gültig. Eine Ausnahme wird jedoch ausgelöst, wenn sowohl ein Start- als auch ein Enddatum nicht definiert sind.

Beim Festlegen von Attributen, die zu einer Richtlinie gehören, können Sie auch Verschlüsselungseinstellungen festlegen. Diese Verschlüsselungseinstellungen wirken sich darauf aus, wenn die Richtlinie auf ein Dokument angewendet wird. Sie können die folgenden Verschlüsselungswerte angeben:

* **AES 256**: Stellt den AES-Verschlüsselungsalgorithmus mit einem 256-Bit-Schlüssel dar.
* **AES128**: Stellt den AES-Verschlüsselungsalgorithmus mit einem 128-Bit-Schlüssel dar.
* **NoEncryption:** Stellt keine Verschlüsselung dar.

Wenn Sie die `NoEncryption` -Option können Sie die `PlaintextMetadata` -Option `false`. Wenn Sie dies versuchen, wird eine Ausnahme ausgelöst.

>[!NOTE]
>
>Weitere Informationen zu anderen Attributen, die Sie festlegen können, finden Sie unter `Policy` Beschreibung der Benutzeroberfläche in [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Einen Richtlinieneintrag erstellen**

Ein Richtlinieneintrag hängt Prinzipale, d. h. Gruppen und Benutzer, sowie Berechtigungen an eine Richtlinie an. Eine Richtlinie muss mindestens einen Richtlinieneintrag enthalten. Assume, for example, that you perform these tasks:

* Create and register a policy entry that enables a group to only view a document while online and prohibits recipients from copying it.
* Attach the policy entry to the policy.
* Sichern Sie ein Dokument mit der Richtlinie mithilfe von Acrobat.

Dadurch können Empfänger das Dokument nur online anzeigen und nicht kopieren. Das Dokument bleibt sicher, bis die Sicherheit entfernt wurde.

**Richtlinie registrieren**

Eine neue Richtlinie muss registriert sein, bevor sie verwendet werden kann. Nachdem Sie eine Richtlinie registriert haben, können Sie sie zum Schutz von Dokumenten verwenden.

### Erstellen einer Richtlinie mit der Java-API {#create-a-policy-using-the-java-api}

Erstellen Sie eine Richtlinie mithilfe der Document Security-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocumentSecurityClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Legen Sie die Attribute der Richtlinie fest.

   * Erstellen Sie eine `Policy` -Objekt durch Aufrufen der `InfomodelObjectFactory` Statische Objektform `createPolicy` -Methode. Diese Methode gibt eine `Policy` -Objekt.
   * Legen Sie das Namensattribut der Richtlinie fest, indem Sie die `Policy` -Objekt `setName` -Methode verwenden und einen string -Wert übergeben, der den Richtliniennamen angibt.
   * Legen Sie die Beschreibung der Richtlinie fest, indem Sie die `Policy` -Objekt `setDescription` -Methode verwenden und einen string -Wert übergeben, der die Beschreibung der Richtlinie angibt.
   * Legen Sie den Richtliniensatz fest, zu dem die neue Richtlinie gehört, indem Sie die `Policy` -Objekt `setPolicySetName` -Methode verwenden und einen string -Wert übergeben, der den Namen des Richtliniensatzes angibt. (Sie können `null` für diesen Parameterwert, der dazu führt, dass die Richtlinie zum *Meine Richtlinien* Richtliniensatz.)
   * Erstellen Sie den Gültigkeitszeitraum der Richtlinie durch Aufrufen der `InfomodelObjectFactory` Statische Objektform `createValidityPeriod` -Methode. Diese Methode gibt eine `ValidityPeriod` -Objekt.
   * Legen Sie die Anzahl der Tage fest, für die auf ein richtliniengeschütztes Dokument zugegriffen werden kann, indem Sie die `ValidityPeriod` -Objekt `setRelativeExpirationDays` -Methode verwenden und einen ganzzahligen Wert übergeben, der die Anzahl der Tage angibt.
   * Legen Sie den Gültigkeitszeitraum der Richtlinie fest, indem Sie die `Policy` -Objekt `setValidityPeriod` -Methode und Übergabe der `ValidityPeriod` -Objekt.

1. Erstellen Sie einen Richtlinieneintrag.

   * Erstellen Sie einen Richtlinieneintrag durch Aufrufen der `InfomodelObjectFactory` Statische Objektform `createPolicyEntry` -Methode. Diese Methode gibt eine `PolicyEntry` -Objekt.
   * Geben Sie die Berechtigungen der Richtlinie an, indem Sie die `InfomodelObjectFactory` Statische Objektform `createPermission` -Methode. Übergeben Sie ein statisches Datenelement, das zum `Permission` -Schnittstelle, die die Berechtigung darstellt. Diese Methode gibt eine `Permission` -Objekt. Um beispielsweise die Berechtigung hinzuzufügen, mit der Benutzer Daten aus einem richtliniengeschützten PDF kopieren können, übergeben Sie `Permission.COPY`. (Wiederholen Sie diesen Schritt für jede hinzuzufügende Berechtigung.)
   * Fügen Sie die Berechtigung zum Richtlinieneintrag hinzu, indem Sie die `PolicyEntry` -Objekt `addPermission` -Methode und Übergabe der `Permission` -Objekt. (Wiederholen Sie diesen Schritt für jeden `Permission` -Objekt).
   * Erstellen Sie den Richtlinienprinzipal durch Aufrufen der `InfomodelObjectFactory` Statische Objektform `createSpecialPrincipal` -Methode. Übergeben eines Datenelements, das zu der `InfomodelObjectFactory` -Objekt, das den Prinzipal darstellt. Diese Methode gibt eine `Principal` -Objekt. Um beispielsweise den Herausgeber des Dokuments als Prinzipal hinzuzufügen, übergeben Sie `InfomodelObjectFactory.PUBLISHER_PRINCIPAL`.
   * Fügen Sie den Prinzipal zum Richtlinieneintrag hinzu, indem Sie die `PolicyEntry` -Objekt `setPrincipal`-Methode und Übergabe der `Principal` -Objekt.
   * Fügen Sie den Richtlinieneintrag zur Richtlinie hinzu, indem Sie die `Policy` -Objekt `addPolicyEntry` -Methode und Übergabe der `PolicyEntry` -Objekt.

1. Registrieren Sie die Richtlinie.

   * Erstellen Sie eine `PolicyManager` -Objekt durch Aufrufen der `DocumentSecurityClient` -Objekt `getPolicyManager` -Methode.
   * Registrieren Sie die Richtlinie, indem Sie die `PolicyManager` -Objekt `registerPolicy` -Methode verwenden und die folgenden Werte übergeben:

      * Die `Policy` -Objekt, das die zu registrierende Richtlinie darstellt.
   * Ein string -Wert für den Richtliniensatz, zu dem die Richtlinie gehört.

   Wenn Sie in den Verbindungseinstellungen ein AEM Forms-Administratorkonto verwenden, erstellen Sie die `DocumentSecurityClient` -Objekt ein und geben Sie dann den Namen des Richtliniensatzes an, wenn Sie die `registerPolicy` -Methode. Wenn Sie eine `null` für den Richtliniensatz, wird die Richtlinie in den Administratoren erstellt. *Meine Richtlinien* Richtliniensatz.

   Wenn Sie einen Document Security-Benutzer in den Verbindungseinstellungen verwenden, können Sie die überladene `registerPolicy` -Methode, die nur die Richtlinie akzeptiert. Das heißt, Sie müssen den Richtliniensatznamen nicht angeben. Die Richtlinie wird jedoch dem Richtliniensatz mit dem Namen *Meine Richtlinien*. Wenn Sie diesem Richtliniensatz die neue Richtlinie nicht hinzufügen möchten, geben Sie beim Aufrufen der `registerPolicy` -Methode.

   >[!NOTE]
   >
   >Referenzieren Sie beim Erstellen einer Richtlinie einen vorhandenen Richtliniensatz. Wenn Sie einen Richtliniensatz angeben, der nicht vorhanden ist, wird eine Ausnahme ausgelöst.

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie unter folgenden Themen:

* &quot;Schnellstart (SOAP-Modus): Erstellen einer Richtlinie mit der Java-API&quot;

### Erstellen einer Richtlinie mithilfe der Webdienst-API {#create-a-policy-using-the-web-service-api}

Erstellen Sie eine Richtlinie mithilfe der Document Security-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie eine `DocumentSecurityServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `DocumentSecurityServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `RightsManagementServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.


1. Legen Sie die Attribute der Richtlinie fest.

   * Erstellen Sie ein Objekt `PolicySpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Namen der Richtlinie fest, indem Sie dem `PolicySpec` -Objekt `name` Datenelement.
   * Legen Sie die Beschreibung der Richtlinie fest, indem Sie dem `PolicySpec` -Objekt `description` Datenelement.
   * Legen Sie den Richtliniensatz fest, zu dem die Richtlinie gehören soll, indem Sie dem `PolicySpec` -Objekt `policySetName` Datenelement. Sie müssen einen vorhandenen Richtliniensatznamen angeben. (Sie können `null` für diesen Parameterwert, der dazu führt, dass die Richtlinie zu *Meine Richtlinien*.
   * Legen Sie die Offline-Nutzungsdauer der Richtlinie fest, indem Sie dem `PolicySpec` -Objekt `offlineLeasePeriod` Datenelement.
   * Legen Sie die `PolicySpec` -Objekt `policyXml` -Datenelement mit einem string -Wert, der PDRL-XML-Daten darstellt. Erstellen Sie dazu eine .NET-Datei `StreamReader` -Objekt durch Verwendung seines -Konstruktors. Übergeben Sie den Speicherort einer PDRL-XML-Datei, die die Richtlinie darstellt, an die `StreamReader` -Konstruktor. Rufen Sie als Nächstes die `StreamReader` -Objekt `ReadLine` -Methode und weisen Sie den Rückgabewert einer Zeichenfolgenvariablen zu. Iteration durch die `StreamReader` -Objekt bis zum `ReadLine` -Methode gibt null zurück. Weisen Sie die Zeichenfolgenvariable dem `PolicySpec` -Objekt `policyXml` Datenelement.

1. Erstellen Sie einen Richtlinieneintrag.

   Es ist nicht erforderlich, beim Erstellen einer Richtlinie mithilfe der Document Security-Webdienst-API einen Richtlinieneintrag zu erstellen. Der Richtlinieneintrag wird im PDRL-Dokument definiert.

1. Registrieren Sie die Richtlinie.

   Registrieren Sie die Richtlinie, indem Sie die `DocumentSecurityServiceClient` -Objekt `registerPolicy` -Methode verwenden und die folgenden Werte übergeben:

   * Die `PolicySpec` -Objekt, das die zu registrierende Richtlinie darstellt.
   * Ein string -Wert für den Richtliniensatz, zu dem die Richtlinie gehört. Sie können eine `null` -Wert, der dazu führt, dass die Richtlinie zum *MyPolies* Richtliniensatz.

   Wenn Sie in den Verbindungseinstellungen ein AEM Forms-Administratorkonto verwenden, erstellen Sie die `DocumentSecurityClient` -Objekt, geben Sie den Richtliniensatznamen an, wenn Sie die `registerPolicy` -Methode.

   Wenn Sie einen Document Security-Benutzer in den Verbindungseinstellungen verwenden, können Sie die überladene `registerPolicy` -Methode, die nur die Richtlinie akzeptiert. Das heißt, Sie müssen den Richtliniensatznamen nicht angeben. Die Richtlinie wird jedoch dem Richtliniensatz mit dem Namen *Meine Richtlinien*. Wenn Sie diesem Richtliniensatz die neue Richtlinie nicht hinzufügen möchten, geben Sie beim Aufrufen der `registerPolicy` -Methode.

   >[!NOTE]
   >
   >Stellen Sie beim Erstellen einer Richtlinie und beim Angeben eines Richtliniensatzes sicher, dass Sie einen vorhandenen Richtliniensatz angeben. Wenn Sie einen Richtliniensatz angeben, der nicht vorhanden ist, wird eine Ausnahme ausgelöst.

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (MTOM): Erstellen einer Richtlinie mithilfe der Webdienst-API&quot;
* &quot;Schnellstart (SwaRef): Erstellen einer Richtlinie mithilfe der Webdienst-API&quot;

## Ändern von Richtlinien {#modifying-policies}

You can modify an existing policy using the Document Security Java API or web service API. Um Änderungen an einer vorhandenen Richtlinie vorzunehmen, rufen Sie sie ab, ändern Sie sie und aktualisieren Sie dann die Richtlinie auf dem Server. Angenommen, Sie rufen eine vorhandene Richtlinie ab und verlängern ihre Gültigkeitsdauer. Bevor die Änderung wirksam wird, müssen Sie die Richtlinie aktualisieren.

Sie können eine Richtlinie ändern, wenn sich die Geschäftsanforderungen ändern und die Richtlinie diese Anforderungen nicht mehr widerspiegelt. Anstatt eine neue Richtlinie zu erstellen, können Sie einfach eine vorhandene Richtlinie aktualisieren.

Um Richtlinienattribute mithilfe eines Webdiensts zu ändern (z. B. mithilfe von Java-Proxy-Klassen, die mit JAX-WS erstellt wurden), müssen Sie sicherstellen, dass die Richtlinie beim Document Security-Dienst registriert ist. Anschließend können Sie mithilfe der `PolicySpec.getPolicyXml` -Methode verwenden und die Richtlinienattribute mithilfe der entsprechenden Methoden ändern. Sie können beispielsweise die Offline-Nutzungsdauer ändern, indem Sie die `PolicySpec.setOfflineLeasePeriod` -Methode.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Um eine vorhandene Richtlinie zu ändern, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Abrufen einer vorhandenen Richtlinie.
1. Richtlinienattribute ändern.
1. Aktualisieren Sie die Richtlinie.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Client-Objekt des Document Security-Dienstes erstellen. Wenn Sie die Java-API verwenden, erstellen Sie eine `RightsManagementClient` -Objekt. Wenn Sie die Document Security-Webdienst-API verwenden, erstellen Sie eine `RightsManagementServiceService` -Objekt.

**Vorhandene Richtlinie abrufen**

Sie müssen eine vorhandene Richtlinie abrufen, um sie zu ändern. Um eine Richtlinie abzurufen, geben Sie den Richtliniennamen und den Richtliniensatz an, zu dem die Richtlinie gehört. Wenn Sie eine `null` für den Richtliniensatznamen, wird die Richtlinie aus dem *Meine Richtlinien* Richtliniensatz.

**Festlegen der Richtlinienattribute**

Um eine Richtlinie zu ändern, ändern Sie den Wert von Richtlinienattributen. Das einzige Richtlinienattribut, das Sie nicht ändern können, ist das Attribut name . Um beispielsweise die Offline-Nutzungsdauer der Richtlinie zu ändern, können Sie den Wert des Attributs für die Offline-Nutzungsdauer der Richtlinie ändern.

Wenn Sie die Offline-Nutzungsdauer einer Richtlinie mithilfe eines Webdiensts ändern, wird die Variable `offlineLeasePeriod` im Feld `PolicySpec` -Benutzeroberfläche ignoriert wird. Um die Offline-Nutzungsdauer zu aktualisieren, ändern Sie die `OfflineLeasePeriod` -Element im XML-Dokument PDRL. Verweisen Sie dann mithilfe der `PolicySpec` -Schnittstelle `policyXML` Datenelement.

>[!NOTE]
>
>Weitere Informationen zu anderen Attributen, die Sie festlegen können, finden Sie unter `Policy` Beschreibung der Benutzeroberfläche in [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Richtlinie aktualisieren**

Before the changes that you make to a policy take affect, you must update the policy with the Document Security service. Änderungen an Richtlinien, die Dokumente schützen, werden aktualisiert, wenn das richtliniengeschützte Dokument das nächste Mal mit dem Document Security-Dienst synchronisiert wird.

### Vorhandene Richtlinien mithilfe der Java-API ändern {#modify-existing-policies-using-the-java-api}

Ändern Sie eine vorhandene Richtlinie mithilfe der Document Security-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `RightsManagementClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen einer vorhandenen Richtlinie.

   * Erstellen Sie eine `PolicyManager` -Objekt durch Aufrufen der `RightsManagementClient` -Objekt `getPolicyManager` -Methode.
   * Erstellen Sie eine `Policy` -Objekt, das die zu aktualisierende Richtlinie darstellt, indem das `PolicyManager` -Objekt `getPolicy` Methode und Übergabe der folgenden Werte&quot;

      * Ein string -Wert, der den Richtliniensatznamen darstellt, zu dem die Richtlinie gehört. Sie können `null` dass `MyPolicies` verwendeter Richtliniensatz.
      * Ein string -Wert, der den Richtliniennamen darstellt.

1. Legen Sie die Attribute der Richtlinie fest.

   Ändern Sie die Attribute der Richtlinie entsprechend Ihren Geschäftsanforderungen. Um beispielsweise die Offline-Nutzungsdauer der Richtlinie zu ändern, rufen Sie die `Policy` -Objekt `setOfflineLeasePeriod` -Methode.

1. Aktualisieren Sie die Richtlinie.

   Aktualisieren der Richtlinie durch Aufrufen von `PolicyManager` -Objekt `updatePolicy` -Methode. Übergeben Sie die `Policy` -Objekt, das die zu aktualisierende Richtlinie darstellt.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie im Schnellstart-Modus (SOAP-Modus): Ändern einer Richtlinie mithilfe des Abschnitts Java-API .

### Vorhandene Richtlinien mithilfe der Webdienst-API ändern {#modify-existing-policies-using-the-web-service-api}

Ändern Sie eine vorhandene Richtlinie mithilfe der Document Security-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie eine `RightsManagementServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `RightsManagementServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `RightsManagementServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.


1. Abrufen einer vorhandenen Richtlinie.

   Erstellen Sie eine `PolicySpec` -Objekt, das die zu ändernde Richtlinie darstellt, indem das `RightsManagementServiceClient` -Objekt `getPolicy` -Methode verwenden und die folgenden Werte übergeben:

   * Ein string -Wert, der den Richtliniensatznamen angibt, zu dem die Richtlinie gehört. Sie können `null` dass `MyPolicies` verwendeter Richtliniensatz.
   * Ein string -Wert, der den Namen der Richtlinie angibt.

1. Legen Sie die Attribute der Richtlinie fest.

   Ändern Sie die Attribute der Richtlinie entsprechend Ihren Geschäftsanforderungen.

1. Aktualisieren Sie die Richtlinie.

   Aktualisieren Sie die Richtlinie, indem Sie die `RightsManagementServiceClient` -Objekt `updatePolicyFromSDK` -Methode und Übergabe der `PolicySpec` -Objekt, das die zu aktualisierende Richtlinie darstellt.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (MTOM): Ändern einer Richtlinie mithilfe der Webdienst-API&quot;
* &quot;Schnellstart (SwaRef): Ändern einer Richtlinie mithilfe der Webdienst-API&quot;

## Löschen von Richtlinien {#deleting-policies}

Sie können eine vorhandene Richtlinie mithilfe der Document Security Java-API oder der Web Service-API löschen. Nachdem eine Richtlinie gelöscht wurde, kann sie nicht mehr zum Schutz von Dokumenten verwendet werden. Vorhandene richtliniengeschützte Dokumente, die die Richtlinie verwenden, sind jedoch weiterhin geschützt. Sie können eine Richtlinie löschen, wenn eine neuere verfügbar ist.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-2}

Um eine vorhandene Richtlinie zu löschen, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Löschen Sie die Richtlinie.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Client-Objekt des Document Security-Dienstes erstellen. Wenn Sie die Java-API verwenden, erstellen Sie eine `RightsManagementClient` -Objekt. Wenn Sie die Document Security-Webdienst-API verwenden, erstellen Sie eine `RightsManagementServiceService` -Objekt.

**Richtlinie löschen**

Um eine Richtlinie zu löschen, geben Sie die zu löschende Richtlinie und den Richtliniensatz an, zu dem die Richtlinie gehört. Der Benutzer, dessen Einstellungen zum Aufrufen von AEM Forms verwendet werden, muss über die Berechtigung zum Löschen der Richtlinie verfügen. andernfalls tritt eine Ausnahme auf. Wenn Sie versuchen, eine nicht vorhandene Richtlinie zu löschen, tritt ebenfalls eine Ausnahme auf.

### Richtlinien mithilfe der Java-API löschen {#delete-policies-using-the-java-api}

Löschen Sie eine Richtlinie mithilfe der Document Security-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `RightsManagementClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Löschen Sie die Richtlinie.

   * Erstellen Sie eine `PolicyManager` -Objekt durch Aufrufen der `RightsManagementClient` -Objekt `getPolicyManager` -Methode.
   * Löschen Sie die Richtlinie, indem Sie die `PolicyManager` -Objekt `deletePolicy` -Methode verwenden und die folgenden Werte übergeben:

      * Ein string -Wert, der den Richtliniensatznamen angibt, zu dem die Richtlinie gehört. Sie können `null` dass `MyPolicies` verwendeter Richtliniensatz.
      * Ein string -Wert, der den Namen der zu löschenden Richtlinie angibt.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (SOAP-Modus): Löschen einer Richtlinie mithilfe der Java-API&quot;

### Richtlinien mithilfe der Webdienst-API löschen {#delete-policies-using-the-web-service-api}

Löschen Sie eine Richtlinie mithilfe der Document Security-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie eine `RightsManagementServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `RightsManagementServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `RightsManagementServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.


1. Löschen Sie die Richtlinie.

   Löschen einer Richtlinie durch Aufrufen der `RightsManagementServiceClient` -Objekt `deletePolicy` -Methode verwenden und die folgenden Werte übergeben:

   * Ein string -Wert, der den Richtliniensatznamen angibt, zu dem die Richtlinie gehört. Sie können `null` dass `MyPolicies` verwendeter Richtliniensatz.
   * Ein string -Wert, der den Namen der zu löschenden Richtlinie angibt.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (MTOM): Löschen einer Richtlinie mithilfe der Webdienst-API&quot;
* &quot;Schnellstart (SwaRef): Löschen einer Richtlinie mithilfe der Webdienst-API&quot;

## Anwenden von Richtlinien auf PDF-Dokumente {#applying-policies-to-pdf-documents}

Sie können eine Richtlinie auf ein PDF-Dokument anwenden, um das Dokument zu schützen. Durch Anwendung einer Richtlinie auf ein PDF-Dokument können Sie den Zugriff auf das Dokument einschränken. Sie können eine Richtlinie nicht auf ein Dokument anwenden, wenn das Dokument bereits mit einer Richtlinie gesichert ist.

Während das Dokument geöffnet ist, können Sie auch den Zugriff auf Acrobat- und Adobe Reader-Funktionen einschränken, einschließlich der Möglichkeit, Text zu drucken und zu kopieren, Änderungen vorzunehmen und Signaturen und Kommentare zu einem Dokument hinzuzufügen. Darüber hinaus können Sie ein richtliniengeschütztes PDF-Dokument sperren, wenn Sie nicht mehr möchten, dass Benutzer auf das Dokument zugreifen.

Sie können die Verwendung eines richtliniengeschützten Dokuments nach dessen Verteilung überwachen. Das heißt, Sie können sehen, wie das Dokument verwendet wird und wer es verwendet. Sie können zum Beispiel herausfinden, wann jemand das Dokument geöffnet hat.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-3}

So wenden Sie eine Richtlinie auf ein PDF-Dokument an:

1. Projektdateien einschließen.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Rufen Sie ein PDF-Dokument ab, auf das eine Richtlinie angewendet wird.
1. Anwenden einer vorhandenen Richtlinie auf das PDF-Dokument.
1. Speichern Sie das richtliniengeschützte PDF-Dokument.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert durchführen können, erstellen Sie ein Client-Objekt des Document Security-Dienstes. Wenn Sie die Java-API verwenden, erstellen Sie eine `DocumentSecurityClient` -Objekt. Wenn Sie die Document Security-Webdienst-API verwenden, erstellen Sie eine `DocumentSecurityServiceService` -Objekt.

**Abrufen eines PDF-Dokuments**

Sie können ein PDF-Dokument abrufen, um eine Richtlinie anzuwenden. Nachdem Sie eine Richtlinie auf das PDF-Dokument angewendet haben, sind die Benutzer bei der Verwendung des Dokuments eingeschränkt. Wenn die Richtlinie beispielsweise nicht das Öffnen des Dokuments im Offline-Modus aktiviert, müssen die Benutzer online sein, um das Dokument zu öffnen.

**Vorhandene Richtlinie auf das PDF-Dokument anwenden**

Um eine Richtlinie auf ein PDF-Dokument anzuwenden, verweisen Sie auf eine vorhandene Richtlinie und geben Sie an, zu welchem Richtliniensatz die Richtlinie gehört. Der Benutzer, der die Verbindungseigenschaften festlegt, muss Zugriff auf die angegebene Richtlinie haben. Wenn nicht, tritt eine Ausnahme auf.

**PDF-Dokument speichern**

Nachdem der Document Security-Dienst eine Richtlinie auf ein PDF-Dokument angewendet hat, können Sie das richtliniengeschützte PDF-Dokument als PDF-Datei speichern.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Zugriff auf Dokumente sperren](protecting-documents-policies.md#revoking-access-to-documents)

### Anwenden einer Richtlinie auf ein PDF-Dokument mithilfe der Java-API {#apply-a-policy-to-a-pdf-document-using-the-java-api}

Wenden Sie mithilfe der Document Security-API (Java) eine Richtlinie auf ein PDF-Dokument an:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `RightsManagementClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie ein PDF-Dokument ab.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das PDF-Dokument mithilfe seines Konstruktors darstellt. Übergeben Sie einen string -Wert, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Anwenden einer vorhandenen Richtlinie auf das PDF-Dokument.

   * Erstellen Sie eine `DocumentManager` -Objekt durch Aufrufen der `RightsManagementClient` -Objekt `getDocumentManager` -Methode.
   * Wenden Sie eine Richtlinie auf das PDF-Dokument an, indem Sie die `DocumentManager` -Objekt `protectDocument` -Methode verwenden und die folgenden Werte übergeben:

      * Die `com.adobe.idp.Document` -Objekt, das das PDF-Dokument enthält, auf das die Richtlinie angewendet wird.
      * Ein string -Wert, der den Namen des Dokuments angibt.
      * Ein string -Wert, der den Namen des Richtliniensatzes angibt, zu dem die Richtlinie gehört. Sie können eine `null` -Wert, der zu `MyPolicies` verwendeter Richtliniensatz.
      * Ein string -Wert, der den Richtliniennamen angibt.
      * Ein string -Wert für den Namen der User Manager-Domäne des Benutzers, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann null sein. (Wenn dieser Parameter null ist, muss der nächste Parameterwert null sein.)
      * Ein string -Wert, der den Namen des kanonischen Benutzers des User Manager-Benutzers darstellt, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann `null` (Wenn dieser Parameter null ist, muss der vorherige Parameterwert `null`).
      * A `com.adobe.livecycle.rightsmanagement.Locale` , das das Gebietsschema darstellt, das für die Auswahl der MS Office-Vorlage verwendet wird. Dieser Parameterwert ist optional und wird nicht für PDF-Dokumente verwendet. Um ein PDF-Dokument zu sichern, geben Sie `null`.

      Die `protectDocument` -Methode gibt eine `RMSecureDocumentResult` -Objekt, das das richtliniengeschützte PDF-Dokument enthält.


1. Speichern Sie das PDF-Dokument.

   * Rufen Sie die `RMSecureDocumentResult` -Objekt `getProtectedDoc` -Methode, um das richtliniengeschützte PDF-Dokument abzurufen. Diese Methode gibt eine `com.adobe.idp.Document` -Objekt.
   * Erstellen Sie eine `java.io.File` -Objekt ein und stellen Sie sicher, dass die Dateierweiterung PDF ist.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `Document` -Objekt auf die Datei verweist (stellen Sie sicher, dass Sie die `Document` -Objekt, das von der `getProtectedDoc` -Methode).

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (EJB-Modus): Anwenden einer Richtlinie auf ein PDF-Dokument mithilfe der Java-API&quot;
* &quot;Schnellstart (SOAP-Modus): Anwenden einer Richtlinie auf ein PDF-Dokument mithilfe der Java-API&quot;

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Anwenden einer Richtlinie auf ein PDF-Dokument mithilfe der Webdienst-API {#apply-a-policy-to-a-pdf-document-using-the-web-service-api}

Wenden Sie mithilfe der Document Security-API (Webdienst) eine Richtlinie auf ein PDF-Dokument an:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie eine `RightsManagementServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `RightsManagementServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `RightsManagementServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.


1. Rufen Sie ein PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern eines PDF-Dokuments verwendet, auf das eine Richtlinie angewendet wird.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Bestimmen Sie die Byte-Array-Größe, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Feld mit dem Inhalt des Byte-Arrays.

1. Anwenden einer vorhandenen Richtlinie auf das PDF-Dokument.

   Wenden Sie eine Richtlinie auf das PDF-Dokument an, indem Sie die `RightsManagementServiceClient` -Objekt `protectDocument` -Methode verwenden und die folgenden Werte übergeben:

   * Die `BLOB` -Objekt, das das PDF-Dokument enthält, auf das die Richtlinie angewendet wird.
   * Ein string -Wert, der den Namen des Dokuments angibt.
   * Ein string -Wert, der den Namen des Richtliniensatzes angibt, zu dem die Richtlinie gehört. You can specify a `null` value that results in the `MyPolicies` policy set being used.
   * Ein string -Wert, der den Richtliniennamen angibt.
   * Ein string -Wert für den Namen der User Manager-Domäne des Benutzers, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann null sein. (Wenn dieser Parameter null ist, muss der nächste Parameterwert `null`).
   * Ein string -Wert, der den Namen des kanonischen Benutzers des User Manager-Benutzers darstellt, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann null sein. (Wenn dieser Parameter null ist, muss der vorherige Parameterwert `null`).
   * A `RMLocale` -Wert, der den Gebietsschemawert angibt (z. B. `RMLocale.en`).
   * Ein string -Ausgabeparameter, der zum Speichern des Richtlinienkennungswerts verwendet wird.
   * Ein string -Ausgabeparameter, der zum Speichern des richtliniengeschützten Bezeichnerwerts verwendet wird.
   * Ein string -Ausgabeparameter, der zum Speichern des MIME-Typs verwendet wird (z. B. `application/pdf`).

   Die `protectDocument` -Methode gibt eine `BLOB` -Objekt, das das richtliniengeschützte PDF-Dokument enthält.

1. Speichern Sie das PDF-Dokument.

   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines string-Werts, der den Dateispeicherort des richtliniengeschützten PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt der `BLOB` -Objekt, das von der `protectDocument` -Methode. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` Datenelement.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (MTOM): Anwenden einer Richtlinie auf ein PDF-Dokument mithilfe der Webdienst-API&quot;
* &quot;Schnellstart (SwaRef): Anwenden einer Richtlinie auf ein PDF-Dokument mithilfe der Webdienst-API&quot;

## Entfernen von Richtlinien aus PDF-Dokumenten {#removing-policies-from-pdf-documents}

Sie können eine Richtlinie aus einem richtliniengeschützten Dokument entfernen, um die Sicherheit aus dem Dokument zu entfernen. Das heißt, wenn das Dokument nicht mehr durch eine Richtlinie geschützt werden soll. Wenn Sie ein richtliniengeschütztes Dokument mit einer neueren Richtlinie aktualisieren möchten, ist es effizienter, die Richtlinie zu wechseln, anstatt die Richtlinie zu entfernen und die aktualisierte Richtlinie hinzuzufügen.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-4}

So entfernen Sie eine Richtlinie aus einem richtliniengeschützten PDF-Dokument:

1. Projektdateien einschließen
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Abrufen eines richtliniengeschützten PDF-Dokuments.
1. Entfernen Sie die Richtlinie aus dem PDF-Dokument.
1. Speichern Sie das ungesicherte PDF-Dokument.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert durchführen können, erstellen Sie ein Client-Objekt des Document Security-Dienstes.

**Abrufen eines richtliniengeschützten PDF-Dokuments**

Sie können ein richtliniengeschütztes PDF-Dokument abrufen, um eine Richtlinie zu entfernen. Wenn Sie versuchen, eine Richtlinie aus einem PDF-Dokument zu entfernen, das nicht durch eine Richtlinie geschützt ist, wird eine Ausnahme verursacht.

**Richtlinie aus dem PDF-Dokument entfernen**

Sie können eine Richtlinie aus einem richtliniengeschützten PDF-Dokument entfernen, sofern in den Verbindungseinstellungen ein Administrator angegeben ist. Ist dies nicht der Fall, muss die zum Schützen eines Dokuments verwendete Richtlinie die `SWITCH_POLICY` -Berechtigung, um eine Richtlinie aus einem PDF-Dokument zu entfernen. Außerdem muss der in den AEM Forms-Verbindungseinstellungen angegebene Benutzer über diese Berechtigung verfügen. Andernfalls wird eine Ausnahme ausgelöst.

**Ungesichertes PDF-Dokument speichern**

Nachdem der Document Security-Dienst eine Richtlinie aus einem PDF-Dokument entfernt hat, können Sie das ungesicherte PDF-Dokument als PDF-Datei speichern.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Anwenden von Richtlinien auf PDF-Dokumente](protecting-documents-policies.md#applying-policies-to-pdf-documents)

### Eine Richtlinie mithilfe der Java-API aus einem PDF-Dokument entfernen {#remove-a-policy-from-a-pdf-document-using-the-java-api}

Entfernen Sie mithilfe der Document Security-API (Java) eine Richtlinie aus einem richtliniengeschützten PDF-Dokument:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocumentSecurityClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen eines richtliniengeschützten PDF-Dokuments.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das richtliniengeschützte PDF-Dokument darstellt, indem es seinen Konstruktor verwendet und einen Zeichenfolgenwert übergibt, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entfernen Sie die Richtlinie aus dem PDF-Dokument.

   * Erstellen Sie eine `DocumentManager` -Objekt durch Aufrufen der `DocumentSecurityClient` -Objekt `getDocumentManager` -Methode.
   * Entfernen Sie eine Richtlinie aus dem PDF-Dokument, indem Sie die `DocumentManager` -Objekt `removeSecurity` -Methode und Übergabe der `com.adobe.idp.Document` -Objekt, das das richtliniengeschützte PDF-Dokument enthält. Diese Methode gibt eine `com.adobe.idp.Document` -Objekt, das ein nicht gesichertes PDF-Dokument enthält.

1. Speichern Sie das ungesicherte PDF-Dokument.

   * Erstellen Sie eine `java.io.File` -Objekt ein und stellen Sie sicher, dass die Dateierweiterung PDF ist.
   * Rufen Sie die `Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `Document` -Objekt auf die Datei verweist (stellen Sie sicher, dass Sie die `Document` -Objekt, das von der `removeSecurity` -Methode).

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (SOAP-Modus): Entfernen einer Richtlinie aus einem PDF-Dokument mithilfe der Java-API&quot;

### Eine Richtlinie mithilfe der Webdienst-API entfernen {#remove-a-policy-using-the-web-service-api}

Entfernen Sie mithilfe der Document Security-API (Webdienst) eine Richtlinie aus einem richtliniengeschützten PDF-Dokument:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie eine `DocumentSecurityServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `DocumentSecurityServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `DocumentSecurityServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.


1. Abrufen eines richtliniengeschützten PDF-Dokuments.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern des richtliniengeschützten PDF-Dokuments verwendet, aus dem die Richtlinie entfernt wird.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Feld mit dem Inhalt des Byte-Arrays.

1. Entfernen Sie die Richtlinie aus dem PDF-Dokument.

   Entfernen Sie die Richtlinie aus dem PDF-Dokument, indem Sie die `DocumentSecurityServiceClient` -Objekt `removePolicySecurity` -Methode und Übergabe der `BLOB` -Objekt, das das richtliniengeschützte PDF-Dokument enthält. Diese Methode gibt eine `BLOB` -Objekt, das ein nicht gesichertes PDF-Dokument enthält.

1. Speichern Sie das ungesicherte PDF-Dokument.

   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des ungesicherten PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt der `BLOB` -Objekt, das von der `removePolicySecurity` -Methode. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` -Feld.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (MTOM): Entfernen einer Richtlinie aus einem PDF-Dokument mithilfe der Webdienst-API&quot;
* &quot;Schnellstart (SwaRef): Entfernen einer Richtlinie aus einem PDF-Dokument mithilfe der Webdienst-API&quot;

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Zugriff auf Dokumente sperren {#revoking-access-to-documents}

Sie können den Zugriff auf ein richtliniengeschütztes PDF-Dokument sperren, sodass alle Dokumentkopien für Benutzer nicht zugänglich sind. Wenn ein Benutzer versucht, ein gesperrtes PDF-Dokument zu öffnen, wird er an eine angegebene URL weitergeleitet, wo ein überarbeitetes Dokument angezeigt werden kann. Die URL, an die der Benutzer umgeleitet wird, muss programmatisch angegeben werden. Wenn Sie den Zugriff auf ein Dokument sperren, wird die Änderung wirksam, wenn sich der Benutzer das nächste Mal mit dem Document Security-Dienst synchronisiert, indem er das richtliniengeschützte Dokument online öffnet.

Die Möglichkeit, den Zugriff auf ein Dokument zu sperren, bietet zusätzliche Sicherheit. Angenommen, eine neuere Version eines Dokuments ist verfügbar, und Sie möchten nicht mehr, dass jemand die veraltete Version anzeigt. In diesem Fall kann der Zugriff auf das ältere Dokument widerrufen werden und niemand kann das Dokument anzeigen, es sei denn, der Zugriff wird wieder aktiviert.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-5}

Um ein richtliniengeschütztes Dokument zu sperren, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Abrufen eines richtliniengeschützten PDF-Dokuments.
1. Sperren Sie das richtliniengeschützte Dokument.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Client-Objekt des Document Security-Dienstes erstellen.

**Abrufen eines richtliniengeschützten PDF-Dokuments**

Sie müssen ein richtliniengeschütztes PDF-Dokument abrufen, um es zu widerrufen. Sie können ein Dokument, das bereits gesperrt wurde oder nicht richtliniengeschützt ist, nicht sperren.

Wenn Sie den Wert der Lizenzkennung des richtliniengeschützten Dokuments kennen, ist es nicht erforderlich, das richtliniengeschützte PDF-Dokument abzurufen. In den meisten Fällen müssen Sie jedoch das PDF-Dokument abrufen, um den Wert der Lizenzkennung abrufen zu können.

**Richtliniengeschütztes Dokument sperren**

Um ein richtliniengeschütztes Dokument zu sperren, geben Sie die Lizenzkennung des richtliniengeschützten Dokuments an. Darüber hinaus können Sie die URL eines Dokuments angeben, das der Benutzer anzeigen kann, wenn er versucht, das gesperrte Dokument zu öffnen. Angenommen, ein veraltetes Dokument wird widerrufen. Wenn ein Benutzer versucht, das gesperrte Dokument zu öffnen, wird ihm anstelle des gesperrten Dokuments ein aktualisiertes Dokument angezeigt.

>[!NOTE]
>
>Wenn Sie versuchen, ein bereits gesperrtes Dokument zu widerrufen, wird eine Ausnahme ausgelöst.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Anwenden von Richtlinien auf PDF-Dokumente](protecting-documents-policies.md#applying-policies-to-pdf-documents)

[Neuer Zugriff auf gesperrte Dokumente](protecting-documents-policies.md#reinstating-access-to-revoked-documents)

### Zugriff auf Dokumente mithilfe der Java-API sperren {#revoke-access-to-documents-using-the-java-api}

Sperren Sie mithilfe der Document Security-API (Java) den Zugriff auf ein richtliniengeschütztes PDF-Dokument:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Document Security Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocumentSecurityClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen eines richtliniengeschützten PDF-Dokuments

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das richtliniengeschützte PDF-Dokument darstellt, indem es seinen Konstruktor verwendet und einen Zeichenfolgenwert übergibt, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Richtliniengeschütztes Dokument sperren

   * Erstellen Sie eine `DocumentManager` -Objekt durch Aufrufen der `DocumentSecurityClient` -Objekt `getDocumentManager` -Methode.
   * Rufen Sie den Wert der Lizenzkennung des richtliniengeschützten Dokuments ab, indem Sie die `DocumentManager` -Objekt `getLicenseId` -Methode. Übergeben Sie die `com.adobe.idp.Document` -Objekt, das das richtliniengeschützte Dokument darstellt. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Wert der Lizenzkennung darstellt.
   * Erstellen Sie eine `LicenseManager` -Objekt durch Aufrufen der `DocumentSecurityClient` -Objekt `getLicenseManager` -Methode.
   * Sperren Sie das richtliniengeschützte Dokument, indem Sie die `LicenseManager` -Objekt `revokeLicense` -Methode verwenden und die folgenden Werte übergeben:

      * Ein string -Wert, der den Wert der Lizenzkennung des richtliniengeschützten Dokuments angibt (geben Sie den Rückgabewert von `DocumentManager` -Objekt `getLicenseId` -Methode).
      * Ein statisches Datenelement der `License` -Schnittstelle, die den Grund zum Sperren des Dokuments angibt. Sie können beispielsweise `License.DOCUMENT_REVISED`.
      * A `java.net.URL` -Wert, der den Speicherort angibt, an dem sich ein überarbeitetes Dokument befindet. Wenn Sie einen Benutzer nicht zu einer anderen URL umleiten möchten, können Sie `null`.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (SOAP-Modus): Aufrufen eines Dokuments mithilfe der Java-API&quot;

### Zugriff auf Dokumente mithilfe der Webdienst-API sperren {#revoke-access-to-documents-using-the-web-service-api}

Sperren Sie mithilfe der Document Security-API (Webdienst) den Zugriff auf ein richtliniengeschütztes PDF-Dokument:

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Document Security Client-API-Objekts

   * Erstellen Sie eine `DocumentSecurityServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `DocumentSecurityServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `DocumentSecurityServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.


1. Abrufen eines richtliniengeschützten PDF-Dokuments

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern eines richtliniengeschützten PDF-Dokuments verwendet, das gesperrt ist.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des zu widerrufenden richtliniengeschützten PDF-Dokuments darstellt, sowie den Modus, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Feld mit dem Inhalt des Byte-Arrays.

1. Richtliniengeschütztes Dokument sperren

   * Rufen Sie den Wert der Lizenzkennung des richtliniengeschützten Dokuments ab, indem Sie die `DocumentSecurityServiceClient` -Objekt `getLicenseID` -Methode und Übergabe der `BLOB` -Objekt, das das richtliniengeschützte Dokument darstellt. Diese Methode gibt einen Zeichenfolgenwert zurück, der die Lizenzkennung darstellt.
   * Sperren Sie das richtliniengeschützte Dokument, indem Sie die `DocumentSecurityServiceClient` -Objekt `revokeLicense` -Methode verwenden und die folgenden Werte übergeben:

      * Ein string -Wert, der den Wert der Lizenzkennung des richtliniengeschützten Dokuments angibt (geben Sie den Rückgabewert von `DocumentSecurityServiceService` -Objekt `getLicenseId` -Methode).
      * Ein statisches Datenelement der `Reason` enum , der den Grund für das Sperren des Dokuments angibt. Sie können beispielsweise `Reason.DOCUMENT_REVISED`.
      * A `string` -Wert, der den URL-Speicherort angibt, an dem sich ein überarbeitetes Dokument befindet. Wenn Sie einen Benutzer nicht zu einer anderen URL umleiten möchten, können Sie `null`.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (MTOM): Sperren eines Dokuments mithilfe der Webdienst-API&quot;
* &quot;Schnellstart (SwaRef): Sperren eines Dokuments mithilfe der Webdienst-API&quot;

**Siehe auch**

[Entfernen von Richtlinien aus Word-Dokumenten](protecting-documents-policies.md#removing-policies-from-word-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Neuer Zugriff auf gesperrte Dokumente {#reinstating-access-to-revoked-documents}

Sie können den Zugriff auf ein gesperrtes PDF-Dokument reaktivieren, sodass alle Exemplare des gesperrten Dokuments für Benutzer zugänglich sind. Wenn ein Benutzer ein reaktiviertes Dokument öffnet, das widerrufen wurde, kann er das Dokument anzeigen.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-6}

Führen Sie die folgenden Schritte aus, um den Zugriff auf ein gesperrtes PDF-Dokument wiederherzustellen:

1. Projektdateien einschließen.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Rufen Sie die Lizenzkennung des gesperrten PDF-Dokuments ab.
1. Reaktivieren Sie den Zugriff auf das gesperrte PDF-Dokument.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Client-Objekt des Document Security-Dienstes erstellen. Wenn Sie die Java-API verwenden, erstellen Sie eine `DocumentSecurityClient` -Objekt. Wenn Sie die Document Security-Webdienst-API verwenden, erstellen Sie eine `DocumentSecurityServiceService` -Objekt.

**Lizenzkennung des gesperrten PDF-Dokuments abrufen**

Sie müssen die Lizenzkennung des gesperrten PDF-Dokuments abrufen, um ein gesperrtes PDF-Dokument erneut zu aktivieren. Nachdem Sie den Wert der Lizenzkennung erhalten haben, können Sie ein gesperrtes Dokument erneut aktivieren. Wenn Sie versuchen, ein Dokument erneut zu aktivieren, das nicht gesperrt ist, wird eine Ausnahme verursacht.

**Zugriff auf das gesperrte PDF-Dokument reaktivieren**

Um den Zugriff auf ein gesperrtes PDF-Dokument wieder zu aktivieren, müssen Sie die Lizenzkennung des gesperrten Dokuments angeben. Wenn Sie versuchen, den Zugriff auf ein nicht widerrufenes PDF-Dokument erneut zu aktivieren, wird eine Ausnahme verursacht.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Anwenden von Richtlinien auf PDF-Dokumente](protecting-documents-policies.md#applying-policies-to-pdf-documents)

[Zugriff auf Dokumente sperren](protecting-documents-policies.md#revoking-access-to-documents)

### Zugriff auf gesperrte Dokumente mit der Java-API reaktivieren {#reinstate-access-to-revoked-documents-using-the-java-api}

Reaktivieren Sie den Zugriff auf ein gesperrtes Dokument mithilfe der Document Security-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocumentSecurityClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie die Lizenzkennung des gesperrten PDF-Dokuments ab.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das gesperrte PDF-Dokument darstellt, indem es seinen Konstruktor verwendet und einen Zeichenfolgenwert übergibt, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.
   * Erstellen Sie eine `DocumentManager` -Objekt durch Aufrufen der `DocumentSecurityClient` -Objekt `getDocumentManager` -Methode.
   * Rufen Sie den Wert der Lizenzkennung des gesperrten Dokuments ab, indem Sie die `DocumentManager` -Objekt `getLicenseId` -Methode und Übergabe der `com.adobe.idp.Document` -Objekt, das das gesperrte Dokument darstellt. Diese Methode gibt einen Zeichenfolgenwert zurück, der die Lizenzkennung darstellt.

1. Reaktivieren Sie den Zugriff auf das gesperrte PDF-Dokument.

   * Erstellen Sie eine `LicenseManager` -Objekt durch Aufrufen der `DocumentSecurityClient` -Objekt `getLicenseManager` -Methode.
   * Den Zugriff auf das gesperrte PDF-Dokument durch Aufrufen der `LicenseManager` -Objekt `unrevokeLicense` -Methode verwenden und den Wert der Lizenzkennung des gesperrten Dokuments übergeben.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (SOAP-Modus): Zugriff auf ein gesperrtes Dokument mit der Web-Dienst-API reaktivieren&quot;

### Zugriff auf gesperrte Dokumente mithilfe der Web-Dienst-API reaktivieren {#reinstate-access-to-revoked-documents-using-the-web-service-api}

Reaktivieren Sie den Zugriff auf ein gesperrtes Dokument mithilfe der Document Security API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie eine `DocumentSecurityServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `DocumentSecurityServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `DocumentSecurityServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.


1. Rufen Sie die Lizenzkennung des gesperrten PDF-Dokuments ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird verwendet, um ein gesperrtes PDF-Dokument zu speichern, auf das der Zugriff erneut aktiviert wird.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des gesperrten PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Feld mit dem Inhalt des Byte-Arrays.

1. Reaktivieren Sie den Zugriff auf das gesperrte PDF-Dokument.

   * Rufen Sie den Wert der Lizenzkennung des gesperrten Dokuments ab, indem Sie die `DocumentSecurityServiceClient` -Objekt `getLicenseID` -Methode und Übergabe der `BLOB` -Objekt, das das gesperrte Dokument darstellt. Diese Methode gibt einen Zeichenfolgenwert zurück, der die Lizenzkennung darstellt.
   * Den Zugriff auf das gesperrte PDF-Dokument durch Aufrufen der `DocumentSecurityServiceClient` -Objekt `unrevokeLicense` -Methode verwenden und einen string -Wert übergeben, der den Lizenzkennungswert des gesperrten PDF-Dokuments angibt (geben Sie den Rückgabewert der `DocumentSecurityServiceClient` -Objekt `getLicenseId` -Methode).

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (MTOM): Zugriff auf ein gesperrtes Dokument mit der Web-Dienst-API reaktivieren&quot;
* &quot;Schnellstart (SwaRef): Zugriff auf ein gesperrtes Dokument mit der Web-Dienst-API reaktivieren&quot;

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Überprüfen von richtliniengeschützten PDF-Dokumenten {#inspecting-policy-protected-pdf-documents}

Sie können die Document Security Service-API (Java- und Webdienst) verwenden, um richtliniengeschützte PDF-Dokumente zu überprüfen. Beim Überprüfen richtliniengeschützter PDF-Dokumente werden Informationen zum richtliniengeschützten PDF-Dokument zurückgegeben. Sie können beispielsweise die Richtlinie bestimmen, die zum Schützen des Dokuments verwendet wurde, sowie das Datum, an dem das Dokument gesichert wurde.

Sie können diese Aufgabe nicht ausführen, wenn Ihre LiveCycle-Version 8.x oder eine frühere Version ist. In AEM Forms wird die Überprüfung richtliniengeschützter Dokumente unterstützt. Wenn Sie versuchen, ein richtliniengeschütztes Dokument mit LiveCycle 8.x (oder früher) zu überprüfen, wird eine Ausnahme ausgelöst.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-7}

So prüfen Sie ein richtliniengeschütztes PDF-Dokument:

1. Projektdateien einschließen.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Rufen Sie ein richtliniengeschütztes Dokument zum Überprüfen ab.
1. Erhalten Sie Informationen zum richtliniengeschützten Dokument.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert durchführen können, erstellen Sie ein Client-Objekt des Document Security-Dienstes. Wenn Sie die Java-API verwenden, erstellen Sie eine `RightsManagementClient` -Objekt. Wenn Sie die Document Security-Webdienst-API verwenden, erstellen Sie eine `RightsManagementServiceService` -Objekt.

**Abrufen eines richtliniengeschützten Dokuments zum Überprüfen**

Rufen Sie ein richtliniengeschütztes Dokument ab, um es zu überprüfen. Wenn Sie versuchen, ein Dokument zu überprüfen, das nicht mit einer Richtlinie gesichert ist oder gesperrt ist, wird eine Ausnahme ausgelöst.

**Inspect des Dokuments**

Nachdem Sie ein richtliniengeschütztes Dokument abgerufen haben, können Sie es überprüfen.

**Informationen zum richtliniengeschützten Dokument abrufen**

Nachdem Sie ein richtliniengeschütztes PDF-Dokument geprüft haben, können Sie Informationen dazu abrufen. Sie können beispielsweise die Richtlinie bestimmen, die zum Schützen des Dokuments verwendet wird.

Wenn Sie ein Dokument mit einer Richtlinie sichern, die zu &quot;Meine Richtlinien&quot;gehört, rufen Sie `RMInspectResult.getPolicysetName` oder `RMInspectResult.getPolicysetId`, wird null zurückgegeben.

Wenn das Dokument mit einer Richtlinie gesichert wird, die in einem Richtliniensatz (außer &quot;Meine Richtlinien&quot;) enthalten ist, dann `RMInspectResult.getPolicysetName` und `RMInspectResult.getPolicysetId` gibt gültige Zeichenfolgen zurück.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Inspect Policy Protected PDF Documents mithilfe der Java-API {#inspect-policy-protected-pdf-documents-using-the-java-api}

Inspect ein richtliniengeschütztes PDF-Dokument mithilfe der Document Security Service-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie die Datei &quot;adobe-rightsmanagement-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein. Weitere Informationen über den Speicherort dieser Dateien finden Sie unter [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Erstellen Sie ein `RightsManagementClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie ein richtliniengeschütztes Dokument zum Überprüfen ab.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das richtliniengeschützte PDF-Dokument mithilfe seines Konstruktors darstellt. Übergeben Sie einen string -Wert, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Inspect das Dokument.

   * Erstellen Sie eine `DocumentManager` -Objekt durch Aufrufen der `RightsManagementClient` -Objekt `getDocumentManager` -Methode.
   * Inspect das richtliniengeschützte Dokument durch Aufrufen der `LicenseManager` -Objekt `inspectDocument` -Methode. Übergeben Sie die `com.adobe.idp.Document` -Objekt, das das richtliniengeschützte PDF-Dokument enthält. Diese Methode gibt eine `RMInspectResult` -Objekt, das Informationen zum richtliniengeschützten Dokument enthält.

1. Erhalten Sie Informationen zum richtliniengeschützten Dokument.

   Um Informationen zum richtliniengeschützten Dokument zu erhalten, rufen Sie die entsprechende Methode auf, die gehört `RMInspectResult` -Objekt. Um beispielsweise den Richtliniennamen abzurufen, rufen Sie die `RMInspectResult` -Objekt `getPolicyName` -Methode.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (SOAP-Modus): Untersuchen richtliniengeschützter PDF-Dokumente mit der Java-API&quot;

### Inspect Policy Protected PDF Documents mithilfe der Web Service-API {#inspect-policy-protected-pdf-documents-using-the-web-service-api}

Inspect a policy-protected PDF document by using the Document Security Service API (web service):

1. Include project files.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie eine `RightsManagementServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `RightsManagementServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `RightsManagementServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.


1. Rufen Sie ein richtliniengeschütztes Dokument zum Überprüfen ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern eines zu prüfenden PDF-Dokuments verwendet.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen seines Konstruktors. Übergeben Sie einen string -Wert, der den Dateispeicherort des PDF-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode. Übergeben Sie das Byte-Array, die Startposition und die Stream-Länge zum Lesen.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Feld mit dem Inhalt des Byte-Arrays.

1. Inspect das Dokument.

   Inspect das richtliniengeschützte Dokument durch Aufrufen der `RightsManagementServiceClient` -Objekt `inspectDocument` -Methode. Übergeben Sie die `BLOB` -Objekt, das das richtliniengeschützte PDF-Dokument enthält. Diese Methode gibt eine `RMInspectResult` -Objekt, das Informationen zum richtliniengeschützten Dokument enthält.

1. Erhalten Sie Informationen zum richtliniengeschützten Dokument.

   Um Informationen zum richtliniengeschützten Dokument zu erhalten, rufen Sie den Wert des entsprechenden Felds ab, das zum `RMInspectResult` -Objekt. Um beispielsweise den Richtliniennamen abzurufen, rufen Sie den Wert der `RMInspectResult` -Objekt `policyName` -Feld.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (MTOM): Untersuchen richtliniengeschützter PDF-Dokumente mithilfe der Web Service-API&quot;
* &quot;Schnellstart (SwaRef): Untersuchen richtliniengeschützter PDF-Dokumente mithilfe der Web Service-API&quot;

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Wasserzeichen erstellen {#creating-watermarks}

Wasserzeichen tragen dazu bei, die Sicherheit eines Dokuments zu gewährleisten, indem sie das Dokument eindeutig identifizieren und die Verletzung des Urheberrechts kontrollieren. Sie können beispielsweise ein Wasserzeichen mit dem Status &quot;Vertraulich&quot;auf allen Seiten eines Dokuments erstellen und platzieren. Nachdem ein Wasserzeichen erstellt wurde, können Sie es als Teil einer Richtlinie einbeziehen. Das heißt, Sie können das Wasserzeichenattribut der Richtlinie mit dem neu erstellten Wasserzeichen festlegen. Nachdem eine Richtlinie, die ein Wasserzeichen enthält, auf ein Dokument angewendet wurde, wird das Wasserzeichen im richtliniengeschützten Dokument angezeigt.

>[!NOTE]
>
>Nur Benutzer mit Administratorrechten für Document Security können Wasserzeichen erstellen. Das heißt, Sie müssen einen solchen Benutzer angeben, wenn Sie Verbindungseinstellungen definieren, die zum Erstellen eines Client-Objekts des Document Security-Dienstes erforderlich sind.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-8}

Gehen Sie wie folgt vor, um ein Wasserzeichen zu erstellen:

1. Projektdateien einschließen.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Legen Sie die Wasserzeichenattribute fest.
1. Registrieren Sie das Wasserzeichen beim Document Security-Dienst.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Client-Objekt des Document Security-Dienstes erstellen. Wenn Sie die Java-API verwenden, erstellen Sie eine `RightsManagementClient` -Objekt. Wenn Sie die Document Security-Webdienst-API verwenden, erstellen Sie eine `RightsManagementServiceService` -Objekt.

**Festlegen der Wasserzeichenattribute**

Um ein neues Wasserzeichen zu erstellen, müssen Sie Wasserzeichenattribute festlegen. Das Attribut name muss immer definiert sein. Zusätzlich zum Attribut name müssen Sie mindestens eines der folgenden Attribute festlegen:

* Benutzerdefinierter Text
* DateIncluded
* UserIdIncluded
* UserNameIncluded

In der folgenden Tabelle sind Schlüssel-Wert-Paare aufgeführt, die zum Erstellen eines Wasserzeichens mit Webdiensten erforderlich sind.

<table> 
 <thead> 
  <tr> 
   <th><p>Schlüsselname</p></th> 
   <th><p>Beschreibung</p></th> 
   <th><p>Wert</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p><code>WaterBackCmd:IS_USERNAME_ENABLED</code></p></td> 
   <td><p>Gibt an, ob der Benutzername des Benutzers, der das Dokument öffnet, Teil des Wasserzeichens ist.</p></td> 
   <td><p>„True“ oder „False“</p></td> 
  </tr> 
  <tr> 
   <td><p><code>WaterBackCmd:IS_USERID_ENABLED</code></p></td> 
   <td><p>Gibt an, ob die Kennung des Benutzers, der das Dokument öffnet, Teil des Wasserzeichens ist.</p></td> 
   <td><p>„True“ oder „False“</p></td> 
  </tr> 
  <tr> 
   <td><p><code>WaterBackCmd:IS_CURRENTDATE_ENABLED</code></p></td> 
   <td><p>Gibt an, ob das aktuelle Datum Teil des Wasserzeichens ist.</p></td> 
   <td><p>„True“ oder „False“</p></td> 
  </tr> 
  <tr> 
   <td><p><code>WaterBackCmd:IS_CUSTOMTEXT_ENABLED</code></p></td> 
   <td><p>Wenn dieser Wert wahr ist, muss der Wert des benutzerdefinierten Texts mithilfe von <code>WaterBackCmd:SRCTEXT</code>.</p></td> 
   <td><p>„True“ oder „False“</p></td> 
  </tr> 
  <tr> 
   <td><p><code>WaterBackCmd:OPACITY</code></p></td> 
   <td><p>Gibt die Deckkraft des Wasserzeichens an. Der Standardwert ist 0,5, wenn er nicht angegeben ist.</p></td> 
   <td><p>Ein Wert zwischen 0,0 und 1,0.</p></td> 
  </tr> 
  <tr> 
   <td><p><code>WaterBackCmd:ROTATION</code></p></td> 
   <td><p>Gibt die Drehung des Wasserzeichens an. Der Standardwert ist 0 Grad.</p></td> 
   <td><p>Ein Wert zwischen 0 und 359.</p></td> 
  </tr> 
  <tr> 
   <td><p><code>WaterBackCmd:SCALE</code></p></td> 
   <td><p>Wenn dieser Wert angegeben ist, dann <code>WaterBackCmd:IS_SIZE_ENABLED</code> muss vorhanden sein und der Wert muss "true"lauten. Wenn dieses Attribut nicht angegeben ist, passt das Standardverhalten zur Seite.</p></td> 
   <td><p>Ein Wert größer als 0.0 und kleiner gleich 1.0.</p></td> 
  </tr> 
  <tr> 
   <td><p><code>WaterBackCmd:HORIZ_ALIGN</code></p></td> 
   <td><p>Gibt die horizontale Ausrichtung des Wasserzeichens an. Der Standardwert ist "center".</p></td> 
   <td><p>links, zentriert oder rechts</p></td> 
  </tr> 
  <tr> 
   <td><p><code>WaterBackCmd:VERT_ALIGN</code></p></td> 
   <td><p>Gibt die vertikale Ausrichtung des Wasserzeichens an. Der Standardwert ist "center".</p></td> 
   <td><p>oben, zentriert oder unten</p></td> 
  </tr> 
  <tr> 
   <td><p><code>WaterBackCmd:IS_USE_BACKGROUND</code></p></td> 
   <td><p>Gibt an, ob das Wasserzeichen ein Hintergrund ist. Der Standardwert lautet false.</p></td> 
   <td><p>„True“ oder „False“</p></td> 
  </tr> 
  <tr> 
   <td><p><code>WaterBackCmd:IS_SIZE_ENABLED</code></p></td> 
   <td><p>True , wenn eine benutzerdefinierte Skala angegeben ist. Wenn dieser Wert "true"ist, muss auch "SCALE"angegeben werden. Wenn dieser Wert false ist, passt der Standardwert zur Seite.</p></td> 
   <td><p>„True“ oder „False“</p></td> 
  </tr> 
  <tr> 
   <td><p><code>WaterBackCmd:SRCTEXT</code></p></td> 
   <td><p>Gibt den benutzerdefinierten Text für ein Wasserzeichen an. Wenn dieser Wert vorhanden ist, dann <code>WaterBackCmd:IS_CUSTOMTEXT_ENABLED</code> muss ebenfalls vorhanden sein und auf "true"gesetzt sein.</p></td> 
   <td><p>„True“ oder „False“</p></td> 
  </tr> 
 </tbody> 
</table>

Für alle Wasserzeichen muss eines der folgenden Attribute definiert sein:

* `WaterBackCmd:IS_USERNAME_ENABLED`
* `WaterBackCmd:IS_USERID_ENABLED`
* `WaterBackCmd:IS_CURRENTDATE_ENABLED`
* `WaterBackCmd:IS_CUSTOMTEXT_ENABLED`

Alle anderen Attribute sind optional.

**Wasserzeichen registrieren**

Ein neues Wasserzeichen muss beim Document Security-Dienst registriert sein, bevor es verwendet werden kann. Nachdem Sie ein Wasserzeichen registriert haben, können Sie es in Richtlinien verwenden.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Anwenden von Richtlinien auf PDF-Dokumente](protecting-documents-policies.md#applying-policies-to-pdf-documents)

### Erstellen von Wasserzeichen mit der Java-API {#create-watermarks-using-the-java-api}

Erstellen Sie mit der Document Security-API (Java) ein Wasserzeichen:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien ein, z. B. die `adobe-rightsmanagement-client.jar`im Klassenpfad Ihres Java-Projekts.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `RightsManagementClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Festlegen der Wasserzeichenattribute

   * Erstellen Sie eine `Watermark` -Objekt durch Aufrufen der `InfomodelObjectFactory` Statische Objektform `createWatermark` -Methode. Diese Methode gibt eine `Watermark` -Objekt.
   * Festlegen des Namensattributs des Wasserzeichens durch Aufrufen der `Watermark` -Objekt `setName` -Methode verwenden und einen string -Wert übergeben, der den Richtliniennamen angibt.
   * Legen Sie das Hintergrundattribut des Wasserzeichens fest, indem Sie die `Watermark` -Objekt `setBackground` Methode und Übergabe `true`. Durch Festlegen dieses Attributs wird das Wasserzeichen im Hintergrund des Dokuments angezeigt.
   * Festlegen des benutzerdefinierten Textattributs des Wasserzeichens durch Aufrufen der `Watermark` -Objekt `setCustomText` -Methode verwenden und einen string -Wert übergeben, der den Text des Wasserzeichens darstellt.
   * Festlegen des Deckkraftattributs des Wasserzeichens durch Aufrufen der `Watermark` -Objekt `setOpacity` -Methode verwenden und einen ganzzahligen Wert übergeben, der die Deckkraft angibt. Der Wert 100 zeigt an, dass das Wasserzeichen vollständig undurchsichtig ist, und der Wert 0 zeigt an, dass das Wasserzeichen vollständig transparent ist.

1. Registrieren Sie das Wasserzeichen.

   * Erstellen Sie eine `WatermarkManager` -Objekt durch Aufrufen der `RightsManagementClient` -Objekt `getWatermarkManager` -Methode. Diese Methode gibt eine `WatermarkManager` -Objekt.
   * Register the watermark by invoking the `WatermarkManager` object’s `registerWatermark` method and passing the `Watermark` object that represents the watermark to register. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Identifizierungswert des Wasserzeichens darstellt.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (SOAP-Modus): Erstellen eines Wasserzeichens mit der Java-API&quot;

### Erstellen von Wasserzeichen mit der Webdienst-API {#create-watermarks-using-the-web-service-api}

Erstellen Sie ein Wasserzeichen mithilfe der Document Security-API (Webdienst):

1. Erstellen Sie ein Document Security Client-API-Objekt.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie eine `RightsManagementServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `RightsManagementServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `RightsManagementServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.


1. Legen Sie die Wasserzeichenattribute fest.

   * Erstellen Sie eine `WatermarkSpec` -Objekt durch Aufrufen der `WatermarkSpec` -Konstruktor.
   * Legen Sie den Namen des Wasserzeichens fest, indem Sie dem `WatermarkSpec` -Objekt `name` Datenelement.
   * Festlegen der `id` -Attribut durch Zuweisen eines Zeichenfolgenwerts zum `WatermarkSpec` -Objekt `id` Datenelement.
   * Erstellen Sie für jede festzulegende Wasserzeicheneigenschaft eine separate `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt.
   * Legen Sie den Schlüsselwert fest, indem Sie dem `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `key` Datenelement (z. B. `WaterBackCmd:OPACITY)`.
   * Legen Sie den Wert fest, indem Sie dem `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `value` Datenelement (z. B. `.25`).
   * Erstellen Sie eine `MyArrayOf_xsd_anyType` -Objekt. Für jeden `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt, rufen Sie die `MyArrayOf_xsd_anyType` -Objekt `Add` -Methode. Übergeben Sie die `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt.
   * Zuweisen der `MyArrayOf_xsd_anyType` -Objekt `WatermarkSpec` -Objekt `values` Datenelement.

1. Registrieren Sie das Wasserzeichen.

   Registrieren Sie das Wasserzeichen, indem Sie die `RightsManagementServiceClient` -Objekt `registerWatermark` -Methode und Übergabe der `WatermarkSpec` -Objekt, das das zu registrierende Wasserzeichen darstellt.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (MTOM): Erstellen eines Wasserzeichens mithilfe der Webdienst-API&quot;
* &quot;Schnellstart (SwaRef): Erstellen eines Wasserzeichens mithilfe der Webdienst-API&quot;

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Ändern von Wasserzeichen {#modifying-watermarks}

Sie können ein vorhandenes Wasserzeichen mithilfe der Document Security Java-API oder der Web Service-API ändern. Um Änderungen an einem vorhandenen Wasserzeichen vorzunehmen, rufen Sie es ab, ändern dessen Attribute und aktualisieren Sie es dann auf dem Server. Angenommen, Sie rufen ein Wasserzeichen ab und ändern dessen Deckkraftattribut. Bevor die Änderung wirksam wird, müssen Sie das Wasserzeichen aktualisieren.

Wenn Sie ein Wasserzeichen ändern, wirkt sich die Änderung auf zukünftige Dokumente aus, auf die das Wasserzeichen angewendet wird. Vorhandene PDF-Dokumente, die das Wasserzeichen enthalten, sind also nicht betroffen.

>[!NOTE]
>
>Nur Benutzer mit Administratorrechten für Document Security können Wasserzeichen ändern. Das heißt, Sie müssen einen solchen Benutzer angeben, wenn Sie Verbindungseinstellungen definieren, die zum Erstellen eines Client-Objekts des Document Security-Dienstes erforderlich sind.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-9}

Gehen Sie wie folgt vor, um ein Wasserzeichen zu ändern:

1. Projektdateien einschließen.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Rufen Sie das zu ändernde Wasserzeichen ab.
1. Legen Sie die Wasserzeichenattribute fest.
1. Aktualisieren Sie das Wasserzeichen.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Client-Objekt des Document Security-Dienstes erstellen. Wenn Sie die Java-API verwenden, erstellen Sie eine `DocumentSecurityClient` -Objekt. Wenn Sie die Document Security-Webdienst-API verwenden, erstellen Sie eine `DocumentSecurityServiceService` -Objekt.

**Abrufen des zu ändernden Wasserzeichens**

Um ein Wasserzeichen zu ändern, müssen Sie ein vorhandenes Wasserzeichen abrufen. Sie können ein Wasserzeichen abrufen, indem Sie dessen Namen angeben oder dessen Bezeichnerwert angeben.

**Festlegen der Wasserzeichenattribute**

Um ein vorhandenes Wasserzeichen zu ändern, ändern Sie den Wert eines oder mehrerer Wasserzeichenattribute. Beim programmatischen Aktualisieren eines Wasserzeichens mithilfe eines Webdiensts müssen Sie alle ursprünglich festgelegten Attribute festlegen, auch wenn sich der Wert nicht ändert. Angenommen, die folgenden Wasserzeichenattribute sind festgelegt: `WaterBackCmd:IS_USERID_ENABLED`, `WaterBackCmd:IS_CUSTOMTEXT_ENABLED`, `WaterBackCmd:OPACITY`und `WaterBackCmd:SRCTEXT`. Das einzige Attribut, das Sie ändern möchten, ist `WaterBackCmd:OPACITY`, müssen Sie die anderen Werte gut festlegen.

>[!NOTE]
>
>Wenn Sie die Java-API zum Ändern eines Wasserzeichens verwenden, müssen Sie nicht alle Attribute angeben. Legen Sie das Wasserzeichenattribut fest, das Sie ändern möchten.

>[!NOTE]
>
>Weitere Informationen zu den Namen von Wasserzeichen-Attributen finden Sie unter [Wasserzeichen erstellen](protecting-documents-policies.md#creating-watermarks).

**Aktualisieren des Wasserzeichens**

Nachdem Sie die Attribute eines Wasserzeichens geändert haben, müssen Sie das Wasserzeichen aktualisieren.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Wasserzeichen erstellen](protecting-documents-policies.md#creating-watermarks)

### Ändern von Wasserzeichen mit der Java-API {#modify-watermarks-using-the-java-api}

Ändern Sie ein Wasserzeichen mithilfe der Document Security-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie die Datei &quot;adobe-rightsmanagement-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocumentSecurityClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie das zu ändernde Wasserzeichen ab.

   Erstellen Sie eine `WatermarkManager` -Objekt durch Aufrufen der `DocumentSecurityClient` -Objekt `getWatermarkManager` -Methode verwenden und einen string -Wert übergeben, der den Namen des Wasserzeichens angibt. Diese Methode gibt eine `Watermark` -Objekt, das das zu ändernde Wasserzeichen darstellt.

1. Legen Sie die Wasserzeichenattribute fest.

   Festlegen des Deckkraftattributs des Wasserzeichens durch Aufrufen der `Watermark` -Objekt `setOpacity` -Methode verwenden und einen ganzzahligen Wert übergeben, der die Deckkraft angibt. Der Wert 100 zeigt an, dass das Wasserzeichen vollständig undurchsichtig ist, und der Wert 0 zeigt an, dass das Wasserzeichen vollständig transparent ist.

   >[!NOTE]
   >
   >In diesem Beispiel wird nur das Trübungsattribut geändert.

1. Aktualisieren Sie das Wasserzeichen.

   * Aktualisieren Sie das Wasserzeichen, indem Sie die `WatermarkManager` -Objekt `updateWatermark` -Methode und übergeben Sie die `Watermark` -Objekt, dessen -Attribut geändert wurde.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie im Schnellstart-Modus (SOAP-Modus): Ändern eines Wasserzeichens mithilfe des Java-API-Abschnitts.

### Ändern von Wasserzeichen mithilfe der Webdienst-API {#modify-watermarks-using-the-web-service-api}

Ändern Sie ein Wasserzeichen mithilfe der Document Security-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie eine `DocumentSecurityServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `RightsManagementServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/DocumentSecurityService?WSDL`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `DocumentSecurityServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.


1. Rufen Sie das zu ändernde Wasserzeichen ab.

   Rufen Sie das zu ändernde Wasserzeichen ab, indem Sie die `DocumentSecurityServiceClient` -Objekt `getWatermarkByName` -Methode. Übergeben Sie einen string -Wert, der den Namen des Wasserzeichens angibt. Diese Methode gibt eine `WatermarkSpec` -Objekt, das das zu ändernde Wasserzeichen darstellt.

1. Legen Sie die Wasserzeichenattribute fest.

   * Erstellen Sie für jede zu aktualisierende Wasserzeicheneigenschaft eine separate `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt.
   * Legen Sie den Schlüsselwert fest, indem Sie dem `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `key` Datenelement (z. B. `WaterBackCmd:OPACITY)`.
   * Legen Sie den Wert fest, indem Sie dem `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `value` Datenelement (z. B. `.50`).
   * Erstellen Sie eine `MyArrayOf_xsd_anyType` -Objekt. Für jeden `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt, rufen Sie die `MyArrayOf_xsd_anyType` -Objekt `Add` -Methode. Übergeben Sie die `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt.
   * Zuweisen der `MyArrayOf_xsd_anyType` -Objekt `WatermarkSpec` -Objekt `values` Datenelement.

1. Aktualisieren Sie das Wasserzeichen.

   Aktualisieren Sie das Wasserzeichen, indem Sie die `DocumentSecurityServiceClient` -Objekt `updateWatermark` -Methode und Übergabe der `WatermarkSpec` -Objekt, das das zu ändernde Wasserzeichen darstellt.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in der folgenden Kurzanleitung:

* &quot;Schnellstart (MTOM): Ändern eines Wasserzeichens mithilfe der Webdienst-API&quot;

## Suchen nach Ereignissen {#searching-for-events}

Der Rights Management-Dienst verfolgt bestimmte Aktionen genau nach ihrem Ablauf, z. B. das Anwenden einer Richtlinie auf ein Dokument, das Öffnen eines richtliniengeschützten Dokuments und das Sperren des Dokumentzugriffs. Die Ereignisprüfung muss für den Rights Management-Dienst aktiviert sein, sonst werden Ereignisse nicht verfolgt.

Ereignisse fallen in eine der folgenden Kategorien:

* Administrator-Ereignisse sind Aktionen, die sich auf einen Administrator beziehen, z. B. die Erstellung eines neuen Administratorkontos.
* Dokumentereignisse sind Aktionen im Zusammenhang mit einem Dokument, z. B. das Schließen eines richtliniengeschützten Dokuments.
* Richtlinienereignisse sind Aktionen im Zusammenhang mit einer Richtlinie, z. B. die Erstellung einer neuen Richtlinie.
* Dienstereignisse sind Aktionen im Zusammenhang mit dem Rights Management-Dienst, z. B. die Synchronisierung mit dem Benutzerordner.

Sie können mit der Rights Management Java-API oder der Web Service-API nach bestimmten Ereignissen suchen. Durch die Suche nach Ereignissen können Sie Aufgaben ausführen, z. B. eine Protokolldatei bestimmter Ereignisse erstellen.

>[!NOTE]
>
>Weitere Informationen zum Rights Management-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-10}

Um nach einem Rights Management-Ereignis zu suchen, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Rights Management Client-API-Objekt.
1. Geben Sie das Ereignis an, nach dem gesucht werden soll.
1. Suchen Sie nach dem Ereignis.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Rights Management Client-API-Objekts**

Bevor Sie einen Rights Management-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Rights Management-Dienst-Client-Objekt erstellen. Wenn Sie die Java-API verwenden, erstellen Sie eine `DocumentSecurityClient` -Objekt. Wenn Sie die Rights Management-Webdienst-API verwenden, erstellen Sie eine `DocumentSecurityServiceService` -Objekt.

**Geben Sie die Ereignisse an, nach denen gesucht werden soll**

Sie müssen das zu suchende Ereignis angeben. Sie können beispielsweise nach dem Richtlinienerstellungsereignis suchen, das beim Erstellen einer neuen Richtlinie auftritt.

**Suchen Sie nach dem Ereignis**

Nachdem Sie das zu suchende Ereignis angegeben haben, können Sie entweder die Rights Management Java-API oder die Rights Management-Webdienst-API verwenden, um nach dem Ereignis zu suchen.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Suchen nach Ereignissen mithilfe der Java-API {#search-for-events-using-the-java-api}

Suchen Sie mithilfe der Rights Management-API (Java) nach Ereignissen:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Rights Management Client-API-Objekts

   Erstellen Sie eine `DocumentSecurityClient` -Objekt mithilfe des -Konstruktors und Übergeben eines `ServiceClientFactory` -Objekt, das Verbindungseigenschaften enthält.

1. Geben Sie die Ereignisse an, nach denen gesucht werden soll

   * Erstellen Sie eine `EventManager` -Objekt durch Aufrufen der `DocumentSecurityClient` -Objekt `getEventManager` -Methode. Diese Methode gibt eine `EventManager` -Objekt.
   * Erstellen Sie eine `EventSearchFilter` -Objekt durch Aufrufen seines Konstruktors.
   * Geben Sie das zu suchende Ereignis an, indem Sie die `EventSearchFilter` -Objekt `setEventCode` -Methode und Übergeben eines statischen Datenelements, das zu der `EventManager` -Klasse, die das Ereignis darstellt, für das gesucht werden soll. Um beispielsweise nach dem Richtlinienerstellungsereignis zu suchen, übergeben Sie `EventManager.POLICY_CREATE_EVENT`.

   >[!NOTE]
   >
   >Sie können zusätzliche Suchkriterien definieren, indem Sie `EventSearchFilter` -Objektmethoden. Rufen Sie beispielsweise die `setUserName` -Methode, um einen mit dem Ereignis verknüpften Benutzer anzugeben.

1. Suchen Sie nach dem Ereignis

   Suchen Sie nach dem Ereignis, indem Sie die `EventManager` -Objekt `searchForEvents` -Methode und Übergabe der `EventSearchFilter` -Objekt, das die Ereignissuchkriterien definiert. Diese Methode gibt ein Array von `Event` Objekte.

**Codebeispiele**

Codebeispiele, die den Rights Management-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (SOAP): Suchen nach Ereignissen mit der Java-API&quot;

### Suchen nach Ereignissen mithilfe der Webdienst-API {#search-for-events-using-the-web-service-api}

Suchen Sie mithilfe der Rights Management-API (Webdienst) nach Ereignissen:

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Rights Management Client-API-Objekts

   * Erstellen Sie eine `DocumentSecurityServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `DocumentSecurityServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `DocumentSecurityServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.


1. Geben Sie die Ereignisse an, nach denen gesucht werden soll

   * Erstellen Sie eine `EventSpec` -Objekt durch Verwendung seines -Konstruktors.
   * Geben Sie den Beginn des Zeitraums an, in dem das Ereignis aufgetreten ist, indem Sie die `EventSpec` -Objekt `firstTime.date` Datenelement mit `DataTime` -Instanz, die den Beginn des Datumsbereichs zum Zeitpunkt des Ereignisses darstellt.
   * Wert zuweisen `true` der `EventSpec` -Objekt `firstTime.dateSpecified` Datenelement.
   * Geben Sie das Ende des Zeitraums an, in dem das Ereignis aufgetreten ist, indem Sie die `EventSpec` -Objekt `lastTime.date` Datenelement mit `DataTime` -Instanz, die das Ende des Datumsbereichs zum Zeitpunkt des Ereignisses darstellt.
   * Wert zuweisen `true` der `EventSpec` -Objekt `lastTime.dateSpecified` Datenelement.
   * Legen Sie das zu suchende Ereignis fest, indem Sie dem `EventSpec` -Objekt `eventCode` Datenelement. In der folgenden Tabelle sind die numerischen Werte aufgeführt, die Sie dieser Eigenschaft zuweisen können:

   <table> 
    <thead> 
    <tr> 
    <th><p>Ereignistyp</p></th> 
    <th><p>Wert</p></th> 
    </tr> 
    </thead> 
    <tbody>
    <tr> 
    <td><p><code>ALL_EVENTS</code></p></td> 
    <td><p>999</p></td> 
    </tr> 
    <tr> 
    <td><p><code>USER_CHANGE_PASSWORD_EVENT</code></p></td> 
    <td><p>1000</p></td> 
    </tr> 
    <tr> 
    <td><p><code>USER_REGISTER_EVENT</code></p></td> 
    <td><p>1001</p></td> 
    </tr> 
    <tr> 
    <td><p><code>USER_PREREGISTER_EVENT</code></p></td> 
    <td><p>1002</p></td> 
    </tr> 
    <tr> 
    <td><p><code>USER_ACTIVATE_EVENT</code></p></td> 
    <td><p>1003</p></td> 
    </tr> 
    <tr> 
    <td><p><code>USER_DEACTIVATE_EVENT</code></p></td> 
    <td><p>1004</p></td> 
    </tr> 
    <tr> 
    <td><p><code>USER_AUTHENTICATE_EVENT</code></p></td> 
    <td><p>1005</p></td> 
    </tr> 
    <tr> 
    <td><p><code>USER_AUTHENTICATE_DENY_EVENT </code></p></td> 
    <td><p>1006</p></td> 
    </tr> 
    <tr> 
    <td><p><code>USER_ACCOUNT_LOCK_EVENT</code></p></td> 
    <td><p>1007</p></td> 
    </tr> 
    <tr> 
    <td><p><code>USER_DELETE_EVENT </code></p></td> 
    <td><p>1008</p></td> 
    </tr> 
    <tr> 
    <td><p><code>USER_UPDATE_PROFILE_EVENT </code></p></td> 
    <td><p>1009</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_VIEW_EVENT </code></p></td> 
    <td><p>2.000</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_PRINT_LOW_EVENT </code></p></td> 
    <td><p>2001</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_PRINT_HIGH_EVENT </code></p></td> 
    <td><p>2002</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_SIGN_EVENT </code></p></td> 
    <td><p>2003</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_ADD_ANNOTATION_EVENT </code></p></td> 
    <td><p>2004</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_FORM_FILL_EVENT </code></p></td> 
    <td><p>2005</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_CLOSE_EVENT </code></p></td> 
    <td><p>2006</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_MODIFY_EVENT </code></p></td> 
    <td><p>2007</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_CHANGE_SECURITY_HANDLER_EVENT </code></p></td> 
    <td><p>2008</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_SWITCH_POLICY_EVENT </code></p></td> 
    <td><p>2009</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_REVOKE_EVENT </code></p></td> 
    <td><p>2010</p></td> 
    </tr> 
    <tr> 
    <td><p><code>$1</code></p></td> 
    <td><p>2011</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_SECURE_EVENT </code></p></td> 
    <td><p>2012</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_UNKNOWN_CLIENT_EVENT </code></p></td> 
    <td><p>2013</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DOCUMENT_CHANGE_REVOKE_URL_EVENT </code></p></td> 
    <td><p>2014</p></td> 
    </tr> 
    <tr> 
    <td><p><code>POLICY_CHANGE_EVENT </code></p></td> 
    <td><p>3000</p></td> 
    </tr> 
    <tr> 
    <td><p><code>POLICY_ENABLE_EVENT </code></p></td> 
    <td><p>3001</p></td> 
    </tr> 
    <tr> 
    <td><p><code>POLICY_DISABLE_EVENT </code></p></td> 
    <td><p>3002</p></td> 
    </tr> 
    <tr> 
    <td><p><code>POLICY_CREATE_EVENT </code></p></td> 
    <td><p>3003</p></td> 
    </tr> 
    <tr> 
    <td><p><code>POLICY_DELETE_EVENT </code></p></td> 
    <td><p>3004</p></td> 
    </tr> 
    <tr> 
    <td><p><code>POLICY_CHANGE_OWNER_EVENT </code></p></td> 
    <td><p>3005</p></td> 
    </tr> 
    <tr> 
    <td><p><code>SERVER_CLIENT_SYNC_EVENT </code></p></td> 
    <td><p>4000</p></td> 
    </tr> 
    <tr> 
    <td><p><code>SERVER_SYNC_DIR_INFO_EVENT </code></p></td> 
    <td><p>4001</p></td> 
    </tr> 
    <tr> 
    <td><p><code>SERVER_SYNC_DIR_COMPLETE_EVENT </code></p></td> 
    <td><p>4002</p></td> 
    </tr> 
    <tr> 
    <td><p><code>SERVER_VERSION_MISMATCH_EVENT </code></p></td> 
    <td><p>4003</p></td> 
    </tr> 
    <tr> 
    <td><p><code>SERVER_CONFIG_CHANGE_EVENT </code></p></td> 
    <td><p>4004</p></td> 
    </tr> 
    <tr> 
    <td><p><code>SERVER_ENABLE_OFFLINE_ACCESS_EVENT </code></p></td> 
    <td><p>4005</p></td> 
    </tr> 
    <tr> 
    <td><p><code>ADMIN_ADD_EVENT </code></p></td> 
    <td><p>5.000</p></td> 
    </tr> 
    <tr> 
    <td><p><code>ADMIN_DELETE_EVENT </code></p></td> 
    <td><p>5001</p></td> 
    </tr> 
    <tr> 
    <td><p><code>ADMIN_EDIT_EVENT </code></p></td> 
    <td><p>5002</p></td> 
    </tr> 
    <tr> 
    <td><p><code>ADMIN_ACTIVATE_EVENT </code></p></td> 
    <td><p>5003</p></td> 
    </tr> 
    <tr> 
    <td><p><code>ADMIN_DEACTIVATE_EVENT </code></p></td> 
    <td><p>5004</p></td> 
    </tr> 
    <tr> 
    <td><p><code>ERROR_DIRECTORY_SERVICE_EVENT </code></p></td> 
    <td><p>6.000</p></td> 
    </tr> 
    <tr> 
    <td><p><code>CREATED_POLICYSET_EVENT</code></p></td> 
    <td><p>7000</p></td> 
    </tr> 
    <tr> 
    <td><p><code>DELETED_POLICYSET_EVENT</code></p></td> 
    <td><p>7001</p></td> 
    </tr> 
    <tr> 
    <td><p><code>MODIFIED_POLICYSET_EVENT</code></p></td> 
    <td><p>7002</p></td> 
    </tr> 
    </tbody> 
    </table>

1. Suchen Sie nach dem Ereignis

   Suchen Sie nach dem Ereignis, indem Sie die `DocumentSecurityServiceClient` -Objekt `searchForEvents` -Methode und Übergabe der `EventSpec` -Objekt, das das Ereignis, für das gesucht werden soll, und die maximale Anzahl von Ergebnissen darstellt. Diese Methode gibt eine `MyArrayOf_xsd_anyType` Sammlung, wobei jedes Element `AuditSpec` -Instanz. Verwenden eines `AuditSpec` -Instanz können Sie Informationen zum Ereignis abrufen, z. B. den Zeitpunkt, zu dem es aufgetreten ist. Die `AuditSpec` -Instanz enthält eine `timestamp` -Datenelement, das diese Informationen angibt.

**Codebeispiele**

Codebeispiele, die den Rights Management-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (MTOM): Suchen nach Ereignissen mithilfe der Webdienst-API&quot;
* &quot;Schnellstart (SwaRef): Suchen nach Ereignissen mithilfe der Webdienst-API&quot;

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Anwenden von Richtlinien auf Word-Dokumente {#applying-policies-to-word-documents}

Neben PDF-Dokumenten unterstützt der Rights Management-Dienst auch weitere Dokumentenformate wie Microsoft Word-Dokumente (DOC-Dateien) und andere Microsoft Office-Dateiformate. Sie können beispielsweise eine Richtlinie auf ein Word-Dokument anwenden, um es zu schützen. Durch Anwendung einer Richtlinie auf ein Word-Dokument können Sie den Zugriff auf das Dokument einschränken. Sie können eine Richtlinie nicht auf ein Dokument anwenden, wenn das Dokument bereits mit einer Richtlinie gesichert ist.

Sie können die Verwendung eines richtliniengeschützten Word-Dokuments nach dessen Verteilung überwachen. Das heißt, Sie können sehen, wie das Dokument verwendet wird und wer es verwendet. Sie können zum Beispiel herausfinden, wann jemand das Dokument geöffnet hat.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-11}

So wenden Sie eine Richtlinie auf ein Word-Dokument an:

1. Projektdateien einschließen.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Rufen Sie ein Word-Dokument ab, auf das eine Richtlinie angewendet wird.
1. Wenden Sie eine vorhandene Richtlinie auf das Word-Dokument an.
1. Speichern Sie das richtliniengeschützte Word-Dokument.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Client-Objekt des Document Security-Dienstes erstellen.

**Abrufen eines Word-Dokuments**

Sie müssen ein Word-Dokument abrufen, um eine Richtlinie anwenden zu können. Nachdem Sie eine Richtlinie auf das Word-Dokument angewendet haben, sind Benutzer bei der Verwendung des Dokuments eingeschränkt. Wenn die Richtlinie beispielsweise nicht das Öffnen des Dokuments im Offline-Modus aktiviert, müssen die Benutzer online sein, um das Dokument zu öffnen.

**Vorhandene Richtlinie auf das Word-Dokument anwenden**

Um eine Richtlinie auf ein Word-Dokument anzuwenden, müssen Sie auf eine vorhandene Richtlinie verweisen und angeben, zu welchem Richtliniensatz die Richtlinie gehört. Der Benutzer, der die Verbindungseigenschaften festlegt, muss Zugriff auf die angegebene Richtlinie haben. Wenn nicht, tritt eine Ausnahme auf.

**Word-Dokument speichern**

Nachdem der Document Security-Dienst eine Richtlinie auf ein Word-Dokument angewendet hat, können Sie das richtliniengeschützte Word-Dokument als DOC-Datei speichern.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Zugriff auf Dokumente sperren](protecting-documents-policies.md#revoking-access-to-documents)

### Anwenden einer Richtlinie auf ein Word-Dokument mithilfe der Java-API {#apply-a-policy-to-a-word-document-using-the-java-api}

Wenden Sie mithilfe der Document Security-API (Java) eine Richtlinie auf ein Word-Dokument an:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocumentSecurityClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie ein Word-Dokument ab.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das Word-Dokument mithilfe des Konstruktors darstellt und einen string -Wert übergibt, der den Speicherort des Word-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Wenden Sie eine vorhandene Richtlinie auf das Word-Dokument an.

   * Erstellen Sie eine `DocumentManager` -Objekt durch Aufrufen der `DocumentSecurityClient` -Objekt `getDocumentManager` -Methode.
   * Wenden Sie eine Richtlinie auf das Word-Dokument an, indem Sie die `DocumentManager` -Objekt `protectDocument` -Methode verwenden und die folgenden Werte übergeben:

      * Die `com.adobe.idp.Document` -Objekt, das das Word-Dokument enthält, auf das die Richtlinie angewendet wird.
      * Ein string -Wert, der den Namen des Dokuments angibt.
      * Ein string -Wert, der den Namen des Richtliniensatzes angibt, zu dem die Richtlinie gehört. You can specify a `null` value that results in the `MyPolicies` policy set being used.
      * Ein string -Wert, der den Richtliniennamen angibt.
      * Ein string -Wert für den Namen der User Manager-Domäne des Benutzers, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann null sein. (Wenn dieser Parameter null ist, muss der nächste Parameterwert null sein.)
      * Ein string -Wert, der den Namen des kanonischen Benutzers des User Manager-Benutzers darstellt, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann `null` (wenn dieser Parameter `null`, muss der vorherige Parameterwert `null`).
      * A `com.adobe.livecycle.rightsmanagement.Locale` , das das Gebietsschema darstellt, das für die Auswahl der MS Office-Vorlage verwendet wird. Dieser Parameterwert ist optional und Sie können `null`.

      Die `protectDocument` -Methode gibt eine `RMSecureDocumentResult` -Objekt, das das richtliniengeschützte Word-Dokument enthält.


1. Speichern Sie das Word-Dokument.

   * Rufen Sie die `RMSecureDocumentResult` -Objekt `getProtectedDoc` -Methode, um das richtliniengeschützte Word-Dokument abzurufen. Diese Methode gibt eine `com.adobe.idp.Document` -Objekt.
   * Erstellen Sie eine `java.io.File` -Objekt ein und stellen Sie sicher, dass die Dateierweiterung DOC lautet.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `Document` -Objekt auf die Datei verweist (stellen Sie sicher, dass Sie die `Document` -Objekt, das von der `getProtectedDoc` -Methode).

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in der folgenden Kurzanleitung:

* &quot;Schnellstart (SOAP-Modus): Anwenden einer Richtlinie auf ein Word-Dokument mithilfe der Java-API&quot;

### Anwenden einer Richtlinie auf ein Word-Dokument mithilfe der Webdienst-API {#apply-a-policy-to-a-word-document-using-the-web-service-api}

Wenden Sie mithilfe der Document Security-API (Webdienst) eine Richtlinie auf ein Word-Dokument an:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/DocumentSecurityService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie eine `DocumentSecurityServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `DocumentSecurityServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/DocumentSecurityService?WSDL`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `DocumentSecurityServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.


1. Rufen Sie ein Word-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern eines Word-Dokuments verwendet, auf das eine Richtlinie angewendet wird.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des Word-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Bestimmen Sie die Byte-Array-Größe, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Feld mit dem Inhalt des Byte-Arrays.

1. Wenden Sie eine vorhandene Richtlinie auf das Word-Dokument an.

   Wenden Sie eine Richtlinie auf das Word-Dokument an, indem Sie die `DocumentSecurityServiceClient` -Objekt `protectDocument` -Methode verwenden und die folgenden Werte übergeben:

   * Die `BLOB` -Objekt, das das Word-Dokument enthält, auf das die Richtlinie angewendet wird.
   * Ein string -Wert, der den Namen des Dokuments angibt.
   * Ein string -Wert, der den Namen des Richtliniensatzes angibt, zu dem die Richtlinie gehört. Sie können eine `null` -Wert, der zu `MyPolicies` verwendeter Richtliniensatz.
   * Ein string -Wert, der den Richtliniennamen angibt.
   * Ein string -Wert für den Namen der User Manager-Domäne des Benutzers, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann null sein. (Wenn dieser Parameter null ist, muss der nächste Parameterwert `null`).
   * Ein string -Wert, der den Namen des kanonischen Benutzers des User Manager-Benutzers darstellt, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann null sein. (Wenn dieser Parameter null ist, muss der vorherige Parameterwert `null`).
   * A `RMLocale` -Wert, der den Gebietsschemawert angibt (z. B. `RMLocale.en`).
   * Ein string -Ausgabeparameter, der zum Speichern des Richtlinienkennungswerts verwendet wird.
   * Ein string -Ausgabeparameter, der zum Speichern des richtliniengeschützten Bezeichnerwerts verwendet wird.
   * Ein string -Ausgabeparameter, der zum Speichern des MIME-Typs verwendet wird (z. B. `application/doc`).

   Die `protectDocument` -Methode gibt eine `BLOB` -Objekt, das das richtliniengeschützte Word-Dokument enthält.

1. Speichern Sie das Word-Dokument.

   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des richtliniengeschützten Word-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt der `BLOB` -Objekt, das von der `protectDocument` -Methode. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` Datenelement.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine Word-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in der folgenden Kurzanleitung:

* &quot;Schnellstart (MTOM): Anwenden einer Richtlinie auf ein Word-Dokument mithilfe der Webdienst-API&quot;

## Entfernen von Richtlinien aus Word-Dokumenten {#removing-policies-from-word-documents}

Sie können eine Richtlinie aus einem richtliniengeschützten Word-Dokument entfernen, um die Sicherheit aus dem Dokument zu entfernen. Das heißt, wenn das Dokument nicht mehr durch eine Richtlinie geschützt werden soll. Wenn Sie ein richtliniengeschütztes Word-Dokument mit einer neueren Richtlinie aktualisieren möchten, ist es effizienter, die Richtlinie zu wechseln, anstatt die Richtlinie zu entfernen und die aktualisierte Richtlinie hinzuzufügen.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-12}

So entfernen Sie eine Richtlinie aus einem richtliniengeschützten Word-Dokument:

1. Projektdateien einschließen
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Rufen Sie ein richtliniengeschütztes Word-Dokument ab.
1. Entfernen Sie die Richtlinie aus dem Word-Dokument.
1. Speichern Sie die nicht gesicherten Word-Dokumente.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert durchführen können, erstellen Sie ein Client-Objekt des Document Security-Dienstes.

**Abrufen eines richtliniengeschützten Word-Dokuments**

Sie müssen ein richtliniengeschütztes Word-Dokument abrufen, um eine Richtlinie zu entfernen. Wenn Sie versuchen, eine Richtlinie aus einem Word-Dokument zu entfernen, das nicht durch eine Richtlinie geschützt ist, wird eine Ausnahme verursacht.

**Richtlinie aus Word-Dokument entfernen**

Sie können eine Richtlinie aus einem richtliniengeschützten Word-Dokument entfernen, sofern in den Verbindungseinstellungen ein Administrator angegeben ist. Ist dies nicht der Fall, muss die zum Schützen eines Dokuments verwendete Richtlinie die `SWITCH_POLICY` -Berechtigung, um eine Richtlinie aus einem Word-Dokument zu entfernen. Außerdem muss der in den AEM Forms-Verbindungseinstellungen angegebene Benutzer über diese Berechtigung verfügen. Andernfalls wird eine Ausnahme ausgelöst.

**Ungesichertes Word-Dokument speichern**

Nachdem der Document Security-Dienst eine Richtlinie aus einem Word-Dokument entfernt hat, können Sie das ungesicherte Word-Dokument als DOC-Datei speichern.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Anwenden von Richtlinien auf Word-Dokumente](protecting-documents-policies.md#applying-policies-to-word-documents)

### Eine Richtlinie mithilfe der Java-API aus einem Word-Dokument entfernen {#remove-a-policy-from-a-word-document-using-the-java-api}

Entfernen Sie mithilfe der Document Security-API (Java) eine Richtlinie aus einem richtliniengeschützten Word-Dokument:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Document Security Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `RightsManagementClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen eines richtliniengeschützten Word-Dokuments

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das richtliniengeschützte Word-Dokument darstellt, indem es seinen Konstruktor verwendet und einen Zeichenfolgenwert übergibt, der den Speicherort des Word-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Richtlinie aus Word-Dokument entfernen

   * Erstellen Sie eine `DocumentManager` -Objekt durch Aufrufen der `RightsManagementClient` -Objekt `getDocumentManager` -Methode.
   * Entfernen Sie eine Richtlinie aus dem Word-Dokument, indem Sie die `DocumentManager` -Objekt `removeSecurity` -Methode und Übergabe der `com.adobe.idp.Document` -Objekt, das das richtliniengeschützte Word-Dokument enthält. Diese Methode gibt eine `com.adobe.idp.Document` -Objekt, das ein ungesichertes Word-Dokument enthält.

1. Ungesichertes Word-Dokument speichern

   * Erstellen Sie eine `java.io.File` -Objekt ein und stellen Sie sicher, dass die Dateierweiterung DOC lautet.
   * Rufen Sie die `Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `Document` -Objekt auf die Datei verweist (stellen Sie sicher, dass Sie die `Document` -Objekt, das von der `removeSecurity` -Methode).

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in der folgenden Kurzanleitung:

* &quot;Schnellstart (SOAP-Modus): Entfernen einer Richtlinie aus einem Word-Dokument mithilfe der Java-API&quot;

### Eine Richtlinie mithilfe der Webdienst-API aus einem Word-Dokument entfernen {#remove-a-policy-from-a-word-document-using-the-web-service-api}

Entfernen Sie mithilfe der Document Security-API (Webdienst) eine Richtlinie aus einem richtliniengeschützten Word-Dokument:

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Document Security Client-API-Objekts

   * Erstellen Sie eine `RightsManagementServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `RightsManagementServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `RightsManagementServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.


1. Abrufen eines richtliniengeschützten Word-Dokuments

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern des richtliniengeschützten Word-Dokuments verwendet, aus dem die Richtlinie entfernt wird.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des Word-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Feld mit dem Inhalt des Byte-Arrays.

1. Richtlinie aus Word-Dokument entfernen

   Entfernen Sie die Richtlinie aus dem Word-Dokument, indem Sie die `RightsManagementServiceClient` -Objekt `removePolicySecurity` -Methode und Übergabe der `BLOB` -Objekt, das das richtliniengeschützte Word-Dokument enthält. Diese Methode gibt eine `BLOB` -Objekt, das ein ungesichertes Word-Dokument enthält.

1. Ungesichertes Word-Dokument speichern

   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des ungesicherten Word-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt der `BLOB` -Objekt, das von der `removePolicySecurity` -Methode. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` -Feld.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in der folgenden Kurzanleitung:

* &quot;Schnellstart (MTOM): Entfernen einer Richtlinie aus einem Word-Dokument mithilfe der Webdienst-API&quot;

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
