---
title: Konfigurieren von AEM Forms zum Senden von Formulardaten an einen AEM Forms on JEE-Prozess
seo-title: Configuring AEM Forms to submit form data to an AEM Forms on JEE process
description: Mit AEM Forms können Sie adaptive Formulare in AEM Forms on JEE-Prozesse integrieren, um Formulardaten zu verarbeiten.
seo-description: AEM Forms allows you to integrate adaptive forms with AEM Forms on JEE processes for processing form data.
uuid: ee7ea442-d604-4520-9af5-ad40ec4927a1
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 03619a67-d1ea-4b80-b1a6-0c65a9e9212f
role: Admin
exl-id: 260e405e-f59c-4aea-b83f-53ee103df94e
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 100%

---

# Konfigurieren von AEM Forms zum Senden von Formulardaten an einen AEM Forms on JEE-Prozess {#configuring-aem-forms-to-submit-form-data-to-an-aem-forms-on-jee-process}

Adaptive Formulare unterstützen die Übermittlung von Daten an einen AEM Forms on JEE-Prozess zur weiteren Verarbeitung. Dadurch können Sie einen AEM Forms-Prozess mit den Daten aus dem gesendeten Formular auslösen. Führen Sie die folgenden Schritte aus, damit Ihre AEM Forms-Instanz ein adaptives Formular an den AEM Forms on JEE-Prozess senden kann:

## Konfigurieren Sie Ihren AEM Forms-Server {#configure-your-aem-forms-server}

Führen Sie die folgenden Schritte aus, damit Ihr AEM Forms-Server Daten an einen AEM Forms on JEE-Server senden kann:

1. Wechseln Sie zur Seite zur Konfiguration der AEM-Web-Konsole unter https://[*Host*]:[*Port*]/system/console/configMgr.

1. Klicken Sie auf die **Adobe LiveCycle Client SDK-Konfigurationskomponente.**
1. Klicken Sie auf die Komponente, um URL, Benutzernamen und das Kennwort des AEM Forms on JEE-Servers zu bearbeiten.
1. Überprüfen Sie die Einstellungen und klicken Sie auf **Speichern**.

![Adobe LiveCycle Client SDK-Konfiguration](assets/clientsdkconfiguration.jpg)

## Zuordnung von Daten mit Verarbeitungsfeldern {#map-data-with-process-fields}

Nachdem der AEM Forms konfiguriert ist, ordnen Sie die Daten-XML und Anhänge vom gesendeten Formular den Feldern im AEM Forms-Prozess zu. Gehen Sie hierfür wie folgt vor:

1. In der AEM-Web-Konfigurationskonsole klicken Sie auf **Guide LiveCycle Process Locator and Invoker**, um die Konfiguration zu bearbeiten.
1. Geben Sie die folgenden Parameter an:

   * **Name der Daten-XML-Parameter** (obligatorisch): Geben Sie die XML-Eigenschaftendatei des AEM Forms-Prozesses an, der die gesendeten Daten verarbeiten muss. Der Standardwert lautet **dataxml**.
   * **Name des Dateianlagenparameters**(optional): Geben Sie die Liste der Dokumentobjekte an, die der AEM Forms on JEE-Prozess verarbeiten muss. Der Standardwert lautet **fileAttachmentsList**.

1. Überprüfen Sie die Einstellungen und klicken Sie auf **Speichern**.

![Guide LiveCycle Process Locator and Invoker](assets/test3.jpg)

Nachdem die Konfiguration abgeschlossen ist, listet die Aktion Senden an Formular-Arbeitsablauf die AEM Forms on JEE-Serverprozesse mit den angegebenen Daten-XML-Parametern.
