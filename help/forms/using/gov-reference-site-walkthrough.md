---
title: Schrittweise Anleitung zur We.Gov-Referenz-Website
seo-title: We.Gov reference site walkthrough
description: Informationen dazu, wie AEM Forms Regierungen bei der Verwaltung individueller Informationen unterstützt, finden Sie in der exemplarischen Anleitung zur We.Gov-Referenz-Website.
seo-description: See the We.Gov reference site walkthrough to understand how AEM Forms helps governments manage individual information.
uuid: 348f9067-28b5-47ed-8e83-0dbadeff0854
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 25a6d702-9995-4c63-99d8-3e5d710bb0c4
exl-id: c8ebd18b-fa24-4264-bd17-f553a2a784d9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2753'
ht-degree: 4%

---

# Schrittweise Anleitung zur We.Gov-Referenz-Website {#we-gov-reference-site-walkthrough}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Voraussetzung {#pre-requisite}

Richten Sie Ihre We.Gov-Referenz-Website ein, wie im Abschnitt [Einrichten und Konfigurieren von AEM Forms-Referenz-Sites](/help/forms/using/setup-reference-sites.md).

## Referenz-Website-Szenario {#reference-site-scenario}

We.Gov ist ein vom Staat geleitetes Unternehmen, bei dem sich Adoptiveltern für Kindergeld registrieren können, wenn sie ein Kind adoptiert haben. Die Site verwaltet Folgendes:

* Eignung des Antragstellers, des Adoptivs
* Persönliche und berufliche Angaben des Antragstellers (falls der Antragsteller für Kindergeld berechtigt ist)
* Persönliche Angaben zum adoptierten Kind

   Der Antragsteller kann Details für mehr als ein Kind angeben
* Angaben zum Bankkonto des Antragstellers, auf dem der Antragsteller Kindergeld erhalten kann
* Rückforderung der Anmeldegebühr
* Beurteilung des Antrags
* Genehmigung des Antrags
* Automatisierte Kommunikation mit dem Antragsteller

Sobald der Antrag eingereicht und die Gebühr bezahlt wurde, erhält der Antragsteller eine E-Mail von der Organisation mit der Bestätigung des gesendeten Antrags.

Die We.Gov-Organisation erhält den Antrag. Die Organisation prüft den Antrag und genehmigt die Anträge, die echt sind.

Nachdem der Antrag genehmigt wurde, erhält der Antragsteller eine E-Mail von der We.Gov-Site. Die **Dokument anzeigen** -Option in der E-Mail verlinkt zu einem Dokument mit den Registrierungsdetails des Antragstellers.

Die nachstehende Infografik zeigt den schrittweisen Arbeitsablauf des We.Gov-Referenz-Website-Szenarios.

![workflow_aem_gov_2](assets/workflow_aem_gov_2.png)

Das Szenario schließt folgende Personen ein:

* Sarah Rose, Adoptivmutter, die Kindergeld beantragt
* Joe, das adoptierte Kind
* Gloria Rios, Leiterin der Genehmigungsabteilung, We.Gov
* Conard Simms, der für die Antragsbeurteilung zuständige Außendienstmitarbeiter

## Sarah leitet ihre Berechtigungsprüfung ein {#sarah-initiates-her-eligibility-check}

Ein Antragsteller kann die Berechtigung für Kindergeld überprüfen. Auf der Website können Benutzer Fragen beantworten, damit sie feststellen können, ob ihre Anwendung für Vorteile infrage kommt. Sarah, eine Adoptivmutter, ist eine potenzielle Antragstellerin dafür. Das Berechtigungsformular ist Teil des Antrags für Kindergeld auf der We.Gov-Website. Sarah klickt auf **[!UICONTROL Kinderunterstützung]** auf der We.Gov-Website. Auf der Seite Kindergeld klickt Sarah auf **[!UICONTROL Ihre Berechtigung überprüfen]**.

Zusätzlich zum oben genannten Ansatz kann Sarah auf **[!UICONTROL Erste Schritte]** auf der Homepage. Sarah wird zur Seite &quot;Alle Anwendungen&quot;geleitet, auf der sie auf Übernehmen unter klicken kann **[!UICONTROL Antrag auf Kindergeld]**. Sarah wird dann zur Berechtigungsprüfung geleitet.

