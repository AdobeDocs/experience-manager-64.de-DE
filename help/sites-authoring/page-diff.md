---
title: Seitenvergleich
seo-title: Page Diff
description: Die Seitenvergleichsfunktion ermöglicht einen bequemen Vergleich von zwei Seiten, die nebeneinander angezeigt werden und deren Unterschiede hervorgehoben sind.
seo-description: The page diff feature allows for the convenient side-by-side comparison of two pages with their differences highlighted.
uuid: cf029ed8-606e-4f12-ac8e-5ea9ebd70b1b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 5a771d8c-cc56-4979-aeab-b508755a2078
exl-id: 1b1fa592-a145-4abe-a455-df24d551b937
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 95%

---

# Seitenvergleich{#page-diff}

## Einführung {#introduction}

Inhaltserstellung ist ein iterativer Vorgang. Damit ein Autor effizient arbeiten kann, muss er sehen können, was sich von Iteration zu Iteration verändert hat. Es ist ineffizient und bringt Fehler mit sich, wenn eine Seitenversion und danach die andere geprüft wird. Ein Autor muss die Möglichkeit haben, die aktuelle Seite direkt mit der anderen Seite zu vergleichen.

Die Seitenvergleichsfunktion ermöglicht einen bequemen Vergleich von zwei Seiten, die nebeneinander angezeigt werden und deren Unterschiede hervorgehoben sind.

>[!CAUTION]
>
>Wenn Sie eine Version vor AEM 6.4.3 ausführen, muss der Benutzer über die **Ändern/Erstellen/Löschen** Berechtigung auf dem Knoten `/content/versionhistory` , um die Funktion zu verwenden.
>
>Weitere Informationen zu dieser Funktion finden Sie unter [Entwicklung und Seitenvergleich](/help/sites-developing/pagediff.md#operation-details).

## Verwenden Sie {#use}

Folgendes kann verglichen werden:

* [Versionen](/help/sites-authoring/working-with-page-versions.md#comparing-a-version-with-current-page) – frühere Version einer Seite mit ihrem aktuellen Status
* [Live Copies](/help/sites-administering/msm-livecopy.md#comparing-a-live-copy-page-with-a-blueprint-page) – Live Copy mit ihrer Blueprint
* [Launches](/help/sites-authoring/launches-editing.md#comparing-a-launch-page-to-its-source-page) – Launch mit seiner Quelle
* [Sprachkopien](/help/sites-administering/tc-manage.md#comparing-language-copies) – eine Seite vor und nach der (erneuten) Übersetzung

Informieren Sie sich unter den entsprechenden Themen, wie der Seitenvergleich im gegebenen Zusammenhang verwendet wird.

### Darstellung von Unterschieden {#presentation-of-differences}

Unabhängig vom verglichenen Inhalt bleibt die Darstellung der Unterschiede gleich.

* Nachdem Sie den Seitenvergleich gestartet haben, wird der ausgewählte Inhalt auf der linken Seite angezeigt (der Differenzeinstiegspunkt).
* Rechts wird der zu vergleichende Inhalt angezeigt (der mit dem ausgewählten Inhalt verglichen wird).

Wenn Sie z. B. Versionen vergleichen, wird die aktuelle Version auf der linken Seite und die Vorversion auf der rechten Seite angezeigt.

Die Quelle beider Seiten wird deutlich in der Kopfzeile am oberen Rand des Browser-Fensters angezeigt.

![chlimage_1-355](assets/chlimage_1-355.png)

Der Seitenvergleich erkennt Änderungen an der Komponente und der HTML-Ebene. Geänderte Elemente werden mit verschiedenen Farben hervorgehoben.

**Komponentenänderungen**

* Hellgrün – Komponente hinzugefügt
* Rosa – Komponente entfernt
* Blau – Komponente geändert
* Blau – Komponente verschoben

Hinweis: Die Farben für geänderte und verschobene Elemente sind identisch.

**HTML-Änderungen**

* Dunkelgrün – HTML hinzugefügt
* Rot – HTML entfernt

>[!NOTE]
>
>Beim Vergleich von Sprachkopien ist die Hervorhebung deaktiviert, da sich in einer Übersetzung alles ändert und Hervorhebung nutzlos wäre.

### Vollbild und Beenden {#fullscreen-and-exiting}

Damit Sie sich auf einen bestimmten Inhalt konzentrieren können, haben Sie die Möglichkeit, auf jeder Seite des Seitenvergleichs auf das Vollbildsymbol zu klicken, um die Ansicht auf das ganze Browser-Fenster zu vergrößern.

![](do-not-localize/chlimage_1-24.png)

Die gewählte Seite füllt dann das gesamte Fenster aus, aber die Leiste am oberen Rand bleibt weiterhin angezeigt und bietet Ihnen die Möglichkeit, zwischen den zwei Seiten zu wechseln.

![chlimage_1-356](assets/chlimage_1-356.png)

Sie können die Vollbildansicht auch schließen, indem Sie auf das Symbol „Vollbildmodus beenden“ klicken.

![](do-not-localize/chlimage_1-25.png)

Sie können den Seitenvergleich jederzeit beenden, indem Sie in der Kopfzeile auf die Schaltfläche „Schließen“ klicken.

## Beschränkungen {#limitations}

In manchen Fällen erkennt der Seitenvergleich einen Unterschied nicht wie erwartet.

* Beim Vergleich von Versionen und Launches berücksichtigt der Seitenvergleich keine dynamischen Komponenten wie Breadcrumbs, Menüs, Produktlisten oder Logos (Komponenten, die die Site-Struktur zur Darstellung ihres Inhalts nutzen).
* Bei Versionen erstellt der Seitenvergleich die Richtlinien zur Zugriffssteuerung und die Live Copy-Beziehungen nicht neu.
* Wenn Änderungen an einem Bild vorgenommen werden, z. B. eine Änderung der alt-, title- oder der src-Attribute, wird das geänderte Element blau hervorgehoben. In manchen Fällen weist ein Bild jedoch eine Base64-Darstellung des src-Attributs auf und selbst dann, wenn beide Bilder gleich aussehen, werden sie vom Seitenvergleich aufgrund der unterschiedlichen src-Attribute gekennzeichnet.
* Der Seitenvergleich erkennt keine Bilddrehung.
* Wenn eine Seite verschoben wird, können Sie keinen Vergleich mit Versionen mehr durchführen, die vor dem Verschieben erstellt wurden.

   * Wenn Probleme beim Vergleich auftreten, überprüfen Sie in der [Zeitleiste](/help/sites-authoring/basic-handling.md#timeline) der Seite, ob die Seite verschoben wurde.

>[!NOTE]
>
>Versionen können nicht miteinander verglichen werden. Nur die aktuelle Version kann mit anderen Versionen der Seite verglichen werden. Die aktuelle Version ist immer die Version, deren Änderungen hervorgehoben sind.

>[!NOTE]
>
>Weitere Informationen zum Ablauf des Seitenvergleichsmechanismus sowie Einschränkungen, die sich auf den Seitenvergleich auswirken können, finden Sie in der [Entwickler-Dokumentation](/help/sites-developing/pagediff.md) zu dieser Funktion.
