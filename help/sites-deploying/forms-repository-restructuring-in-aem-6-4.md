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
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 87%

---

# Forms-Repository-Neustrukturierung in AEM 6.4{#forms-repository-restructuring-in-aem}

Wie im übergeordneten Element beschrieben [Repository-Neustrukturierung in AEM 6.4](/help/sites-deploying/repository-restructuring.md) -Seite verwenden, sollten Kunden, die auf AEM 6.4 aktualisieren, diese Seite verwenden, um den Arbeitsaufwand im Zusammenhang mit Repository-Änderungen zu bewerten, die sich auf die AEM Forms-Lösung auswirken. Einige Änderungen erfordern einen Arbeitsaufwand während des Aktualisierungsprozesses auf AEM 6.4, während andere bis zu einer Aktualisierung auf 6.5 verschoben werden können.

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
| **Leitfaden für die Neustrukturierung** | Alle expliziten Verweise im benutzerdefinierten Code auf den alten Speicherort müssen an den neuen Speicherort aktualisiert werden. |
| **Anmerkungen** | Diese Client-Bibliotheken sollten nicht modifiziert oder erweitert werden. |

| **Vorheriger Speicherort** | `/etc/clientlibs/fd/rte` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/rte` |
| **Leitfaden für die Neustrukturierung** | Für die Ressourcen in den Client-Bibliotheken, die über absolute Pfade referenziert werden können, müssen Sie in neuen Assets neuere Pfade verwenden. |
| **Anmerkungen** | Nicht zutreffend |

| **Vorheriger Speicherort** | `/etc/clientlibs/fd/af` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/af/authoring/clientlibs` |
| **Leitfaden für die Neustrukturierung** | Für die Ressourcen in den Client-Bibliotheken, die über absolute Pfade referenziert werden können, müssen Sie in neuen Assets neuere Pfade verwenden. |
| **Anmerkungen** | Nicht zutreffend |

| **Vorheriger Speicherort** | `/etc/clientlibs/fd/xfaforms` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/xfaforms/clientlibs/` |
| **Leitfaden für die Neustrukturierung** | Für die Ressourcen in den Client-Bibliotheken, die über absolute Pfade referenziert werden können, müssen Sie in neuen Assets neuere Pfade verwenden. |
| **Anmerkungen** | Nicht zutreffend |

| **Vorheriger Speicherort** | `/etc/clientlibs/fd/af` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/af/runtime/clientlibs` |
| **Leitfaden für die Neustrukturierung** | Für die Ressourcen in den Client-Bibliotheken, die über absolute Pfade referenziert werden können, müssen Sie in neuen Assets neuere Pfade verwenden. |
| **Anmerkungen** | Nicht zutreffend |

| **Vorheriger Speicherort** | `/etc/clientlibs/fd/af` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/af/runtime/clientlibs` |
| **Leitfaden für die Neustrukturierung** | Für die Ressourcen in den Client-Bibliotheken, die über absolute Pfade referenziert werden können, müssen Sie in neuen Assets neuere Pfade verwenden. |
| **Anmerkungen** | Nicht zutreffend |

| **Vorheriger Speicherort** | `/etc/clientlibs/fd/expeditor` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/expeditor/clientlibs` |
| **Leitfaden für die Neustrukturierung** | Für die Ressourcen in den Client-Bibliotheken, die über absolute Pfade referenziert werden können, müssen Sie in neuen Assets neuere Pfade verwenden. |
| **Anmerkungen** | Nicht zutreffend |

| **Vorheriger Speicherort** | `/etc/clientlibs/fd/fmaddon` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/fmaddon` |
| **Leitfaden für die Neustrukturierung** | Das Ändern dieser Client-Bibliotheken wurde nie empfohlen oder unterstützt. Wenn Änderungen an diesen Client-Bibliotheken vorgenommen wurden, sollten diese auf den von AEM bereitgestellten Code zurückgesetzt werden. |
| **Anmerkungen** | Nicht zutreffend |

| **Vorheriger Speicherort** | `/etc/aep` |
|---|---|
| **Neuer Speicherort** | `/var/fd/content/annotations` |
| **Leitfaden für die Neustrukturierung** | Das Ändern dieser Client-Bibliotheken wurde nie empfohlen oder unterstützt. Wenn Änderungen an diesen Client-Bibliotheken vorgenommen wurden, sollten diese auf den von AEM bereitgestellten Code zurückgesetzt werden. |
| **Anmerkungen** | Nicht zutreffend |

## Vor der Aktualisierung auf 6.5 {#prior-to-upgrade}

### Echosign-Cloud-Service-Konfiguration {#echosign-cloud-service-configuration}

| **Vorheriger Speicherort** | `/etc/cloudservices/echosign` |
|---|---|
| **Neuer Speicherort** | `/conf/<tenant>/settings/cloudconfigs/echosign` |
| **Leitfaden für die Neustrukturierung** | Das Dienstprogramm [Erleichterte Inhaltsmigration](/help/sites-deploying/lazy-content-migration.md) wird von der Migrationsoberfläche von Forms ausgelöst. |
| **Anmerkungen** | Nicht zutreffend |

### Recaptcha-Cloud-Service-Konfigurationen {#recaptcha-cloud-service-configurations}

| **Vorheriger Speicherort** | `/etc/cloudservices/recaptcha` |
|---|---|
| **Neuer Speicherort** | `/conf/<tenant>/settings/cloudconfigs/recaptcha` |
| **Leitfaden für die Neustrukturierung** | Das Dienstprogramm [Erleichterte Inhaltsmigration](/help/sites-deploying/lazy-content-migration.md) wird von der Migrationsoberfläche von Forms ausgelöst. |
| **Anmerkungen** | Nicht zutreffend |

### Typekit-Cloud-Service-Konfigurationen {#typekit-cloud-service-configurations}

| **Vorheriger Speicherort** | `/etc/cloudservices/typekit` |
|---|---|
| **Neuer Speicherort** | `/conf/<tenant>/settings/cloudconfigs/typekit` |
| **Leitfaden für die Neustrukturierung** | Das Dienstprogramm [Erleichterte Inhaltsmigration](/help/sites-deploying/lazy-content-migration.md) wird von der Migrationsoberfläche von Forms ausgelöst. |
| **Anmerkungen** | Nicht zutreffend |

### Verschiedenes {#misc-1}

| **Vorheriger Speicherort** | `/etc/cloudservices/fdm` |
|---|---|
| **Neuer Speicherort** | `/conf/<tenant>/settings/cloudconfigs/fdm` |
| **Leitfaden für die Neustrukturierung** | Das Dienstprogramm [Erleichterte Inhaltsmigration](/help/sites-deploying/lazy-content-migration.md) wird von der Migrationsoberfläche von Forms ausgelöst. |
| **Anmerkungen** | Nicht zutreffend |

| **Vorheriger Speicherort** | `/etc/designs/fd/fp` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/fp` |
| **Leitfaden für die Neustrukturierung** | Alle Verweise auf die /etc-Vorlagen sollten schließlich aktualisiert werden, um auf ihre `/libs` Entsprechungen. |
| **Anmerkungen** | Nicht zutreffend |