Auf der Seite &quot;Berechtigung für Kindergeld überprüfen&quot;wird Sarah eine Reihe von Fragen gestellt, um ihre Berechtigung für Kindergeld zu bestimmen. Anhand der Fragenliste wird sie gefragt:

* Wenn sie die Sorgerecht für das Kind hat
* Wenn sie und das Kind im Bundesstaat GX leben
* Die Altersgruppe des Kindes und die Erziehung des Kindes.

Sarah beantwortet diese Fragen und ihre Berechtigung wird bestätigt. Ihre Antworten bestimmen, ob sie für Kindergeld berechtigt ist.

Sarah wird informiert, dass sie Anspruch auf Kindergeld hat, und die Antragsgebühr beträgt 25 USD.

### Funktionsweise {#how-it-works}

Sarahs Berechtigung wird durch eine Berechtigungsgrenze validiert, die mithilfe des Regeleditors erstellt wurde. Im Regeleditor können Sie Bedingungen angeben, die erfüllt sind, bevor ein Antragsteller das Antragsformular ausfüllen kann. Wenn Sarah, die Antragstellerin, alle Förderkriterien erfüllt, landet sie auf dem Antragsformular.

Die Prüfung der Berechtigung ist Teil des adaptiven Formulars für Kindergeld. Die Regel validiert die Berechtigung, wenn:

* Der Antragsteller ist Elternteil mit Sorgerecht
* Der Antragsteller und das Kind bleiben im Bundesstaat GX
* Der Antragsteller hat die tägliche Betreuung des Kindes
* Das Alter des Kindes, das Unterstützung erhält, liegt unter 16 Jahren.

### Sehen Sie selbst {#see-it-yourself}

Öffnen Sie in Ihrem Browser `https://<hostname>:<PublishPort>/content/we-gov/en.html`. Klicken Sie auf der Site &quot;We.Gov&quot;auf Kindergeld. Klicken Sie auf der Seite Kindergeld auf Berechtigung überprüfen .

So zeigen Sie die Regeln an:

1. Öffnen Sie das Formular im Bearbeitungsmodus in der Autoreninstanz. URL: `https://<hostname>:<AuthorPort>/editor.html/content/forms/af/we-gov/child-support/css.html`.
1. Wählen Sie eine Komponente aus und klicken Sie auf ![edit-rules](assets/edit-rules.png).

   Der Regeleditor wird geöffnet und listet alle im Formular angewendeten Regeln auf.

1. Klicken Sie im linken Seitenbereich auf Regeln . `passMsg` und `failMsg` um zu verstehen, wie die Eignungsprüfung funktioniert.

## Sarah beginnt mit ihrem Antrag auf Kindergeld {#sarah-starts-her-application-for-child-support}

Sarah klickt **[!UICONTROL Anwendung starten]** nachdem sie über ihre Berechtigung für Kindergeld informiert wurde.\
Auf der Seite &quot;Antrag auf Kindergeld&quot;gibt Sarah Details in den folgenden Abschnitten an:

* **[!UICONTROL Über den Antragsteller]**: Ermöglicht Sarah, ihre Details in diesem Abschnitt anzugeben.

* **[!UICONTROL Kinderinformationen]**: Ermöglicht Sarah die Angabe von Kinderinformationen, die unter die Unterstützungsdienste fallen.

* **[!UICONTROL Zahlung]**: Ermöglicht Sarah, ihre Bankdaten anzugeben, in denen We.Gov monatliche Support-Ausgleichszahlungen hinterlegen kann.

* **[!UICONTROL Gebührenzahlung]**: Ermöglicht Sarah, ihre Kreditkartendaten zur Zahlung der Anmeldegebühr anzugeben.

Sarah wird standardmäßig zum **[!UICONTROL Über den Antragsteller]** Abschnitt.

![Kindergeldanwendung auf dem Desktop](assets/desktop.png)

Sarah kann jederzeit auf **[!UICONTROL Später wiederkommen]** und setzen Sie mit ihrem Antrag fort. Wenn sie klickt **[!UICONTROL Später wiederkommen]**, wird ihr Fortschritt als Entwurf gespeichert und sie erhält die Möglichkeit, den Entwurf per E-Mail zu versenden.

Wenn sie klickt **[!UICONTROL E-Mail senden]** erhält sie eine E-Mail mit einem Link zum Formularentwurf.

