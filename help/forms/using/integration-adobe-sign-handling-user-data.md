---
title: Integration mit Acrobat Sign | Umgang mit Benutzerdaten
seo-title: Integration with Acrobat Sign | Handling user data
description: AEM Forms kann mit Acrobat Sign integriert werden, um E-Signatur-Workflows in adaptiven Formularen zu ermöglichen, um Formulare oder Vereinbarungen für Rechts-, Verkaufs-, Gehaltsabrechnungs- und Personalverwaltungs-Workflows zu verarbeiten. Detailliertere Informationen zu Benutzerdaten und Datenspeichern sowie zum Zugriff auf und Löschen von Benutzerdaten.
seo-description: AEM Forms integrates with Acrobat Sign to enable e-signature workflows in adaptive forms to process forms or agreements for legal, sales, payroll, human resource management workflows. Dig deeper on user data, data stores, and access and delete user data.
uuid: cb3a455d-2e33-44c8-8f71-3a7ecd939cd8
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e9e0d8fb-955e-4021-9e9a-9c95c6ffe88d
feature: Acrobat Sign
role: Admin
exl-id: c2061de7-8627-4595-b96c-aa2d6abffddd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 13%

---

# Integration mit Acrobat Sign | Umgang mit Benutzerdaten {#integration-with-adobe-sign-handling-user-data}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

AEM Forms kann mit Acrobat Sign integriert werden, um E-Signatur-Workflows in adaptiven Formularen zu ermöglichen, um Formulare oder Vereinbarungen für Rechts-, Verkaufs-, Gehaltsabrechnungs- und Personalverwaltungs-Workflows zu verarbeiten. Es ermöglicht das Signieren von Einzel- und Mehrbenutzer-Signaturen, sequenzielle und simultane Signier-Workflows, das Signieren von Formularen als anonymer oder angemeldeter Benutzer und mehrere Möglichkeiten zur Authentifizierung von Benutzern.

Wenn ein Unterzeichner oder mehrere Unterzeichner ein adaptives Formular signieren und senden, wird eine Acrobat Sign-Vereinbarung generiert, die Informationen zu den Unterzeichnern enthält.

Weitere Informationen zur Integration von AEM Forms mit Acrobat Sign finden Sie unter [Verwenden von Acrobat Sign in einem adaptiven Formular](/help/forms/using/working-with-adobe-sign.md).

## Benutzerdaten und Datenspeicher {#data}

Für Acrobat Sign aktiviertes adaptives Formular enthält Informationen zu den Unterzeichnern und kann andere Benutzerdaten enthalten, die vom adaptiven Formular erfasst werden. Der Acrobat Sign-Dienst speichert Benutzerdaten mit der Signatur innerhalb der Vereinbarung. Die Vereinbarung wird auf dem Acrobat Sign-Server gespeichert, der in AEM Forms Cloud Services konfiguriert ist. Wenn das adaptive Formular für die Verwendung der Übermittlungsaktion für Forms Portal konfiguriert ist, werden die Vertragsdaten zusammen mit den Formulardaten im Forms Portal-Datenspeicher gespeichert.

## Zugreifen auf und Löschen von Benutzerdaten {#access-and-delete-user-data}

Benutzerdaten werden innerhalb der Vereinbarung erfasst, aber nicht in einer der Service-Tabellen gespeichert. Mit Acrobat Sign können Administratoren ihre eigenen Entscheidungen bezüglich der Verwaltung von Daten treffen, die sie im Dienst steuern. Datenschutzadministratoren im Acrobat Sign-Dienst können Vereinbarungen anhand der E-Mail-Adresse eines Anfragenden auflisten oder entfernen.

Acrobat Sign bietet eine Webanwendung, die das Durchsuchen von Vereinbarungen durch Teilnehmer ermöglicht und diese bei Bedarf löscht. Weitere Informationen finden Sie unter [Acrobat Sign - Funktion: Benutzerinformationen löschen](https://helpx.adobe.com/de/sign/help/adobesign_gdpr_user_deletion.html).

Vereinbarungsdaten für adaptive Formulare, die für die Verwendung der Übermittlungsaktion für Forms Portal konfiguriert sind, werden ebenfalls im Forms Portal-Datenspeicher gespeichert. Informationen zum Zugreifen auf und Löschen von Daten aus dem Forms Portal-Datenspeicher finden Sie unter [Forms-Portal | Umgang mit Benutzerdaten](/help/forms/using/forms-portal-handling-user-data.md).
