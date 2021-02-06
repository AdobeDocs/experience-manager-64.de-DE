---
title: Erweiterte Bewertung und Abzeichen
seo-title: Erweiterte Bewertung und Abzeichen
description: Einrichten der erweiterten Bewertung
seo-description: Einrichten der erweiterten Bewertung
uuid: 3854b668-729a-42b8-b7cd-5d5ec1ca8380
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 42fb3c50-8728-4897-ade9-6b839294a10e
translation-type: tm+mt
source-git-commit: ddf92a270835259998aa28f5960abcf55f56d1fc
workflow-type: tm+mt
source-wordcount: '1141'
ht-degree: 1%

---


# Erweiterte Bewertung und Abzeichen {#advanced-scoring-and-badges}

## Überblick {#overview}

Die erweiterte Bewertung ermöglicht die Vergabe von Kennzeichen, um Mitglieder als Experten zu identifizieren. Bei der erweiterten Bewertung werden Punkte basierend auf der Menge *und* der Qualität des Inhalts zugewiesen, der von einem Mitglied erstellt wurde, während bei der grundlegenden Bewertung Punkte nur auf der Grundlage der Menge des erstellten Inhalts zugewiesen werden.

Dieser Unterschied ist auf die Bewertungsmaschine zurückzuführen, die zur Berechnung der Ergebnisse verwendet wird. Die Basis-Scoring-Engine verwendet einfache Mathematik. Die Advanced Scoring Engine ist ein adaptiver Algorithmus, der aktive Mitglieder belohnt, die wertvollen und relevanten Inhalt beisteuern, der durch die natürliche Sprachverarbeitung (Natural Language Processing, NLP) eines Themas abgezogen wird.

Neben der Relevanz von Inhalten berücksichtigen die Bewertungsalgorithmen auch Aktivitäten von Mitgliedern, wie z. B. Abstimmung und Prozentsatz der Antworten. Während die grundlegende Bewertung sie quantitativ umfasst, verwendet die erweiterte Bewertung sie algorithmisch.

