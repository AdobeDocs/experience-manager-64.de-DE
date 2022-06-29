---
title: Anleitung zur We.Finance-Referenz-Site
seo-title: We.Finance reference site walkthrough
description: 'Sehen Sie sich die We.Finance-Referenz-Website an, um zu verstehen, wie sie implementiert wurde. We.Finance ist eine Beispielimplementierung, die wichtige Funktionen von AEM Forms zeigt. '
seo-description: Explore the We.Finance reference site and understand how it has been implemented. We.Finance is a sample implementation to showcase key features and functionalities of AEM Forms.
uuid: cbcedba4-6151-475d-b6c2-9859e0382768
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 0c1b6ad7-9d25-41dc-b1fe-a4cb9366c259
exl-id: 17e8c644-ee17-496c-a781-a295a4796cb9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '9201'
ht-degree: 65%

---

# Anleitung zur We.Finance-Referenz-Site {#we-finance-reference-site-walkthrough}

## Voraussetzungen {#pre-requisites}

Richten Sie die Referenz-Websites ein wie in [Einrichten und Konfigurieren von AEM Forms-Referenz-Websites](/help/forms/using/setup-reference-sites.md) beschrieben.

## Szenarien zur We.Finance-Referenz-Site {#we-finance-reference-site-scenarios}

We.Finance ist ein führendes Finanzdienstleistungsunternehmen, das umfassende und personalisierte Finanzlösungen bereitstellt, um die Anforderungen verschiedener Kundenprofile zu erfüllen. Sie bieten Kreditkarten, Haushypotheken und Hausratsversicherungen.

Ihr Ziel ist es, bestehende und potenzielle Kunden auf ihrem bevorzugten Gerät zu erreichen, die Vorteile ihrer Dienste zu erläutern und ihnen bei der Anmeldung bei ihren Diensten zu helfen. Darüber hinaus suchen sie nach weiteren Finanzprodukten wie Add-On-Karten, die für die Kunden interessant sein könnten.

Lesen Sie weiter, um detaillierte Anleitungen zu Anwendungsfällen von We.Finance zu erhalten und zu verstehen, wie AEM Forms Finanzorganisationen dabei hilft, ihre Ziele zu erreichen. Die folgenden exemplarischen Vorgehensweisen werden behandelt:

