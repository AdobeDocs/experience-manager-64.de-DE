---
title: Anleitung zur Erneuerung der Kfz-Versicherung auf der Referenz-Site von We.Finance
seo-title: Anleitung zur Erneuerung der Kfz-Versicherung auf der Referenz-Site von We.Finance
description: 'null'
seo-description: 'null'
uuid: 18676ab4-9f8d-4014-b751-2a722fd152da
contentOwner: dekalra
topic-tags: introduction
discoiquuid: a960d489-f5a3-436a-b028-54292648c7be
translation-type: tm+mt
source-git-commit: 4466161992d877b17d43fe73e3298dd6252733c0
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 37%

---


# Anleitung zur Erneuerung der Kfz-Versicherung auf der Referenz-Site von We.Finance {#we-finance-auto-insurance-renewal-reference-site-walkthrough}

## Voraussetzungen {#pre-requisites}

Setup the reference site as described in [Setup and configure AEM 6.4 Forms Reference Site](/help/forms/using/setup-reference-sites.md).

## Szenario für We.Finance-Referenz-Site  {#we-finance-reference-site-scenario}

Wir.Finance Website ist eine Finanzdienstleistungs-Website, die Ihnen hilft, interaktive Kommunikationsfähigkeiten von AEM Forms zu lernen.

Lesen Sie die ausführliche Anleitung von We.Finance Auto Insurance Verwendungsfall, in der erläutert wird, wie AEM Formulare und ihre Integration mit Microsoft Dynamics zu einer personalisierten Kundenerfahrung in einer Finanzdienstleistungsbranche beitragen. Die interaktive exemplarische Vorgehensweise soll die Implementierung komplexer digitaler Transaktionen und die Kundenkommunikation in einer finanziellen Firma erleichtern.

**Das Ganze beginnt mit dem Benutzerszenario:** 

Sarah Rose ist bereits We.Finance-Kundin und hat eine Kfz-Versicherungspolice erworben. Jetzt wird es Zeit für die Erneuerung ihrer Versicherungspolice. Gloria Rios, Versicherungsmitarbeiterin von We.Finance sendet Sarah eine Erinnerung bezüglich der Erneuerung ihrer Versicherungspolice. Sarah folgt den Anweisungen in der E-Mail und schließt den Vorgang erfolgreich ab.

## Anleitung für einen Antrag auf eine Kfz-Versicherung {#auto-insurance-application-walkthrough}

Das Anwendungsszenario &quot;Wir.Finance Auto Insurance&quot;ist eine visuelle Anmerkung für den Benutzer und basiert auf zwei Personen:

* Sarah Rose, einen We.Finance-Kunden
* Gloria Rios, Versicherungsmitarbeiterin, We.Finance

### Gloria sendet eine Mitteilung zur Erneuerung der Versicherungspolice von We.Finance {#gloria-sends-an-insurance-policy-renewal-communication-from-we-finance}

Gloria logs into AEM instance, clicks **Auto Insurance Renewal,** and then clicks **Open Agent UI.** Der Klick füllt das Versicherungs-Dokument mit den Richtliniendetails von Sarah Rose im Voraus aus. Gloria clicks **Submit** and a message is displayed on the screen “Submission Initiated” and then in few seconds “Submitted Successfully”.

Sarah erhält eine E-Mail mit dem Betreff &quot;Ihre Auto-Versicherung Verlängerung&quot;.

![agent_ui_email](assets/agent_ui_email.png)

#### Sehen Sie selbst{#see-it-yourself} 

Go to **Adobe Experience Manager** > **Forms** > **Forms &amp; Documents** > **We.Finance** > **Auto Insurance**. Select the **Auto Insurance Renewal** interactive communication and click **Open Agent UI**. Die interaktive Kommunikation wird in der Agent UI geöffnet. Geben Sie eine gültige E-Mail-Adresse ein, um die E-Mail mit dem angehängten Policy-Dokument zu erhalten, und klicken Sie auf Senden.

You can access and review the Auto Insurance Renewal interactive communication directly from `https://[authorHost]: authorPort]/aem/formdetails.html/content/dam/formsanddocuments/we-finance/autoinsurance/auto-insurance-renewal.`

