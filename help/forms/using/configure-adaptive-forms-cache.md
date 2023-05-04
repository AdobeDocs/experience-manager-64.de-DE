---
title: Konfigurieren des Caches für adaptive Formulare
seo-title: Configure adaptive forms cache
description: Der Cache für adaptive Formulare wurde speziell für adaptive Formulare und Dokumente entwickelt. Adaptive Formulare und adaptive Dokumente werden zwischengespeichert, um die zum Rendern eines adaptiven Formulars oder Dokuments auf dem Client erforderliche Zeit zu reduzieren.
seo-description: The adaptive forms cache is designed specifically for adaptive forms and documents. It caches adaptive forms and adaptive documents with the objective of reducing the time required to render an adaptive form or document on the client.
uuid: 3bd4e405-1eab-4e02-95cd-eb6ac25d18e3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: dd18f7b5-882d-4e81-ab3d-85f1e5d74992
role: Admin
exl-id: 6a610e9d-beec-486d-b1d2-78b5fec44c52
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 49%

---

# Cache für adaptive Formulare konfigurieren {#configure-adaptive-forms-cache}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Cachen ist ein Mechanismus zum Verkürzen von Datenzugriffszeiten, zur Reduktion von Wartezeiten und zur Steigerung der Geschwindigkeit der Eingabe/Ausgabe (I/O). Der Cache für adaptive Formulare speichert nur HTML-Inhalte und JSON-Strukturen eines adaptiven Formulars, ohne dass vorausgefüllte Daten gespeichert werden. Dies hilft bei der Verkürzung der zum Rendern eines adaptiven Formulars oder Dokuments auf dem Client erforderlichen Zeit. Es wurde speziell für adaptive Formulare entwickelt und unterstützt auch adaptive Dokumente.

>[!NOTE]
>
>Verwenden Sie bei Verwendung des Cache für adaptive Formulare den AEM Dispatcher, um Client-Bibliotheken (CSS und JavaScript) eines adaptiven Formulars oder Dokuments zwischenzuspeichern.

>[!NOTE]
>
>Beim Entwickeln von benutzerdefinierten Komponenten muss auf dem für die Entwicklung verwendeten Server der Cache für adaptive Formulare deaktiviert bleiben.

## Cache konfigurieren {#configure-the-cache}

Führen Sie die folgenden Schritte aus, um den Cache für adaptive Formulare zu konfigurieren:

1. Wechseln Sie zum Konfigurations-Manager der AEM-Web-Konsole unter `https://[server]:[port]/system/console/configMgr`.
1. Klicken Sie auf **Konfiguration für adaptive Formulare und interaktiven Kommunikations-Web-Kanal**, um die Konfigurationswerte zu bearbeiten.
1. Geben Sie im Dialogfeld „Konfigurationswerte bearbeiten“ die maximale Anzahl von Formularen oder Dokumenten an, die eine Instanz des AEM Forms-Servers im Feld **Anzahl adaptiver Formulare** zwischenspeichern kann. Der Standardwert ist 100.

   >[!NOTE]
   >
   >Um den Cache zu deaktivieren, setzen Sie den Wert im Feld Anzahl adaptiver Forms auf **0**. Der Cache wird zurückgesetzt, und alle Formulare und Dokumente werden aus dem Cache entfernt, wenn Sie die Cachekonfiguration deaktivieren oder ändern.

   ![Dialogfeld für HTML-Cache für adaptive Formulare konfigurieren](assets/cache-configuration-edit.png)

1. Klicken Sie auf **Speichern**, um die Konfiguration zu speichern.
