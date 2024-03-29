---
title: Grundlagen zur Dateibibliothek
seo-title: File Library Essentials
description: Arbeiten mit der Dateibibliotheksfunktion
seo-description: Working with the file library feature
uuid: 0630f13e-97b4-4f93-9dce-07f559287c29
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 9019b967-fff8-4dda-bc5a-fd4a3e14a4ef
exl-id: 0e9d508e-d7dc-478a-99c0-c6885bcdcb81
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 5%

---

# Grundlagen zur Dateibibliothek {#file-library-essentials}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Auf dieser Seite finden Sie die wichtigsten Informationen zum Arbeiten mit der Dateibibliotheksfunktion.

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/filelibrary/components/hbs/filelibrary</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>einschließen</strong></a></td> 
   <td>Nein</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.stimating<br /> cq.social.hbs.filelilibrary</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/filelibrary/components/hbs/filelibrary/filelibrary.hbs<br /> /libs/social/filelibrary/components/hbs/folder/folder.hbs<br /> /libs/social/filelibrary/components/hbs/folder/item.hbs<br /> /libs/social/filelibrary/components/hbs/document/document.hbs<br /> /libs/social/filelibrary/components/hbs/document/item.hbs<br /> </td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/filelibrary/components/hbs/filelibrary/clientlibs/filelibrary.css</td> 
  </tr>
  <tr>
   <td><strong> properties</strong></td> 
   <td>Siehe <a href="file-library.md">Dateibibliothek-Funktion</a></td> 
  </tr>
 </tbody>
</table>

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für Server-seitige Unterstützung {#essentials-for-server-side}

* [Dateibibliothek-API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/filelibrary/client/api/package-summary.html)

* [Dateibibliothek-Endpunkte](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/filelibrary/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

### Dateibibliotheksfunktion {#file-library-function}

Eine Community-Site-Struktur mit [Dateibibliotheksfunktion](functions.md#file-library-function)enthält eine konfigurierte `file library` -Komponente.

### Zugreifen auf für Dateibibliotheken gepostete Kommentare {#accessing-comments-posted-for-file-libraries-ugc}

UGC sollte mit einer der Standardmethoden für die Moderation moderiert werden.\
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities: Verwendung einer [gemeinsamer Speicher](working-with-srp.md) für UGC umfasst den programmatischen Zugriff auf UGC, unabhängig von der ausgewählten Speicheroption (wie ASRP, MSRP oder JSRP).

**Speicherort und Format der UGC im Repository können ohne Warnung geändert werden**.

Siehe:

* [Übersicht über den Speicheranbieter](srp.md) - Einführung und Übersicht über die Repository-Nutzung
* [Grundlagen zu SRP und UGC](srp-and-ugc.md) - SRP-Anwendungsmethoden und -Beispiele
* [Zugreifen auf UGC mit SRP](accessing-ugc-with-srp.md) - Codierungsrichtlinien
* [SocialUtils-Refaktorierung](socialutils.md) - Zuordnung veralteter Methoden von Dienstprogrammen zu aktuellen Methoden des SRP-Dienstprogramms
