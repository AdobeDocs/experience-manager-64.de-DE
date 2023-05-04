---
title: Forms-Repository-Neustrukturierung in AEM 6.4
seo-title: Forms Repository Restructuring in AEM 6.4
description: Erfahren Sie, wie Sie die erforderlichen Änderungen vornehmen können, um die neue Repository-Struktur in AEM 6.4 für Forms zu migrieren.
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.4 for Forms.
uuid: e60830d4-23ca-4be9-941a-ee4abe4786a6
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 1ce9a622-5968-407f-a74b-d325a2bff669
feature: Upgrading
exl-id: a2d6524e-3f5b-4d1e-af64-61ff95889657
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 50%

---

# Forms-Repository-Neustrukturierung in AEM 6.4{#forms-repository-restructuring-in-aem}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Wie auf der übergeordneten Seite [Repository-Neustrukturierung in AEM 6.4](/help/sites-deploying/repository-restructuring.md) beschrieben, sollten Kunden, die ein Upgrade auf AEM 6.4 durchführen, diese Seite nutzen, um den Arbeitsaufwand im Zusammenhang mit Repository-Änderungen abzuschätzen, die sich auf AEM Forms Solution auswirken. Einige Änderungen erfordern während des Aktualisierungsprozesses von AEM 6.4 Arbeitsaufwand, während andere bis zu einem Upgrade auf 6.5 verschoben werden können.

**Mit der Aktualisierung auf 6.4**

