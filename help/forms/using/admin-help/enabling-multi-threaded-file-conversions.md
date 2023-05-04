---
title: Aktivieren mehrprozessgestützter Dateikonvertierungen
seo-title: Enabling multi-threaded file conversions
description: Erfahren Sie, wie Sie mehrprozessgestützte Dateikonvertierungen aktivieren.
seo-description: Learn how to enable multi-threaded file conversions.
uuid: 830c78aa-4f68-4e01-8b24-69a0275689c7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 85d655bb-1b6b-4b4d-ae39-eca3ef9b7fd7
feature: PDF Generator
exl-id: f0441588-7c16-40ab-841f-e89576a0d292
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '905'
ht-degree: 8%

---

# Aktivieren mehrprozessgestützter Dateikonvertierungen {#enabling-multi-threaded-file-conversions}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

PDF Generator bietet die Möglichkeit, mehrprozessgestützte Dateikonvertierungen für bestimmte Dateitypen zu aktivieren. Mehrprozessgestützte Dateikonvertierungen verbessern die Leistung von PDF Generator, da mehrere Konvertierungen gleichzeitig durchgeführt werden können.

## Mehrprozessgestützte Dateikonvertierungen für OpenOffice-, Word- und PowerPoint-Dokumente aktivieren {#enabling-multi-threaded-file-conversions-for-openoffice-word-and-powerpoint-documents}

Standardmäßig kann PDF Generator nur ein OpenOffice-, Microsoft Word- oder PowerPoint-Dokument gleichzeitig konvertieren. Wenn Sie mehrprozessgestützte Konvertierungen aktivieren, kann PDF Generator mehrere Dokumente gleichzeitig konvertieren. PDF Generator startet mehrere Instanzen von OpenOffice oder PDFMaker (zum Ausführen der Word- und PowerPoint-Konvertierungen).

>[!NOTE]
>
>Mehrprozessgestützte Dateikonvertierungen werden in Microsoft Word 2003 und PowerPoint 2003 nicht unterstützt. Um mehrprozessgestützte Dateikonvertierungen zu aktivieren, aktualisieren Sie auf Microsoft Word 2007 und PowerPoint 2007 oder Microsoft Word 2010 und PowerPoint 2010.

>[!NOTE]
>
>Mehrprozessgestützte Dateikonvertierungen werden von Microsoft Excel, Microsoft Visio, Microsoft Project oder Microsoft Publisher nicht unterstützt.

Jede Instanz von OpenOffice oder PDFMaker wird mithilfe eines separaten Benutzerkontos gestartet. Jedes von Ihnen hinzugefügte Benutzerkonto muss zu einem gültigen Benutzer mit Administratorrechten für den Formularservercomputer gehören. In einer Clusterumgebung muss derselbe Satz von Benutzern für alle Knoten des Clusters gültig sein.

Auf der Seite &quot;Benutzerkonten&quot;in Administration Console können Sie angeben, welche Benutzerkonten für mehrprozessgestützte Dateikonvertierungen verwendet werden sollen. Sie können Konten hinzufügen, löschen oder Kontokennwörter ändern. Wenn Sie PDF Generator unter Windows Server 2003 oder Windows Server 2008 ausführen, fügen Sie mindestens drei Benutzerkonten mit Administratorrechten hinzu.

Wenn Sie Benutzer für OpenOffice, Microsoft Word oder Microsoft PowerPoint unter Windows Server 2003 oder 2008 oder für OpenOffice unter Linux oder Sun™ Solaris™ hinzufügen, schließen Sie die anfänglichen Aktivierungsdialogfelder für alle Benutzer.

### Berechtigung zum Ersetzen des Tokens auf Prozessebene hinzufügen {#add-the-right-to-replace-the-process-level-token}

Unter einem Windows-Betriebssystem benötigen die Administrator-Benutzerkonten, die für die PDF-Konvertierung verwendet werden (PDFG-Benutzer), die Berechtigung zum Ersetzen von Token auf Prozessebene. Sie können diese Berechtigung mit dem Gruppenrichtlinien-Editor hinzufügen:

1. Klicken Sie im Windows-Startmenü auf Ausführen und geben Sie dann gpedit.msc ein.
1. Klicken Sie auf Lokale Computerrichtlinie > Computerkonfiguration > Windows-Einstellungen > Sicherheitseinstellungen > Lokale Richtlinien > Zuweisen von Benutzerrechten. Bearbeiten Sie die *Ersetzen eines Tokens auf Prozessebene* Richtlinie, um die Gruppe Administratoren einzubeziehen.
1. Fügen Sie den Benutzer zum Eintrag &quot;Token auf Prozessebene ersetzen&quot;hinzu.

### Zusätzliche für OpenOffice, Microsoft Word und Microsoft PowerPoint unter Windows Server 2008 erforderliche Konfiguration {#additional-configuration-required-for-openoffice-microsoft-word-and-microsoft-powerpoint-on-windows-server-2008}

Wenn Sie OpenOffice, Microsoft Word oder Microsoft PowerPoint unter Windows Server 2008 ausführen, deaktivieren Sie die Benutzerkontensteuerung für jeden hinzugefügten Benutzer.