Das Formular für Kindergeld auf der Site &quot;We.Gov&quot;verwendet adaptive Formulare. Sie kann den Link in ihrer E-Mail verwenden und das Formular auf ihrem Mobilgerät ausfüllen.

>[!NOTE]
>
>Der Workflow &quot;Von E-Mail fortsetzen&quot;funktioniert nur bei angemeldeten Benutzern. Stellen Sie im Referenzsite-Szenario sicher, dass der Benutzer Sarah Rose hinzugefügt wird. Sarahs Anmeldedaten lauten `srose/password`.

![mob1](assets/mob1.png)

Sarah kann in jedem Abschnitt Details angeben, aber die Antragsgebühr wird erst akzeptiert, nachdem sie die erforderlichen Informationen in allen Abschnitten bereitgestellt hat. Ein Antrag ist unvollständig, ohne dass eine Gebühr entrichtet wird, und die mit einem Sternchen gekennzeichneten Felder sind Pflichtfelder.

### <strong>Sarah stellt ihre Informationen bereit</strong> {#strong-sarah-provides-her-information-strong}

Nachdem Sarah klickt **[!UICONTROL Anwendung starten]**, wird sie zum Abschnitt &quot;Informationen zum Antragsteller&quot;auf der Seite &quot;Antrag auf Kindergeld&quot;geleitet. Unter &quot;Informationen zum Antragsteller&quot;navigiert Sarah durch die Registerkarten und gibt ihre personenbezogenen Daten für die Anwendung an. Sie klickt **[!UICONTROL Nächste]** um durch die Registerkarten zu navigieren.

Unter &quot;Informationen zum Antragsteller&quot;wird sie gebeten, auf den folgenden Registerkarten Details anzugeben:

* **[!UICONTROL Grundlegende Informationen]**

Unter &quot;Grundlegende Informationen&quot;stellt Sarah ihren ID-Nachweis und ihre personenbezogenen Daten bereit. Sarahs persönliche Informationen umfassen ihren Namen, ihre E-Mail-Adresse und ihre Sozialversicherungsnummer.

* **[!UICONTROL Beziehung]**

   Unter &quot;Beziehung&quot;gibt Sarah Informationen über ihren Familienstand ein.

* **[!UICONTROL Zusätzliche Informationen]**

   Unter &quot;Zusätzliche Informationen&quot;gibt Sarah eine ID-Nummer, ihr Geburtsdatum sowie die aktuelle Adresse und Telefonnummer ein.

### Sarah stellt Kinderinformationen bereit {#sarah-provides-child-information}

Nachdem Sarah ihre personenbezogenen Daten bereitgestellt hat und auf **[!UICONTROL Nächste]**, wird sie zum Abschnitt &quot;Informationen zum Kind&quot;geleitet.

Im Abschnitt &quot;Informationen zum Kind&quot;gibt sie die folgenden Details an:

* Anzahl der Kinder, für die Kindergeld beantragt werden soll
* Name des Kindes, Sozialversicherungsnummer, Geburtsdatum und Geburtsort

Wenn Sarah mehr als ein Kind auswählt, erhält sie zusätzliche Formulare, die mit denselben Details ausgefüllt werden.\
Sarah wählt ihr einziges Kind, Joe, aus und gibt seinen Namen ein.

### Sarah stellt Zahlungsinformationen bereit {#sarah-provides-payment-information}

Nachdem Sarah Informationen zum adoptierten Kind (oder zu den adoptierten Kindern) bereitgestellt hat, klicken Sie auf **[!UICONTROL Nächste]**, wird sie zur **[!UICONTROL Zahlungsinformationen]** Abschnitt.

Im Bereich Zahlungsinformationen gibt sie die Kontodetails an, auf denen sie die Kindergeld-Leistungen erhalten kann.\
Sie gibt ihre zehnstellige Bankkontonummer ein.

## Sarah zahlt die Anmeldegebühr und unterzeichnet das Formular {#sarah-pays-the-application-fee-and-signs-the-form}

Nachdem Sarah den Nutzungsbedingungen des Antrags zugestimmt hat, zahlt sie die Anmeldegebühr von 25 USD. Für die Bearbeitung ihres Antrags ist eine Anmeldegebühr erforderlich.\
Sarah gibt ihre Kreditkartendetails ein und klickt auf **[!UICONTROL Jetzt bezahlen]**. Nach Zahlung der Gebühren erscheint eine PDF-Version des Antrags mit einem Signaturfeld.

