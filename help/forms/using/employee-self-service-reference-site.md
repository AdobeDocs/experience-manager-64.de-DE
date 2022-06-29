---
title: Schrittweise Anleitung zur Referenz-Site für Mitarbeiter-Self-Service
seo-title: Employee self-service
description: Die Referenzseite von AEM Forms zeigt, wie Unternehmen die Funktionen von AEM Forms nutzen können, um Mitarbeiterrekrutierung und Self-Service-Workflows zu implementieren.
seo-description: AEM Forms reference site showcases how organizations can leverage AEM Forms features to implement employee recruitment and self-service workflows.
uuid: ecc98e0d-c964-44dc-b219-9ebe92632d22
topic-tags: introduction
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d2695f71-5126-477c-ae6b-a964fb55728b
exl-id: 7fbdd976-5a70-4af4-b449-7c2d6bcfd915
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1623'
ht-degree: 84%

---

# Mitarbeiter-Self-Service Schrittweise Anleitung zur Referenz-Website {#employee-self-service-reference-site-walkthrough}

## Voraussetzung {#prerequisite}

Richten Sie die Referenz-Websites ein wie in [Einrichten und Konfigurieren von AEM Forms-Referenz-Websites](/help/forms/using/setup-reference-sites.md) beschrieben.

## Übersicht {#overview}

Mitarbeiter-Self-Service-Systeme, die in der Regel im firmeneigenen Intranet gehostet werden, bieten Mitarbeitern Zugang zu einer Vielzahl von Informationen und Diensten, die sie von ihrem Schreibtisch aus nutzen können. Es gibt den Mitarbeitern die vollständige Kontrolle über die Durchführung von Maßnahmen wie den Zugang zu ihren Mitarbeiterdaten, die Beantragung von Urlaub und das Einreichen von Spesenabrechnungen. Umgekehrt hilft es Organisationen, die Prozesseffizienz zu verbessern und Kosten zu senken, während die Mitarbeiter informiert und engagiert bleiben.

Die Mitarbeiter-Self-Service-Referenzseite zeigt, wie Sie mit AEM Forms das Self-Services-System für Mitarbeiter in Ihrer Organisation implementieren können.

>[!NOTE]
>
>Anwendungsfälle für Mitarbeiter-Self-Service sind sowohl auf We.Finance- als auch auf We.Gov-Referenz-Websites verfügbar. Die in den Anleitungen verwendeten Beispiele, Bilder und Beschreibungen beziehen sich auf die We.Finance-Referenz-Website. Sie können diese Anwendungsfälle jedoch auch mit We.Gov ausführen und dort Artefakte überprüfen. Ersetzen Sie dazu in den genannten URLs **we-finance** durch **we-gov**.

## Interessenkonflikt- Schrittweiser Fragebogen {#conflict-of-interest-questionnaire-walkthrough}

Unternehmen fordern von Zeit zu Zeit ihre Mitarbeiter auf, einen Fragebogen zu Interessenkonflikten zu übermitteln, um externe Aktivitäten oder persönliche Beziehungen ihrer Mitarbeiter zu identifizieren, die möglicherweise in Konflikt mit ihrer Organisation stehen.

Die Compliance-Abteilung von Sarahs Organisation hat Mitarbeiter gebeten, den Fragebogen zu Interessenkonflikten einzureichen.

### Sarah reicht den Fragebogen zu Interessenkonflikten ein {#sarah-submits-the-conflict-of-interest-questionnaire}

Sarah geht zum Portal ihrer Organisation, meldet sich an und klickt auf „Mitarbeiter“, um auf das Mitarbeiter-Dashboard zuzugreifen. Sie findet den Fragebogen zu Interessenkonflikten auf dem Mitarbeiter-Dashboard und klickt auf **[!UICONTROL Beantragen.]**

![we-finance-home](assets/we-finance-home.png)
**Abbildung:** *Organisationsportal*

![employee-dashboard](assets/employee-dashboard.png)
**Abbildung:** *Mitarbeiter-Dashboard*

Sarah navigiert durch das Formular mit der Schaltfläche „Weiter“ und liest die Abschnitte „Einführung“ und „Definition“. Sie beantwortet die Fragen im Abschnitt „Fragen“. Schließlich unterschreibt sie den Fragebogen und reicht ihn ein.

