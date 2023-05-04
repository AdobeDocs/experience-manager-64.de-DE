---
title: Erstellung barrierefrei zugänglicher Inhalte (in Übereinstimmung mit den WCAG 2.0-Richtlinien)
seo-title: Creating Accessible Content (WCAG 2.0 Conformance)
description: Barrierefreies Nutzen von Web-Inhalten durch Personen mit Behinderungen
seo-description: Help make web content accessible to, and usable by, persons with disabilities
uuid: 416be3a1-6f02-4911-a69e-cae1825ee022
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 3d4258de-c0bb-4952-b6f0-0c5f2a15e531
exl-id: f792a65d-35f5-4143-bec2-c64de3f567b4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '8959'
ht-degree: 59%

---

# Erstellung barrierefrei zugänglicher Inhalte (in Übereinstimmung mit den WCAG 2.0-Richtlinien) {#creating-accessible-content-wcag-conformance}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

WCAG 2.0 umfasst eine Reihe technologieunabhängiger Richtlinien und Erfolgskriterien, die Sie bei der Erstellung von Web-Inhalten unterstützen, die für Personen mit Behinderungen barrierefrei zugänglich sind.

>[!NOTE]
>
>Siehe auch:
>
>* our [Kurzanleitung zu WCAG 2.0](/help/managing/qg-wcag.md) für weitere Informationen
>* [Konfigurieren des Rich-Text-Editors (RTE) für die Erstellung von barrierefrei zugänglichen Inhalten](/help/sites-administering/rte-accessible-content.md)
>


Diese werden nach drei Konformitätsstufen bewertet: Level A (niedrigste), Level AA und Level AAA (höchste). Die Ebenen werden kurz wie folgt definiert:

* **Stufe A:** Ihre Site erreicht eine einfache, minimale Barrierefreiheit. Bei Erreichen dieser Stufe sind alle Kategorie-A-Erfolgskriterien erfüllt.
* **Level AA:** Dies ist ein ideales Level der Barrierefreiheit, das Sie anstreben sollten. Auf diesem Level erreicht Ihre Site ein höheres Maß an Barrierefreiheit, da sie für die meisten Menschen in den meisten Situationen mit den meisten Technologien barrierefrei zugänglich ist. Um dieses Level zu erreichen, müssen alle Erfolgskriterien von Level A und Level AA erfüllt sein.
* **Stufe AAA:** Ihre Site erreicht eine sehr hohe Barrierefreiheit. Bei Erreichen dieser Stufe sind alle Kategorie-A-, -AA- und -AAA-Erfolgskriterien erfüllt.

Bei der Erstellung der Site sollten Sie festlegen, welchen Level Ihre Site insgesamt erfüllen soll.

