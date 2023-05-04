---
title: APIs zum Zugriff auf Briefinstanzen
seo-title: APIs to access letter instances
description: Erfahren Sie, wie Sie mit APIs auf Briefinstanzen zugreifen können.
seo-description: Learn how to use APIs to access letter instances.
uuid: e7fb7798-f49d-458f-87f5-22df5f3e7d10
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: 9c27f976-972a-4250-b56d-b84a7d72f8c8
feature: Correspondence Management
exl-id: 64ca6baa-5534-4227-a969-fb67cc6eb207
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 61%

---

# APIs zum Zugriff auf Briefinstanzen {#apis-to-access-letter-instances}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht {#overview}

Mithilfe der Benutzeroberfläche &quot;Korrespondenz erstellen&quot;von Correspondence Management können Sie Entwürfe von Briefinstanzen unter &quot;Fortschritt&quot;speichern und es gibt gesendete Briefinstanzen.

Correspondence Management stellt Ihnen APIs bereit, mit denen Sie die Listenschnittstelle für die Arbeit mit gesendeten Briefinstanzen oder Entwürfen erstellen können. Die APIs listen und öffnen gesendete und Entwurfsbriefinstanzen eines Agenten, damit der Agent weiterhin am Entwurf oder an der gesendeten Briefinstanz arbeiten kann.

## Abrufen von Briefinstanzen {#fetching-letter-instances}

Correspondence Management stellt APIs bereit, um  Briefinstanzen mithilfe von LetterInstanceService abzurufen.

| Methode | Beschreibung |
|--- |--- |
| getAllLetterInstances | Ruft Briefinstanzen anhand des Eingabeabfrageparameters ab. Um alle Briefinstanzen abzurufen, übergeben Sie den Abfrageparameter als null. |
| getLetterInstance | Ruft die angegebene Briefinstanz basierend auf der Briefinstanz-ID ab. |
| letterInstanceExists | Überprüft anhand des angegebenen Namens, ob eine Briefinstanz vorhanden ist. |

>[!NOTE]
>
>LetterInstanceService ist ein OSGI-Service, dessen Instanz mit Hilfe von @Reference in Java abgerufen werden kann\
>Klasse oder sling.getService(LetterInstanceService. Class) in JSP.

### Verwendung von getAllLetterInstances {#using-nbsp-getallletterinstances}