Das Unternehmensportal und der Fragebogen sind interaktiv und kann auf mobilen Geräten genutzt werden. Der folgende Workflow zeigt, wie Sarah den Fragebogen auf ihrem Mobilgerät durchsucht und übermittelt.

![conflict-form-on-mobile](assets/conflict-form-on-mobile.png)

**Funktionsweise**

Das Unternehmensportal und das Mitarbeiter-Dashboard sind AEM-Sites. Das Dashboard listet verschiedene Self-Service-Optionen auf, z. B. den Fragebogen zu Interessenkonflikten. Die Schaltfläche „Beantragen“ ist mit einem adaptiven Formular verknüpft.

Das adaptive Formular verwendet Regeln, um Informationen basierend auf der Antwort auf der Registerkarte „Fragen“ ein- oder auszublenden. Außerdem verwendet das Formular die Scribble-Komponente zum Signieren auf der Registerkarte „Deklaration“. Überprüfen Sie das adaptive Formular unter `https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/employee/self-service/conflict-of-interest.html`.

**Sehen Sie selbst**

Navigieren Sie zu `https://[publishHost]:[publishPort]/content/we-finance/global/en/self-service-forms.html` und melden Sie sich mit `srose/srose` als Benutzername/Kennwort für Sarah. Klicken Sie auf **[!UICONTROL Mitarbeiter]**, um auf das Dashboard zuzugreifen, und klicken Sie anschließend auf **[!UICONTROL Beantragen]** im Fragebogen zu Interessenkonflikten. Überprüfen und übermitteln Sie den Fragebogen.

### Gloria prüft und genehmigt die Übermittlung des Fragebogens zu Interessenkonflikten {#gloria-reviews-and-approves-the-conflict-of-interest-questionnaire-submission}

Der von Sarah eingereichte Fragebogen zum Interessenkonflikt wird Gloria Rios zur Überprüfung übergeben. Gloria arbeitet als Compliance Officer in dem Unternehmen. Gloria meldet sich bei ihrem AEM-Posteingang an und überprüft die ihr zugewiesenen Aufgaben. Sie genehmigt den von Sarah eingereichten Fragebogen und schließt die Aufgabe ab.

![Posteingang für Konflikte](assets/conflict-inbox.png)
**Abbildung:** *Glorias Posteingang*

![konfliktgenehmigt](assets/conflict-approved.png)
**Abbildung:** *Aufgabe öffnen*

**Funktionsweise**

Die Übermittlungsaktion im Fragebogen „Interessenkonflikt“ löst einen Workflow aus, der eine Aufgabe in Glorias Posteingang zur Genehmigung erstellt. Überprüfen Sie den Forms Workflow unter `https://[authorHost]:[authorPort]/editor.html/conf/global/settings/workflow/models/we-finance/employee/self-service/we-finance-employee-conflict-of-interest.html`

![employee-self-service-reference-site](assets/employee-self-service-reference-site.png)

**Sehen Sie selbst**

Navigieren Sie zu `https://[publishHost]:[publishPort]/content/we-finance/global/en/login.html?resource=/aem/inbox.html` und melden Sie sich mit `grios/password` als Benutzername/Kennwort für Gloria Rios. Öffnen Sie die für den Fragebogen zu Interessenkonflikten erstellte Aufgabe und genehmigen Sie diese.

## Antrag auf Unternehmenskarte - Anleitung {#corporate-card-application-walkthrough}

Sarah reist viel geschäftlich und benötigt eine Unternehmenskreditkarte, um ihre Rechnungen unterwegs zu bezahlen. Sie beantragt eine Firmenkarte über das Mitarbeiterportal ihres Unternehmens.

### Sarah reicht den Antrag für die Unternehmenskarte ein {#sarah-submits-the-corporate-card-application}

Sarah geht zum Portal ihres Unternehmens, meldet sich an und klickt auf **[!UICONTROL Mitarbeiter]**, um auf das Mitarbeiter-Dashboard zuzugreifen. Sie findet den Antrag für die Unternehmenskarte auf dem Mitarbeiter-Dashboard und klickt auf **[!UICONTROL Übernehmen]**.

![we-finance-home-1](assets/we-finance-home-1.png)
**Abbildung:** *Organisationsportal*

