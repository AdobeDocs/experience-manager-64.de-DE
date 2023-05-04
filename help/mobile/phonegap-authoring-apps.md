---
title: Erstellen von mobilen Anwendungen
seo-title: Authoring Mobile Applications
description: Mit dem AEM Mobile Dashboard können Sie Ihre Mobile App erstellen, erstellen und bereitstellen sowie Metadaten für Anwendungen erstellen, löschen und bearbeiten. Auf dieser Seite erfahren Sie mehr.
seo-description: he AEM Mobile Dashboard allows you to create, build and deploy your mobile application, create, delete and edit application metadata. Follow this page to learn more.
uuid: 293b5d29-df7e-42dd-ae64-8c677317e7a5
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: authoring-adobe-phonegap-enterprise
discoiquuid: abfeea65-102d-4800-abeb-304d61afcc13
exl-id: dbaa5221-4011-49cf-8123-5f8daa7fae76
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1060'
ht-degree: 3%

---

# Erstellen von mobilen Anwendungen{#authoring-mobile-applications}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Mit dem AEM Mobile Dashboard können Sie Ihre Mobile App erstellen, erstellen und bereitstellen sowie Metadaten für Anwendungen erstellen, löschen und bearbeiten. Sobald Ihre Anwendung live ist, können Sie Anwendungsanalysen einschließlich Lebenszyklus- und Nutzungsmetriken analysieren, um die Kundenkonvertierung und Markenloyalität zu verbessern.

Informationen zum Erstellen Ihrer AEM Mobile-Anwendung finden Sie unter [Erstellen von Mobile Apps](/help/mobile/building-app-mobile-phonegap.md) Seite.

Informationen zum Einrichten der Umgebung und zu den ersten Schritten finden Sie unter [Verwalten von AEM zur Verwendung AEM PhoneGap Enterprise](/help/mobile/administer-phonegap.md).

## Der AEM Mobile Apps-Katalog {#the-aem-mobile-apps-catalog}