![sarah-sign-1](assets/sarah-sign-1.png)

Sarah kann entweder eintippen, Zeichnen zum Schreiben verwenden, ein Bild der Signatur einfügen oder den Touchscreen ihres Mobiltelefons verwenden, um ihre Signatur zu zeichnen. Sarah gibt ihren Namen ein und klickt auf &quot;Click To Sign&quot;.

Ihr Antrag wird auf der Site &quot;We.Gov&quot;eingereicht.

### <strong>Sarah erhält eine Bestätigungs-E-Mail</strong> {#strong-sarah-receives-an-acknowledgement-email-strong}

Nachdem Sarah die Anmeldegebühr bezahlt hat, erhält sie eine Bestätigungs-E-Mail von der We.Gov-Site.\
We.Gov bearbeitet den Antrag und Sarah wird informiert, dass sie eine monatliche Entschädigung erhält, nachdem ihr Antrag genehmigt wurde.

![sarah-ack-email](assets/sarah-ack-email.png)

### Funktionsweise {#how-it-works-1}

Die Anwendung für Kindergeld verwendet eine Kombination aus Bedienfeldlayouts wie obere Registerkarte, Assistent und Akkordeon, um das Erlebnis zu erstellen. Es wird eine Formularvorlage mit dem Namen &quot;We.Gov Child Template&quot;verwendet.

Der Antragsteller kann zwischen Abschnitten wechseln, um verschiedene Komponenten des Formulars auszufüllen. Wenn der Antragsteller das Formular ausfüllt, einreicht, den Bedingungen zustimmt und die Gebühr zahlt, wird ein benutzerdefinierter Workflow initiiert. Der benutzerdefinierte Workflow sendet eine automatisierte E-Mail an den Antragsteller, in der die Antragseinsendung bestätigt wird. Der Antrag wird zur Prüfung und Genehmigung an die zuständige Abteilung der Organisation weitergeleitet.

Das Layout des Formulars wird im Gov Child Support Service-Design festgelegt. Die Formatierung umfasst Komponentenstil, Seitenhintergrund, Fehlerstatusformatierung von Komponenten und Schriftstile.

Bei der Prüfung der Eignung werden die im Formular angegebenen Regeln verwendet. Es werden die unten angegebenen Gültigkeitsprüfungen verwendet:

`SHOW passMsgWHEN (Does the child live in the state of GX? is equal to Yes) AND (Do you live in the state of GX? is equal to Yes) AND ( (Who has the main day-to-day care of the child? is equal to You) AND (Are you: is equal to The custodial parent) ) AND (Is the child you are applying for: is equal to Under 16 years) ELSE Hide`

`HIDE failMsg WHEN (Does the child lives in the state of GX? is equal to Yes) AND ( (Do you live in the state of GX? is equal to Yes) AND (Who has the main day-to-day care of the child? is equal to You) ) AND (Is the child you are applying for: is equal to Under 16 years) AND (Are you: is equal to The custodial parent) ELSE Show`

### Sehen Sie selbst {#see-it-yourself-1}

Öffnen Sie in Ihrem Browser `https://<hostname>:<PublishPort>/content/forms/af/we-gov/child-support/css.html` und füllen Sie die erforderlichen Informationen aus. Wenn Sie den Antrag senden, nachdem Sie die erforderlichen Informationen ausgefüllt, die Gebühren bezahlt und das Dokument unterschrieben haben, erhalten Sie die Bestätigungs-E-Mail.

Die We.Gov-untergeordnete Vorlage finden Sie hier: `https://<hostname>:<AuthorPort>/editor.html/conf/we-gov/settings/wcm/templates/we-gov-child-template/structure.html`

Das Thema finden Sie hier: `https://<hostname>:<AuthorPort>/editor.html/content/dam/formsanddocuments-themes/we-gov/we-gov-theme-A/jcr:content`

Um alle Regeln anzuzeigen, führen Sie die folgenden Schritte aus:

1. Öffnen Sie das Formular im Authoring-Modus.

   URL: `https://<hostname>:<AuthorPort>/editor.html/content/forms/af/we-gov/child-support/css.html`

1. Wählen Sie eine Komponente aus und tippen Sie auf ![edit-rules](assets/edit-rules.png). Alle Regeln werden im Regeleditor aufgelistet, einschließlich der oben aufgeführten Regeln.

## Gloria erhält den Antrag {#gloria-receives-the-application}

