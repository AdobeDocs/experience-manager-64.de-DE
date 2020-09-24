---
title: AEM Forms JEE Patch Installer
description: 'null'
uuid: e709871b-c04c-43bb-a7d0-45e89fbd3d44
content-type: reference
discoiquuid: 83bace08-1d4f-4192-a634-c7c4879963d8
translation-type: tm+mt
source-git-commit: 610e9a54adad3abdfecb8b2c4da67d677f75175e
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 44%

---


# AEM Forms JEE Patch Installer {#aem-forms-jee-patch-installer}

>[!NOTE]
>
>[Wenden Sie sich an den Support](https://www.adobe.com/de/account/sign-in.supportportal.html) , um weitere Informationen zu erhalten oder den Patch zu erhalten.

## Informationen zum Patch-Installationsprogramm {#about-the-patch-installer}

Das AEM 6.4 Forms JEE Patch-Installationsprogramm enthält alle behobenen Probleme für alle Komponenten von AEM 6.4 Forms JEE, die bis zur Veröffentlichung dieses Patches verfügbar sind. Eine vollständige Liste der behobenen Probleme finden Sie in den aktuellen Versionshinweisen [zum](cfp-release-notes.md) Cumulative Fix Pack.

## Voraussetzungen für die Installation des Patches {#prerequisites-to-installing-the-patch}

* AEM 6.4 Forms

## Installieren und Konfigurieren des Patches {#installing-and-configuring-the-patch}

1. Erstellen Sie eine Sicherungskopie des Ordners *aem-forms_root*. Das ist erforderlich, wenn Sie die Schnellkorrektur deinstallieren.
1. Stoppen Sie den Anwendungsserver.
1. Extrahieren Sie die Patch-Installationsarchivdatei auf Ihre Festplatte.
1. Im Ordner mit dem Namen entsprechend des von Ihnen verwendeten Betriebssystems:

   * **Windows** Navigieren Sie zum entsprechenden Ordner auf dem Installationsdatenträger oder dem Installationsordner auf der Festplatte, in den Sie das Installationsprogramm kopiert haben, und klicken Sie mit der Dublette auf das 
`aemforms64_cfp_install.exe` file.

      * (Windows 32-bit) `Windows\Disk1\InstData\VM`
      * (Windows 64-bit) `Windows_64Bit`\ `Disk1\InstData\VM`
   * **Linux, Solaris, AIX** Navigieren Sie zum entsprechenden Ordner und geben Sie an einer Eingabeaufforderung 
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
1. When the installation is complete, click **[!UICONTROL Next]**to apply the quick fix updates to your installed files.
1. [Nur] Windows Führen Sie einen der folgenden Schritte aus:

   * Deaktivieren Sie die Option „LiveCycle Configuration Manager“ starten, bevor Sie auf „Fertig“ klicken. Führen Sie Configuration Manager zu einem späteren Zeitpunkt mithilfe der `ConfigurationManager.bat` Datei unter `[aem-forms root]\configurationManager\bin`. Mithilfe dieser `ConfigurationManager.bat` Hilfe vermeiden Sie die manuelle Aktualisierung des Namens axis.jar in .lax-Dateien
   * Deaktivieren Sie die Option „LiveCycle Configuration Manager“ starten, bevor Sie auf „Fertig“ klicken. Bevor Sie Configuration Manager mit **ConfigurationManager.exe** oder **ConfigurationManager_IPv6.exe** ausführen, navigieren Sie zum Ordner *&lt;AEMForms_Install_Dir>\configurationManager\bin* und aktualisieren Sie **axis.jar** in den folgenden Dateien auf **axis-1.4.1.1.jar** :

      * ConfigurationManager.lax
      * ConfigurationManager_IPv6.lax

1. (Nur Unix-basiert) Das Kontrollkästchen Beginn Configuration Manager ist standardmäßig aktiviert. Klicken Sie auf **[!UICONTROL Fertig]**, um Configuration Manager auszuführen.

   Um Configuration Manager später auszuführen, deaktivieren Sie die Option Configuration Manager starten, bevor Sie auf Fertig klicken. You can start Configuration Manager later using the appropriate script in the `[AEM_forms_root]/configurationManager/bin` directory.

1. Wählen Sie je nach Anwendungsserver eines der folgenden Dokumente aus und befolgen Sie die Anweisungen im Bereich *Konfigurieren und Bereitstellen von AEM Forms*.

   * [Installieren und Bereitstellen von AEM Forms für JBoss](http://www.adobe.com/go/learn_aemforms_installJBoss_64_de) 
   * [Installieren und Bereitstellen von AEM Forms für WebSphere](http://www.adobe.com/go/learn_aemforms_installWebSphere_64_de)
   * [Installieren und Bereitstellen von AEM Forms für WebLogic](http://www.adobe.com/go/learn_aemforms_installWebLogic_64_de)

1. (Nur JBoss) Löschen Sie nach der Installation des Patches und Konfiguration des Servers die Ordner &quot;tmp&quot;und &quot;work&quot;des JBoss-Anwendungsservers.

## Konfigurationen nach der Bereitstellung {#post-deployment-configurations}

### SAML-Konfigurationen {#saml-configurations}

Wenn Sie die SAML-Authentifizierung konfiguriert haben und Probleme mit großen IDP-Metadaten auftreten, führen Sie nach der Installation des Patches die folgenden Schritte aus:

1. Legen Sie die folgende Systemeigenschaft auf Ihrem Anwendungsserver fest:\
   `um.saml.enable.large.xml=true`

1. Starten Sie den Server neu.
1. Löschen Sie vorhandene SAML-Authentifizierungsanbieter und fügen Sie sie erneut für bestehende Domänen hinzu, wie in den SAML-Einstellungen beschrieben.

## Betroffene Module {#impacted-modules}

* Document Services
* Document Security
* Foundation JEE
* PDFG Service

[Support kontaktieren](https://www.adobe.com/de/account/sign-in.supportportal.html)