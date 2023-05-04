---
title: Arbeiten im Offline-Modus
seo-title: Working in the offline mode
description: Arbeiten Sie mit Ihrem Mobilgerät offline an der AEM Forms-App, indem Sie es außerhalb Ihres AEM Forms-Netzwerks oder vollständig offline schalten.
seo-description: Take your mobile device offline outside your AEM Forms network range or in a completely offline mode and work on the AEM Forms app
uuid: b900a0f8-90ce-486a-bde6-6cdf11bd2801
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 9a3c6ab4-8bb9-40c7-8c56-59153b364887
exl-id: 14303b8f-40a7-4bc5-8282-7526e0319264
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 48%

---

# Arbeiten im Offline-Modus {#working-in-the-offline-mode}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Der Offline-Modus der AEM Forms-Mobile-App ermöglicht es, die Arbeit nahtlos fortzusetzen, selbst wenn die Mobile App offline geht. Sie können ein Formular öffnen, aktualisieren und senden, ohne dass eine Netzwerkverbindung erforderlich ist.

Sie beginnen Ihre Arbeit mit der AEM Forms-Mobile-App, indem Sie die Mobile App mit dem AEM Forms-Server synchronisieren. Alle Formulare, die Ihnen zugewiesen sind, werden in Ihre App heruntergeladen. Bei AEM Forms on JEE werden Aufgaben auf der Registerkarte &quot;Aufgaben&quot;abgerufen sowie mit Startpunkten verknüpfte Formulare und andere Formulare auf der Registerkarte &quot;Forms&quot;. Bei AEM Forms unter OSGi werden nur Forms auf der Registerkarte Forms geladen.

Weitere Informationen zum Synchronisieren der App finden Sie unter [Synchronisieren der App](/help/forms/using/sync-app.md).

## Offline-Verfügbarkeit von Forms {#making-forms-available-offline}

Wenn Sie die App mit dem AEM Forms-Server synchronisieren, werden die Formulare auf Ihr mobiles Gerät heruntergeladen. Die mit der Aufgabe verknüpften Anhänge werden jedoch standardmäßig nicht heruntergeladen. Dies bedeutet, dass Sie die Anlagen anzeigen können, wenn Sie online sind. Um jedoch sicherzustellen, dass Sie die Anlage im Offline-Modus anzeigen können, ändern Sie die Standardeinstellungen in Ihrer App.

Um sicherzustellen, dass die verknüpften Anlagen mit jedem Formular heruntergeladen werden, setzen Sie &quot;Fetch attachments&quot;auf &quot;ON&quot;. Weitere Informationen finden Sie unter [Aktualisieren allgemeiner Einstellungen](/help/forms/using/update-general-settings.md).

Da das Herunterladen von Daten die Leistung des mobilen Geräts beeinträchtigen kann, ist die Option „Fetch attachments“ standardmäßig auf „OFF“ gesetzt. Wenn diese Einstellung auf „ON“ gesetzt wird, werden die Anlagen für alle Aufgaben, die danach vom Server heruntergeladen werden, auf das mobile Gerät geladen. Der Benutzer kann im Offline-Modus alle Aufgaben bearbeiten, die auf das Gerät heruntergeladen wurden, nachdem die Option **Fetch attachments** auf „ON“ gesetzt wurde.

## Konfiguration des Offlinedienstes für die AEM Forms-App {#configuring-offline-service-for-aem-forms-app-br}

Der Dienst für die AEM Forms Offline-App identifiziert die in einem Formular verwendeten Ressourcen. Die AEM Forms-App nutzt diesen Dienst zum Abrufen von Informationen zu Formularabhängigkeiten. Informationen zu Formularabhängigkeiten sind erforderlich, um Offline-Funktionen zu aktivieren. Der Offlinedienst für die AEM Forms-App speichert die Pfade oder URLs der in einem Formular verwendeten Ressourcen zwischen. Der Cache wird anhand der Änderungen im Formular und der für den Offlinedienst konfigurierten Gültigkeitsdauer aktualisiert. Durch das Zwischenspeichern der Pfa oder URLs der in einem Formular verwendeten Ressourcen wird die serverseitige Leistung verbessert.

Serverseitige Offlinekomponente der AEM Forms-App konfigurieren:

1. Navigieren Sie auf der Autoreninstanz zu **Adobe Experience Manager** > **Werkzeuge** > **Formulare** > **Offline-Service für Forms-Mobile- App konfigurieren**.

   URL: `https://<server>:<port>/<context-path>/libs/fd/workspace-offline/gui/content/config.html`

1. Unter &quot;Allgemeine Einstellungen&quot;können Sie Folgendes ausführen:

   * **Cache löschen**: Löscht den serverseitigen Cache der Formularabhängigkeiten.
   * **Konfiguration zurücksetzen**: Setzt die Offline-Konfiguration der AEM Forms-Mobile-App zurück.
   * **Cache-Gültigkeit**: Gibt den Gültigkeitszeitraum für den serverseitigen Offline-Cache an.
   * **Ressourcenüberwachungspfade**: Gibt Pfade an, unter denen der Offlinedienst auf Ressourcenänderungen überwacht. Wenn Änderungen in den angegebenen Pfaden auftreten, wird der Offline-Cache aller abhängigen Formulare aktualisiert. Beispiel: `/etc/clientlibs/fd,/content/dam/images`.

1. Im **Manueller Ressourcen-Cache** -Registerkarte angeben, geben Sie die Formularabhängigkeiten an, die der Offlinedienst nicht identifizieren kann. Sie können Ressourcen angeben, z. B. aus JavaScript geladene Bilder. Das AEM Forms-Programm lädt diese Ressourcen auch für den Offline-Modus herunter.
