---
title: Tally Essentials
seo-title: Tally Essentials
description: Übersicht über die Tally-Klasse
seo-description: Tally class overview
uuid: c369c6a1-9ced-4b5c-af43-8c03236eaa52
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 9941ba90-3d40-4c90-bca8-5db49603cbfa
exl-id: f04ec253-08b8-4ee2-9873-4a51549daeba
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 2%

---

# Tally Essentials {#tally-essentials}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Tally ist eine abstrakte Klasse, die eine Standardmethode zur Erfassung von Feedback von Mitgliedern darüber bietet, wie sie bestimmte Produkte und Services bewerten. Anonymes Feedback wird nicht unterstützt. Der Besucher der Site muss sich registrieren und sich anmelden, um teilnehmen zu können und sich anzumelden, um sein Feedback zu ändern. Die Anmeldung erleichtert die Moderation und erhöht den Wert des Feedbacks, indem mehrere Beiträge verhindert werden.

Eine benutzerdefinierte Tally-Komponente kann durch Erweitern der abstrakten Tally-Klasse erstellt werden.

[Gefällt mir](essentials-liking.md) ist eine Umsetzung von Tally, die eine einfache Form der positiven Meinung ist.

[Abstimmung](essentials-voting.md) ist eine Umsetzung einer Tabelle, die einfach eine positive oder negative Meinung ausdrücken kann.

[Bewertung](rating-basics.md) ist eine Implementierung von Tally, die ein Sternsystem verwendet, um eine Reihe von Meinungen von positiv bis negativ auszudrücken.

Ab AEM 6.1 wird die *Umfrage* -Komponente nicht mehr verfügbar ist.

[Überprüfungen](reviews-basics.md) ist eine SCF-Komponente, die ein Hybrid von [Kommentare](essentials-comments.md) und [Bewertung](rating-basics.md).

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für Server-seitige Unterstützung {#essentials-for-server-side}

* [Tally-APIs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [Tally Endpoints](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

### Zugreifen auf gepostete Tabellen (UGC) {#accessing-posted-tallies-ugc}

UGC sollte mit einer der Standardmethoden für die Moderation moderiert werden.\
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities: Verwendung einer [gemeinsamer Speicher](working-with-srp.md) für UGC umfasst den programmatischen Zugriff auf UGC, unabhängig von der ausgewählten Speicheroption (wie ASRP, MSRP oder JSRP).

**Speicherort und Format der UGC im Repository können ohne Warnung geändert werden**.

Siehe:

* [Übersicht über den Speicheranbieter](srp.md) - Einführung und Übersicht über die Repository-Nutzung
* [Grundlagen zu SRP und UGC](srp-and-ugc.md) - SRP-Anwendungsmethoden und -Beispiele
* [Zugreifen auf UGC mit SRP](accessing-ugc-with-srp.md) - Codierungsrichtlinien
* [SocialUtils-Refaktorierung](socialutils.md) - Zuordnung veralteter Methoden von Dienstprogrammen zu aktuellen Methoden des SRP-Dienstprogramms
