---
title: Übersicht über den Speicheranbieter
seo-title: Storage Resource Provider Overview
description: Gemeinsame Speicherung für Communities
seo-description: Common storage for Communities
uuid: abdf4e5a-767b-428f-9aa4-0dc06819a26e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 63abeda4-6ea1-4b45-b188-f9c6b44ca0cd
exl-id: 17105abe-177b-4e73-bb4f-22b208c436ef
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1189'
ht-degree: 2%

---

# Übersicht über den Speicheranbieter {#storage-resource-provider-overview}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Einführung {#introduction}

Ab AEM Communities 6.1 werden Community-Inhalte, häufig als benutzergenerierte Inhalte bezeichnet, in einem einzigen, gemeinsamen Speicher gespeichert, der von einem [Speicherressourcenanbieter](working-with-srp.md) (SRP).

Es gibt mehrere SRP-Optionen, die alle über eine neue AEM Communities-Oberfläche auf UGC zugreifen: [SocialResourceProvider-API](srp-and-ugc.md) (SRP-API), die alle CRUD-Vorgänge (Erstellen, Lesen, Aktualisieren und Löschen) umfasst.

Alle SCF-Komponenten werden mithilfe der SRP-API implementiert, sodass Code ohne Kenntnis der [zugrunde liegende Topologie](topologies.md) oder Standort der UGC.

***Die SocialResourceProvider-API steht nur lizenzierten Kunden von AEM Communities zur Verfügung.***

>[!NOTE]
>
>**Benutzerdefinierte Komponenten**: Für lizenzierte Kunden von AEM Communities ist die SRP-API für Entwickler von benutzerdefinierten Komponenten verfügbar, um ungeachtet der zugrunde liegenden Topologie auf UGC zugreifen zu können. Siehe [Grundlagen zu SRP und UGC](srp-and-ugc.md).

Siehe auch:

* [Grundlagen zu SRP und UGC](srp-and-ugc.md) - SRP-Anwendungsmethoden und -Beispiele
* [Zugreifen auf UGC mit SRP](accessing-ugc-with-srp.md) - Kodierungsrichtlinien
* [SocialUtils-Refaktorierung](socialutils.md) - Zuordnen von nicht mehr unterstützten Methoden zu aktuellen SRP-Dienstprogrammmethoden

## Über das Repository {#about-the-repository}

Um SRP zu verstehen, ist es hilfreich, die Rolle des AEM-Repositorys (OAK) auf einer AEM Community-Site zu verstehen.

