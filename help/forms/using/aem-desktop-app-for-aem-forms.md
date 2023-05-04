---
title: AEM Desktop-App für AEM Forms
seo-title: AEM desktop app for AEM Forms
description: Mit der AEM Desktop-App können Sie das Assets-Repository von Adobe Experience Manager (AEM) und Binärdateien für AEM Forms einem Netzwerkverzeichnis in Ihrem System zuordnen. Erfahren Sie mehr über die in AEM Desktop-Programm unterstützten Assets und darüber, wie Sie AEM Forms für AEM Desktop-Programm aktivieren.
seo-description: AEM desktop app lets you map the Adobe Experience Manager (AEM) Assets repository and AEM Forms binary files to a network directory on your system. Learn more about the assets supported in AEM desktop app and how to enable AEM Forms for AEM desktop app.
uuid: 99e0f2fb-8623-45bb-8e2e-5c5d6f482366
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: manage
discoiquuid: c30332b6-e012-442d-8e84-28832c116c7b
noindex: true
role: Admin
exl-id: 26cd0851-cadf-4a8f-b3bf-59f77671f584
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 50%

---

# AEM Desktop-App für AEM Forms {#aem-desktop-app-for-aem-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mit der AEM Desktop-App können Sie das Assets-Repository von Adobe Experience Manager (AEM) und Binärdateien für AEM Forms einem Netzwerkverzeichnis in Ihrem System zuordnen. Sie können die synchronisierten Assets und Binärdateien in einem Datei-Explorer anzeigen und verschiedene Apps verwenden, um die Dateien nach Bedarf zu bearbeiten. Neben der Ansicht der Dateien können Sie auch die Binärdateien erstellen, hochladen und löschen. Sie können Dateien auch direkt aus der Software öffnen, bearbeiten und speichern. Sie können beispielsweise eine XDP-Datei direkt in Designer öffnen und bearbeiten. Die Änderungen, die Sie lokal an den Assets vornehmen, spiegeln sich im AEM Assets-Repository und in der AEM Forms-Benutzeroberfläche wider.

Sie können die App von einer AEM-Instanz herunterladen. Ausführliche Informationen zum Herunterladen der App finden Sie in den [Versionshinweisen zur AEM Desktop-App](https://helpx.adobe.com/de/experience-manager/desktop-app/release-notes.html).

## AEM Forms-Assets, die in der AEM Desktop-App unterstützt werden {#aem-forms-assets-supported-in-aem-desktop-app}

Sie können das Programm zum Synchronisieren von AEM Forms-Binärdateien des folgenden Typs verwenden: Formularvorlagen (.xdp), PDF-Formular (.pdf), Dokument (.pdf), Bilder, XML-Schema (.xsd), Stylesheets (.xfs). Das Programm listet alle anderen Dateien (nicht unterstützte Dateien) als 0-Byte-Dateien auf. Durch das Auflisten nicht unterstützter Dateien als 0-Byte-Dateien wird sichergestellt, dass der Benutzer weiß, dass andere auf dem AEM Forms-Server verfügbare Assets vorhanden sind.

>[!NOTE]
>
>Dateinamen dürfen nur alphanumerische Zeichen, Bindestriche oder Unterstriche enthalten.

## Aktivieren von AEM Forms für die AEM Desktop-App {#enable-aem-forms-for-aem-desktop-app}

AEM Desktop-Programm verwendet das WebDAV-Protokoll unter Microsoft Windows und SMB1 unter Mac OS X, um eine Verbindung zu einem AEM Forms-Server herzustellen. Standardmäßig ist der AEM Forms-Server nicht zum Synchronisieren von Binärdateien und anderen Assets mit einem WebDAV- oder SMB-Client aktiviert. Führen Sie die folgenden Schritte aus, um AEM Forms für AEM Desktop-Programm zu aktivieren:

1. Melden Sie sich bei AEM Forms als Administrator an.
1. Klicken Sie in der Authoring-Instanz auf ![adobeexperiencemanager](assets/adobeexperiencemanager.png) **[!UICONTROL Adobe Experience Manager > Tools]** ![Hammer](assets/hammer.png) **[!UICONTROL Implementierung > Vorgänge > Web-Konsole]**. Die Webkonsole wird in einem neuen Fenster geöffnet.
1. Suchen Sie im Fenster der Web-Konsole die Option **[!UICONTROL FormsManager AddOn Configuration]** und öffnen Sie sie.
1. Deaktivieren Sie im Dialogfeld „FormsManager AddOn Configuration“ das Kontrollkästchen **[!UICONTROL Asynchronously Sync Resources]** und klicken Sie auf **[!UICONTROL Speichern]**.
1. Starten Sie den AEM Forms-Server neu. Nach dem Neustart kann der AEM Forms-Server Inhalte von der AEM Desktop-App akzeptieren und mit ihr austauschen.
1. Öffnen Sie die App und stellen Sie eine Verbindung zum AEM Forms-Server her.

   Wird die Verbindung erfolgreich hergestellt, füllt die App die Ordner `content/dam` und `content/dam/formsanddocuments`. Sie können mithilfe der App nicht nur Dateien aus den oben genannten Ordnern in lokale Ordner und umgekehrt, sondern auch Inhalte zwischen automatisch gefüllten Ordnern verschieben.
