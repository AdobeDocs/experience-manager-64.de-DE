---
title: Konfigurieren sicherer Verwaltungseinstellungen für AEM Forms on JEE
seo-title: Configuring Secure Administration Settings for AEM Forms on JEE
description: Erfahren Sie, wie Sie Benutzerkonten und Services verwalten, die zwar in einer privaten Entwicklungsumgebung erforderlich sind, aber in einer Produktionsumgebung von AEM Forms on JEE nicht benötigt werden.
seo-description: Learn how to administer user accounts and services that, although required in a private development environment, are not required in a production environment of AEM Forms on JEE.
uuid: 04e45d06-f57d-406c-8228-15f483199430
content-type: reference
topic-tags: Security
products: SG_EXPERIENCEMANAGER/6.4
discoiquuid: d211d8b0-e75f-49c3-808d-5d0e26ad3a6b
role: Admin
exl-id: 980d420c-a768-4634-9b8c-3f1d7327285d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 28%

---

# Konfigurieren sicherer Verwaltungseinstellungen für AEM Forms on JEE {#configuring-secure-administration-settings-for-aem-forms-on-jee}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Erfahren Sie, wie Sie Benutzerkonten und Services verwalten, die zwar in einer privaten Entwicklungsumgebung erforderlich sind, aber in einer Produktionsumgebung von AEM Forms on JEE nicht benötigt werden.

Im Allgemeinen verwenden Entwickler die Produktionsumgebung nicht zum Erstellen und Testen ihrer Anwendungen. Daher müssen Sie Benutzerkonten und Dienste verwalten, die zwar in einer privaten Entwicklungsumgebung erforderlich sind, aber in einer Produktionsumgebung nicht benötigt werden.

In diesem Artikel werden Methoden beschrieben, mit denen Sie die Gesamtangriffsfläche durch Verwaltungsoptionen, die AEM Forms on JEE bereitstellt, reduzieren können.

## Nicht erforderlichen Remote-Zugriff auf Dienste deaktivieren {#disabling-non-essential-remote-access-to-services}

Nachdem AEM Forms on JEE installiert und konfiguriert wurde, stehen viele Dienste für den Remote-Aufruf über SOAP und Enterprise JavaBeans™ (EJB) zur Verfügung. Der Begriff Remote bezieht sich in diesem Fall auf alle Aufrufer mit Netzwerkzugriff auf die SOAP-, EJB- oder AMF-Anschlüsse (Action Message Format) für den Anwendungsserver.

AEM Forms on JEE-Dienste erfordern zwar, dass gültige Berechtigungen für einen autorisierten Aufrufer übergeben werden, dennoch sollten Sie den Remote-Zugriff nur für Dienste zulassen, für die der Remote-Zugriff erforderlich ist. Um eine eingeschränkte Barrierefreiheit zu erreichen, sollten Sie den Satz von Diensten mit Remote-Zugriff auf das für ein funktionierendes System mögliche Minimum reduzieren und dann den Remote-Aufruf für die zusätzlichen Dienste aktivieren, die Sie benötigen.

AEM Forms on JEE-Dienste benötigen immer mindestens SOAP-Zugriff. Diese Dienste sind normalerweise für die Verwendung durch Workbench erforderlich, umfassen aber auch Dienste, die von der Workspace-Webanwendung aufgerufen werden.

Führen Sie dieses Verfahren mithilfe der Web-Seite „Programme und Services“ in Administration-Console durch:

1. Melden Sie sich bei Administration-Console an, indem Sie die folgende URL in einen Webbrowser eingeben:

   ```as3
            https://[host name]:[port]/adminui
   ```

1. Klicken **Dienste > Anwendungen und Dienste > Voreinstellungen**.
1. Legen Sie die Voreinstellungen fest, um bis zu 200 Dienste und Endpunkte auf derselben Seite anzuzeigen.
1. Klicken **Dienste** > **Anwendungen und Dienste** > **Endpunktverwaltung**.
1. Auswählen **EJB** von **Anbieter** und klicken Sie auf **Filter**.
1. Um alle EJB-Endpunkte zu deaktivieren, aktivieren Sie das Kontrollkästchen neben allen Endpunkten in der Liste und klicken Sie auf **Deaktivieren**.
1. Klicken **Nächste** und wiederholen Sie den vorherigen Schritt für alle EJB-Endpunkte. Stellen Sie sicher, dass EJB in der Spalte Anbieter aufgeführt ist, bevor Sie Endpunkte deaktivieren.
1. Auswählen **SOAP** von **Anbieter** und klicken Sie auf **Filter**.
1. Um SOAP-Endpunkte zu entfernen, aktivieren Sie das Kontrollkästchen neben jedem Endpunkt in der Liste und klicken Sie auf **Entfernen**. Entfernen Sie nicht die folgenden Endpunkte:

   * AuthenticationManagerService
   * DirectoryManagerService
   * JobManager
   * event_management_service
   * event_configuration_service
   * ProcessManager
   * TemplateManager
   * RepositoryService
   * TaskManagerService
   * TaskQueueManager
   * TaskManagerQueryService
   * WorkspaceSingleSignOn
   * ApplicationManager

