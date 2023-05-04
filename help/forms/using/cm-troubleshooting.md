---
title: "Correspondence Management: Fehlerbehebung"
seo-title: Correspondence Management Troubleshooting
description: Correspondence Management - Fehlerbehebung
seo-description: Correspondence Management Troubleshooting
uuid: 25828cdd-110e-4a84-8f31-d82cd610a54f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: cc473808-e71a-4834-bb30-91e6df783e60
feature: Correspondence Management
exl-id: 82a35d81-13d0-435f-875e-6fd0a6d574d5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 28%

---

# Correspondence Management: Fehlerbehebung {#correspondence-management-troubleshooting}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Fehler beim Speichern eines Briefs {#errors-when-saving-a-letter}

### Problem {#issue}

Einer der folgenden Fehler wird beim Speichern eines Briefs angezeigt:

* Datenbindung für das Textmodul nicht vorhanden
* Geben Sie die Eigenschaftsangaben an, die für Folgendes benötigt werden

### Grund {#reason}

Diese Fehler können aus einem der folgenden Gründe auftreten:

* Ein Datenwörterbuch ist an den Brief gebunden, aber nicht auf dem Server vorhanden.
* Ein Datenwörterbuch ist an den Brief gebunden, hat jedoch einen Unterstrich (_) in seinem Namen.

### Problemumgehung {#workaround}

Stellen Sie sicher, dass das Datenwörterbuch, das Sie im Brief verwenden, auf dem Server vorhanden ist und keinen Unterstrich (_) im Namen enthält.

## Fehler bei der Briefvorschau {#error-when-previewing-a-letter}

### Problem {#issue-1}

Bei der Vorschau eines Briefs wird der Fehler &quot;Fehler beim Laden des Briefs: Asset konnte nicht aus XML-Eingabe importiert werden&quot;wird auch dann angezeigt, wenn ein zuvor unveröffentlichtes Textelement im Brief veröffentlicht wird.

### Problemumgehung {#workaround-1}

Setzen Sie den Brief-Cache auf der Veröffentlichungsinstanz mit den folgenden Schritten zurück und versuchen Sie dann erneut, den Brief anzuzeigen:

1. Navigieren Sie zu **`https://[server]:[port]/[contextPath]/system/console/configMgr`** und melden Sie sich als Administrator an.
1. Wählen Sie **Correspondence Management-Konfigurationens**.
1. Deaktivieren Sie in **Correspondence Management-Konfigurationen** die Option **Briefcache aktivieren** und klicken Sie auf **Speichern.**
1. Aktivieren Sie **Brief-Cache aktivieren** und klicken Sie dann auf **Speichern**.
1. Versuchen sie noch einmal, den Brief anzuzeigen.
