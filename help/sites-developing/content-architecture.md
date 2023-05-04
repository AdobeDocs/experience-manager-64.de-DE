---
title: Inhaltsarchitektur
seo-title: Content Architecture
description: 'Tipps für die Entwicklung einer Inhaltsarchitektur (Hinweis: Alles ist Inhalt.)'
seo-description: Tips for architecting your content in Adobe Experience Manager (AEM). (hint - everything is content)
uuid: fef2bf0f-70ec-4621-8479-a62b7e1fbc07
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: ca46b74c-6114-458b-98c0-2a93abffcdc3
exl-id: 9fff10fb-4b65-459a-a7a7-6ee9c0c26bf5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 68%

---

# Inhaltsarchitektur{#content-architecture}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## David&#39;s Modell folgen {#follow-david-s-model}

„David’s Model“ wurde vor Jahren von David Nuescheler entworfen, hat aber bis heute Gültigkeit. Die wichtigsten Grundsätze des Modells lauten:

* Erst die Daten, dann die Struktur. Zumindest gegebenenfalls.
* Steuern Sie die Content-Hierarchie, anstatt sie dem Zufall zu überlassen.
* Workspaces sind für `clone()`, `merge()` und `update()` vorgesehen.
* Vorsicht vor gleichnamigen Geschwistern.
* Verweise gelten als schädlich.
* Dateien sind Dateien.
* IDs sind zu vermeiden.

„David’s Model“ finden Sie im Jackrabbit-Wiki unter [https://wiki.apache.org/jackrabbit/DavidsModel](https://wiki.apache.org/jackrabbit/DavidsModel).

### Alles ist Inhalt {#everything-is-content}

Alles sollte im Repository gespeichert werden, anstatt sich auf separate Datenquellen von Drittanbietern wie Datenbanken zu verlassen. Dies gilt für erstellte Inhalte, Binärdaten wie Bilder, Code, Konfigurationen usw. Auf diese Weise können wir eine Reihe von APIs verwenden, um alle Inhalte zu verwalten und die Promotion dieses Inhalts durch Replikation zu verwalten. Wir erhalten auch eine einzige Quelle für Backup, Protokollierung usw.

### Verwenden des Designprinzips &quot;Inhaltsmodell zuerst&quot; {#use-the-content-model-first-design-principle}

Wenn Sie eine neue Funktion entwickeln, beginnen Sie immer damit, zunächst die JCR-Inhaltsstruktur zu entwerfen. Befassen Sie sich dann erst mit dem Lesen und Schreiben Ihrer Inhalte mithilfe der standardmäßigen Sling-Servlets. Auf diese Weise können Sie sicherstellen, dass Ihre Implementierung problemlos mit Standardmechanismen für die Zugriffssteuerung funktioniert, und darüber hinaus die Erstellung überflüssiger Servlets im CRUD-Stil vermeiden.

### RESTful statt Panik {#be-restful}

Servlets sollten auf Basis von Ressourcentypen anstelle von Pfaden definiert werden. Dies ermöglicht die Verwendung von JCR-Zugriffssteuerungen, die Anwendung der REST-Prinzipien und die Verwendung der Ressource und des Ressourcen-Resolvers, die in der Anforderung bereitgestellt werden. Damit lassen sich außerdem die Skripte ändern, die URLs auf Serverseite rendern, ohne die URLs auf Client-Seite ändern zu müssen, während die serverseitigen Implementierungsdetails vor dem Client verborgen werden, um die Sicherheit zu erhöhen.

### Vermeiden der Definition neuer Knotentypen {#avoid-defining-new-node-types}

Knotentypen setzen auf einer niedrigen Ebene der Infrastrukturschicht an und die meisten Anforderungen können erfüllt werden, indem ein „sling:resourceType“ verwendet wird, der einem Knotentyp „nt:unstructured“, „oak:Unstructured“, „sling:Folder“ oder „cq:Page“ zugewiesen ist. Knotentypen entsprechen dem Schema im Repository und das Ändern von Knotentypen kann sich äußerst aufwendig gestalten.

### Einhalten Sie Namenskonventionen im JCR {#adhere-to-naming-conventions-in-the-jcr}

Durch die Einhaltung von Namenskonventionen wird die Konsistenz der Codebasis erhöht, die Fehler-Inzidenzrate gesenkt und der Arbeitsprozess der beteiligten Entwickler beschleunigt. Adobe wendet die folgenden Konventionen bei der Entwicklung von AEM an:

* Knotennamen

   * Kleinbuchstaben
   * Worttrennung mithilfe von Bindestrichen

* Eigenschaftsnamen

   * Groß-/Kleinschreibung, beginnend mit einem Kleinbuchstaben

* Komponenten (JSP/HTML)

   * Kleinbuchstaben
   * Worttrennung mithilfe von Bindestrichen