1. Klicken **Nächste** und wiederholen Sie den vorherigen Schritt für SOAP-Endpunkte, die nicht in der obigen Liste enthalten sind. Stellen Sie sicher, dass SOAP in der Spalte Anbieter aufgeführt ist, bevor Sie Endpunkte entfernen.

## Nicht erforderlichen anonymen Zugriff auf Dienste deaktivieren {#disabling-non-essential-anonymous-access-to-services}

Einige Formularserverdienste lassen den nicht authentifizierten (anonymen) Aufruf für einige Vorgänge zu. Dies bedeutet, dass ein oder mehrere vom Dienst offen gelegte Vorgänge als ein authentifizierter Benutzer oder gar kein authentifizierter Benutzer aufgerufen werden können.

1. Melden Sie sich bei Administration Console an, indem Sie die folgende URL in einen Webbrowser eingeben:

   ```as3
            https://[host name]:[port]/adminui
   ```

1. Klicken **Dienste > Anwendungen und Dienste > Dienstverwaltung**.
1. Klicken Sie auf den Namen des Dienstes, den Sie deaktivieren möchten (z. B. AuthenticationManagerService).
1. Klicken Sie auf die **Registerkarte Sicherheit**, deaktivieren Sie **Anonymen Zugriff zulassen**, und klicken Sie dann auf **Speichern**.
1. Führen Sie die Schritte 3 und 4 für die folgenden Dienste aus:

   * AuthenticationManagerService
   * EJB
   * E-Mail
   * JobManager
   * WatchedFolder
   * UsermanagerUtilService
   * Remoting
   * RepositoryProviderService
   * EMCDocumentumRepositoryProvider
   * IBMFilenetRepositoryProvider
   * FormAugmenter
   * TaskManagerService
   * TaskManagerConnector
   * TaskManagerQueryService
   * TaskQueueManager
   * TaskEndpointManager
   * UserService
   * WorkspaceSearchTemplateService
   * WorkspacePropertyService
   * OutputService
   * FormsService

   Wenn Sie vorhaben, alle oder einiger dieser Dienste für den Remote-Aufruf verfügbar zu machen, sollten Sie auch überlegen, ob Sie nicht den anonymen Zugriff für diese Dienste deaktivieren. Andernfalls kann jeder Aufrufer mit Netzwerkzugriff auf diesen Dienst den Dienst aufrufen, ohne gültige Anmeldeinformationen zu übergeben.

   Der anonyme Zugriff sollte für alle nicht erforderlichen Dienste deaktiviert werden. Für viele interne Dienste muss die anonyme Authentifizierung aktiviert sein, da sie von potenziell jedem Benutzer im System aufgerufen werden muss, ohne dass eine Vorautorisierung erforderlich ist.

## Standardmäßiges globales Zeitlimit ändern  {#changing-the-default-global-time-out}

Endbenutzer von AEM Forms können sich über Workbench, Web-Anwendungen für AEM Forms oder über benutzerdefinierte Anwendungen, die Server-Services für AEM Forms aufrufen, authentifizieren. Mithilfe einer globalen Zeitlimiteinstellung wird festgelegt, wie lange solche Benutzer AEM Forms nutzen können (mittels einer auf SAML basierenden Bestätigung), bevor sie sich erneut authentifizieren müssen. Der Standardwert ist zwei Stunden. In einer Produktionsumgebung muss die Zeitdauer auf die akzeptable Mindestanzahl von Minuten reduziert werden.

### Minimieren des Zeitlimits für die erneute Authentifizierung {#minimize-reauthentication-time-limit}

1. Melden Sie sich bei Administration Console an, indem Sie die folgende URL in einen Webbrowser eingeben:

   ```as3
            https://[host name]:[port]/adminui
   ```

1. Klicken **Einstellungen > User Management > Konfiguration > Import und Export von Konfigurationsdateien**.
1. Klicken **Export** um eine config.xml -Datei mit den vorhandenen AEM Forms-Einstellungen zu erstellen.
1. Öffnen Sie die XML-Datei in einem Editor und suchen Sie den folgenden Eintrag:

   `<entry key=”assertionValidityInMinutes” value=”120”/>`

1. Ändern Sie den Wert in eine Zahl größer 5 (in Minuten) und speichern Sie die Datei.
1. Navigieren Sie in Administration Console zur Seite Konfigurationsdateien importieren und exportieren .
1. Geben Sie den Pfad zur geänderten Datei &quot;config.xml&quot;ein oder klicken Sie auf Durchsuchen , um zu dieser Datei zu navigieren.
1. Klicken **Import** , um die geänderte Datei &quot;config.xml&quot;hochzuladen, und klicken Sie dann auf **OK**.