Die folgende API findet die Briefinstanzen basierend auf dem Abfrageobjekt (Gesendet und Entwurf). Wenn das Abfrageobjekt null ist, werden alle Briefinstanzen zurückgegeben. Diese API gibt eine Liste von [LetterInstanceVO](https://helpx.adobe.com/de/aem-forms/6-2/javadocs/com/adobe/icc/dbforms/obj/LetterInstanceVO.html)-Objekten zurück, die zum Extrahieren zusätzlicher Informationen der Briefinstanz verwendet werden können

**Syntax**: `List getAllLetterInstances(Query query) throws ICCException;`

<table> 
 <tbody> 
  <tr> 
   <td><strong>Parameter</strong></td> 
   <td><strong>Beschreibung</strong></td> 
  </tr> 
  <tr> 
   <td>Abfrage</td> 
   <td>Der Abfrageparameter wird zum Suchen/Filtern der Briefinstanz verwendet. Hier unterstützt die Abfrage nur Attribute/Eigenschaften des Objekts auf höchster Ebene. Abfrage besteht aus Anweisungen und der im Statement-Objekt verwendete "attributeName"sollte der Name der Eigenschaft im Briefinstanzobjekt sein.<br /> </td> 
  </tr> 
 </tbody> 
</table>

#### Beispiel 1: Abrufen aller Briefinstanzen des Typs &quot;SUBMITTED&quot; {#example-fetch-all-the-letter-instances-of-type-submitted}

Der folgende Code gibt die Liste der gesendeten Briefinstanzen zurück. Um nur Entwürfe zu erhalten, ändern Sie `LetterInstanceType.COMPLETE.name()` in `LetterInstanceType.DRAFT.name().`

```java
@Reference
LetterInstanceService letterInstanceService;
Query query = new Query();
 
List<LetterInstanceVO> submittedLetterInstances = new ArrayList<LetterInstanceVO>();
 
Statement statementForInstanceType = new Statement();
statementForInstanceType.setAttributeName("letterInstanceType");
statementForInstanceType.setOperator(Operator.EQUALS);
statementForInstanceType.setAttributeValue(LetterInstanceType.COMPLETE.name());
query.addStatement(statementForInstanceType);
submittedLetterInstances = letterInstanceService.getAllLetterInstances(query);
```

#### Beispiel 2: Rufen Sie alle Briefinstanzen, die von einem Benutzer gesendet wurden auf; der Briefinstanztyp ist ENTWURF {#example-nbsp-fetch-all-the-letter-instances-submitted-by-a-user-and-letter-instance-type-is-draft}

Der folgende Code hat mehrfache Aussagen in der gleichen Abfrage zum Filtern der Ergebnisse, basierend auf unterschiedlichen Kriterien wie von einem Benutzer gesendete Briefinstanz (Attribut gesendet von) und Typ von letterInstanceType ist ENTWURF.

```java
@Reference
LetterInstanceService letterInstanceService;
 
String submittedBy = "tglodman";
Query query = new Query();
 
List<LetterInstanceVO> submittedLetterInstances = new ArrayList<LetterInstanceVO>();
 
Statement statementForInstanceType = new Statement();
statementForInstanceType.setAttributeName("letterInstanceType");
statementForInstanceType.setOperator(Operator.EQUALS);
statementForInstanceType.setAttributeValue(LetterInstanceType.COMPLETE.name());
query.addStatement(statementForInstanceType);
 
Statement statementForSubmittedBy = new Statement();
statementForSubmittedBy .setAttributeName("submittedby");
statementForSubmittedBy .setOperator(Operator.EQUALS);
statementForSubmittedBy .setAttributeValue(submittedBy);
query.addStatement(statementForSubmittedBy );
submittedLetterInstances = letterInstanceService.getAllLetterInstances(query);
```

### Verwenden von getLetterInstance {#using-nbsp-getletterinstance}

Rufen Sie die Briefinstanz auf, die von der angegebenen Briefinstanz-ID identifiziert wird. Es wird „null“ zurückgegeben, wenn die Instanz-ID nicht übereinstimmt.

**Syntax**: `public LetterInstanceVO getLetterInstance(String letterInstanceId) throws ICCException;`

```java
@Reference
LetterInstanceService letterInstanceService;
String letterInstanceId = "/content/apps/cm/letterInstances/1001/sampleLetterInstance";
LetterInstanceVO letterInstance = letterInstanceService.getLetterInstance(letterInstanceId );
```

### Überprüfen, ob Briefinstanz vorhanden ist {#verifying-if-letterinstance-exist}

Prüfen Sie anhand des angegebenen Namens, ob eine Briefinstanz vorhanden ist

**Syntax**: `public Boolean letterInstanceExists(String letterInstanceName) throws ICCException;`

| **Parameter** | **Beschreibung** |
|---|---|
| letterInstanceName | Name der Briefinstanz, deren Existenz Sie überprüfen möchten. |

```java
@Reference
LetterInstanceService letterInstanceService;
String letterInstanceName = "sampleLetterInstance";
Boolean result = letterInstanceService.letterInstanceExists(letterInstanceName );
```

## Öffnen von Briefinstanzen {#opening-letter-instances}

Briefinstanz kann vom Typ „Gesendet“ oder „Entwurf“ sein. Das Öffnen beider Briefinstanztypen zeigt unterschiedliche Verhaltensweisen:

* Im Falle der Briefinstanz &quot;Gesendet&quot; wird eine PDF geöffnet, die die Briefinstanz darstellt. Die Briefinstanz &quot;Gesendet&quot;, die auf dem Server persistiert wird, enthält auch die dataXML und verarbeitete XDP, die verwendet werden können, um einen Anwendungsfall wie das Erstellen einer PDF/A auszuführen und weiter anzupassen.
* Im Falle der Briefinstanz „Entwurf“ wird die Benutzeroberfläche „Korrespondenz erstellen“ in den genauen Status wie zuvor neu geladen, als sie als Entwurf erstellt wurde

### Öffnen der Briefinstanz „Entwurf“  {#opening-draft-letter-instance-nbsp}

CCR Benutzeroberfläche  unterstützt den Parameter cmLetterInstanceId, der zum Neuladen des Briefs verwendet werden kann.

`https://[hostName]:[portNo]/[contextPath]//aem/forms/createcorrespondence.html?random=[randomNo]&cmLetterInstanceId=[letterInstanceId]`

>[!NOTE]
>
>Sie müssen beim Neuladen einer Korrespondenz weder cmLetterId noch cmLetterName/State/Version angeben, da die gesendeten Daten bereits alle Details zu dieser Korrespondenz enthalten. RandomNo wird verwendet, um Probleme mit dem Browser-Cache zu vermeiden. Sie können Zeitstempel als zufällige Zahl verwenden.

### Öffnen der gesendeten Briefinstanz {#opening-submitted-letter-instance}

Gesendete PDF kann direkt mit der Briefinstanz-ID geöffnet werden:

`https://[hostName]:[portNo]/[contextPath]/[letterInstanceId]`
