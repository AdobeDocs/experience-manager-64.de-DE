---
title: Druckkanal und Web-Kanal
seo-title: Print channel and web channel
description: Importieren von Druckkanalvorlagen und Erstellen und Aktivieren von Webkanalvorlagen
seo-description: Importing print channel templates and creating and enabling web channel templates
uuid: 19e6ffab-00d2-4084-9ee7-9643b11eb6c6
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 71bba66a-3cac-445b-9941-aa4bcf9b2160
feature: Interactive Communication
exl-id: cb7a8e96-4440-47ec-b506-275d5acc774e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 50%

---

# Druckkanal und Web-Kanal {#print-channel-and-web-channel}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Importieren von Druckkanalvorlagen und Erstellen und Aktivieren von Webkanalvorlagen

Interaktive Kommunikation kann über zwei Kanäle bereitgestellt werden: Druck und Web. Der Druckkanal wird verwendet, um PDF- und Papiernachrichten zu erstellen, z. B. einen gedruckten Brief als Erinnerung an Versicherungsprämie-Zahlungen, während der Webkanal zur Bereitstellung von Online-Erlebnissen wie einem Kreditkartenauszug auf einer Website verwendet wird.

Autoren der Vorlage für die interaktive Kommunikation können Elemente wie Dokumentfragmente und Bilder verwenden, um die Druck- bzw. Netzversionen der Vorlage für die interaktive Kommunikation zu erstellen.

Eine der Voraussetzungen für das [Erstellen einer interaktiver Kommunikation](/help/forms/using/create-interactive-communication.md) ist, dass die Vorlagen für den Druck- und/oder Webkanal auf dem Server verfügbar sind. Während Vorlagenautoren die Webkanalvorlage in AEM selbst erstellen, wird die Druckkanalvorlage XDP in Adobe Forms Designer erstellt und auf den Server hochgeladen.

## Druckkanal {#printchannel}

Der Druckkanal einer interaktiven Kommunikation verwendet die XFA-Formularvorlage XDP. Eine XDP wird mit Adobe Forms Designer entwickelt. Weitere Informationen zum Erstellen von Druckkanalvorlagen finden Sie unter [Layout-Design](/help/forms/using/layout-design-details.md). Um eine Druckkanalvorlage in Ihrer interaktiven Kommunikation zu verwenden, müssen Sie die Vorlage auf den AEM Forms-Server hochladen.

### Druckkanalvorlage für die interaktive Kommunikation hochladen {#upload-interactive-communication-print-channel-template}

Um die Vorlage hochzuladen, müssen Sie Mitglied der Gruppe &quot;forms-user&quot;sein. Führen Sie die folgenden Schritte aus, um die Druckkanalvorlage (XDP) in AEM Forms hochzuladen:

1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Formulare &amp; Dokumente]**.

1. Tippen Sie auf **[!UICONTROL Erstellen]** > **[!UICONTROL Datei hochladen]**.

   Navigieren Sie zur entsprechenden Druckkanalvorlage (XDP), wählen Sie diese aus und tippen Sie auf **[!UICONTROL Öffnen]**.

## Webkanal {#web-channel}

Vorlagenautoren und -administratoren können Webvorlagen erstellen, bearbeiten und aktivieren. Damit andere Benutzer Webvorlagen erstellen können, müssen Sie ihnen Berechtigungen erteilen. Weitere Informationen finden Sie unter [Verwalten von Benutzer-, Gruppen- und Zugriffsrechten](/help/sites-administering/user-group-ac-admin.md).

### Erstellen einer Webkanalvorlage {#authoring-web-channel-template}

Um eine Webkanalvorlage zu erstellen, müssen Sie zunächst einen Vorlagenordner erstellen. Sobald Sie eine Webvorlage in einem Vorlagenordner erstellt haben, müssen Sie die Vorlage aktivieren, damit die Formularbenutzer den Webkanal einer interaktiven Kommunikation basierend auf der Vorlage erstellen können.

Führen Sie die folgenden Schritte aus, um eine Webkanalvorlage zu erstellen:

