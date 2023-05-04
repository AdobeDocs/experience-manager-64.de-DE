---
title: Aktualisierung auf AEM 6.4 Forms
seo-title: Upgrade to AEM 6.4 Forms
description: Sie können direkt von AEM 6.1 Forms, AEM 6.2 Forms und LiveCycle ES4 SP1 auf AEM 6.3 Forms aktualisieren.
seo-description: You can perform a direct upgrade from AEM 6.1 Forms, AEM 6.2 Forms, and LiveCycle ES4 SP1 to AEM 6.3 Forms.
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
role: Admin
exl-id: e41eb0fa-ae88-44d5-9181-0d925b8b62c6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1716'
ht-degree: 17%

---

# Aktualisierung auf AEM 6.4 Forms auf JEE {#upgrade-to-aem-forms-jee}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Verwenden Sie je nach Umgebung einen der folgenden Aktualisierungspfade.

## AEM 6.2 Forms on JEE oder AEM 6.3 Forms on JEE > AEM 6.4 Forms on JEE {#aem-forms-jee-62-63-to-64}

Führen Sie folgendes Verfahren durch um von der vorhandenen AEM 6.2 Forms on JEE oder AEM 6.3 Forms on JEE auf AEM 6.4 Forms on JEE zu aktualisieren:

