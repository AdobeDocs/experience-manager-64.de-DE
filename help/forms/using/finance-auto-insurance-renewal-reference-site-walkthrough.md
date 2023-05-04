---
title: Anleitung zur Erneuerung der Kfz-Versicherung auf der Referenz-Site von We.Finance
seo-title: We.Finance Auto Insurance Renewal reference site walkthrough
description: Lesen Sie die ausführliche Anleitung der Referenz-Website zum We.Finance-Anwendungsbeispiel für Kfz-Versicherung , in der erläutert wird, wie AEM Formulare und seine Integration mit Microsoft Dynamics zur Personalisierung des Kundenerlebnisses in einem Finanzdienstleistungsunternehmen beitragen.
seo-description: Read on detailed reference site walkthrough of We.Finance Auto Insurance use case which showcases how AEM forms and its integration with Microsoft Dynamics helps personalize customer experience in a financial service company.
uuid: 18676ab4-9f8d-4014-b751-2a722fd152da
contentOwner: dekalra
topic-tags: introduction
discoiquuid: a960d489-f5a3-436a-b028-54292648c7be
exl-id: db416cbc-27a7-4a2c-b4b3-43e8963faf22
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 75%

---

# Anleitung zur Erneuerung der Kfz-Versicherung auf der Referenz-Site von We.Finance {#we-finance-auto-insurance-renewal-reference-site-walkthrough}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Voraussetzungen {#pre-requisites}

Richten Sie die Referenz-Website ein, wie unter [Einrichten und Konfigurieren AEM 6.4 Forms Reference Site](/help/forms/using/setup-reference-sites.md).

## Szenario für We.Finance-Referenz-Site  {#we-finance-reference-site-scenario}

Die Website von We.Finance ist eine Website für Finanzdienstleistungen, mit der Sie interaktive Kommunikationsfunktionen von AEM Forms erlernen können.

Erfahren Sie mehr über die detaillierte Anleitung des Anwendungsfalls zur Kfz-Versicherung von We.Finance, der zeigt, wie Sie AEM Forms und die Integration in Microsoft Dynamics nutzen können, um die Kundenerfahrung in einem Finanzdienstleistungsunternehmen zu personalisieren. Die interaktive Anleitung hat das Ziel, die Implementierung komplexer digitaler Transaktionen und Kundenkommunikationen in einem Finanzunternehmen zu erleichtern.

**Das Ganze beginnt mit dem Benutzerszenario:** 

Sarah Rose ist bereits We.Finance-Kundin und hat eine Kfz-Versicherungspolice erworben. Jetzt wird es Zeit für die Erneuerung ihrer Versicherungspolice. Gloria Rios, Versicherungs-Agent, We.Finance sendet eine Erinnerung an Sarah über die Verlängerung ihrer Police. Sarah folgt den Anweisungen in der E-Mail und schließt den Prozess erfolgreich ab.

## Anleitung zur Anwendung für Kfz-Versicherungen {#auto-insurance-application-walkthrough}

Das Szenario für den Antrag auf Kfz-Versicherung von We.Finance ist eine visuelle Schilderung für den Benutzer und basiert auf zwei Personen:

* Sarah Rose, We.Finance-Kunde
* Gloria Rios, Versicherungs-Agent, We.Finance

### Gloria sendet eine Mitteilung zur Erneuerung einer Versicherungspolice von We.Finance {#gloria-sends-an-insurance-policy-renewal-communication-from-we-finance}

Gloria meldet sich bei der AEM-Instanz an, klickt auf **Erneuerung der Kfz-Versicherung** und dann auf **Agent-Benutzeroberfläche öffnen.** Durch das Klicken wird das Versicherungsdokument mit den Vertragsdetails von Sarah Rose vorausgefüllt. Gloria klickt auf **Senden**, woraufhin auf dem Bildschirm die Meldung „Submission Initiated (Absenden eingeleitet)“ und dann wenige Sekunden danach „Submitted Successfully (Erfolgreich abgesendet)“ erscheint.

Sarah erhält eine E-Mail mit dem Betreff „Die Erneuerung Ihrer Kfz-Versicherung“.

![agent_ui_email](assets/agent_ui_email.png)

#### Sehen Sie selbst {#see-it-yourself}

Wechseln Sie zu **Adobe Experience Manager** > **Formulare** > **Formulare und Dokumente** > **We.Finance** > **Kfz-Versicherung**. Wählen Sie die **Erneuerung der Kfz-Versicherung** interaktive Kommunikation und Klicken **Benutzeroberfläche für Agenten öffnen**. Die interaktive Kommunikation wird in der Agent UI geöffnet. Geben Sie eine gültige E-Mail-Adresse ein, um die E-Mail mit dem angehängten Dokument zur Police zu erhalten, und klicken Sie auf „Senden“.

