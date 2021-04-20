---
title: Cache für adaptive Formulare konfigurieren
seo-title: Cache für adaptive Formulare konfigurieren
description: 'Der Cache für adaptive Formulare wurde speziell für adaptive Formulare und Dokumente entworfen. Adaptive Formulare und adaptive Dokumente werden zwischengespeichert, um die Zeit zu minimieren, die zum Rendern eines adaptiven Formulars oder Dokuments auf dem Client notwendig ist. '
seo-description: 'Der Cache für adaptive Formulare wurde speziell für adaptive Formulare und Dokumente entworfen. Adaptive Formulare und adaptive Dokumente werden zwischengespeichert, um die Zeit zu minimieren, die zum Rendern eines adaptiven Formulars oder Dokuments auf dem Client notwendig ist. '
uuid: 3bd4e405-1eab-4e02-95cd-eb6ac25d18e3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: dd18f7b5-882d-4e81-ab3d-85f1e5d74992
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 87%

---


# Cache für adaptive Formulare konfigurieren {#configure-adaptive-forms-cache}

Eine Cache ist ein Vorgang, um Datenzugriffzeiten zu verkürzen, die Wartezeit zu reduzieren, und die Geschwindigkeit von Eingabe/Ausgabe (I/A) zu verbessern. Cache für adaptive Formulare speichert nur HTML-Inhalte und JSON-Strukturen eines adaptiven Formulars, ohne die vorausgefüllten Daten zu speichern. Die Zeit, die benötigt wird, um ein adaptives Formular oder ein Dokument auf dem Client zu rendern, wird reduziert. Es wurde speziell für adaptive Formulare und adaptive Dokumente entworfen.

>[!NOTE]
>
>Wenn Sie den Cache für adaptive Formulare verwenden, nutzen Sie den AEM-Dispatcher, um Client-Bibliotheken (CSS und JavaScript) eines adaptiven Formulars oder Dokuments zwischenzuspeichern.

>[!NOTE]
>
>Beim Entwickeln der benutzerdefinierten Komponenten muss auf dem für die Entwicklung verwendeten Server der Cache für adaptive Formulare deaktiviert bleiben.

## Cache konfigurieren  {#configure-the-cache}

Führen Sie die folgenden Schritte aus, um den Cache für adaptive Formulare zu konfigurieren:

1. Gehen Sie zu AEM Web Console Configuration Manager unter `https://[server]:[port]/system/console/configMgr`.
1. Klicken Sie auf **Konfiguration für adaptive Formulare und interaktiver Kommunikationswebkanal**, um die Konfigurationswerte zu bearbeiten.
1. Geben Sie im Dialogfeld &quot;Konfigurationswerte bearbeiten&quot;die maximale Anzahl von Formularen oder Dokumenten an, die eine Instanz des AEM Forms-Servers im Feld **Anzahl der adaptiven Forms** zwischenspeichern kann. Der Standardwert ist 100. 

   >[!NOTE]
   >
   >Um den Cache zu deaktivieren, legen Sie den Wert für die Anzahl adaptiver Formulare auf **0** fest. Der Cache wird zurückgesetzt und alle Formulare und Dokumente werden aus dem Cache entfernt, wenn Sie die Cachekonfiguration deaktivieren oder ändern.

   ![Dialogfeld für HTML-Cache für adaptive Formulare konfigurieren](assets/cache-configuration-edit.png)

1. Klicken Sie auf **Speichern**, um die Konfiguration zu speichern.

