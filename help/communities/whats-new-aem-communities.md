---
title: Neue Funktionen in AEM 6.4 Communities
description: AEM Communities Angebots bietet Unternehmen einen Rahmen für die Zusammenarbeit zwischen ihren Partnern, Kunden und Mitarbeitern.
uuid: e4bf343c-59cd-48ac-bee4-85db109e4c65
contentOwner: mgulati
discoiquuid: 3e3c867f-afb0-4402-94f4-16e1a556ddee
exl-id: fcdc65c9-929d-4a87-8ff7-5e3cf5711fd9
translation-type: tm+mt
source-git-commit: 1a7ecec2f3c2618bb6d0280a8f9a66754cd8a1a3
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 1%

---

# Neue Funktionen in AEM 6.4 Communities {#what-s-new-in-aem-communities}

AEM Communities Angebots bietet Unternehmen einen Rahmen für die Zusammenarbeit zwischen ihren Partnern, Kunden und Mitarbeitern. Es bietet soziale Möglichkeiten zur Website-Struktur und hilft Unternehmen, sich mit ihren Interessenvertretern zu beschäftigen und ihnen Wissen zu vermitteln, um ihren Markenwert auf ihre Weise zu verbessern.

AEM 6.4 Communities bietet Funktionen, um die Benutzererfahrung in der Community zu verbessern und die Aufgaben von Administratoren, Moderatoren und Managern in der Community zu erleichtern.

Lesen Sie mehr, um sich schnell mit neuen Funktionen und Verbesserungen vertraut zu machen. Siehe auch AEM 6.4 Communities [Versionshinweise](../release-notes/communities-release-notes.md). Die Dokumentation zu AEM 6.4 Communities finden Sie unter [AEM 6.4 Communities Benutzerhandbuch](home.md).

## Verwalten von Untergemeinschaften oder Community-Gruppen {#managing-sub-communities-or-community-groups}

AEM Communities ermöglicht es Community-Administratoren, Gruppen und Untergruppen innerhalb der Communities-Site mithilfe vordefinierter Vorlagen in der Authoring-Umgebung zu erstellen. Diese Gruppen dienen als Untergruppen, die viele Konfigurationen übernehmen können, z. B. Themen und Stile von der übergeordneten Site. Diese Gruppen können jedoch von der übergeordneten Site abweichen, beispielsweise mit einem anderen Satz von Gruppenmoderatoren, oder die Sicherheitsstufe variieren. Diese Gruppen fungieren als unabhängige, vollwertige Mini-Communities, die durch die folgenden Erweiterungen weiter gestärkt werden.

### Erstellen mehrsprachiger Gruppen in einem einzigen Schritt{#create-multi-locale-groups-in-single-step} 

Als Teil einer Community-Site können mehrsprachige Gruppen in einem einzigen Vorgang erstellt werden. **[!UICONTROL Zusätzliche verfügbare Community-Gruppensprache(n)]** Feld in der  **[!UICONTROL Community-]** Gruppenvorlage, das beim Erstellen einer  [neuen Community-](groups.md) Gruppe innerhalb einer Community-Site verfügbar ist, macht dies möglich.

![multilingualgroup-1](assets/multilingualgroup-1.png)

Um solche Gruppen zu erstellen, können die Benutzer über die Site-Konsole einfach zur Gruppensammlung der gewünschten Communities navigieren. Erstellen Sie eine Gruppe und geben Sie die gewünschten Sprachen im Feld **[!UICONTROL Zusätzliche verfügbare Community-Gruppensprache(n)]** der Seite **[!UICONTROL Community-Gruppenvorlage]** an.

### Community-Gruppen aus der Gruppenkonsole {#delete-community-groups-from-groups-console} löschen

