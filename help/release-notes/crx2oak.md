---
title: Migrationstool CRX2OAK
seo-title: CRX2OAK Migration Tool
description: Spezifische Versionshinweise zum Adobe Experience Manager 6.4 CRX2OAK-Migrationstool.
seo-description: Release notes specific to the Adobe Experience Manager 6.4 CRX2OAK Migration tool.
uuid: 1b582faf-2dc6-41a2-9419-7e82347f9d6c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: cfdaceac-a5b3-4070-ad4c-f1457b1e2e4b
exl-id: 441c8ba0-f8b2-4c2c-b7be-cfdad9e1e498
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 2%

---

# Migrationstool CRX2OAK {#crx-oak-migration-tool}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Liste der Änderungen und Fehlerbehebungen {#list-of-changes-and-fixes}

### 1.8.6 (Juni 2018) {#june}

* OAK-7339 Korrigieren Sie alle mit UnsupportedOperationException unterbrochenen Seitenabbrüche bei MissingBlobStore durch Einführung von LoopbackBlobStore.
* Verwenden von Oak 1.8.4

### 1.8.4 (April 2018) {#april}

* Verwenden von Oak Version 1.8.2
* GRANITE-18104 Repo Migration Error von 6.3 zu 6.4 sollte aussagekräftiger sein
* GRANITE-16571 Nutzung von SHA-1 ersetzen

   * Die Tool-Prüfsumme ist jetzt SHA-512 bei Verwendung der Option —version .

* GRANITE-17601 Embed oak-upgrade in CRX2Oak mit oak-blob-cloud
* GRANITE-18553 crx2oak hinterlässt Versionseigenschaften auf dem Knoten, selbst wenn Versionen nicht migriert werden

### Version 1.6.8 (März 2017) {#version-march}

* Oak-Version wurde auf 1.6.1 aktualisiert.
* CQ-61847 Zusammenführen von crx2oak-quickstart-extension mit crx2oak (hinzugefügte Migrationsprofile)
* CQ-97488 Weiterleiten und Ablegen AEM Ausführungsmodi (durch Neuschreiben der Datei sling.options.file)
* GRANITE-12798/OAK-4260 Fähigkeit, eine Nebenstufe vom Oak-Segment zum Oak-Segment-Tar zu erstellen

### Version 1.4.2 (März 2016) {#version-march-1}

* Aktualisierung der Oak-Version auf 1.4.1
* OAK-3846/GRANITE-10748 SNS-Knoten umbenennen, wenn sie Knotentyp-Einschränkungen verletzen
* OAK-3910/GRANITE-10730 Migrieren des Knotens, der erbt von `mix:versionable` ohne Versionsverlauf
* OAK-4128/GRANITE-11757 `RepositorySidegrade` kopiert keine Eigenschaften des Stammknotens

### Version 1.3.4 (Januar 2016) {#version-january}

* Aktualisierung der Oak-Version auf Version 1.3.16
* OAK-3844/GRANITE-10730 Bessere Unterstützung für versionierbare Knoten ohne Versionsverläufe
* OAK-3846 SNS-Knoten umbenennen, wenn sie Knotentyp-Einschränkungen verletzen

### Version 1.3.2 (Dezember 2015) {#version-december}

* Upgrade der Oak-Version auf 1.3.12
* Datenspeicherverzeichnis sollte nach der Migration nicht verschoben werden (GRANITE-10447)
* Zusammenführen von crx2oak-quickstart-extension mit crx2oak (CQ-61847)
* crx2oak schlägt bei doppelten Werten im Repository fehl (CQ-61906)
* Lange AEM nach der Migration von CQ 5.x (GRANITE-10309)
* Unterstützung für mehrere LDAP-Server in crx2oak (GRANITE-9917)
* Erzwingen der Überprüfung auf maximale Knotennamenlänge (OAK-3111)
* Unterstützung von S3DataSource als Migrationsquelle (OAK-3685)