Sie können direkt unter `https://[authorHost]: authorPort]/aem/formdetails.html/content/dam/formsanddocuments/we-finance/autoinsurance/auto-insurance-renewal.` auf die interaktive Kommunikation zur Erneuerung der Kfz-Versicherung zugreifen und sie dort überprüfen.

### Sarah erhält von We.Finance eine Mitteilung zur Erneuerung der Kfz-Versicherung und entscheidet sich für eine Erneuerung. {#sarah-receives-an-insurance-policy-renewal-communication-from-we-finance-and-decides-to-renew}

Sarah erhält eine E-Mail mit einem Anhang von We.Finance, die sie daran erinnert, dass ihre Kfz-Versicherungspolice bald abläuft. Der Anhang ist die Druckversion des Schreibens zu ihrer Kfz-Versicherung.

Sarah klickt auf **Jetzt erneuern** und wird zur Web-Version des Schreibens zu ihrer Kfz-Versicherung weitergeleitet. Oben im Schreiben sieht Sarah die Anzahl der Tage bis zum Ablauf ihrer Police. Die Seite bietet Sarah einen grundlegenden Überblick über die Details ihrer Versicherungspolice wie die Nummer der Police, den fälligen Betrag und andere Informationen wie Rabattangebote und Treueprämien. Sarah klickt auf **Jetzt erneuern** am Ende der Police.

![ref1](assets/ref1.png)

#### Funktionsweise {#how-it-works}

Die Web- und Druckausgabe Ihres Schreibens zur Kfz-Versicherung wird mithilfe der Mehrkanalfunktionen der interaktiven Kommunikation erstellt.

Die Schaltfläche Jetzt erneuern in der E-Mail ist mit der Anwendung zur Erneuerung der Kfz-Versicherung verknüpft, bei der es sich um eine interaktive Kommunikation auf einer Veröffentlichungsinstanz handelt.

#### Sehen Sie selbst {#see-it-yourself-1}

Sie müssen eine E-Mail mit einer angehängten PDF erhalten haben. Die PDF-Datei ist eine Druckversion dieses Schreibens zur Kfz-Versicherung. Klicken Sie auf **Jetzt erneuern**, um zur Web-Version der Police zu gelangen. Überprüfen Sie Ihre persönlichen Angaben und Details der Police und klicken Sie auf **Jetzt erneuern**, um zu einer anderen interaktiven Kommunikation zu gelangen.

Die Schaltfläche **Jetzt erneuern** in der E-Mail leitet Sarah zur Web-Version der Police. Sie können folgende URL aufrufen:

`https://[authorServer]:[authorPort]/content/document.html?schema=fdm&documentId=/content/forms/af/we-finance/autoinsurance/auto-insurance-renewal/channels/web.html&customerId=1`

Sie können die detaillierte Zusammenfassung der Erneuerung Ihrer Kfz-Versicherung überprüfen und auf **Jetzt erneuern** unten auf der Seite klicken.

### Sarah wird auf die Zahlungsseite geleitet. {#sarah-reaches-the-payment-page}

We.Finance leitet Sarah zur Zahlungsseite. Sarah vergleicht ihre Police-Nummer und das Ablaufdatum mit ihren Unterlagen. Rechts auf der Seite prüft sie die Zahlungszusammenfassung ihrer Erneuerung mit 10 % Prämienrabatt auf den Gesamtbetrag.

#### Funktionsweise {#how-it-works-1}

Die Schaltfläche „Jetzt erneuern“ leitet Sarah auf die Zahlungsseite. Die Zahlungsseite ist ein adaptives Formular.

#### Sehen Sie selbst {#see-it-yourself-2}

Klicken Sie auf **Jetzt erneuern**, um zur Zahlungsseite zu gelangen. Geben Sie Ihre Kreditkarteninformationen ein und klicken Sie auf **Zahlung ausführen.**

Sie werden zur Zahlungsseite in der Authoring-Instanz geleitet:

`https://[authorServer]:[authorPort]/content/document.html?documentId=/content/forms/af/we-finance/credit-card/ccbillpayment.html&schema=fdm&customerId=1`

### Sarah nimmt die Zahlung vor und schließt den Prozess ab. {#sarah-makes-the-payment-and-completes-the-process}

Sarah gibt ihre Kreditkartendetails ein und klickt auf **Zahlung ausführen**.

#### Funktionsweise {#how-it-works-2}

Wenn Sarah die Kreditkartendetails ausfüllt und auf Senden klickt, wird ihre Kreditkartenzahlung verarbeitet und eine im adaptiven Formular konfigurierte Dankesnachricht wird auf dem Bildschirm angezeigt.

#### Sehen Sie selbst {#see-it-yourself-3}

Sie können die Bestätigungsmeldung anzeigen, nachdem Sie auf „Zahlung ausführen“ geklickt haben

`https://[authorServer]:[authorPort]/content/forms/af/we-finance/credit-card/ccbillpayment/jcr:content/guideContainer.guideThankYouPage.html?owner=admin&status=Submitted`