* [Verschiedenes](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#misc)

**Vor der Aktualisierung auf 6.5**

* [Echosign-Cloud-Service-Konfiguration](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#echosign-cloud-service-configuration)
* [Recaptcha-Cloud-Service-Konfigurationen](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#recaptcha-cloud-service-configurations)
* [Typekit-Cloud-Service-Konfigurationen](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#typekit-cloud-service-configurations)
* [Verschiedenes](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#misc)

## Mit der Aktualisierung auf 6.4 {#with-upgrade}

### Verschiedenes {#misc}

| **Vorheriger Speicherort** | `/etc/clientlibs/fd/fp` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/fp/components` |
| **Leitfaden für die Neustrukturierung** | Alle expliziten Verweise im benutzerdefinierten Code auf den alten Speicherort müssen auf den neuen Speicherort aktualisiert werden. |
| **Anmerkungen** | Diese Client-Bibliotheken sollten nicht geändert oder erweitert werden. |

| **Vorheriger Speicherort** | `/etc/clientlibs/fd/rte` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/rte` |
| **Leitfaden für die Neustrukturierung** | Für die Ressourcen in den Client-Bibliotheken, die durch absolute Pfade referenziert werden können, müssen Sie neuere Pfade in neuen Assets verwenden. |
| **Anmerkungen** | Nicht zutreffend |

| **Vorheriger Speicherort** | `/etc/clientlibs/fd/af` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/af/authoring/clientlibs` |
| **Leitfaden für die Neustrukturierung** | Für die Ressourcen in den Client-Bibliotheken, die durch absolute Pfade referenziert werden können, müssen Sie neuere Pfade in neuen Assets verwenden. |
| **Anmerkungen** | Nicht zutreffend |

| **Vorheriger Speicherort** | `/etc/clientlibs/fd/xfaforms` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/xfaforms/clientlibs/` |
| **Leitfaden für die Neustrukturierung** | Für die Ressourcen in den Client-Bibliotheken, die durch absolute Pfade referenziert werden können, müssen Sie neuere Pfade in neuen Assets verwenden. |
| **Anmerkungen** | Nicht zutreffend |

| **Vorheriger Speicherort** | `/etc/clientlibs/fd/af` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/af/runtime/clientlibs` |
| **Leitfaden für die Neustrukturierung** | Für die Ressourcen in den Client-Bibliotheken, die durch absolute Pfade referenziert werden können, müssen Sie neuere Pfade in neuen Assets verwenden. |
| **Anmerkungen** | Nicht zutreffend |

| **Vorheriger Speicherort** | `/etc/clientlibs/fd/af` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/af/runtime/clientlibs` |
| **Leitfaden für die Neustrukturierung** | Für die Ressourcen in den Client-Bibliotheken, die durch absolute Pfade referenziert werden können, müssen Sie neuere Pfade in neuen Assets verwenden. |
| **Anmerkungen** | Nicht zutreffend |

| **Vorheriger Speicherort** | `/etc/clientlibs/fd/expeditor` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/expeditor/clientlibs` |
| **Leitfaden für die Neustrukturierung** | Für die Ressourcen in den Client-Bibliotheken, die durch absolute Pfade referenziert werden können, müssen Sie neuere Pfade in neuen Assets verwenden. |
| **Anmerkungen** | Nicht zutreffend |

| **Vorheriger Speicherort** | `/etc/clientlibs/fd/fmaddon` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/fmaddon` |
| **Leitfaden für die Neustrukturierung** | Das Ändern dieser Client-Bibliotheken wurde nie empfohlen oder unterstützt. Wenn Änderungen an diesen Client-Bibliotheken vorgenommen wurden, sollten sie zurückgesetzt werden, um den AEM Code zu verwenden. |
| **Anmerkungen** | Nicht zutreffend |

| **Vorheriger Speicherort** | `/etc/aep` |
|---|---|
| **Neuer Speicherort** | `/var/fd/content/annotations` |
| **Leitfaden für die Neustrukturierung** | Das Ändern dieser Client-Bibliotheken wurde nie empfohlen oder unterstützt. Wenn Änderungen an diesen Client-Bibliotheken vorgenommen wurden, sollten sie zurückgesetzt werden, um den AEM Code zu verwenden. |
| **Anmerkungen** | Nicht zutreffend |

## Vor der Aktualisierung auf 6.5 {#prior-to-upgrade}

### Echosign-Cloud-Service-Konfiguration {#echosign-cloud-service-configuration}

| **Vorheriger Speicherort** | `/etc/cloudservices/echosign` |
|---|---|
| **Neuer Speicherort** | `/conf/<tenant>/settings/cloudconfigs/echosign` |
| **Leitfaden für die Neustrukturierung** | Die [Lazy-Content-Migration](/help/sites-deploying/lazy-content-migration.md) -Dienstprogramm, das über die Forms-Migrationsbenutzeroberfläche ausgelöst werden soll. |
| **Anmerkungen** | Nicht zutreffend |

### Recaptcha-Cloud-Service-Konfigurationen {#recaptcha-cloud-service-configurations}

| **Vorheriger Speicherort** | `/etc/cloudservices/recaptcha` |
|---|---|
| **Neuer Speicherort** | `/conf/<tenant>/settings/cloudconfigs/recaptcha` |
| **Leitfaden für die Neustrukturierung** | Die [Lazy-Content-Migration](/help/sites-deploying/lazy-content-migration.md) -Dienstprogramm, das über die Forms-Migrationsbenutzeroberfläche ausgelöst werden soll. |
| **Anmerkungen** | Nicht zutreffend |

### Typekit-Cloud-Service-Konfigurationen {#typekit-cloud-service-configurations}

| **Vorheriger Speicherort** | `/etc/cloudservices/typekit` |
|---|---|
| **Neuer Speicherort** | `/conf/<tenant>/settings/cloudconfigs/typekit` |
| **Leitfaden für die Neustrukturierung** | Die [Lazy-Content-Migration](/help/sites-deploying/lazy-content-migration.md) -Dienstprogramm, das über die Forms-Migrationsbenutzeroberfläche ausgelöst werden soll. |
| **Anmerkungen** | Nicht zutreffend |

### Verschiedenes {#misc-1}

| **Vorheriger Speicherort** | `/etc/cloudservices/fdm` |
|---|---|
| **Neuer Speicherort** | `/conf/<tenant>/settings/cloudconfigs/fdm` |
| **Leitfaden für die Neustrukturierung** | Die [Lazy-Content-Migration](/help/sites-deploying/lazy-content-migration.md) -Dienstprogramm, das über die Forms-Migrationsbenutzeroberfläche ausgelöst werden soll. |
| **Anmerkungen** | Nicht zutreffend |

| **Vorheriger Speicherort** | `/etc/designs/fd/fp` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/fp` |
| **Leitfaden für die Neustrukturierung** | Alle Verweise auf die /etc-Vorlagen müssen schließlich so aktualisiert werden, dass sie auf ihre `/libs`-Gegenstücke verweisen. |
| **Anmerkungen** | Nicht zutreffend |
