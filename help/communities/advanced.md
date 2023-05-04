---
title: Erweiterte Scoring- und Badges
seo-title: Advanced Scoring and Badges
description: Einrichten der erweiterten Auswertung
seo-description: Setting up advanced scoring
uuid: 3854b668-729a-42b8-b7cd-5d5ec1ca8380
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 42fb3c50-8728-4897-ade9-6b839294a10e
role: Admin
exl-id: c9406aae-288e-4cdf-ac01-cb26b423639e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1177'
ht-degree: 2%

---

# Erweiterte Scoring- und Badges {#advanced-scoring-and-badges}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht {#overview}

Die erweiterte Bewertung ermöglicht die Vergabe von Abzeichen, um Mitglieder als Experten zu identifizieren. Bei der erweiterten Auswertung werden Punkte basierend auf der Menge zugewiesen. *und* Qualität des Inhalts, der von einem Mitglied erstellt wurde, während bei der einfachen Auswertung Punkte einfach anhand der Menge des erstellten Inhalts zugewiesen werden.

Dieser Unterschied beruht auf der Scoring-Engine, die zur Berechnung der Werte verwendet wird. Die grundlegende Scoring-Engine wendet einfache Mathematik an. Die erweiterte Scoring-Engine ist ein adaptiver Algorithmus, der aktive Mitglieder belohnt, die wertvolle und relevante Inhalte beisteuern, die durch die natürliche Sprachverarbeitung (NLP) eines Themas abgeleitet werden.

Neben der Inhaltsrelevanz berücksichtigen die Scoring-Algorithmen Mitgliederaktivitäten wie Abstimmung und Prozentsatz der Antworten. Während die grundlegende Bewertung sie quantitativ beinhaltet, verwendet die erweiterte Auswertung sie algorithmisch.

