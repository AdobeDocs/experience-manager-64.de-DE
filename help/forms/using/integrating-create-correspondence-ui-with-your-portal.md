---
title: Integrieren der Benutzeroberfläche „Korrespondenz erstellen“ in Ihr benutzerdefiniertes Portal
seo-title: Integrating Create Correspondence UI with your custom portal
description: Erfahren Sie, wie Sie die Benutzeroberfläche "Korrespondenz erstellen"in Ihr benutzerdefiniertes Portal integrieren.
seo-description: Learn how to integrate create correspondence UI with your custom portal
uuid: 4ae9c5fb-bb9d-46d8-be84-455f386ab443
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: cb232931-60b7-4956-bc77-10636c19325e
feature: Correspondence Management
exl-id: 8b1bbd85-66ba-4e96-917a-d768d84a417f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 20%

---

# Integrieren der Benutzeroberfläche „Korrespondenz erstellen“ in Ihr benutzerdefiniertes Portal {#integrating-create-correspondence-ui-with-your-custom-portal}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht {#overview}

In diesem Artikel wird beschrieben, wie Sie die Lösung &quot;Korrespondenz erstellen&quot;in Ihre Umgebung integrieren können.

## URL-basierter Aufruf {#url-based-invocation}

Eine Möglichkeit, die Anwendung &quot;Korrespondenz erstellen&quot;über ein benutzerdefiniertes Portal aufzurufen, besteht darin, die URL mit den folgenden Anforderungsparametern vorzubereiten:

* die Kennung für die Briefvorlage (unter Verwendung des cmLetterId-Parameters) oder den Namen der Briefvorlage (unter Verwendung des cmLetterName-Parameters)

* die URL für die XML-Datei, die aus der gewünschten Datenquelle (unter Verwendung des cmDataUrl-Parameters) erfasst wurde

Beispielsweise würde das benutzerdefinierte Portal die URL als\
`https://[server]:[port]/[contextPath]/aem/forms/createcorrespondence.html?random=[timestamp]&cmLetterId=[letter identifier]&cmDataUrl=[data URL]` vorbereiten, wobei es sich um die href eines Links auf dem Portal handeln könnte.\
Wenn das Portal den Namen der Briefvorlage enthält, kann die URL\
`https://[server]:[port]/content/cm/createcorrespondence.html?cmLetterName=[letter name]&cmDataUrl=[data URL]`.

>[!NOTE]
>
>Ein solcher Aufruf ist nicht sicher, da die erforderlichen Parameter als GET-Anfrage übergeben werden, indem der gleiche (deutlich sichtbare) Parameter in der URL offen gelegt wird.

>[!NOTE]
>
>Bevor Sie die Anwendung &quot;Korrespondenz erstellen&quot;aufrufen, speichern und laden Sie die Daten hoch, um die Benutzeroberfläche &quot;Korrespondenz erstellen&quot;unter der angegebenen dataURL aufzurufen. Dies kann entweder vom benutzerdefinierten Portal selbst oder über einen anderen Back-End-Prozess erfolgen.

## Inline-datenbasierter Aufruf {#inline-data-based-invocation}

Eine weitere (und sicherere) Möglichkeit, die Anwendung &quot;Korrespondenz erstellen&quot;aufzurufen, besteht darin, einfach die URL unter `https://[server]:[port]/[contextPath]/aem/forms/createcorrespondence.html`, während die Parameter und Daten gesendet werden, um die Anwendung &quot;Korrespondenz erstellen&quot;als POST-Anfrage aufzurufen (diese für den Endbenutzer auszublenden). Dies bedeutet auch, dass Sie jetzt die XML-Daten für die Anwendung &quot;Korrespondenz erstellen&quot;inline übergeben können (als Teil derselben Anforderung, unter Verwendung des cmData-Parameters), was im vorherigen Ansatz nicht möglich/ideal war.

### Parameter für die Angabe von Briefen {#parameters-for-specifying-letter}

<table> 
 <tbody>
  <tr>
   <td><strong>Name</strong></td> 
   <td><strong>Typ</strong></td> 
   <td><strong>Beschreibung</strong></td> 
  </tr>
  <tr>
   <td>cmLetterInstanceId</td> 
   <td>Zeichenfolge</td> 
   <td>Der Bezeichner für die Briefinstanz.</td> 
  </tr>
  <tr>
   <td>cmLetterName</td> 
   <td>Zeichenfolge</td> 
   <td><p>Die Kennung für die Briefvorlage. </p> <p>Wenn auf einem Server mehrere CM-Buchstaben mit demselben Namen vorhanden sind, löst die Verwendung des cmLetterName-Parameters in der URL den Fehler "Mehrere Buchstaben mit dem Namen vorhanden"aus. Verwenden Sie in diesem Fall den Parameter cmLetterId in der URL anstelle von cmLetterName.</p> </td> 
  </tr>
  <tr>
   <td>cmLetterId</td> 
   <td>Zeichenfolge</td> 
   <td>Der Name der Briefvorlage.</td> 
  </tr>
 </tbody>
</table>

Die Reihenfolge der Parameter in der Tabelle gibt die Voreinstellungen der Parameter an, die zum Laden des Briefs verwendet werden.

### Parameter zum Angeben der XML-Datenquelle {#parameters-for-specifying-the-xml-data-source}

<table> 
 <tbody>
  <tr>
   <td><strong>Name</strong></td> 
   <td><strong>Typ</strong></td> 
   <td><strong>Beschreibung</strong></td> 
  </tr>
  <tr>
   <td>cmDataUrl<br /> </td> 
   <td>URL</td> 
   <td>XML-Daten aus einer Quelldatei mit Grundprotokollen wie cq, ftp, http oder file.<br /> </td> 
  </tr>
  <tr>
   <td>cmLetterInstanceId</td> 
   <td>Zeichenfolge</td> 
   <td>Verwenden von XML-Daten, die in der Briefinstanz verfügbar sind.</td> 
  </tr>
  <tr>
   <td>cmUseTestData</td> 
   <td>Boolesch</td> 
   <td>Um die im Datenwörterbuch angehängten Testdaten wiederzuverwenden.</td> 
  </tr>
 </tbody>
</table>

Die Reihenfolge der Parameter in der Tabelle gibt die Voreinstellungen der Parameter an, die zum Laden der XML-Daten verwendet werden.

### Andere Parameter {#other-parameters}

<table> 
 <tbody>
  <tr>
   <td><strong>Name</strong></td> 
   <td><strong>Typ</strong></td> 
   <td><strong>Beschreibung</strong></td> 
  </tr>
  <tr>
   <td>cmPreview<br /> </td> 
   <td>Boolesch</td> 
   <td>True zum Öffnen des Briefs im Vorschaumodus<br /> </td> 
  </tr>
  <tr>
   <td>Willkürlich</td> 
   <td>Zeitstempel</td> 
   <td>Beheben von Problemen beim Zwischenspeichern im Browser.</td> 
  </tr>
 </tbody>
</table>

Wenn Sie ein HTTP- oder CQ-Protokoll für cmDataURL verwenden, muss die HTTP/CQ-URL anonym zugänglich sein.
