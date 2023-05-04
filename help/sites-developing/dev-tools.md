---
title: Entwicklungs-Tools
seo-title: Development Tools
description: Zur Entwicklung Ihrer JCR-, Apache Sling- oder AEM-Anwendungen stehen verschiedene Toolsets zur Verfügung
seo-description: To develop your JCR, Apache Sling or AEM applications, a number of tool sets are available
uuid: 1bee3a52-5d76-4b0c-a222-a02e12ff3a43
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: 76c570e5-46ed-46be-9864-4fe4a83f0caf
exl-id: 3c18feab-97a6-49f2-96be-7e7458199f5d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 69%

---

# Entwicklungs-Tools{#development-tools}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Um Ihre JCR-, Apache Sling- oder AEM-Anwendungen zu entwickeln, sind die folgenden Toolsets verfügbar:

* Ein Set mit [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) und WebDAV. CRXDE Lite ist in CRX/AEM integriert und ermöglicht es Ihnen, gängige Entwicklungstätigkeiten im Browser vorzunehmen. Mit CRXDE Lite können Sie Dateien (etwa JSP- und JAVA-Dateien), Ordner, Vorlagen, Komponenten, Dialoge, Knoten, Eigenschaften und Pakete erstellen und bearbeiten, während eine Protokollierung und Integration mit SVN erfolgt.

   CRXDE Lite wird empfohlen, wenn Sie keinen direkten Zugriff auf den CRX-/AEM-Server haben, wenn Sie eine Anwendung entwickeln, indem Sie die vordefinierten Komponenten und Java-Bundles erweitern oder ändern oder wenn Sie keinen dedizierten Debugger, keine Codevervollständigung und keine Syntaxhervorhebung benötigen.

* Ein Set bestehend aus einer integrierten Entwicklungsumgebung (z. B. [Eclipse](/help/sites-developing/howto-projects-eclipse.md) oder [IntelliJ](/help/sites-developing/ht-intellij.md)), einem Build-Tool (z. B. [Apache Maven](/help/sites-developing/ht-projects-maven.md)), FileVault – einem von Adobe entwickelten Tool zum Zuordnen eines Repositorys zu einem Dateisystem, einem Versionskontrollsystem (z. B. Subversion), einem Fehlererfassungssystem (z. B. Jira), einem zentralen Abhängigkeitsverwaltungssystem (z. B. Apache Archiva) und einem System zur Build-Automatisierung (z. B. Apache Continuum).

   Diese Ausstattung ermöglicht Ihnen, Ihre Anwendung (Inhalte, Code, Konfiguration) vollständig in beliebige Entwicklungsumgebungen und -prozesse zu integrieren. Die Verbindung zwischen den verschiedenen Elementen ist die Dateisystemdarstellung des Repositorys durch FileVault, da alle genannten Entwicklungs-Tools mit Dateien umgehen können.

## Erweiterungen für integrierte Entwicklungsumgebungen {#extensions-for-integrated-development-environments}

Adobe hat die folgenden Erweiterungen veröffentlicht:

* [AEM Eclipse-Erweiterung](/help/sites-developing/aem-eclipse.md)
* [AEM Brackets-Erweiterung](/help/sites-developing/aem-brackets.md)
* [AEM IntelliJ-Erweiterung](https://github.com/headwirecom/aem-ide-tooling-4-intellij/blob/master/documenation/AEM%20Tooling%20Plugin%20for%20IntelliJ%20IDEA.pdf) (von Headwire)

### Sonstige Instrumente {#other-tools}

AEM mit anderen Werkzeugen, die die Entwicklung erleichtern:

* [Dialogfeldeditor](/help/sites-developing/dialog-editor.md)
* [Verwalten von Wörterbüchern mithilfe des Übersetzers](/help/sites-developing/i18n-translator.md)
* [Verwalten von Paketen mithilfe von Maven](/help/sites-developing/vlt-mavenplugin.md)
* [Entwickeln von AEM-Projekten mit Eclipse](/help/sites-developing/howto-projects-eclipse.md)
* [Erstellen von AEM-Projekten mit Apache Maven](/help/sites-developing/ht-projects-maven.md)
* [Entwicklung von AEM-Projekten mit IntelliJ IDEA](/help/sites-developing/ht-intellij.md)
* [Vewenden des VLT-Tools](/help/sites-developing/ht-vlttool.md)
* [Verwendung des Proxy-Server-Tools](/help/sites-developing/ht-proxy-server.md)
* [AEM-Modernisierungs-Tools](/help/sites-developing/modernization-tools.md)
* [AEM Repo Tool](/help/sites-developing/aem-repo-tool.md)

Tools, die die Erstellung neuer Projekte erleichtern:

* [AEM-Projektarchetyp](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype)
* [AEM-Lazybones-Vorlagen](https://github.com/Adobe-Consulting-Services/lazybones-aem-templates)

>[!NOTE]
>
>Das folgende Tutorial kann für den Start eines neuen AEM-Projekts von Interesse sein:\
>[Erste Schritte mit AEM Sites – Teil 1: Projekteinrichtung](https://helpx.adobe.com/de/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part1.html)
