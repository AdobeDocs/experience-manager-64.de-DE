---
title: Tipps zum Minimieren des Datenbankwachstums
seo-title: Tips for minimizing database growth
description: Prozesse mit langer Lebensdauer speichern Prozessdaten in der AEM Formulardatenbank. Das Wachstum der AEM Forms-Datenbank kann mithilfe einiger einfacher Prozessdesign- und Produktkonfigurationsstrategien minimiert werden.
seo-description: Long-lived processes store process data in the AEM forms database. The growth of the AEM forms database can be minimized using a few easy process design and product configuration strategies.
uuid: 13f99d4f-848e-451e-90d9-55e202dc0bdb
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 89441336-babc-4d1f-9053-d1566cd42d22
exl-id: 7b266170-c7e2-42e7-8ee0-153e1e73a901
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 5%

---

# Tipps zum Minimieren des Datenbankwachstums {#tips-for-minimizing-database-growth}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Prozesse mit langer Lebensdauer speichern Prozessdaten in der AEM Formulardatenbank. Das Wachstum der AEM Forms-Datenbank kann mithilfe einiger einfacher Prozessdesign- und Produktkonfigurationsstrategien minimiert werden.

## Tipps zur Prozessgestaltung {#process-design-tips}

Verwenden Sie nach Möglichkeit kurzlebige Prozesse. In kurzlebigen Prozessen werden keine Prozessdaten in der Datenbank gespeichert. Der Nachteil kurzlebiger Prozesse besteht darin, dass ihr Status und Status nicht in Administration Console verfolgt werden und der Prozess nicht protokolliert wird.

Einige Dienstvorgänge wie der Vorgang &quot;Assign Task&quot;(User-Dienst) erfordern, dass sie in langlebigen Prozessen verwendet werden. In diesem Fall können Sie den Prozess in mehrere Teilprozesse unterteilen und nach Möglichkeit kurzlebig gestalten. Wenn Sie diese Strategie verwenden, sollten kurzlebige Teilprozesse große Datenelemente wie Dokumentwerte verarbeiten.

Verwenden Sie Variablen sparsam. Bei der Verwendung langlebiger Prozesse wird für jede Prozessinstanz der Datenbank für jede Variable im Prozess Speicherplatz zugewiesen. Die strategische Nutzung von Variablen kann viel Platz sparen. Sie können beispielsweise Variablenwerte überschreiben, wenn alte Werte im Prozess nicht mehr benötigt werden. Löschen Sie alle Variablen, die Sie erstellt haben und nicht verwenden. Sie können den Prozess validieren, um nicht verwendete Variablen zu finden.

Verwenden Sie einfache Variablentypen (z. B. Zeichenfolge oder int) und vermeiden Sie die Verwendung komplexer Variablentypen, wann immer möglich. Datenbankspeicherplatz wird Variablen zugewiesen, selbst wenn sie keinen Wert enthalten. Komplexe Variablen benötigen in der Regel mehr Platz als einfache.

## Tipps zur Produktverwaltung {#product-administration-tips}

Verwenden Sie den globalen Dokumentenspeicher (GDS) effektiv. Der Ordner des globalen Dokumentenspeichers auf dem Formularserver wird unter anderem zum Speichern von Dateien verwendet, die an Dienste übergeben werden, die Teil AEM Formulare in Prozessen sind. Zur Leistungsverbesserung werden kleinere Dokumente stattdessen im Arbeitsspeicher gespeichert und in der Datenbank beibehalten.

Administration Console stellt die Eigenschaft &quot;Default Document Max Inline Size&quot;zur Konfiguration der maximalen Größe von Dokumenten bereit, die im Speicher gespeichert und in der Datenbank beibehalten werden. (Siehe [Konfigurieren allgemeiner AEM Forms-Einstellungen](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings).) Wenn Sie diese Eigenschaft auf einen niedrigen Wert setzen, werden die meisten Dokumente im Ordner des globalen Dokumentenspeichers und nicht in der Datenbank beibehalten. Der Vorteil besteht darin, dass Sie die Dateien leichter löschen können, wenn sie nicht mehr benötigt werden, wenn sie im Ordner des globalen Dokumentenspeichers gespeichert sind.
