---
title: Einrichten und Konfigurieren von AEM Forms-Referenz-Sites
seo-title: Einrichten und Konfigurieren von AEM Forms-Referenz-Sites
description: AEM Forms Referenz-Sites zeigen, wie Sie mit AEM Forms End-to-End-Workflows in einer Organisation implementieren können.
seo-description: AEM Forms Referenz-Sites zeigen, wie Sie mit AEM Forms End-to-End-Workflows in einer Organisation implementieren können.
uuid: 087d58a1-d84e-49ac-a82d-4e7fc708f00f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 2feb4a9c-57ad-4c6b-a572-0047bc409bbb
translation-type: tm+mt
source-git-commit: 6a8fa45ec61014acebe09048066972ecb1284641
workflow-type: tm+mt
source-wordcount: '2922'
ht-degree: 48%

---


# Einrichten und Konfigurieren von AEM Forms-Referenzwebsites {#set-up-and-configure-aem-forms-reference-sites}

AEM Forms stellt eine Referenz-Site-Implementierung bereit, um zu zeigen, wie AEM Forms der Finanzdienstleistungsbranche und Regierungseinrichtungen helfen kann, komplexe Transaktionen in einfache digitale Vorgänge umzuwandeln, jederzeit und auf jedem Gerät.

Die We.Finance- und We.Gov-Referenz-Sites zeigen tatsächliche Anwendungsfälle für die Interaktion mit bestehenden und potenziellen Kunden von der ersten Kontaktaufnahme bis hin zum Verwalten von Korrespondenz und Transaktionen auf eine personalisierte und kostengünstige Weise.

Mithilfe der Referenz-Sites können Sie die folgenden wichtigen Funktionen von AEM Forms testen und präsentieren.

* Vereinfachte Authoring-Erfahrung bei ansprechenden und reaktionsfähigen adaptiven Formularen und interaktiver Kommunikation.
* Interaktive Kommunikation zur Erstellung interaktiver, personalisierter und reaktionsfähiger Kundenkommunikation, die sich an die Geräteeinstellung und das Layout anpassen.
* Datenintegration für die Verbindung zu unterschiedlichen Datenquellen zum Vorausfüllen und Übermitteln von Formulardaten über ein Formulardatenmodell.
* Forms-Workflow zur Automatisierung von Geschäftsprozessen und Workflows.
* Erweiterte Funktionen zur Verwaltung und Verarbeitung von Benutzerdaten.
* Integration mit Adobe Sign, um adaptive Formulare sicher zu signieren und zu senden.  
* Integration mit Adobe Target, um gezielten Empfehlungen nachzukommen und A/B-Tests durchzuführen, wodurch die Rentabilität eines Formulars maximiert werden kann.
* Integration mit Adobe Analytics, um die Leistung eines Formulars oder einer Kampagne zu messen und fundierte Entscheidungen treffen.
* Verbessertes Ausfüllen von Formularen.

Die Referenz-Sites stellen wiederverwendbare Assets bereit, die Sie als Vorlagen zum Erstellen eigener Assets verwenden können.

* Integration mit Adobe Sign, um adaptive Formulare sicher zu signieren und zu senden.  

* Integration mit Adobe Sign, um adaptive Formulare sicher zu signieren und zu senden.  

## Voraussetzungen und Schritte zum Einrichten der Referenz-Sites {#prerequisites-and-steps-to-set-up-reference-sites}

Bevor Sie die Referenz-Website einrichten, stellen Sie Folgendes sicher:

* **AEM**

   AEM QuickStart-, AEM Forms Add-On-Paket und Referenz-Website-Pakete. Weitere Informationen zu Add-On- und Referenz-Sitepaketen finden Sie unter [AEM Forms Releases](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html).

* **Einen SMTP-Dienst** Sie können einen beliebigen SMTP-Dienst verwenden.

