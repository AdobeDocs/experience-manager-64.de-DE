---
title: Dienst-Container
seo-title: Service container
description: Erfahren Sie mehr über die Funktionen des Dienstcontainers. Darüber hinaus werden in diesem Artikel auch die verschiedenen Möglichkeiten beschrieben, wie Sie AEM Forms-Dienste programmgesteuert aufrufen können.
seo-description: Learn more about the functionalities of service container. In addition, the article also describes the different ways in which you can programmatically invoke AEM Forms services.
uuid: 89f2fd3d-63d7-4b70-b335-47314441f3ec
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: development-tools, coding
discoiquuid: dd9c0ec4-a195-4b78-8992-81d0efcc0a7e
role: Developer
exl-id: 92351e2d-1928-4bc4-aaff-d557ee09d1ee
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '967'
ht-degree: 94%

---

# Dienst-Container {#service-container}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

AEM Forms-Services, die sich im Service-Container befinden (einschließlich Standard-Services wie dem Verschlüsselungs-Service, langlebigen und kurzlebigen Prozessen), können mit verschiedenen Providern, wie z. B. einem EJB-Provider, aufgerufen werden. Ein EJB-Anbieter ermöglicht den Aufruf von AEM Forms-Services über RMI/IIOP. Ein Webservice-Anbieter stellt Services als Web-Services (WSDL-Generierung) unter Verwendung von Standards wie SOAP/HTTP und SOAP/JMS bereit.

In der folgenden Tabelle werden die verschiedenen Methoden zum programmgesteuerten Aufrufen von AEM Forms-Services beschrieben.

<table>
 <thead>
  <tr>
   <th><p>Aufrufmethode</p></th> 
   <th><p>Beschreibung</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr>
   <td><p>Remote-Integration</p></td> 
   <td><p>Die Remote-Integration bietet Flex-Clients die Möglichkeit, Service-Vorgänge aufzurufen. (Siehe <a href="/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting">Aufrufen von AEM Forms mithilfe von AEM Forms Remoting (für AEM-Formulare nicht mehr unterstützt)</a>.)</p></td> 
  </tr> 
  <tr>
   <td><p>Java-API</p></td> 
   <td><p>Eine Java-API kann einen AEM Forms-Service aufrufen. Die Java-API ist in Client-Bibliotheken und die Java-Aufruf-API unterteilt. (Siehe <a href="/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api">Aufrufen von AEM Forms mithilfe der Java-API</a>.)</p></td> 
  </tr> 
  <tr>
   <td><p>Web-Services</p></td> 
   <td><p>AEM Forms unterstützt Webservice-Standards wie SOAP/HTTP. Ein Service kann als Webservice verfügbar gemacht werden, wobei die WSDL den vom W3C definierten Webservice-Standards entspricht.</p><p>Ein Service kann von jedem Webservice-Stapel aus aufgerufen werden, einschließlich .NET Framework und Sun™ Web Services SDK. (Siehe <a href="/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services">Aufrufen von AEM Forms mithilfe von Web-Services</a>.)</p></td> 
  </tr> 
  <tr>
   <td><p>REST-Anfragen</p></td> 
   <td><p>AEM Forms unterstützt REST-Anfragen. Ein Service kann direkt von einer HTML-Seite aus aufgerufen werden. (Siehe <a href="/help/forms/developing/invoking-aem-forms-using-rest.md#invoking-aem-forms-using-rest-requests">Aufrufen von AEM Forms mithilfe von REST-Anfragen</a>.)</p></td> 
  </tr> 
 </tbody> 
</table>

Die folgende Abbildung zeigt die verschiedenen Möglichkeiten, wie AEM Forms-Services programmgesteuert aufgerufen werden können.

>[!NOTE]
>
>Sie können das AEM Forms-SDK nicht nur zum Erstellen von Client-Programmen verwenden, die AEM Forms-Services aufrufen können, sondern auch zum Erstellen von Komponenten, die im Service-Container bereitgestellt werden können. Sie können beispielsweise eine Bankkomponente erstellen, die benutzerdefinierte Datentypen enthält, die in Prozessen verwendet werden können. Das heißt, Sie können einen Datentyp wie `com.adobe.idp.BankAccount` erstellen. Anschließend können Sie `com.adobe.idp.BankAccount`-Instanzen in Ihren Client-Programmen erstellen.

Der Service-Container bietet die folgenden Funktionen:

