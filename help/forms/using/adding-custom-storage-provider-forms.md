---
title: Benutzerdefinierter Speicher für die Komponente „Entwürfe und Sendungen“
seo-title: Custom storage for drafts and submissions component
description: Erfahren Sie, wie Sie die Speicherung von Benutzerdaten für Entwürfe und Übermittlungen anpassen.
seo-description: See how to customize the storage of user data for drafts and submissions.
uuid: ac2e80ee-a9c7-44e6-801e-fe5a840cb7f8
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 154255e7-468a-42e6-a33d-eee691cf854d
feature: Forms Portal
exl-id: 22f78940-de5f-4e16-b1f8-c3762d81802b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 48%

---

# Benutzerdefinierter Speicher für Komponenten „Drafts and Submissions (Entwurf und Übermittlung)“ {#custom-storage-for-drafts-and-submissions-component}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht {#overview}

Mit AEM Forms können Sie ein Formular als Entwurf speichern. Mit der Entwurfsfunktion können Sie ein laufendes Formular verwalten, das Sie später von jedem Gerät aus abschließen und senden können.

Standardmäßig speichert AEM Forms die Benutzerdaten, die mit dem Entwurf und der Übermittlung eines Formulars verknüpft sind, im `/content/forms/fp`-Knoten in der Publish-Instanz. Darüber hinaus stellen die AEM Forms-Portalkomponenten Datendienste bereit, mit denen Sie die Implementierung der Speicherung von Benutzerdaten für Entwürfe und Übermittlungen anpassen können. Beispielsweise können Sie Benutzerdaten in einem Datenspeicher speichern.

## Voraussetzungen  {#prerequisites}