Daher benötigt die erweiterte Scoring-Engine genügend Daten, um die Analyse sinnvoll zu gestalten. Die Erfolgsschwelle für die Expertenaktivität wird ständig neu bewertet, da sich der Algorithmus kontinuierlich an die Menge und Qualität der erstellten Inhalte anpasst. Es gibt auch ein Konzept von *Abfall* der älteren Beiträge eines Mitglieds. Wenn ein Expertenmitglied nicht mehr an dem Gegenstand teilnimmt, in dem es einen Sachverständigenstatus erlangt hat, zu einem bestimmten Zeitpunkt (siehe [Konfiguration der Scoring-Engine](#configurable-scoring-engine)) könnten sie ihren Status als Experte verlieren.

Die Einrichtung der erweiterten Auswertung ist praktisch identisch mit der grundlegenden Auswertung:

* Grundlegende und erweiterte Scoring- und Badging-Regeln sind [auf Inhalt angewendet](implementing-scoring.md#apply-rules-to-content) in gleicher Weise
   * Einfache und erweiterte Scoring- und Badging-Regeln können auf denselben Inhalt angewendet werden
* [Aktivieren von Abzeichen für Komponenten](implementing-scoring.md#enable-badges-for-component) ist generisch

Bei der Einrichtung der Scoring- und Badging-Regeln gibt es folgende Unterschiede:

* Konfigurierbare erweiterte Scoring-Engine
* Erweiterte Scoring-Regeln:
   * `scoringType` auf **[!UICONTROL advanced]**
   * Erfordert Stoppwörter

* Erweiterte Badging-Regeln:
   * `badgingType` auf **[!UICONTROL advanced]**
   * `badgingLevels` Anzahl der zu vergebenden Expertenebenen
   * Erfordert `badgingPaths` Array von Abzeichen anstelle von Schwellenwerten Array-Zuordnungspunkten zu Abzeichen

>[!NOTE]
>
>Um erweiterte Scoring- und Badging-Funktionen zu verwenden, installieren Sie die [Expertenkennungspaket](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq610%2Fsocial%2Ffeaturepack%2Fcq-social-expert-identification-pkg).

## Konfigurierbare Scoring-Engine {#configurable-scoring-engine}

Die erweiterte Scoring-Engine bietet eine OSGi-Konfiguration mit Parametern, die sich auf den erweiterten Scoring-Algorithmus auswirken.

![chlimage_1-260](assets/chlimage_1-260.png)

* **[!UICONTROL Scoring-Gewichtungen]**
Geben Sie für ein Thema das Verb an, dem bei der Berechnung des Ergebnisses die höchste Priorität eingeräumt werden soll. Ein oder mehrere Themen können eingegeben werden, jedoch auf **ein Verb pro Thema**. Siehe [Themen und Verben](implementing-scoring.md#topics-and-verbs).

   Eingestiegen als `topic,verb` mit Escapezeichen. Beispiel:

   `/social/forum/hbs/social/forum\,ADD`

   Standardmäßig ist das ADD-Verb für QnA- und Forenkomponenten festgelegt.


* **[!UICONTROL Scoring-Bereich]**

   Der Bereich für erweiterte Bewertungen wird durch diesen Wert (maximal mögliche Punktzahl) und 0 (niedrigstmögliche Punktzahl) definiert.

   Der Standardwert ist 100, sodass der Scoring-Bereich zwischen 0 und 100 liegt.


* **[!UICONTROL Zeitintervall für Entitätsverfall]**

   Dieser Parameter stellt die Anzahl der Stunden dar, nach denen alle Entitätsbewertungen veraltet sind. Dies ist erforderlich, um alte Inhalte nicht mehr in Bewertungen für eine Community-Site aufzunehmen.

   Der Standardwert ist 216000 Stunden (~24 Jahre).


* **[!UICONTROL Scoring-Wachstumsrate]**

   Gibt die Punktzahl an. zwischen 0 und Scoring-Bereich, über die das Wachstum langsamer zu begrenzen die Anzahl der Experten.

   Der Standardwert ist 50.

## Erweiterte Scoring-Regeln {#advanced-scoring-rules}

Bei der grundlegenden Bewertung ist die zum Verdienen eines Abzeichens erforderliche Menge bekannt.

Bei der erweiterten Auswertung wird die benötigte Menge ständig angepasst, basierend auf der Menge an Qualitätsdaten innerhalb des Systems. Die Auswertung wird kontinuierlich so berechnet, dass sie einer Glockenkurve ähnelt.

Wenn ein Mitglied ein Expertenabzeichen für ein Thema erhält, das nicht mehr aktiv ist, besteht die Möglichkeit, dass es sein Abzeichen aufgrund des Verfalls mit der Zeit verliert.

### ScoringType {#scoringtype}

Eine Scoring-Regel ist ein Satz von Scoring-Unterregeln, von denen jede die `scoringType`.

Um die erweiterte Scoring-Engine aufzurufen, muss die `scoringType`auf `advanced`.

Siehe [Scoring-Unterregeln](implementing-scoring.md#scoring-sub-rules).

![chlimage_1-261](assets/chlimage_1-261.png)

### Stoppwörter {#stopwords}

Das erweiterte Scoring-Paket installiert einen Konfigurationsordner, der eine stopwords -Datei enthält:

* `/etc/community/scoring/configuration/stopwords`

Der erweiterte Scoring-Algorithmus verwendet die Liste der in der Stoppwörter-Datei enthaltenen Wörter, um häufig verwendete englische Wörter zu identifizieren, die bei der Inhaltsverarbeitung ignoriert werden.

Es ist nicht zu erwarten, dass diese Datei geändert wird.

Wenn die Stoppwörter-Datei fehlt, gibt die erweiterte Scoring-Engine einen Fehler aus.

## Erweiterte Badging-Regeln {#advanced-badging-rules}

Die Eigenschaften der erweiterten Badging-Regel unterscheiden sich von der [Grundlegende Eigenschaften von Badging-Regeln](implementing-scoring.md#badging-rules).

Anstatt Punkte mit einem Badge-Bild zu verknüpfen, ist es nur erforderlich, die Anzahl der zulässigen Experten und das zu vergebende Badge-Bild zu identifizieren.

![chlimage_1-262](assets/chlimage_1-262.png)

| **Eigenschaft** | **Typ** | **Wertbeschreibung** |
|---------------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| badgingPath | Zeichenfolge[] | (Erforderlich) Eine mehrwertige Zeichenfolge von Badge-Bildern bis zur Anzahl der badgingLevels. Die Badge-Bildpfade müssen so angeordnet sein, dass der erste an den höchsten Fachmann vergeben wird. Wenn es weniger Abzeichen gibt, als durch badgingLevels angegeben, füllt das letzte Abzeichen im Array den Rest des Arrays aus. Beispieleintrag:/etc/community/badging/images/experte-badge/jcr:content/expert.png |
| badgingLevels | Long | (Optional) Gibt den Umfang des zu vergebenden Fachwissens an. Wenn es beispielsweise einen Experten und einen fast erfahrenen Benutzer (zwei Abzeichen) geben sollte, sollte der Wert auf 2 gesetzt werden. BadgingLevel sollte mit der Anzahl der von Experten verwendeten Badge-Bilder übereinstimmen, die für die badgingPath -Eigenschaft aufgelistet sind. Der Standardwert ist 1. |
| badgingType | Zeichenfolge | (Erforderlich) Identifiziert die Scoring-Engine entweder als &quot;Basis&quot;oder als &quot;Erweitert&quot;. Auf &quot;Erweitert&quot;gesetzt, andernfalls ist der Standardwert &quot;Standard&quot;. |
| scoringRules | Zeichenfolge[] | (Optional) Eine Zeichenfolge mit mehreren Werten, um die Badging-Regel auf die von den aufgelisteten Scoring-Regeln identifizierten Scoring-Ereignisse zu beschränken. Beispieleintrag:/etc/community/scoring/rules/adv-comments-scoringDefault ist keine Einschränkung. |

## Einbezogene Regeln und Zeichen {#included-rules-and-badge}

### Include Badge {#included-badge}

Diese Beta-Version beinhaltet ein belohnungsbasiertes Expertenabzeichen:

* Expert

   `/etc/community/badging/images/expert-badge/jcr:content/expert.png`

![chlimage_1-263](assets/chlimage_1-263.png)

Damit das Expertenabzeichen als Belohnung für Aktivitäten erscheint, müssen zwei Dinge geschehen:

* `badges` muss für die Funktion aktiviert sein, z. B. eine Forum- oder QnA-Komponente
* Erweiterte Scoring- und Badging-Regeln müssen auf die Seite (oder den Vorgänger) angewendet werden, auf der die Komponente platziert wird

Siehe die grundlegenden Informationen für:

* [Aktivieren von Abzeichen für eine Komponente](implementing-scoring.md#enable-badges-for-component)
* [Regeln anwenden](implementing-scoring.md#apply-rules-to-content)

### Einbezogene Scoring-Regeln und Unterregeln {#included-scoring-rules-and-sub-rules}

In der Beta-Version sind zwei erweiterte Scoring-Regeln für die [Forumsfunktion](functions.md#forum-function) (jeweils eine für die Foren- und Kommentarkomponenten der Forumsfunktion):

1. /etc/community/scoring/rules/adv-comments-scoring

   * `subRules[]` =

      /etc/community/scoring/rules/sub-rules/adv-comments-rule

      /etc/community/scoring/rules/sub-rules/adv-stimme-rule-owner

      /etc/community/scoring/rules/sub-rules/adv-voice-rule

2. /etc/community/scoring/rules/adv-forums-scoring

   * `subRules[]` =

      /etc/community/scoring/rules/sub-rules/adv-forums-rule

      /etc/community/scoring/rules/sub-rules/adv-comments-rule

      /etc/community/scoring/rules/sub-rules/adv-stimme-rule-owner

**Anmerkungen:**

* Beide `rules`und `sub-rules` Knoten sind vom Typ `cq:Page`
* `subRules` ist ein Attribut des Typs String[] zur Regel `jcr:content` Knoten
* `sub-rules` kann für verschiedene Scoring-Regeln freigegeben werden
* `rules` sollte sich in einem Repository-Speicherort mit Leserechte für alle befinden
   * Regelnamen müssen unabhängig vom Speicherort eindeutig sein.

### Einbezogene Badging-Regeln {#included-badging-rules}

In der Version sind zwei erweiterte Badging-Regeln enthalten, die dem [erweiterte Foren und Regeln zur Kommentarbewertung](#included-scoring-rules-and-sub-rules).

* /etc/community/badging/rules/adv-comments-badging
* /etc/community/badging/rules/adv-forums-badging

**Anmerkungen:**

* `rules` Knoten sind vom Typ `cq:Page`
* `rules`sollte sich in einem Repository-Speicherort mit Leserechte für alle befinden
   * Regelnamen müssen unabhängig vom Speicherort eindeutig sein.