* Ermöglicht den Aufruf von AEM Forms-Services mit verschiedenen Methoden. Sie können einen Service konfigurieren, indem Sie Endpunkte festlegen, damit er mit allen Methoden aufgerufen werden kann: Remoting, die Java-API, Web-Services und REST. (Siehe [Programmgesteuertes Verwalten von Endpunkten](/help/forms/developing/programmatically-endpoints.md#programmatically-managing-endpoints).)
* Konvertiert eine Nachricht in ein normalisiertes Format, das als Aufrufanfrage bezeichnet wird. Eine Aufrufanfrage wird von einem Client-Programm (oder einem anderen Service) an einen Service gesendet, der sich im Service-Container befindet. Eine Aufrufanfrage enthält Informationen wie den Namen des aufzurufenden Services und Datenwerte, die zur Durchführung des Vorgangs erforderlich sind. Viele Services benötigen ein Dokument, um einen Vorgang auszuführen. Daher enthält eine Aufrufanfrage normalerweise ein Dokument, bei dem es sich um PDF-Daten, XDP-Daten, XML-Daten usw. handeln kann.
* Sendet Aufrufanfragen an entsprechende Services (der Name des aufzurufenden Services ist Teil der Aufrufanfrage).
* Führt Aufgaben durch wie die Bestimmung, ob der Aufrufer berechtigt ist, den angegebenen Service-Vorgang aufzurufen. Die Aufrufanfrage muss einen gültigen Benutzernamen und ein gültiges Kennwort für AEM Forms enthalten.

   Es gibt verschiedene Möglichkeiten, eine Aufrufanfrage an einen Service zu senden. Außerdem gibt es verschiedene Möglichkeiten, erforderliche Eingabewerte an den Service zu senden. Angenommen, Sie verwenden die Java-API zum Aufrufen eines Services, für den ein PDF-Dokument erforderlich ist. Die entsprechende Java-Methode enthält einen Parameter, der ein PDF-Dokument akzeptiert. In diesem Fall lautet der Datentyp des Parameters `com.adobe.idp.Document`. (Siehe [Übergeben von Daten an AEM Forms-Services mithilfe der Java-API](/help/forms/developing/invoking-aem-forms-using-java.md#passing-data-to-aem-forms-services-using-the-java-api).)

   Wenn Sie einen Service mithilfe von überwachten Ordnern aufrufen, wird eine Aufrufanfrage gesendet, sobald Sie eine Datei in einem konfigurierten überwachten Ordner platzieren. Wenn Sie einen Service per E-Mail aufrufen, wird eine Aufrufanfrage an einen Service gesendet, sobald eine E-Mail-Nachricht in einem konfigurierten Posteingang eingeht.

   Der Service-Container sendet nach Durchführung des Vorgangs eine Aufrufantwort zurück. Eine Aufrufantwort enthält Informationen wie die Vorgangsergebnisse. Wenn der Vorgang beispielsweise ein PDF-Dokument ändert, enthält die Aufrufantwort das geänderte PDF-Dokument. Wenn der Vorgang nicht erfolgreich war, enthält die Aufrufantwort eine Fehlermeldung.

   Eine Aufrufantwort kann auf dieselbe Weise abgerufen werden wie eine Aufrufanfrage. Das heißt, wenn die Aufrufanfrage mit der Java-API gesendet wird, kann mit der Java-API eine Aufrufantwort abgerufen werden. Angenommen, ein Vorgang ändert ein PDF-Dokument. Sie können das geänderte PDF-Dokument abrufen, indem Sie den Rückgabewert der Java-Methode abrufen, die den Service aufgerufen hat.

   Wenn ein langlebiger Prozess aufgerufen wird, enthält eine Aufrufantwort einen Kennungswert, der mit der Aufrufanfrage verknüpft ist. Mithilfe dieses Kennungswerts können Sie den Status des Prozesses zu einem späteren Zeitpunkt überprüfen. Nehmen wir zum Beispiel den langlebigen Service MortgageLoan. Mithilfe des Kennungswerts können Sie überprüfen, ob der Prozess erfolgreich abgeschlossen wurde. (Siehe [An Menschen orientierte langlebige Prozesse aufrufen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).)

   Das folgende Diagramm zeigt ein Client-Programm (das die Java-API verwendet), das einen Service aufruft.

   Wenn ein Client-Programm einen Service aufruft, treten drei Ereignisse auf:

   1. Ein Client-Programm sendet eine Aufrufanfrage an einen Service.
   1. Der Service führt den in der Aufrufanfrage angegebenen Vorgang aus.
   1. Der Service-Container gibt eine Aufrufantwort an das Client-Programm zurück.

**Siehe auch**

[Grundlagen zu AEM Forms-Prozessen](/help/forms/developing/aem-forms-processes.md#understanding-aem-forms-processes)

[Aufrufen von AEM Forms mithilfe von AEM Forms Remoting (für AEM Forms nicht mehr unterstützt)](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting)

[AEM Forms mit der JavaAPI aufrufen](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[AEM Forms mit Web Services aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services)

[An Menschen orientierte langlebige Prozesse aufrufen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes)

[Aufrufen von AEM Forms mithilfe von REST-Anforderungen](/help/forms/developing/invoking-aem-forms-using-rest.md#invoking-aem-forms-using-rest-requests)
