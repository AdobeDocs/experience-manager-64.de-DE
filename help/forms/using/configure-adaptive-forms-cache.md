---
title: Cache für adaptive Formulare konfigurieren
seo-title: Configure adaptive forms cache
description: Der Cache für adaptive Formulare wurde speziell für adaptive Formulare und Dokumente entworfen. Adaptive Formulare und adaptive Dokumente werden zwischengespeichert, um die Zeit zu minimieren, die zum Rendern eines adaptiven Formulars oder Dokuments auf dem Client notwendig ist.
seo-description: The adaptive forms cache is designed specifically for adaptive forms and documents. It caches adaptive forms and adaptive documents with the objective of reducing the time required to render an adaptive form or document on the client.
uuid: 3bd4e405-1eab-4e02-95cd-eb6ac25d18e3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: dd18f7b5-882d-4e81-ab3d-85f1e5d74992
role: Admin
exl-id: 6a610e9d-beec-486d-b1d2-78b5fec44c52
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 100%

---

# Cache für adaptive Formulare konfigurieren {#configure-adaptive-forms-cache}

Cachen ist ein Mechanismus zum Verkürzen von Datenzugriffszeiten, zur Reduktion von Wartezeiten und zur Steigerung der Geschwindigkeit der Eingabe/Ausgabe (I/O). Cache für adaptive Formulare speichert nur HTML-Inhalte und JSON-Strukturen eines adaptiven Formulars, ohne die vorausgefüllten Daten zu speichern. Die Zeit, die benötigt wird, um ein adaptives Formular oder ein Dokument auf dem Client zu rendern, wird reduziert. Es wurde speziell für adaptive Formulare und adaptive Dokumente entworfen.

>[!NOTE]
>
>Wenn Sie den Cache für adaptive Formulare verwenden, nutzen Sie den AEM-Dispatcher, um Client-Bibliotheken (CSS und JavaScript) eines adaptiven Formulars oder Dokuments zwischenzuspeichern.

>[!NOTE]
>
>Beim Entwickeln von benutzerdefinierten Komponenten muss auf dem für die Entwicklung verwendeten Server der Cache für adaptive Formulare deaktiviert bleiben.

## Cache konfigurieren  {#configure-the-cache}

Führen Sie die folgenden Schritte aus, um den Cache für adaptive Formulare zu konfigurieren:

1. Wechseln Sie zum Konfigurations-Manager der AEM-Web-Konsole unter `https://[server]:[port]/system/console/configMgr`.
1. Klicken Sie auf **Konfiguration für adaptive Formulare und interaktiven Kommunikations-Web-Kanal**, um die Konfigurationswerte zu bearbeiten.
1. Geben Sie im Dialogfeld „Konfigurationswerte bearbeiten“ die maximale Anzahl von Formularen oder Dokumenten an, die eine Instanz des AEM Forms-Servers im Feld **Anzahl adaptiver Formulare** zwischenspeichern kann. Der Standardwert ist 100.

   >[!NOTE]
   >
   >Um den Cache zu deaktivieren, legen Sie den Wert für die Anzahl adaptiver Formulare auf **0** fest. Der Cache wird zurückgesetzt, und alle Formulare und Dokumente werden aus dem Cache entfernt, wenn Sie die Cachekonfiguration deaktivieren oder ändern.

   ![Dialogfeld für HTML-Cache für adaptive Formulare konfigurieren](assets/cache-configuration-edit.png)

1. Klicken Sie auf **Speichern**, um die Konfiguration zu speichern.
