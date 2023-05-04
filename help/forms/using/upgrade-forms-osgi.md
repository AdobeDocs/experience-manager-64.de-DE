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
exl-id: 183ed9c6-6a9a-4932-8405-5ae2c6fac1ec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 53%

---

# Aktualisierung auf AEM 6.4 Forms auf OSGi {#upgrade-to-aem-forms-osgi}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Verwenden Sie je nach Umgebung einen der folgenden Aktualisierungspfade.

## AEM 6.2 Forms oder AEM 6.3 Forms > AEM 6.4 Forms {#upgrade-aem-forms-62-63-to-64}

Sie können direkt von AEM 6.2 Forms oder AEM 6.3 Forms auf AEM 6.4 Forms aktualisieren. Gehen Sie folgendermaßen vor:

1. Aktualisieren Sie die bestehende AEM-Instanz auf AEM 6.4. Dies umfasst die folgenden Schritte:

   1. Installieren Sie das aktuelle Service Pack und die Patches für AEM 6.2 Forms bzw. AEM 6.3 Forms. Weitere Informationen finden Sie unter:

      * [AEM 6.2 – Versionshinweise](https://helpx.adobe.com/de/experience-manager/6-2/release-notes.html)
      * [AEM 6.3 – Versionshinweise](https://helpx.adobe.com/de/experience-manager/6-3/release-notes.html)
      * [AEM Sustenanz-Hub](https://helpx.adobe.com/de/experience-manager/aem-releases-updates.html)
   1. Bereiten Sie die Quellinstanz für die Aktualisierung vor. Ausführliche Anweisungen finden Sie unter [Aktualisieren auf AEM 6.4](/help/sites-deploying/upgrade.md#preparing%20the%20source%20instance).
   1. Laden Sie [AEM 6.4 QuickStart](/help/sites-deploying/deploy.md#getting%20the%20software) herunter.
   1. **(Nur Unix/Linux-basierte Installationen)** Wenn Sie UNIX oder Linux als Betriebssystem verwenden, öffnen Sie das Terminalfenster, um zu dem Ordner mit „crx-quickstart“ zu navigieren, und führen Sie den folgenden Befehl aus:

      `chmod -R 755 ../crx-quickstart`

   1. Aktualisieren Sie Ihre AEM-Instanz auf AEM 6.3. Anweisungen in Einzelschritten finden Sie unter [Aktualisieren auf AEM 6.4](/help/sites-deploying/upgrade.md).

      Bevor Sie mit den nächsten Schritten fortfahren, warten Sie, bis die Nachrichten ServiceEvent REGISTERED und ServiceEvent UNREGISTERED nicht mehr in der Datei &lt;crx-repository>/error.log angezeigt werden.

      >[!NOTE]
      >
      >Nachdem der Server ausgeführt wurde, bleiben einige AEM Forms-Bundles im Installationsstatus. Die Anzahl der Bundles kann für jede Installation variieren. Sie können den Status dieser Bundles sicher ignorieren. Die Bundles sind unter `https://[server]:[port]/system/console/` aufgeführt. 


1. Installieren des AEM Forms-Add-on-Pakets. Die Schritte sind unten aufgeführt:

   1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
   1. Tippen Sie im Kopfzeilenmenü auf **[!UICONTROL Adobe Experience Manager]**.
   1. Im **[!UICONTROL Filter]** Abschnitt:
      1. Auswählen **[!UICONTROL Forms]** von **[!UICONTROL Lösung]** Dropdown-Liste.
      1. Wählen Sie die Version aus und geben Sie für das Paket ein. Sie können auch die Option **[!UICONTROL Downloads durchsuchen]** verwenden, um die Ergebnisse zu filtern.
   1. Tippen Sie auf den für Ihr Betriebssystem zutreffenden Paketnamen, wählen Sie **[!UICONTROL EULA-Bedingungen akzeptieren]** und tippen Sie auf **[!UICONTROL Herunterladen]**.
   1. Öffnen Sie [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
   1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

      Sie können das Paket auch über den direkten Link herunterladen, der im Artikel [AEM Forms-Versionen](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html) aufgeführt ist.

      >[!NOTE]
      >
      >Sobald das Paket installiert ist, werden Sie aufgefordert, die AEM-Instanz neu zu starten. **Beenden Sie den Server nicht sofort.** Warten Sie vor dem Anhalten des AEM Forms-Servers, bis die Meldungen ServiceEvent REGISTERED und ServiceEvent UNREGISTERED nicht mehr in der &lt;crx-repository>/error.log und das Protokoll ist stabil. Beachten Sie außerdem, dass einige Pakete im installierten Status verbleiben können. Sie können den Status dieser Pakete ignorieren.

   1. Beenden Sie die AEM-Instanz und löschen Sie die folgenden Dateien:

      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcmail-jdk15-1.35`
      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcprov-jdk15-1.35`
   1. Starten Sie die AEM-Instanz.


1. Führen Sie nach der Installation Aktivitäten durch.

   * **Migrationsdienstprogramm ausführen**

      Das Migrationsdienstprogramm macht die adaptiven Formulare und Korrespondenzmanagement-Assets aus früheren Versionen kompatibel mit AEM 6.4 Forms. Sie können das Dienstprogramm von der AEM Software Distribution herunterladen. Informationen in Einzelschritten zur Konfiguration und Verwendung des Migrationsdienstprogramms finden Sie in der Dokumentation zum [Migrationsdienstprogramm](/help/forms/using/migration-utility.md).

      Wenn Sie [Beispiel zur Integrierung der Komponente für Entwurf und Übermittlung](integrate-draft-submission-database.md) mit der Datenbank verwenden und von einer früheren Version aktualisieren, führen Sie nach der Aktualisierung die folgenden SQL-Abfragen aus:

      ```
      UPDATE metadata m, additionalmetadatatable am
      SET m.dataType = am.value
      WHERE m.id = am.id
      AND am.key = 'dataType'
      ```

      ```
      DELETE from additionalmetadatatable
      WHERE `key` = 'dataType'
      ```

   * **(Nur bei Aktualisierung von AEM 6.2 Forms oder früheren Versionen) Konfigurieren Sie Acrobat Sign neu**

      Wenn Sie Acrobat Sign in der vorherigen Version von AEM Forms konfiguriert haben, konfigurieren Sie Acrobat Sign von AEM Cloud Services neu. Weitere Informationen finden Sie unter [Integrieren von Acrobat Sign mit AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

   * **(Nur wenn Sie von AEM 6.2 Forms oder früheren Versionen aktualisieren) Konfigurieren Sie Analysen und Berichte neu**

      In AEM 6.4 Forms sind keine Traffic-Variablen für Quelle und Erfolgsereignis für Impressionen verfügbar. Wenn Sie von AEM 6.2 Forms oder vorherigen Versionen aktualisieren, sendet AEM Forms daher keine Daten mehr an den Adobe Analytics-Server und es stehen keine Analyseberichte für adaptive Formulare zur Verfügung. Darüber hinaus führt Forms AEM 6.4 Traffic-Variablen für die Version der Formularanalyse und das Erfolgsereignis für die für ein Feld verbrachte Zeit ein. Konfigurieren Sie daher die Analyse und Berichte für Ihre AEM Forms-Umgebung neu. Ausführliche Anweisungen finden Sie unter [Konfigurieren von Analysen und Berichten](/help/forms/using/configure-analytics-forms-documents.md).

1. Vergewissern Sie sich, dass der Server erfolgreich aktualisiert und alle Daten migriert wurden und dass der Server einwandfrei funktioniert.

   * **Überprüfen Sie den Status der Pakete:** Stellen Sie sicher, dass alle Pakete sich im aktiven Status befinden.
   * **Überprüfen Sie die Replikation und Rückwärtsreplikation:** Veröffentlichen, Ausfüllen und Senden einiger migrierter Formulare. Überprüfen Sie auch die gesendeten Daten.
   * **Überprüfen Sie den Zugriff auf die Administrator- und Entwicklerbenutzeroberflächen:** Melden Sie sich von einem Administratorkonto aus bei AEM Instanz an und stellen Sie sicher, dass Sie Zugriff auf die folgenden URLs haben:

      * `https://[server]:[port]/crx/packmgr`
      * `https://[server]:[port]/crx/de`
      * `https://[server]:[port]/aem/forms.html/content/dam/formsanddocuments`

   >[!NOTE]
   In AEM 6.4 Forms hat sich die Struktur des crx-Repository geändert. Verwenden Sie nach dem Upgrade auf AEM 6.4 Forms die geänderten Pfade zur Anpassung, die Sie neu erstellen. Eine vollständige Liste der geänderten Pfade finden Sie unter [Forms-Repository-Neustrukturierung in AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

## AEM 6.0 Forms und AEM 6.1 Forms > AEM 6.4 Forms {#upgrade-aem-forms-60-61-to-64}

Direkter Aktualisierungspfad von **AEM 6.0 Forms** und **AEM 6.1 Forms** bis AEM 6.4 Forms ist nicht verfügbar. Zwischenergebnis [Upgrade auf AEM 6.2 Forms](/help/forms/using/upgrade.md) oder [Upgrade auf AEM 6.3 Forms](/help/forms/using/upgrade.md) und dann von AEM 6.2 Forms oder AEM 6.3 Forms auf AEM 6.4 Forms aktualisieren.