* **Adobe Sign-Entwicklerkonto und Adobe Sign API-Anwendung**

   Um digitale Signaturen verwenden zu können, ist ein Adobe Sign-Entwicklerkonto erforderlich. Siehe[ Adobe Sign](https://acrobat.adobe.com/de/de/why-adobe/developer-form.html).

* Eine laufende Instanz von Microsoft Dynamics 365 zur Integration mit AEM Forms. Um die Referenz-Website auszuführen, importieren Sie die Beispieldaten in die Microsoft Dynamics-Instanz, um die interaktive Kommunikation, die auf der Referenz-Website verwendet wird, im Voraus auszufüllen.
* Eine laufende Instanz von AEM 6.4 mit Forms Add-On-Paket. Weitere Informationen finden Sie unter [Installation und Konfiguration von AEM Forms](installing-configuring-aem-forms-osgi.md).

Führen Sie die folgenden Schritte in der empfohlenen Reihenfolge aus, um die Referenz-Sites einzurichten und konfigurieren.

<table> 
 <tbody> 
  <tr> 
   <th><strong>Schritt</strong></th> 
   <th><strong>Konfigurieren</strong></th> 
   <th><strong>Hinweise</strong></th> 
  </tr> 
  <tr> 
   <td><a href="#installaemforms">Installieren und Konfigurieren von AEM Forms</a></td> 
   <td>Authoring und Veröffentlichen</td> 
   <td>Installieren und konfigurieren Sie die AEM Forms Authoring- und Veröffentlichungsinstanz.</td> 
  </tr> 
  <tr> 
   <td><a href="#ssl">SSL-Konfiguration</a></td> 
   <td>Authoring und Veröffentlichen<br />  </td> 
   <td>Aktivieren Sie HTTP über SSL für eine sichere Kommunikation mit Adobe Sign.</td> 
  </tr> 
  <tr> 
   <td><p><a href="#externalizer">Konfigurieren der Day CQ Link Externalizer-Konfiguration</a></p> </td> 
   <td>Authoring und Veröffentlichen<br />  </td> 
   <td><p>Referenzsite-Anwendungsfälle liefern E-Mails für verschiedene Transaktionen. Diese Einstellung ist zum Versenden von Newsletters per E-Mail erforderlich. Sie stellt sicher, dass URLs und Bilder auf die Veröffentlichungsinstanz verweisen. </p> </td> 
  </tr> 
  <tr> 
   <td><a href="#cqmail">Konfigurieren des Day CQ Mail Service</a></td> 
   <td>Authoring und Veröffentlichen</td> 
   <td>Erforderlich für die E-Mail-Kommunikation.</td> 
  </tr> 
  <tr> 
   <td><a href="#xss">Außerkraftsetzen der standardmäßigen XSS-Konfiguration</a></td> 
   <td>Veröffentlichung</td> 
   <td>Wird verwendet, um $-, {- und }-Zeichen zu überschreiben, die von xss security blockiert werden.</td> 
  </tr> 
  <tr> 
   <td><a href="#aemds">Einstellungen für AEM DS konfigurieren</a></td> 
   <td>Autor</td> 
   <td>Konfigurieren Sie AEM DS zum Senden von Formularen in der Veröffentlichungsinstanz und zum Verarbeiten von Workflows in der Authoring-Instanz.</td> 
  </tr> 
  <tr> 
   <td><a href="#refsite">Referenz-Site-Pakete bereitstellen</a></td> 
   <td>Autor</td> 
   <td>Stellen Sie Referenz-Site-Pakete in der Authoring-Instanz von AEM Forms bereit.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/setup-reference-sites.md#optional-import-sample-data-into-microsoft-dynamics">Importieren von Beispieldaten in Microsoft Dynamics</a></td> 
   <td>Authoring und Veröffentlichen</td> 
   <td>Musterdaten für Kreditkartenantrag, HypoHypothekenantrag und Anleitung zum Bedienen von Wohnversicherungsanträgen importieren</td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/setup-reference-sites.md#configure-oauth-cloud-service-for-microsoft-dynamics">Konfigurieren des OAuth-Cloud-Dienst für Microsoft Dynamics</a></td> 
   <td>Authoring und Veröffentlichen</td> 
   <td>Konfigurieren Sie den OAuth Cloud-Dienst in AEM Forms, um die Kommunikation zwischen AEM Forms und Microsoft Dynamics zu ermöglichen. </td> 
  </tr> 
  <tr> 
   <td><a href="#scheduler">Adobe Sign Scheduler konfigurieren</a></td> 
   <td>Authoring und Veröffentlichen<br />  </td> 
   <td>Ändern Sie die Konfiguration des Schedulers, sodass der Status alle zwei Minuten überprüft wird.</td> 
  </tr> 
  <tr> 
   <td><a href="#sign-service">Cloud-Service von Adobe Sign für Referenz-Site konfigurieren</a></td> 
   <td>Authoring und Veröffentlichen<br />  </td> 
   <td>Eine Konfiguration, die Referenz-Site-Pakete enthält und mit gültigen Anmeldeinformationen neu konfiguriert werden muss.</td> 
  </tr> 
  <tr> 
   <td><a href="#anonymous">Allgemeinen Forms-Konfigurationsdienst für anonyme Benutzer konfigurieren</a></td> 
   <td>Veröffentlichung</td> 
   <td>Die Konfiguration ermöglicht das Senden, Signieren und Dokument der Datensatzgenerierung für anonyme Benutzer.</td> 
  </tr> 
  <tr> 
   <td><a href="#fdm">REST-Dienst-Swagger-Datei für das Formulardatenmodell ändern</a></td> 
   <td>Authoring und Veröffentlichen<br /> </td> 
   <td>Ändern Sie den Dienst für Ihre Umgebung.</td> 
  </tr> 
 </tbody> 
</table>

## Installieren und Konfigurieren von AEM Forms {#install-and-configure-aem-forms}

Installieren und stellen Sie AEM Forms wie unter [Installieren und Konfigurieren von AEM Forms auf OSGi](/help/forms/using/installing-configuring-aem-forms-osgi.md) beschrieben bereit.

>[!NOTE]
>
>Konfigurieren Sie Replikations- und Rückwärtsreplikations-Agents, wenn mehrere Veröffentlichungsinstanzen vorhanden sind oder Authoring- und Veröffentlichungsinstanz sich auf verschiedenen Computern befinden.

## SSL-Konfiguration  {#ssl}

Die SSL-Konfiguration ist für die Kommunikation mit den Adobe Sign-Servern erforderlich. Ausführliche Anweisungen finden Sie unter [Aktivieren von HTTP über SSL](/help/sites-administering/ssl-by-default.md).

>[!CAUTION]
>
>Konfigurieren Sie SSL nicht für den Ordner `/etc/map`.

## Konfigurieren der Day CQ Link Externalizer-Konfiguration {#externalizer}

In AEM ist der **Externalizer** ein OSGI-Dienst, mit dem Sie einen Ressourcenpfad (z. /path/to/my/page) in eine externe und absolute URL (z. B. https://www.mycompany.com/path/to/my/page) hinein, indem dem Pfad ein vorkonfiguriertes DNS vorangestellt wird. Siehe[ Auslagern von URLs](/help/sites-developing/externalizer.md).

>[!CAUTION]
>
>Wenn Sie ein selbstsigniertes Zertifikat für SSL verwenden, lagern Sie nicht auf eine HTTPS-URL aus.
>
>Verwenden Sie außerdem für den lokalen Server nicht dessen Hostnamen, sondern „localhost“.

Führen Sie folgende Schritte für die Autoren- und Veröffentlichungsinstanzen aus: 

1. Gehen Sie zu OSGi-Konfiguration unter https://&lt;*Hostname>*:*Anschluss>*/system/console/configMgr.
1. Suchen und tippen Sie auf **[!UICONTROL Day CQ Link Externalizer]** Konfiguration.

   Der Day CQ Link Externalizer-Dialog wird zur Bearbeitung der Konfiguration geöffnet.

1. Im Day CQ Link Externalizer-Dialog im Domänefeld:

   * Geben Sie in der Autoreninstanz eine Veröffentlichungs-URL an, auf die über ein externes System zugegriffen werden kann. Verwenden Sie beispielsweise einen Hostnamen oder einen Veröffentlichungswebserver.
   * Geben Sie in der Veröffentlichungsinstanz sowohl die Authoring- als auch die Veröffentlichungs-URL an.

1. Stellen Sie sicher, dass im Autor- und Veröffentlichungsmodus die lokale Server-URL im Domänefeld angegeben ist.
1. Tippen Sie auf **[!UICONTROL Speichern]**. Warten Sie kurz, bis alle Dienste neu gestartet wurden. 

## Konfigurieren des Day CQ Mail Service  {#cqmail}

Referenzsiteimplementierung erfordert, dass E-Mails an Beispielbenutzer gesendet werden, wenn diese Formulare ausfüllen und einreichen. Beim Konfigurieren von Day CQ Mail Service können Sie SMTP-Dienstdetails angeben, um automatisierte E-Mails an Kunden zu senden. Siehe [Konfigurieren von E-Mail-Benachrichtigungen](/help/sites-administering/notification.md).

Führen Sie die folgenden Schritte aus, um einen Mail-Dienst im Veröffentlichungsmodus zu konfigurieren:

1. Gehen Sie zu OSGi-Konfiguration unter https://&lt;*Hostname>*:*Anschluss>*/system/console/configMgr.
1. Suchen und tippen Sie auf **[!UICONTROL Day CQ Mail Service]**, um ihn zur Konfiguration zu öffnen.
1. Geben Sie den SMTP-Server-Hostnamen und Port-Werte an.
1. Tippen Sie auf **[!UICONTROL Speichern]**.

>[!NOTE]
>
>Sie können den SMTP-Dienst Ihres Unternehmens oder einen öffentlichen Dienst wie Gmail verwenden. Informationen zum Konfigurieren des SMTP-Diensts finden Sie in der Dokumentation zum SMTP-Dienst.

## Außerkraftsetzen der standardmäßigen XSS-Konfiguration  {#xss}

Die E-Mail-Vorlagen für die We.Finance-Referenz-Site enthalten personalisierte Links in E-Mails. Diese Verknüpfungen haben Platzhalter wie `${placeholder}`. Diese Platzhalter werden durch tatsächliche Werte ersetzt, bevor E-Mails versendet werden. Die standardmäßige XSS-Schutzkonfiguration für AEM erlaubt keine (**{ }**) in der URL und im HTML-Inhalt. Sie können jedoch die Standardkonfiguration außer Kraft setzen, indem Sie folgende Schritte im Veröffentlichungsmodus ausführen: 

1. Kopieren Sie `/libs/cq/xssprotection/config.xml` nach `/apps/cq/xssprotection/config.xml`.
1. Öffnen Sie `/apps/cq/xssprotection/config.xml`.
1. Ändern Sie im Abschnitt `common-regexps` den Eintrag `onsiteURL` wie folgt und speichern Sie die Datei.

   `<regexp name="onsiteURL" value="([\p{L}\p{N}\\\.\#@\$\{\}%\+&;\-_~,\?=/!\*\(\)]*|\#(\w)+)"/>`

>[!NOTE]
>
>Geschweifte Klammern (**{}**) sind in den akzeptierten Zeichen in der URL im HTML-Inhalt inbegriffen.

Nach dem Konfigurieren des SMTP-Servers, versuchen Sie, ein Formular nach dem Sarah Rose-Beispiel auszufüllen, und speichern Sie es als Entwurf. Wenn Sie es als Entwurf speichern, erhalten Sie eine Option, um den Entwurf über die E-Mail zu empfangen. Wenn Sie beim Tippen auf **E-Mail senden** eine E-Mail mit einem Link zum Entwurf des Antrags erhalten, war Ihre E-Mail-Konfiguration erfolgreich. Stellen Sie sicher, dass Sie sich mit den Anmeldedaten von Sarah anmelden, um den Entwurf anzuzeigen.

## Einstellungen für AEM DS konfigurieren  {#aemds}

AEM Einstellungen des DS-Dienstes sind in der Veröffentlichungsinstanz für die E-Mail-Kommunikation in den Anwendungsfällen der Referenz-Website erforderlich. Ausführliche Anweisungen zum Konfigurieren AEM DS-Diensts für die Veröffentlichungsinstanz finden Sie unter [AEM DS-Einstellungen konfigurieren](/help/forms/using/configuring-the-processing-server-url-.md).

Geben Sie für AEM Forms-Referenz-Sites im AEM DS-Einstellungsdienst die URL des Veröffentlichungsservers anstelle der URL des Verarbeitungsservers an.

>[!CAUTION]
>
>Setzen Sie `/lc` nicht in die URL des Verarbeitungsservers, wenn Sie sie für AEM Forms OSGi konfigurieren.

## Referenz-Site-Pakete bereitstellen {#refsite}

Installieren Sie die folgenden Referenzstandortpakete mithilfe der Software Distribution.

* [AEM-FORMS-6.4-FSI-REF-SITE](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-FSI-REF-SITE)
* [AEM-FORMS-6.4-GOV-REF-SITE](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-GOV-REF-SITE)

Weitere Informationen zur Verwendung von Paketen finden Sie unter [Arbeiten mit Paketen](/help/sites-administering/package-manager.md).

Nachdem Sie die Pakete installiert und den Autoren- und Veröffentlichungsmodus begonnen haben, besuchen Sie die folgenden URLs in Ihrem Browser:

* `https://[server]:[port]/wegov`
* `https://[server]:[port]/wefinance`

Wenn die Installation erfolgreich abläuft, können Sie auf die Startseiten der Referenz-Sites We.Gov und We.Finance zugreifen.

## (Optional) Importieren von Musterdaten in Microsoft Dynamics {#optional-import-sample-data-into-microsoft-dynamics}

Die Referenzseiten für die Hypothekenanwendung und die Anwendung für die automatische Versicherung sind für die Verwendung von Datensätzen von Microsoft Dynamics konfiguriert. Das Referenz-Website-Paket installiert eine benutzerdefinierte Entität und Beispieldatensätze, die Sie in Microsoft Dynamics importieren können, um die Referenz-Website auszuführen. Führen Sie die folgenden Schritte aus, um die Musterdaten zu migrieren und einzurichten:

So importieren Sie die benutzerdefinierte Entität für die Anwendung für die automatische Versicherung:

1. Laden Sie das Lösungspaket **WeFinanceAutoInsurance_1_0.zip** von `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/WeFinanceAutoInsurance_1_0.zip` auf Ihre AEM Autoreninstanz herunter.
1. Wechseln Sie in Ihrer Microsoft Dynamics-Instanz zu **[!UICONTROL Lösungen]** im Menü **[!UICONTROL Einstellungen]** und klicken Sie auf **[!UICONTROL Importieren]**. Wählen Sie das Paket aus und importieren Sie es.

So importieren Sie die benutzerdefinierte Entität für die Anwendung für die automatische Versicherung:

1. Laden Sie das Paket **AEMFormsFSIRefsite_1_0.zip** von https://[author]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/AEMFormsFSIRefsite_1_0.zip herunter. Wählen Sie das Paket aus und importieren Sie es.

1. Wechseln Sie in Ihrer Microsoft Dynamics-Instanz zu **[!UICONTROL Lösungen]** im Menü **[!UICONTROL Einstellungen]** und klicken Sie auf **[!UICONTROL Importieren]**. Wählen Sie das Paket aus und importieren Sie es.

Importieren der Kunden- und Versicherungspolice-Datensätze:

1. Laden Sie die Datendateien **We.Finance Customers.csv, We.Finance Auto Insurance Renewals.csv** und **Home mortgage** von den folgenden Speicherorten in Ihrer AEM Autoreninstanz herunter:

   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Customers.csv`
   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Auto Insurance Renewals.csv`
   * `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/Sarah%20Rose%20Contact.csv`

1. Führen Sie in Ihrer Microsoft Dynamics-Instanz die folgenden Schritte aus:

   * Gehen Sie zu **[!UICONTROL Vertrieb > Wir.Finance Customers]** und klicken Sie auf **[!UICONTROL Import]**.
   * Gehen Sie zu **[!UICONTROL Vertrieb > Wir.Finance Auto Insurance]** und klicken Sie auf **[!UICONTROL Import]**.
   * Gehen Sie zu **[!UICONTROL Verkauf > Wir.Finance Home Mortgage]** und klicken Sie auf **[!UICONTROL Import]**.

## Konfigurieren des OAuth-Cloud-Dienst für Microsoft Dynamics {#configure-oauth-cloud-service-for-microsoft-dynamics}

Konfigurieren Sie den OAuth Cloud-Dienst in AEM Forms, um die Kommunikation zwischen AEM Forms und Microsoft Dynamics zu ermöglichen. Führen Sie die folgenden Schritte aus, um den OAuth-Cloud Service in AEM Autoren- und Veröffentlichungsinstanzen zu konfigurieren:

1. Wechseln Sie in AEM Autoreninstanz zu **[!UICONTROL Tools > Cloud Services > Data Sources > global]**. Tippen Sie auf das Symbol **[!UICONTROL Refsite Dynamics Integration]** und dann auf **[!UICONTROL Eigenschaften]**.
1. Navigieren Sie zum Microsoft Azure Active Directory-Konto. Fügen Sie die kopierte URL der Cloud-Dienstkonfiguration in der Einstellung **[!UICONTROL Antwort-URL]** URL-Einstellung für Ihre registrierte Anwendung hinzu. Speichern Sie die Konfiguration.
1. Geben Sie auf der Registerkarte Authentifizierungseinstellungen für Ihre Microsoft Dynamics-Instanz **[!UICONTROL Dienststamm]**, **[!UICONTROL Client-ID]**, **[!UICONTROL Clientgeheimnis]** und **[!UICONTROL Ressourcen-URL]** an. Klicken Sie auf **[!UICONTROL Mit OAuth]** verbinden, um zur Microsoft Dynamics Anmeldeseite umzuleiten.
1. Geben Sie Ihre Anmeldedaten ein. Nach der Anmeldung werden Sie zur Konfigurationsseite des AEM Forms Cloud-Dienstes weitergeleitet. Klicken Sie auf **[!UICONTROL Speichern und schließen]**. Die Cloud-Dienstkonfiguration wird gespeichert.
1. Gehen Sie zu **[!UICONTROL Forms > Datenintegrationen > We.Finance]**. Wählen Sie Auto Insurance (Dynamics) und klicken Sie auf Edit. Microsoft Dynamics-Entitäten werden unter der Registerkarte Data Sources aufgeführt. Warten Sie, bis alle Entitäten von Microsoft Dynamics abgerufen und unter der Registerkarte &quot;Datenquellen&quot;aufgelistet wurden.
1. Wählen Sie die **[!UICONTROL AutoInsuranceRenewal-Entität]** und klicken Sie auf **[!UICONTROL Testmodellobjekt]**. Geben Sie im Abschnitt &quot;Eingabeanforderung&quot;den Wert für die Kunden-ID als &quot;900001&quot;an und klicken Sie auf **[!UICONTROL Test]**. Im Bereich &quot;Ausgabe&quot;werden die Datensätze angezeigt, die von Microsoft Dynamics für die Kunden-ID 900001 abgerufen wurden.
1. Geben Sie im Abschnitt &quot;Eingabeanforderung&quot;den Wert für die Kunden-ID als &quot;900001&quot;an und klicken Sie auf **[!UICONTROL Test]**. Im Bereich &quot;Ausgabe&quot;werden die Datensätze angezeigt, die von Microsoft Dynamics für die Kunden-ID 900001 abgerufen wurden.
1. Wiederholen Sie die Schritte 1 bis 6 für die Veröffentlichungsinstanz.

## Adobe Sign Scheduler konfigurieren {#scheduler}

Führen Sie die folgenden Schritte sowohl auf der Authoring- als auch auf der Veröffentlichungsinstanz aus:

1. Wechseln Sie zu AEM Web Configuration Console unter `https://[server]:[host]/system/console/configMgr`.
1. Suchen Sie nach **[!UICONTROL Adobe Sign Configuration Service]** und tippen Sie darauf, um ihn zur Konfiguration zu öffnen.
1. Konfigurieren Sie den Ausdruck **[!UICONTROL Statusupdate-Planung]** als **0/2 &amp;ast; &amp;ast; &amp;ast; ?**.

   >[!NOTE]
   >
   >In der oben gezeigten Konfiguration des Planers wird der Status des Adobe Sign-Dienstes alle zwei Minuten überprüft.

1. Tippen Sie auf **[!UICONTROL Speichern]**.

## Cloud-Service von Adobe Sign für Referenz-Site konfigurieren  {#sign-service}

Führen Sie die folgenden Schritte sowohl auf der Authoring- als auch auf der Veröffentlichungsinstanz aus:

1. Gehen Sie zu **[!UICONTROL Tools > Cloud Services > Adobe Sign > global]**. Wählen Sie **[!UICONTROL AEM Forms Reference Site Sign]** und tippen Sie auf **[!UICONTROL Properties]**.

   >[!CAUTION]
   >
   >Stellen Sie sicher, dass die URL https://[host]:[ssl_port]/mnt/overlay/adobesign/cloudservices/adobesign/properties.html zur Liste der Umleitungs-URL der OAuth-Konfiguration der Adobe Sign API-Anwendung hinzugefügt wird.

1. Geben Sie Client-ID und Secret der OAuth-Konfiguration für Adobe Sign an.
1. (Optional) Wählen Sie die Option **[!UICONTROL Adobe Sign für Anlagen auch aktivieren]** und tippen Sie auf **[!UICONTROL Verbindung zu Adobe Sign]** herstellen. Dadurch werden Dateien, die an ein adaptives Formular angehängt sind, an das dazugehörige Adobe Sign-Dokument angehängt, das zum Signieren übermittelt wird.
1. Tippen Sie auf **[!UICONTROL Verbindung zu Adobe Sign]** herstellen und melden Sie sich mit Ihren Adobe Sign-Anmeldedaten an.

## Allgemeinen Konfigurationsdienst von Forms konfigurieren {#anonymous}

Führen Sie in der Veröffentlichungsinstanz die folgenden Schritte aus, um anonymen Benutzern den Zugriff zu ermöglichen:

1. Wechseln Sie zu AEM Web Configuration Console unter `https://[server]:[port]/system/console/configMgr`.
1. Suchen Sie den Forms Common Configuration Service ]**und tippen Sie darauf, um ihn zur Konfiguration zu öffnen.**[!UICONTROL 
1. Konfigurieren Sie das Feld **[!UICONTROL Allow]** für **[!UICONTROL All Users]**.
1. Tippen Sie auf **[!UICONTROL Speichern]**.

## REST-Dienst für Formulardatenmodell ändern  {#fdm}

Führen Sie die folgenden Schritte sowohl auf der Authoring- als auch auf der Veröffentlichungsinstanz aus:

1. Wechseln Sie zu CRXDE unter `https://[server]:[port]/crx/de/index.jsp`.
1. Navigieren Sie zu **/conf/global/settings/cloudconfigs/fdm/roi-rest/jcr:content/swaggerFile** und öffnen Sie die Swagger-Datei.
1. Aktualisieren Sie die Host- und Anschlusseinstellungen gemäß Ihrer Umgebung.
1. Speichern Sie die Einstellungen.
1. (**Nur Autoreninstanz**) Gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Datenquellen]** > **[!UICONTROL global]**. Wählen Sie **[!UICONTROL roi-rest]** und tippen Sie auf **[!UICONTROL Eigenschaften]**. Tippen Sie auf **[!UICONTROL Authentifizierungseinstellungen]** und setzen Sie **[!UICONTROL Authentifizierungstyp]** auf **[!UICONTROL Grundlegende Authentifizierung]**. Geben Sie `admin`/ `admin`als Benutzernamen/Kennwort für den Zugriff auf den Dienst an. Tippen Sie auf **[!UICONTROL Speichern und Schließen]**.

## Integration mit Marketing Cloud {#integrate-with-marketing-cloud}

Sie können das AEM Forms mit Adobe Analytics und Adobe Target integrieren. Während Adobe Analytics Ihnen dabei hilft, Berichte zu erstellen und die Leistung adaptiver Formulare zu analysieren, hilft Ihnen Adobe Target dabei, personalisierte Erlebnisse bereitzustellen und A/B-Tests für adaptive Formulare durchzuführen.

Führen Sie die folgenden Schritte aus, um Adobe Analytics und Adobe Target in AEM Forms zu konfigurieren.

### Konfigurieren Sie Analytics {#configure-adobe-analytics}

Anhand von AEM Forms-Integration und Adobe Analytics können Sie verfolgen und analysieren, wie Ihre Kunden mit Ihren Formularen und Dokumenten interagieren. Es hilft Ihnen, Problembereiche zu identifizieren und zu beheben und zu handeln, um das Konversionsrate zu erhöhen.

Um diese Funktion auf der Referenz-Website zu nutzen, konfigurieren Sie Ihr Analytics-Konto, wie beschrieben unter [Konfigurieren von Analysen und Berichten](/help/forms/using/configure-analytics-forms-documents.md).

Zur Erstellung eines Berichts werden Seed-Daten mit den Referenz-Sites gebündelt. Bevor Sie Seed-Daten verwenden, führen Sie die folgenden Schritte aus:

1. Stellen Sie sicher, dass die Analysekonfigurationen We.Finance und We.Gov in den AEM Cloud-Diensten verfügbar sind. Sie können Cloud-Dienste auf eine der folgenden Arten finden:

   * Navigieren Sie zu **[!UICONTROL Cloud Services>Ältere Cloud Services]** oder navigieren Sie zu https://&lt;host>:&lt;port>/libs/cq/core/content/tools/cloudservices.html.
   * Klicken Sie auf der Seite **[!UICONTROL Cloud Services]** unter **[!UICONTROL Adobe Analytics]** auf `Show Configurations`. Sie können die Konfigurationen We.Finance und We.Gov sehen. Klicken Sie auf „Öffnen“, um die Konfiguration zu öffnen. Klicken Sie auf der Konfigurationsseite auf **[!UICONTROL Bearbeiten]**. Geben Sie gültige Firma, Benutzernamen, Shared Secret (Kennwort) und Data Center ein und klicken Sie auf **[!UICONTROL Verbindung zu Analytics]** herstellen. Nachdem Sie das Dialogfeld Verbindung erfolgreich abgeschlossen haben, klicken Sie im Konfigurationsdialogfeld auf **[!UICONTROL OK]**. Konfigurieren Sie das Framework unter der Analytics-Konfiguration, wie unter [Konfigurieren von Analytics und Reports](/help/forms/using/configure-analytics-forms-documents.md) beschrieben.

1. Navigieren Sie zu https://&lt;*host*:&lt;*port*>/system/console/configMgr und führen Sie folgende Schritte aus:

   * Suchen Sie auf der Seite **[!UICONTROL Web-Konsolenkonfiguration]** nach **[!UICONTROL AEM Forms Analytics-Konfiguration]** und klicken Sie darauf.
   * Wählen Sie im Feld **[!UICONTROL SiteCatalyst Framework]** des Dialogfelds &quot;AEM Forms Analytics-Konfiguration&quot;die Option we-finance(we-finance) oder we-gov(we-gov).
   * Klicken Sie auf **[!UICONTROL Speichern]** und aktualisieren Sie die Seite.

1. Navigieren Sie zum Forms Manager unter https://&lt;Host>:&lt;Anschluss>/aem/forms und führen Sie die folgenden Schritte aus:

   * Öffnen Sie den Ordner &quot;We.Finance&quot;oder &quot;We.Gov&quot;und wählen Sie das Formular aus, für das Sie den Bericht anzeigen möchten.
   * Klicken Sie in der Aktions-Symbolleiste auf Analyse aktivieren. Nachdem Sie die Analyse für das Formular aktiviert haben, klicken Sie auf Analysebericht. Sie können sehen, dass ein leerer Bericht generiert wurde. Nachdem ein leerer Bericht generiert wurde, müssen Sie Seed-Daten bereitstellen, die mit refsite-Paket versandt werden, um einen Analysebericht für Demozwecke zu erstellen.

   Referenz-Websites bieten dem Analytics-Berichte Startdaten für Kreditkarten-, Hypotheken- und Kindergeld-Anwendungsfälle. Informationen zur Konfiguration der Seed-Daten finden Sie unter Umgehung der Website [We.Finance-Referenz](/help/forms/using/finance-reference-site-walkthrough.md)- und [We.Gov-Referenz-Website - Umgehungslösung](/help/forms/using/gov-reference-site-walkthrough.md).

### Target konfigurieren {#configure-target}

Die Referenz-Website zeigt die Integration von AEM Forms mit Adobe Target, einer Anwendung, die Ihnen erlaubt, zielgruppenorientierten und personalisierten Inhalt in adaptive Dokumente aufzunehmen. Auch können A/B-Tests für adaptive Formulare erstellt werden. 

Um die Integration auf der Referenz-Website zu testen, führen Sie folgende Schritte aus, um Target in AEM zu konfigurieren:

1. Beginn Sie den Autor quickstart mit dem jvm-Argument `-Dabtesting.enabled=true`, um A/B-Tests auf dem Server zu aktivieren.

   **Hinweis**: Wenn die AEM-Instanz auf JBoss ausgeführt wird, das als Dienst aus der Turnkey-Installation gestartet wird, fügen Sie den  `-Dabtesting.enabled=true` Parameter in den folgenden Eintrag in der  `jboss\bin\standalone.conf.bat` Datei ein:

   `set "JAVA_OPTS=%JAVA_OPTS% -Dadobeidp.serverName=server1 -Dfile.encoding=utf8 -Djava.net.preferIPv4Stack=true -Dabtesting.enabled=true"`

1. Zugriff auf https://&lt;*Hostname*:&lt;*Anschluss*>/libs/cq/core/content/tools/cloudservices.html.

1. Klicken Sie im Abschnitt **[!UICONTROL Adobe Target]** auf **[!UICONTROL Konfigurationen anzeigen]**. Die Konfiguration der Web.Finance-Zielgruppe ist verfügbar. Klicken Sie auf „Öffnen“, um die Konfiguration zu öffnen. Klicken Sie auf der Konfigurationsseite auf **[!UICONTROL Bearbeiten]**. Das Dialogfeld **[!UICONTROL Komponente bearbeiten]** für die Konfiguration wird geöffnet.

1. Geben Sie Ihren Client-Code, die E-Mail und das Kennwort an, die mit Ihrem Target-Konto verknüpft sind. Wählen Sie den API-Typ als **[!UICONTROL REST]**.
1. Klicken Sie auf **[!UICONTROL Verbindung mit Adobe-Target herstellen]**. Klicken Sie nach erfolgreicher Konfiguration des Kontos auf **[!UICONTROL OK]**. Sie können sehen, dass die gepackte Konfiguration über ein Zielgruppe Framework verfügt.

1. Gehen Sie zu https://&lt;*Hostname*:&lt;*Anschluss*>/system/console/configMgr.

1. Klicken Sie auf **[!UICONTROL AEM Forms Target-Konfiguration]**.
1. Wählen Sie ein Zielgruppe-Framework.
1. Geben Sie im Feld **[!UICONTROL Target-URLs]** die URL für AEM Forms ein. Beispiel: https://&lt;*Hostname*:&lt;*Anschluss*>.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

Anwendungsfälle für Kreditkartenanträge und Hypothekenanträge zeigen, wie A/B-Tests durchgeführt werden und wie ein Bericht zu Demozwecken dargestellt wird. exemplarische Vorgehensweisen finden Sie unter [Umgehungslösung der Referenz-Website für We.Finance](/help/forms/using/finance-reference-site-walkthrough.md).

## Nächster Schritt {#next-step}

Jetzt können Sie die Referenz-Website erkunden. Weitere Informationen zum Arbeitsablauf auf Referenzseiten finden Sie unter:

* [Schrittweise Anleitung zur We.Finance-Referenz-Site](/help/forms/using/finance-reference-site-walkthrough.md)
* [Schrittweise Anleitung zur We.Gov-Referenz-Site](/help/forms/using/gov-reference-site-walkthrough.md)

* [Schrittweise Anleitung zur Referenz-Site für Mitarbeiter-Self-Service](/help/forms/using/employee-self-service-reference-site.md)