1. Klicken Sie auf Systemsteuerung > Benutzerkonten > Benutzerkontensteuerung aktivieren oder deaktivieren.
1. Deaktivieren Sie das Kontrollkästchen &quot;Use User Account Control (UAC) to help protect your computer&quot;und klicken Sie auf &quot;OK&quot;.
1. Starten Sie den Computer neu, damit die Einstellungen wirksam werden.

### Zusätzliche für OpenOffice unter Linux oder Solaris erforderliche Konfiguration {#additional-configuration-required-for-openoffice-on-linux-or-solaris}

1. Fügen Sie Benutzerkonten hinzu. (Siehe [Hinzufügen von Benutzerkonten](enabling-multi-threaded-file-conversions.md#add-a-user-account).
1. Als Nächstes nehmen Sie Änderungen an der Datei /etc/sudoers vor. Die Standardberechtigung für diese Datei ist 440. Ändern Sie die Berechtigung für diese Datei in Schreibzugriff.
1. Fügen Sie Einträge für weitere Benutzer (außer dem Administrator, der den Formularserver ausführt) in der Datei &quot;/etc/sudoers&quot;hinzu. Wenn Sie beispielsweise AEM Formulare als Benutzer mit dem Namen &quot;lcadm&quot;und einen Server mit dem Namen &quot;myhost&quot;ausführen und Sie die Identität von &quot;Benutzer1&quot;und &quot;Benutzer2&quot;annehmen möchten, fügen Sie &quot;/etc/sudoers&quot;die folgenden Einträge hinzu:

   ```as3
    lcadm myhost=(user1) NOPASSWD: ALL 
    lcadm myhost=(user2) NOPASSWD: ALL
   ```

   Diese Konfiguration ermöglicht es lcadm, jeden Befehl auf dem Host &quot;myhost&quot;als &quot;user1&quot;oder &quot;user2&quot;auszuführen, ohne ein Kennwort einzugeben.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Sie &quot;Benutzer1&quot;und &quot;Benutzer2&quot;Systembenutzer- und PDFG-Benutzerrollen zugewiesen haben. Informationen zum Zuweisen der PDFG-Rolle zu einem Benutzer finden Sie unter [Hinzufügen von Benutzerkonten](enabling-multi-threaded-file-conversions.md#add-a-user-account)

1. Suchen und kommentieren Sie diese Zeile auch in der Datei &quot;/etc/sudoers&quot;aus, indem Sie am Anfang der Zeile ein Nummernzeichen (#) hinzufügen:

   ```as3
   Defaults requiretty
   ```

   Dadurch können Sie Linux-Benutzer hinzufügen.

1. Ändern Sie die Berechtigung für die Datei &quot;etc/sudoers&quot;zurück in 440.
1. Erlauben Sie allen Benutzern, die Sie über [Ein Benutzerkonto hinzufügen](enabling-multi-threaded-file-conversions.md#add-a-user-account) hinzugefügt haben, Verbindungen zum Formularserver herzustellen. Wenn Sie beispielsweise einem lokalen Benutzer mit dem Namen „Benutzer1“ die Berechtigung zuweisen möchten, eine Verbindung zum Formularserver herzustellen, verwenden Sie den folgenden Befehl:

   `xhost +local:user1@`

   Weitere Informationen finden Sie in der Dokumentation zum xhost-Befehl .

1. Starten Sie den Server neu.

>[!NOTE]
>
>OpenOffice muss in einem Ordnerspeicherort installiert sein, auf den alle PDFG-Benutzer zugreifen können. Sie können dies überprüfen, indem Sie sich als PDFG-Benutzer anmelden und überprüfen, ob Sie OpenOffice ohne Probleme starten können.

### Hinzufügen von Benutzerkonten {#add-a-user-account}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;Benutzerkonten&quot;.
1. Klicken Sie auf Hinzufügen und geben Sie den Benutzernamen und das Kennwort eines Benutzers ein, der über Administratorrechte auf dem Formularserver verfügt. Wenn Sie Benutzer für OpenOffice konfigurieren, schließen Sie die anfänglichen OpenOffice-Aktivierungsdialogfelder.

   >[!NOTE]
   >
   >Wenn Sie Benutzer für OpenOffice konfigurieren, darf die Anzahl der Instanzen von OpenOffice nicht größer sein als die Anzahl der in diesem Schritt angegebenen Benutzerkonten.

1. Starten Sie den Formularserver neu.

### Entfernen Sie einen Benutzer aus der Liste, die für mehrprozessgestützte Dateikonvertierungen verwendet wird. {#remove-a-user-from-the-list-used-for-multi-threaded-file-conversions}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;Benutzerkonten&quot;.
1. Aktivieren Sie das Kontrollkästchen neben dem Benutzer, den Sie entfernen möchten, und klicken Sie auf &quot;Löschen&quot;.
1. Klicken Sie auf der Bestätigungsseite auf Löschen.
1. Starten Sie den Formularserver neu.

### Ändern des Kennworts für ein Konto {#change-the-password-for-an-account}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;Benutzerkonten&quot;.
1. Klicken Sie auf den Benutzernamen, geben Sie das neue Kennwort ein und bestätigen Sie es. Dieses Kennwort muss mit dem Systemkennwort des Benutzers übereinstimmen.