* [Anleitung für einen Antrag auf Kreditkarten](#credit-card-application-walkthrough)
* [Haushypothekantrag - Anleitung](#home-mortgage-application-walkthrough)
* [Hypothekenantrag - Anleitung mit Microsoft Dynamics](#home-mortgage-application-walkthrough-with-microsoft-dynamics)
* [Antrag auf Hypothek - Anleitung](#home-insurance-application-walkthrough)
* [Anleitung zum Vermögensmanagement](#wealthmanagementwalkthrough)
* [Anleitung zur Anwendung für automatische Versicherung](#autoinsuranceapplicationwalkthrough)

## Anleitung für einen Antrag auf Kreditkarten {#credit-card-application-walkthrough}

Das Szenario für einen Antrag auf eine We.Finance-Kreditkarte umfasst folgende Personen:

* Sarah Rose, einen We.Finance-Kunden
* Gloria Rios, Direktor von Kreditkarten und Hypotheken bei We.Finance

Die folgende Infografik zeigt eine Schritt-für-Schritt-Anleitung für einen Antrag auf eine Kreditkarte.

![workflow_aem](assets/workflow_aem.png)

Schauen wir uns das Referenz-Site-Szenario im Detail an, um zu verstehen, wie die AEM-Formulare We.Finance dabei helfen, ihre Ziele zu erreichen.

### Sarah erhält einen Newsletter von We.Finance und beantragt eine Kreditkarte {#sarah-receives-a-newsletter-from-we-finance-and-applies-for-a-credit-card}

Sarah Rose ist bereits eine We.Finance-Kundin. Sie erhält einen Newsletter von We.Finance über neue Kreditkartenangebote. Sie findet die Angebote spannend und beschließt, eine Kreditkarte zu beantragen. Sie klickt im Newsletter auf die Schaltfläche „Jetzt beantragen“, was sie zum Kreditkartenantrag auf dem Portal We.Finance leitet.

![marketing-email](assets/marketing-email.png)

#### Funktionsweise {#how-it-works}

Der an Sarah gesendete Newsletter ist eine benutzerdefinierte Implementierung, die eine E-Mail an die angegebene E-Mail-ID auslöst. Die Schaltfläche „Jetzt beantragen“ in der E-Mail ist mit dem Kreditkartenantrag verknüpft, bei dem es sich um ein adaptives Formular für eine Veröffentlichungsinstanz handelt.

#### Sehen Sie selbst {#see-it-yourself}

Öffnen Sie die folgende URL in der Veröffentlichungsinstanz, um eine Newsletter-E-Mail Trigger. Stellen Sie sicher, dass Sie `[emailID]` mit einem gültigen E-Mail-Konto, um den Newsletter zu erhalten. Öffnen Sie den Newsletter und klicken Sie auf **[!UICONTROL Jetzt beantragen]**, um zum Kreditkartenantrag zu gelangen.

`https://[publishServer]:[publsihPort]/content/campaigns/we-finance/start.html?app=cc&email=[emailID]&givenName=Sarah&familyName=Rose`

### Sarah findet das Angebot interessant und beschließt, einen Antrag zu stellen  {#sarah-finds-the-offer-interesting-and-chooses-to-apply}

Sarah beschließt, sich um die Kreditkarte zu bewerben und tippt **[!UICONTROL Jetzt anwenden]** in der E-Mail. Sarah wird zum Kreditkartenantrag auf dem We.Finance-Portal geleitet.  Das Antragsformular besteht aus verschiedenen Abschnitten, wie beispielsweise dem Kartenlayout.

Sarah wählt eine Kreditkarte aus den verfügbaren Optionen aus und klickt auf **[!UICONTROL Weiter]**.

![cc-application-form-desktop](assets/cc-application-form-desktop.png)

Auf der Seite „Persönliche Daten“ erhält Sarah, da sie ihre Sozialversicherungsnummer angibt, eine Aufforderung, sich mit ihren Zugangsdaten anzumelden.

![login-ssn](assets/login-ssn.png)

Sarah ist bereits eine We.Finance-Kundin. Sie meldet sich mit ihren We.Finance-Kontoanmeldeinformationen an und ihre persönlichen Daten werden im Formular automatisch ausgefüllt. Sarah füllt weiterhin das Antragsformular aus. Dann erscheint eine Erinnerung an ein Treffen, an dem sie teilnehmen muss. Sie klickt **[!UICONTROL Fortschritt speichern]** auf dem Antragsformular. Es speichert alle Informationen, die Sarah bisher eingegeben hat, und es wird ein Dialogfeld angezeigt, in dem Sie bestätigen kann, ob sie eine E-Mail mit einem Link zu ihrem Entwurf anfordern möchte, den sie später ausfüllen möchte.

Sarah klickt auf **[!UICONTROL E-Mail senden]**. Sie erhält eine E-Mail mit einem Link, um ihren Kreditkartenantrag fortzusetzen.

![resume](assets/resume.png)


<!--Theses sections used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Sarah greift von ihrem Mobilgerät aus auf den Kreditkartenantrag zu {#a-sarah-access}

Wenn Sarah von ihrem Mobilgerät aus auf den Kreditkartenantrag zugreift, wird der interaktive Antrag in einer für mobile Geräte optimierten Ansicht geöffnet. In dieser Ansicht wird das Antragsformular als ein Abschnitt wiedergegeben. Es ermöglicht Sarah, Informationen progressiv zu sehen und zu liefern, während sie durch den Antrag navigiert.

![form-on-mobile](assets/form-on-mobile.png)

### Funktionsweise {#a-how-it-works}

Über die Schaltfläche **[!UICONTROL Jetzt beantragen]** wird Sarah zum Kreditkartenantrag geleitet. Der Antrag ist ein adaptives Formular, das Sie in den Authoring-Instanzen unter `https://[host]:[Port]/editor.html/content/forms/af/we-finance/cc-app.html`.

Einige der wichtigsten Funktionen, die Sie im adaptiven Formular überprüfen können, sind:

* Es basiert auf einem XSD-Schema.
* Es wird mit dem We Finance-Design A für Stile und der We.Finance-Vorlage für Layout erstellt. Außerdem verwendet es im Formularkopfzeilenlayout für die mobile Navigation Layout ohne Bereichstitel. Es zeigt ein progressives Layout für Mobilgeräte an, wenn es von einem Mobilgerät aus geöffnet wird. Sie können die Vorlage unter `https://[host]:[Port]/libs/wcm/core/content/sites/templates.html/conf/we-finance` und das Thema unter `https://[host]:[Port]/editor.html/content/dam/formsanddocuments-themes/we-finance/we-finance-theme-a/jcr:content`.
* Es enthält adaptive Formularregeln zum Aufrufen von Formulardatenmodelldiensten, um Benutzerdetails des angemeldeten Benutzers vorab zu befüllen. Es ruft auch Dienste auf, um Informationen anhand der im Formular angegebenen Sozialversicherungsnummer oder E-Mail-Adresse vorab zu befüllen. Sie können die Formulardatenmodelle und ihre Dienste unter `https://[host]:[Port]/aem/forms.html/content/dam/formsanddocuments-fdm`.
* Es verwendet verschiedene adaptive Formularkomponenten, um Eingaben zu erfassen und sich an Benutzerreaktionen anzupassen. Es verwendet auch Komponenten wie E-Mail, die HTML5-Eingabetypen unterstützen.
* Es verwendet die Signaturschrittkomponente, um das ausgefüllte Formular anzuzeigen, und ermöglicht die elektronische Unterschrift auf dem Formular.
* Die Schaltfläche „Fortschritt speichern“ generiert eine eindeutige ID für den Benutzer und speichert die teilweise ausgefüllte Anwendung als Entwurf in einem Knoten im AEM-Repository. Außerdem wird ein Dialogfeld mit einer Bitte um Bestätigung angezeigt, damit eine E-Mail mit einer Verknüpfung zu dem Knoten gesendet werden kann, der den Antragsentwurf enthält. Über die im Bestätigungsdialogfeld angezeigte Schaltfläche E-Mail senden wird die Versendung einer E-Mail mit einer Verknüpfung zu dem Knoten ausgelöst, der den Entwurf enthält.
* Es verwendet die Aktion „AEM-Workflow aufrufen“, um den Kreditkarten-Genehmigungs-Workflow auszulösen. Sie können den in diesem Formular verwendeten Workflow unter `https://[host]:[Port]/editor.html/conf/global/settings/workflow/models/we-finance-credit-card-workflow.html`

Es wird empfohlen, das Formular zu lesen, um das Schema, die Komponenten, die Regeln, die Formulardatenmodelle, den Formularworkflow und die Aktion zum Erstellen des Formulars zu verstehen.

In der folgenden Dokumentation finden Sie weitere Informationen zu Funktionen, die im adaptiven Formular des Kreditkartenantrags verwendet werden:

* [Einführung in das Authoring adaptiver Formulare](/help/forms/using/introduction-forms-authoring.md)
* [Adaptive Formulare mithilfe des XML-Schemas erstellen](/help/forms/using/adaptive-form-xml-schema-form-model.md)
* [Regeleditor](/help/forms/using/rule-editor.md)
* [Designs](/help/forms/using/themes.md)
* [-Datenintegration](/help/forms/using/data-integration.md)
* [Verwenden von Adobe Sign in adaptiven Formularen ](/help/forms/using/working-with-adobe-sign.md)
* [Formularzentrierte Workflows in OSGi](/help/forms/using/aem-forms-workflow.md)

### Sehen Sie selbst {#a-see-it-yourself}

Wenn Sie als Sarah Rose angemeldet sind, klicken Sie im Kreditkartenantrag auf **[!UICONTROL Jetzt beantragen]**. Vervollständigen Sie Angaben, sehen Sie sich verschiedene adaptive Formularkomponenten an, und klicken Sie auf **[!UICONTROL Fortschritt speichern]**, um eine weitere E-Mail mit der Schaltfläche **[!UICONTROL Fortsetzen]** zu enthalten, die eine Verknüpfung mit dem Antragsentwurf enthält. Stellen Sie sicher, dass Sie Ihre E-Mail-ID des Antragsformulars angeben, um E-Mails zu empfangen.

Überprüfen Sie das We.Finance-Design, das verfügbar ist:

`https://<host>:<AuthorPort>/editor.html/content/dam/formsanddocuments-themes/we-Finance/we-Finance-Theme-A/jcr:content`

Sie können die We.Finance-Vorlage hier ansehen:

`https://<host>:<AuthorPort>/editor.html/conf/we-finance/settings/wcm/templates/we-finance-template/structure.html`

### Sarah setzt den Vorgang fort und sendet den Antrag  {#sarah-resumes-and-submits-the-application}

Sarah kommt später zurück und findet eine E-Mail von We.Finance. Sie klickt auf die Schaltfläche **[!UICONTROL Fortsetzen]** in der E-Mail, die sie zu ihrem Kreditkartenantrag führt. Die Informationen, die Sie zuvor eingetragen hat, sind bereits vorausgefüllt. Sie füllt das verbleibende Antragsformular aus, unterschreibt den Antrag und reicht ihn ein.

![resume-1](assets/resume-1.png)

Alternativ kann sie auf der Homepage von **[!UICONTROL Meine Formulare]** unter We.Finance auf ihren Entwurf zugreifen.

![portal-drafts](assets/portal-drafts.png)

#### Funktionsweise {#how-it-works-1}

Mithilfe der in der E-Mail angezeigten Schaltfläche „Fortsetzen“ gelangt Sarah zu dem Knoten, der ihren Antragsentwurf enthält.

#### Sehen Sie selbst {#see-it-yourself-1}

Sie müssen eine E-Mail mit einem Link zum Antragsentwurf in Ihrer E-Mail-ID erhalten haben, die Sie beim Ausfüllen des Antragsformulars angegeben haben. Füllen Sie die übrigen Abschnitte des Antrags aus und senden Sie ihn. 

### We.Finance erhält und genehmigt den Antrag {#approving-the-application}

We.Finance erhält den Kreditkartenantrag von Sarah. Eine Aufgabe wird Gloria Rios zugewiesen. Sie überprüft die Aufgabe in ihrem AEM-Posteingang und genehmigt sie.

![inbox](assets/inbox.png)

#### Funktionsweise {#how-it-works-2}

Wenn Sarah den Kreditkartenantrag ausfüllt und abschickt, wird ein Formularworkflow ausgelöst und eine Aufgabe in Glorias AEM-Posteingang erstellt.

AEM Forms on OSGi bietet formularbasierte Workflows, mit denen Sie adaptive formularbasierte Workflows erstellen können. Diese Workflows können für Überprüfungen und Genehmigungen, Geschäftsprozessabläufe, zum Starten von Dokumentdiensten, zur Integration mit Adobe Sign-Signatur-Workflows usw. verwendet werden. Weitere Informationen finden Sie unter [Formularzentrierte Workflows in OSGi](/help/forms/using/aem-forms-workflow.md).

Die folgende Abbildung zeigt den AEM-Workflow, der den Kreditkartenantrag verarbeitet und eine PDF-Ausgabe des Antrags generiert. 

![ Workflow](assets/workflow.png)

#### Sehen Sie selbst {#see-it-yourself-2}

Sie können AEM Posteingang für die Site &quot;we.finance&quot;unter https://&lt;*hostname*>:&lt;*PublishPort*>/content/we-finance/global/en.html. Tippen Sie auf der Seite auf **[!UICONTROL Anmelden]**, wählen Sie die **[!UICONTROL Als Vertreter anmelden]** Kontrollkästchen aktivieren, melden Sie sich mit `grios/password` als Benutzernamen/Kennwort für Gloria Rios und genehmigen Sie den Kreditkartenantrag. Weitere Informationen zur Verwendung des AEM-Posteingangs für formularzentrierte Workflow-Aufgaben finden Sie unter [Verwalten von Formularanwendungen und Aufgaben im AEM-Posteingang](/help/forms/using/manage-applications-inbox.md).

![inbox-1](assets/inbox-1.png)

Wenn Sie dden Antrag genehmigen, erhält Sarah eine E-Mail mit einem Wilkommens-Kit.

### Sarah erhält das Willkommenspaket und beantragt eine Zusatzkarte {#sarah-receives-the-welcome-kit-and-applies-for-an-add-on-card}

Während der von Sarah gestellte Kreditkartenantrag genehmigt wird, erhält sie eine E-Mail mit einer Verknüpfung zum Begrüßungs-Kit. Sie öffnet das Begrüßungs-Kit, das Angaben zu ihrem Kreditkartekonto enthält. Das Begrüßungs-Kit enthält auch für Sarah personalisierte Werbeangebote. Wenn Alison nach unten blättert, sieht sie, dass das Begrüßungs-Kit ein eingebettetes Formular für die Beantragung einer Zusatzkarte enthält. Sarah füllt schnell die erforderlichen Informationen aus dem Begrüßungs-Kit aus und beantragt die Zusatzkarte. Ein Bestätigungsdialogfeld für den Zusatzkartenantrag wird angezeigt. 

![welcome-kit-for-sara](assets/welcome-kit-for-sara.png)

Das Begrüßungs-Kit ist für Sarah personalisiert und zeigt Informationen, die für sie relevant sind. Es bietet die Möglichkeit, eine PDF-Version des Begrüßungs-Kits herunterzuladen.

![Vorteile einer Platin-Karte](assets/benefits-of-platinum-card.png)

Das Begrüßungspaket enthält ein weiteres Antragsformular, das Sarah ausfüllen und einreichen kann, um eine Zusatzkarte aus dem Willkommenspaket zu beantragen, ohne das We.Finance-Portal zu besuchen.

![apply-addon-card](assets/apply-addon-card.png)

#### Funktionsweise {#how-it-works-3}

Das Begrüßungs-Kit ist eine interaktive Kommunikation, die im `cq-we-finance-content-pkg.zip` Paket. Die interaktiven Karten in der Desktopversion, welche die Vorteile der Kreditkarte im Begrüßungs-Kit zeigt, haben ein benutzerdefiniertes Layout, das mithilfe des Standardkartenlayouts eines Dokumentfragments erstellt wird. 

Der Zusatzkartenantrag ist ein eingebettetes adaptives Formular in der interaktiven Kommunikation des Begrüßungs-Kits.

#### Sehen Sie selbst {#see-it-yourself-3}

Klicken Sie auf **[!UICONTROL Fortsetzen]** in der E-Mail, die Sie im vorherigen Schritt erhalten haben. Dadurch wird der Antragsentwurf geöffnet. Tragen Sie alle Angaben ein und senden Sie den Antrag. Dann erhalten Sie ein Begrüßungs-Kit. Prüfen Sie das Begrüßungs-Kit. 

Sie können das Willkommenspaket auch unter der folgenden URL anzeigen:

https://&lt;*Host*>:&lt;*port*>/content/aemforms-refsite/doclink.html?document=/content/forms/af/we-finance/credit-card/creditcardwelcomekit&amp;customerId=197&amp;channel=web

Sie können auf sie in den Autor- und Veröffentlichungsinstanzen zugreifen.

### Sarah erhält einen Kreditkartenauszug  {#sarah-receives-a-credit-card-statement}

Als Sarah anfängt, die Kreditkarte zu benutzen, erhält sie eine weitere E-Mail von We.Finance, die ihre Kreditkartenabrechnung enthält. Die folgenden Abbildungen zeigen die E-Mail mit einer Verknüpfung zum Kreditkartenauszug auf dem Mobilgerät. 

![statement-email](assets/statement-email.png)

Sarah klickt in der E-Mail auf „Auszug anzeigen“, um den Kreditkartenauszug anzuzeigen. Die Anweisung ist eine interaktive Kommunikation. Es verfügt sowohl über Web- als auch über Print-Versionen (PDF). Die Anweisung wird in das Forms-Datenmodell integriert, um kundenspezifische Daten aus der Datenbank abzurufen. Der interaktive Auszug besteht aus verschiedenen Elementen:

* Auszugsübersicht
* Ausführlicher Ausgabenbericht 
* Grafische Ausgabenanalyse 
* Option für die Tätigung der Zahlung eines fälligen Betrags innerhalb des Auszugs 
* Zahlungsbeleg herunterladen 

![Verschiedene Teile des Kreditkartenauszugs](assets/sara-rose-statement.png)

Sarah muss nicht zum Portal gehen oder in ihren E-Mails nach einer PDF-Version des Kreditkartenauszugs suchen, um die Offline-Archivierung durchzuführen. Sie klickt einfach auf die Download-Anweisung, um eine PDF-Version der Anweisung herunterzuladen.

Die detaillierte Anweisung wird in einer responsiven Tabelle dargestellt. Der Auszug bietet auch die Möglichkeit, einen Teil oder den gesamten fälligen Betrag innerhalb des Auszugs zu bezahlen.

![Ausführlicher Auszug](assets/statement-details.png)

Sarah plant die Zahlung innerhalb des Auszugs. Sarah kann auch die Flexi Pay-Option verwenden, um die Zahlung in gleiche Teile zu unterteilen.

#### Funktionsweise {#how-it-works-4}

Der Kreditkartenauszug ist eine interaktive Kommunikation. Die detaillierte Ausgabentabelle im Auszug ist reagibel. Die Grafik zur Ausgabenanalyse ist eine Diagrammkomponente, liest die Ausgabentabelle und generiert das Kreisdiagramm.

#### Sehen Sie selbst {#see-it-yourself-4}

Sie können den interaktiven Kreditkartenauszug unter folgender URL einsehen: 

https://&lt;*hostname*>:&lt;*port*>/content/aemforms-refsite/doclink.html?document=/content/forms/af/we-finance/credit-card/credit-card-statement&amp;customerId=197&amp;channel=web

Sie können auf sie in den Autor- und Veröffentlichungsinstanzen zugreifen.

Der Kreditkartenauszug zeigt Werbeangebote am Ende des Auszugs an. Sie können Adobe Target in die interaktive Kommunikation mit AEM Forms integrieren, um auf der Grundlage bestimmter Kundensegmente zielgerichtete Werbeangebote bereitzustellen. Informationen zum Konfigurieren der interaktiven Kommunikation für die Verwendung von Adobe Target für benutzerdefinierte und zielgerichtete Angebote finden Sie unter [Erstellen zielgerichteter Erlebnisse](/help/forms/using/experience-targeting-forms.md).

![](do-not-localize/offers.png)

### We.Finance analysiert die Leistung des Kreditkartenantrags {#we-finance-analyzes-the-performance-of-the-credit-card-application}

We.Finance überprüft von Zeit zu Zeit die Leistung seiner Kreditkarteanwendung, um festzustellen, ob Probleme auftreten, mit denen Kunden konfrontiert werden können. Das Unternehmen verwendet diese Analyse, um fundierte Entscheidungen über erforderliche Änderungen an der Kreditkarteanwendung zu treffen. Auf diese Weise wird die Benutzerfreundlichkeit verbessert und die Abbruchrate der Formulare reduziert, wodurch die Konversionsrate erhöht wird. Zur Analyse nutzt das Unternehmen die Integration von AEM Forms mit Adobe Analytics. Die folgende Abbildung zeigt das Analyse-Dashboard des Unternehmens.

Weitere Informationen zur Interpretation des Analyse-Dashboards finden Sie unter [Anzeigen und Verstehen von AEM Forms-Analyseberichten](/help/forms/using/view-understand-aem-forms-analytics-reports.md).

![cc-analytics](assets/cc-analytics.png)

#### Funktionsweise {#how-it-works-5}

Die Leistungsmetriken für das Kreditkartenantragsformular werden mit Adobe Analytics verfolgt. Weitere Informationen zur Konfiguration von Adobe Analytics und zum Anzeigen der Berichte finden Sie unter [Konfigurieren der Analyse für Formulare und Dokumente](/help/forms/using/configure-analytics-forms-documents.md).

#### Sehen Sie selbst {#see-it-yourself-br}

Damit Sie den Analysebericht anzeigen und prüfen können, stellen wir Seed-Daten für die Kreditkarteanwendung in der Referenz-Website bereit. Bevor Sie Seed-Daten verwenden, lesen Sie[ Konfigurieren von Analytics](/help/forms/using/setup-reference-sites.md#configureanalytics). Führen Sie folgende Schritte im Autorenmodus aus, um den Bericht mit den Seed-Daten anzuzeigen: 

1. Navigieren Sie zu **[!UICONTROL Forms und Dokumente]** UI unter https://&lt;*hostname*>:&lt;*AuthorPort*>/aem/forms.html/content/dam/formsanddocuments.

1. Klicken Sie auf den Ordner **[!UICONTROL We.Finance]**, um ihn zu öffnen.
1. Auswählen **[!UICONTROL Kreditkartenantrag]** adaptives Formular und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Analytics aktivieren]**.

1. Wählen Sie das adaptive Formular erneut aus und klicken Sie auf **[!UICONTROL Analytics-Bericht]** in der Symbolleiste, um den Bericht zu erstellen. Zunächst wird ein leerer Bericht angezeigt.

So generieren Sie einen Analysebericht mit Seed-Daten:

1. Im Adressbrowser von CRXDE Lite, geben Sie Folgendes ein: `/apps/we-finance/demo-artifacts/analyticsTestData/Credit card Analytics Test Data`
1. Die Testdaten werden in der linken Seitenstruktur ausgewählt.
1. Doppelklicken Sie auf die ausgewählte Datei, um ihren Inhalt im rechten Seitenbereich zu öffnen.
1. Kopieren Sie den gesamten Inhalt der Seed-Datendatei.
1. Navigieren Sie in CRXDE zu: `/content/dam/formsanddocuments/we-finance/cc-app/jcr:content/analyticsdatanode/lastsevendays`
1. Im **[!UICONTROL analyticsdata]** Feld unter **[!UICONTROL Eigenschaften]**, fügen Sie den kopierten Inhalt der Seed-Datendatei ein.

1. Auswählen **Kreditkartenantrag** adaptives Formular und klicken Sie auf **[!UICONTROL Analytics-Bericht]** in der Symbolleiste, um den Bericht mit Seed-Daten zu generieren.

**A/B-Tests der Kreditkarteanwendung** 

Zusätzlich zur Analyse und kontinuierlichen Verbesserung der Kreditkartenanwendung nutzt We.Finance die Integration von AEM Forms mit Target, um A/B-Tests zu erstellen. Dadurch ist es möglich, auf verschiedene Erlebnisse im Zusammenhang mit der Bearbeitung des Kreditkartenantragsformulars zu reagieren und Erlebnisse zu bestimmen, die zu einer besseren Konversionsrate in Bezug auf das Ausfüllen und Übermitten von Formularen führen. 

Informationen zum Konfigurieren von Target auf dem AEM Forms-Server finden Sie unter [Target einrichten und in AEM Forms integrieren](/help/forms/using/ab-testing-adaptive-forms.md#set%20up%20and%20integrate%20target%20in%20aem%20forms).

Führen Sie folgende Schritte aus, um die Erstellung eines A/B-Tests für das We.Finance-Kreditkartenantragsformular zu erleben: 

1. Navigieren Sie zu **[!UICONTROL Forms und Dokumente]** https://&lt;*hostname*>:&lt;*AuthorPort*>/aem/forms.html/content/dam/formsanddocuments.

1. Klicken Sie auf den Ordner **[!UICONTROL We.Finance]**, um ihn zu öffnen.
1. Wählen Sie das adaptive Formular **[!UICONTROL Kreditkartenantrag]**.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Mehr]** und wählen Sie **[!UICONTROL A/B-Tests konfigurieren]**. Die Seite „A/B-Tests konfigurieren“ wird geöffnet.

1. Geben Sie eine **[!UICONTROL Aktivitätsbezeichnung]** an.
1. Wählen Sie in der Dropdown-Liste „Zielgruppe“ die Zielgruppe, deren Reaktionen auf verschiedene Varianten des Formulars Sie testen möchten. Dies könnten beispielsweise **Besucher, die Chrome verwenden** sein.
1. Geben Sie in den Feldern für **[!UICONTROL Erlebnisverteilung]** für die Erlebnisvarianten A und B deren Verteilung auf die Gesamtzielgruppe in Prozent an. Wenn Sie beispielsweise „40“ und „60“ für Erlebnis A bzw. B angeben, wird Erlebnis A für 40 % der Zielgruppe und Erlebnis B für die verbleibenden 60 % angezeigt.
1. Klicken Sie auf **Konfigurieren**. Es wird ein Dialogfeld angezeigt, in dem die Erstellung des A/B-Tests bestätigt wird.
1. Klicken Sie auf **Fertig**.
1. Wählen Sie die **Kreditkartenantrag** Formular und klicken Sie auf **Bearbeiten**. Es bietet die Möglichkeit, eines der Erlebnisse zu öffnen. Klicken Sie auf **Erlebnis B**. Das Formular wird im Bearbeitungsmodus geöffnet. 

1. Ändern Sie beliebig das Formular, um ein anderes Erlebnis als das Standarderlebnis A zu erstellen. 
1. Wechseln Sie zur Benutzeroberfläche für Formulare und Dokumente, wählen Sie das Formular aus, klicken Sie auf **Mehr** und wählen Sie **A/B-Tests starten**.

1. Öffnen Sie jetzt das Formular mehrmals im Chrome-Browser mit der folgenden URL:

   `https://[hostname]:[port]/content/dam/formsanddocuments/we-finance/cc-app/jcr:content?wcmmode=disabled`

   >[!NOTE]
   >
   >Entfernen Sie das Cookie mit dem Namen **mbox** aus der Cookiepersistenz des Browsers, bevor Sie das Formular das nächste Mal öffnen. Sie sehen dann das Erlebnis A und B des Formulars in zufälliger Ordnung.

1. Wählen Sie das Formular aus, klicken Sie auf **Mehr**, und klicken Sie dann auf **A/B-Testbericht**. Sie werden nicht viele Daten im Bericht finden, da Sie gerade erst mit dem Testen begonnen haben. Jetzt werden wir einige Seed-Daten bereitstellen, um zu sehen, wie der A/B-Testbericht aussehen wird. 

1. Öffnen Sie CRXDE Lite und erstellen Sie eine Sicherungskopie der folgenden Datei: /libs/fd/fmaddon/gui/components/admin/targetreport/clientlibs/targetreport/js/targetreport.js
1. Ersetzen der Definition der Funktion `onReportLoadSuccess` in der oben genannten Datei mit der Funktionsdefinition in der folgenden Datei: /apps/we-finance/demo-artifacts/targetreport.js

   **Hinweis:** Diese Änderungen dienen nur dem Zweck der Demo. Stellen Sie unbedingt den Dateiinhalt wieder her, nachdem Sie dieses Verfahren abgeschlossen haben. 

1. Aktualisieren Sie den von Ihnen erstellten Bericht. Dann sehen Sie Folgendes. Prüfen Sie das Berichts-Dashboard. 

![ab-test-report-3](assets/ab-test-report-3.png)

Um den A/B-Test zu beenden, klicken Sie im Berichts-Dashboard auf die Schaltfläche **A/B-Test beenden**. An diesem Punkt Sie aufgefordert, ein Erlebnis anzugeben. Wählen Sie einen Gewinner und bestätigen Sie, dass Sie den A/B-Test beenden möchten.
 

Wenn Sie Erlebnis A als Gewinner auswählen, wird der A/B-Test beendet, und in Zukunft wird nur Erlebnis A für sämtliche Zielgruppen (einschließlich Chrome-Benutzer) angezeigt.

## Haushypothekantrag - Anleitung {#home-mortgage-application-walkthrough}

Das Szenario der Hypothek von We.Finance umfasst folgende Personen:

* Sarah Rose, einen We.Finance-Kunden
* Gloria Rios, Direktor von Kreditkarten und Hypotheken bei We.Finance
* John Doe, Kundenbetreuer, We.Finance

Die folgende Infografik zeigt eine Schritt-für-Schritt-Anleitung für einen Antrag auf eine Hypothek.

![home_mortgage_application_walkthrough](assets/home_mortgage_application_walkthrough.png)

Schauen wir uns nun an, wie die Schritte des Referenz-Website-Szenarios im Einzelnen aussehen, um Aufschluss zu erhalten, wie AEM Forms dem Unternehmen We.Finance hilft, das Ziel zu erreichen. 

### Sarah besucht die Website von We.Finance und beantragt eine Hypothek {#sarah-visits-we-finance-website-and-applies-for-home-mortgage}

Sarah Rose plant, ein Haus zu kaufen und nach einem Hypotheksplan zu suchen. Sie ist eine We.Finance-Kundin und besucht daher das We.Finance-Portal, um Hypothekenangebote zu erkunden. Sie geht in den Bereich „Kredite“ und findet einen Hypothekenrechner auf dem Portal. Sie füllt die Details aus und klickt auf „Meine Hypothek berechnen“, die einen Hypothekenplan zurückgibt.

![Kredite1](assets/loans1.png) ![Kredite2](assets/loans2.png)
**Abbildung:** *Hypothekenrechner*

![Kredite3](assets/loans3.png)
**Abbildung:** *Ergebnis des Hypothekenrechners*

#### Funktionsweise {#how-it-works-6}

Der Hypothekenrechner auf der Seite „Darlehen“ ist ein eingebettetes adaptives Formular in der AEM-Seite. Sie können die Seite Darlehen im Bearbeitungsmodus unter `https://[authorHost]:[authorPort]/editor.html/content/we-finance/global/en/loan-landing-page.html`.

Der eingebettete Hypothekenrechner, bei dem es sich um ein adaptives Formular handelt, verwendet Regeln zur Berechnung des EMI-Betrags basierend auf den Kreditdetails, die in den Rechnerfeldern angegeben sind. Sie können das adaptive Formular unter `https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/hm-calc.html` überprüfen.

#### Sehen Sie selbst {#see-it-yourself-5}

Gehen Sie zum We.Finance-Portal unter `https://<publishHost>:<publishPort>/content/we-finance/global/en.html` und klicken Sie auf **[!UICONTROL Darlehen]**. Geben Sie Details in den Hypothekenrechner ein und sehen Sie sich die Ergebnisse an.

### Sarah findet das Angebot interessant und beschließt, einen Antrag zu stellen  {#sarah-finds-the-offer-interesting-and-chooses-to-apply-1}

Sarah beschließt, einen Antrag auf Hypothek und Klicks zu stellen **[!UICONTROL Jetzt anwenden]** auf Hypothekenrechner. Es wird der Antrag für Hypotheken geöffnet.

Wenn Sarah von ihrem Mobilgerät aus auf den Antrag für die Hypothek zugreift, wird das Antragsformular in einer Ansicht geöffnet, die für die Anzeige auf einem mobilen Gerät optimiert ist. In dieser Ansicht zeigt das Antragsformular jeweils einen Abschnitt an. Es ermöglicht Sarah, Informationen progressiv zu sehen und zu liefern, während sie durch das Antragsformular navigiert.

Die folgenden Bilder zeigen den Arbeitsablauf, während Sarah auf ihrem Mobilgerät durch die Hypothekenanwendung navigiert.

![Ausfüllen des Hypothekenantrags auf einem Mobilgerät](assets/mortgage-form-on-mobile.png)

Wenn Sarah von ihrem Desktop aus auf **Jetzt beantragen** klickt, öffnet sich das Antragsformular für Hypotheken wie folgt. Die Informationen, die Sarah im Hypothekenrechner zur Verfügung stellt, sind im Antragsformular vorgefüllt. Sarah füllt die restlichen Details aus und klickt auf **Weiter**.

![Hypothekenanwendung](assets/mortgage-application.png)

Basierend auf den Informationen, die Sarah in den Hypothekenrechner eingegeben hat, werden ihr einige Hypothekenpläne vorgelegt. Sie wählt den Plan, der ihren Anforderungen entspricht, und füllt weiterhin den Antrag aus. Sie unterschreibt und reicht den Antrag ein.

Der eingereichte Antrag geht an We.Finance zur Genehmigung.

![Speichern eines Antragsentwurfs](assets/mortgage-plans.png)

#### Funktionsweise {#how-it-works-7}

Die Schaltfläche **Jetzt beantragen** leitet Sarah zum Hypothekenantrag weiter. Der Antrag ist ein adaptives Formular, das Sie in den Authoring-Instanzen unter `https://[host]:[Port]/editor.html/content/forms/af/we-finance/hm-app.html`.

Einige der wichtigsten Funktionen, die Sie im adaptiven Formular überprüfen können, sind:

* Es basiert auf einem XSD-Schema, `homeMortgageApplication.xsd`.
* Es wird mit dem We Finance-Design B für Stile und der We.Finance-Vorlage für Layout erstellt. Außerdem verwendet es im Formularkopfzeilenlayout für die mobile Navigation Layout ohne Bereichstitel. Es zeigt ein progressives Layout für Mobilgeräte an, wenn es von einem Mobilgerät aus geöffnet wird. Sie können die Vorlage und das im adaptiven Formular verwendete Design an den folgenden Stellen in Ihrer AEM-Autoreninstanz anzeigen:

   * `https://[host]:[Port]/libs/wcm/core/content/sites/templates.html/conf/we-finance`
   * `https://[host]:[Port]/editor.html/content/dam/formsanddocuments-themes/we-finance/we-finance-theme-b/jcr:content`

* Die erste Registerkarte „Erste Schritte“ im Antrag ist ein dynamischer Hypothekenrechner, der Optionen basierend auf der Benutzerauswahl anzeigt. Zum Beispiel sind die Felder und Werte für Kauf- und Refinanzierungsoptionen unterschiedlich. Diese Funktionalität wird mithilfe von Regeln zum Ein- bzw. Ausblenden erreicht. Wenn Sie auf „Weiter“ klicken und die Registerkarte „Pläne“ initialisiert wird, ruft sie außerdem einen Web-Dienst auf, der in einem Formulardatenmodell zum Abrufen und Anzeigen von Hypothekenplänen konfiguriert ist. Sie können die Formulardatenmodelle und konfigurierten Dienste unter `https://[host]:[Port]/aem/forms.html/content/dam/formsanddocuments-fdm`.
* Es verwendet verschiedene adaptive Formularkomponenten, um Eingaben zu erfassen und sich an Benutzerreaktionen anzupassen. Es verwendet auch Komponenten wie E-Mail, die HTML5-Eingabetypen unterstützen.
* Es verwendet die Signaturschrittkomponente, um das ausgefüllte Formular anzuzeigen, und ermöglicht die elektronische Unterschrift auf dem Formular.
* Es verwendet die Aktion „AEM Workflow senden“, um den We.Finance AEM-Workflow zur Hypothek auszulösen. Sie können den in diesem Formular verwendeten Workflow unter `https://[host]:[Port]/editor.html/conf/global/settings/workflow/models/we-finance-home-mortgage-workflow.html`

Es wird empfohlen, das Formular zu lesen, um das Schema, die Komponenten, die Regeln, die Formulardatenmodelle, den Formularworkflow und die Aktion zum Erstellen des Formulars zu verstehen.

In der folgenden Dokumentation finden Sie weitere Informationen zu Funktionen, die im adaptiven Formular für Hypothekendarlehen verwendet werden:

* [Einführung in das Authoring adaptiver Formulare](/help/forms/using/introduction-forms-authoring.md)
* [Adaptive Formulare mithilfe des XML-Schemas erstellen](/help/forms/using/adaptive-form-xml-schema-form-model.md)
* [Regeleditor](/help/forms/using/rule-editor.md)
* [Designs](/help/forms/using/themes.md)
* [-Datenintegration](/help/forms/using/data-integration.md)
* [Verwenden von Adobe Sign in adaptiven Formularen ](/help/forms/using/working-with-adobe-sign.md)
* [Formularzentrierte Workflows in OSGi](/help/forms/using/aem-forms-workflow.md)

#### Sehen Sie selbst {#see-it-yourself-6}

Navigieren Sie zu `https://[server]:[port]/content/we-finance/global/en/all-forms.html` und klicken Sie auf **Jetzt anwenden** auf Hypothekenantrag. Füllen Sie die Details auf der Registerkarte „Erste Schritte“ aus, probieren Sie verschiedene Optionen aus und senden Sie den Antrag.

Stellen Sie sicher, dass Sie im Antrag eine gültige E-Mail-ID angeben, um eine Bestätigungsnachricht in Ihrem Posteingang zu empfangen.

### We.Finance erhält den Antrag {#approving_the_application-1}

We.Finance empfängt den von Sarah gesendeten Hypothekenantrag. Die Aufgabe, den Antrag zu genehmigen oder abzulehnen, wird Gloria Rios zugewiesen. Sie überprüft den Antrag und stellt fest, dass Sarahs Regierungs-ID fehlt.

![grios-inbox](assets/grios-inbox.png)

Gloria öffnet die Aufgabe und klickt auf „Weitere Informationen werden benötigt“ und gibt einen Kommentar zur fehlenden ID ab.

![need-more-info](assets/need-more-info.png)

Die Aufgabe wird nun John Doe, einem Kundenbetreuer bei We.Finance, übertragen. Er öffnet die Aufgabe und überprüft Glorias Kommentar. Er kontaktiert Sarah und bittet sie, eine Kopie ihres Ausweises zu schicken. Nachdem er eine Kopie von Sarahs ID erhalten hat, hängt er sie an die Aufgabe an und reicht den Antrag zur Neubewertung ein.

![Neubewertung](assets/reevaluation.png)

Die Aufgabe wird Gloria wieder zugewiesen. Sie überprüft die beigefügte ID und genehmigt den Antrag.

#### Funktionsweise {#how-it-works-8}

Wenn Sarah den Hypothekenantrag ausfüllt und einreicht, wird ein Formular-Workflow ausgelöst und eine Aufgabe in Glorias AEM-Posteingang erstellt. Während Gloria den Antrag prüft und weitere Informationen anfordert, wird die Aufgabe John Doe zugewiesen. Wenn John Doe die ID anfügt und den Antrag erneut absendet, wird sie Gloria zugewiesen. Dies ist in dem mit dem Hypothekenantrag verknüpften AEM-Workflow definiert.

AEM Forms on OSGi bietet formularbasierte Workflows, mit denen Sie adaptive formularbasierte Workflows erstellen können. Diese Workflows können für Überprüfungen und Genehmigungen, Geschäftsprozessabläufe, zum Starten von Dokumentdiensten, zur Integration mit Adobe Sign-Signatur-Workflows usw. verwendet werden. Weitere Informationen finden Sie unter [Formularzentrierte Workflows in OSGi](/help/forms/using/aem-forms-workflow.md).

Das folgende Bild zeigt den AEM-Workflow, der mit dem Hypothekenantrag verknüpft ist.

![mortgage-workflow-model](assets/mortgage-workflow-model.png)

#### Sehen Sie selbst {#see-it-yourself-7}

Sie können auf den AEM-Posteingang unter https://&lt;***hostname***>:&lt;***AuthorPort***>/content/we-finance/global/en/login.html?resource=/aem/inbox.html. Melden Sie sich mit dem AEM-Posteingang an. `grios/password` als Benutzername/Kennwort für Gloria Rios und `jdoe/jdoe` für John Doe verwenden und den Workflow für Hypothekenanträge durchsuchen.

Weitere Informationen zur Verwendung des AEM-Posteingangs für formularzentrierte Workflow-Aufgaben finden Sie unter [Verwalten von Formularanwendungen und Aufgaben im AEM-Posteingang](/help/forms/using/manage-applications-inbox.md).

### Sarah erhält das Begrüßungs-Kit {#sarah-receives-the-welcome-kit}

Während der von Sarah gestellte Hypothekenantrag genehmigt wird, erhält sie eine E-Mail mit einer Verknüpfung zum Begrüßungs-Kit. Sie öffnet das Willkommenspaket, das ein Karussell mit für Sarah personalisierten Werbeangeboten enthält.

![mortgage-welcome-kit](assets/mortgage-welcome-kit.png)

Das Begrüßungs-Kit ist für Sarah personalisiert und zeigt Informationen, die für sie relevant sind. Es bietet die Möglichkeit, eine PDF-Version des Begrüßungs-Kits herunterzuladen. Mit der Pfeiltaste am unteren Rand kann Sarah nach unten blättern und durch andere Abschnitte des Begrüßungs-Kits navigieren. 

#### Funktionsweise {#how-it-works-9}

Das Begrüßungs-Kit ist eine interaktive Kommunikation, die im `cq-we-finance-content-pkg.zip` Paket. Die Werbeangebote im Begrüßungs-Kit werden vom Adobe Target-Server bereitgestellt. Die angepassten Angebote sind auf bestimmte Kundensegmente ausgerichtet. Das Begrüßungs-Kit ruft von einem vorkonfigurierten Adobe Target-Server Angebote für ein Zielgruppensegment mit weiblichen Kunden ab.

Die interaktiven Karten in der Desktopversion des Begrüßgungs-Kits haben ein benutzerdefiniertes Layout, das mithilfe des Standardkartenlayouts eines Dokumentfragments erstellt wird.

#### Sehen Sie selbst {#see-it-yourself-8}

Wenn Sie beim Ausfüllen des Hypothekenantrags Ihre E-Mail-ID angegeben haben, sollten Sie eine E-Mail mit einem Link zum Willkommenspaket erhalten haben. Überprüfen Sie Ihren Posteingang und schauen Sie sich das Willkommenspaket an.

Sie können es in der AEM-Veröffentlichungsinstanz unter der folgenden URL ansehen:

`https://[host]:[port]/content/forms/af/we-finance/mortgage-loan-welcome-kit.html`

### Sarah erhält einen Kontoauszug {#sarah-receives-an-account-statement}

Als Sarah das Darlehen in Anspruch nimmt und mit der Bezahlung der Raten beginnt, erhält sie eine weitere E-Mail von We.Finance, die ihren monatlichen Kontoauszug enthält.

![mortgage-statement-email](assets/mortgage-statement-email.png)

Sarah klickt in der E-Mail auf „Kontoauszug anzeigen“, um den Hypothekenkontoauszug anzuzeigen. Der interaktive Auszug besteht aus verschiedenen Elementen:

* Auszugsübersicht
* Anweisungs-Details

Die folgende Abbildung zeigt einen anderen Teil des Kontoauszugs auf dem Desktop.

![Hypothekenkontoauszug](assets/mortgage-statement.png)

Der in einer reagiblen Tabelle angezeigte detaillierte Auszug bietet die Möglichkeit, den fälligen Betrag teilweise oder vollständig innerhalb des Auszugs zu zahlen. 

#### Funktionsweise {#how-it-works-10}

Der Hypothekenauszug ist eine interaktive Kommunikation. Es wird mithilfe des JSON-Batchprozesses generiert. Die detaillierte Ausgabentabelle im Auszug ist reagibel.

#### Sehen Sie selbst {#see-it-yourself-9}

Sie können den interaktiven Hypothekenkontoauszug unter folgender URL einsehen:

https://&lt;*hostname*>:&lt;*port*>/content/forms/af/we-finance/mortgage-account-statement.html?wcmmode=disabled

Sie können auf sie in den Autor- und Veröffentlichungsinstanzen zugreifen.

### We.Finance analysiert die Leistung des Hypothekenantrags {#we-finance-analyzes-the-performance-of-the-mortgage-application}

Von Zeit zu Zeit überprüft We.Finance die ihre Hypothekenanträge, um nach Problemen zu suchen, denen die Kunden möglicherweise ausgesetzt sind. Das Unternehmen verwendet diese Analyse, um fundierte Entscheidungen über erforderliche Änderungen an der Hypothekenanwendung zu treffen. Auf diese Weise wird die Benutzerfreundlichkeit verbessert und die Abbruchrate der Formulare reduziert, wodurch die Konversionsrate erhöht wird. Zur Analyse nutzt das Unternehmen die Integration von AEM Forms mit Adobe Analytics. Die folgende Abbildung zeigt das Analyse-Dashboard des Unternehmens.

Weitere Informationen zur Interpretation des Analyse-Dashboards finden Sie unter [Anzeigen und Verstehen von AEM Forms-Analyseberichten](/help/forms/using/view-understand-aem-forms-analytics-reports.md).

![mortgage-analytics](assets/mortgage-analytics.png)

#### Funktionsweise {#how-it-works-11}

Die Leistungsmetriken für das Hypothekenantragsformular werden mit Adobe Analytics verfolgt. Weitere Informationen zur Konfiguration von Adobe Analytics und zum Anzeigen der Berichte finden Sie unter [Konfigurieren der Analyse für Formulare und Dokumente](/help/forms/using/configure-analytics-forms-documents.md).

#### Sehen Sie selbst {#see-it-yourself-br-1}

Damit Sie den Analysebericht anzeigen und prüfen können, stellen wir Seed-Daten für die Hypothekenanwendung in der Referenz-Website bereit. Bevor Sie Seed-Daten verwenden, lesen Sie[ Konfigurieren von Analytics](/help/forms/using/setup-reference-sites.md#configureanalytics). Führen Sie folgende Schritte im Autorenmodus aus, um den Bericht mit den Seed-Daten anzuzeigen: 

1. Navigieren Sie zu **Forms und Dokumente** UI unter https://&lt;*hostname*>:&lt;*AuthorPort*>/aem/forms.html/content/dam/formsanddocuments.

1. Klicken Sie auf „Öffnen“, um den **We-Finance**-Ordner zu öffnen.
1. Auswählen **[!UICONTROL Antrag auf Hypothek]** adaptives Formular und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Analytics aktivieren]**.

1. Wählen Sie das Formular erneut aus und klicken Sie auf **[!UICONTROL Analytics-Bericht]** in der Symbolleiste, um den Bericht zu erstellen. Zunächst wird ein leerer Bericht angezeigt.

So generieren Sie einen Analysebericht mit Seed-Daten:

1. Geben Sie im Adressbrowser von CRXDE Lite Folgendes ein: `/apps/we-finance/demo-artifacts/analyticsTestData/HomeMortgageAnalyticsTestData`
1. Die Testdaten werden in der linken Seitenstruktur ausgewählt.
1. Doppelklicken Sie auf die ausgewählte Datei, um ihren Inhalt im rechten Seitenbereich zu öffnen.
1. Kopieren Sie den gesamten Inhalt der Seed-Datendatei.
1. Navigieren Sie in CRXDE zu: `/content/dam/formsanddocuments/we-finance/hm-app/jcr:content/analyticsdatanode/lastsevendays`
1. Fügen Sie im Feld analyticsdata unter Eigenschaften den kopierten Inhalt der Seed-Datendatei ein.
1. Erstellen Sie nun den Analysebericht erneut für das Antragsformular für Hypothekendarlehen. Der Bericht wird mit Seed-Daten angezeigt.

**A/B-Tests der Kreditkarteanwendung**

Zusätzlich zur Analyse und kontinuierlichen Verbesserung der Hypothekenanwendung nutzt We.Finance die Integration von AEM Forms mit Target, um A/B-Tests zu erstellen. Dadurch ist es möglich, auf verschiedene Erlebnisse im Zusammenhang mit der Bearbeitung des Antragsformulars zu reagieren und Erlebnisse zu bestimmen, die zu einer besseren Konversionsrate in Bezug auf das Ausfüllen und Übermitteln von Formularen führen. 

Informationen zum Konfigurieren von Target auf dem AEM Forms-Server finden Sie unter [Target einrichten und in AEM Forms integrieren](/help/forms/using/ab-testing-adaptive-forms.md#set%20up%20and%20integrate%20target%20in%20aem%20forms).

Führen Sie folgende Schritte im Autorenmodus aus, um A/B-Tests für das We.Finance-Hypothekenantragsformular zu erstellen:

1. Navigieren Sie zu **Forms und Dokumente** https://&lt;*hostname*>:&lt;*AuthorPort*>/aem/forms.html/content/dam/formsanddocuments.

1. Klicken Sie auf den Ordner **We.Finance**, um ihn zu öffnen.
1. Auswählen **Antrag auf Hypothek** adaptives Formular.
1. Klicken Sie in der Symbolleiste auf **Mehr** und wählen Sie **A/B-Tests konfigurieren**. Die Seite „A/B-Tests konfigurieren“ wird geöffnet.

1. Geben Sie eine **Aktivitätsbezeichnung** an.
1. Wählen Sie in der Dropdown-Liste „Zielgruppe“ die Zielgruppe, deren Reaktionen auf verschiedene Varianten des Formulars Sie testen möchten. Dies könnten beispielsweise **Besucher, die Chrome verwenden** sein.
1. Geben Sie in den Feldern für **Erlebnisverteilung** für die Erlebnisvarianten A und B deren Verteilung auf die Gesamtzielgruppe in Prozent an. Wenn Sie beispielsweise „40“ und „60“ für Erlebnis A bzw. B angeben, wird Erlebnis A für 40 % der Zielgruppe und Erlebnis B für die verbleibenden 60 % angezeigt.
1. Klicken Sie auf **Konfigurieren**. Es wird ein Dialogfeld angezeigt, in dem die Erstellung des A/B-Tests bestätigt wird.
1. Klicken Sie auf **Fertig**.
1. Wählen Sie die **Antrag auf Hypothek** adaptives Formular und klicken Sie auf **Bearbeiten**. Es bietet die Möglichkeit, eines der Erlebnisse zu öffnen. Klicken Sie auf **Erlebnis B**. Das Formular wird im Bearbeitungsmodus geöffnet. 

1. Ändern Sie beliebig das Formular, um ein anderes Erlebnis als das Standarderlebnis A zu erstellen. 
1. Wechseln Sie zur Benutzeroberfläche für Formulare und Dokumente, wählen Sie das Formular aus, klicken Sie auf **Mehr** und wählen Sie **A/B-Tests starten**.

1. Öffnen Sie jetzt das Formular mehrmals im Chrome-Browser mit der folgenden URL:

   `https://[hostname]:[port]/content/dam/formsanddocuments/we-finance/hm-app/jcr:content?wcmmode=disabled`

   >[!NOTE]
   >
   >Entfernen Sie das Cookie mit dem Namen **mbox** aus der Cookiepersistenz des Browsers, bevor Sie das Formular das nächste Mal öffnen. Sie sehen dann das Erlebnis A und B des Formulars in zufälliger Ordnung.

1. Wählen Sie das Formular aus, klicken Sie auf **Mehr**, und klicken Sie dann auf **A/B-Testbericht**. Sie werden nicht viele Daten im Bericht finden, da Sie gerade erst mit dem Testen begonnen haben. Jetzt werden wir einige Seed-Daten bereitstellen, um zu sehen, wie der A/B-Testbericht aussehen wird. 

1. Öffnen Sie CRXDE Lite und erstellen Sie eine Sicherungskopie der folgenden Datei: /libs/fd/fmaddon/gui/components/admin/targetreport/clientlibs/targetreport/js/targetreport.js
1. Ersetzen Sie die Definition der `onReportLoadSuccess` -Funktion in der oben genannten Datei mit der Funktionsdefinition in der folgenden Datei verwenden: /apps/we-finance/demo-artifacts/targetreport.js

   >[!NOTE]
   >
   >Diese Änderungen dienen nur dem Zweck der Demonstration. Stellen Sie unbedingt den Dateiinhalt wieder her, nachdem Sie dieses Verfahren abgeschlossen haben. 

1. Aktualisieren Sie den von Ihnen erstellten Bericht. Dann sehen Sie Folgendes. Prüfen Sie das Berichts-Dashboard. 

![ab-test-report-4](assets/ab-test-report-4.png)

Um den A/B-Test zu beenden, klicken Sie im Berichts-Dashboard auf die Schaltfläche **A/B-Test beenden**. An diesem Punkt Sie aufgefordert, ein Erlebnis anzugeben. Wählen Sie einen Gewinner und bestätigen Sie, dass Sie den A/B-Test beenden möchten.
 

Wenn Sie Erlebnis A als Gewinner auswählen, wird der A/B-Test beendet, und in Zukunft wird nur Erlebnis A für sämtliche Zielgruppen (einschließlich Chrome-Benutzer) angezeigt.

## Hypothekenantrag - Anleitung mit Microsoft Dynamics {#home-mortgage-application-walkthrough-with-microsoft-dynamics}

Die Hypothek von We.Finance mit Microsoft Dynamics umfasst die folgenden Personen:

* Sarah Rose, einen We.Finance-Kunden
* Den Administrator der We.Finance Microsoft Dynamics-Instanz

Die Anleitung zur Antragstellung für Hypothekendarlehen mit Microsoft Dynamics zeigt, wie ein We.Finance-Kunde die Website verwenden kann, um eine Hypothek zu beantragen, wenn die Referenz-Website Microsoft Dynamics für die Datenintegration verwendet. Die Anleitung endet mit den Daten, die vom Benutzer ausgefüllt wurden und von Microsoft Dynamics empfangen wurden. Bevor Sie mit diesem Szenario fortfahren, müssen Sie die [Microsoft Dynamics 365-Konfiguration für den Hypotheken-Workflow der We.Finance-Referenz-Website](/help/forms/using/ms-dynamics-configuration-home-mortgage.md).

### Sarah besucht die Website von We.Finance und beantragt eine Hypothek {#sarah-visits-we-finance-website-and-applies-for-home-mortgage-1}

Sarah Rose plant, ein Haus zu kaufen und nach einem Hypotheksplan zu suchen. Sie ist eine We.Finance-Kundin und besucht daher das We.Finance-Portal, um Hypothekenangebote zu erkunden. Sie geht in den Bereich „Kredite“ und findet einen Hypothekenrechner auf dem Portal. Sie füllt die Details aus und klickt auf „Meine Hypothek berechnen“, die einen Hypothekenplan zurückgibt.

![Kredite1](assets/loans1.png) ![Kredite2](assets/loans2.png)
**Abbildung:** *Hypothekenrechner*

![Kredite3](assets/loans3.png)
**Abbildung:** *Ergebnis des Hypothekenrechners*

#### Funktionsweise {#how-it-works-12}

Der Hypothekenrechner auf der Seite „Darlehen“ ist ein eingebettetes adaptives Formular in der AEM-Seite. Sie können die Seite Darlehen im Bearbeitungsmodus unter `https://[authorHost]:[authorPort]/editor.html/content/we-finance/global/en/loan-landing-page.html`.

Der eingebettete Hypothekenrechner, bei dem es sich um ein adaptives Formular handelt, verwendet Regeln zur Berechnung des EMI-Betrags basierend auf den Kreditdetails, die in den Rechnerfeldern angegeben sind. Sie können das adaptive Formular unter `https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/ms-dynamics/home-mortgage-calculator.html` überprüfen.

#### Sehen Sie selbst {#see-it-yourself-10}

Gehen Sie zum We.Finance-Portal unter `https://<publishHost>:<publishPort>/content/we-finance/global/en.html` und klicken Sie auf **[!UICONTROL Darlehen]**. Geben Sie Details in den Hypothekenrechner ein und sehen Sie sich die Ergebnisse an.

### Sarah findet das Angebot interessant und beschließt, einen Antrag zu stellen  {#sarah-finds-the-offer-interesting-and-chooses-to-apply-2}

Sarah beschließt, einen Antrag auf Hypothek und Klicks zu stellen **[!UICONTROL Jetzt anwenden]** auf Hypothekenrechner. Es wird der Antrag für Hypotheken geöffnet.

Wenn Sarah von ihrem Mobilgerät aus auf den Antrag für die Hypothek zugreift, wird das Antragsformular in einer Ansicht geöffnet, die für die Anzeige auf einem mobilen Gerät optimiert ist. In dieser Ansicht zeigt das Antragsformular jeweils einen Abschnitt an. Es ermöglicht Sarah, Informationen progressiv zu sehen und zu liefern, während sie durch das Antragsformular navigiert.

Die folgenden Bilder zeigen den Arbeitsablauf, während Sarah auf ihrem Mobilgerät durch die Hypothekenanwendung navigiert.

![Ausfüllen des Hypothekenantrags auf einem Mobilgerät](assets/mortgage-form-on-mobile.png)

Wenn Sarah von ihrem Desktop aus auf **Jetzt beantragen** klickt, öffnet sich das Antragsformular für Hypotheken wie folgt. Die Informationen, die Sarah im Hypothekenrechner zur Verfügung stellt, sind im Antragsformular vorgefüllt. Sarah füllt die restlichen Details aus und klickt auf **Weiter**.

![Hypothekenanwendung](assets/mortgage-application.png)

Basierend auf den Informationen, die Sarah in den Hypothekenrechner eingegeben hat, werden ihr einige Hypothekenpläne vorgelegt. Sie wählt den Plan, der ihren Anforderungen entspricht, und füllt weiterhin den Antrag aus. Sie unterschreibt und reicht den Antrag ein.

Der eingereichte Antrag geht an We.Finance zur Genehmigung.

![Speichern eines Antragsentwurfs](assets/mortgage-plans.png)

#### Funktionsweise {#how-it-works-13}

Die Schaltfläche **Jetzt beantragen** leitet Sarah zum Hypothekenantrag weiter. Der Antrag ist ein adaptives Formular, das Sie in den Authoring-Instanzen unter `https://[host]:[Port]/editor.html/content/forms/af/we-finance/ms-dynamics/application-for-home-mortgage.html`.

Einige der wichtigsten Funktionen, die Sie im adaptiven Formular überprüfen können, sind:

* Es basiert auf einem XSD-Schema, `homeMortgageApplication.xsd`.
* Es wird mit dem We Finance-Design B für Stile und der We.Finance-Vorlage für Layout erstellt. Außerdem verwendet es im Formularkopfzeilenlayout für die mobile Navigation Layout ohne Bereichstitel. Es zeigt ein progressives Layout für Mobilgeräte an, wenn es von einem Mobilgerät aus geöffnet wird. Sie können die Vorlage und das im adaptiven Formular verwendete Design an den folgenden Stellen in Ihrer AEM-Autoreninstanz anzeigen:

   * `https://[host]:[Port]/libs/wcm/core/content/sites/templates.html/conf/we-finance`
   * `https://[host]:[Port]/editor.html/content/dam/formsanddocuments-themes/we-finance/we-finance-theme-b/jcr:content`

* Die erste Registerkarte „Erste Schritte“ im Antrag ist ein dynamischer Hypothekenrechner, der Optionen basierend auf der Benutzerauswahl anzeigt. Zum Beispiel sind die Felder und Werte für Kauf- und Refinanzierungsoptionen unterschiedlich. Diese Funktionalität wird mithilfe von Regeln zum Ein- bzw. Ausblenden erreicht. Wenn Sie auf „Weiter“ klicken und die Registerkarte „Pläne“ initialisiert wird, ruft sie außerdem einen Web-Dienst auf, der in einem Formulardatenmodell zum Abrufen und Anzeigen von Hypothekenplänen konfiguriert ist. Sie können die Formulardatenmodelle und konfigurierten Dienste unter `https://[host]:[Port]/aem/forms.html/content/dam/formsanddocuments-fdm`.
* Es verwendet verschiedene adaptive Formularkomponenten, um Eingaben zu erfassen und sich an Benutzerreaktionen anzupassen. Es verwendet auch Komponenten wie E-Mail, die HTML5-Eingabetypen unterstützen.
* Es verwendet die Signaturschrittkomponente, um das ausgefüllte Formular anzuzeigen, und ermöglicht die elektronische Unterschrift auf dem Formular.

Es wird empfohlen, das Formular zu lesen, um das Schema, die Komponenten, die Regeln, die Formulardatenmodelle, den Formularworkflow und die Aktion zum Erstellen des Formulars zu verstehen.

### Der Administrator zeigt die übermittelten Daten in der Microsoft Dynamics-Instanz an {#the-administrator-views-the-submitted-data-in-the-microsoft-dynamics-instance}

We.Finance erhält den von Sarah gestellten Hypothekenantrag auf der Microsoft Dynamics-Instanz. Der Administrator tippt auf den Eintrag in der Hauptspalte, um zu dem für Sarah Rose erstellten Führungsdatensatz zu gelangen.

![msdynamicsrecord](assets/msdynamicsrecord.png)

## Antrag auf Hypothek - Anleitung {#home-insurance-application-walkthrough}

Im We.Finance-Hausversicherungsszenario kommen die folgenden Personen vor:

* Sarah Rose, einen We.Finance-Kunden
* Gloria Rios, Direktor von Kreditkarten und Hypotheken bei We.Finance
* Frank De Costa, Versicherungsagent, We.Finance

Die folgende Infografik zeigt eine Schritt-für-Schritt-Anleitung für einen Antrag auf eine Hausversicherung.

![workflow_insurance](assets/workflow_insurance.png)

Schauen wir uns nun an, wie die Schritte des Referenz-Website-Szenarios im Einzelnen aussehen, um Aufschluss zu erhalten, wie AEM Forms dem Unternehmen We.Finance hilft, das Ziel zu erreichen. 

### Sarah erhält einen Newsletter von We.Finance und beantragt eine Hausversicherung  {#sarah-receives-a-newsletter-from-we-finance-and-applies-for-home-insurance}

Sarah Rose ist eine Haushypothekenkundin von We.Finance und auf der Suche nach einem guten Angebot für eine Hausversicherung. Sie besucht das We.Finance-Portal und sucht nach Hausversicherungsplänen. We.Finance identifizierte sie als bestehende Kundin und schickt ihr einen gezielten Newsletter per E-Mail. Der Newsletter enthält Hausversicherungen.

![insurance-newsletter](assets/insurance-newsletter.png)

#### Funktionsweise {#how-it-works-14}

Der an Sarah gesendete Newsletter ist eine benutzerdefinierte Implementierung, die eine E-Mail an die angegebene E-Mail-ID auslöst. Die Schaltfläche „Jetzt beantragen“ im Newsletter ist mit dem Hausversicherungsantrag verknüpft, bei dem es sich um ein adaptives Formular für eine Veröffentlichungsinstanz handelt.

#### Sehen Sie selbst {#see-it-yourself-11}

Öffnen Sie die folgende URL, um eine Newsletter-E-Mail auszulösen. Stellen Sie sicher, dass Sie `[emailID]` mit einem gültigen E-Mail-Konto, um den Newsletter zu erhalten. Öffnen Sie den Newsletter und klicken Sie auf **[!UICONTROL Jetzt anwenden]** , um zur Hausversicherungsanwendung zu wechseln.

`https://[authorServer]:[authorPort]/content/campaigns/we-finance/start.html?app=ins&email=[emailID]&givenName=Sarah&familyName=Rose`

### Sarah findet das Angebot interessant und beschließt, einen Antrag auf eine Hausversicherung zu stellen  {#sarah-finds-the-home-insurance-offer-interesting-and-chooses-to-apply}

Sarah mag die Hausversicherung im Newsletter und beschließt, einen Antrag zu stellen. Sie klickt auf „Jetzt beantragen“ im Newsletter, der den Hausversicherungsantrag auf dem We.Finance-Portal öffnet.  Das Antragsformular besteht aus verschiedenen Abschnitten, wie beispielsweise dem Kartenlayout.

Auf der Seite „Persönliche Daten“ erhält Sarah, da sie ihre Sozialversicherungsnummer angibt, eine Aufforderung, sich mit ihren Zugangsdaten anzumelden.

![insurance-ssn](assets/insurance-ssn.png)

Sarah ist bereits eine We.Finance-Kundin. Sie meldet sich mit ihren We.Finance-Kontoanmeldeinformationen an und ihre persönlichen Daten werden im Formular automatisch ausgefüllt. Sie füllt den Antrag weiterhin aus und reicht ihn ein.

Wenn Sarah den Antrag auf einem mobilen Gerät eingereicht hat, sieht sie die folgenden Bildschirme.

![insurance-form-on-mobile](assets/insurance-form-on-mobile.png)

#### Funktionsweise {#how-it-works-15}

Über die Schaltfläche **Jetzt beantragen“ im Newsletter wird Sarah zum Hausversicherungsantrag auf dem We.Finance-Portal weitergeleitet.** Der Antrag ist ein adaptives Formular, das Sie in der Authoring-Instanz unter `https://[host]:[Port]/editor.html/content/forms/af/we-finance/insurance/application-for-insurance.html`.

Einige der wichtigsten Funktionen, die Sie im adaptiven Formular überprüfen können, sind:

* Es basiert auf einem XSD-Schema, `insurance.xsd`.
* Er wird unter Verwendung von „Versicherung“ für das Design erstellt und verwendet Layout ohne Bereichstitel im Formularüberschriften-Layout für die mobile Navigation. Es zeigt ein progressives Layout für Mobilgeräte an, wenn es von einem Mobilgerät aus geöffnet wird. Sie können die Vorlage unter `https://[host]:[Port]/libs/wcm/core/content/sites/templates.html/conf/we-finance` und das Thema unter `https://[host]:[Port]/editor.html/content/dam/formsanddocuments-themes/we-finance/insurance/jcr:content`.

* Es enthält adaptive Formularregeln zum Aufrufen von Formulardatenmodelldiensten, um Benutzerdetails des angemeldeten Benutzers vorab zu befüllen. Es ruft auch Dienste auf, um Informationen anhand der im Formular angegebenen Sozialversicherungsnummer oder E-Mail-Adresse vorab zu befüllen. Sie können die Formulardatenmodelle und ihre Dienste unter `https://[host]:[Port]/aem/forms.html/content/dam/formsanddocuments-fdm`.
* Es verwendet verschiedene adaptive Formularkomponenten, um Eingaben zu erfassen und sich an Benutzerreaktionen anzupassen. Es verwendet auch Komponenten wie E-Mail, die HTML5-Eingabetypen unterstützen.
* Die Schaltfläche „Fortschritt speichern“ generiert eine eindeutige ID für den Benutzer und speichert die teilweise ausgefüllte Anwendung als Entwurf in einem Knoten im AEM-Repository. Außerdem wird ein Dialogfeld mit einer Bitte um Bestätigung angezeigt, damit eine E-Mail mit einer Verknüpfung zu dem Knoten gesendet werden kann, der den Antragsentwurf enthält. Über die im Bestätigungsdialogfeld angezeigte Schaltfläche E-Mail senden wird die Versendung einer E-Mail mit einer Verknüpfung zu dem Knoten ausgelöst, der den Entwurf enthält.
* Es verwendet die Aktion „AEM-Workflow aufrufen“, um den Hausversicherungs-Genehmigungs-Workflow auszulösen. Sie können den in diesem Formular verwendeten Workflow unter `https://[host]:[Port]/editor.html/conf/global/settings/workflow/models/we-finance-insurance-workflow.html`

Es wird empfohlen, das Formular zu lesen, um das Schema, die Komponenten, die Regeln, die Formulardatenmodelle, den Formularworkflow und die Aktion zum Erstellen des Formulars zu verstehen.

In der folgenden Dokumentation finden Sie weitere Informationen zu Funktionen, die im adaptiven Formular für den Antrag auf Hausversicherungen verwendet werden:

* [Einführung in das Authoring adaptiver Formulare](/help/forms/using/introduction-forms-authoring.md)
* [Adaptive Formulare mithilfe des XML-Schemas erstellen](/help/forms/using/adaptive-form-xml-schema-form-model.md)
* [Regeleditor](/help/forms/using/rule-editor.md)
* [Designs](/help/forms/using/themes.md)
* [-Datenintegration](/help/forms/using/data-integration.md)
* [Verwenden von Adobe Sign in adaptiven Formularen ](/help/forms/using/working-with-adobe-sign.md)
* [Formularzentrierte Workflows in OSGi](/help/forms/using/aem-forms-workflow.md)

#### Sehen Sie selbst {#see-it-yourself-12}

Klicken Sie auf die Schaltfläche **Jetzt beantragen** im Newsletter, den Sie in Ihrer E-Mail erhalten haben. Alternativ können Sie zu `https://[publishHost]:[publishPort]/content/we-finance/global/en/all-forms.html` und klicken Sie auf **[!UICONTROL Anwenden]** über den Versicherungsantrag. Geben Sie`123456789`   im Feld „Sozialversicherungsnummer“ ein. Wenn Sie dazu aufgefordert werden, melden Sie sich mit `srose/srose` als Benutzername/Passwort an.

Füllen Sie Details aus, untersuchen Sie verschiedene adaptive Formularkomponenten und senden Sie den Antrag. Sie können das adaptive Formular unter `https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/insurance/application-for-insurance.html` überprüfen.

### We.Finance genehmigt den Antrag und ein Vertrag wird unterschrieben {#we-finance-approves-the-application-and-a-contract-is-signed}

We.Finance erhält den von Sarah gestellten Antrag auf Hausversicherung. Eine Aufgabe wird Gloria Rios zugewiesen. Sie überprüft den Antrag in ihrem AEM-Posteingang und genehmigt ihn.

![insurance-inbox-grios](assets/insurance-inbox-grios.png)

Wenn Gloria Sarahs Hausversicherungsantrag genehmigt, wird eine Aufgabe im AEM-Posteingang von Frank De Costa erstellt. Frank überprüft die Aufgabe. Er bereitet einen Hausversicherungsvertrag für Sarah vor, hängt den Vertrag an ihren Antrag und sendet ihn an Sarah, um den Vertrag zu unterzeichnen. Der Vertrag, der unten in der Benutzeroberfläche für Agenten angezeigt wird, ist die Druckversion der interaktiven Kommunikation.

![insurance-contact-letter](assets/insurance-contact-letter.png)

Sarah erhält eine E-Mail mit einem Link zum Vertrag mit der Hausversicherung zur Unterzeichnung. Sarah prüft und unterzeichnet den Vertrag.

![insurance-contract-email](assets/insurance-contract-email.png)

#### Funktionsweise {#how-it-works-16}

Wenn Sarah den Hausversicherungsantrag einreicht, wird ein Formular-Workflow ausgelöst und eine Aufgabe in Glorias AEM-Posteingang erstellt. Wenn Gloria den Antrag prüft und genehmigt, wird die Aufgabe Frank De Costa zugewiesen. Der Aufgabenfluss von einer Person zur anderen wird im AEM Workflow definiert, der mit dem Versicherungsantrag verknüpft ist. Weitere Informationen zu Workflows finden Sie unter [Forms-orientierter Workflow auf OSGi](/help/forms/using/aem-forms-workflow.md).

Das folgende Bild zeigt den AEM-Workflow, der mit dem Hausversicherungsantrag verknüpft ist.

![we-finance-insurance-workflow-model](assets/we-finance-insurance-workflow-model.png)

Frank verwendet das Correspondence Management, um einen Vertrag für eine Hausversicherung zu erstellen. Er lädt das Vertrags-PDF herunter und hängt es an die Anwendung von Sarah an und klickt auf „Vertrag senden“. Der Workflow löst eine E-Mail an Sarah aus, die den Vertrag mit der Hausversicherung zum Unterzeichnen unterzeichnet.

#### Sehen Sie selbst {#see-it-yourself-13}

Gehen Sie folgendermaßen vor:

1. Wechseln Sie zum AEM Posteingang, `https://[publishHost]:[publishPort]/content/we-finance/global/en/login.html?resource=/aem/inbox.html`und melden Sie sich mit `grios/grios` als Benutzername Kennwort für Glorias Person. Genehmigen Sie die Aufgabe für Sarahs Hausversicherungsantrag.

1. Melden Sie sich dann beim AEM-Posteingang mit `fdcosta/password` als Benutzername für Franks Person an. Sehen Sie sich die Aufgabe an.
1. Gehen Sie jetzt zu `https://[authorHost]:[authorPort]/aem/forms.html/content/dam/formsanddocuments/we-finance/insurance` und zeigen Sie eine Vorschau der Briefvorlage für HomeInsuranceWelcomeKit an.
1. Geben Sie Informationen im Datenbereich an. Klicken Sie auf **[!UICONTROL Vorschau]** und laden Sie dann die PDF-Datei auf Ihr lokales Dateisystem herunter. Stellen Sie sicher, dass die PDF-Datei mit dem Dateinamen „contract.pdf“ gespeichert wird.
1. Gehen Sie zu Franks AEM-Posteingang, öffnen Sie die Aufgabe, hängen Sie die heruntergeladene Vertrags-PDF an und klicken Sie auf **[!UICONTROL Vertrag senden]**.
1. Öffnen Sie die E-Mail mit Vertrag und unterschreiben Sie das Dokument.

### Sarah erhält ein Willkommenspaket {#sarah-receives-a-welcome-kit}

Als Sarah den Hausversicherungsvertrag unterschreibt, erhält sie eine E-Mail mit den Versicherungsbedingungen.

![insurance-policy-details](assets/insurance-policy-details.png)

Dann erhält sie eine weitere E-Mail von We.Finance mit einem Willkommenspaket für ihre Versicherungspolice. Mit dem Willkommenspaket kann Sarah auf ihre Richtliniendokumente zugreifen und Auszüge anzeigen.

![insurance-welcome-kit](assets/insurance-welcome-kit.png)

#### Sehen Sie selbst {#see-it-yourself-14}

Wenn Sie Ihre E-Mail-ID im Antrag angegeben haben, haben Sie eine E-Mail mit einem Link zum Willkommenspaket erhalten. Klicken Sie auf „Mein Willkommenspaket“, um das Willkommenspaket zu öffnen.****

![insurance-welcome-kit-email](assets/insurance-welcome-kit-email.png)

## Prospekt für Vermögensverwaltung - Anleitung {#wealth-management-prospectus-walkthrough}

Das We.Finance-Szenario &quot;Vermögensverwaltung&quot;umfasst die folgenden Personen:

* Sarah Rose, einen We.Finance-Kunden

Die Anleitung zur Vermögensverwaltung zeigt, wie ein We.Finance-Kunde die Website nutzen kann, um mehr über einen Fonds auf Gegenseitigkeit, den Blue Chip Growth Fund, zu erfahren. Die Referenz-Website verwendet eine interaktive Kommunikation, um Informationen über den Fonds anzuzeigen. Die Informationen sind sowohl im Web- als auch im PDF-Format verfügbar. Die exemplarische Vorgehensweise endet mit einer E-Mail-Versendung der PDF-Version der Informationen an ihren Bruder.

Die folgende Abbildung zeigt den Workflow der exemplarischen Vorgehensweise zur Vermögensverwaltung:

![Vermögen-Management-Prospekt-Walkthrough](assets/wealth-management-prospectus-walkthrough.png)

### Sarah besucht die We.Finance-Website und eröffnet den Prospekt des Blue Chip Growth Fund {#sarah-visits-we-finance-website-and-opens-the-blue-chip-growth-fund-prospectus}

Sarah Rose plant, in einen Fonds auf Gegenseitigkeit zu investieren. Sie ist eine bestehende We.Finance-Kundin und besucht daher das We.Finance-Portal, um verfügbare Investmentfonds zu erkunden. Sie öffnet im Bereich Vermögensverwaltung die Seite We.Finance Blue Chip Growth Fund . Die Seite enthält Links zum Prospekt, der Details zu aktuellen und historischen Preisen, monatlicher Performance, sektorspezifischer Diversifizierung, Ausgaben, Gebühren, Steuern und weiteren Informationen über die Fonds enthält.

![Folie1](assets/slide1.png)

#### Funktionsweise {#how-it-works-17}

Der Prospekt des Blue Chip Growth Fund ist eine interaktive Kommunikation. Es verwendet Texte, Bilder, Diagramme und Tabellenkomponenten (Dokumentfragmente), um Produktzusammenfassung, Aktienstil, Fondsleistung, Fondsdetails und andere zugehörige Informationen anzuzeigen. Sie können die interaktive Kommunikation im Bearbeitungsmodus unter https:// überprüfen.[authorHost]:[ authorPort]/editor.html/content/forms/af/we-finance/wealth-management/wealth-management/channels/web.html

Die Diagramme und Tabellen rufen Daten aus einem Formulardatenmodell ab. Das Formulardatenmodell stellt eine Verbindung zu konfigurierten Datenquellen her, einer Datenbank in dieser exemplarischen Vorgehensweise, um fondsspezifische Informationen abzurufen. Sie können das Formulardatenmodell unter https:// überprüfen.[authorHost]:[authorPort]/aem/fdm/editor.html/content/dam/formsanddocuments-fdm/we-finance/wealth-management

#### Sehen Sie selbst  {#see-it-yourself-15}

Gehen Sie zum We.Finance-Portal unter https://[publishHost]:[publishPort]/wefinance, tippen Sie auf Vermögensverwaltung, erweitern Sie Fonds nach Asset-Klasse und tippen Sie auf We.Finance Blue Chip Growth Fund. Der Prospekt des We.Finance Blue Chip Growth Fund wird eröffnet.

### Sarah untersucht den Prospekt des Blue Chip Growth Fund, um mehr über den Fonds zu erfahren {#sarah-explores-the-blue-chip-growth-fund-prospectus-to-learn-about-the-fund}

Sarah untersucht die Tabs Übersicht, Preis &amp; Leistung, Portfolio-Management, Gebühr &amp; Minimum sowie Steuern und Zahlungen des Prospekts, um aktuelle und historische Preise, historische Zuwächse, Vergleich mit S&amp;P 500-Index, sektorbezogene Diversifizierung, Fondsverwalter und Ausgaben im Zusammenhang mit dem Fonds zu erlernen. Die zugehörigen Informationen sind in verschiedene Tabs unterteilt. Der Prospekt ist eine interaktive Kommunikation. Die interaktive Kommunikation hat ein responsives Design. Sie kann die interaktive Kommunikation auf einem Gerät beliebiger Bildschirmgröße öffnen und die interaktive Kommunikation lässt das Design an das zugrunde liegende Gerät anpassen.

![slide1-1](assets/slide1-1.png)

#### Funktionsweise {#how-it-works-18}

Die interaktive Kommunikation des Blue Chip Growth Fund nutzt Eltern- und untergeordnete Bedienfelder, um verwandte Informationen in verschiedene Abschnitte zu unterteilen. Das übergeordnete Bedienfeld organisiert alle untergeordneten Bedienfelder in Registerkarten.

Das Layout der übergeordneten Registerkarte ist auf &quot;Registerkarten oben&quot;festgelegt, um alle untergeordneten Bedienfelder in Registerkarten zu konvertieren. Sie können die Bedienfelder der interaktiven Kommunikation im Bearbeitungsmodus unter https:// überprüfen.[authorHost]:[ authorPort]/editor.html/content/forms/af/we-finance/wealth-management/wealth-management/channels/web.html

#### Sehen Sie selbst  {#see-it-yourself-16}

Wechseln Sie zur interaktiven Kommunikation des Blue Chip Growth Fund unter https://[publishHost]:[ publishPort]/content/forms/af/we-finance/wealth-management/wealth-management/channels/web.html?wcmmode=disabled. Durchsuchen Sie alle Registerkarten.

### Sarah sieht sich die PDF-Version der Blue Chip Growth Fund-Seite an und sendet sie per E-Mail. {#sarah-views-and-emails-the-pdf-version-of-the-blue-chip-growth-fund-page}

Sarah reist am Wochenende auf das Land. Sie will mit ihrem älteren Bruder über den Blue Chip Growth Fund sprechen. Ihr älterer Bruder arbeitet mit einer Bank und hilft ihr bei Entscheidungen im Zusammenhang mit der Finanzierung. Sarah lädt auf ihrem Laptop eine Kopie der PDF-Version der Blue Chip Growth Fund-Seite herunter, um sie offline zu lesen. Sie sendet ihrem Bruder auch eine Kopie der PDF-Version per E-Mail.

![blue-chip-pdf](assets/blue-chip-pdf.gif)

#### Funktionsweise {#how-it-works-19}

Der Prospekt des Blue Chip Growth Fund ist eine interaktive Kommunikation. Es verfügt über einen Web- und PDF-Kanal. Die interaktive Kommunikation ist mit AEM Workflows integriert, um die PDF-Version über eine E-Mail zu senden. Sie können das Workflow-Modell unter https:// überprüfen.[authorHost]:[ authorPort]/editor.html/conf/global/settings/workflow/models/wealthmanagement.html

![Vermögensverwaltung](assets/wealth-management.png)

#### Sehen Sie selbst  {#see-it-yourself-17}

Um die PDF-Version herunterzuladen, gehen Sie zur interaktiven Kommunikation des Blue Chip Growth Fund https://[publishHost]:[ publishPort]/content/forms/af/we-finance/wealth-management/wealth-management/channels/web.html, tippen Sie auf PDF herunterladen.

Um PDF per E-Mail zu senden, gehen Sie zur interaktiven Kommunikation des Blue Chip Growth Fund https://[publishHost]:[ publishPort]/content/forms/af/we-finance/wealth-management/wealth-management/channels/web.html, tippen Sie auf E-MAIL-PDF. Angeben **Vollständiger Name** und **Email-Adresse**. Klicken **E-Mail senden**.

## Anleitung zur Anwendung für automatische Versicherung {#auto-insurance-application-walkthrough}

Das Szenario der automatischen We.Finance-Versicherungsanwendung umfasst die folgende Person:

* Sarah Rose, einen We.Finance-Kunden
* Conrad Simms, Insurance Agent, We.Finance

Sarah Rose ist bereits We.Finance-Kundin und hat eine Kfz-Versicherungspolice erworben. Jetzt wird es Zeit für die Erneuerung ihrer Versicherungspolice. Conrad Simms, Insurance Agent, We.Finance sendet eine Erinnerung an Sarah über die Verlängerung ihrer Police. Die E-Mail zur Erinnerung enthält eine PDF mit Details zur Verlängerung der Richtlinie und einen Link zur Webversion der interaktiven Kommunikation. Die interaktive Kommunikation hat ein benutzerfreundliches und reaktionsfähiges Design für Mobilgeräte. Sie kann die interaktive Kommunikation auf jedem Gerät öffnen und die interaktive Kommunikation wird entsprechend der Bildschirmgröße des zugrunde liegenden Geräts angezeigt. Die an E-Mails angehängte PDF-Version der interaktiven Kommunikation ist für die Offline-Lesbarkeit hilfreich.

Sarah folgt den Anweisungen in der E-Mail und erneuert den Prozess erfolgreich. Die folgende Abbildung zeigt den Workflow der exemplarischen Vorgehensweise für die automatische Versicherungsanwendung:  ![auto-insurance-application-walkthrough](assets/auto-insurance-application-walkthrough.png)

### Conrad sendet eine Mitteilung zur Erneuerung einer Versicherungspolice von We.Finance {#conrad-sends-an-insurance-policy-renewal-communication-from-we-finance}

Conrad meldet sich in AEM Instanz an, öffnet das Kfz-Versicherungsdashboard, um Sarahs **Kunden-ID**, und Klicks **Richtlinie erneuern**. Die **Benutzeroberfläche des Agenten** wird mit Richtliniendetails von Sarah Rose geöffnet, die bereits ausgefüllt sind. Konkrete E-Mail-Adresse von Sarah und Klicks **Einsenden**. Sarah erhält eine E-Mail mit dem Betreff **Ihre Erneuerung der Kfz-Versicherung**.

![cc-dashboard](assets/cc-dashboard.png)

#### Funktionsweise {#how-it-works-20}

Die Mitteilung zur Erneuerung der Versicherungspolice ist eine interaktive Mitteilung. Conrad Simms verwendet die Benutzeroberfläche für Agenten, um die Mitteilung zur Erneuerung der Versicherungspolice an Sarah zu senden. Die Kommunikation umfasst Druck (PDF) und eine Verknüpfung zum Webkanal der interaktiven Kommunikation. Die interaktive Kommunikation verwendet AEM Workflow zum Senden der E-Mail. Sie können den Workflow unter https:// sehen.[authorHost]:[ authorPort]/editor.html/conf/global/settings/workflow/models/we-finance-auto-insurance-renewal.html

![auto-insurance-workflow](assets/auto-insurance-workflow.png)

#### Sehen Sie selbst  {#see-it-yourself-18}

Anmelden bei **We.Finance Auto Insurance Dashboard** als Conrad Simms (csimms/password). Die URL lautet https://[publishhost]:[publishport]/content/we-finance/global/en/login.html?resource=/content/we-finance/ccdashboard.html. Geben Sie die **Kunden-ID**. Kunden-ID von Sarah Rose ist 900001. Klicken **Richtlinie erneuern**. Die interaktive Kommunikation wird in der Agent UI geöffnet. Geben Sie in der Benutzeroberfläche für Agenten eine gültige E-Mail-Adresse ein, an die die E-Mail mit dem angehängten Richtliniendokument gesendet werden soll, und klicken Sie auf **Einsenden**. Eine Nachricht (&quot;Sendung initiiert&quot;) wird auf dem Bildschirm angezeigt und in wenigen Sekunden wird eine weitere Nachricht (&quot;Gesendet erfolgreich gesendet&quot;) angezeigt. Eine E-Mail mit dem Betreff **Ihre Erneuerung der Kfz-Versicherung** und wird an die angegebene E-Mail-Adresse gesendet. Die Sarah Rose angebotene Richtlinie ist eine Premium-Richtlinie.

Die Anleitung zur Kfz-Versicherung enthält auch einen anderen Kunden, Alison Jones. Die Kunden-ID von Alison Jones lautet 900002. Wenn Sie die interaktive Kommunikation an Alison Jones senden, wird eine Standardrichtlinie gesendet. Der Unterschied zwischen Standard- und Premium-Politik besteht darin,

* Die Premium-Richtlinie hat ein Bannerbild und die Standardrichtlinie enthält nur Text unter dem Adressblock.
* Die Standardpolitik kostet weniger als die Prämienpolitik.
* Die Prämienpolitik ist gegen Diebstahl und die Standardpolitik hat intelligente Belohnung

Beide Richtlinien verwenden dieselbe interaktive Kommunikation. Die Abschnitte in der Richtlinie werden basierend auf der Bedingung des Richtlinientyps geändert oder ausgeblendet. Sie können die interaktive Kommunikation zur Erneuerung der automatischen Versicherungsverlängerung direkt über `https://[authorHost]: [authorPort]/aem/formdetails.html/content/dam/formsanddocuments/we-finance/autoinsurance/auto-insurance-renewal`

**Verwenden von Microsoft Dynamics als Datenquelle**

Die Referenz-Website bietet außerdem eine interaktive Kommunikation, die Microsoft Dynamics als Datenquelle für das Formulardatenmodell verwendet. Führen Sie die folgenden Schritte aus, um die interaktive Kommunikation für die Anleitung zur automatischen Versicherung zu konfigurieren:

1. Melden Sie sich bei https:// an[author]:[port]/crx/de als Administrator.
1. Öffnen Sie die `/apps/we-finance/components/ccrui/ccrui.jsp`-Datei.
1. Legen Sie den Wert von `FormFieldRequestParameter`nach `/content/dam/formsanddocuments/we-finance/autoinsurance/auto-insurance-renewal-dynamics`
1. Tippen Sie auf **Alle speichern**. Die Referenz-Website ist für die Verwendung der interaktiven Kommunikation konfiguriert, die MS Dynamics als Datenquelle verwendet.

Melden Sie sich jetzt bei an. **We.Finance Auto Insurance Dashboard** als Conrad Simms (csimms/password). Die URL lautet https://[publishhost]:[publishport]/content/we-finance/global/en/login.html?resource=/content/we-finance/ccdashboard.html. Geben Sie die **Kunden-ID**. Kunden-ID von Sarah Rose ist 900001. Klicken **Richtlinie erneuern**. Die interaktive Kommunikation wird in der Agent UI geöffnet. Geben Sie in der Benutzeroberfläche für Agenten eine gültige E-Mail-Adresse ein, an die die E-Mail mit dem angehängten Richtliniendokument gesendet werden soll, und klicken Sie auf **Einsenden**. Eine Nachricht (&quot;Sendung initiiert&quot;) wird auf dem Bildschirm angezeigt und in wenigen Sekunden wird eine weitere Nachricht (&quot;Gesendet erfolgreich gesendet&quot;) angezeigt. Eine E-Mail mit dem Betreff **Ihre Erneuerung der Kfz-Versicherung** an die angegebene E-Mail-Adresse gesendet.

>[!NOTE]
>
>Wenn Sie die interaktive Kommunikation verwenden, die Microsoft Dynamics als Datenquelle verwendet, verweisen die Links in den an Sarah gesendeten E-Mails auf interaktive Kommunikation, die nicht Microsoft Dynamics verwendet. Um das Problem zu beheben, ändern Sie manuell die Links in E-Mail-Vorlagen.

![agent_ui_email-1](assets/agent_ui_email-1.png)

### Sarah erhält von We.Finance eine Mitteilung zur Erneuerung der Kfz-Versicherung und entscheidet sich für eine Erneuerung. {#sarah-receives-an-insurance-policy-renewal-communication-from-we-finance-and-decides-to-renew}

Sarah erhält eine E-Mail mit einer Anlage von We.Finance, die sie daran erinnert, dass ihre Kfz-Versicherungspolice bald abläuft. Der Anhang ist die Druckversion ihrer Details zur Erneuerung ihrer Kfz-Versicherungspolice.

Sarah klickt **Jetzt erneuern** und wird zur Web-Version ihres Autoversicherungs-Briefes weitergeleitet. Zusätzlich zu diesem Brief findet Sarah noch einige Tage, bis ihre Richtlinie abläuft. Auf der Seite erhalten Sarah einen Überblick über ihre Details zu den Versicherungspolice, wie z. B. die Policennummer, den fälligen Betrag und andere Informationen wie Rabattangebote und Treuebelohnungen. Sarah klickt auf **Jetzt erneuern** am Ende der Police.

![auto-insurance-extending-email](assets/auto-insurance-renewal-email.png)

#### Funktionsweise  {#how-it-works-21}

Die Web- und Druckausgaben Ihres Autoversicherungs-Briefs werden mithilfe der kanalübergreifenden Funktionen der interaktiven Kommunikation erstellt. Die **Jetzt erneuern** in der E-Mail mit der Anwendung zur automatischen Versicherungsverlängerung verknüpft ist, bei der es sich um eine interaktive Kommunikation auf einer Veröffentlichungsinstanz handelt.

![ic-web-version](assets/ic-web-version.png)

#### Sehen Sie selbst  {#see-it-yourself-19}

Sie müssen eine E-Mail mit einem angehängten PDF-Dokument erhalten haben. Die PDF ist eine Druckversion Ihres Autoversicherungs-Briefes. Klicken Sie auf **Jetzt erneuern**, um zur Web-Version der Police zu gelangen. Überprüfen Sie Ihre personenbezogenen Daten und Richtliniendetails und klicken Sie auf **Jetzt erneuern**. Sie werden zum adaptiven Formular zur Zahlung weitergeleitet.

Die Schaltfläche **Jetzt erneuern** in der E-Mail leitet Sarah zur Web-Version der Police. Sie können folgende URL aufrufen:

https://[publishServer]:[publishPort]/content/document.html?schema=fdm&amp;documentId=/content/forms/af/we-finance/autoinsurance/auto-insurance-renewal/channels/web.html&amp;customerId=90001

Sie können die detaillierte Zusammenfassung der Erneuerung Ihrer Kfz-Versicherung überprüfen und auf **Jetzt erneuern** unten auf der Seite.

### Sarah öffnet die Zahlungsseite, nimmt die Zahlung vor und schließt den Prozess ab {#sarah-opens-the-payment-page-and-makes-the-payment-and-completes-the-process}

Wenn Sarah klickt **Jetzt erneuern** in der Webversion der interaktiven Kommunikation wird die Zahlungsseite geöffnet. Sarah vergleicht ihre Police-Nummer und das Ablaufdatum mit ihren Unterlagen. Rechts auf der Seite prüft sie die Zahlungszusammenfassung ihrer Erneuerung mit 10 % Prämienrabatt auf den Gesamtbetrag. Sarah gibt ihre Kreditkartendetails ein und klickt auf **Zahlung ausführen**.

![payment-adaptive-form](assets/payment-adaptive-form.png)

#### Funktionsweise  {#how-it-works-22}

Die Schaltfläche „Jetzt erneuern“ leitet Sarah auf die Zahlungsseite. Die Zahlungsseite ist ein adaptives Formular. Sarah füllt die Kreditkartendetails aus und klickt auf **Einsenden**. Ihre Kreditkartenzahlung wird verarbeitet und eine im adaptiven Formular konfigurierte Dankesnachricht wird auf dem Bildschirm angezeigt.

#### Sehen Sie selbst  {#see-it-yourself-20}

Klicken Sie auf **Jetzt erneuern**, um zur Zahlungsseite zu gelangen. Geben Sie Ihre Kreditkarteninformationen ein und klicken Sie auf **Zahlung ausführen.** Sie können die Zahlungsseite in der Authoring-Instanz erreichen unter:

https://[authorServer]:[authorPort]/content/document.html?documentId=/content/forms/af/we-finance/credit-card/ccbillpayment.html&amp;schema=fdm&amp;customerId=90001

Die Dankesmeldung wird angezeigt, nachdem auf die Schaltfläche Zahlung vornehmen geklickt wurde.