* Aktivieren von [Formularportalkomponenten](/help/forms/using/enabling-forms-portal-components.md)
* Erstellen einer [Formularportalseite](/help/forms/using/creating-form-portal-page.md)
* Aktivieren von [adaptiven Formularen für das Formularportal](/help/forms/using/draft-submission-component.md)
* Erfahren Sie mehr über [Implementierungsdetails für benutzerdefiniertes Speichern](/help/forms/using/draft-submission-component.md#customizing-the-storage)

## Entwurfsdatendienst {#draft-data-service}

Um das Speichern der Benutzerdaten für Entwürfe anzupassen, müssen Sie alle Methoden der `DraftDataService`-Schnittstelle implementieren. Im Folgenden Beispielcode werden die Methoden und die Argumente beschrieben.

```java
/**
 * DraftDataService service will get/delete/save user data (attachments and form data) filled with a draft instance of Form  
 */

public interface DraftDataService {
    
    /**
     * To save/modify user data for this userDataID, it will be null in case of creation 
     * @param draftDataID: unique identifier associated with the form data
     * @param formName: name of the form whose draft is being saved
     * @param formData: user data associated with this draft
     * @return userdataID corresponding to which user data has been stored and which can be used later to retrieve this user data
     * @throws FormsPortalException
     */
    public String saveData (String draftDataID, String formName, String formData) throws FormsPortalException;
     
    /**
     * Returns the user data stored against the ID passed as the argument
     * @param userDataID: unique data id for user data associated with a draft
     * @return user data associated with this data ID
     * @throws FormsPortalException
     */
     
    public byte[] getData (String userDataID) throws FormsPortalException;
     
    /**
     * To delete data associated with this draft
     * @param userDataID: unique data id for data associated with a draft
     * @return status of delete operation on data associated with this draft 
     * @throws FormsPortalException
     */
     
    public boolean deleteData (String userDataID) throws FormsPortalException;
     
    /**
     * Saves the attachment for current form instance
     * @param attachmentsBytes: byte array of the attachment to be saved
     * @return unique id (attachmentID) for the attachment just saved (so that it could be retrieved later)
     * @throws FormsPortalException
     */
    public String saveAttachment (byte[] attachmentBytes) throws FormsPortalException;
     
    /**
     * To delete an attachment
     * @param attachmentID: unique id for this attachment
     * @return status of delete operation performed on attachment corresponding to this attachment ID
     * @throws FormsPortalException
     */
    public boolean deleteAttachment (String attachmentID) throws FormsPortalException;
     
    /**
     * To get attachment bytes
     * @param attachmentID: unique id for this attachment
     * @return data corresponding to this attachmentID
     * @throws FormsPortalException
     */
    public byte[] getAttachment (String attachmentID) throws FormsPortalException;
}
```

## Übermittlungsdatendienst {#submission-data-service}

Um das Speichern der Benutzerdaten für Übermittlungen anzupassen, müssen Sie alle Methoden der `SubmitDataService`-Schnittstelle implementieren. Im Folgenden Beispiel-Code werden die Methoden und die Argumente beschrieben.

```java
/**
 * SubmitDataService service will get/delete/submit user data (attachments and form data) filled with a submission of Form  
 */
public interface SubmitDataService {
    
    /**
     * Submits the user data passed in argument map
     * @param userDataID, unique identifier associated with this user data
     * @param formName, name of the form whose draft is being submitted
     * @param formData, user data associated with this submission
     * @return userdataID, corresponding to which the user data has been stored and which can be used later to retrieve this data
     * @throws FormsPortalException
     */
    public String saveData (String userDataID, String formName, String formData) throws FormsPortalException;

    /**
     * Submits the user data provided as byte array
     * @param id
     * @param data
     * @return id corresponding to saved data
     * @throws FormsPortalException
     */
    public String saveData (String id, byte[] data) throws FormsPortalException;
    
    /** Submits the user data provided as byte array asynchronously for the user name provided in the options map 
     * @param data data to be saved in bytes
     * @param options map containing options that affect this save
     * @return id of the saved data instance
     */
    public String saveDataAsynchronusly(byte[] data, Map<String, Object> options) throws FormsPortalException; 
     
    /**
     * Gets the user data stored against the ID passed as argument
     * @param userDataID: unique id associated with this user data for this submission
     * @return user data associated with this submission
     * @throws FormsPortalException
     */
    public byte[] getData(String userDataID) throws FormsPortalException;
     
    /**
     * Deletes user data stored against the userDataID
     * @param userDataID: unique id associated with this user data for this submission
     * @return status of the delete operation on this submission
     * @throws FormsPortalException
     */
     
    public boolean deleteData(String userDataID) throws FormsPortalException;

    /**
     * Submits the attachment bytes passed as argument
     * @param attachmentsBytes: would expect byte array of the attachment for this submission
     * @return attachmentID for the attachment just saved (so that it could be retrieved later) 
     * @throws FormsPortalException
     */
    public String saveAttachment(byte[] attachmentBytes) throws FormsPortalException;
    
    /** Submits the attachment bytes passed as argument asynchronously for the user id provided in options map.
     * @param attachmentBytes would expect byte array of the attachment for this submission
     * @param options map containing options that affect this save
     * @return attachmentID for the attachment just saved (so that it could be retrieved later)
     * @throws FormsPortalException
     */
    public String saveAttachmentAsynchronously(byte[] attachmentBytes, Map<String, Object> options) throws FormsPortalException;
 
    /**
     * To delete an attachment
     * @param attachmentID: Unique id for this attachment
     * @return status of delete operation performed on attachment corresponding to this attachment ID
     * @throws FormsPortalException
     */
    public boolean deleteAttachment (String attachmentID) throws FormsPortalException;
     
    /**
     * To get attachment bytes
     * @param attachmentID: unique id for this attachment
     * @return data corresponding to this attachmentID
     * @throws FormsPortalException
     */
    public byte[] getAttachment (String attachmentID) throws FormsPortalException;
}
```

Das Forms-Portal verwendet das UUID-Konzept (Universally Unique Identifier), um eine eindeutige ID für jeden Entwurf und jedes gesendete Formular zu generieren. Sie können auch eine eigene eindeutige ID generieren. Sie können die FPKeyGeneratorService-Schnittstelle implementieren, ihre Methoden überschreiben und eine benutzerdefinierte Logik entwickeln, um eine benutzerdefinierte eindeutige ID für jeden Entwurf und jedes übermittelte Formular zu generieren. Legen Sie außerdem den Dienstrang der Implementierung der benutzerdefinierten ID-Generierung auf über 0 fest. Dadurch wird sichergestellt, dass die benutzerdefinierte Implementierung anstelle der Standardimplementierung verwendet wird.

```java
public interface FPKeyGeneratorService {
    /**
     * returns a unique id for draft and submission
     *
     * @param none
     * @return unique id in string format as per the implementation
     * @throws FormsPortalException
     */
    public String getUniqueId() throws FormsPortalException;
}
```

Sie können die folgende Anmerkung verwenden, um das Dienstranking für benutzerdefinierte IDs zu erhöhen, die mit dem obigen Code generiert wurden:

`@Properties(value = { @Property(name = "service.ranking", intValue = 15) } )`

Um die obige Anmerkung zu verwenden, importieren Sie das Folgende in Ihr Projekt: 

```
import org.apache.felix.scr.annotations.Properties;
 import org.apache.felix.scr.annotations.Property;
```