Gloria, Leiter der Genehmigungsabteilung bei We.Gov, kann eingereichte Anträge anzeigen, genehmigen oder ablehnen. AEM Posteingang ermöglicht ihr die Anzeige aller eingereichten Anträge an einem Ort.

### Funktionsweise {#how-it-works-2}

Wenn Sarah den Kindergeld-Antrag ausfüllt und sendet, wird eine PDF oder ein Datensatzdokument des Antrags erstellt und an den Posteingang von Gloria Rios gesendet. Gloria kann den eingereichten Antrag anzeigen und akzeptieren oder ablehnen.

### Sehen Sie selbst {#see-it-yourself-2}

Seite öffnen `https://<hostname***>:<PublishPort>/content/we-gov/en.html`. Tippen Sie auf der Seite auf **[!UICONTROL Anmelden]**, wählen Sie die **[!UICONTROL Als Vertreter anmelden]** aktivieren, melden Sie sich mit grios/password als Benutzernamen/Kennwort für Gloria Rios beim AEM-Posteingang an. Die Kindergeld-Anwendung wird angezeigt. Weitere Informationen zur Verwendung des AEM-Posteingangs für formularzentrierte Workflow-Aufgaben finden Sie unter [Verwalten von Formularanwendungen und Aufgaben im AEM-Posteingang](/help/forms/using/manage-applications-inbox.md).

![Glorias Posteingang auf der We.Gov-Refsite](assets/gloria-inbox.png)

Gloria kann den Antrag im Antrags-Dashboard anzeigen, genehmigen oder ablehnen.

### Funktionsweise {#how-it-works-3}

Gloria, Leiter der Genehmigungsabteilung bei We.Gov, öffnet ihren AEM Posteingang. Sie sieht eine Prüfungsaufgabe in ihrer Aufgabenliste. Sie öffnet und sieht sich die Prüfungsaufgabe an.

Sie sieht eine PDF des Formulars, das mit den von Sarah eingegebenen Informationen sowie den von Sarah hochgeladenen Dokumenten gefüllt ist.\
Gloria kann den Antrag genehmigen oder ablehnen. Gloria klickt jedoch auf **[!UICONTROL Bewertung erforderlich]** , um den Antrag zu prüfen.

![gloria-send-assessment](assets/gloria-sends-assessment.png)

Sarahs Antrag ist ein Startpunkt im AEM Workflow. Er initiiert den AEM Workflow, wenn das Formular für Kindergeld eingereicht wird. Der AEM Workflow erstellt eine Aufgabe für Gloria, die in ihrem AEM Posteingang angezeigt wird. Wenn Gloria eine Überprüfung vor Ort anfordert, wird eine neue Aufgabe für den Feldagenten erstellt.

### Sehen Sie selbst {#see-it-yourself-3}

Wenn die Konfiguration abgeschlossen ist, beginnt der AEM-Workflow sofort, nachdem das Formular gesendet wurde. Melden Sie sich mit den Anmeldedaten von Gloria beim Posteingang an.

Auf Posteingang zugreifen unter https://&lt;***hostname***>:&lt;***PublishPort***>/content/we-gov/en.html. Tippen Sie auf der Seite auf **[!UICONTROL Anmelden]**, wählen Sie die **[!UICONTROL Als Vertreter anmelden]** -Kontrollkästchen verwenden Sie die standardmäßigen Anmeldedaten von Gloria:

* Benutzername: grios
* Kennwort: password

In ihrem AEM Posteingang wird Sarahs Antrag als Prüfungsaufgabe hinzugefügt. Wählen Sie die Aufgabe aus und klicken Sie auf **Bewertung erforderlich** , um mit dem nächsten Schritt fortzufahren.

### Conard erhält die Überprüfungsaufgabe {#conard-assessment-task}

Wenn Gloria klickt **[!UICONTROL Bewertung erforderlich]**, erhält Conard die Prüfungsaufgabe in seinem AEM Posteingang. Die Aufgabe ist der nächste Schritt im AEM Workflow, der im Workflow-Modell definiert ist. Er sieht die Prüfungsaufgabe und öffnet sie.

Conard erhält die Aufgabe zur Überprüfung des Antragstellers wie unten dargestellt.

![Posteingang](assets/conrad-inbox.png)

