---
title: Grundlegendes zur Segmentierung
seo-title: Understanding Segmentation
description: Die Segmentierung ist bei der Erstellung einer Kampagne eine grundlegende Überlegung. In den meisten Fällen müssen Segmente bereits definiert sein, bevor Sie mit der Kampagne beginnen.
seo-description: Segmentation is a key consideration when creating a campaign. In most cases, you will need to have segments already defined before starting your campaign.
uuid: 609d83b3-df0e-44ad-8e27-90b676d2666b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: bb75f4ab-d983-45f6-98a3-da8bd9b63751
exl-id: 441cf983-e1dc-4343-9c2c-e5ed5891e84b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '601'
ht-degree: 70%

---

# Grundlegendes zur Segmentierung{#understanding-segmentation}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die Segmentierung ist bei der Erstellung einer Kampagne eine grundlegende Überlegung. In den meisten Fällen müssen Segmente bereits definiert sein, bevor Sie mit der Kampagne beginnen.

Besucher von Websites haben unterschiedliche Interessen und Ziele, wenn sie eine Site besuchen. Diese Ziele zu verstehen und die Erwartungen zu erfüllen, ist ein wichtiger Erfolgsfaktor für Online-Marketing.

Die Segmentierung hilft dabei, die folgenden Punkte eines Besuchers zu analysieren und zu charakterisieren:

* Aktivität auf der Website
* Profil
* Aktivitäten auf anderen Websites

Inhalte können dann entsprechend den jeweiligen Segmenten speziell auf die Bedürfnisse und Interessen des Besuchers abgestimmt werden.

## Verwenden von Segmentierung {#using-segmentation}

Segmente werden definiert in [Konfigurieren der Segmentierung](/help/sites-administering/campaign-segmentation.md). Sie werden dazu verwendet, den tatsächlich für Zielgruppen sichtbaren Inhalt zu steuern.

## Segmentierungsterminologie {#segmentation-terminology}

Im Rahmen der Segmentierung wird die folgende Terminologie verwendet:

**Besucherin/Besucher**: Eine Besucherin bzw. ein Besucher ist eine Person, die eine Website besucht. Der Besuch dieser Person beginnt in der Regel auf einer verweisenden Seite und geht dann über auf eine oder mehrere Seitenansichten auf Ihrer eigenen Website. Aus den Details des Besuchs dieser Person kann ein Verhaltensprofil erstellt werden.

**Benutzerin/Benutzer**: Eine Benutzerin bzw. ein Benutzer ist eine Besucherin oder ein Besucher, die/der sich bei der Website registriert, um ein Kontoprofil zu erhalten. Um ein Profil zu erstellen, geben Benutzer weitere Informationen zu ihrer Person an, z. B. eine E-Mail-Adresse oder ihr Geschlecht. Es können auch weitere Informationen erfasst werden, beispielsweise Aktivität in der Community und Kaufmuster. Basierend auf den im Profil angegebenen Informationen kann ein demografisches Profil erstellt werden.

**Eigenschaft**: Eine Eigenschaft ist ein Merkmal oder eine Charakteristik einer Besucherin oder eines Besuchers, das bzw. die verwendet werden kann, um die Zugehörigkeit zu einem bestimmten Segment zu bestimmen.

**Segment**: Ein Segment ist eine Sammlung von Besuchenden, die bestimmte Eigenschaften gemeinsam haben. Segmente sollten klar voneinander getrennt sein und so wenig Überlappung wie möglich mit anderen Segmenten aufweisen.

**Verhaltenseigenschaften**: Bei Verhaltenseigenschaften handelt es sich um die Eigenschaften, die sich auf das Verhalten einer Besucherin oder eines Besuchers auf einer Website beziehen. Dazu gehören:

* Interessensgebiete auf Ihrer Website, einschließlich besuchter Seiten und gekaufter Produkte.
* Interessensgebiete auf der verweisenden Website, einschließlich verwendeter Suchbegriffe oder Anzeigen, auf die geklickt wurde.
* Interessensgebiete auf anderen Sites, die durch Tools wie Spyjax ermittelt werden.
* Besucherloyalität; Dauer des Besuchs, Häufigkeit der Besuche.

**Demografische Eigenschaften**: Dabei handelt es sich um ausgewählte Merkmale der Population, darunter:

* Alter
* Einkommen
* Familiengröße
* Familienstand
* Geschlecht
* Standort

**Abgeleitete Eigenschaften**  

Einige demografische Eigenschaften lassen sich ohne Registrierung nur schwer ermitteln, können jedoch durch Kombination von Verhaltens- und demografischen Eigenschaften abgeleitet werden.

Beispielsweise können Besitzer von Sites durch Kombination der verweisenden URL (als Verhaltenseigenschaft) mit demografischen Informationen (ermittelt mithilfe von Tools wie [Google Ad Planner](https://www.google.com/adplanner/)) demografische Eigenschaften ihrer Besucher ableiten.

**Untersegment**: Ein Segment kann in mehrere Untersegmente unterteilt werden. Dies geschieht über das Definieren weiterer Eigenschaften.

**Teaser-Seite**: Eine Teaser-Seite richtet sich an eine bestimmte Zielgruppe. Sie enthält wiederverwendbare Inhalte, die in dem Teaser-Absatz verwendet werden können.

**Kampagne**: Bei einer Kampagne handelt es sich um eine Sammlung von Teaser-Seiten und E-Mail-Marketing-Seiten, z. B. Newsletter oder Einladungen. Eine Kampagne läuft in der Regel für eine begrenzte Zeitdauer und wird dann von einer anderen Kampagne abgelöst.

**Teaser-Absatz**: Dies ist ein Absatz, der Inhalte in Abhängigkeit von einer Auswahlstrategie von einer anderen Seite abruft. Bei dieser Auswahlstrategie können Segmente und Kampagnen berücksichtigt werden.

**Liste**: Eine Liste wird aus einem Segment registrierter Benutzerinnen und Benutzer extrahiert. Beispielsweise der Ort, der verwendet wird, um die Inhalte des Teaser-Absatzes zu steuern.

>[!NOTE]
>
>Weitere Informationen zu Segmenten in AEM finden Sie unter [Segmentierung](/help/sites-administering/campaign-segmentation.md).