Die [AEM Mobile Apps-Katalog](http://localhost:4502/aem/apps.html/content/phonegap) zeigt alle Ihre Mobile App an, die in AEM verwaltet wird.

Stellen Sie sich diesen Katalog als &quot;Landingpage&quot;für AEM Mobile vor, auf der Administratoren eine neue AEM Mobile-Anwendung starten können, indem sie entweder basierend auf einer Vorlage erstellen oder eine vorhandene App hochladen, die bereits von einem Mobile-Entwickler gestartet wurde.

Gehen Sie wie folgt vor, um zur Landingpage des Apps-Katalogs zu gelangen:

1. Navigieren Sie zu **Navigation** und wählen Sie dann **Mobile**.

1. Auswählen **Apps** , um den Apps-Katalog zu öffnen.

![AEM Mobile Apps-Katalog](assets/chlimage_1-135.png)

## Das Dashboard der AEM Mobile-App {#the-aem-mobile-app-dashboard}

Wenn Sie eine AEM Mobile-App aus dem Katalog auswählen, wird das zugehörige Dashboard angezeigt. Hier können Sie Ihre App verwalten, Statistiken anzeigen, Inhalte für Ihre Mobile App erstellen, bereitstellen und verwalten.

Sie können jede Kachel im AEM Mobile Dashboard erweitern, um Details anzuzeigen oder zu bearbeiten, indem Sie auf &quot;...&quot;klicken in der unteren rechten Ecke.

![AEM Mobile Applications Command Center](assets/chlimage_1-136.png)

### Die Kachel App verwalten {#the-manage-app-tile}

Im Bereich App verwalten werden Ihr Anwendungssymbol, Ihr Name, Ihre Beschreibung, die unterstützten Plattformen sowie der Aufruf der Startseite mit Informationen zu Updates-URL und Version angezeigt. Sie können diese Kachel näher untersuchen, um die PhoneGap-Anwendungskonfiguration (config.xml) zu bearbeiten und zu verwalten und Ihre Anwendung für die Übermittlung an die verschiedenen Anwendungsspeicher für die Verteilung vorzubereiten.

Klicken [here](/help/mobile/phonegap-app-details-tile.md) für Details.

![chlimage_1-137](assets/chlimage_1-137.png)

### Kachel &quot;Seiteninhalt verwalten&quot; {#the-manage-page-content-tile}

Inhalte können in AEM Mobile auf die gleiche Weise erstellt, aktualisiert und gelöscht werden wie in AEM Sites. Die **Kachel &quot;Seiteninhalt verwalten&quot;** zeigt die Anzahl der Seiten verwalteten Inhalts und der zuletzt geänderten Inhalte an. Sie können einen Drilldown in den Inhalt durchführen, um Seiten zu erstellen, zu kopieren, zu verschieben, zu löschen und zu aktualisieren, indem Sie auf jeden Datensatz in der Kachel klicken. Sobald der Inhalt aktualisiert wurde, können Sie Ihren Kunden eine Inhaltsaktualisierung über die **Kachel &quot;Inhaltspakete verwalten&quot;.**

![Inhaltsbereich](assets/chlimage_1-138.png)

### Die Kachel Inhaltspakete verwalten {#the-manage-content-packages-tile}

Nachdem Sie Ihren Inhalt über die Kachel Seiteninhalt verwalten hinzugefügt oder geändert haben, können Sie diese Änderungen mit einem Update der Inhaltsfreigabe an Ihre Kunden senden.

Das Inhaltspaket ermöglicht es dem AEM App-Autor, Seiteninhalte in AEM zu verwalten und Ihr Entwicklungsteam dazu zu veranlassen, Änderungen an Ihrer PhoneGap Shell-Anwendung vorzunehmen (d. h. App-Framework oder -Infrastruktur) und diese Änderungen dann schnell an Ihre Kunden zu senden, ohne dass ein Entwickler die Möglichkeit haben muss, sich zur Verteilung an die verschiedenen Stores erneut anzumelden.

Das Inhaltspaket erstellt für jedes Update eine ZIP-Datei, die als Inhaltsfreigabepaket gilt. Diese Pakete enthalten HTML-Ressourcen und HTML-Seiten, die beim Rendern der App generiert werden und intelligent genug sind, nur die Dateien zu verpacken, die seit der letzten Aktualisierung geändert wurden.

Die Kachel &quot;Inhaltspaket verwalten&quot; **Typ** -Spalte zeigt entweder &quot;App&quot;an, um Anwendungs-Shell-Inhalt anzugeben, z. B. das Framework oder die Infrastruktur der App, die von einem Entwickler verwaltet wird, oder &quot;Inhalt&quot;, der den vom Inhaltsautor verwalteten Seiteninhalt darstellt.

Inhalte können als Sprache oder als bestimmter Teil der App dargestellt werden, in dem die App mehrere Inhaltsfreigabe-Pakete nutzt. Die Art und Weise, wie Sie Ihre Inhalte bündeln, ist flexibel und hängt vollständig davon ab, wie Sie Inhalte für Ihre Anwendung verwalten möchten.

Die **Geändert** gibt an, wann die Seiten zuletzt geändert wurden.

Die **Staging** gibt an, wann die letzte Inhaltsaktualisierung erstellt wurde. Um eine neue Inhaltsaktualisierung zu erstellen und Ihre Änderungen zu testen, öffnen Sie einen beliebigen Datensatz in der Kachel und erstellen Sie eine neue Aktualisierung.

Die **Veröffentlicht** gibt an, wann die letzte Inhaltsaktualisierung veröffentlicht und für Ihre Kunden zur Verfügung gestellt wurde. Um Inhalte zu veröffentlichen, müssen Sie zunächst diesen Inhalt bereitstellen und dann die Aktualisierung veröffentlichen, indem Sie in diese Kachel navigieren und über die Konsole Inhaltsfreigabe-Details veröffentlichen.

![Bereich &quot;Inhaltsfreigabe&quot;](assets/chlimage_1-139.png) ![ContentSync-Paket für die App-Shell](do-not-localize/chlimage_1-5.png)

Dieses Symbol stellt ein Inhaltsfreigabepaket für die App-Shell dar

![](do-not-localize/chlimage_1-6.png)

Diese Symbole stellen ein Inhaltsfreigabepaket für App-Inhalte dar

### Der PhoneGap Build {#the-phonegap-build-tile}

Die **PhoneGap Build** verbindet mit [https://build.phonegap.com](https://build.phonegap.com) um Remote-Builds zu erstellen und zu hosten. Nach der Erstellung wird der Build entweder als Download oder direkt auf Ihrem Gerät über einen QR-Code bereitgestellt.

Alternativ können Sie die Gerätequelle herunterladen, um sie lokal über die [PhoneGap-CLI](https://docs.phonegap.com/en/3.5.0/guide_cli_index.md.html).

![PhoneGap Build](assets/chlimage_1-140.png)

### Bereich &quot;Metriken&quot; {#the-metrics-tile}

>[!CAUTION]
>
>Die Kachel Metriken wird erst nach der Konfiguration des Cloud-Service angezeigt.
>
>Siehe [Adobe Mobile Services Cloud Service konfigurieren](/help/mobile/configure-adobe-mobile-cloud-service.md) für Details.

AEM Mobile integriert in Adobe Analytics über [Adobe Mobile Services SDK](https://www.adobe.com/ca/solutions/digital-marketing/mobile-services/app-sdk.html) (AMS).

Das Kontrollzentrum **Bereich &quot;Metriken&quot;** zeigt zusammenfassende Analysen an, die von AMS für Ihre Anwendung abgerufen wurden. Sie können einen Drilldown im Analyse-Dashboard durchführen, indem Sie auf &quot;...&quot;klicken unten rechts.

![Bereich &quot;Metriken&quot;](assets/chlimage_1-141.png)

### Kachel &quot;Entitätsinhalt verwalten&quot; {#the-manage-entity-content-tile}

Mit der Kachel &quot;Entitätsinhalt verwalten&quot;können Sie App-Definitionen hinzufügen und verwalten. Mit App-Definitionen können Sie ermitteln, welche Leerzeichen (und andere Konfigurationen) für die App geeignet sind. Auf diese Weise kann ein neues Leerzeichen hinzugefügt werden, ohne dass die App neu kompiliert werden muss. Die App-Definition wird aktualisiert und enthält die Informationen zu neuen Platzierungen.

Klicken [here](/help/mobile/phonegap-app-definitions.md) , um Ihre App-Definitionen zu erstellen und zu verwalten.

Sie können den Detaillierungsgrad des Dashboards zum Verwalten des Entitätsinhalts anzeigen, indem Sie auf &quot;...&quot;klicken unten rechts.

![chlimage_1-142](assets/chlimage_1-142.png)

#### Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Zuständigkeiten von Administratoren und Entwicklern finden Sie in den folgenden Ressourcen:

* [Entwickeln für Adobe PhoneGap Enterprise mit AEM](/help/mobile/developing-in-phonegap.md)
* [Verwalten von Inhalten für Adobe PhoneGap Enterprise mit AEM](/help/mobile/administer-phonegap.md)