Die Kindergeld-Bewertung ist ein Formular, das mit der Aufgabe verknüpft ist. Er erhält Sarahs Details zusammen mit den unterstützenden Dokumenten (angehängt in Aufgabendetails). Conard füllt das Überprüfungsformular im Feld auf einem Gerät aus und sendet es zur Neubewertung.

Conard überprüft alle von Sarah angegebenen Details und Sarah unterschreibt die Überprüfung. AEM Forms kann den Ort und den Zeitstempel nehmen und sie zur Signatur hinzufügen.

![submit-for-re-evaluate](assets/submit-for-re-evaluation.png)

Conard-Klicks **[!UICONTROL Zur Neubewertung einreichen]** und der AEM-Workflow die Bewertung an die We.Gov-Organisation sendet.

### Funktionsweise {#how-it-works-4}

Wenn Gloria eine Bewertung anfordert, wird der nächste Schritt in AEM Workflow eingeleitet und die Überprüfungsaufgabe wird in Conards Posteingang hinzugefügt. Conard ist der Außendienstmitarbeiter.

Conard besucht Sarahs Ort, vergewissert sich, dass die von Sarah bereitgestellten Informationen echt sind, und füllt das Überprüfungsformular aus. Conard kann auf eine PDF des vollständigen Formulars zugreifen, das Sarah ausgefüllt hat.

### Sehen Sie selbst {#see-it-yourself-4}

Öffnen Sie den AEM-Posteingang auf Ihrem Tablet und melden Sie sich mit Conards Anmeldedaten an.

Conards Standardanmeldedaten lauten:

* Benutzername: csimms
* Kennwort: password

Im Posteingang wird eine neue Überprüfungsanforderung hinzugefügt. Senden Sie die abgeschlossene Bewertung und fahren Sie mit dem nächsten Schritt fort.

### Gloria prüft die Bewertung und genehmigt den Antrag {#gloria-reviews-the-assessment-and-approves-the-application}

Nachdem Conard die Überprüfung gesendet hat, wird Gloria eine Überprüfungsaufgabe in ihrem Posteingang angezeigt. Sie wählt und öffnet sich **[!UICONTROL Überprüfen]**.

![gloriainbox-1](assets/gloriainbox-1.png)

Unter &quot;Aufgabendetails&quot;sieht Gloria die letzte Aktion, die als &quot;Senden zur Neubewertung&quot;durchgeführt wurde (von Conard). Gloria sieht, dass Conard Simms den Antrag geprüft hat.

![gloriaapproves](assets/gloriaapproves.png)

### Funktionsweise {#how-it-works-5}

Nachdem Conard die Überprüfung gesendet hat, wird Gloria eine Überprüfungsaufgabe in ihrem Posteingang angezeigt. Sie wählt Review aus und öffnet ihn. Unter &quot;Aufgabendetails&quot;sieht Gloria den Bewertungskommentar von Conard, der lautet: &quot;Alles, was in Ordnung gefunden wurde&quot;.

Gloria genehmigt den Antrag.

### Sehen Sie selbst {#see-it-yourself-5}

Öffnen Sie den Posteingang und melden Sie sich mit den Anmeldedaten von Gloria an. Im Posteingang wird eine neue Aufgabe namens &quot;Überprüfen&quot;angezeigt.

Öffnen Sie die Aufgabe, um den Status der zuletzt ausgeführten Aktion anzuzeigen. Genehmigen Sie den Antrag anhand der Beurteilung.

## Sarah erhält eine Genehmigungs-E-Mail {#sarah-receives-an-approval-email}

Nachdem Gloria den Antrag genehmigt hat, erhält Sarah eine E-Mail von We.Gov, dass ihr Antrag genehmigt wurde.

Die **[!UICONTROL Dokument anzeigen]** in der E-Mail Links zu ihren Registrierungsdetails. Sarah klickt **[!UICONTROL Dokument anzeigen.]**

![approval-enrolment-kit-email](assets/approval-enrolment-kit-email.png)

Im Registrierungsdokument werden Details wie die Referenz-ID, das betroffene Kind, das Datum der Initiierung, die Bankkontonummer, die Zahlungsfrequenz und der Zahlungsbetrag aufgelistet.

![sarah-enrollment-details](assets/sarah-enrollment-details.png)

Sarah kann die Dokumente anzeigen, die sie auf derselben Seite hochgeladen hat.

![uploaded-documents](assets/uploaded-documents.png)

### Funktionsweise {#how-it-works-6}

