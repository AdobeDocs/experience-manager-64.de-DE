---
title: Bearbeiten von Anwendungen
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
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1024'
ht-degree: 32%

---

# Bearbeiten von Anwendungen{#authoring-mobile-applications}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Mit dem AEM Mobile Dashboard können Sie Ihre Mobile App erstellen, erstellen und bereitstellen sowie Metadaten für Anwendungen erstellen, löschen und bearbeiten. Sobald Ihre Anwendung live ist, können Sie Anwendungsanalysen einschließlich Lebenszyklus- und Nutzungsmetriken analysieren, um die Kundenkonvertierung und Markenloyalität zu verbessern.

Informationen zum Erstellen Ihrer AEM Mobile-Anwendung finden Sie unter [Erstellen von Mobile Apps](/help/mobile/building-app-mobile-phonegap.md) Seite.

Informationen zum Einrichten der Umgebung und zu den ersten Schritten finden Sie unter [Verwalten von AEM zur Verwendung AEM PhoneGap Enterprise](/help/mobile/administer-phonegap.md).

## Der AEM Mobile-App-Katalog {#the-aem-mobile-apps-catalog}

Die [AEM Mobile Apps-Katalog](http://localhost:4502/aem/apps.html/content/phonegap) zeigt alle Ihre Mobile App an, die in AEM verwaltet wird.

Stellen Sie sich diesen Katalog als &quot;Landingpage&quot;für AEM Mobile vor, auf der Administratoren eine neue AEM Mobile-Anwendung starten können, indem sie entweder basierend auf einer Vorlage erstellen oder eine vorhandene App hochladen, die bereits von einem Mobile-Entwickler gestartet wurde.

Gehen Sie wie folgt vor, um zur Landingpage des Apps-Katalogs zu gelangen:

1. Navigieren Sie zu **Navigation** und wählen Sie dann **Mobile**.

1. Auswählen **Apps** , um den Apps-Katalog zu öffnen.

![AEM Mobile-App-Katalog](assets/chlimage_1-135.png)

## Das AEM Mobile-App-Dashboard {#the-aem-mobile-app-dashboard}

Wenn Sie eine AEM Mobile-App aus dem Katalog auswählen, wird das entsprechende Dashboard angezeigt. Hier können Sie Ihre App verwalten, Statistiken anzeigen, Inhalte für Ihre Mobile App erstellen, bereitstellen und verwalten.

Sie können jede Kachel im AEM Mobile Dashboard erweitern, um Details anzuzeigen oder zu bearbeiten, indem Sie auf &quot;...&quot;klicken in der unteren rechten Ecke.

![AEM Mobile-Apps-Befehlszentrale](assets/chlimage_1-136.png)

### Bereich „App verwalten“ {#the-manage-app-tile}

Der Bereich „App verwalten“ zeigt Symbol, Name, Beschreibung, unterstützte Plattformen, Quell-URL für Updates sowie Versionsinformationen an. Sie können diese Kachel näher untersuchen, um die PhoneGap-Anwendungskonfiguration (config.xml) zu bearbeiten und zu verwalten und Ihre Anwendung für die Übermittlung an die verschiedenen Anwendungsspeicher für die Verteilung vorzubereiten.

Klicken [here](/help/mobile/phonegap-app-details-tile.md) für Details.

![chlimage_1-137](assets/chlimage_1-137.png)

### Kachel &quot;Seiteninhalt verwalten&quot; {#the-manage-page-content-tile}

Inhalt kann in AEM Mobile im Prinzip auf dieselbe Weise wie in AEM Sites erstellt, aktualisiert und gelöscht werden. Die **Kachel &quot;Seiteninhalt verwalten&quot;** zeigt die Anzahl der Seiten verwalteten Inhalts und der zuletzt geänderten Inhalte an. Durch Klicken auf die einzelnen Datensätze in diesem Bereich können Sie Details für den Inhalt anzeigen, um Seiten zu erstellen, zu kopieren, zu verschieben, zu löschen und zu aktualisieren. Sobald der Inhalt aktualisiert wurde, können Sie Ihren Kunden eine Inhaltsaktualisierung über die **Kachel &quot;Inhaltspakete verwalten&quot;.**

![Bereich „Inhalt“](assets/chlimage_1-138.png)

### Die Kachel Inhaltspakete verwalten {#the-manage-content-packages-tile}

Nachdem Sie Ihren Inhalt über die Kachel Seiteninhalt verwalten hinzugefügt oder geändert haben, können Sie diese Änderungen mit einem Update der Inhaltsfreigabe an Ihre Kunden senden.

Das Inhaltspaket ermöglicht es dem AEM App-Autor, Seiteninhalte in AEM zu verwalten und Ihr Entwicklungsteam dazu zu veranlassen, Änderungen an Ihrer PhoneGap Shell-Anwendung vorzunehmen (d. h. App-Framework oder -Infrastruktur) und diese Änderungen dann schnell an Ihre Kunden zu senden, ohne dass ein Entwickler die Möglichkeit haben muss, sich zur Verteilung an die verschiedenen Stores erneut anzumelden.

Das Inhaltspaket erstellt für jedes Update eine ZIP-Datei, die als Inhaltsfreigabepaket gilt. Diese Pakete enthalten HTML-Ressourcen und HTML-Seiten, die beim Rendern der App generiert werden und intelligent genug sind, nur die Dateien zu verpacken, die seit der letzten Aktualisierung geändert wurden.

Die Kachel &quot;Inhaltspaket verwalten&quot; **Typ** -Spalte zeigt entweder &quot;App&quot;an, um Anwendungs-Shell-Inhalt anzugeben, z. B. das Framework oder die Infrastruktur der App, die von einem Entwickler verwaltet wird, oder &quot;Inhalt&quot;, der den vom Inhaltsautor verwalteten Seiteninhalt darstellt.

Inhalt kann als Sprache dargestellt werden oder als ein bestimmter Teil der App, in dem mehrere Inhaltsfreigabe-Pakete von der App genutzt werden. Die Art und Weise der Inhaltsbündelung ist flexibel und hängt komplett davon ab, wie Sie den Inhalt Ihrer App verwalten möchten.

Die Spalte **Geändert** gibt an, wann Seiten zuletzt geändert wurden.

Die Spalte **Gestaffelt** zeigt an, wann die letzte Inhaltsaktualisierung erstellt wurde. Um eine neue Inhaltsaktualisierung zu erstellen und die Änderungen gestaffelt bereitzustellen, öffnen Sie einen beliebigen Datensatz in diesem Bereich und erstellen Sie eine neue Aktualisierung.

Die Spalte **Veröffentlicht** zeigt an, wann die letzte Inhaltsaktualisierung veröffentlicht und für die Nutzung durch Ihre Kunden zur Verfügung gestellt wurde. Um Inhalte zu veröffentlichen, müssen Sie zunächst diesen Inhalt bereitstellen und dann die Aktualisierung veröffentlichen, indem Sie in diese Kachel navigieren und über die Konsole Inhaltsfreigabe-Details veröffentlichen.

![Bereich &quot;Inhaltsfreigabe&quot;](assets/chlimage_1-139.png) ![ContentSync-Paket für die App-Shell](do-not-localize/chlimage_1-5.png)

Dieses Symbol stellt ein Inhaltsaktualisierungs-Paket für die App-Shell dar

![](do-not-localize/chlimage_1-6.png)

Dieses Symbol stellt ein Inhaltsaktualisierungs-Paket für den App-Inhalt dar

### Bereich „PhoneGap-Build“ {#the-phonegap-build-tile}

Die **PhoneGap Build** verbindet mit [https://build.phonegap.com](https://build.phonegap.com) um Remote-Builds zu erstellen und zu hosten. Nach der Erstellung wird der Build entweder als Download oder direkt auf Ihrem Gerät über einen QR-Code bereitgestellt.

Sie können auch die Gerätequelle herunterladen, um die Erstellung lokal über die [PhoneGap-CLI](https://docs.phonegap.com/en/3.5.0/guide_cli_index.md.html) abzuwickeln.

![Bereich „PhoneGap-Build“](assets/chlimage_1-140.png)

### Bereich „Metrik“ {#the-metrics-tile}

>[!CAUTION]
>
>Die Kachel Metriken wird erst nach der Konfiguration des Cloud-Service angezeigt.
>
>Siehe [Adobe Mobile Services Cloud Service konfigurieren](/help/mobile/configure-adobe-mobile-cloud-service.md) für Details.

AEM Mobile integriert in Adobe Analytics über [Adobe Mobile Services SDK](https://www.adobe.com/ca/solutions/digital-marketing/mobile-services/app-sdk.html) (AMS).

Im **Bereich „Metrik“** des Kontrollzentrums wird für Ihre App eine zusammenfassende Analyse mit Daten aus AMS angezeigt. Sie können Details im Analyse-Dashboard anzeigen, indem Sie rechts unten auf „...“ klicken.

![Bereich „Metrik“](assets/chlimage_1-141.png)

### Kachel &quot;Entitätsinhalt verwalten&quot; {#the-manage-entity-content-tile}

Mit der Kachel &quot;Entitätsinhalt verwalten&quot;können Sie App-Definitionen hinzufügen und verwalten. Mit App-Definitionen können Sie ermitteln, welche Leerzeichen (und andere Konfigurationen) für die App geeignet sind. Auf diese Weise kann ein neues Leerzeichen hinzugefügt werden, ohne dass die App neu kompiliert werden muss. Die App-Definition wird aktualisiert und enthält die Informationen zu neuen Platzierungen.

Klicken [here](/help/mobile/phonegap-app-definitions.md) , um Ihre App-Definitionen zu erstellen und zu verwalten.

Sie können den Detaillierungsgrad des Dashboards zum Verwalten des Entitätsinhalts anzeigen, indem Sie auf &quot;...&quot;klicken unten rechts.

![chlimage_1-142](assets/chlimage_1-142.png)

#### Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Zuständigkeiten von Administratoren und Entwicklern finden Sie in den folgenden Ressourcen:

* [Entwickeln für Adobe PhoneGap Enterprise mit AEM](/help/mobile/developing-in-phonegap.md)
* [Verwalten von Inhalten für Adobe PhoneGap Enterprise mit AEM](/help/mobile/administer-phonegap.md)
