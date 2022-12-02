---
title: AEM Forms JEE-Patch-Installationsprogramm
description: AEM Forms JEE-Patch-Installationsprogramm
uuid: e709871b-c04c-43bb-a7d0-45e89fbd3d44
content-type: reference
discoiquuid: 83bace08-1d4f-4192-a634-c7c4879963d8
exl-id: ce5300ce-03f4-4e7b-bc5b-01a9968ebe06
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 73%

---

# AEM Forms JEE-Patch-Installationsprogramm {#aem-forms-jee-patch-installer}

>[!NOTE]
>
>[Kontaktieren Sie den Support](https://www.adobe.com/account/sign-in.supportportal.html), um weitere Informationen oder den Patch zu erhalten.

## Über das Patch-Installationsprogramm {#about-the-patch-installer}

Das AEM 6.4 Forms JEE Patch-Installationsprogramm enthält alle behobenen Probleme für alle Komponenten von AEM 6.4 Forms JEE, die bis zur Veröffentlichung dieses Patches verfügbar waren. Aktuelle Informationen anzeigen  [Versionshinweise zum Cumulative Fix Pack](cfp-release-notes.md) für eine vollständige Liste der behobenen Probleme.

## Voraussetzungen für die Installation des Patches {#prerequisites-to-installing-the-patch}

* AEM 6.4 Forms

## Installieren und Konfigurieren des Patches {#installing-and-configuring-the-patch}

1. Erstellen Sie eine Sicherungskopie des Ordners *aem-forms_root*. Das ist erforderlich, wenn Sie die Schnellkorrektur deinstallieren.
1. Stoppen Sie den Programm-Server.
1. Extrahieren Sie die Archivdatei des Patch-Installationsprogramms auf Ihrer Festplatte.
1. Im Ordner mit dem Namen entsprechend des von Ihnen verwendeten Betriebssystems:

   * **Windows**


Navigieren Sie zum entsprechenden Ordner auf dem Installationsdatenträger oder dem Ordner auf der Festplatte, in den Sie das Installationsprogramm kopiert haben, und doppelklicken Sie auf die 
`aemforms64_cfp_install.exe` file.

      * (Windows 32-Bit) `Windows\Disk1\InstData\VM`
      * (Windows 64-Bit) `Windows_64Bit`\ `Disk1\InstData\VM`
   * **Linux, Solaris, AIX**
Navigieren Sie zum entsprechenden Ordner und geben Sie an einer Eingabeaufforderung Folgendes ein: 
`./aem64_cfp_install.bin`.

      * (Linux) `Linux/Disk1/InstData/NoVM`
      * (Solaris) `Solaris/Disk1/InstData/NoVM`
      * (AIX)

         ```
         AIX/Disk1/InstData/VM
         ```
   Hierdurch wird das Installieren des Assistenten gestartet, der Sie durch die Installation führt.

1. Klicken Sie im Begrüßungsbildschirm auf **[!UICONTROL Weiter]**.
1. Stellen Sie auf dem Bildschirm „Installationsordner auswählen“ sicher, dass der Standardspeicherort, der angezeigt wird, für Ihre bestehende Installation korrekt ist, oder klicken Sie auf **[!UICONTROL Durchsuchen]**, um den alternativen Ordner auszuwählen, auf dem AEM Forms installiert ist, und klicken Sie auf **[!UICONTROL Weiter]**.

1. Lesen Sie die Schnellkorrekturzusammenfassung und klicken Sie auf **[!UICONTROL Weiter]**.
1. Lesen Sie die Informationen zur „Zusammenfassung vor der Installation“ und klicken Sie auf **[!UICONTROL Installieren]**.
1. Klicken Sie nach Abschluss der Installation auf **[!UICONTROL Nächste]**um die Schnellkorrektur-Updates auf Ihre installierten Dateien anzuwenden.
1. [Nur Windows] Führen Sie einen der folgenden Schritte aus:

   * Deaktivieren Sie die Option „LiveCycle Configuration Manager“ starten, bevor Sie auf „Fertig“ klicken. Führen Sie Configuration Manager später mit dem `ConfigurationManager.bat` Datei in `[aem-forms root]\configurationManager\bin`. Verwenden `ConfigurationManager.bat` hilft Ihnen, das manuelle Aktualisieren des Namens von axis.jar in .lax-Dateien zu vermeiden
   * Deaktivieren Sie die Option „LiveCycle Configuration Manager“ starten, bevor Sie auf „Fertig“ klicken. Vor dem Ausführen von Configuration Manager mithilfe von **ConfigurationManager.exe** oder **ConfigurationManager_IPv6.exe**, navigieren Sie zu *&lt;aemforms_install_dir>\configurationManager\bin* Verzeichnis und aktualisieren **axis.jar** nach **axis-1.4.1.1.jar** in den folgenden Dateien:

      * ConfigurationManager.lax
      * ConfigurationManager_IPv6.lax

1. (Nur Unix-basiert) Das Kontrollkästchen Configuration Manager starten ist standardmäßig aktiviert. Klicken Sie auf **[!UICONTROL Fertig]**, um Configuration Manager auszuführen.

   Um Configuration Manager später auszuführen, deaktivieren Sie die Option Configuration Manager starten, bevor Sie auf Fertig klicken. Sie können Configuration Manager mithilfe des entsprechenden Skripts im Verzeichnis `[AEM_forms_root]/configurationManager/bin` starten,

1. Wählen Sie je nach Anwendungsserver eines der folgenden Dokumente aus und befolgen Sie die Anweisungen im Bereich *Konfigurieren und Bereitstellen von AEM Forms*.

   * [Installieren und Bereitstellen von AEM Forms für JBoss](http://www.adobe.com/go/learn_aemforms_installJBoss_64_de) 
   * [Installieren und Bereitstellen von AEM Forms für WebSphere](http://www.adobe.com/go/learn_aemforms_installWebSphere_64_de)
   * [Installieren und Bereitstellen von AEM Forms für WebLogic](http://www.adobe.com/go/learn_aemforms_installWebLogic_64_de)

1. (Nur JBoss) Löschen Sie nach der Installation des Patches und der Konfiguration des Servers die Ordner „tmp“ und „work“ des JBoss-Anwendungsservers.

## Konfigurationen nach der Bereitstellung {#post-deployment-configurations}

### SAML-Konfigurationen {#saml-configurations}

Wenn Sie die SAML-Authentifizierung konfiguriert hatten und Probleme mit großen IDP-Metadaten haben, führen Sie nach der Installation des Patches die folgenden Schritte aus:

1. Legen Sie die folgende Systemeigenschaft auf Ihrem Anwendungsserver fest:\
   `um.saml.enable.large.xml=true`

1. Starten Sie den Server neu.
1. Löschen Sie vorhandene SAML-Authentifizierungsanbieter und fügen Sie sie erneut für bestehende Domains hinzu, wie in den SAML-Einstellungen beschrieben.

## Betroffene Module {#impacted-modules}

* Document Services
* Document Security
* Foundation JEE
* PDFG Service

[Support kontaktieren](https://www.adobe.com/account/sign-in.supportportal.html)