Wenn Gloria den Antrag genehmigt, erhält Sarah eine automatische E-Mail mit einem Link zum Registrierungsdokument.

Das Registrierungsdokument ist eine interaktive Kommunikation, die auf jedem Gerät angezeigt werden kann. Er enthält Details zum Kindergeld-Service und Informationen, die Sarah bereitgestellt hat.

### Sehen Sie selbst {#see-it-yourself-6}

Überprüfen Sie den E-Mail-Client, den Sie für die automatisierte E-Mail mit einem Link zum Registrierungsdokument konfiguriert haben.

Alternativ können Sie das Dokument in Ihrem Browser öffnen: `https://<hostname>:<PublishPort>/content/aemforms-refsite/doclink.html?document=/content/forms/af/we-gov/child-support/enrollment-document&referenceId=[reference-id]&channel=web`

## We.Gov analysiert die Leistung der Anwendung {#we-gov-analyzes-the-performance-of-the-application}

We.Gov überprüft von Zeit zu Zeit die Leistung ihrer Kindergeld-Service-Anwendung, um nach Problemen zu suchen, mit denen Kunden konfrontiert sein könnten. Sie verwenden diese Analyse, um fundierte Entscheidungen über die Änderungen zu treffen, die in der Anwendung für Kindergeld-Services erforderlich sind, um das Benutzererlebnis zu verbessern, die Abbruchrate von Formularen zu reduzieren und damit die Konvertierung zu verbessern. Sie nutzen die Integration von AEM Forms mit Adobe Analytics für ihre Analyse. Die folgende Abbildung zeigt ihr Analyse-Dashboard.

![child-support-analytics-dashboard](assets/child-support-analytics-dashboard.png)

### Funktionsweise {#how-it-works-7}

Die Leistungsmetriken für das Antragsformular für Kindergeld werden mit Adobe Analytics verfolgt. Weitere Informationen zum Konfigurieren von Adobe Analytics und zum Anzeigen von Berichten finden Sie unter [Konfigurieren der Analyse für Formulare und Dokumente](/help/forms/using/configure-analytics-forms-documents.md).

### Sehen Sie selbst {#see-it-yourself-7}

Damit Sie den Analysebericht anzeigen und untersuchen können, stellen wir Seed-Daten für die Anwendung der Kindergeld-Services auf der Referenz-Website bereit. Bevor Sie Seed-Daten verwenden, lesen Sie [Konfigurieren von Analytics](/help/forms/using/setup-reference-sites.md#configureanalytics). Führen Sie die folgenden Schritte in der Autoreninstanz aus, um den Bericht mit den Seed-Daten anzuzeigen:

1. Navigieren Sie zu **[!UICONTROL Forms und Dokumente]** UI unter https://&lt;*hostname*>:&lt;*AuthorPort*>/aem/forms.html/content/dam/formsanddocuments.

1. Klicken Sie auf , um die **We.Gov** Ordner.
1. Auswählen **[!UICONTROL Antrag auf Kindergeld]** adaptives Formular und klicken Sie dann auf **[!UICONTROL Analytics aktivieren]** in der Symbolleiste.

1. Wählen Sie das Formular erneut aus und klicken Sie auf **[!UICONTROL Analytics-Bericht]** in der Symbolleiste, um den Bericht zu erstellen. Zunächst wird ein leerer Bericht angezeigt.

So generieren Sie einen Analysebericht mit Seed-Daten:

1. Geben Sie im Adressbrowser von CRXDE Lite Folgendes ein: **/apps/we-gov/demo-artifacts/analyticsTestData/Child support service Analytics Test Data**
1. Die Seed-Daten werden in der linken Ordnerstruktur ausgewählt.
1. Doppelklicken Sie auf die ausgewählte Datei, um ihren Inhalt im rechten Seitenbereich zu öffnen.
1. Kopieren Sie den gesamten Inhalt der Testdatendatei.
1. Navigieren Sie in CRXDE zu: **/content/dam/formsanddocuments/we-gov/child-support/css/jcr:content/analyticsdatanode/lastsevendays**
1. Fügen Sie im Feld analyticsdata unter Eigenschaften den kopierten Inhalt der Testdatendatei ein.
1. Erstellen Sie nun erneut einen Analysebericht für **[!UICONTROL Antrag auf Kindergeld]**. Die Seed-Daten werden im erstellten Bericht angezeigt.