### Sarah erhält von We.Finance eine Mitteilung zur Erneuerung der Kfz-Versicherung und entscheidet sich für eine Erneuerung.{#sarah-receives-an-insurance-policy-renewal-communication-from-we-finance-and-decides-to-renew}

Sarah erhält eine E-Mail mit einem Anhang von We.Finance, der sie daran erinnert, dass ihre Auto-Versicherung läuft. Die Anlage ist die Druckversion ihres Autoversicherungsbriefs.

Sarah clicks **Renew Now** and is directed to the web version of her Auto Insurance letter. Über diesem Brief hinaus findet Sarah noch viele Tage, bis ihre Richtlinie abläuft. Die Seite bietet Sarah einen grundlegenden Überblick über ihre Versicherungsrichtlinien wie Versicherungsnummer, Fälligkeitsbetrag und andere Informationen wie Rabatt-Angebote und Treuebelohnungen. Sarah again clicks **Renew Now** at the bottom of the policy.

![ref1](assets/ref1.png)

#### Funktionsweise {#how-it-works}

Die Web- und Druckausgabe Ihres Autom. Versicherungsbriefs wird mit den Funktionen von Interactive Communications (mit mehreren Kanälen) erstellt.

Die Schaltfläche „Jetzt erneuern“ in der E-Mail ist mit der Anwendung „Kfz-Versicherung erneuern“ verknüpft, die eine interaktive Kommunikation auf einer Veröffentlichungsinstanz ist.

#### Sehen Sie selbst {#see-it-yourself-1}

Sie müssen eine E-Mail mit einem angehängten PDF-Dokument erhalten haben. Die PDF-Datei ist eine Druckversion Ihres Autoversicherungsantrags. Click **Renew Now** to reach to the web version of the policy. Check your personal information and policy details and click **Renew Now** which takes you to another Interactive Communication.

The **Renew Now** button in the email directs Sarah to the web version of the policy. Sie können folgende URL aufrufen:

`https://[authorServer]:[authorPort]/content/document.html?schema=fdm&documentId=/content/forms/af/we-finance/autoinsurance/auto-insurance-renewal/channels/web.html&customerId=1`

You can check the detailed summary of your Auto Insurance Renewal and click **Renew Now** at the bottom of the page.

### Sarah wird auf die Zahlungsseite geleitet.{#sarah-reaches-the-payment-page}

We.Finance leitet Sarah zur Zahlungsseite. Sarah überprüft ihre Richtliniennummer und ihr Ablaufdatum mit ihren Aufzeichnungen. Auf der rechten Seite der Seite prüft sie die Zahlungszusammenfassung ihrer Verlängerung mit 10% Premium Rabatt auf den Gesamtbetrag.

#### Funktionsweise {#how-it-works-1}

Über die Schaltfläche &quot;Jetzt verlängern&quot;wird Sarah zur Zahlungsseite geleitet. Die Zahlungsseite ist ein adaptives Formular.

#### Sehen Sie selbst{#see-it-yourself-2} 

Klicken Sie auf **Jetzt erneuern**, um zur Zahlungsseite zu gelangen. Fill in your Credit Card information, and click **Make Payment.**

Sie können die Zahlungsseite in der Authoring-Instanz unter

`https://[authorServer]:[authorPort]/content/document.html?documentId=/content/forms/af/we-finance/credit-card/ccbillpayment.html&schema=fdm&customerId=1`

### Sarah nimmt die Zahlung vor und schließt den Prozess ab.{#sarah-makes-the-payment-and-completes-the-process}

Sarah gibt ihre Kreditkartendetails ein und klickt auf **Zahlung ausführen**.

#### Funktionsweise {#how-it-works-2}

Wenn Sarah die Kreditkartendaten eingibt und auf „Senden“ klickt, wird ihre Kreditkartenzahlung verarbeitet und auf dem Bildschirm erscheint eine Dankesnachricht, die im adaptiven Formular konfiguriert wurde.

#### Sehen Sie selbst {#see-it-yourself-3}

Sie können die Bestätigungsmeldung anzeigen, nachdem Sie auf „Zahlung ausführen“ geklickt haben

`https://[authorServer]:[authorPort]/content/forms/af/we-finance/credit-card/ccbillpayment/jcr:content/guideContainer.guideThankYouPage.html?owner=admin&status=Submitted`
