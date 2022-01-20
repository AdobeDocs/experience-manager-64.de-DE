---
title: AEM Desktop-Programm für AEM Forms
seo-title: AEM desktop app for AEM Forms
description: Mit AEM Desktop-Programm können Sie das Adobe Experience Manager (AEM) Assets-Repository und die binären AEM Forms-Dateien einem Netzwerkverzeichnis auf Ihrem System zuordnen. Erfahren Sie mehr über die in AEM Desktop-Programm unterstützten Assets und darüber, wie Sie AEM Forms für AEM Desktop-Programm aktivieren.
seo-description: AEM desktop app lets you map the Adobe Experience Manager (AEM) Assets repository and AEM Forms binary files to a network directory on your system. Learn more about the assets supported in AEM desktop app and how to enable AEM Forms for AEM desktop app.
uuid: 99e0f2fb-8623-45bb-8e2e-5c5d6f482366
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: manage
discoiquuid: c30332b6-e012-442d-8e84-28832c116c7b
noindex: true
role: Admin
exl-id: 26cd0851-cadf-4a8f-b3bf-59f77671f584
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 58%

---

# AEM Desktop-Programm für AEM Forms {#aem-desktop-app-for-aem-forms}

Mit AEM Desktop-Programm können Sie das Adobe Experience Manager (AEM) Assets-Repository und die binären AEM Forms-Dateien einem Netzwerkverzeichnis auf Ihrem System zuordnen. Sie können die synchronisierten Elemente und Binärdateien in einem Datei-Explorer anzeigen und die Dateien wie gewünscht mit einer Reihe von Apps bearbeiten. Dabei können Sie die Dateien nicht nur anzeigen, sondern auch Binärdateien erstellen, hochladen und löschen. Sie können Dateien auch direkt von der Software aus öffnen, bearbeiten und speichern. Sie können beispielsweise eine XDP-Datei direkt in Designer öffnen und bearbeiten. Die Änderungen, die Sie lokal an den Assets vornehmen, werden im AEM-Assets-Repository und in der AEM Forms-Benutzeroberfläche übernommen.

Sie können die App aus einer AEM-Instanz aus herunterladen. Ausführliche Informationen zum Herunterladen der App finden Sie unter [Versionshinweise zum AEM Desktop-Programm](https://helpx.adobe.com/experience-manager/desktop-app/release-notes.html).

## Unterstützte AEM Forms-Assets in AEM Desktop-Programm {#aem-forms-assets-supported-in-aem-desktop-app}

Mithilfe der App können Sie AEM Forms-Binärdateien der Typen Formatvorlage (.xdp), PDF-Formular (.pdf), Dokument (.pdf), Bilder, XML-Schema (.xsd) und Formatvorlage (.xfs) synchronisieren. Die App listet alle anderen Dateien (nicht unterstützte Dateien) als 0-Byte-Dateien auf. Durch die Anzeige nicht unterstützter Dateien als 0-Byte-Dateien wird der Benutzer darauf aufmerksam gemacht, dass andere Assets auf dem AEM Forms-Server vorhanden sind.

>[!NOTE]
>
>Ein Dateiname darf nur alphanumerische Zeichen, Bindestriche oder Unterstriche enthalten.

## AEM Forms für AEM Desktop-Programm aktivieren {#enable-aem-forms-for-aem-desktop-app}

AEM Desktop-Programm verwendet das WebDAV-Protokoll unter Microsoft Windows und SMB1 unter Mac OS X, um eine Verbindung zu einem AEM Forms-Server herzustellen. Standardmäßig ist der AEM Forms-Server nicht zum Synchronisieren von Binärdateien und anderen Assets mit einem WebDAV- oder SMB-Client aktiviert. Führen Sie die folgenden Schritte aus, um AEM Forms für AEM Desktop-Programm zu aktivieren:

1. Melden Sie sich bei AEM Forms als Administrator an.
1. Klicken Sie in der Autoreninstanz auf ![adobeexperiencemanager](assets/adobeexperiencemanager.png) **[!UICONTROL Adobe Experience Manager > Tools]** ![Hammer](assets/hammer.png) **[!UICONTROL > Bereitstellung > Vorgänge > Web-Konsole]**. Die Webkonsole wird in einem neuen Fenster geöffnet.
1. Suchen Sie im Fenster der Web-Konsole die Option **[!UICONTROL FormsManager AddOn Configuration]** und öffnen Sie sie.
1. Deaktivieren Sie im Dialogfeld „FormsManager AddOn Configuration“ das Kontrollkästchen **[!UICONTROL Asynchronously Sync Resources]** und klicken Sie auf **[!UICONTROL Speichern]**.
1. Starten Sie den AEM Forms-Server neu. Nach dem Neustart ist der AEM Forms-Server für die Annahme und Freigabe von Inhalten für AEM Desktop-Programm aktiviert.
1. Öffnen Sie die App und stellen Sie eine Verbindung zum AEM Forms-Server her.

   Bei erfolgreicher Verbindung füllt die App die `content/dam` und `content/dam/formsanddocuments` Ordner. Sie können mithilfe der App nicht nur Dateien aus den oben genannten Ordnern in lokale Ordner und umgekehrt, sondern auch Inhalte zwischen automatisch gefüllten Ordnern verschieben.
