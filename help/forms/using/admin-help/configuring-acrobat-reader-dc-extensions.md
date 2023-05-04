---
title: Konfigurieren von Acrobat Reader DC Extensions für die Datenerfassung
seo-title: Configuring Acrobat Reader DC extensions for data capture
description: Erfahren Sie, wie Sie Acrobat Reader DC-Erweiterungen für die Datenerfassung konfigurieren.
seo-description: Learn how to configure Acrobat Reader DC extensions for data capture.
uuid: af6b3c72-601e-4f54-8343-a323eeee5906
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 8f8367fe-a8e9-46ee-a980-1633be02932d
exl-id: 3609ad29-f5b4-4426-8bbc-7c2e38f9b140
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 13%

---

# Konfigurieren von Acrobat Reader DC Extensions für die Datenerfassung {#configuring-acrobat-reader-dc-extensions-for-data-capture}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Wenn Benutzer Ihrer AEM Forms-Installation die Datenerfassungsfunktion von Content Services (nicht mehr unterstützt) verwenden, wird empfohlen, eine Rolle mit schreibgeschütztem Zugriff für diese Benutzer zu erstellen.

***Hinweis**: Adobe® LiveCycle® Content Services ES (nicht mehr unterstützt) ist ein Content-Management-System, das mit LiveCycle installiert wird. Sie ermöglicht es Benutzern, am Menschen orientierte Prozesse zu entwerfen, zu verwalten, zu überwachen und zu optimieren. Die Unterstützung von Content Services (veraltet) endet am 31.12.2014.

Für die Datenerfassung müssen Sie eine Benutzerrolle für den Zugriff auf die SampleReaderExtensionsCredential zuweisen. Sie können die standardmäßige Rolle &quot;Vertrauensadministrator&quot;zuweisen. Beachten Sie jedoch, dass diese Rolle allgemeinen, nicht administrativen Benutzern die leistungsstarken Administratorberechtigungen gewährt, die die PKI-Vertrauenseinstellungen steuern und PKI-Anmeldeinformationen verwalten. Dies könnte die Sicherheit Ihrer AEM Forms-Installation in einer Produktionsumgebung beeinträchtigen. Es wird empfohlen, dass der AEM Forms-Systemadministrator eine Rolle erstellt, die nur schreibgeschützten Zugriff auf den Trust Store gewährt, und diese neue Rolle Benutzern ohne Administratorrechte zuweist, die die Datenerfassung verwenden.

## Rollen für Datenerfassungsbenutzer erstellen {#create-a-role-for-data-capture-users}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Rollenverwaltung&quot;und dann auf &quot;Neue Rolle&quot;.
1. Geben Sie den Rollennamen (z. B. &quot;Datenerfassungsbenutzer&quot;) und die Beschreibung in die entsprechenden Felder ein und klicken Sie dann auf &quot;Weiter&quot;.
1. Klicken Sie im Bildschirm &quot;Rollenberechtigungen&quot;auf &quot;Berechtigungen suchen&quot;und wählen Sie dann in der Liste der verfügbaren Berechtigungen die Option &quot;Berechtigung lesen&quot;aus.
1. Klicken Sie auf OK und dann auf Fertigstellen.

## Datenerfassungsrolle zuweisen {#assign-the-data-capture-role}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Rollenverwaltung&quot;und dann auf &quot;Suchen&quot;.
1. Klicken Sie auf die von Ihnen erstellte Benutzerrolle für die Datenerfassung.
1. Klicken Sie auf der Registerkarte Rollenbenutzer/-gruppen auf Benutzer/Gruppen suchen .
1. Klicken Sie im Bildschirm &quot;Benutzer und Gruppen suchen&quot;auf &quot;Suchen&quot;, wählen Sie die Benutzer aus, die die Datenerfassungsbenutzerrolle benötigen, und klicken Sie dann auf &quot;OK&quot;.
1. Klicken Sie im Bildschirm Rolle bearbeiten auf Speichern.