**Java Content Repository (JCR)**
Dieser Standard definiert ein Datenmodell und eine Anwendungsprogrammierschnittstelle ([JCR-API](https://jackrabbit.apache.org/jcr/jcr-api.html)) für Inhalts-Repositorys. Es kombiniert die Eigenschaften herkömmlicher Dateisysteme mit denen relationaler Datenbanken und bietet eine Reihe zusätzlicher Funktionen, die Content-Anwendungen häufig benötigen.

Eine Implementierung von JCR ist das AEM Repository, OAK.

**Apache Jackrabbit Oak (OAK)**
[OAK](../../help/sites-deploying/platform.md) ist eine Implementierung von JCR 2.0, einem Datenspeichersystem, das speziell für inhaltsorientierte Anwendungen entwickelt wurde. Es handelt sich um eine hierarchische Datenbank, die für unstrukturierte und teilstrukturierte Daten entwickelt wurde. Das Repository speichert nicht nur den für die Benutzenden sichtbaren Inhalt, sondern auch den gesamten Code, die Vorlagen und die internen Daten, die von der Anwendung verwendet werden. Die Benutzeroberfläche für den Zugriff auf Inhalte lautet [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md).

Sowohl JCR als auch OAK werden normalerweise verwendet, um auf das AEM Repository zu verweisen.

Nachdem Sie Site-Inhalte in der privaten Autorenumgebung entwickelt haben, müssen Sie sie durch Kopieren in die öffentliche Veröffentlichungsumgebung kopieren. Dies geschieht oft durch einen Vorgang namens *[Replikation](deploy-communities.md#replication-agents-on-author)*. Dies geschieht unter der Kontrolle des Autors/Entwicklers/Administrators.

Für UGC wird der Inhalt von registrierten Site-Besuchern (Community-Mitgliedern) in der öffentlichen Veröffentlichungsumgebung eingegeben. Dies geschieht zufällig.

Für die Verwaltung und Berichterstellung ist es nützlich, von der privaten Autorenumgebung aus Zugriff auf UGC zu haben. Mit SRP ist der Zugriff auf UGC vom Autor konsistenter und leistungsfähiger, da die Rückwärtsreplikation von der Veröffentlichung zum Autor nicht erforderlich ist.

## Über SRP {#about-srp}

Wenn UGC im freigegebenen Speicher gespeichert wird, gibt es eine einzelne Instanz von Mitgliederinhalten, auf die in den meisten Bereitstellungen sowohl von der Autoren- als auch der Veröffentlichungsumgebung aus zugegriffen werden kann. Unabhängig von der SRP-Auswahl (MSRP, ASRP, JSRP) muss über die SRP-API programmgesteuert auf alle zugegriffen werden.

>[!NOTE]
>
>Siehe [Grundlagen zu SRP und UGC](srp-and-ugc.md) für Beispielcode und zusätzliche Details.
>
>Siehe [Zugreifen auf UGC mit SRP](accessing-ugc-with-srp.md) für Best Practices beim Programmieren.

### ASRP {#asrp}

Im Falle von ASRP wird UGC nicht in JCR gespeichert, sondern in einem Cloud-Service gespeichert, der von Adobe gehostet und verwaltet wird. In ASRP gespeicherte benutzergenerierte Inhalte können weder mit CRXDE Lite angezeigt noch mit der JCR-API aufgerufen werden.

Siehe [ASRP - Adobe Storage Resource Provider](asrp.md).

Entwickler können nicht direkt auf die UGC zugreifen.

ASRP verwendet Adobe Cloud für Abfragen.

### MSRP {#msrp}

Bei MSRP wird UGC nicht in JCR gespeichert, sondern in MongoDB. In MSRP gespeicherte benutzergenerierte Inhalte können weder mit CRXDE Lite angezeigt noch mit der JCR-API aufgerufen werden.

Siehe [MSRP - MongoDB Storage Resource Provider](msrp.md).

MSRP ist zwar mit ASRP vergleichbar, da alle AEM Serverinstanzen auf dieselbe UGC zugreifen, es ist jedoch möglich, allgemeine Tools zu verwenden, um direkt auf die in MongoDB gespeicherte UGC zuzugreifen.

MSRP verwendet Solr für Abfragen.

### JSRP {#jsrp}

JSRP ist der Standardanbieter für den Zugriff auf alle benutzergenerierten Inhalte auf einer einzigen AEM. Es bietet die Möglichkeit, AEM Communities 6.1 schnell zu erleben, ohne dass MSRP oder ASRP eingerichtet werden muss.

Siehe [JSRP - JCR Storage Resource Provider](jsrp.md).

Im Falle von JSRP wird während UGC in JCR gespeichert ist und sowohl über die CRXDE Lite- als auch die JCR-API zugänglich ist, dringend empfohlen, dafür niemals die JCR-API zu verwenden. Andernfalls können sich zukünftige Änderungen auf benutzerdefinierten Code auswirken.

Außerdem wird das Repository für die Autoren- und Veröffentlichungsumgebungen nicht freigegeben. Während ein Cluster von Veröffentlichungsinstanzen zu einem freigegebenen Veröffentlichungs-Repository führt, ist in der Veröffentlichungsinstanz eingegebener UGC nicht in der Autoreninstanz sichtbar, sodass keine Möglichkeit besteht, benutzergenerierte Inhalte von der Autoreninstanz aus zu verwalten. UGC wird nur im AEM Repository (JCR) der Instanz beibehalten, in der es eingegeben wurde.

JSRP verwendet die Oak-Indizes für Abfragen.

## Über Shadow-Knoten in JCR {#about-shadow-nodes-in-jcr}

Shadow-Knoten, die den Pfad zu UGC imitieren, sind im lokalen Repository vorhanden und dienen zwei Zwecken:

1. [Zugriffskontrolle (ACLs)](#for-access-control-acls))
1. [Nicht vorhandene Ressourcen (NERs)](#for-non-existing-resources-ners)

Unabhängig von der SRP-Implementierung ist der tatsächliche UGC *nicht *am selben Speicherort wie der Shadow-Knoten sichtbar.

### Für Zugriffskontrolle (ACLs) {#for-access-control-acls}

Einige SRP-Implementierungen wie ASRP und MSRP speichern Community-Inhalte in Datenbanken, die keine ACL-Verifizierung bieten. Shadow-Knoten bieten einen Speicherort im lokalen Repository, auf den ACLs angewendet werden können.

Mithilfe der SRP-API führen alle SRP-Optionen vor allen CRUD-Vorgängen dieselbe Prüfung der Shadow-Position durch.

Die ACL-Prüfung verwendet eine Dienstprogrammmethode, die einen Pfad zurückgibt, der zum Überprüfen der auf die UGC der Ressource angewendeten Berechtigungen geeignet ist.

Siehe [Grundlagen zu SRP und UGC](srp-and-ugc.md) für Beispielcode.

### Für nicht vorhandene Ressourcen (NERs) {#for-non-existing-resources-ners}

Einige Communities-Komponenten sind in einem Skript enthalten und erfordern daher einen adressierbaren Sling-Knoten, um Communities-Funktionen zu unterstützen. [Enthaltene Komponenten](scf.md#add-or-include-a-communities-component) werden als nicht vorhandene Ressourcen (NER) bezeichnet.

Shadow-Knoten bieten einen adressierbaren Sling-Speicherort im Repository.

>[!CAUTION]
>
>Da der Shadow-Knoten mehrere Verwendungen hat, bewirkt das Vorhandensein eines Shadow-Knotens, dass *not* bedeutet, dass die Komponente ein NER ist.

### Speicherort {#storage-location}

Im Folgenden finden Sie ein Beispiel für einen Shadow-Knoten mit der [Kommentarkomponente](http://localhost:4502/content/community-components/en/comments.html) im [Handbuch zu Community-Komponenten](components-guide.md):

* Die Komponente befindet sich im lokalen Repository unter:

   /content/community-components/en/comments/jcr:content/content/include/comments

* Der entsprechende Shadow-Knoten existiert im lokalen Repository unter:

   /content/usergenerated/content/community-components/en/comments/jcr:content/content/include/comments

Unter dem Shadow-Knoten wird kein UGC gefunden.

Das Standardverhalten besteht darin, Shadow-Knoten in einer Veröffentlichungsinstanz einzurichten, wenn die relevante Unterstruktur für Lese- oder Schreibvorgänge referenziert wird.

Angenommen, die Bereitstellung lautet [MSRP](msrp.md) mit einer TarMK-Veröffentlichungsfarm.

Wenn eine [Mitglied](users.md) postet UGC auf pub1 (gespeichert in MongoDB), werden Shadow-Knoten in JCR auf pub1 erstellt.

Wenn das UGC zum ersten Mal in pub2 gelesen wird und nichts eingerichtet ist, besteht das Standardverhalten darin, die Shadow-Knoten zu erstellen.

Wenn andere als das Standardverhalten gewünscht werden, muss es in der Autoreninstanz eingerichtet und an alle Veröffentlichungsinstanzen weitergeleitet werden, was normalerweise ein manueller Prozess ist.