Daher benötigt die erweiterte Scoring-Engine genügend Daten, um eine aussagekräftige Analyse zu ermöglichen. Der Leistungsschwellenwert für die Expertenausbildung wird ständig neu bewertet, da sich der Algorithmus ständig an die Menge und Qualität der erstellten Inhalte anpasst. Es gibt auch ein Konzept für *decay* der älteren Beiträge eines Mitglieds. Wenn ein Expertenmitglied nicht mehr an dem Thema teilnimmt, in dem es einen Expertenstatus erlangt hat, könnte es an einem bestimmten Punkt (siehe [Konfiguration der bewerteten Engine](#configurable-scoring-engine)) seinen Status als Experte verlieren.

Die Einrichtung einer erweiterten Bewertung ist praktisch identisch mit der eines Basisscorings:

* Grundlegende und erweiterte Scoring- und Kennzeichnungsregeln werden auf Inhalt](implementing-scoring.md#apply-rules-to-content) auf dieselbe Weise angewendet[
   * Grundlegende und erweiterte Scoring- und Kennzeichnungsregeln können auf denselben Inhalt angewendet werden
* [Aktivieren von Kennzeichen für ](implementing-scoring.md#enable-badges-for-component) Komponenten generisch

Die verschiedenen Regeln für die Bewertung und Kennzeichnung unterscheiden sich:

* Konfigurierbare erweiterte Scoring-Engine
* Erweiterte Bewertungsregeln:
   * `scoringType` auf  **[!UICONTROL erweitert einstellen]**
   * Stoppwörter erforderlich

* Erweiterte Kennzeichnungsregeln:
   * `badgingType` auf  **[!UICONTROL erweitert einstellen]**
   * `badgingLevels` auf die Anzahl der zu vergebenden Expertenstufen
   * Erfordert ein `badgingPaths`-Array von Kennzeichen anstelle von Schwellenwerten für Array-Zuordnungspunkten zu Kennzeichen

>[!NOTE]
>
>Um erweiterte Scoring- und Abzeichen-Funktionen zu verwenden, installieren Sie das [Expert Identification-Paket](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/cq-social-expert-identification-pkg).

## Konfigurierbare Scoring-Engine {#configurable-scoring-engine}

Die erweiterte Scoring-Engine bietet eine OSGi-Konfiguration mit Parametern, die sich auf den erweiterten Scoring-Algorithmus auswirken.

![chlimage_1-260](assets/chlimage_1-260.png)

* **[!UICONTROL Bewertungsgewichte]**
Geben Sie für ein Thema das Verb an, dem bei der Berechnung des Ergebnisses die höchste Priorität eingeräumt werden soll. Es können ein oder mehrere Themen eingegeben werden, jedoch nur **ein Verb pro Thema**. Siehe [Themen und Verben](implementing-scoring.md#topics-and-verbs).

   Wird als `topic,verb` mit Escape-Zeichen eingegeben. Beispiel:

   `/social/forum/hbs/social/forum\,ADD`

   Die Standardeinstellung ist auf das HINZUFÜGEN Verb für QnA- und Forumkomponenten festgelegt.


* **[!UICONTROL Bewertungsbereich]**

   Der Bereich für erweiterte Ergebnisse wird durch diesen Wert (maximal mögliche Punktzahl) und 0 (niedrigstmögliche Punktzahl) definiert.

   Der Standardwert ist 100, sodass der Bewertungsbereich zwischen 0 und 100 liegt.


* **[!UICONTROL Zeitintervall für Entitätsabbruch]**

   Dieser Parameter stellt die Anzahl der Stunden dar, nach denen alle Entitätsbewertungen veraltet sind. Dies ist erforderlich, damit alte Inhalte nicht mehr in Bewertungen für eine Community-Site einbezogen werden.

   Der Standardwert ist 216000 Stunden (~24 Jahre).


* **[!UICONTROL Bewertungswachstumsrate]**

   Dies gibt das Ergebnis an. zwischen 0 und einer Bewertungsspanne, über die das Wachstum langsamer wird, um die Anzahl der Experten zu begrenzen.

   Der Standardwert ist 50.

## Erweiterte Scoring-Regeln {#advanced-scoring-rules}

In der Grundbewertung ist die Menge, die benötigt wird, um ein Zeichen zu verdienen, bekannt.

Bei der erweiterten Bewertung wird die benötigte Menge ständig an die Menge der Qualitätsdaten innerhalb des Systems angepasst. Die Bewertung wird kontinuierlich auf eine Weise berechnet, die einer Glockenkurve ähnlich ist.

Wenn ein Mitglied ein Expertenabzeichen zu einem Thema erhält, das nicht mehr aktiv ist, besteht die Möglichkeit, dass es sein Abzeichen aufgrund des Verfalls mit der Zeit verliert.

### ScoringType {#scoringtype}

Eine Bewertungsregel ist ein Satz von Scoring-Unterregeln, von denen jede das `scoringType` deklariert.

Um die erweiterte Scoring-Engine aufzurufen, muss `scoringType`auf `advanced` eingestellt sein.

Siehe [Scoring-Unterregeln](implementing-scoring.md#scoring-sub-rules).

![chlimage_1-261](assets/chlimage_1-261.png)

### Stoppwörter {#stopwords}

Das erweiterte Bewertungspaket installiert einen Konfigurationsordner, der eine stopwords-Datei enthält:

* `/etc/community/scoring/configuration/stopwords`

Der erweiterte Bewertungsalgorithmus verwendet die Liste der Wörter, die in der Stoppwortdatei enthalten sind, um häufig verwendete englische Wörter zu identifizieren, die bei der Inhaltsverarbeitung ignoriert werden.

Es wird nicht erwartet, dass diese Datei geändert wird.

Wenn die stopwords-Datei fehlt, gibt die erweiterte Scoring-Engine einen Fehler aus.

## Erweiterte Kennzeichnungsregeln {#advanced-badging-rules}

Die Eigenschaften der erweiterten Kennzeichnungsregel unterscheiden sich von den Eigenschaften der [grundlegenden Kennzeichnungsregel](implementing-scoring.md#badging-rules).

Anstatt Punkte mit einem Abzeichen zu verknüpfen, ist es nur notwendig, die Anzahl der zulässigen Experten und das zu vergebende Abbild zu identifizieren.

![chlimage_1-262](assets/chlimage_1-262.png)

| **Eigenschaft** | **Typ** | **Wertbeschreibung** |
|---------------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| badgingPath | Zeichenfolge[] | (Erforderlich) Eine Zeichenfolge mit mehreren Werten für Abzeichen bis zur Anzahl der badgingLevels. Die Abzeichen-Bildpfade müssen so angeordnet sein, dass der erste dem höchsten Fachmann verliehen wird. Wenn weniger Zeichen vorhanden sind als durch badgingLevels angegeben, füllt das letzte Zeichen im Array den Rest des Arrays aus. Beispieleintrag:/etc/community/badging/images/expertenbadge/jcr:content/expert.png |
| badgingLevels | Long | (Optional) Gibt die zu vergebenden Fachkenntnisse an. Wenn beispielsweise ein Experte und ein fast Experte (zwei Abzeichen) vorhanden sein sollten, sollte der Wert auf 2 gesetzt werden. Die badgingLevel-Eigenschaft sollte mit der Anzahl der Kennzeichnungsbilder für Experten übereinstimmen, die für die badgingPath-Eigenschaft aufgelistet sind. Der Standardwert ist 1. |
| badgingType | Zeichenfolge | (Erforderlich) Identifiziert die Scoring-Engine entweder als &quot;Basis&quot;oder als &quot;Erweitert&quot;. Auf &quot;advanced&quot;gesetzt, andernfalls ist der Standard &quot;basic&quot;. |
| scoringRules | Zeichenfolge[] | (Optional) Eine Zeichenfolge mit mehreren Werten, mit der die Kennzeichnungsregel auf von der/den aufgeführten Bewertungsregel(n) identifizierte Ereignis beschränkt wird.Beispieleintrag:/etc/community/scoring/rules/adv-comments-scoringDefault ist keine Einschränkung. |

## Einschließlich Regeln und Zeichen {#included-rules-and-badge}

### Einschließlich Badge {#included-badge}

In dieser Beta-Version ist ein auf Belohnung basierendes Expertenabzeichen enthalten:

* Expert

   `/etc/community/badging/images/expert-badge/jcr:content/expert.png`

![chlimage_1-263](assets/chlimage_1-263.png)

Damit das Expertenzeichen als Belohnung für Aktivität erscheinen kann, müssen zwei Dinge geschehen:

* `badges` muss für die Funktion aktiviert sein, z. B. eine Forum- oder QnA-Komponente
* erweiterte Scoring- und Kennzeichnungsregeln müssen auf die Seite (oder den Vorgänger) angewendet werden, auf der die Komponente platziert wird

Die Basisinformationen finden Sie unter:

* [Aktivieren der Markierung für eine Komponente](implementing-scoring.md#enable-badges-for-component)
* [Anwenden von Regeln](implementing-scoring.md#apply-rules-to-content)

### Einbezogene Bewertungsregeln und Unterregeln {#included-scoring-rules-and-sub-rules}

In der Beta-Version sind zwei erweiterte Bewertungsregeln für die [Forum-Funktion](functions.md#forum-function) enthalten (eine für die Foren- und Kommentarkomponenten der Forumsfunktion):

1. /etc/community/scoring/rules/adv-comments-scoring

   * `subRules[]` =

      /etc/community/scoring/rules/sub-rules/adv-comments-rule

      /etc/community/scoring/rules/sub-rules/adv-stimmungs-rule-owner

      /etc/community/scoring/rules/sub-rules/adv-stimmregel

2. /etc/community/scoring/rules/adv-forums-scoring

   * `subRules[]` =

      /etc/community/scoring/rules/sub-rules/adv-forums-rule

      /etc/community/scoring/rules/sub-rules/adv-comments-rule

      /etc/community/scoring/rules/sub-rules/adv-stimmungs-rule-owner

**Hinweise:**

* Die Knoten `rules`und `sub-rules` sind vom Typ `cq:Page`
* `subRules` ist ein Attribut des Typs [] Stringon der  `jcr:content` Knoten der Regel
* `sub-rules` kann für verschiedene Bewertungsregeln freigegeben werden
* `rules` sollte sich in einem Repository mit Leserechte für alle befinden
   * Regelnamen müssen unabhängig vom Ort eindeutig sein

### Einbezogene Kennzeichnungsregeln {#included-badging-rules}

In der Version sind zwei erweiterte Kennzeichnungsregeln enthalten, die mit den [erweiterten Foren und Kommentarkennungsregeln](#included-scoring-rules-and-sub-rules) übereinstimmen.

* /etc/community/badging/rules/adv-comments-badging
* /etc/community/badging/rules/adv-forums-badging

**Hinweise:**

* `rules` Knoten sind vom Typ  `cq:Page`
* `rules`sollte sich in einem Repository mit Leserechte für alle befinden
   * Regelnamen müssen unabhängig vom Ort eindeutig sein
