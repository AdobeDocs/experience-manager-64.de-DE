---
title: Aktualisierung auf AEM 6.4 Forms
seo-title: Aktualisierung auf AEM 6.4 Forms
description: 'Sie können direkt von AEM 6.1 Forms, AEM 6.2 Forms und LiveCycle ES4 SP1 auf AEM 6.3 Forms aktualisieren. '
seo-description: 'Sie können direkt von AEM 6.1 Forms, AEM 6.2 Forms und LiveCycle ES4 SP1 auf AEM 6.3 Forms aktualisieren. '
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
role: Administrator
exl-id: e41eb0fa-ae88-44d5-9181-0d925b8b62c6
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1702'
ht-degree: 80%

---

# Aktualisierung auf AEM 6.4 Forms on JEE {#upgrade-to-aem-forms-jee}

Verwenden Sie einen der folgenden Aktualisierungspfade wie für Ihre Umgebung benötigt.

## AEM 6.2 Forms on JEE oder AEM 6.3 Forms on JEE > AEM 6.4 Forms on JEE {#aem-forms-jee-62-63-to-64}

Führen Sie folgendes Verfahren durch um von der vorhandenen AEM 6.2 Forms on JEE oder AEM 6.3 Forms on JEE auf AEM 6.4 Forms on JEE zu aktualisieren:

1. Laden Sie das Installationsprogramm für AEM 6.4 Forms on JEE von der [Adobe Licensing-Website (LWS)](https://licensing.adobe.com/) herunter. Sie benötigen einen gültigen Vertrag für Wartung und Support, um das Installationsprogramm herunterzuladen.
1. Informationen zu den Prüfungen, die durchgeführt werden müssen, um eine erfolgreiche Aktualisierung sicherzustellen, finden Sie unter [Checkliste für die Aktualisierung und Planung](https://www.adobe.com/go/learn_aemfroms_upgrade_checklist_63).
1. Siehe [Vorbereiten der Aktualisierung auf AEM Forms](https://www.adobe.com/go/learn_aemforms_prepareupgrade_63) , um zu erfahren, wie Sie die Aufgaben durchführen, die sicherstellen, dass die Aktualisierung ordnungsgemäß und mit minimalem Serverausfall ausgeführt wird.
1. Wählen Sie je nach vorhandener Umgebung und Anwendungsserver eines der folgenden Dokumente und befolgen Sie die Anweisungen.

   * [Upgrade von AEM 6.2 oder AEM 6.3 Forms auf AEM 6.4 Forms for JBoss ](assets/upgrade-jboss.pdf)
   * [Upgrade von AEM 6.2 oder AEM 6.3 Forms auf AEM 6.4 Forms for Weblogic](assets/upgrade-weblogic.pdf)
   * [Upgrade von AEM 6.2 oder AEM 6.3 Forms auf AEM 6.4 Forms for WebSphere](assets/upgrade-websphere.pdf)
   * [Upgrade von AEM 6.2 oder AEM 6.3 Forms auf AEM 6.4 Forms for JBoss Turnkey](assets/upgrade-turnkey.pdf)

## AEM 6.0 Forms on JEE > AEM 6.3 Forms on JEE {#aem-forms-jee-60-to-63}

Die direkte Aktualisierung von LiveCycle ES2, LiveCycle ES3, AEM 6.0 Forms, AEM 6.1 Forms auf AEM 6.4 Forms ist nicht verfügbar. Sie können eine Zwischenaktualisierung auf eine oder mehrere Versionen von LiveCycle oder AEM Forms durchführen und dann auf AEM 6.4 Forms aktualisieren. Eine Liste der Zwischenversionen und entsprechenden Aktualisierungsanweisungen finden Sie unter [Aktualisierungspfad wählen](upgrade.md).

## LiveCycle ES4 SP1 > AEM 6.4 Forms on JEE  {#livecycle-es4sp1-forms-jee}

Die Aktualisierung von LiveCycle ES4 SP1 auf AEM 6.4 Forms on JEE ist ein Out-of-Place Upgrade, da es die Migration von Assets und Daten von früheren Versionen auf die neuen Instanzen (die neuen Versionen) von unterstützten Anwendungsservern, Betriebssystemen und Datenbanken erfordert.

Im Folgenden finden Sie eine Übersicht über das Verfahren zum Aktualisieren eines vorhandenen LiveCycle ES4 SP1-Servers auf AEM 6.4 Forms. Detaillierte Anweisungen finden Sie in den am Ende des Verfahrens aufgeführten Dokumenten.

1. Vor der Aktualisierung:

   1. Laden Sie das Installationsprogramm für AEM 6.4 Forms on JEE von der [Adobe Licensing-Website (LWS)](https://licensing.adobe.com/) herunter. Sie benötigen einen gültigen Vertrag für Wartung und Support, um das Installationsprogramm herunterzuladen.
   1. Legen Sie den zu verwendenden Content Repository-Typ (CRX-Repository) fest. Nur wenige AEM Forms on JEE-Funktionen verwenden die CRX Repository-Persistenz zum Speichern von Inhalten und Assets. Installieren und konfigurieren Sie das Content Repository nur, wenn Sie solche AEM Forms on JEE-Funktionen verwenden möchten:

      * In LiveCycle ES4 SP1 verwenden die Funktionen Correspondence Management, Forms Portal, HTML Workspace, and Process Reporting Content Repository. Wenn Sie diese Funktionen nicht in LiveCycle ES4 verwendet haben und planen, diese Funktionen nicht in AEM Forms zu verwenden, ist kein Content Repository erforderlich.
      * In AEM Forms, Adaptive Forms, Correspondence Management, HTML5-Formularen (bekannt als Mobile Forms in LiveCycle ES4 SP1), Forms Portal, HTML Workspace, Process Reporting, formularzentrierten Workflows unter OSGi wird Content Repository verwendet. Wenn Sie planen, AEM Forms für diese Funktionen zu verwenden, ist Content Repository erforderlich.
      * Sie benötigen kein Content Repository für AEM Forms Document Security.

      Darüber hinaus unterscheidet sich der Repository-Typ von LiveCycle und AEM Forms. Weitere Informationen zu verfügbaren Repository-Typen und zugehörige Informationen finden Sie unter [Persistenztyp für eine AEM Forms-Installation wählen](/help/forms/using/choosing-persistence-type-for-aem-forms.md).

   1. Erstellen Sie eine Sicherung der LiveCycle ES4 SP1-Inhalte und -Daten:

      Erstellen Sie eine Sicherung der LiveCycle ES4 SP1-Datenbank, des globalen Datenspeichers (GDS) und des CRX-Repository (für Document Security nicht erforderlich). Wenn Sie auf MongoMK oder RDBMK-Persistenz aktualisieren, exportieren Sie LiveCycle ES4 SP1 Correspondence Management Assets in eine CMP-Datei und erstellen Sie Assets als AEM-Paket.

   1. Stellen Sie sicher, dass Ihre vorhandene Plattform (d. h. Anwendungsserver, Datenbank, Betriebssystem, Adobe Acrobat oder Hardware) für AEM 6.4 Forms on JEE unterstützt wird. Informationen zu unterstützter Hardware und Software finden Sie im Dokument [Unterstützte Plattformkombinationen](/help/forms/using/aem-forms-jee-supported-platforms.md).

      Wenn Sie eine neue Instanz der Datenbank erstellen, importieren Sie die in Schritt 3 gesicherten Daten in die Datenbank. Informationen zum Importieren von Daten in eine Datenbank finden Sie in der Dokumentation des entsprechenden Datenbankanbieters.

      >[!NOTE]
      >
      >Wenn Sie das RDBMK-Persistenzformat verwenden, verwenden Sie eine einzige Datenbank für die Repository-Persistenz und die Dokumentdienste, die auf AEM Forms on JEE ausgeführt werden.


1. Führen Sie die Aktualisierung durch:

   1. Installieren Sie AEM 6.4 Forms on JEE auf einem neuen Server, indem Sie das Installationsprogramm ausführen. Das Installationsprogramm legt alle erforderlichen Dateien in derselben Installationsordnerstruktur auf dem Computer ab.
   1. Nach Abschluss der Installation führen Sie den **Configuration Manager** aus, um verschiedene AEM Forms-Module zu konfigurieren und die entsprechenden Konfigurationen festzulegen. Zusammen mit den Konfigurationseinstellungen können Sie den Pfad des Global Data Storage (GDS) und des CRX-Repository angeben.

      >[!NOTE]
      >
      >Wählen Sie im Bildschirm &quot;Auswahl der Aktualisierungsaufgaben&quot;die Option **[!UICONTROL Von Adobe Experience Manager Forms 6.2.0]** aktualisieren . Mit der Option **[!UICONTROL Upgrade von Adobe Experience Manager Forms 6.2.0]** kann der Konfigurationsmanager von LiveCycle ES4 SP1 auf AEM 6.4 Forms aktualisieren.

   1. (Nicht erforderlich für AEM Forms-Dokumentsicherheitsmodul) Importieren Sie Inhalte in das Content Repository (CRX-Repository) in den AEM 6.4 Forms-Server.

      >[!NOTE]
      >
      >* Nachdem das CRX-Repository aktualisiert wurde und der Inhalt migriert wurde, ändern Sie das Kennwort des Administratorkontos. Ausführliche Anweisungen finden Sie unter [Ändern des Kennworts für einen vorhandenen Benutzer](/help/sites-administering/granite-user-group-admin.md).


1. Führen Sie die Aufgaben nach der Bereitstellung aus, um Anmeldeinformationen zu überprüfen, Document Services, Correspondence Management, Document Security und mehr je nach Anwendungsfall zu konfigurieren.
1. Stellen Sie sicher, dass der Server erfolgreich aktualisiert wurde:

   Führen Sie einige Routinevorgänge auf dem aktualisierten AEM Forms-Server aus, um sicherzustellen, dass der Server erfolgreich aktualisiert wurde. Sie können einige migrierte Formulare ausfüllen und absenden oder Dokumente schützen, um eine erfolgreiche Aktualisierung sicherzustellen.

   >[!NOTE]
   >
   >In AEM 6.4 Forms hat sich die Struktur des crx-Repository geändert. Verwenden Sie nach dem Upgrade auf AEM 6.4 Forms die geänderten Pfade für die Anpassung, die Sie neu erstellen. Sie finden die vollständige Liste der geänderten Pfade unter [Forms Repository-Restrukturierung in AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**Wählen Sie je nach vorhandener Umgebung und Anwendungsserver eines der folgenden Dokumente und befolgen Sie die detaillierten Anweisungen:**

* [Aktualisieren von LiveCycle ES4 SP1 auf AEM 6.4 Forms for JBoss](assets/upgrade-jboss-livecycle.pdf)
* [Upgrade von LiveCycle ES4 SP1 auf AEM 6.4 Forms for WebLogic](assets/upgrade-weblogic-livecycle.pdf)
* [Upgrade von LiveCycle ES4 SP1 auf AEM 6.4 Forms for WebSphere](assets/upgrade-websphere-livecycle.pdf)
* [Aktualisieren von LiveCycle ES4 SP1 auf AEM 6.4 Forms mithilfe von JBoss Turnkey](assets/upgrade-turnkey-livecycle.pdf)

<!--Theses sections used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

## LiveCycle ES3 > AEM 6.4 Forms on JEE {#livecycle-es3-forms-jee}

Die Aktualisierung von LiveCycle ES3 auf AEM 6.4 Forms on JEE ist ein Out-of-Place Upgrade, da es die Migration von Assets und Daten von früheren Versionen auf die neuen Instanzen (die neuen Versionen) von unterstützten Anwendungsservern, Betriebssystemen und Datenbanken erfordert.

Im Folgenden finden Sie eine Übersicht über das Verfahren zum Aktualisieren eines vorhandenen LiveCycle ES3 -Servers auf AEM 6.4 Forms. Detaillierte Anweisungen finden Sie in den am Ende des Verfahrens aufgeführten Dokumenten.

1. Vor der Aktualisierung:

   1. Laden Sie das Installationsprogramm für AEM 6.4 Forms on JEE von der [Adobe Licensing-Website (LWS)](https://licensing.adobe.com/) herunter. Sie benötigen einen gültigen Vertrag für Wartung und Support, um das Installationsprogramm herunterzuladen.
   1. Legen Sie den zu verwendenden Content Repository-Typ (CRX-Repository) fest. Nur wenige AEM Forms on JEE-Funktionen verwenden die CRX Repository-Persistenz zum Speichern von Inhalten und Assets. Installieren und konfigurieren Sie das Content Repository nur, wenn Sie solche AEM Forms on JEE-Funktionen verwenden möchten:

      * In AEM Forms, adaptiven Formularen, Correspondence Management, HTML5-Formularen, Forms Portal, HTML Workspace, Prozessberichterstellung, formularbasierten Workflows unter OSGi, verwenden Sie Content Repository. Wenn Sie planen, AEM Forms für diese Funktionen zu verwenden, ist Content Repository erforderlich.
      * Sie benötigen kein Content Repository für AEM Forms Document Security.

      Darüber hinaus unterscheidet sich der Repository-Typ von LiveCycle und AEM Forms. Weitere Informationen zu verfügbaren Repository-Typen und zugehörige Informationen finden Sie unter [Persistenztyp für eine AEM Forms-Installation wählen](/help/forms/using/choosing-persistence-type-for-aem-forms.md).

   1. Erstellen Sie eine Sicherung der LiveCycle ES3-Datenbank, des globalen Datenspeichers (GDS) und des Inhalts-Repositorys (nicht für Document Security erforderlich). Wenn Sie auf MongoMK oder RDBMK-Persistenz aktualisieren, exportieren Sie LiveCycle ES3 Correspondence Management Assets in eine CMP-Datei und erstellen Sie Assets als AEM-Paket.
   1. Stellen Sie sicher, dass Ihre vorhandene Plattform (d. h. Anwendungsserver, Datenbank, Betriebssystem, Adobe Acrobat oder Hardware) für AEM 6.4 Forms on JEE unterstützt wird. Informationen zu unterstützter Hardware und Software finden Sie im Dokument [Unterstützte Plattformkombinationen](/help/forms/using/aem-forms-jee-supported-platforms.md).

      Wenn Sie eine neue Instanz der Datenbank erstellen, importieren Sie die in Schritt 3 gesicherten Daten in die Datenbank. Informationen zum Importieren von Daten in eine Datenbank finden Sie in der Dokumentation des entsprechenden Datenbankanbieters.

      >[!NOTE]
      >
      >Wenn Sie das RDBMK-Persistenzformat verwenden, verwenden Sie eine einzige Datenbank für die Repository-Persistenz und die Dokumentdienste, die auf AEM Forms on JEE ausgeführt werden.


1. Führen Sie die Aktualisierung durch:

   1. Installieren Sie AEM 6.4 Forms on JEE auf einem neuen Server, indem Sie das Installationsprogramm ausführen. Das Installationsprogramm legt alle erforderlichen Dateien in derselben Installationsordnerstruktur auf dem Computer ab.
   1. Nach Abschluss der Installation führen Sie den **Configuration Manager** aus, um verschiedene AEM Forms-Module zu konfigurieren und die entsprechenden Konfigurationen festzulegen. Zusammen mit den Konfigurationseinstellungen können Sie den Pfad des Global Data Storage (GDS) und des CRX-Repository angeben.

      >[!NOTE]
      >
      >Wählen Sie im Bildschirm &quot;Auswahl der Aktualisierungsaufgaben&quot;die Option **[!UICONTROL Von Adobe Experience Manager Forms 6.2.0]** aktualisieren . Mit der Option **[!UICONTROL Upgrade von Adobe Experience Manager Forms 6.2.0]** kann der Konfigurationsmanager von LiveCycle ES3 auf AEM 6.4 Forms aktualisieren.

   1. (Für das AEM Forms Document Security-Modul nicht erforderlich) Aktualisieren und importieren Sie das CRX-Repository auf den AEM 6.4 Forms-Server.

      >[!NOTE]
      >
      >Nachdem das CRX-Repository aktualisiert wurde und der Inhalt migriert wurde, ändern Sie das Kennwort des Administratorkontos. Ausführliche Anweisungen finden Sie unter [Ändern des Kennworts für einen vorhandenen Benutzer](/help/sites-administering/granite-user-group-admin.md).
1. Führen Sie die Aufgaben nach der Bereitstellung aus, um Anmeldeinformationen zu überprüfen, Document Services, Correspondence Management, Document Security und mehr je nach Anwendungsfall zu konfigurieren.
1. Stellen Sie sicher, dass der Server erfolgreich aktualisiert wurde:

   Führen Sie einige Routinevorgänge auf dem aktualisierten AEM Forms-Server aus, um sicherzustellen, dass der Server erfolgreich aktualisiert wurde. Sie können einige migrierte Formulare ausfüllen und absenden oder Dokumente schützen, um eine erfolgreiche Aktualisierung sicherzustellen.

   >[!NOTE]
   >
   >In AEM 6.4 Forms hat sich die Struktur des crx-Repository geändert. Verwenden Sie nach dem Upgrade auf AEM 6.4 Forms die geänderten Pfade für die Anpassung, die Sie neu erstellen. Sie finden die vollständige Liste der geänderten Pfade unter [Forms Repository-Restrukturierung in AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**Wählen Sie je nach vorhandener Umgebung und Anwendungsserver eines der folgenden Dokumente und befolgen Sie die detaillierten Anweisungen:**

* [Aktualisieren von LiveCycle ES3 auf AEM 6.4 Forms for JBoss](assets/upgrade-jboss-livecycle-es3.pdf)
* [Upgrade von LiveCycle ES3 auf AEM 6.4 Forms for WebLogic](assets/upgrade-weblogic-livecycle-es3.pdf)
* [Upgrade von LiveCycle ES3 auf AEM 6.4 Forms for WebSphere](assets/upgrade-websphere-livecycle-es3.pdf)
* [Aktualisieren von LiveCycle ES3 auf AEM 6.4 Forms mithilfe von JBoss Turnkey](assets/upgrade-turnkey-livecycle-es3.pdf)