![employee-dashboard-1](assets/employee-dashboard-1.png)
**Abbildung:** *Mitarbeiter-Dashboard*

Sie klickt auf **[!UICONTROL Übernehmen]** im Antrag für die Unternehmenskarte. Ein Antrag auf einer einzelnen Seite wird geöffnet. Sie füllt alle Details aus und klickt auf **[!UICONTROL Übernehmen]**, um die Anwendung zu senden.

![Kartenformular](assets/card-form.png)

**Funktionsweise**

Das Unternehmensportal und das Mitarbeiter-Dashboard sind AEM-Sites. Das Dashboard listet verschiedene Self-Service-Optionen auf, z. B. den Antrag für die Unternehmenskarten. Die Schaltfläche „Übernehmen“ im Antrag ist mit einem adaptiven Formular verknüpft.

Das adaptive Formular für einen Antrag auf eine Unternehmenskarte ist ein einfaches, einseitiges, interaktives adaptives Formular. Es verwendet grundlegende adaptive Formularkomponenten wie Text, Telefon, numerisches Feld und numerischen Stepper. Überprüfen Sie das adaptive Formular unter:\
`https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/employee/self-service/corporate-card.html`.

**Sehen Sie selbst**

Navigieren Sie zu `https://[publishHost]:[publishPort]/content/we-finance/global/en/self-service-forms.html` und melden Sie sich mit `srose/srose` als Benutzername/Kennwort für Sarah. Klicken Sie auf **[!UICONTROL Mitarbeiter]**, um auf das Dashboard zuzugreifen, und klicken Sie dann auf **[!UICONTROL Übernehmen]** im Antrag auf die Unternehmenskarte. Geben Sie die Details ein und senden Sie den Antrag ab.

### Gloria prüft und genehmigt die Anwendung der Unternehmenskarte {#gloria-reviews-and-approves-the-corporate-card-application}

Der von Sarah eingereichte Antrag auf eine Unternehmenskarte wird zur Prüfung an Gloria Rios weitergeleitet. Gloria meldet sich bei ihrem AEM-Posteingang an und überprüft die ihr zugewiesenen Aufgaben. Sie genehmigt den von Sarah eingereichten Antrag und schließt die Aufgabe ab.

![corporate-card-inbox](assets/corporate-card-inbox.png)
**Abbildung:** *Glorias Posteingang*

![Corporate Card-authorised](assets/corporate-card-approved.png)
**Abbildung:** *Aufgabe öffnen*

**Funktionsweise**

Der Workflow für die Einreichung auf dem Antrag auf eine Unternehmenskarte löst einen Workflow für Formulare aus, der eine Aufgabe in Glorias Posteingang zur Genehmigung erstellt. Überprüfen Sie den Forms Workflow unter `https://[authorHost]:[authorPort]/editor.html/conf/global/settings/workflow/models/we-finance/employee/self-service/we-finance-employee-corporate-card.html`

![corporate-card-workflow-model](assets/corporate-card-workflow-model.png)

**Sehen Sie selbst**

Navigieren Sie zu `https://[publishHost]:[publishPort]/content/we-finance/global/en/login.html?resource=/aem/inbox.html` und melden Sie sich mit `grios/password` als Benutzername/Kennwort für Gloria Rios. Öffnen Sie die Aufgabe, die für den Antrag auf eine Unternehmenskarte erstellt wurde, und genehmigen Sie sie.

## Einreichung von Spesenberichten - Anleitung {#expense-report-submission-walkthrough}

Da Sarah während Geschäftsreisen Ausgaben hat, muss sie Spesenberichte zur Genehmigung einreichen. Mit der Self-Service-Option in ihrem Unternehmen kann sie die Spesenabrechnung online einreichen.

### Sarah reicht den Antrag für den Spesenbericht ein {#sarah-submits-the-expense-report-application}

Sarah geht zum Portal ihres Unternehmens, meldet sich an und klickt auf **[!UICONTROL Mitarbeiter]**, um auf das Mitarbeiter-Dashboard zuzugreifen. Sie findet den Antrag für den Spesenbericht auf dem Mitarbeiter-Dashboard und klickt auf **[!UICONTROL Beantragen]**.

![we-finance-home-2](assets/we-finance-home-2.png)
**Abbildung:** *Organisationsportal*