1. Erstellen Sie einen Vorlagenordner, um Ihre Webvorlagen für interaktive Kommunikation zu speichern, falls noch kein entsprechender Ordner eingerichtet ist. Weitere Informationen finden Sie unter „Vorlagenordner“ in [Seitenvorlagen – Bearbeitbar](/help/sites-developing/page-templates-editable.md).

   1. Tippen **[!UICONTROL Instrumente]** ![tools-1](assets/tools-1.png) > **[!UICONTROL Konfigurationsbrowser]**.
      * Weitere Informationen finden Sie in der Dokumentation zum [Konfigurations-Browser.](/help/sites-administering/configurations.md)
   1. Tippen Sie auf der Seite „Konfigurationsbrowser“ auf **[!UICONTROL Erstellen]**.
   1. Legen Sie im Dialogfeld „Konfiguration erstellen“ einen Titel für den Ordner fest, aktivieren Sie **[!UICONTROL Bearbeitbare Vorlagen]** und tippen Sie auf **[!UICONTROL Erstellen]**.

      Der Ordner wird erstellt und auf der Seite „Konfigurationsbrowser“ aufgelistet.

1. Navigieren Sie zum entsprechenden Vorlagenordner und erstellen Sie eine Webvorlage.

   1. Navigieren Sie durch Auswahl zum entsprechenden Vorlagenordner **[!UICONTROL Instrumente]** > **[!UICONTROL Vorlagen > Ordner]**.
   1. Tippen Sie auf **[!UICONTROL Erstellen]**.
   1. Wählen Sie **[!UICONTROL Interaktive Kommunikation – Web-Kanal]** aus und tippen Sie auf **[!UICONTROL Weiter]**.
   1. Geben Sie einen Vorlagentitel und eine Beschreibung ein und tippen Sie anschließend auf **[!UICONTROL Erstellen]**.

      Die Vorlage wird erstellt und ein Dialogfeld wird angezeigt.

   1. Tippen **[!UICONTROL Öffnen]** , um die von Ihnen erstellte Vorlage im Vorlageneditor zu öffnen.

      Der Vorlagen-Editor wird angezeigt.

      ![webchanneltemplate](assets/webchanneltemplate.png)

      Beim Erstellen oder Bearbeiten einer Vorlage kann ein Vorlagenautor verschiedene Aspekte definieren. Das Erstellen oder Bearbeiten einer Vorlage ähnelt dem Erstellen von Seiten. Weitere Informationen finden Sie unter „Bearbeiten von Vorlagen – Vorlagenautoren“ in [Erstellen von Seitenvorlagen](/help/sites-authoring/templates.md).

1. Aktivieren Sie die Vorlage, um ihre Verwendung für die Erstellung interaktiver Kommunikation zu ermöglichen.

   1. Tippen **[!UICONTROL Instrumente]** ![tools-1](assets/tools-1.png) > **[!UICONTROL Vorlagen]**.
   1. Navigieren Sie zu der entsprechenden Vorlage, wählen Sie sie aus und tippen Sie auf **[!UICONTROL Aktivieren]**, dann tippen Sie in der Warnmeldung auf **[!UICONTROL Aktivieren]**.

      Die Vorlage ist aktiviert und ihr Status wird als Aktiviert angezeigt. Jetzt können Sie mit der Erstellung einer interaktiven Kommunikation fortfahren, in der Sie die neu erstellte Webkanalvorlage verwenden können.

### Druckkanal als Übergeordnet für Webkanal {#print-channel-as-master-for-web-channel}

Beim Erstellen einer interaktiven Kommunikation können Autoren diese Option auswählen, um den Webkanal synchron mit dem Druckkanal zu erstellen. Die Verwendung des Druckkanals als Übergeordnet für den Webkanal stellt sicher, dass der Inhalt, die Vererbung und die Datenbindung des Webkanals vom Druckkanal abgeleitet werden und die im Druckkanal vorgenommenen Änderungen im Webkanal übernommen werden können. Die Autoren der interaktiven Kommunikation können jedoch bei Bedarf die Vererbung für bestimmte Komponenten im Webkanal unterbrechen.

![printweb_2-2](assets/printweb_2-2.png)