AEM 6.4 Communities stellt das Symbol &quot;Gruppe löschen&quot;für die vorhandenen Community-Gruppen in der Community-Gruppensammlung in der Community-Sites-Konsole bereit. Dies ermöglicht das Löschen der Gruppe [mit einem Klick sowie das Löschen aller Elemente, die mit der Gruppe verbunden sind (z. B. Inhalte und Benutzermitgliedschaften).](groups.md#deleting-the-group)

![deletegrp](assets/deletegrp.png)

### Erstellen und Zuweisen von Aktivierungsressourcen innerhalb von Gruppen {#create-and-assign-enablement-resources-within-groups}

Lerninhalte können jetzt für eine bestimmte Gruppe von zielgerichteten Community-Mitgliedern erstellt, verwaltet und veröffentlicht werden. Aufgrund der Verfügbarkeit von Katalog- und Zuweisungsfunktionen für Community-Gruppen (und nicht nur für die gesamte Community-Site) können Aktivierungsmanager [Aktivierungsressourcen](resource.md) und Lernpfad auch einer kleinen Gruppe von Personen zuweisen.

![zuweisungskatalog](assets/assignmentcatalog.png)

## Moderieren benutzergenerierter Inhalte {#moderating-user-generated-content}

AEM 6.4 Communities Angebote zeigen nur wenige Verbesserungen in der Moderation, die das tägliche Leben der Moderatoren in der Community erleichtern.

### Automatische Spamerkennung{#automatic-spam-detection} 

Die neue Spam-Erkennungs-Engine hilft beim Herausfiltern der unerwünschten und unerwünschten Benutzergenerierten Inhalte auf Community-Sites oder -Gruppen. Wenn diese Funktion aktiviert ist, kann ein Teil des vom Benutzer generierten Inhalts basierend auf einem vordefinierten Satz von Spam-Wörtern als Spam oder Nicht Spam gekennzeichnet werden. Moderatoren können den Inhalt weiter bearbeiten, um ihn in der Veröffentlichungsinstanz zu verweigern oder zu deaktivieren. Diese Moderationsaktionen können inline oder über Massenmoderationskonsole durchgeführt werden.

![spamdetect-1](assets/spamdetection-1.png)

[Spam ](moderate-ugc.md#spam-detection) findet und kennzeichnet ein bestimmtes Stück von Benutzergenerierten Inhalten mit 90% Genauigkeit. Diese Funktion ist jedoch nicht standardmäßig aktiviert. Um dies zu aktivieren, müssen Community-Administratoren zu configMgr auf System/Konsole navigieren und Spam Process hinzufügen.

![spamprocess-1](assets/spamprocess-1.png)

### Neue Filter (beantwortet/unbeantwortet) für QnA {#new-answered-unanswered-filters-for-qna}

AEM 6.4 fügt zwei [neue Filter](moderation.md#filter-rail) mit dem Namen &quot;Beantwortet&quot;und &quot;Nicht beantwortet&quot;für QnA-Fragen zu Massen-Moderationskonsole hinzu. Diese Filter sind unter Status in der Filterleiste verfügbar.

![Status](assets/statuses.png)

Bei Auswahl des Status &quot;Beantwortet&quot;sind alle beantworteten Fragen für den Moderator im Inhaltsbereich sichtbar. Wenn jedoch nur der Status &quot;Nicht beantwortet&quot;ausgewählt ist, wird dem Moderator der gesamte Inhalt (für alle Inhaltstypen) mit Ausnahme der beantworteten Fragen angezeigt, da die Eigenschaft, die für die beantwortete Frage zuständig ist, nicht vorhanden ist, wenn Fragen und andere Inhalte wie Forenthema, Blog-Artikel oder Kommentare nicht beantwortet werden.

### Lesezeichen für Moderationsfilter {#bookmark-moderation-filters}

AEM Communities bietet die Möglichkeit, die vordefinierten Moderations-Filter](moderation.md#filter-rail) in der Moderationskonsole mit einem Lesezeichen zu versehen. [ Diese gespeicherten Lesezeichen können später erneut besucht und für andere Benutzer freigegeben werden.

Die Benutzer müssen einfach die gewünschten Filter aus der Filterleiste in der Moderationskonsole auswählen, um das gefilterte benutzerspezifische Benutzerkontensymbol Ansicht und die Filter mit einem Lesezeichen in ihren Browsern zu versehen. Diese Filter werden an das Ende der URL-Zeichenfolge angehängt und können daher später freigegeben, wiederverwendet und erneut aufgerufen werden.

## Verwalten von Community-Sites {#managing-community-sites}

AEM 6.4 Communities bietet Site-Management-Verbesserungen, die sicherstellen, dass zahlreiche Community-Sites in verschiedenen Sprachen einfach von Site-Administratoren erstellt, verwaltet und gelöscht werden können.

### Mehrere Gebietsschema-Community-Sites in einem Schritt {#create-multi-locale-community-sites-in-one-step} erstellen

AEM Communities ermöglicht die Erstellung einer [mehrsprachigen Community-Site](create-site.md) in einem einzigen Vorgang. Dies ist möglich, da mehrere Sprachen verfügbar sind, die Sie auf der Seite **[!UICONTROL Community Site Base Language]** im Feld **[!UICONTROL Site Template]** auswählen können, während Sie eine neue Community-Site aus der Site-Konsole erstellen.

![multilocalesite](assets/multilocalesite.png)

Benutzer können Konfigurationsordner, Branding und viele andere Konfigurationen auf einmal für alle diese Sites auswählen.

### Löschen Sie Community-Sites aus der Sitekonsole {#delete-community-sites-from-sites-console}

AEM 6.4 Communities stellt auf den bestehenden Community-Sites in der Community-Sites-Konsole das Symbol zum Löschen von Sites bereit. Dadurch wird das Löschen der Site](create-site.md) und der zugehörigen Elemente in einem Klick aktiviert.[

![sitteactions](assets/siteactions.png)

## Verwalten von UGC- und Benutzereinstellungen {#managing-ugc-and-user-profiles}-Profilen

AEM Communities bewahrt den Schutz von Benutzerdaten im Zentrum der Community-Erfahrung auf und stellt [APIs standardmäßig bereit](user-ugc-management-service.md) und [Beispiel-Servlet](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet). Diese APIs helfen bei der Massenverwaltung (Massenlöschung und Massenexport) benutzergenerierter Profil und beim Löschen von Benutzerinhalten und sind bei der Bearbeitung von EU-Anforderungen zur Einhaltung der PDF-Richtlinien von entscheidender Bedeutung.

## Was wird geändert {#what-s-changed}

* Die Captcha-Verifizierung beim Erstellen einer neuen Community-Site ist in AEM 6.4 Communities nicht mehr standardmäßig verfügbar. Die Communities-Site kann jedoch angepasst werden, um [Google-Komponente reCAPTCHA](https://helpx.adobe.com/experience-manager/using/aem_recaptcha.html) einzuschließen, um die Sicherheit zu verbessern.
* Die Option zum Hochladen einer benutzerdefinierten CSS wurde aus dem Design der Community-Sites und -Gruppen entfernt.
* In der Benutzeroberfläche &quot;Massenmoderation&quot;der Filterleiste wurden Symbole für &quot;Nur Inhalt&quot;und &quot;Suche&quot;hinzugefügt.
* Der Filter &quot;Inhaltspfad&quot;wurde in der Benutzeroberfläche &quot;Filterleiste in Massenmoderation&quot;hinzugefügt.
* Der Wechsel zum Massenmodus und der Ausstiegsstapelmodus wurden aus der Benutzeroberfläche für die Massenmoderation entfernt. Um in den Mehrfachauswahlmodus zu wechseln, klicken Sie auf das Symbol Auswählen ( ![Auswahl](assets/selecticon.png)) in einem Beitrag, das angezeigt wird, wenn Sie mit der Maus (Desktop) darauf zeigen oder einen Finger auf dem Beitrag drücken und gedrückt halten (Mobil).