![employee-dashboard-2](assets/employee-dashboard-2.png)
**Abbildung:** *Mitarbeiter-Dashboard*

Sie klickt auf **[!UICONTROL Beantragen]** im Antrag für den Spesenbericht. Ein Antragsformular wird geöffnet, das zwei Registerkarten enthält: Berichtsname und Berichtsdetails. Mit dem **+**-Symbol auf der Registerkarte „Berichtsdetails“ kann sie mehr als nur Spesen in einem Bericht hinzufügen.

Das Unternehmensportal und die Anträge sind interaktiv und können auf mobilen Geräten genutzt werden. Der folgende Workflow zeigt, wie Sarah den Spesenbericht auf ihrem Mobilgerät durchsucht und einreicht.

![cost-report-on-mobile](assets/expense-report-on-mobile.png)

**Funktionsweise**

Das Unternehmensportal und das Mitarbeiter-Dashboard sind AEM-Sites. Das Dashboard listet mehrere Self-Service-Optionen auf, z. B. den Antrag für den Spesenbericht. Die Schaltfläche „Beantragen“ ist mit einem adaptiven Formular verknüpft.

Die Registerkarten „Berichtsname“ und „Berichtsdetails“ im adaptiven Formular sind Bereichskomponenten. Der Bereich „Berichtdetails“ enthält den Bereich „Spesen“. Es ist einen wiederholbaren Bereich, mit dem mehrere Spesen im Bericht hinzugefügt werden können. Überprüfen Sie das adaptive Formular und seine Konfigurationen unter `https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/employee/expense-report.html`.

**Sehen Sie selbst**

Navigieren Sie zu `https://[publishHost]:[publishPort]/content/we-finance/global/en/self-service-forms.html` und melden Sie sich mit `srose/srose` als Benutzername/Kennwort für Sarah. Klicken Sie auf **[!UICONTROL Mitarbeiter]**, um auf das Dashboard zuzugreifen, und klicken Sie dann auf **[!UICONTROL Beantragen]** im Spesenbericht. Geben Sie die Details ein und übermitteln Sie den Antrag.

### Gloria überprüft und genehmigt die Spesenabrechnung {#gloria-reviews-and-approves-the-expense-report}

Der von Sarah eingereichte Spesenbericht wird Gloria Rios zur Prüfung übergeben. Gloria meldet sich bei ihrem AEM-Posteingang an und überprüft die ihr zugewiesenen Aufgaben. Sie genehmigt den von Sarah eingereichten Antrag und schließt die Aufgabe ab.

![cost-report-inbox](assets/expense-report-inbox.png)
**Abbildung:** *Glorias Posteingang*

![Spesenbericht-genehmigt](assets/expense-report-approved.png)
**Abbildung:** *Aufgabe öffnen*

**Funktionsweise**

Der Übermittlungs-Workflow Antrag für den Spesenbericht löst einen Formular-Workflow aus, der eine Aufgabe in Glorias Posteingang zur Genehmigung erstellt. Überprüfen Sie den Forms Workflow unter `https://[authorHost]:[authorPort]/editor.html/conf/global/settings/workflow/models/we-finance/employee/self-service/we-finance-employee-expense-report-workflow.html`

![corporate-card-cost-report-workflow-model](assets/corporate-card-expense-report-workflow-model.png)

**Sehen Sie selbst**

Navigieren Sie zu `https://[publishHost]:[publishPort]/content/we-finance/global/en/login.html?resource=/aem/inbox.html` und melden Sie sich mit `grios/password` als Benutzername/Kennwort für Gloria Rios. Öffnen Sie die Aufgabe, die für den Antrag für den Spesenbericht erstellt wurde, und genehmigen Sie sie.

## Antrag auf Urlaub - Anleitung {#leave-application-walkthrough}

Sarah plant nächsten Monat einen Familienurlaub und will einen Antrag auf eine Woche Urlaub stellen.

### Sarah reicht den Urlaubsantrag ein {#sarah-submits-the-leave-application}

Sarah geht zum Portal ihres Unternehmens, meldet sich an und klickt auf **[!UICONTROL Mitarbeiter]**, um auf das Mitarbeiter-Dashboard zuzugreifen. Sie findet den Antrag auf Urlaub auf dem Mitarbeiter-Dashboard und klickt auf **[!UICONTROL Beantragen]**.

