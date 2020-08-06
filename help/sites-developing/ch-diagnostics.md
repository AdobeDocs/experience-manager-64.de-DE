---
title: ContextHub-Diagnosen
seo-title: ContextHub-Diagnosen
description: ContextHub bietet eine Diagnoseseite, auf der Sie einen Überblick über das ContextHub-Framework erhalten
seo-description: ContextHub bietet eine Diagnoseseite, auf der Sie einen Überblick über das ContextHub-Framework erhalten
uuid: 94ef0696-3977-4781-ad32-9f4f117eb096
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 6aa88583-5d34-4f77-a932-d47d84785eca
translation-type: tm+mt
source-git-commit: 39b6af8ee815e8f6fa6e0b4a0a6dc80f29165243
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 63%

---


# ContextHub-Diagnosen {#contexthub-diagnostics}

ContextHub bietet eine Diagnoseseite, auf der Sie einen Überblick über das ContextHub-Framework erhalten To open the page, go to the `contexthub.diagnostics.html` page of your AEM author instance, for example:

`http://<host>:<port>/conf/<tenant>/settings/cloudsettings/default/contexthub.diagnostics.html`

Die „Seite ContextHub-Diagnose“ enthält Informationen zu den erstellten Stores und Benutzeroberflächenmodulen, den geladenen Client-Bibliotheksordnern und Links zu nützlichen Seiten.

>[!NOTE]
>
>Damit Diagnoseinformationen zurückgegeben werden können, muss der Debug-Modus aktiviert sein, da andernfalls die Diagnoseseite leer ist. In [diesem Dokument](/help/sites-administering/contexthub-config.md#debugging-contexthub) finden Sie Details zum Aktivieren des Debug-Modus.

>[!NOTE]
>
>Bei ContextHub-Konfigurationen, die sich noch unter ihren alten Pfaden befinden, befindet sich der Speicherort der Diagnoseseite `http://<host>:<port>/libs/settings/cloudsettings/legacy/contexthub.diagnostics.html`.

## Stores {#stores}

Der Abschnitt „Stores“ listet alle ContextHub-Stores auf, die konfiguriert wurden. Jedes Element in der Liste besteht aus folgenden Informationen:

* **Title:** Der[ Storetyp](/help/sites-developing/ch-samplestores.md), auf dem der Store basiert.
* **path:** Der Pfad zum Repository-Knoten, der die Konfiguration enthält.
* **resourceType:** Der Pfad des Repository-Knotens, in dem der Storetyp definiert ist.
* **clientlibs:** Die Kategorien der geladenen Client-Bibliotheken, die den Storetyp implementieren.

## Modules {#modules}

Der Abschnitt „Modules“ listet alle ContextHub Benutzeroberflächenmodule auf, die konfiguriert wurden. Jedes Element in der Liste besteht aus folgenden Informationen:

* **Titel:** Der [UI-Modultyp](/help/sites-developing/ch-samplemodules.md) , auf dem das UI-Modul basiert.
* **path:** Der Pfad zum Repository-Knoten, der die Konfiguration enthält.
* **resourceType:** Der Pfad des Repository-Knotens, in dem der Benutzeroberflächenmodultyp definiert ist.
* **clientlibs:** Die Kategorien der geladenen Client-Bibliotheken, die den Benutzeroberflächenmodultyp implementieren.

## Clientlibs {#clientlibs}

Der Abschnitt „Clientlibs“ listet alle Ordner der Client-Bibliothek auf, die ContextHub geladen hat. Die Client-Bibliotheken sind kategorisiert:

* **kernel.js:** Client-Bibliotheken, die das ContextHub-Framework, die Segment-Engine und Storetypen implementieren.
* **ui.js:** Client-Bibliotheken, die die ContextHub-Benutzeroberfläche und Benutzeroberflächenmodultypen implementieren.
* **style.css:** CSS-Dateien, die aus Client-Bibliotheken geladen werden.

## URLs     {#urls}

Der Abschnitt „URLs“ enthält Links zu ContextHub-Features:

* **Konfigurationseditor:** Öffnet die Seite &quot; [ContextHub-Konfiguration&quot;](/help/sites-administering/contexthub-config.md) , auf der Sie Stores, UI-Modi und UI-Module konfigurieren können.

* **Konfiguration der ContextHub-Module:** Öffnet die Datei /etc/cloudsettings/default/contexthub.config.kernel.js, die die Javascript-Objektdarstellung der ContextHub-Speicherkonfigurationen enthält.
* **Konfiguration der ContextHub-Benutzeroberfläche:** Öffnet die Datei /etc/cloudsettings/default/contexthub.config.ui.js, die die Javascript-Objektdarstellung der ContextHub-UI-Moduskonfigurationen enthält.
* **kernel.js:** Öffnet die Datei &quot;/etc/cloudsettings/default/contexthub.kernel.js&quot;, die den Quellcode der Client-Bibliotheken enthält, die das ContextHub-Framework, die Segment-Engine und die Store-Typen implementieren.
* **ui.js:** Öffnet die Datei /etc/cloudsettings/default/contexthub.ui.js, die den Quellcode der Clientbibliotheken enthält, die die ContextHub-UI- und UI-Modultypen implementieren.
* **style.css:** Öffnet die Datei &quot;/etc/cloudsettings/default/contexthub.styles.css&quot;, die die CSS-Stile für die ContextHub-UI- und -UI-Module enthält.