Im folgenden Abschnitt finden Sie die [WCAG 2.0-Richtlinien](https://www.w3.org/TR/WCAG20/#guidelines) mit den entsprechenden Erfolgskriterien für die [Konformitäts-Level](https://www.w3.org/TR/UNDERSTANDING-WCAG20/conformance.html) Level A und Level AA.

>[!NOTE]
>
>Da es nicht möglich ist, alle Erfolgskriterien der Stufe AAA für bestimmte Inhaltstypen zu erfüllen, wird davon abgeraten, diese Konformität als allgemeine Richtlinie zu verlangen.

>[!NOTE]
>
>In diesem Dokument verwenden wir Folgendes:
>
>* Die Kurznamen für die [WCAG 2.0-Richtlinien](https://www.w3.org/TR/WCAG20/#guidelines).
>* Die Nummerierung der [WCAG 2.0-Richtlinien](https://www.w3.org/TR/WCAG20/#guidelines) zur Erleichterung von Querverweisen zur WCAG-Website.
>


## Grundsatz 1: Erkennbar     {#principle-perceivable}

[Grundsatz 1: Erkennbar – Informationen und Komponenten der Benutzeroberfläche müssen für die Benutzer so dargestellt sein, dass sie sie erkennen können.](https://www.w3.org/TR/WCAG20/#perceivable)

### Textalternativen (1.1) {#text-alternatives}

[Richtlinie 1.1 Textalternativen: Bieten Sie Textalternativen für nichttextliche Inhalte, damit sie in andere Formate geändert werden, die von bestimmten Personen benötigt werden, wie zum Beispiel Großdruck, Braille, Sprache, Symbole oder einfachere Sprache.](https://www.w3.org/TR/WCAG20/#text-equiv)

### Nichttextlicher Inhalt (1.1.1) {#non-text-content}

* Erfolgskriterium 1.1.1
* Level A
* Nichttextlicher Inhalt: Alle nichttextlichen Inhalte, die Benutzern präsentiert werden, haben eine Textalternative, die dem jeweiligen Zweck entspricht, ausgenommen die unten aufgeführten Situationen.

#### Zweck: Nichttextliche Inhalte (1.1.1) {#purpose-non-text-content}

Informationen auf einer Webseite können in vielen verschiedenen nichttextlichen Formaten wie Bildern, Videos, Animationen, Diagrammen und Grafiken bereitgestellt werden. Blinde Personen oder Personen mit schweren Sehbehinderungen können keinen nichttextlichen Inhalt anzeigen, können jedoch auf Textinhalte zugreifen, indem sie ihn von einer Bildschirmlesehilfe lesen lassen oder von einem Braille-Anzeigegerät in taktiler Form präsentiert werden. Indem Sie also Textalternativen zu Inhalten im grafischen Format bereitstellen, können Personen, die den grafischen Inhalt nicht sehen können, auf eine äquivalente Version der Informationen zugreifen, die der Inhalt bereitstellt.

Ein nützlicher weiterer Vorteil besteht darin, dass Textalternativen es ermöglichen, nichttextliche Inhalte durch Suchmaschinentechnologie zu indizieren.

#### Erfüllen: Nichttextlicher Inhalt (1.1.1) {#how-to-meet-non-text-content}

Bei statischen Grafiken besteht die Grundanforderung darin, eine gleichwertige Textalternative für die Grafik bereitzustellen. Dies kann im Abschnitt **Alternativtext** -Feld:

>[!NOTE]
>
>Einige integrierte Komponenten wie **Karussell** und **Dia-Show** bieten keine Möglichkeit zum Hinzufügen von alternativen Textbeschreibungen zu Bildern. Wenn Sie Versionen davon für Ihre AEM-Instanz implementieren, muss Ihr Entwicklungs-Team diese Komponenten so konfigurieren, dass das `alt`-Attribut unterstützt wird, damit Autoren es dem Inhalt hinzufügen können (siehe [Hinzufügen von Support für weitere HTML-Elemente und -Attribute](/help/sites-administering/rte-accessible-content.md#adding-support-for-additional-html-elements-and-attributes)).

Die **Alternativtext** -Feld im **Bild** Komponentendialogfeld auf **Metadaten** tab:

![Dialogfeld &quot;Bearbeiten&quot;der Bildkomponente in der Touch-optimierten Benutzeroberfläche; zeigt das Feld ALT-Text an.](assets/screen_shot_2018-03-21at165045.png)

In AEM muss das Feld **Alternativtext** standardmäßig ausgefüllt werden. Wenn das Bild rein dekorativ ist und Alternativtext unsinnig wäre, wird das **Bild ist dekorativ** -Option aktiviert werden.

#### Erstellen guter Textalternativen {#creating-good-text-alternatives}

Es gibt verschiedene Arten von nichttextlichem Inhalt. Daher hängt der Wert der Textalternative von der Rolle ab, die die Grafik auf der Web-Seite spielt. Zu den allgemeinen Faustregeln gehören:

* Textalternativen sollten kurz sein, doch sollten sie die wesentlichen Informationen, die durch den nichttextlichen Inhalt bereitgestellt werden, eindeutig erfassen.
* Übermäßig lange Beschreibungen (über 100 Zeichen) sollten vermieden werden. Wenn eine Textalternative mehr Details erfordert:

   * Geben Sie im Alternativtext eine kurze Beschreibung an
   * und fügen Sie irgendwo anders auf der entsprechenden Seite oder auf einer anderen Web-Seite eine längere Beschreibung ein. Verlinken Sie auf diese separate Beschreibung, indem Sie das Bild mit einem Link unterlegen oder indem Sie neben das Bild einen Text-Link platzieren.

* Alternativer Text sollte keine Inhalte replizieren, die in Textformularen bereitgestellt werden, die sich in der Nähe auf derselben Seite befinden. Beachten Sie, dass viele Bilder Abbildungen von Punkten sind, die bereits im Text einer Seite behandelt werden, sodass möglicherweise bereits eine detaillierte Textalternative vorhanden ist.
* Wenn der nichttextliche Inhalt ein Link zu einer anderen Seite oder zu einem anderen Dokument ist und kein anderer Text Teil desselben Links ist, muss der alternative Text für das Bild das Ziel des Links angeben, nicht das Bild beschreiben.
* Wenn der nichttextliche Inhalt in einem Schaltflächenelement enthalten ist und kein Text Teil derselben Schaltfläche ist, muss der alternative Text des Bildes die Funktionalität der Schaltfläche angeben, nicht das Bild beschreiben.
* Es ist völlig in Ordnung, wenn für ein Bild ein leerer Alternativtext (null) angegeben wird, allerdings nur dann, wenn das Bild keinen Alternativtext hat (wenn es sich beispielsweise nur um eine dekorative Grafik handelt) oder der entsprechende Text bereits im Seitentext vorhanden ist.

Die [W3C-Entwurf: HTML5 Techniken zur Bereitstellung nützlicher Textalternativen](https://dev.w3.org/html5/alt-techniques/) verfügt über weitere Details und Beispiele für die Bereitstellung geeigneter alternativer Texte für Bilder unterschiedlicher Typen.

Bestimmte Arten von nichttextlichem Inhalt, für den Textalternativen erforderlich sind:

* Veranschaulichende Fotos:
Hierbei handelt es sich um Bilder von Menschen, Objekten oder Orten. Denken Sie an die Rolle des Fotos auf der Seite. ein angemessenes Textäquivalent wahrscheinlich *Foto von [Objekt]*, kann jedoch vom umliegenden Text abhängen.
* Symbole: Hierbei handelt es sich um kleine Piktogramme (Grafiken), die bestimmte Informationen vermitteln. Sie müssen durchgängig auf einer Seite und Site verwendet werden. Alle Instanzen des Symbols auf einer Seite oder Site sollten dieselbe kurze und knappe Textalternative aufweisen, es sei denn, dass dadurch eine unnötige Verdoppelung von bereits vorhandenem Text erzeugt würde.
* Diagramme: Normalerweise werden dadurch numerische Daten dargestellt. So könnte als eine Möglichkeit zur Bereitstellung von Alternativtext eine kurze Zusammenfassung der im Diagramm gezeigten Haupt-Trends eingefügt werden. Fall nötig, können Sie eine detailliertere Textbeschreibung im Feld **Beschreibung** auf der Registerkarte **Erweiterte Bildeigenschaften** einfügen. Außerdem könnten Sie die Quelldaten an anderer Stelle auf der Seite oder Site als Tabelle zur Verfügung stellen.

   ![Beispiel eines Diagramms. Nachfolgend sehen Sie einen bewährten Ansatz zur Bereitstellung einer Alternative.](assets/chlimage_1.jpeg)

   Zur Bereitstellung einer Alternative für dieses Beispieldiagramm können Sie dem Bild selbst einen knappen `alt`-Text hinzufügen und dann dem Bild eine vollständige Textalternative folgen lassen.

   ```xml
   <p><img src="figure1.gif" alt="Figure 1" ></p>
   <p> Figure 1. Distribution of Articles by Journal Category.
   Pie chart: Language=68%, Education=14% and Science=18%.</p>
   ```

   >[!NOTE]
   >
   >Der obige Ausschnitt dient nur zur Veranschaulichung der Reihenfolge. Es wird empfohlen, die Komponente **Bild** (statt des oben verwendeten `img src`-Verweises) zu verwenden.

   In AEM können Sie dies anhand einer Kombination der Felder **ALT-Text** und **Beschreibung** im Konfigurationsdialogfeld des Bildes erreichen, wie in [Erfüllen: Nichttextlicher Inhalt (1.1.1)](#how-to-meet-non-text-content).

* Karten, Diagramme, Flussdiagramme: Für Grafiken mit räumlichen Daten (z. B. um Beziehungen zwischen Objekten oder einem Prozess zu beschreiben), stellen Sie sicher, dass die Schlüsselmeldung im Textformat bereitgestellt wird. Bei Karten ist die Bereitstellung eines Volltextäquivalents wahrscheinlich nicht praktikabel, aber wenn die Karte bereitgestellt wird, um den Weg zu einer bestimmten Position zu erleichtern, kann der Alternativtext des Kartenbildes kurz *Karte von X* angeben und dann eine Wegbeschreibung zu dieser Position im Text an einer anderen Stelle auf der Seite oder über das Feld **Beschreibung** auf der Registerkarte **Erweitert** der Komponente **Bild** angeben.
* CAPTCHAs: Ein CAPTCHA ist ein *vollautomatischer öffentlicher Turing-Test zur Unterscheidung von Computern und Menschen*. Es handelt sich dabei um eine Sicherheitsprüfung, die auf Webseiten verwendet wird, um Menschen von böswilliger Software zu unterscheiden, was jedoch Barrierefreiheitsbarrieren verursachen kann. Hierbei handelt es sich um Bilder, bei denen Benutzer beschreiben müssen, was sie sehen, um einen Sicherheitstest bestehen zu können. Es ist offensichtlich nicht möglich, eine Textalternative für das Bild bereitzustellen. Daher müssen Sie stattdessen alternative nichtgrafische Lösungen in Betracht ziehen.

   Das W3C bietet eine Reihe von Vorschlägen. Diese Ansätze haben jedoch sowohl Vor- als auch Nachteile.

   * Logikpuzzles
   * Verwendung der Tonausgabe anstelle von Bildern
   * Eingeschränkte Benutzerkonten und Spam-Filter

* Hintergrundbilder: Diese werden mithilfe von Cascading Style Sheets (CSS) anstelle von HTML erreicht. Dies bedeutet, dass es nicht möglich ist, einen alternativen Textwert anzugeben. Daher sollten Hintergrundbilder keine wichtigen textlichen Informationen enthalten. Wenn sie dies tun, müssen diese Informationen auch im Text der Seite angegeben werden.

   Es ist jedoch wichtig, dass ein alternativer Hintergrund angezeigt wird, wenn das Bild nicht angezeigt werden kann.

   >[!NOTE]
   >
   >Es sollte ein Mindestmaß an Kontrast zwischen dem Hintergrund- und dem Vordergrundtext vorhanden sein; weitere Details hierzu finden Sie unter [Kontrast (Minimum) (1.4.3)](#contrast-minimum).

#### Weitere Informationen: Nichttextlicher Inhalt (1.1.1) {#more-information-non-text-content}

* [Erfolgskriterien 1.1.1 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/text-equiv-all.html)
* [Erfolgskriterien 1.1.1 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#text-equiv)
* [W3C: HTML5-Techniken zur Bereitstellung nützlicher Textalternativen (Entwurf)](https://dev.w3.org/html5/alt-techniques/)
* [W3C-Erklärung und Alternativen zu CAPTCHAs](https://www.w3.org/TR/turingtest/)

### Zeitbasierte Medien (1.2) {#time-based-media}

[Richtlinie 1.2 Zeitbasierte Medien: Stellen Sie Alternativen für zeitbasierte Medien bereit.](https://www.w3.org/TR/WCAG20/#text-equiv)

Diese Richtlinie behandelt Web-Inhalte, die *zeitbasiert* sind. Es handelt sich um Inhalte, die der Benutzer abspielen kann (wie Video, Audio und animierte Inhalte) und die entweder vorher aufgezeichnet wurden oder als Live-Stream verfügbar sind.

### Nur-Audio und Nur-Video (aufgezeichnet) (1.2.1) {#audio-only-and-video-only-pre-recorded}

* Erfolgskriterium 1.2.1
* Level A
* Nur-Audio und Nur-Video (aufgezeichnet): Für aufgezeichnete Nur-Audio- und aufgezeichnete Nur-Video-Medien ist Folgendes wahr, es sei denn, das Audio oder Video ist eine Medienalternative für Text und als solche eindeutig gekennzeichnet:

   * Nur aufgezeichnete Audio-Dateien: Es wird eine Alternative für zeitbasierte Medien bereitgestellt, die gleichwertige Informationen für aufgezeichnete Nur-Audio-Inhalte bereitstellen.
   * Nur aufgezeichnetes Video: Es wird entweder eine Alternative für zeitbasierte Medien oder ein Audio-Track bereitgestellt, der gleichwertige Informationen für aufgezeichnete Nur-Video-Inhalte enthält.

#### Zweck: Nur-Audio und Nur-Video (aufgezeichnet) (1.2.1)     {#purpose-audio-only-and-video-only-pre-recorded}

Probleme bei der Barrierefreiheit von Video und Audio können auftreten bei:

* Personen mit eingeschränkter Sehkraft, wenn kein Soundtrack vorhanden ist oder der Soundtrack nicht ausreicht, um sie über die Ereignisse im Video oder der Animation zu informieren;
* Menschen mit Hörbehinderungen oder taub, die den Soundtrack nicht hören können;
* Personen, die den Soundtrack hören können, aber nicht verstehen, was gesprochen wird (z. B. weil er in einer Sprache ist, die sie nicht verstehen).

Video- oder Audioinhalte stehen u. U. auch Personen nicht zur Verfügung, die Browser oder Geräte verwenden, die die Wiedergabe von Inhalten in bestimmten Medienformaten, z. B. Adobe Flash, nicht unterstützen.

Wenn Sie diese Informationen in einem anderen Format bereitstellen, z. B. Text (oder Audio für Video ohne Audio), können Sie sie für Personen verfügbar machen, die nicht auf den ursprünglichen Inhalt zugreifen können.

#### Erfüllen: Nur-Audio und Nur-Video (aufgezeichnet) (1.2.1)     {#how-to-meet-audio-only-and-video-only-pre-recorded}

* Wenn es sich bei dem Inhalt um aufgezeichnetes Audio ohne Video (wie zum Beispiel einen Podcast) handelt:

   * Stellen Sie direkt vor oder nach dem Inhalt einen Link zu einem Texttranskript des Audioinhalts bereit.

      Das Transkript sollte eine HTML-Seite mit einer Textentsprechung aller gesprochenen und wichtigen nicht gesprochenen Inhalte sein und den Sprecher, eine Beschreibung der Szenerie, sprachliche Ausdrücke und eine Beschreibung anderer wichtiger Audioinhalte angeben.

* Wenn es sich bei dem Inhalt um eine Animation oder ein aufgezeichnetes Video ohne Audio handelt:

   * Stellen Sie unmittelbar vor oder nach dem Inhalt einen Link zu einer entsprechenden Textbeschreibung der vom Video bereitgestellten Informationen bereit
   * Oder eine gleichwertige Audiobeschreibung in einem häufig verwendeten Audioformat wie MP3.

>[!NOTE]
>
>Wenn der Audio- oder Videoinhalt als Alternative zu Inhalten bereitgestellt wird, die bereits in einem anderen Format auf einer Web-Seite vorhanden sind, müssen die oben genannten Anforderungen nicht erfüllt werden. Wenn ein Video beispielsweise eine Liste von Textanweisungen veranschaulicht, ist für dieses Video keine Alternative erforderlich, da die Textanweisungen bereits als Alternative zum Video dienen.

Das Einfügen von Multimedia-Inhalten, insbesondere Flash-Inhalten, in Ihre AEM Webseiten ist ähnlich wie das Einfügen eines Bildes. Da Multimedia jedoch weit mehr ist als ein Standbild, gibt es eine Vielzahl von verschiedenen Einstellungen und Optionen zur Steuerung, wie die Multimedia-Inhalte abgespielt werden.

>[!NOTE]
>
>Wenn Sie Multimedia mit informativem Inhalt verwenden, müssen Sie auch Links zu Alternativen erstellen. Beispielsweise müssen Sie zum Hinzufügen eines Texttranskripts eine HTML-Seite für die Anzeige des Transkripts erstellen und dann neben oder unter dem Audioinhalt einen Link hinzufügen.

#### Weitere Informationen: Nur-Audio und Nur-Video (aufgezeichnet) (1.2.1) {#more-information-audio-only-and-video-only-pre-recorded}

* [Erfolgskriterien 1.2.1 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-av-only-alt.html)
* [Erfolgskriterien 1.2.1 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#media-equiv)

### Untertitel (aufgezeichnet) (1.2.2)     {#captions-pre-recorded}

* Erfolgskriterium 1.2.2
* Level A
* Untertitel (aufgezeichnet): Untertitel werden für alle aufgezeichneten Audioinhalte in synchronisierten Medien bereitgestellt, außer wenn das Medium eine Medienalternative für Text und als solche ausdrücklich gekennzeichnet ist.

#### Zweck: Untertitel (aufgezeichnet) (1.2.2)     {#purpose-captions-pre-recorded}

Gehörlose oder schwerhörige Menschen können Audioinhalte gar nicht oder nur schwer verstehen. Untertitel sind Textentsprechungen für gesprochene und nicht gesprochene Audioinhalte; sie werden im Video zum richtigen Zeitpunkt auf dem Bildschirm angezeigt und ermöglichen es Menschen, die das Audio nicht hören können, zu verstehen, was vor sich geht.

>[!NOTE]
>
>Untertitel sind nicht erforderlich, wenn auf derselben Seite wie das Video oder die Animation geeignete Text- oder Nicht-Text-Entsprechungen (die direkt gleichwertige Informationen bereitstellen) verfügbar sind.

#### Erfüllen: Untertitel (aufgezeichnet) (1.2.2)     {#how-to-meet-captions-pre-recorded}

Es gibt zwei Arten von Untertiteln:

* Offen: Immer sichtbar, wenn das Video abgespielt wird)
* Geschlossen: Benutzer können die Untertitel ein- oder ausschalten

Verwenden Sie möglichst geschlossene Untertitel, da Benutzer so wählen können, ob die Untertitel angezeigt werden.

Für geschlossene Untertitel müssen Sie eine synchronisierte Untertiteldatei in einem entsprechenden Format (wie [SMIL](https://www.w3.org/AudioVideo/)) erstellen und zusammen mit der Videodatei bereitstellen (Details dazu, wie dieser Vorgang ausgeführt wird, sind im Rahmen dieses Leitfadens nicht möglich, doch wir haben Ihnen Links zu einigen Lernprogrammen unter [Weitere Informationen: Untertitel (aufgezeichnet) (1.2.2)](#more-information-captions-pre-recorded) zusammengestellt). Stellen Sie sicher, dass Sie einen Hinweis bereitstellen, um den Benutzern mitzuteilen, dass Untertitel für das Video verfügbar sind.

Wenn Sie offene Untertitel verwenden müssen, betten Sie den Text in die Videospur ein. Dies erreichen Sie mithilfe von Programmen zur Videobearbeitung, die die Überlagerung von Untertiteln im Video ermöglichen.

#### Weitere Informationen: Untertitel (aufgezeichnet) (1.2.2)     {#more-information-captions-pre-recorded}

* [Erfolgskriterium 1.2.2 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-captions.html):
* [Erfolgskriterien 1.2.2 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#media-equiv)
* [W3C: Synchronisiertes Multimedia](https://www.w3.org/AudioVideo/)
* [Untertitel, Transkripte und Audiobeschreibungen – mit WebAIM](https://webaim.org/techniques/captions/)

### Audiobeschreibung oder Medienalternative (aufgezeichnet) (1.2.3)     {#audio-description-or-media-alternative-pre-recorded}

* Erfolgskriterium 1.2.3
* Level A
* Audiobeschreibung oder Medienalternative (aufgezeichnet): Eine Alternative für zeitbasierte Medien oder Audiobeschreibung des aufgezeichneten Videoinhalts wird für synchronisierte Medien bereitgestellt, es sei denn, das Medium ist eine Medienalternative für Text und ist als solche eindeutig gekennzeichnet.

#### Zweck: Audiobeschreibung oder Medienalternative (aufgezeichnet) (1.2.3)     {#purpose-audio-description-or-media-alternative-pre-recorded}

Blinde Menschen oder Menschen mit eingeschränktem Sehvermögen haben keinen Zugang zu Informationen in einem Video oder einer Animation, wenn diese nur visuell vermittelt werden oder wenn der Soundtrack nicht genügend Informationen bietet, damit sie verstehen können, was visuell gezeigt wird.

#### Erfüllen: Audiobeschreibung oder Medienalternative (aufgezeichnet) (1.2.3)     {#how-to-meet-audio-description-or-media-alternative-pre-recorded}

Es gibt zwei Ansätze, die angewendet werden können, um dieses Erfolgskriterium zu erfüllen. Beide sind zulässig:

1. Fügen Sie zusätzliche Audiobeschreibungen für den Videoinhalt hinzu. Dies lässt sich auf eine von drei Arten erreichen:

   * Geben Sie während der Pausen im vorhandenen Dialogfeld Informationen zu Änderungen in der Szene an, die nicht als Teil des vorhandenen Audio-Tracks angezeigt werden.
   * Stellen Sie einen neuen, zusätzlichen und optionalen Audio-Track bereit, der den ursprünglichen Soundtrack und zudem weitere Audioinformationen zu den Änderungen in der Szene enthält.

      * Dadurch können Benutzer zwischen dem vorhandenen Audio-Track (der *keine* Audiobeschreibung enthält) und dem neuen Audio-Track (*mit* einer Audiobeschreibung) wechseln.
      * Dadurch wird verhindert, dass Benutzer, die die zusätzliche Beschreibung nicht benötigen, gestört werden.
   * Erstellen Sie eine zweite Version des Videoinhalts, um erweiterte Audiobeschreibungen zu ermöglichen. Dadurch werden die Schwierigkeiten bei der Bereitstellung detaillierter Audiobeschreibungen innerhalb der Lücken zwischen dem bestehenden Dialog verringert, indem Audio und Video an geeigneten Punkten vorübergehend angehalten werden. Daher kann eine wesentlich längere Audiobeschreibung gegeben werden, bevor die Aktion erneut gestartet wird. Wie im vorherigen Beispiel ist dies am besten als optionaler zusätzlicher Audio-Track bereitgestellt, um Störungen bei Benutzern zu vermeiden, die die zusätzliche Beschreibung nicht benötigen.


1. Geben Sie ein Text-Transkript an, das den Audio- und visuellen Elementen des Videos oder der Animation entspricht. Dies sollte gegebenenfalls einen Hinweis darauf enthalten, wer spricht, eine Beschreibung der Einstellung, laute Ausdrücke. Je nach Länge können Sie das Transkript auf derselben Seite wie das Video oder die Animation oder auf einer separaten Seite platzieren. Wenn Sie die zweite Option wählen, geben Sie einen Link zum Transkript an, das an das Video oder die Animation angrenzt.

Genaue Details zum Erstellen von Audiobeschreibungen für Videos werden in diesem Handbuch nicht behandelt. Die Erstellung von Audiobeschreibungen kann zeitaufwendig sein, doch andere Adobe-Produkte helfen Ihnen bei diesen Aufgaben. Wenn Sie Inhalte in Adobe Flash Professional erstellen, sollten Sie auch ein Skript erstellen, um den Benutzer aufzufordern, das entsprechende Plug-in herunterzuladen. Zudem sollten Sie eine Textalternative anhand des Elements `<noscript>` bereitstellen.

#### Weitere Informationen: Audiobeschreibung oder Medienalternative (aufgezeichnet) (1.2.3) {#more-information-audio-description-or-media-alternative-pre-recorded}

* [Erfolgskriterien 1.2.3 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-audio-desc.html):
* [Erfolgskriterien 1.2.3 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-media-equiv-audio-desc)
* [Adobe Encore CS5](https://www.adobe.com/de/products/premiere/encore/)

### Untertitel (live) (1.2.4)          {#captions-live}

* Erfolgskriterium 1.2.4
* Level AA
* Untertitel (Live): Untertitel werden für alle Live-Audioinhalte in synchronisierten Medien bereitgestellt.

#### Zweck: Untertitel (Live) (1.2.4) {#purpose-captions-live}

Dieses Erfolgskriterium entspricht dem Erfolgskriterium zu [Untertitel (aufgezeichnet)](#captions-pre-recorded) insofern, als es Zugangsbarrieren behandelt, die gehörlose oder schwerhörige Menschen erfahren; der Unterschied besteht darin, dass dieses Erfolgskriterium Live-Präsentationen wie Webcasts behandelt.

#### Erfüllen: Untertitel (Live) (1.2.4) {#how-to-meet-captions-live}

Befolgen Sie die Anleitungen, die oben unter [Untertitel (aufgezeichnet)](#captions-pre-recorded) genannt wurden. Da die Medien live übermittelt werden, muss die Bereitstellung so schnell wie möglich erfolgen und sofort auf das reagieren, was passiert. Daher sollten Sie Tools für die Echtzeit-Untertitelung oder für Speech-to-Text in Erwägung ziehen.

Detaillierte Anweisungen dazu würden den Rahmen dieses Dokuments sprengen, doch in den folgenden Ressourcen finden Sie nützliche Informationen:

* [WebAIM: Echtzeit-Untertitelung](https://www.webaim.org/techniques/captions/realtime.php)
* [AccessIT (University of Washington): Können Untertitel automatisch über die Spracherkennung erstellt werden?](https://www.washington.edu/accessit/articles?1209)

#### Weitere Informationen: Untertitel (Live) (1.2.4)     {#more-information-captions-live}

* [Erfolgskriterien 1.2.4 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-real-time-captions.html)
* [Erfolgskriterien 1.2.4 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-media-equiv-real-time-captions)

### Audiobeschreibung (aufgezeichnet) (1.2.5)          {#audio-description-pre-recorded}

* Erfolgskriterium 1.2.5
* Level AA
* Audiobeschreibung (aufgezeichnet): Audiobeschreibung wird für alle aufgezeichneten Videoinhalte in synchronisierten Medien bereitgestellt.

#### Zweck: Audiobeschreibung (aufgezeichnet) (1.2.5)     {#purpose-audio-description-pre-recorded}

Dieses Erfolgskriterium entspricht dem Erfolgskriterium zu [Audiobeschreibung oder Medienalternative (aufgezeichnet)](#audio-description-or-media-alternative-pre-recorded), mit dem Unterschied, dass Autoren eine wesentlich detailliertere Audiobeschreibung verfassen müssen, um Level AA zu erfüllen.

#### Erfüllen: Audiobeschreibung (aufgezeichnet) (1.2.5)     {#how-to-meet-audio-description-pre-recorded}

Befolgen Sie die Anweisungen für [Audiobeschreibung oder Medienalternative (aufgezeichnet)](#audio-description-or-media-alternative-pre-recorded).

#### Weitere Informationen: Audiobeschreibung (aufgezeichnet) (1.2.5)     {#more-information-audio-description-pre-recorded}

* [Erfolgskriterien 1.2.5 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-audio-desc-only.html)
* [Erfolgskriterien 1.2.5 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-media-equiv-audio-desc-only)

### Anpassbar (1.3) {#adaptable}

[Richtlinie 1.3 Anpassbar: Erstellen Sie Inhalte, die auf unterschiedliche Weise präsentiert werden können (z. B. einfacheres Layout), ohne Informationen oder Struktur zu verlieren.](https://www.w3.org/TR/WCAG20/#content-structure-separation)

Diese Richtlinie deckt die Anforderungen ab, die zur Unterstützung von Personen erforderlich sind, die:

* kann möglicherweise nicht auf Informationen zugreifen, die von einem Autor in einer *standard* zweidimensionales, mehrspaltiges, farbiges Webseitenlayout

* Personen, die eine Nur-Audio-Darstellung oder alternative visuelle Darstellung wie Großdruck oder hohen Kontrast verwenden wollen.

### Informationen und Beziehungen (1.3.1)              {#info-and-relationships}

* Erfolgskriterium 1.3.1
* Level A
* Informationen und Beziehungen: Informationen, Struktur und Beziehungen, die durch die Präsentation vermittelt werden, können programmatisch bestimmt werden oder sind im Text verfügbar.

#### Zweck: Informationen und Beziehungen (1.3.1) {#purpose-info-and-relationships}

Viele Hilfstechnologien, die von Menschen mit Behinderungen genutzt werden, sind auf strukturelle Informationen angewiesen, um Inhalte effektiv anzeigen oder ausgeben zu können. Diese Strukturinformationen können in Form von Seitenüberschriften, Tabellenzeilen und Spaltenüberschriften sowie Listentypen vorliegen. Beispielsweise könnte eine Bildschirmlesehilfe einem Benutzer die Navigation von einer Überschrift zur nächsten ermöglichen. Wenn Seiteninhalte jedoch nur über visuelles Design und nicht über das zugrunde liegende HTML strukturiert zu sein scheinen, stehen für Hilfstechnologien keine Strukturinformationen zur Verfügung, sodass sie das Browsen beschränken können.

Dieses Erfolgskriterium besteht darin sicherzustellen, dass solche Strukturinformationen über HTML bereitgestellt werden, damit Browser und Hilfstechnologien auf die Informationen zugreifen und diese nutzen können.

#### Erfüllen: Informationen und Beziehungen (1.3.1)       {#how-to-meet-info-and-relationships}

AEM erleichtert den Aufbau von Web-Seiten mit den entsprechenden HTML-Elementen. Öffnen Sie Ihren Seiteninhalt im RTE (eine Textkomponente) und geben Sie im Menü **Paraformat** (Absatzsymbol) das entsprechende Strukturelement (zum Beispiel Absatz, Überschrift usw.) an.

Die folgende Abbildung zeigt Text, der als Absatztext formatiert wurde.

![Ein Beispiel des Absatz-Elements im Modus zur Bearbeitung des Quell-Codes (klassische Benutzeroberfläche).](assets/screen_shot_2018-03-21at165623.png)

Sie können folgendermaßen sicherstellen, dass Ihre Web-Seiten die entsprechende Struktur erhalten:

* **Verwendung von Überschriften:**  

   Solange die Barrierefreiheitsfunktionen des RTE aktiviert sind (siehe [AEM und Zugänglichkeit](#AdobeExperienceManagerandAccessibility)), bietet AEM drei Ebenen für Seitenüberschriften. Sie können diese verwenden, um Abschnitte und Unterabschnitte des Inhalts zu identifizieren. Überschrift 1 ist die höchste Überschriftenebene, Überschrift 3 die niedrigste. Der Systemadministrator kann das System so konfigurieren, dass mehr Überschriftenebenen verwendet werden können.

   Im folgenden Bild ist ein Beispiel der verschiedenen Überschriftentypen zu sehen.

   ![Überschrift H1 bis H3 in der Dropdown-Auswahl (klassische Benutzeroberfläche).](assets/screen_shot_2018-03-21at165719.png)

* **Hervorgehobener Text**:

   Verwenden Sie das - oder -Element, um eine Hervorhebung anzugeben. Verwenden Sie keine Überschriften zum Hervorheben von Text in Absätzen.

   * Markieren Sie den Text, den Sie hervorheben möchten.
   * Klicken Sie auf das Symbol **B** (für &lt;strong>) oder das Symbol **I** (für &lt;em>), die im Bedienfeld **Eigenschaften** angezeigt werden (vergewissern Sie sich, dass HTML ausgewählt ist).

   >[!NOTE]
   >
   >RTE ist in einer Standardinstallation von AEM wie folgt eingerichtet:
   >
   >* &lt;b> für &lt;strong>
   * &lt;i> für &lt;em>

   Sie sind im Grunde identisch, aber und sind vorzuziehen, da sie semantisch korrekt HTML sind. Ihr Entwicklungsteam kann den RTE für die Verwendung und (anstelle von und) bei der Entwicklung Ihrer Projektinstanz konfigurieren.

* **Listen verwenden**: Mit HTML können Sie drei verschiedene Arten von Listen angeben:

   * Das Element `<ul>` wird für *nicht geordnete* Listen (Aufzählungslisten) verwendet. Einzelne Listenelemente werden mit dem Element `<li>` gekennzeichnet.

      Verwenden Sie im RTE die **Aufzählungsliste** Symbol.

   * Das Element `<ol>` wird für *nummerierte Listen verwendet*. Einzelne Listenelemente werden mit dem Element `<li>` gekennzeichnet.

      Verwenden Sie in RTE das Symbol **Nummerierte Liste**.
   Wenn Sie vorhandenen Inhalt in einen bestimmten Listentyp ändern möchten, markieren Sie den entsprechenden Text und wählen Sie den entsprechenden Listentyp aus. Wie im vorherigen Beispiel, das zeigt, wie Absatztext eingegeben wird, werden die entsprechenden Listenelemente automatisch zu Ihrer HTML hinzugefügt.

   Im Vollbildmodus sind die einzelnen Symbole **Aufzählungsliste** und **Nummerierte Liste** sichtbar. Wenn Sie sich nicht im Vollbildmodus befinden, sind die beiden Optionen hinter dem einzelnen Symbol **Listen** verfügbar.

   ![](do-not-localize/screen_shot_2018-03-21at165756.png)

   >[!NOTE]
   `<dl>` wird vom RTE nicht unterstützt.

* **Tabellen verwenden**:

   Datentabellen müssen mithilfe von HTML-Tabellenelementen identifiziert werden:

   * Ein Element `<table>`
   * Ein Element `<tr>` für jede Tabellenzeile
   * Ein Element `<th>` für jede Zeilen- und Spaltenüberschrift
   * Ein Element `<td>` für jede Datenzelle

   >[!NOTE]
   In der klassischen Benutzeroberfläche sollten Tabellen mit dem **Verzeichnis** -Komponente.

   Außerdem nutzen barrierefrei zugängliche Tabellen die folgenden Elemente und Attribute:

   * Das Element `<caption>` wird verwendet, um für die Tabelle eine sichtbare Tabellenbeschriftung bereitzustellen. Beschriftungen werden standardmäßig zentriert über der Tabelle angezeigt, können jedoch mithilfe von CSS entsprechend positioniert werden. Die Beschriftung wird programmatisch mit der Tabelle verknüpft. Daher ist sie eine nützliche Methode, um eine Einführung in Inhalte bereitzustellen.
   * Das Element `<summary>` unterstützt blinde Benutzer dabei, die in einer Tabelle dargestellten Informationen zu verstehen, weil ihnen damit eine Inhaltsangabe dessen geboten wird, was sehende Benutzer sehen können. Dies ist besonders nützlich bei komplexen oder unkonventionellen Tabellen-Layouts (dieses Attribut wird nicht im Browser angezeigt, sondern nur für Hilfstechnologien ausgelesen).
   * Das Attribut `scope` des Elements `<th>` wird verwendet, um anzugeben, ob eine Zelle eine Überschrift für eine bestimmte Zeile oder eine bestimmte Spalte darstellt. Auf ähnliche Weise können die Überschrift und ID-Attribute in komplexen Tabellen verwendet werden, bei denen Datenzellen mit einer oder mehreren Überschriften verknüpft sein können.

   >[!NOTE]
   Diese Elemente und Attribute sind standardmäßig nicht direkt verfügbar, doch der Systemadministrator kann Support für diese Werte im Dialogfeld **Tabelleneigenschaften** hinzufügen (siehe [Hinzufügen von Support für zusätzliche HTML-Elemente und -Attribute](/help/sites-administering/rte-accessible-content.md#adding-support-for-additional-html-elements-and-attributes)).

   Beim Hinzufügen von **Verzeichnis** Sie können **Tabelleneigenschaften** über das Dialogfeld.

   * geeignete **Beschriftung**.
   * Im Idealfall entfernen Sie alle Standardwerte für **Breite**, **Höhe**, **Rand**, **Zellauffüllung**, **Zellabstand**, da diese Eigenschaften in einem globalen Stylesheet festgelegt werden können.

   ![Dialogfeld „Tabelleneigenschaften“](assets/chlimage_1-205.png)

   Anschließend können Sie die **Zellen-Eigenschaften** , um festzulegen, ob es sich bei der Zelle um eine Daten- oder Kopfzeilenzelle handelt, und, falls es sich um eine Kopfzeilenzelle handelt, ob sie sich auf eine Zeile, Spalte oder beides bezieht:

   ![Dialogfeld „Zelleneigenschaften“; Festlegen einer Zeile (normalerweise die erste Zeile) als Überschriftzeile.](assets/chlimage_1-206.png)

* **Komplexe Datentabellen:**

   In einigen Fällen, in denen komplexe Tabellen mit zwei oder mehr Überschriftenebenen vorhanden sind, reicht das normale Dialogfeld „Tabelleneigenschaften“ nicht aus, um alle benötigten Strukturinformationen anzugeben. Für diese Arten von komplexen Tabellen müssen direkte Beziehungen zwischen den Überschriften und deren dazugehörigen Zellen erstellt werden. Zu diesem Zweck werden die Attribute **Überschrift** und **ID** verwendet. Beispielsweise werden in der Tabelle unten Überschriften und IDs zugeordnet, um eine programmgesteuerte Verbindung für Benutzer von Hilfstechnologien herzustellen.

   >[!NOTE]
   Das id-Attribut ist in einer nativen Installation nicht verfügbar. Sie kann durch die Konfiguration von HTML-Regeln und des Serialisierungsprogramms im RTE aktiviert werden.

   >[!NOTE]
   In der klassischen Benutzeroberfläche sollten Tabellen mit dem **Verzeichnis** -Komponente.

   ```xml
   <table>
      <tr>
        <th rowspan="2" id="h">Homework</th>
        <th colspan="3" id="e">Exams</th>
        <th colspan="3" id="p">Projects</th>
      </tr>
      <tr>
        <th id="e1" headers="e">1</th>
        <th id="e2" headers="e">2</th>
        <th id="ef" headers="e">Final</th>
        <th id="p1" headers="p">1</th>
        <th id="p2" headers="p">2</th>
        <th id="pf" headers="p">Final</th>
      </tr>
      <tr>
       <td headers="h">15%</td>
       <td headers="e e1">15%</td>
       <td headers="e e2">15%</td>
       <td headers="e ef">20%</td>
       <td headers="p p1">10%</td>
       <td headers="p p2">10%</td>
       <td headers="p pf">15%</td>
      </tr>
   </table>
   ```

   Um dies in AEM zu erreichen, müssen Sie das Markup hinzufügen, indem Sie direkt den Modus zur Bearbeitung des Quell-Codes verwenden.

   >[!NOTE]
   Diese Funktion ist in einer Standardinstallation nicht sofort verfügbar. Dies erfordert die Konfiguration des RTE, der HTML-Regeln und des Serialisierungsprogramms.

#### Weitere Informationen: Informationen und Beziehungen (1.3.1) {#more-information-info-and-relationships}

* [Erfolgskriterien 1.3.1 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/content-structure-separation-programmatic.html)
* [Erfolgskriterien 1.3.1 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-content-structure-separation-programmatic)

### Sensorische Eigenschaften (1.3.3)          {#sensory-characteristics}

* Erfolgskriterium 1.3.3
* Level A
* Sensorische Eigenschaften: Anweisungen, die zum Verstehen und Bedienen von Inhalt verfügbar sind, beziehen sich nicht nur auf sensorische Eigenschaften der Komponenten wie Form, Größe, visuelle Position, Ausrichtung oder Klang.

#### Zweck: Sensorische Eigenschaften (1.3.3) {#purpose-sensory-characteristics}

Entwickler konzentrieren sich bei der Präsentation von Informationen oft auf visuelle Design-Funktionen wie Farbe, Form, Textstil oder die absolute oder relative Position eines Inhaltselements. Hierbei kann es sich um sehr leistungsstarke Design-Techniken zur Informationsübermittlung handeln, aber blinde oder sehbehinderte Menschen können möglicherweise nicht auf Informationen zugreifen, die eine visuelle Identifizierung von Attributen wie Position, Farbe oder Form erfordern.

Entsprechend sind Informationen, für die zwischen verschiedenen Klängen (z. B. Inhalten, die von einer Frau oder einem Mann gesprochen werden) unterschieden werden muss, für Menschen mit eingeschränktem Hörvermögen nicht verfügbar, wenn sie nicht in Textalternativen für den Audioinhalt umgesetzt wurden.

>[!NOTE]
Die Anforderungen, die sich auf die Alternativen für Farben beziehen, finden Sie unter [Verwendung von Farbe](#use-of-color).

#### Erfüllen: Sensorische Eigenschaften (1.3.3) {#how-to-meet-sensory-characteristics}

Stellen Sie sicher, dass alle Informationen, die sich auf visuelle Eigenschaften des Seiteninhalts stützen, auch in einem alternativen Format angezeigt werden.

* Verlassen Sie sich nicht auf die visuelle Position, um Informationen anzugeben. Wenn Sie beispielsweise Benutzer auf ein Menü rechts auf der Seite verweisen möchten, über das sie auf weitere Informationen zugreifen können, lesen Sie *das Menü rechts*; Benennen Sie stattdessen das Menü (z. B. über eine Überschrift) und verweisen Sie im Text auf diesen Namen.
* Verwenden Sie nicht die Textformatierung (z. B. fett oder kursiv gedruckten Text) als einzige Möglichkeit, Informationen zu vermitteln.

>[!NOTE]
Die Verwendung beschreibender Begriffe ist zulässig, wenn sie in einem nicht visuellen Kontext eine Bedeutung haben. Verwenden Sie beispielsweise *above* und *below* im Allgemeinen akzeptabel ist, da sie jeweils Inhalte vor und nach einem bestimmten Inhaltselement implizieren; Dies wäre immer noch sinnvoll, wenn der Inhalt laut gesprochen wird.

#### Weitere Informationen – Sensorische Eigenschaften (1.3.3) {#more-information-sensory-characteristics}

* [Erfolgskriterien 1.3.3 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/content-structure-separation-understanding.html)
* [Erfolgskriterien 1.3.3 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-content-structure-separation-understanding)

### Unterscheidbar (1.4) {#distinguishable}

[Richtlinie 1.4 Unterscheidbar: Erleichtern Sie den Benutzern das Sehen und Hören von Inhalt einschließlich der Unterscheidung von Vorder- und Hintergrund.](https://www.w3.org/TR/WCAG20/#visual-audio-contrast)

### Verwendung von Farbe (1.4.1)  {#use-of-color}

* Erfolgskriterium 1.4.1
* Level A
* Verwendung von Farbe: Farbe wird nicht als einziges visuelles Mittel zur Informationsübermittlung, zur Angabe einer Aktion, zur Aufforderung einer Antwort oder zur Unterscheidung eines visuellen Elements verwendet.

>[!NOTE]
Dieses Erfolgskriterium bezieht sich speziell auf die Farbwahrnehmung. Andere Wahrnehmungsformen werden unter [Anpassbar (1.3)](#adaptable); einschließlich programmatischer Zugriff auf Farbe und andere visuelle Darstellungskodierungen.

#### Zweck - Verwendung von Farbe (1.4.1) {#purpose-use-of-color}

Farbe bietet sichtbar eine effektive Möglichkeit, die Ästhetik von Web-Seiten zu verbessern, und kann auch die Vermittlung von Informationen unterstützen. Es gibt jedoch eine Reihe visueller Beeinträchtigungen, von Blindheit bis zu Sehschwäche, was bedeutet, dass einige Menschen nicht in der Lage sind, zwischen bestimmten Farben zu unterscheiden. Dies macht die Farbcodierung zu einer unzuverlässigen Methode zur Bereitstellung von Informationen.

So kann z. B. jemand mit einem rot-grünen Sehmangel nicht zwischen Grün- und Rottönen unterscheiden. Sie können beide Farben als dritte Farbe sehen (z. B. braun), in diesem Fall können sie nicht zwischen rot, grün und braun unterscheiden.

Darüber hinaus kann die Farbe nicht von Personen wahrgenommen werden, die reinen Text-Browsern, monochromen Anzeigegeräten oder einem Schwarzweiß-Ausdruck auf der Seite verwenden.

#### Erfüllen - Verwendung von Farbe (1.4.1)       {#how-to-meet-use-of-color}

Immer wenn Farbe verwendet wird, um Informationen zu vermitteln, müssen Sie sicherstellen, dass die verfügbaren Informationen auch verfügbar sind, wenn die Farbe nicht sichtbar ist.

Stellen Sie z. B. sicher, dass die durch die Farbe vermittelte Information auch explizit im Text enthalten ist. Die folgende Abbildung zeigt, wie Farbe und Text sowohl die Sitzverfügbarkeit für eine Leistung anzeigen:

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Leistung</strong></p> </td> 
   <td><p><strong>Verfügbarkeit</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Dienstag, 16. März<sup>th</sup></p> </td> 
   <td><p>VERFÜGBARE SITZE</p> </td> 
  </tr> 
  <tr> 
   <td><p>Mittwoch, 17. März</p> </td> 
   <td><p>VERFÜGBARE SITZE</p> </td> 
  </tr> 
  <tr> 
   <td><p>Donnerstag 18. März<sup>th</sup></p> </td> 
   <td><p>VERKAUFT</p> </td> 
  </tr> 
 </tbody> 
</table>

Wenn Farbe als Hinweis für Informationen verwendet wird, sollten Sie für einen zusätzlichen visuellen Hinweis sorgen, z. B. durch Ändern des Stils (z. B. fett, kursiv) oder der Schriftart. So können auch Personen mit Seh- oder Farbschwäche die Informationen erkennen. Sie dürfen sich jedoch nicht vollständig auf diese Maßnahmen verlassen, da sie für Menschen, die die Seite überhaupt nicht sehen können, keine Hilfe bieten.

#### Weitere Informationen – Verwendung von Farbe (1.4.1) {#more-information-use-of-color}

* [Erfolgskriterien 1.4.1 verstehen](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/working-examples/G183/link-contrast.html)
* [Erfolgskriterien 1.4.1 erfüllen](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/working-examples/G183/link-contrast.html)
* [Anleitung für das Erzielen eines Kontrastverhältnisses von 3:1 mit einer Liste Web-sicherer Farben](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/working-examples/G183/link-contrast.html)

### Kontrast (Minimum) (1.4.3) {#contrast-minimum}

* Erfolgskriterium 1.4.3
* Level AA
* Kontrast (Minimum): Die visuelle Darstellung von Text und Bildern von Text hat ein Kontrastverhältnis von mindestens 4,5:1, mit Ausnahme der folgenden:

   * Großer Text: Großformatigen Text und Bilder von großformatigem Text weisen ein Kontrastverhältnis von mindestens 3:1 auf.
   * Beiläufig: Für Text oder Textbilder, die Teil einer inaktiven Komponente der Benutzeroberfläche sind, die reine Dekoration darstellen, die für niemanden sichtbar sind oder die Teil eines Bildes sind, das signifikanten anderen visuellen Inhalt enthält, ist kein Kontrast erforderlich.
   * Firmenschriftzüge: Für Text, der Teil eines Logos oder eines Markennamens ist, gibt es keine Kontrastanforderungen.

#### Zweck - Kontrast (Minimum) (1.4.3)       {#purpose-contrast-minimum}

Personen mit bestimmten Sehbehinderungen können möglicherweise nicht zwischen bestimmten Farbpaaren mit geringem Kontrast unterscheiden. Für diese Personen können Probleme mit der Barrierefreiheit auftreten, wenn

* Wenn zwischen dem Text und der Hintergrundfarbe nur wenig Kontrast besteht.
* Die Farbkodierung von Text (z. B. Linktext und Nicht-Link-Text) ist für die Unterscheidung von Informationen wichtig.

>[!NOTE]
Text, der ausschließlich für Dekorationszwecke verwendet wird, ist von diesem Erfolgskriterium ausgeschlossen.

#### Erfüllen - Kontrast (Minimum) (1.4.3) {#how-to-meet-contrast-minimum}

Stellen Sie sicher, dass der Text ausreichend mit dem Hintergrund kontrastiert. Die Kontrastverhältnisse hängen von der Größe und dem Stil des betreffenden Textes ab:

* Für Text mit einer Größe von weniger als 18 Punkt (oder 14 Punkt bei Fettschrift) sollte das Kontrastverhältnis zwischen Text/Bildern mit Text und dem Hintergrund mindestens 4,5:1 betragen.
* Für Text mit einer Größe von mindestens 18 Punkt (oder 14 Punkt fett) sollte das Kontrastverhältnis mindestens 3:1 betragen.
* Wenn ein Hintergrund gemustert ist, sollte der Hintergrund um einen beliebigen Text schattiert werden, sodass das Verhältnis 4,5:1 oder 3:1 beibehalten wird.

Verwenden Sie ein Farbkontrast-Tool, um das Kontrastverhältnis zu prüfen, z. B. den [Color Contrast Analyser von Paciello Group](https://www.paciellogroup.com/resources/contrast-analyser.html) oder den [Color Contrast Checker von WebAIM](https://www.webaim.org/resources/contrastchecker/). Mit diesen Tools können Sie Farbpaare überprüfen und über Kontrastprobleme berichten.

Wenn Sie sich weniger Gedanken darüber machen, das Erscheinungsbild Ihrer Seite festzulegen, können Sie auch festlegen, dass keine Farben für Hintergrund- und Vordergrundtext festgelegt werden. Es ist keine Kontrastprüfung erforderlich, da der Browser des Benutzers die Farben des Texts und des Hintergrunds bestimmt.

Wenn es nicht möglich ist, die empfohlenen Kontraststufen zu erreichen, müssen Sie einen Link zu einer alternativen, äquivalenten Version der Seite bereitstellen (die keine Farbkontrastprobleme aufweist) oder dem Benutzer die Möglichkeit geben, den Kontrast des Seitenfarbschemas an seine eigenen Anforderungen anzupassen.

#### Weitere Informationen - Kontrast (Minimum) (1.4.3) {#more-information-contrast-minimum}

* [Erfolgskriterien 1.4.3 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-contrast.html)
* [Erfolgskriterien 1.4.3 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-visual-audio-contrast-contrast)

### Bilder von Text (1.4.5)     {#images-of-text}

* Erfolgskriterium 1.4.5
* Level AA
* Bilder von Text: Falls die verwendeten Technologien die visuelle Präsentation realisieren können, wird für die Vermittlung von Informationen Text verwendet – keine Bilder von Text. Dabei gelten folgende Ausnahmen:

   * Anpassbar: Das Textbild kann visuell an die Anforderungen des Benutzers angepasst werden.
   * Wesentlich: Eine besondere Textdarstellung ist für die vermittelte Information von wesentlicher Bedeutung.

>[!NOTE]
Logotypen (Text, der Teil eines Logos oder Markennamen ist) werden als wesentlich betrachtet.

#### Zweck - Bilder von Text (1.4.5) {#purpose-images-of-text}

Bilder von Text werden häufig verwendet, wenn ein bestimmter Textstil bevorzugt wird. z. B. ein Logtyp oder wenn Text aus einer anderen Quelle generiert wurde (z. B. eine Prüfung eines Papierdokuments). Im Vergleich zu Text, der im HTML vorgestellt und mit CSS formatiert wird, haben Textbilder jedoch nicht die Flexibilität, die Größe oder das Erscheinungsbild zu ändern, die für Personen mit Sehbehinderungen oder Leseschwächen erforderlich sein könnten.

#### Erfüllen - Bilder von Text (1.4.5) {#how-to-meet-images-of-text}

Wenn Textbilder verwendet werden müssen, verwenden Sie CSS, um die Textbilder durch entsprechenden Text im HTML zu ersetzen, damit der Text auf anpassbare Weise verfügbar ist. Ein Beispiel hierfür finden Sie unter [C30: Verwenden von CSS, um Text durch Bilder von Text zu ersetzen und ein Steuerelement zum Umschalten auf der Benutzeroberfläche bereitzustellen](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/C30).

#### Weitere Informationen - Bilder von Text (1.4.5) {#more-information-images-of-text}

* [Erfolgskriterien 1.4.5 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-text-presentation.html)
* [Erfolgskriterien 1.4.5 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-visual-audio-contrast-text-presentation)

## Grundsatz 2: Bedienbar {#principle-operable}

[Grundsatz 2: Bedienbar – Komponenten der Benutzerschnittstelle und der Navigation müssen bedienbar sein.](https://www.w3.org/TR/WCAG20/#operable)

### Pausieren, Beenden, Ausblenden (2.2.2)          {#pause-stop-hide}

* Erfolgskriterium 2.2.2
* Level A
* Pausieren, Beenden, Ausblenden: Für sich bewegende, blinkende, scrollende oder sich automatisch aktualisierende Informationen gelten folgenden Regeln:

   * Verschieben, blinken, scrollen: Für bewegte, blinkende oder scrollende Informationen, die (a) automatisch gestartet werden, (b) länger als fünf Sekunden dauern und (c) parallel zu anderen Inhalten präsentiert werden, gibt es einen Mechanismus, mit dem der Benutzer sie anhalten, stoppen oder verbergen kann, es sei denn, die Bewegung, das Blinken oder Scrollen ist Teil einer Aktivität, in der sie wichtig ist.
   * Automatische Aktualisierung: Für alle automatisch aktualisierten Informationen, die (a) automatisch gestartet und (b) parallel zu anderen Inhalten angezeigt werden, gibt es einen Mechanismus, mit dem der Benutzer sie anhalten, stoppen oder ausblenden oder die Häufigkeit der Aktualisierung steuern kann, es sei denn, die automatische Aktualisierung ist Teil einer Aktivität, in der sie wichtig ist.

Beachten Sie Folgendes:

1. Die Anforderungen für flackernden oder blinkenden Inhalt finden Sie unter [Gestalten Sie Inhalte nicht auf Arten, von denen bekannt ist, dass sie zu Anfällen führen (2.3)](#seizures).
1. Jeglicher Inhalt, der dieses Erfolgskriterium nicht erfüllt, kann die Möglichkeit eines Benutzers beeinträchtigen, die gesamte Seite zu nutzen. Daher muss jeglicher Inhalt auf einer Web-Seite (egal ob er dazu dient, andere Erfolgskriterien zu erfüllen oder nicht) dieses Erfolgskriterium erfüllen. Siehe [Konformitätsanforderung 5: Nichtinterferenz](https://www.w3.org/TR/WCAG20/#cc5).
1. Inhalte, die regelmäßig durch Software aktualisiert werden oder an den Benutzeragenten gestreamt werden, müssen Informationen, die zwischen der Initiierung der Pause und der Wiederaufnahme der Präsentation generiert oder empfangen wurden, nicht beibehalten oder präsentieren, da dies technisch möglicherweise nicht möglich ist und in vielen Situationen irreführend sein könnte.
1. Eine Animation, die im Rahmen einer Vorausladephase oder einer ähnlichen Situation auftritt, kann als wesentlich angesehen werden, wenn während dieser Phase keine Interaktion für alle Benutzer stattfinden kann und wenn kein Hinweis auf Fortschritt angezeigt wird, Benutzer verwirren könnte oder sie glauben lässt, dass der Inhalt eingefroren oder beschädigt wurde.

#### Zweck - Pausieren, Beenden, Ausblenden (2.2.2) {#purpose-pause-stop-hide}

Manche Benutzer können Inhalte, die sich bewegen, ablenkend finden und es schwierig machen, sich auf andere Teile der Seite zu konzentrieren. Darüber hinaus sind solche Inhalte für Menschen schwierig, die beim Lesen Probleme haben, bewegtem Text zu folgen.

#### Erfüllen - Pausieren, Beenden, Ausblenden (2.2.2) {#how-to-meet-pause-stop-hide}

Abhängig von der Art des Inhalts können Sie beim Erstellen von Web-Seiten mit sich bewegendem, blitzendem oder blinkendem Inhalt die folgenden Empfehlungen beachten:

* Bieten Sie die Möglichkeit, das Scrollen des Inhalts anzuhalten, um Benutzern Zeit zum Lesen zu geben; z. B. Nachrichten-Ticker oder automatisch aktualisierten Text.
* Stellen Sie sicher, dass blinkende Inhalte maximal fünf Sekunden lang blinken.
* Nutzen Sie Technologien, mit denen die Anzeige von blinkenden Inhalten im Browser deaktiviert werden kann, z. B. Dateien im GIF- (Graphics Interchange Format) oder APNG-Format (Animated Portable Network Graphics).
* Stellen Sie ein Formularsteuerelement auf der Web-Seite bereit, damit der Benutzer alle blinkenden Inhalte auf der Seite deaktivieren kann.
* Wenn einer der oben genannten Punkte nicht möglich ist, stellen Sie einen Link zu einer Seite bereit, die den gesamten Inhalt enthält, jedoch ohne Blinken.

#### Weitere Informationen - Pausieren, Beenden, Ausblenden (2.2.2)       {#more-information-pause-stop-hide}

* [Erfolgskriterium 2.2.2 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-pause.html)
* [Erfolgskriterium 2.2.2 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-time-limits-pause)

### Anfälle (2.3)     {#seizures}

[Richtlinie 2.3 Anfälle: Gestalten Sie Inhalt nicht auf Arten, von denen bekannt ist, dass sie zu Anfällen führen.](https://www.w3.org/TR/WCAG20/#seizure)

### Grenzwert von maximal dreimaligem Blitzen (2.3.1)     {#three-flashes-or-below-threshold}

* Erfolgskriterium 2.3.1
* Level A
* Grenzwert von maximal dreimaligem Blitzen: Web-Seiten dürfen nichts enthalten, das in einem Zeitraum von einer Sekunde öfter als dreimal blitzt oder dessen Blitz unterhalb der allgemeinen Grenzwerte für Blitze und rote Blitze liegt.

>[!NOTE]
Jeglicher Inhalt, der dieses Erfolgskriterium nicht erfüllt, kann die Möglichkeit eines Benutzers beeinträchtigen, die gesamte Seite zu nutzen. Daher muss jeglicher Inhalt auf einer Web-Seite (egal ob er dazu dient, andere Erfolgskriterien zu erfüllen oder nicht) dieses Erfolgskriterium erfüllen. Siehe [Konformitätsanforderung 5: Nichtinterferenz](https://www.w3.org/TR/WCAG20/#cc5).

#### Zweck – Grenzwert von maximal dreimaligem Blitzen (2.3.1) {#purpose-three-flashes-or-below-threshold}

In bestimmten Fällen kann ein blitzender Inhalt zu photosensiblen Anfällen führen. Mit diesem Erfolgskriterium können diese Benutzer auf alle Inhalte zugreifen und diese erleben, ohne sich Gedanken über blitzende Inhalte machen zu müssen.

#### Erfüllen - Grenzwert von maximal dreimaligem Blitzen (2.3.1) {#how-to-meet-three-flashes-or-below-threshold}

Sie sollten Maßnahmen ergreifen, um sicherzustellen, dass die folgenden Techniken angewendet werden:

* Stellen Sie sicher, dass die Komponenten während eines Zeitraums von einer Sekunde maximal dreimal blitzen;
* Falls die obige Bedingung nicht erfüllt werden kann, platzieren Sie den blitzenden Inhalt in einem *kleinen sicheren Bereich* in Pixel auf dem Bildschirm. Dieser Bereich wird anhand einer komplexen Formel berechnet, die unter [G176: Blitzende Bereiche ausreichend klein halten](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/G176) behandelt wird. Diese Technik sollte ausschließlich dann angewendet werden, wenn ein blitzender Inhalt *unbedingt* erforderlich ist.

#### Weitere Informationen – Grenzwert von maximal dreimaligem Blitzen (2.3.1) {#more-information-three-flashes-or-below-threshold}

* [Erfolgskriterium 2.3.1 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/seizure-does-not-violate.html)
* [Erfolgskriterium 2.3.1 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#seizure)

### Seite mit Titel versehen (2.4.2)          {#page-titled}

* Erfolgskriterium 2.4.2
* Level A
* Seite mit Titel versehen: Web-Seiten haben einen Titel, der das Thema oder den Zweck beschreibt

#### Zweck - Seite mit Titel versehen (2.4.2) {#purpose-page-titled}

Dieses Erfolgskriterium ist für alle Benutzer hilfreich - unabhängig von etwaigen Beeinträchtigungen - um schnell den Inhalt einer Web-Seite zu ermitteln, ohne die Seite vollständig zu lesen. Dies ist insbesondere dann nützlich, wenn mehrere Web-Seiten in Browsertabs geöffnet sind, da der Seitentitel auf den Tabs angezeigt wird, was die Seiten schnell auffindbar macht.

#### Erfüllen - Seite mit Titel versehen (2.4.2) {#how-to-meet-page-titled}

Wenn Sie in AEM eine neue HTML-Seite erstellen, können Sie den Seitentitel angeben. Stellen Sie sicher, dass der Titel den Inhalt der Seite angemessen beschreibt, damit Besucher schnell erkennen können, ob der Inhalt tatsächlich für ihre Anforderungen relevant ist.

Sie können während der Bearbeitung einer Seite auch den Seitentitel ändern. Öffnen Sie dazu **Seiteninformationen** > **Eigenschaften**.

#### Weitere Informationen – Seite mit Titel versehen (2.4.2) {#more-information-page-titled}

* [Erfolgskriterium 2.4.2 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-title.html)
* [Erfolgskriterium 2.4.2 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-navigation-mechanisms-title)

### Link-Zweck (im Kontext) (2.4.4)          {#link-purpose-in-context}

* Erfolgskriterium 2.4.4
* Level A
* Link-Zweck (im Kontext): Der Zweck jedes Links kann allein durch den Link-Text oder durch den Link-Text zusammen mit dem programmatisch festgelegten Link-Kontext bestimmt werden. Ausgenommen sind Fälle, in denen der Zweck des Links für Benutzer generell mehrdeutig ist.

#### Zweck - Link-Zweck (im Kontext) (2.4.4) {#purpose-link-purpose-in-context}

Unabhängig von etwaigen Beeinträchtigungen ist es für alle Benutzer von entscheidender Bedeutung, dass durch einen passenden Link-Text klar erkenntlich ist wohin ein Link führt. So können Benutzer entscheiden, ob sie einem Link folgen möchten oder nicht. Für sehende Benutzer ist ein aussagekräftiger Link-Text ausgesprochen nützlich, wenn sich auf einer Seite mehrere Links befinden (vor allem, wenn eine Seite sehr viel Text enthält), da ein aussagekräftiger Link-Text einen deutlicheren Hinweis auf die Funktion der Zielseite liefert. Benutzer von Hilfstechnologien, die eine Liste aller Links auf einer Seite generieren können, können den Link-Text zwar außerhalb des Kontexts leichter verstehen.

#### Erfüllen - Link-Zweck (im Kontext) (2.4.4)       {#how-to-meet-link-purpose-in-context}

Stellen Sie vor allem sicher, dass der Link-Text den Zweck eines Links eindeutig beschreibt.

* Schlechtes Beispiel:

   * Text: Für Details zu unseren Abendkursen im Herbst 2010 klicken Sie auf <u>here</u>.
   * Grund: Es geht nicht deutlich und unmissverständlich hervor wohin der Link führt.

* Gutes Beispiel:

   * Text: <u>Abendkurse im Herbst 2010</u> - Einzelheiten.
   * Grund: Durch eine kleine Anpassung des Textes und der Position des Linkelements lässt sich der Link-Text verbessern:

Links sollten auf den Seiten eine konsistente Bezeichnung erhalten. Dies gilt insbesondere für Navigationsleisten. Wenn ein Link zu einer bestimmten Seite z. B. auf einer Seite **Publikationen** heißt, dann sollte er auch auf allen anderen Seiten denselben Namen erhalten.

Zum Zeitpunkt des Schreibens gibt es jedoch einige Probleme im Zusammenhang mit der Verwendung von Titeln:

* Im Titelattribut enthaltener Text steht im Allgemeinen nur Mausbenutzern als QuickInfo-Popup zur Verfügung und kann nicht über die Tastatur aufgerufen werden.
* Bildschirmlesehilfen können Titelattribute auslesen, diese Funktion ist jedoch möglicherweise nicht standardmäßig aktiviert. sodass Benutzer möglicherweise nicht wissen, dass ein Titelattribut vorhanden ist.
* Es ist schwierig, das Erscheinungsbild des Titeltextes zu ändern, was bedeutet, dass es für einige Personen schwierig oder unmöglich sein könnte, ihn zu lesen.

Das Title-Attribut kann also genutzt werden, um zusätzlichen Kontext zu einem Link bereitzustellen, Sie sollten aber diese Einschränkungen bedenken und es daher nicht als Alternative für einen geeigneten Link-Text nutzen.

Wenn ein Link aus einem Bild besteht, müssen Sie sicherstellen, dass der alternative Text für das Bild das Ziel des Links beschreibt. Wenn z. B. ein Bild eines Bücherregals als Link zu den Publikationen einer Person festgelegt wird, sollte der alternative Text **Publikationen von John Smith** lauten und nicht **Bücherregal**.

Wenn der Link-Anker alternativ Text enthält, der den Zweck des Links zusätzlich zum Bildelement beschreibt (und der Text daher neben dem Bild angezeigt wird), verwenden Sie ein leeres ALT-Attribut für das Bild:

```xml
<a href="publications.html">
<img src = "bookshelf.jpg" alt = "" />
John Smith’s publications
</a>
```

>[!NOTE]
Das obige Snippet ist eine Illustration. Es wird empfohlen, die **Bild** -Komponente.

Auch wenn es angeraten ist, einen Link-Text bereitzustellen, der den Zweck des Links verdeutlicht, ohne zusätzlichen Kontext zu benötigen, gibt es Fälle, in denen dies nicht möglich ist. Links ohne Kontext können in den folgenden Fällen verwendet werden. HTML-Beispiele hierzu finden Sie unter [Erfolgskriterium 2.4.4 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-navigation-mechanisms-refs).

* Wenn der Link-Text zu einer Liste eng zusammenhängender Links gehört und das den Link umgebende Listenelement ausreichend Kontext liefert.
* Wenn der Zweck eines Links aus dem *vorangehenden* (nicht dem nachfolgenden) Text des Absatzes klar hervorgeht.
* Wenn die Relation in einer Datentabelle enthalten ist und der Zweck daher aus den zugehörigen Überschriften eindeutig identifiziert werden kann.
* Wenn eine Liste von Links in einem Satz von Überschriften enthalten ist und die Überschrift selbst einen geeigneten Kontext bietet.
* Wenn eine Liste von Links in einem verschachtelten Link enthalten ist und das übergeordnete Listenelement über dem verschachtelten Link einen geeigneten Kontext bietet.

In einigen Fällen, in denen sich mehrere Links auf einer Seite befinden (von denen jeder das Ziel des Links durch komplexe, aber erforderliche Details angibt), kann es sinnvoll sein, eine alternative Version der Web-Seite anzubieten, die denselben Inhalt anzeigt, auf der der Link-Text jedoch weniger ausführlich ist.

Alternativ können Skripts verwendet werden. Dabei wird im Link selbst ein minimaler Text bereitgestellt. Bei der Aktivierung des entsprechenden Steuerelements im oberen Bereich der Seite wird der Link-Text jedoch *erweitert* und es werden mehr Details angezeigt. Einen ähnlichen Ansatz bietet die Verwendung von CSS, um den vollständigen Link für sehende Benutzer *auszublenden*, ihn für Benutzer der Sprachausgabe jedoch auszugeben. Dies überschreitet jedoch den Rahmen dieses Dokuments; weitere Informationen hierzu finden Sie jedoch unter [Weitere Informationen – Link-Zweck (im Kontext) (2.4.4)](#more-information-link-purpose-in-context).

#### Weitere Informationen – Link-Zweck (im Kontext) (2.4.4) {#more-information-link-purpose-in-context}

* [Erfolgskriterium 2.4.4 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-refs.html)
* [Erfolgskriterium 2.4.4 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-navigation-mechanisms-refs)
* [C7: Verwendung von CSS, um einen Teil des Link-Textes auszublenden](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/C7)

## Grundsatz 3: Verständlich     {#principle-understandable}

[Grundsatz 3: Verständlich – Informationen und die Bedienung der Benutzerschnittstelle müssen verständlich sein.](https://www.w3.org/TR/WCAG20/#understandable)

### Machen Sie Inhalt lesbar und verständlich (3.1) {#make-text-content-readable-and-understandable}

[Richtlinie 3.1 Lesbar: Machen Sie Inhalt lesbar und verständlich.](https://www.w3.org/TR/WCAG20/#meaning)

### Sprache der Seite (3.1.1) {#language-of-page}

* Erfolgskriterium 3.1.1
* Level A
* Sprache der Seite: Die voreingestellte menschliche Sprache einer Web-Seite kann programmatisch bestimmt werden.

#### Zweck - Sprache der Seite (3.1.1) {#purpose-language-of-page}

Mit diesem Erfolgskriterium soll sichergestellt werden, dass Text und andere sprachliche Inhalte korrekt wiedergegeben werden. Für Benutzer von Bildschirmlesehilfen wird dadurch sichergestellt, dass der Inhalt korrekt ausgesprochen wird, während bei visuellen Browsern die Wahrscheinlichkeit höher ist, dass bestimmte Zeichensätze korrekt angezeigt werden.

#### Erfüllen - Sprache der Seite (3.1.1) {#how-to-meet-language-of-page}

Um dieses Erfolgskriterium zu erfüllen, kann die Standardsprache einer Web-Seite über das Attribut `lang` innerhalb des Elements `<html>` am Anfang der Seite festgelegt werden. Beispiel:

* Wenn eine Seite z. B. in britischem Englisch verfasst ist, sollte das Element `<html>` wie folgt angegeben werden: `<html lang = “en-gb”>`

* Wenn eine Seite hingegen als Seite in US-Englisch gerendert werden soll, ist folgende Angabe erforderlich: `<html lang = “en-us”>`

In AEM wird die Standardsprache einer Seite bei ihrer Erstellung festgelegt, kann aber auch bei ihrer Bearbeitung geändert werden. Öffnen Sie dazu den **Sidekick** > Registerkarte **Seite** > **Seiteneigenschaften…** > Registerkarte **Erweitert**.

#### Weitere Informationen – Sprache der Seite (3.1.1) {#more-information-language-of-page}

* [Erfolgskriterium 3.1.1 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-doc-lang-id.html)
* [Erfolgskriterium 3.1.1 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-meaning-doc-lang-id)
* Die Codes basieren auf ISO 639-1. Eine ausführlichere Liste der Codes für jede Sprache finden Sie im [Website der W3-Schulen](https://www.w3schools.com/tags/ref_language_codes.asp).

### Sprache von Teilen (3.1.2)  {#language-of-parts}

* Erfolgskriterium 3.1.2
* Level AA
* Sprache von Teilen: Die menschliche Sprache eines jeden Passes oder Satzes im Inhalt kann programmatisch bestimmt werden, mit Ausnahme von Eigennamen, technischen Begriffen, Wörtern unbestimmter Sprache und Wörtern oder Redewendungen, die Teil des Wörterbuchs des unmittelbar umgebenden Textes geworden sind.

#### Zweck - Sprache von Teilen (3.1.2) {#purpose-language-of-parts}

Der Zweck dieses Erfolgskriteriums ähnelt dem Zweck des Erfolgskriteriums [Sprache der Seite](#language-of-page). Es gilt jedoch für Web-Seiten, die auf einer Seite Inhalte im mehreren Sprachen enthalten (z. B. in Form von Zitaten oder wenig geläufigen Lehnwörtern).

Seiten, die dieses Erfolgskriterium anwenden, ermöglichen Folgendes:

* Braille-Transition-Software zum Einfügen von Akzentzeichen.
* Bildschirmlesehilfen können Wörter, die nicht in der Standardsprache enthalten sind, korrekt aussprechen.
* Übersetzungs-Tools wie der Google Übersetzer können Inhalt korrekt von einer Sprache in eine andere übersetzen.

#### Erfüllen - Sprache von Teilen (3.1.2) {#how-to-meet-language-of-parts}

Mit dem Attribut `lang` können Änderungen in Bezug auf die Sprache des Inhalts ermittelt werden. Ein deutschsprachiges Zitat (ISO 639-1-Code „de“) kann z. B. wie folgt angezeigt werden:

```xml
<blockquote cite = "John F. Kennedy" lang = "de"> 
     <p>Ich bin ein Berliner</p>
 </blockquote>
```

>[!NOTE]
Blockzitate werden in einer nativen Instanz nicht unterstützt. Eine benutzerdefinierte Komponente kann entwickelt werden, um die Funktion zu unterstützen.

Auf ähnliche Weise kann der Browser ein wenig geläufiges Lehnwort oder eine Redewendung korrekt rendern, wenn das Element `span` wie folgt verwendet wird:

```xml
<p>The only French phrase I know is <span lang = “fr”>je ne sais quoi</span>.</p>
```

>[!NOTE]
Dieses Erfolgskriterium muss nicht beachtet werden, wenn Namen oder Städte in verschiedenen Sprachen vorkommen oder wenn Sie Lehnwörter oder Redewendungen nutzen, die in der Standardsprache gängig geworden sind (wie *Schadenfreude* im Englischen).

Um ein span-Element mit der entsprechenden Sprache hinzuzufügen, können Sie Ihren HTML-Code im Bearbeitungsmodus für den Quelltext im RTE manuell bearbeiten, damit er wie oben aussieht. Alternativ kann ein Systemadministrator das `lang`-Attribut im RTE einfügen (siehe [Unterstützung für zusätzliche HTML-Elemente und -Attribute hinzufügen](/help/sites-administering/rte-accessible-content.md#adding-support-for-additional-html-elements-and-attributes)).

#### Weitere Informationen – Sprache von Teilen (3.1.2) {#more-information-language-of-parts}

* [Erfolgskriterium 3.1.2 verstehen](https://www.w3.org/TR/2016/NOTE-UNDERSTANDING-WCAG20-20161007/meaning-other-lang-id.html)
* [Erfolgskriterium 3.1.2 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-meaning-other-lang-id)

### Helfen Sie Benutzern, Fehler zu vermeiden und zu korrigieren (3.3)     {#help-users-avoid-and-correct-mistakes}

[Richtlinie 3.3 Hilfestellung bei der Eingabe: Helfen Sie Benutzern, Fehler zu vermeiden und zu korrigieren.](https://www.w3.org/TR/WCAG20/#minimize-error)

### Beschriftungen oder Anweisungen (3.3.2)     {#labels-or-instructions}

* Erfolgskriterium 3.3.2
* Level A
* Beschriftungen oder Anweisungen: Beschriftungen oder Anweisungen werden bereitgestellt, wenn Inhalte Benutzereingaben erfordern.

#### Zweck - Beschriftungen oder Anweisungen (3.3.2) {#purpose-labels-or-instructions}

Die Bereitstellung von Anweisungen, die den Personen beim Ausfüllen von Formularen helfen, ist ein grundlegender Bestandteil der bewährten Verfahren für die Benutzerfreundlichkeit der Benutzeroberfläche. Dies ist besonders für Menschen mit visuellen oder kognitiven Beeinträchtigungen hilfreich, die andernfalls Schwierigkeiten haben, das Layout eines Formulars und die Art der Daten zu verstehen, die in einem bestimmten Formularfeld bereitgestellt werden sollen.

AEM wird beim Hinzufügen einer Formularkomponente eine Standardbeschriftung hinzugefügt, z. B. **Textfeld**, um zur Seite zu gelangen. Dieser Standardtitel hängt vom Komponententyp ab. Sie können Ihren eigenen Titel in der **Titel und Text** Registerkarte des Bearbeitungsdialogfelds für dieses Feld. Es ist wichtig sicherzustellen, dass Benutzer anhand von Bezeichnungen die mit den einzelnen Formularkomponenten verknüpften Daten besser verstehen können.

![Registerkarte „Titel und Text“ (Dialogfeld „Bearbeiten“). Der Titel „Description“ wurde hinzugefügt.](assets/chlimage_1-207.png)

Diese **Titel** -Feld muss für Feldelemente verwendet werden, da es eine Beschriftung bereitstellt, die für Hilfstechnologien verfügbar ist. Das einfache Schreiben einer Beschriftung in Text neben dem Feld reicht nicht aus.

Für einige Komponenten können Beschriftungen auch über das Kontrollkästchen **Titel ausblenden** ausgeblendet werden. Auf diesem Weg ausgeblendete Beschriftungen sind für Sprachausgabetechnologien weiterhin verfügbar, werden auf dem Bildschirm jedoch nicht angezeigt. Auch wenn dies in einigen Situationen einen guten Ansatz bilden kann, ist es in der Regel besser, möglichst immer eine sichtbare Beschriftung hinzuzufügen, da manche Benutzer nur einen sehr kleinen Ausschnitt des Bildschirms sehen (jeweils ein Feld) und die Felder nur anhand der Beschriftung richtig zuordnen können.

#### Bild-Schaltflächen {#image-buttons}

Wenn Bild-Schaltflächen verwendet werden (z. B. die Komponente **Bild-Schaltfläche**) liefert das Feld **Titel** auf der Registerkarte **Titel und Text** des Bearbeitungsdialogfelds den Alt-Text für das Bild und nicht die Beschriftung. Im folgenden Beispiel wurde daher für das Bild mit dem Text `Submit` im Bearbeitungsdialogfeld der Alt-Text `Submit` über das Feld **Titel** hinzugefügt.

![Schaltfläche „Bild“ mit im Feld „Titel“ festgelegtem Alt-Text (Dialogfeld „Bearbeiten“).](assets/chlimage_1-208.png)

#### Gruppen von Formularfeldern {#groups-of-form-fields}

Bei einer Gruppe miteinander verbundener Steuerelemente, z. B. **Optionsfeldgruppe**, kann ein Titel für die Gruppe sowie einzelne Steuerelemente erforderlich sein. Wenn Sie einen Satz Optionsfelder in AEM hinzufügen, gibt das Feld **Titel** diesen Gruppentitel an, während die einzelnen Titel beim Erstellen der Optionsfelder (**Elemente**) angegeben werden.

![Hinzufügen von Elementen zur Optionsfeldgruppe. Der Gruppentitel lautet „Contact me by“ - im Titel-Feld definiert.](assets/chlimage_1-209.png)

Es gibt jedoch keine programmatische Zuordnung zwischen dem Gruppentitel und den Optionsschaltflächen. Der Titel muss beim Bearbeiten der Vorlage in die erforderlichen Tags `fieldset` und `legend` gesetzt werden, um diese Zuordnung herzustellen. Dies kann ausschließlich über die Bearbeitung des Seitenquell-Codes erfolgen. Alternativ kann ein Systemadministrator die Unterstützung für diese Elemente hinzufügen, damit sie im Dialogfeld **Feldeigenschaften** angezeigt werden (siehe [Unterstützung für zusätzliche HTML-Elemente und -Attribute hinzufügen](/help/sites-administering/rte-accessible-content.md#adding-support-for-additional-html-elements-and-attributes)).

#### Weitere Aspekte für Formulare {#additional-considerations-for-forms}

Wenn Daten in einem bestimmten Format eingegeben werden müssen, sollten Sie dies in der Beschriftung deutlich machen. Wenn z. B. ein Datum im Format `DD-MM-YYYY` eingegeben werden soll, fügen Sie diese Angabe in die Beschriftung ein. Wenn Benutzer der Sprachausgabe auf das Feld stoßen, wird daher automatisch die Beschriftung zusammen mit den zusätzlichen Informationen zum Format angezeigt.

Wenn die Eingabe für ein Formularfeld obligatorisch ist, machen Sie dies deutlich, indem Sie das erforderliche Wort als Teil der Bezeichnung verwenden. AEM fügt ein Sternchen hinzu, wenn ein Feld erforderlich ist. Idealerweise sollte jedoch das Wort `required` (erforderlich) direkt in die Beschriftung eingefügt werden (im Feld **Titel** im Bearbeitungsdialogfeld).

![Hinzufügen weiterer Informationen im Feld „Titel“ (das Wort „required“) für Benutzer der Sprachausgabe.](assets/chlimage_1-210.png)

Die Positionierung von Bezeichnungen ist ebenfalls wichtig, da sie ihnen beim Suchen nach geeigneten Feldern helfen. Dies ist besonders wichtig, wenn der Benutzer mit einem komplexen Formular konfrontiert ist. Befolgen Sie die unten stehende Konvention:

* Kontrollkästchen oder Optionsschaltflächen: 
Beschriftungen direkt rechts neben dem Feld platzieren.
* Alle anderen Formularkomponenten (z. B. Textfelder, Kombinationsfelder): 
Beschriftungen entweder direkt über dem Feld oder direkt links vom Feld platzieren.

In einfachen Formularen mit wenigen Funktionen kann die Beschriftung einer Schaltfläche mit `Submit` als Beschriftung für das angrenzende Feld dienen (z. B. `Search`). Dies ist in Situationen nützlich, in denen wenig Platz für die Beschriftung vorhanden ist.

#### Weitere Informationen – Beschriftungen oder Anweisungen (3.3.2) {#more-information-labels-or-instructions}

* [Erfolgskriterium 3.3.2 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-cues.html)
* [Erfolgskriterium 3.3.2 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-minimize-error-cues)