![we-finance-home-3](assets/we-finance-home-3.png)
**Abbildung:** *Organisationsportal*

![employee-dashboard-3](assets/employee-dashboard-3.png)
**Abbildung:** *Mitarbeiter-Dashboard*

Der Antrag auf Urlaub wird mit dem Namen und der Angestellten-ID von Sarah geöffnet, die im Formular bereits ausgefüllt sind. Es zeigt auch ihr Urlaubsguthaben und den Verlauf. Sie füllt die Urlaubsdaten aus und reicht den Antrag zur Genehmigung ein.

Das Unternehmensportal und die Anträge sind interaktiv und können auf mobilen Geräten genutzt werden. Der folgende Workflow zeigt, wie Sarah durch den Antrag navigiert und diesen auf ihrem mobilen Gerät übermittelt.

![leave-form-on-mobile](assets/leave-form-on-mobile.png)

**Funktionsweise**

Das Unternehmensportal und das Mitarbeiter-Dashboard sind AEM-Sites. Das Dashboard listet mehrere Self-Service-Optionen auf, z. B. den Antrag auf Urlaub. Die Schaltfläche „Beantragen“ ist mit einem adaptiven Formular verknüpft.

Das adaptive Formular für den Antrag auf Urlaub basiert auf dem Formulardatenmodell für Urlaub für Mitarbeiter. Im Abschnitt „Urlaubsstand“ wird die Tabelle für den Urlaubsstand mithilfe des `getLeavesOf`-Formulardatenmodelldienstes befüllt. Die Felder „Anfangsdatum“ und „Enddatum“ verwenden Regeln, um zu überprüfen, ob die Datumswerte gleich oder nach dem aktuellen Datum liegen. Die Urlaubsdauer wird mit der Funktion `calcBusinessDays` berechnet.

Sie können das adaptive Formular und das Formulardatenmodell an folgenden Stellen überprüfen:

`https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/employee/self-service/leave-application.html`

`https://[authorHost]:[authorPort]/aem/fdm/editor.html/content/dam/formsanddocuments-fdm/db`

**Sehen Sie selbst**

Navigieren Sie zu `https://[publishHost]:[publishPort]/content/we-finance/global/en/self-service-forms.html` und melden Sie sich mit `srose/srose` als Benutzername/Kennwort für Sarah. Klicken Sie auf **[!UICONTROL Mitarbeiter]**, um auf das Dashboard zuzugreifen, und klicken Sie dann auf **[!UICONTROL Beantragen]** im Urlaubsantrag. Geben Sie die Details ein und übermitteln Sie den Antrag.

### Gloria geprüft und genehmigt den Urlaubsantrag {#gloria-reviews-and-approves-the-leave-application}

Der von Sarah eingereichte Urlaubsantrag wird Gloria Rios zur Überprüfung übergeben. Gloria meldet sich bei ihrem AEM-Posteingang an und überprüft die ihr zugewiesenen Aufgaben. Sie genehmigt den von Sarah eingereichten Antrag und schließt die Aufgabe ab.

![Posteingang verlassen](assets/leave-inbox.png)
**Abbildung:** *Glorias Posteingang*

![freilassen](assets/leave-approved.png)
**Abbildung:** *Aufgabe öffnen*

**Funktionsweise**

Der Übermittlungs-Workflow im Urlaubsantrag löst einen Formular-Workflow aus, der eine Aufgabe in Glorias Posteingang zur Genehmigung erstellt. Überprüfen Sie den Forms Workflow unter `https://[authorHost]:[authorPort]/editor.html/conf/global/settings/workflow/models/we-finance/employee/self-service/we-finance-employee-leave-application.html`

![corporate-card-leave-application-workflow-model](assets/corporate-card-leave-application-workflow-model.png)

**Sehen Sie selbst**

Navigieren Sie zu `https://[publishHost]:[publishPort]/content/we-finance/global/en/login.html?resource=/aem/inbox.html` und melden Sie sich mit `grios/password` als Benutzername/Kennwort für Gloria Rios. Öffnen Sie die Aufgabe, die für den Antrag auf Urlaub erstellt wurde, und genehmigen Sie sie.
