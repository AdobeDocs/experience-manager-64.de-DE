---
title: 'Dateispeicherorte für Output angeben '
seo-title: Specify file locations for Output
description: Erfahren Sie, wie Sie Dateispeicherorte für die Ausgabe angegeben.
seo-description: Learn how to specify file locations for Output.
uuid: 3287274f-85b5-4811-8abb-d347a9b80947
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 460bbb31-8187-469c-8102-b310093b6c03
exl-id: 5b8f04dd-6781-4126-8bb2-5d8b7a2f19c8
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 71%

---

# Dateispeicherorte für Output angeben {#specify-file-locations-for-output}

Sie können die Speicherorte angeben, an denen Output nach bestimmten Typen von erforderlichen Dateien suchen soll.

1. Klicken Sie in Administration Console auf „Dienste“ > „Output“.
1. Geben Sie unter „Speicherorte“ die entsprechenden Optionen an.
1. Klicken Sie auf Speichern.

## Speicherorteinstellungen {#locations-settings}

**Inhaltsstamm-URI:** Der URI oder der absolute Speicherort des Repositorys, aus dem Formulare abgerufen werden. Dieser Wert wird mit dem Parameter sForm kombiniert, der über die API angegeben wird, um den absoluten Pfad zu dem Formular zu erzeugen, das abgerufen wird. Dieser Wert kann auf einen Ordner oder einen Webspeicherort verweisen, auf den über HTTP zugegriffen werden kann. 

 Der Standardwert ist eine leere Zeichenfolge.

**XCI-Konfigurationsdatei:** Der relative oder absolute Speicherort der XCI-Konfigurationsdatei, die der Output-Dienst für die Wiedergabe verwendet. Bei einem relativen Wert wird vorausgesetzt, dass sich die XCI-Datei in der von AEM Forms bereitstellbaren EAR-Datei befindet.

Der Standardwert ist `com/adobe/formServer/PA/pa_output.xci`.

**Cache-Speicherort:** Gibt den Speicherort des Output Disk-Cache an. Nachdem Sie diese Einstellung geändert haben, werden alle vorhandenen Zwischenspeicherinformationen am aktuellen Speicherort zurückgesetzt und es wird ein neuer Zwischenspeicher am neuen Speicherort erstellt. Wählen Sie eine der folgenden Optionen aus:

**Standardspeicherort:** Dies ist die Standardauswahl. Wenn diese Option ausgewählt ist, wird der Zwischenspeicher an einem Speicherort erstellt, der von dem von Ihnen verwendeten Anwendungsserver abhängig ist:

* **JBoss:** `[JBoss Home]\server\[install type]\svcdata\Output\Cache`
* **WebLogic:** `[WebLogic Home]\user_projects\domains\[aem-forms domain Name]\adobe\[forms server name]\Output\Cache`
* **WebSphere:** `[IBM Home]\WebSphere\AppServer\installedApps\adobe\server1\Output\Cache`

**LC Temp Directory:** Der Cache wird in einem Unterverzeichnis des temporären Ordners für AEM Formulare erstellt, das in der Administration Console unter &quot;Einstellungen&quot;> &quot;Core-Systemeinstellungen&quot;> &quot;Konfigurationen&quot;> &quot;Speicherort des temporären Ordners&quot;angegeben ist. Der Unterordner heißt `adobeoutput_[servername]`.

>[!NOTE]
>
>Wenn Sie ein Bereinigungsprogramm für temporäre Dateien verwenden, beachten Sie, dass das Löschen dieser Ordner zwar keine Auswirkungen auf die Funktionalität hat; die Leistung kann jedoch kurzzeitig erheblich beeinträchtigt werden, bis der neue Zwischenspeicher erstellt ist. Um dieses Problem zu vermeiden, sollten Sie diese Ordner nicht löschen, während die temporären Ordner von AEM Forms gelöscht werden.
