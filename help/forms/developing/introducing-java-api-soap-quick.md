---
title: Einführung in Java API QuickStart
seo-title: Introducing Java API QuickStart
description: Mit Schnellstartprogrammen für Java-API können Sie die Entwicklung von Programmen beschleunigen, die mit AEM Forms-Diensten interagieren. Sie können die Schnellstartprogramme der Java-API in Ihrem Projekt als Ausgangspunkt verwenden und anpassen.
seo-description: Java API Quick Start programs help you expedite the development of programs that interact with AEM Forms services. You can use the Java API Quick Start programs in your project as a starting point and customize it.
uuid: 480e1809-f789-4ad8-b5d5-2d97aba8411a
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: development-tools, develop
discoiquuid: 38fd51ec-347e-4ae3-86d4-9d2429f79bdd
role: Developer
exl-id: 8a3f2eb9-d686-49d4-baa4-c0921622d01a
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---

# Einführung in Java API - Schnellstart {#introducing-java-api-quickstart}

Adobe AEM Forms API Quick Start kann Ihnen dabei helfen, Ihre Bemühungen zur Entwicklung von Programmen zu beschleunigen, die mit AEM Forms-Diensten interagieren. *Schnellstart* s sind komplette Programme, die Sie kopieren und in Ihre eigenen Projekte einfügen und als Ausgangspunkt verwenden können. Sie können einen Schnellstart ausführen, um zu sehen, wie er sich verhält, und ihn für Ihre eigenen Anforderungen anpassen.

AEM Forms-Vorgänge können mit der stark typisierten AEM Forms-API ausgeführt werden und der Verbindungsmodus sollte auf SOAP festgelegt werden.

Java-Schnellstart mit starker Typisierung für die API bietet eine Liste von JAR-Dateien, die zum Ausführen der Java-Anwendung erforderlich sind. Die meisten Java-Schnellstarts sind Konsolenanwendungen, die in `main`. Das Forms Java-Schnellstart mit starker Typisierung für die API wird jedoch als Java-Servlet implementiert, das in einer Webanwendung ausgeführt wird.

Die Liste der JAR-Dateien befindet sich in einem Kommentarabschnitt am Anfang des Schnellstarts. Der folgende Kommentar befindet sich beispielsweise in einem Schnellstart für die Ausgabe und ist eine typische JAR-Dateiliste, die in jedem Schnellstart für Java enthalten ist.

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-output-client.jar 
     * 2. adobe--client.jar 
     * 3. adobe-usermanager-client.jar 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/Adobe/Adobe_Experience_Manager_forms/SDK/client-libs/common 
     * 
     * The adobe-utilities.jar file is located in the following path: 
     * <install directory>/Adobe/Adobe_Experience_Manager_forms/SDK/client-libs/jboss 
     * 
     * The jboss-client.jar file is located in the following path: 
     * <install directory>/Adobe/Adobe_Experience_Manager_forms/jboss/bin/client 
     * 
     * If you want to invoke a remote AEM Forms instance and there is a 
     * firewall between the client application and AEM Forms, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/Adobe/Adobe_Experience_Manager_forms/SDK/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     * 
     * For complete details about the location of the AEM Forms JAR files,  
     * see "Including AEM Forms library files" in Programming  
     * with AEM Forms 
     */
```

## Schnellstart für mehrere Dienste {#multiple-services-quick-start}

Die meisten Schnellstarts befinden sich unter *Programmieren mit AEM Forms* Rufen Sie einen bestimmten Dienst auf, um einen Vorgang auszuführen. Einige Schnellstarts rufen jedoch mehrere AEM Forms-Dienste auf, um einen bestimmten Workflow auszuführen. Die folgende Liste enthält Java-Schnellstarts, die mehr als einen AEM Forms-Dienst aufrufen:

[Schnellstart (SOAP-Modus): Übergeben eines Dokuments im AEM Forms-Repository an den Output-Dienst mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-a-document-located-in-the-repository-to-the-output-service-using-the-java-api) (ruft den Repository- und Output-Dienst auf)

[Schnellstart (SOAP-Modus): Erstellen eines PDF-Dokuments basierend auf Fragmenten mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-fragments-using-the-java-api) (ruft den Assembler- und Output-Dienst auf)

[Schnellstart (SOAP-Modus): Erstellen von PDF-Dokumenten mit gesendeten XML-Daten mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-creating-pdf-documents-with-submitted-xml-data-using-the-java-api) (ruft den Forms-, Output- und Document Management-Dienst auf)

[Schnellstart (SOAP-Modus): Übergeben von Dokumenten an den Forms-Dienst mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-passing-documents-to-the-forms-service-using-the-java-api) (ruft den Forms- und Document Management-Dienst auf)

[Schnellstart (SOAP-Modus): Digitales Signieren eines XFA-basierten Formulars mit der Java-API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-digitally-signing-a-xfa-based-form-using-the-java-api) (ruft den Forms- und Signature-Dienst auf)

[Schnellstart (SOAP-Modus): Verwalten von Rollen und Berechtigungen mithilfe der Java-API](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-managing-roles-and-permissions-using-the-java-api) (Ruft den DirectoryManager und den AuthorizationManager-Dienst auf)

[Schnellstart (SOAP-Modus): Übergeben von Dokumenten an den Output-Dienst mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-documents-to-the-output-service-using-the-java-api) (Aufrufen des Output- und Document Management-Dienstes)

>[!NOTE]
>
>Schnellstart für die Programmierung mit AEM Forms basiert auf der Bereitstellung von AEM Forms auf JBoss® Application Server und dem Microsoft® Windows®-Betriebssystem. Wenn Sie jedoch ein anderes Betriebssystem wie UNIX® verwenden, ersetzen Sie Windows-spezifische Pfade durch Pfade, die vom jeweiligen Betriebssystem unterstützt werden. Wenn Sie einen anderen J2EE-Anwendungsserver verwenden, stellen Sie sicher, dass Sie gültige Verbindungseigenschaften angeben. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)

>[!NOTE]
>
>Die meisten Webdienst-Schnellstarts werden in C# geschrieben und verwenden das .NET-Framework. Sie können jedoch eine Client-Anwendungslogik erstellen, die in der Lage ist, AEM Forms-Dienste in jeder Entwicklungsumgebung aufzurufen, die SOAP-Standards unterstützt. (Siehe [Aufrufen von AEM Forms mithilfe von Webdiensten](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).