1. Laden Sie das Installationsprogramm für AEM 6.4 Forms on JEE von der [Adobe Licensing-Website (LWS)](https://licensing.adobe.com/) herunter. Sie benötigen einen gültigen Vertrag für Wartung und Support, um das Installationsprogramm herunterzuladen.
1. Lesen Sie das Dokument [Checkliste für die Aktualisierung und Planung](https://www.adobe.com/go/learn_aemfroms_upgrade_checklist_63), um sich über die Überprüfungen zu informieren, die für eine erfolgreiche Aktualisierung ausgeführt werden müssen.
1. Lesen Sie das Dokument [Vorbereiten auf die Aktualisierung auf AEM Forms](https://www.adobe.com/go/learn_aemforms_prepareupgrade_63_de), um zu erfahren, wie Sie die Aufgaben durchführen, die sicherstellen, dass die Aktualisierung richtig und nur mit minimalem Serverausfall verläuft.
1. Wählen Sie je nach vorhandener Umgebung und Anwendungsserver eines der folgenden Dokumente und befolgen Sie die Anweisungen.

   * [Upgrade von AEM 6.2 oder AEM 6.3 Forms auf AEM 6.4 Forms for JBoss ](assets/upgrade-jboss.pdf)
   * [Upgrade von AEM 6.2 oder AEM 6.3 Forms auf AEM 6.4 Forms for WebLogic](assets/upgrade-weblogic.pdf)
   * [Upgrade von AEM 6.2 oder AEM 6.3 Forms auf AEM 6.4 Forms for WebSphere](assets/upgrade-websphere.pdf)
   * [Upgrade von AEM 6.2 oder AEM 6.3 Forms auf AEM 6.4 Forms for JBoss Turnkey](assets/upgrade-turnkey.pdf)

## AEM 6.0 Forms on JEE > AEM 6.3 Forms on JEE {#aem-forms-jee-60-to-63}

Die direkte Aktualisierung von LiveCycle ES2, Live Cycle ES3, AEM 6.0 6.1 Forms oder AEM Forms auf AEM 6.4 Forms ist nicht verfügbar. Sie können eine Zwischenaktualisierung auf eine oder mehrere Versionen von LiveCycle oder AEM Forms durchführen und dann auf AEM 6.4 Forms aktualisieren. Eine Liste der Zwischenversionen und entsprechenden Aktualisierungsanweisungen finden Sie unter [Auswählen eines Aktualisierungspfads](upgrade.md).

## LiveCycle ES4 SP1 > AEM 6.4 Forms on JEE {#livecycle-es4sp1-forms-jee}

Die Aktualisierung von LiveCycle ES4 SP1 auf AEM 6.4 Forms on JEE ist eine nicht ersetzende Aktualisierung, da Assets und Daten aus früheren Versionen auf die neuen Instanzen (neuen Versionen) der unterstützten Anwendungsserver, Betriebssysteme und Datenbanken migriert werden müssen.

Im Folgenden finden Sie einen Überblick über das Verfahren zum Aktualisieren eines bestehenden LiveCycle ES4 SP1-Servers auf AEM 6.4 Forms. Detaillierte Anweisungen finden Sie in den am Ende des Verfahrens aufgelisteten Dokumenten.

1. Vor der Aktualisierung:

   1. Laden Sie das Installationsprogramm für AEM 6.4 Forms on JEE von der [Adobe Licensing-Website (LWS)](https://licensing.adobe.com/) herunter. Sie benötigen einen gültigen Vertrag für Wartung und Support, um das Installationsprogramm herunterzuladen.
   1. Wählen Sie den zu verwendenden Content Repository-Typ (CRX-Repository). Nur wenige AEM Forms on JEE-Funktionen verwenden die Persistenz des Content Repository zum Speichern von Inhalten und Assets. Installieren und konfigurieren Sie das Content Repository nur, wenn Sie solche AEM Forms on JEE-Funktionen verwenden möchten:

      * In LiveCycle ES4 SP1 verwenden die Funktionen Correspondence Management, Forms Portal, HTML Workspace und Process Reporting das Content Repository. Wenn Sie diese Funktionen nicht in LiveCycle ES4 verwendet haben und planen, diese Funktionen nicht in AEM Forms zu verwenden, ist kein Content Repository erforderlich.
      * In AEM Forms, Adaptive Forms, Correspondence Management, HTML5 Forms (in LiveCycle ES4 SP1 als Mobile Forms bezeichnet), Forms Portal, HTML Workspace, Process Reporting, Forms zentralen Workflows in OSGi, können Sie Content Repository verwenden. Wenn Sie planen, AEM Forms für diese Funktionen zu verwenden, ist Content Repository erforderlich.
      * Sie benötigen kein Content Repository für AEM Forms Document Security.

      Außerdem unterscheiden sich die Repository-Typen von LiveCycle und AEM Forms. Verfügbare Repository-Typen und zugehörige Informationen finden Sie unter [Persistenztyp für eine AEM Forms-Installation auswählen](/help/forms/using/choosing-persistence-type-for-aem-forms.md).

   1. Erstellen Sie eine Sicherung der Inhalte und Daten von LiveCycle ES4 SP1:

      Erstellen Sie eine Sicherung der LiveCycle ES4 SP1-Datenbank, des globalen Datenspeichers (GDS) und des CRX-Repository (nicht für Document Security erforderlich). Wenn Sie auf MongoMK oder RDBMK-Persistenz aktualisieren, exportieren Sie LiveCycle ES4 SP1 Correspondence Management-Assets in eine .cmp-Datei und forms-Assets als AEM-Paket.

   1. Stellen Sie sicher, dass Ihre vorhandene Plattform (d. h. Anwendungsserver, Datenbank, Betriebssystem, Adobe Acrobat, Anwendungen von Drittanbietern und Hardware) für AEM 6.4 Forms on JEE unterstützt wird. Informationen zu unterstützter Hardware und Software finden Sie im Abschnitt [Unterstützte Plattformkombinationen](/help/forms/using/aem-forms-jee-supported-platforms.md) Dokument.

      Wenn Sie eine neue Instanz der Datenbank erstellen, importieren Sie die in Schritt 3 gesicherten Daten in die Datenbank. Informationen zum Importieren von Daten in eine Datenbank finden Sie in der Dokumentation des entsprechenden Datenbankanbieters.

      >[!NOTE]
      >
      >Wenn Sie das RDBMK-Persistenzformat verwenden, verwenden Sie eine einzige Datenbank sowohl für die Repository-Persistenz als auch für Document Services, die auf AEM Forms on JEE ausgeführt werden.


1. Führen Sie das Upgrade durch:

   1. Installieren Sie AEM 6.4 Forms on JEE auf einem neuen Server, indem Sie das Installationsprogramm ausführen. Das Installationsprogramm legt alle erforderlichen Dateien auf dem Computer in einer Installationsordnerstruktur ab.
   1. Führen Sie nach Abschluss der Installation den **Configuration Manager** um verschiedene AEM Forms-Module zu konfigurieren und entsprechende Konfigurationen festzulegen. Zusammen mit den Konfigurationseinstellungen können Sie damit den Pfad des globalen Datenspeichers (GDS) und des CRX-Repositorys angeben.

      >[!NOTE]
      >
      >Wählen Sie im Bildschirm &quot;Auswahl der Aktualisierungsaufgaben&quot;die **[!UICONTROL Upgrade von Adobe Experience Manager Forms 6.2.0]** -Option. Die **[!UICONTROL Upgrade von Adobe Experience Manager Forms 6.2.0]** ermöglicht dem Konfigurationsmanager ein Upgrade von LiveCycle ES4 SP1 auf AEM 6.4 Forms.

   1. (Nicht erforderlich für AEM Forms Document Security-Modul) Importieren Sie Inhalte in das Content Repository (CRX-Repository) in AEM 6.4 Forms-Server.

      >[!NOTE]
      >
      >* Nachdem das CRX-Repository aktualisiert und der Inhalt migriert wurde, ändern Sie das Kennwort des Administratorkontos. Detaillierte Anweisungen finden Sie unter [Ändern des Kennworts für einen vorhandenen Benutzer](/help/sites-administering/granite-user-group-admin.md).


1. Führen Sie die Aufgaben nach der Bereitstellung aus, um die Anmeldedaten zu überprüfen, Document Services, Correspondence Management, Document Security und mehr zu konfigurieren, je nach Anwendungsfall.
1. Stellen Sie sicher, dass der Server erfolgreich aktualisiert wurde:

   Führen Sie einige Routinevorgänge auf dem aktualisierten AEM Forms-Server durch, um sicherzustellen, dass der Server erfolgreich aktualisiert wurde. Sie können einige migrierte Formulare ausfüllen und senden oder Dokumente schützen, um eine erfolgreiche Aktualisierung sicherzustellen.

   >[!NOTE]
   >
   >In AEM 6.4 Forms hat sich die Struktur des crx-Repository geändert. Verwenden Sie nach dem Upgrade auf AEM 6.4 Forms die geänderten Pfade zur Anpassung, die Sie neu erstellen. Eine vollständige Liste der geänderten Pfade finden Sie unter [Forms-Repository-Neustrukturierung in AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**Wählen Sie je nach vorhandener Umgebung und Anwendungsserver eines der folgenden Dokumente aus und befolgen Sie die detaillierten Anweisungen:**

* [Upgrade von LiveCycle ES4 SP1 auf AEM 6.4 Forms for JBoss](assets/upgrade-jboss-livecycle.pdf)
* [Upgrade von LiveCycle ES4 SP1 auf AEM 6.4 Forms for WebLogic](assets/upgrade-weblogic-livecycle.pdf)
* [Upgrade von LiveCycle ES4 SP1 auf AEM 6.4 Forms for WebSphere](assets/upgrade-websphere-livecycle.pdf)
* [Aktualisieren von LiveCycle ES4 SP1 auf AEM 6.4 Forms mithilfe von JBoss Turnkey](assets/upgrade-turnkey-livecycle.pdf)

<!--Theses sections used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

## LiveCycle ES3 > AEM 6.4 Forms on JEE {#livecycle-es3-forms-jee}

Die Aktualisierung von LiveCycle ES3 auf AEM 6.4 Forms on JEE ist eine nicht ersetzende Aktualisierung, da Assets und Daten aus früheren Versionen auf die neuen Instanzen (neuen Versionen) der unterstützten Anwendungsserver, Betriebssysteme und Datenbanken migriert werden müssen.

Im Folgenden finden Sie einen Überblick über das Verfahren zum Aktualisieren eines bestehenden LiveCycle ES3-Servers auf AEM 6.4 Forms. Detaillierte Anweisungen finden Sie in den am Ende des Verfahrens aufgelisteten Dokumenten.

1. Vor der Aktualisierung:

   1. Laden Sie das Installationsprogramm für AEM 6.4 Forms on JEE von der [Adobe Licensing-Website (LWS)](https://licensing.adobe.com/) herunter. Sie benötigen einen gültigen Vertrag für Wartung und Support, um das Installationsprogramm herunterzuladen.
   1. Wählen Sie den zu verwendenden Content Repository-Typ (CRX-Repository). Nur wenige AEM Forms on JEE-Funktionen verwenden die Persistenz des Content Repository zum Speichern von Inhalten und Assets. Installieren und konfigurieren Sie das Content Repository nur, wenn Sie solche AEM Forms on JEE-Funktionen verwenden möchten:

      * In AEM Forms, Adaptive Forms, Correspondence Management, HTML5 Forms, Forms Portal, HTML Workspace, Process Reporting und Forms-orientierten Workflows für OSGi-Funktionen verwenden Sie Content Repository. Wenn Sie planen, AEM Forms für diese Funktionen zu verwenden, ist Content Repository erforderlich.
      * Sie benötigen kein Content Repository für AEM Forms Document Security.

      Außerdem unterscheiden sich die Repository-Typen von LiveCycle und AEM Forms. Verfügbare Repository-Typen und zugehörige Informationen finden Sie unter [Persistenztyp für eine AEM Forms-Installation auswählen](/help/forms/using/choosing-persistence-type-for-aem-forms.md).

   1. Erstellen Sie eine Sicherung der LiveCycle ES3-Datenbank, des globalen Datenspeichers (GDS) und des Inhalts-Repositorys (nicht für Document Security erforderlich). Wenn Sie auf MongoMK- oder RDBMK-Persistenz aktualisieren, exportieren Sie LiveCycle ES3-Correspondence Management-Assets als Archiv.
   1. Stellen Sie sicher, dass Ihre vorhandene Plattform (d. h. Anwendungsserver, Datenbank, Betriebssystem, Adobe Acrobat, Anwendungen von Drittanbietern und Hardware) für AEM 6.4 Forms on JEE unterstützt wird. Informationen zu unterstützter Hardware und Software finden Sie im Abschnitt [Unterstützte Plattformkombinationen](/help/forms/using/aem-forms-jee-supported-platforms.md) Dokument.

      Wenn Sie eine neue Instanz der Datenbank erstellen, importieren Sie die in Schritt 3 gesicherten Daten in die Datenbank. Informationen zum Importieren von Daten in eine Datenbank finden Sie in der Dokumentation des entsprechenden Datenbankanbieters.

      >[!NOTE]
      >
      >Wenn Sie das RDBMK-Persistenzformat verwenden, verwenden Sie eine einzige Datenbank sowohl für die Repository-Persistenz als auch für Document Services, die auf AEM Forms on JEE ausgeführt werden.


1. Führen Sie das Upgrade durch:

   1. Installieren Sie AEM 6.4 Forms on JEE auf einem neuen Server, indem Sie das Installationsprogramm ausführen. Das Installationsprogramm legt alle erforderlichen Dateien auf dem Computer in einer Installationsordnerstruktur ab.
   1. Führen Sie nach Abschluss der Installation den **Configuration Manager** um verschiedene AEM Forms-Module zu konfigurieren und entsprechende Konfigurationen festzulegen. Zusammen mit den Konfigurationseinstellungen können Sie damit den Pfad des globalen Datenspeichers (GDS) und des CRX-Repositorys angeben.

      >[!NOTE]
      >
      >Wählen Sie im Bildschirm &quot;Auswahl der Aktualisierungsaufgaben&quot;die **[!UICONTROL Upgrade von Adobe Experience Manager Forms 6.2.0]** -Option. Die **[!UICONTROL Upgrade von Adobe Experience Manager Forms 6.2.0]** ermöglicht es dem Konfigurationsmanager, von LiveCycle ES3 auf AEM 6.4 Forms zu aktualisieren.

   1. (Nicht für das AEM Forms Document Security-Modul erforderlich) Aktualisieren und importieren Sie das CRX-Repository auf AEM 6.4 Forms-Server.

      >[!NOTE]
      >
      >Nachdem das CRX-Repository aktualisiert und der Inhalt migriert wurde, ändern Sie das Kennwort des Administratorkontos. Detaillierte Anweisungen finden Sie unter [Ändern des Kennworts für einen vorhandenen Benutzer](/help/sites-administering/granite-user-group-admin.md).
1. Führen Sie die Aufgaben nach der Bereitstellung aus, um die Anmeldedaten zu überprüfen, Document Services, Correspondence Management, Document Security und mehr zu konfigurieren, je nach Anwendungsfall.
1. Stellen Sie sicher, dass der Server erfolgreich aktualisiert wurde:

   Führen Sie einige Routinevorgänge auf dem aktualisierten AEM Forms-Server durch, um sicherzustellen, dass der Server erfolgreich aktualisiert wurde. Sie können einige migrierte Formulare ausfüllen und senden oder Dokumente schützen, um eine erfolgreiche Aktualisierung sicherzustellen.

   >[!NOTE]
   >
   >In AEM 6.4 Forms hat sich die Struktur des crx-Repository geändert. Verwenden Sie nach dem Upgrade auf AEM 6.4 Forms die geänderten Pfade zur Anpassung, die Sie neu erstellen. Eine vollständige Liste der geänderten Pfade finden Sie unter [Forms-Repository-Neustrukturierung in AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**Wählen Sie je nach vorhandener Umgebung und Anwendungsserver eines der folgenden Dokumente aus und befolgen Sie die detaillierten Anweisungen:**

* [Upgrade von LiveCycle ES3 auf AEM 6.4 Forms für JBoss](assets/upgrade-jboss-livecycle-es3.pdf)
* [Upgrade von LiveCycle ES3 auf AEM 6.4 Forms for WebLogic](assets/upgrade-weblogic-livecycle-es3.pdf)
* [Upgrade von LiveCycle ES3 auf AEM 6.4 Forms for WebSphere](assets/upgrade-websphere-livecycle-es3.pdf)
* [Aktualisieren von LiveCycle ES3 auf AEM 6.4 Forms mithilfe von JBoss Turnkey](assets/upgrade-turnkey-livecycle-es3.pdf)
