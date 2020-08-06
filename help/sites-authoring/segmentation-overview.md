---
title: Grundlegendes zur Segmentierung
seo-title: Grundlegendes zur Segmentierung
description: Die Segmentierung ist ein wichtiger Faktor, der bei der Erstellung einer Kampagne berücksichtigt werden muss.
seo-description: Die Segmentierung ist ein wichtiger Faktor, der bei der Erstellung einer Kampagne berücksichtigt werden muss.
uuid: 900da068-5dda-4b6b-8be3-4b7ad614126d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: personalization
discoiquuid: 36c87684-e62a-4983-b123-87f56dbf7bc5
translation-type: tm+mt
source-git-commit: 9a1fe3265f1cd7907dfe576666a694b3c5b78d76
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 68%

---


# Grundlegendes zur Segmentierung{#understanding-segmentation}

Die Segmentierung ist ein wichtiger Faktor, der bei der Erstellung einer Kampagne berücksichtigt werden muss. In den meisten Fällen müssen vor dem Start einer Kampagne bereits Segmente definiert sein.

Besucher von Websites haben unterschiedliche Interessen und Ziele, wenn sie eine Site besuchen. Das Verstehen dieser Ziele und das Erfüllen der Erwartungen sind wichtige Erfolgsfaktoren beim Onlinemarketing.

Dies können Sie mithilfe der Segmentierung erreichen, indem Sie die folgenden Faktoren eines Besuchers analysieren und charakterisieren:

* Aktivität auf der Website
* Profil
* Aktivität auf anderen Websites

Inhalte können dann entsprechend den zutreffenden Segmenten speziell auf die Anforderungen und Interessen des Besuchers abgestimmt werden.

## Verwenden von Segmentierung {#using-segmentation}

Segmente werden unter [Konfigurieren von Segmentierung](/help/sites-administering/campaign-segmentation.md) definiert. Sie werden dazu verwendet, den tatsächlich für Zielgruppen sichtbaren Inhalt zu steuern.

## Segmentierungsterminologie {#segmentation-terminology}

Im Rahmen der Segmentierung wird die folgende Terminologie verwendet:

**Besucher** A Besucher ist eine Person, die eine Website besucht. Der Besuch dieser Person beginnt in der Regel auf einer verweisenden Seite und geht dann über auf eine oder mehrere Seitenansichten auf Ihrer eigenen Website. Aus den Details des Besuchs dieser Person kann ein Verhaltensprofil erstellt werden.

**Benutzer** Ein Benutzer ist ein Besucher, der sich bei der Website registriert, um ein Konto-Profil zu erhalten. Um ein Profil zu erstellen, geben Benutzer weitere Informationen zu ihrer Person an, z. B. eine E-Mail-Adresse oder ihr Geschlecht. Es können auch weitere Informationen erfasst werden, beispielsweise Aktivität in der Community und Kaufmuster. Basierend auf den in dem Profil angegebenen Informationen kann ein demografisches Profil erstellt werden.

**Eigenschaft** A ist ein Merkmal oder eine Eigenschaft eines Besuchers, mit dem die Mitgliedschaft in einem bestimmten Segment bestimmt werden kann.

**Segment** A ist eine Sammlung von Besuchern, die bestimmte Eigenschaften gemeinsam haben. Segmente sollten klar voneinander getrennt sein und so wenig Überlappung wie möglich mit anderen Segmenten aufweisen.

**Verhaltensbasierte Eigenschaften** beziehen sich auf das Verhalten eines Besuchers auf der Website. Dazu gehören:

* Interessensgebiete auf Ihrer Website, einschließlich besuchter Seiten und gekaufter Produkte.
* Interessensgebiete auf der verweisenden Website, einschließlich verwendeter Suchbegriffe oder Anzeigen, auf die geklickt wurde.
* Interessensgebiete auf anderen Sites, die durch Tools wie Spyjax ermittelt werden.
* Loyalität der Besucher, Dauer des Besuchs, Häufigkeit der Besuche.

**Demografische Eigenschaften** Diese sind ausgewählte Bevölkerungsmerkmale, darunter:

* Alter
* Einkommen
* Größe der Familie
* Familienstand
* Geschlecht
* Ort

**Abgeleitete Eigenschaften** Einige demografische Eigenschaften lassen sich nur schwer ohne Registrierung ermitteln, können aber durch Kombination von verhaltensbezogenen und demografischen Eigenschaften abgeleitet werden.

Beispielsweise können Besitzer von Sites durch Kombination der verweisenden URL (als Verhaltenseigenschaft) mit demografischen Informationen (ermittelt mithilfe von Tools wie [Google Ad Planner](https://www.google.com/adplanner/)) demografische Eigenschaften ihrer Besucher ableiten.

**Teilsegment** Ein Segment kann in mehrere Untersegmente unterteilt werden. Dies geschieht über das Definieren weiterer Eigenschaften.

**Teaser-Seite** Eine Teaser-Seite ist auf eine bestimmte Audience gerichtet. Sie enthält wiederverwendbare Inhalte, die in dem Teaser-Absatz verwendet werden können.

**Kampagne** Eine Kampagne ist eine Sammlung von Teaser-Seiten und E-Mail-Marketingseiten, z. B. Newsletter oder Einladungen. Eine Kampagne läuft in der Regel für eine begrenzte Zeitdauer und wird dann von einer anderen Kampagne abgelöst.

**Teaser-Absatz** Dieser Absatz bezieht Inhalte von einer anderen Seite, die von einer Auswahlstrategie abhängig ist. Bei dieser Auswahlstrategie können Segmente und Kampagnen berücksichtigt werden.

**Liste** A Liste wird aus einem Benutzersegment extrahiert. Beispielsweise der Ort, der verwendet wird, um die Inhalte des Teaser-Absatzes zu steuern.

>[!NOTE]
>
>Please see [Segmentation](/help/sites-administering/campaign-segmentation.md) for further information on segments in AEM.

