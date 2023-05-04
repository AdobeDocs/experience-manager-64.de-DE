---
title: Konfigurieren von AEM-Apps
seo-title: Configuring for AEM Apps
description: Erfahren Sie, wie Sie AEM Apps konfigurieren.
seo-description: Learn how to configure AEM Apps.
uuid: ab9acd93-da7f-4bb7-8d26-224044899068
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 34f24837-f5e2-41f0-a359-fdb695e1b8f2
exl-id: 593a588c-02f1-4b48-ac57-9348d6652bcc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 61%

---

# Konfigurieren von AEM-Apps{#configuring-for-aem-apps}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Adobe Experience Manager-Apps stellen die Möglichkeit zur Over-the-Air(OTA)-Aktualisierung des Inhalts Ihrer Anwendung bereit. Die aktualisierten Inhalte werden in der Veröffentlichungsinstanz gespeichert. Damit die App auf Ihrem Gerät eine Verbindung zur Veröffentlichungsinstanz herstellen und nach Updates suchen kann, muss die Veröffentlichungsinstanz so konfiguriert werden, dass ein leerer Referrer-Header zulässig ist.

## Konfigurieren der Kopfzeile des leeren Referrers {#configuring-empty-referrer-header}

So konfigurieren Sie den Referrer-Filterdienst:

* Öffnen Sie die Apache Felix-Konsole (**Konfigurationen**) bei:
* https://&lt;Server>:&lt;Port-Nummer>/system/console/configMgr
* Melden Sie sich als admin an.
* Wählen Sie im Menü **Configurations**: *Apache Sling Referrer Filter*.
* Aktivieren Sie das Feld „Leeres Feld zulassen“, um leere/fehlende Referrer-Header zuzulassen.
* Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

![chlimage_1-58](assets/chlimage_1-58.png)

Weitere Informationen erhalten Sie unter [OSGi-Konfigurationseinstellungen](/help/sites-deploying/osgi-configuration-settings.md) und [Sicherheitsprüfliste – Probleme mit Site-übergreifenden Anforderungsfälschungen](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery).
