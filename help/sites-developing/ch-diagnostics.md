---
title: ContextHub-Diagnosen
seo-title: ContextHub Diagnostics
description: ContextHub bietet eine Diagnoseseite, auf der Sie einen Überblick über das ContextHub-Framework erhalten.
seo-description: ContextHub provides a diagnostics page where you can see an overview of the ContextHub framework
uuid: 94ef0696-3977-4781-ad32-9f4f117eb096
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 6aa88583-5d34-4f77-a932-d47d84785eca
exl-id: 31926737-1a06-4fb9-b851-665095954875
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 100%

---

# ContextHub-Diagnosen {#contexthub-diagnostics}

ContextHub bietet eine Diagnoseseite, auf der Sie einen Überblick über das ContextHub-Framework erhalten. Um die Seite zu öffnen, gehen Sie zur `contexthub.diagnostics.html`-Seite Ihrer AEM-Autorenrinstanz, z. B.:

`http://<host>:<port>/conf/<tenant>/settings/cloudsettings/default/contexthub.diagnostics.html`

Die „Seite ContextHub-Diagnose“ enthält Informationen zu den erstellten Stores und Benutzeroberflächenmodulen, den geladenen Client-Bibliotheksordnern und Links zu nützlichen Seiten.

>[!NOTE]
>
>Damit Diagnoseinformationen zurückgegeben werden können, muss der Debug-Modus aktiviert sein, da andernfalls die Diagnoseseite leer ist. In [diesem Dokument](/help/sites-administering/contexthub-config.md#debugging-contexthub) finden Sie Details zum Aktivieren des Debug-Modus.

>[!NOTE]
>
>Für ContextHub-Konfigurationen, die sich noch unter ihren alten Pfaden befinden, befindet sich die Diagnoseseite unter `http://<host>:<port>/libs/settings/cloudsettings/legacy/contexthub.diagnostics.html`.

## Stores {#stores}

Der Abschnitt „Stores“ listet alle ContextHub-Stores auf, die konfiguriert wurden. Jedes Element in der Liste besteht aus folgenden Informationen:

* **Title:** Der [Store-Typ](/help/sites-developing/ch-samplestores.md), auf dem der Store basiert.
* **path:** Der Pfad zum Repository-Knoten, der die Konfiguration enthält.
* **resourceType:** Der Pfad des Repository-Knotens, in dem der Storetyp definiert ist.
* **clientlibs:** Die Kategorien der geladenen Client-Bibliotheken, die den Storetyp implementieren.

## Modules {#modules}

Der Abschnitt „Modules“ listet alle ContextHub Benutzeroberflächenmodule auf, die konfiguriert wurden. Jedes Element in der Liste besteht aus folgenden Informationen:

* **Title:** Der [Benutzeroberflächenmodultyp](/help/sites-developing/ch-samplemodules.md), auf dem das Benutzeroberflächenmodul basiert.
* **path:** Der Pfad zum Repository-Knoten, der die Konfiguration enthält.
* **resourceType:** Der Pfad des Repository-Knotens, in dem der Benutzeroberflächenmodultyp definiert ist.
* **clientlibs:** Die Kategorien der geladenen Client-Bibliotheken, die den Benutzeroberflächenmodultyp implementieren.

## Clientlibs {#clientlibs}

Der Abschnitt „Clientlibs“ listet alle Ordner der Client-Bibliothek auf, die ContextHub geladen hat. Die Client-Bibliotheken sind kategorisiert:

* **kernel.js:** Client-Bibliotheken, die das ContextHub-Framework, die Segment-Engine und Storetypen implementieren.
* **ui.js:** Client-Bibliotheken, die die ContextHub-Benutzeroberfläche und Benutzeroberflächenmodultypen implementieren.
* **style.css:** CSS-Dateien, die aus Client-Bibliotheken geladen werden.

## URLs {#urls}

Der Abschnitt „URLs“ enthält Links zu ContextHub-Features:

* **Konfigurationseditor:** Öffnet die [ContextHub-Konfigurationsseite](/help/sites-administering/contexthub-config.md), wo Sie Stores, Benutzeroberflächenmodi und Benutzeroberflächenmodule konfigurieren können.

* **Konfigurieren von ContextHub-Modulen:** Öffnet die Datei /etc/cloudsettings/default/contexthub.config.kernel.js, die die JavaScript-Objektdarstellung der ContextHub-Store-Konfigurationen enthält.
* **Konfigurieren der ContextHub-Benutzeroberfläche:** Öffnet die Datei /etc/cloudsettings/default/contexthub.config.ui.js, die die JavaScript-Objektdarstellung der ContextHub-Benutzeroberflächenmoduskonfigurationen enthält.
* **kernel.js:** Öffnet die Datei /etc/cloudsettings/default/contexthub.kernel.js, die den Quell-Code der Client-Bibliotheken enthält, welche das ContextHub-Framework, die Segment-Engine und die Speichertypen implementieren.
* **ui.js:** Öffnet die Datei /etc/cloudsettings/default/ contexthub.ui.js, die den Quell-Code der Client-Bibliotheken enthält, welche die ContextHub-Benutzeroberfläche und Benutzeroberflächenmodultypen implementieren.
* **style.css:** Öffnet die Datei /etc/cloudsettings/default/contexthub.styles.css, die die CSS-Stile für die ContextHub-Benutzeroberfläche und Benutzeroberflächenmodule enthält.
