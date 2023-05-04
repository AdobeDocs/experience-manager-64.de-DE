---
title: Einrichten und Konfigurieren von AEM Forms-Referenz-Sites
seo-title: Set up and configure AEM Forms reference sites
description: AEM Forms-Referenz-Sites zeigen, wie Sie mit AEM Forms End-to-End-Workflows in einer Organisation implementieren können.
seo-description: AEM Forms reference sites showcase how you can use AEM Forms to implement end-to-end workflow in an organization.
uuid: 087d58a1-d84e-49ac-a82d-4e7fc708f00f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 2feb4a9c-57ad-4c6b-a572-0047bc409bbb
exl-id: 9c5d956c-06bc-4428-afcd-02b4f81b802f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2947'
ht-degree: 5%

---

# Einrichten und Konfigurieren von AEM Forms-Referenz-Sites {#set-up-and-configure-aem-forms-reference-sites}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

AEM Forms bietet eine Referenz-Site-Implementierung, um zu veranschaulichen, wie AEM Forms Finanzdienstleistungsbranche und Regierungseinrichtungen dabei unterstützt, komplexe Transaktionen in einfache digitale Erlebnisse umzuwandeln, jederzeit und auf jedem Gerät.

We.Finance- und We.Gov-Referenz-Sites zeichnen reale Nutzungsszenarien aus, um mit bestehenden und potenziellen Kunden zu interagieren, von der Erstkontakt-Phase bis hin zur Verwaltung von Korrespondenzen und Transaktionen auf personalisierte und kostengünstige Weise.

Mithilfe der Referenz-Sites können Sie die folgenden wichtigen Funktionen von AEM Forms erkunden und präsentieren.

* Vereinfachtes Authoring mit ansprechenden und responsiven adaptiven Formularen und interaktiver Kommunikation.
* Interaktive Kommunikation zur Erstellung interaktiver, personalisierter und responsiver Kundenkommunikation, die sich an die Geräteeinstellung und das Layout anpasst.
* Datenintegration zum Herstellen einer Verbindung zu unterschiedlichen Datenquellen zum Vorausfüllen und Senden von Formulardaten über ein Formulardatenmodell.
* Forms-Workflow zur Automatisierung von Geschäftsprozessen und Workflows.
* Erweiterte Funktionen zur Verwaltung und Verarbeitung von Benutzerdaten.
* Integration mit Acrobat Sign zum sicheren Signieren und Senden adaptiver Formulare.
* Integration mit Adobe Target, um gezielte Empfehlungen bereitzustellen und A/B-Tests durchzuführen, um den ROI aus einem Formular zu maximieren.
* Integration mit Adobe Analytics, um die Leistung eines Formulars oder einer Kampagne zu messen und fundierte Entscheidungen zu treffen.
* Erweiterte Funktionen zum Ausfüllen von Formularen.

Die Referenz-Sites bieten wiederverwendbare Assets, die Sie als Vorlagen verwenden können, um eigene Assets zu erstellen.

* Integration mit Acrobat Sign zum sicheren Signieren und Senden adaptiver Formulare.

* Integration mit Acrobat Sign zum sicheren Signieren und Senden adaptiver Formulare.

## Voraussetzungen und Schritte zum Einrichten von Referenzsites {#prerequisites-and-steps-to-set-up-reference-sites}

Bevor Sie die Referenz-Website einrichten, stellen Sie Folgendes sicher:

* **AEM Grundlagen**

   AEM Schnellstart, AEM Forms Add-On-Paket und Referenz-Website-Pakete. Siehe [AEM Forms-Versionen](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html) für Details zu Add-On- und Referenz-Sites-Paketen.

* **SMTP-Dienst**
Sie können einen beliebigen SMTP-Dienst verwenden.

* **Acrobat Sign-Entwicklerkonto und Acrobat Sign-API-Anwendung**

   Um digitale Signaturfunktionen zu verwenden, ist ein Acrobat Sign-Entwicklerkonto erforderlich. Siehe [Acrobat Sign](https://acrobat.adobe.com/de/de/why-adobe/developer-form.html).

* Eine laufende Instanz von Microsoft Dynamics 365 zur Integration mit AEM Forms. Um die Referenz-Website auszuführen, importieren Sie die Beispieldaten in die Microsoft Dynamics-Instanz, um die auf der Referenz-Website verwendete interaktive Kommunikation im Voraus auszufüllen.
* Eine laufende Instanz von AEM 6.4 mit dem Forms-Add-On-Paket. Weitere Informationen finden Sie unter [Installieren und Konfigurieren von AEM Forms](installing-configuring-aem-forms-osgi.md).

Führen Sie die folgenden Schritte in der empfohlenen Reihenfolge aus, um die Referenz-Sites einzurichten und zu konfigurieren.

<table> 
 <tbody> 
  <tr> 
   <th><strong>Schritt</strong></th> 
   <th><strong>Konfigurieren</strong></th> 
   <th><strong>Anmerkungen</strong></th> 
  </tr> 
  <tr> 
   <td><a href="#installaemforms">Installieren und Konfigurieren von AEM Forms</a></td> 
   <td>Authoring und Veröffentlichen</td> 
   <td>Installieren und konfigurieren Sie AEM Forms-Autoren- und Veröffentlichungsinstanzen.</td> 
  </tr> 
  <tr> 
   <td><a href="#ssl">SSL konfigurieren</a></td> 
   <td>Authoring und Veröffentlichen<br /> </td> 
   <td>Aktivieren Sie HTTP über SSL für sichere Kommunikation mit Acrobat Sign.</td> 
  </tr> 
  <tr> 
   <td><p><a href="#externalizer">Konfigurieren der Day CQ Link Externalizer-Konfiguration</a></p> </td> 
   <td>Authoring und Veröffentlichen<br /> </td> 
   <td><p>Anwendungsfälle der Referenz-Website liefern E-Mails für verschiedene Transaktionen. Diese Einstellung ist für den Versand von Newslettern per E-Mail erforderlich. Dadurch wird sichergestellt, dass URLs und Bilder auf die Veröffentlichungsinstanz verweisen. </p> </td> 
  </tr> 
  <tr> 
   <td><a href="#cqmail">Konfigurieren des Day CQ Mail Service</a></td> 
   <td>Authoring und Veröffentlichen</td> 
   <td>Erforderlich für die E-Mail-Kommunikation.</td> 
  </tr> 
  <tr> 
   <td><a href="#xss">Außerkraftsetzen der standardmäßigen XSS-Konfiguration</a></td> 
   <td>Veröffentlichen </td> 
   <td>Wird verwendet, um $-, {- und }-Zeichen zu überschreiben, die von xss security blockiert werden.</td> 
  </tr> 
  <tr> 
   <td><a href="#aemds">AEM DS-Einstellungen konfigurieren</a></td> 
   <td>Autor</td> 
   <td>Konfigurieren Sie AEM DS für die Formularübermittlung in der Veröffentlichungsinstanz und die Verarbeitungs-Workflows in der Autoreninstanz.</td> 
  </tr> 
  <tr> 
   <td><a href="#refsite">Bereitstellen von Referenz-Sites-Paketen</a></td> 
   <td>Autor</td> 
   <td>Stellen Sie Referenzsites-Pakete in der AEM Forms-Autoreninstanz bereit.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/setup-reference-sites.md#optional-import-sample-data-into-microsoft-dynamics">Importieren von Beispieldaten in Microsoft Dynamics</a></td> 
   <td>Authoring und Veröffentlichen</td> 
   <td>Beispieldaten für Kreditkartenantrag, Hypothekenantrag und Anleitung für Hausversicherungsanträge importieren</td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/setup-reference-sites.md#configure-oauth-cloud-service-for-microsoft-dynamics">Konfigurieren des OAuth-Cloud-Service für Microsoft Dynamics</a></td> 
   <td>Authoring und Veröffentlichen</td> 
   <td>Konfigurieren Sie den OAuth-Cloud-Dienst in AEM Forms, um die Kommunikation zwischen AEM Forms und Microsoft Dynamics zu aktivieren. </td> 
  </tr> 
  <tr> 
   <td><a href="#scheduler">Konfigurieren des Acrobat Sign-Planers</a></td> 
   <td>Authoring und Veröffentlichen<br /> </td> 
   <td>Ändern Sie die Konfiguration der Planung, um den Status alle zwei Minuten zu überprüfen.</td> 
  </tr> 
  <tr> 
   <td><a href="#sign-service">Konfigurieren von Reference Site Acrobat Sign Cloud Service</a></td> 
   <td>Authoring und Veröffentlichen<br /> </td> 
   <td>Eine Konfiguration, die mit Referenz-Sites-Paketen geliefert wird und eine Neukonfiguration mit gültigen Anmeldeinformationen erfordert.</td> 
  </tr> 
  <tr> 
   <td><a href="#anonymous">Konfigurieren des allgemeinen Forms-Konfigurationsdienstes für anonyme Benutzer</a></td> 
   <td>Veröffentlichen </td> 
   <td>Die Konfiguration ermöglicht die Erstellung von Signaturen und Dokumenten aus Datensätzen für anonyme Benutzer.</td> 
  </tr> 
  <tr> 
   <td><a href="#fdm">REST Service Swagger-Datei für Formulardatenmodell ändern</a></td> 
   <td>Authoring und Veröffentlichen<br /> </td> 
   <td>Ändern Sie den Dienst für Ihre Umgebung.</td> 
  </tr> 
 </tbody> 
</table>

## Installieren und Konfigurieren von AEM Forms {#install-and-configure-aem-forms}

Installieren und Bereitstellen von AEM Forms wie beschrieben unter [Installieren und Konfigurieren von AEM Forms on OSGi](/help/forms/using/installing-configuring-aem-forms-osgi.md).

>[!NOTE]
>
>Konfigurieren Sie Replikations- und Agenten für die Rückwärtsreplikation, wenn mehrere Veröffentlichungsinstanzen vorhanden sind oder sich Autoren- und Veröffentlichungsinstanzen auf verschiedenen Computern befinden.

## SSL konfigurieren {#ssl}

Für die Kommunikation mit Acrobat Sign-Servern ist eine SSL-Konfiguration erforderlich. Ausführliche Anweisungen finden Sie unter [Aktivieren von HTTP über SSL](/help/sites-administering/ssl-by-default.md).

>[!CAUTION]
>
>Konfigurieren Sie SSL nicht erzwingen unter `/etc/map` Ordner.

## Konfigurieren der Day CQ Link Externalizer-Konfiguration {#externalizer}

In AEM **Externalizer** ist ein OSGi-Dienst, mit dem Sie einen Ressourcenpfad (z. B. /path/to/my/page) programmgesteuert in eine externe und absolute URL umwandeln können (z. B. https://www.mycompany.com/path/to/my/page), indem dem Pfad ein vorkonfiguriertes DNS vorangestellt wird. Siehe [Externalisieren von URLs](/help/sites-developing/externalizer.md).

>[!CAUTION]
>
>Externalisieren Sie nicht die HTTPS-URL, wenn Sie ein selbstsigniertes Zertifikat für SSL verwenden.
>
>Verwenden Sie außerdem localhost anstelle des Hostnamens für den lokalen Server.

Führen Sie die folgenden Schritte für Autoren- und Veröffentlichungsinstanzen aus:

1. Navigieren Sie zur OSGi-Konfiguration unter https://&lt;*hostname>*:&lt;*port>*/system/console/configMgr.
1. Suchen und Tippen **[!UICONTROL Day CQ Link Externalizer]** Konfiguration.

   Das Dialogfeld Day CQ Link Externalizer wird zur Bearbeitung der Konfiguration geöffnet.

1. Im Dialogfeld Day CQ Link Externalizer im Feld Domänen :

   * Geben Sie in der Autoreninstanz eine Veröffentlichungs-URL an, auf die von einem externen System aus zugegriffen werden kann. Beispiel: ein Hostname oder ein Veröffentlichungs-Webserver.
   * Geben Sie in der Veröffentlichungsinstanz sowohl die Autoren- als auch die Veröffentlichungs-URLs an.

1. Stellen Sie sowohl bei der Autoren- als auch bei der Veröffentlichungsinstanz sicher, dass die lokale Server-URL im Feld Domänen angegeben ist.
1. Tippen Sie auf **[!UICONTROL Speichern]**. Warten Sie eine Weile, bis alle Dienste neu gestartet wurden.

## Konfigurieren des Day CQ Mail Service {#cqmail}

Bei der Implementierung der Referenz-Website müssen E-Mails an Beispielbenutzer gesendet werden, wenn diese Formulare ausfüllen und senden. Durch die Konfiguration von Day CQ Mail Service können Sie SMTP-Dienstdetails bereitstellen, um automatisierte E-Mails an Kunden zu senden. Siehe [Konfigurieren von E-Mail-Benachrichtigungen](/help/sites-administering/notification.md).

Führen Sie die folgenden Schritte aus, um den E-Mail-Dienst auf der Veröffentlichungsinstanz zu konfigurieren:

1. Navigieren Sie zur OSGi-Konfiguration unter https://&lt;*hostname>*:&lt;*port>*/system/console/configMgr.
1. Suchen und Tippen **[!UICONTROL Day CQ Mail Service]** , um es zur Konfiguration zu öffnen.
1. Geben Sie SMTP-Server-Hostnamen und Anschlusswerte an.
1. Tippen Sie auf **[!UICONTROL Speichern]**.

>[!NOTE]
>
>Sie können Ihren Unternehmens-SMTP-Dienst oder öffentliche Dienste wie Gmail verwenden. Informationen zum Konfigurieren des SMTP-Dienstes finden Sie in der Dokumentation zum SMTP-Dienst .

## Außerkraftsetzen der standardmäßigen XSS-Konfiguration {#xss}

Die E-Mail-Vorlagen für die We.Finance-Referenz-Website enthalten personalisierte Links in E-Mails. Diese Links haben Platzhalter als `${placeholder}`. Diese Platzhalter werden vor dem Senden von E-Mails durch tatsächliche Werte ersetzt. Die standardmäßige XSS-Schutzkonfiguration für AEM erlaubt keine geschweiften Klammern (**{ }**) in der URL im HTML-Inhalt. Sie können die Standardkonfiguration jedoch außer Kraft setzen, indem Sie die folgenden Schritte in der Veröffentlichungsinstanz ausführen:

1. Kopieren Sie `/libs/cq/xssprotection/config.xml` nach `/apps/cq/xssprotection/config.xml`.
1. Öffnen Sie `/apps/cq/xssprotection/config.xml`.
1. Im `common-regexps` ändern Sie die `onsiteURL` eingeben und die Datei speichern.

   `<regexp name="onsiteURL" value="([\p{L}\p{N}\\\.\#@\$\{\}%\+&;\-_~,\?=/!\*\(\)]*|\#(\w)+)"/>`

>[!NOTE]
>
>Geschweifte Klammern (**{ }**) als zulässige Zeichen in die URL im HTML-Inhalt aufgenommen werden.

Nachdem Sie den SMTP-Server konfiguriert haben, versuchen Sie, ein Formular mit der Rolle &quot;Sarah Rose&quot;auszufüllen und es als Entwurf zu speichern. Wenn Sie als Entwurf speichern, erhalten Sie eine Option, den Entwurf per E-Mail zu erhalten. Beim Tippen auf **E-Mail senden** Wenn Sie eine E-Mail mit einer Verknüpfung zum Antragsentwurf erhalten, ist Ihre E-Mail-Konfiguration erfolgreich. Stellen Sie sicher, dass Sie sich mit den Anmeldedaten von Sarah anmelden, um den Entwurf anzuzeigen.

## AEM DS-Einstellungen konfigurieren {#aemds}

AEM DS-Diensteinstellungen sind in der Veröffentlichungsinstanz für die E-Mail-Kommunikation in den Anwendungsfällen der Referenz-Website erforderlich. Ausführliche Anweisungen zum Konfigurieren AEM DS-Service-Setup auf der Veröffentlichungsinstanz finden Sie unter [AEM DS-Einstellungen konfigurieren](/help/forms/using/configuring-the-processing-server-url-.md).

Geben Sie für AEM Forms-Referenzsites im AEM DS Settings Service die URL des Veröffentlichungsservers anstelle der URL des Verarbeitungsservers an.

>[!CAUTION]
>
>Nicht absetzen `/lc` in der Verarbeitungsserver-URL, wenn Sie sie für AEM Forms OSGi konfigurieren.

## Bereitstellen von Referenz-Sites-Paketen {#refsite}

Installieren Sie die folgenden Referenz-Website-Pakete mithilfe der Software Distribution.

* [AEM-FORMS-6.4-FSI-REF-SITE](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-FSI-REF-SITE)
* [AEM-FORMS-6.4-GOV-REF-SITE](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-GOV-REF-SITE)

Weitere Informationen zur Verwendung von Paketen finden Sie unter [Arbeiten mit Paketen](/help/sites-administering/package-manager.md).

Nachdem Sie die Pakete installiert und die Autoren- und Veröffentlichungsinstanzen gestartet haben, rufen Sie die folgenden URLs in Ihrem Browser auf:

* `https://[server]:[port]/wegov`
* `https://[server]:[port]/wefinance`

Wenn Ihre Installation erfolgreich ist, können Sie auf die Landingpages der We.Gov- und We.Finance-Referenz-Sites zugreifen.

## (Optional) Importieren von Beispieldaten in Microsoft Dynamics {#optional-import-sample-data-into-microsoft-dynamics}

Die Referenzseiten für Hypothekenanwendungen und für die Anwendung für die automatische Versicherung sind so konfiguriert, dass sie Datensätze aus Microsoft Dynamics verwenden. Das Referenz-Website-Paket installiert eine benutzerdefinierte Entität und Beispieldatensätze, die Sie in Microsoft Dynamics importieren können, um die Referenz-Website auszuführen. Führen Sie die folgenden Schritte aus, um die Beispieldaten zu migrieren und einzurichten:

So importieren Sie die benutzerdefinierte Entität für die Anwendung für die automatische Versicherung:

1. Laden Sie die **WeFinanceAutoInsurance_1_0.zip** Lösungspaket von `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/WeFinanceAutoInsurance_1_0.zip` auf Ihrer AEM Autoreninstanz.
1. Wechseln Sie in Ihrer Microsoft Dynamics-Instanz zu **[!UICONTROL Lösungen]** im **[!UICONTROL Einstellungen]** Menü und klicken Sie auf **[!UICONTROL Import]**. Wählen Sie das Package aus und importieren Sie es.

So importieren Sie die benutzerdefinierte Entität für die Anwendung für die automatische Versicherung:

1. Laden Sie die **AEMFormsFSIRefsite_1_0.zip** Paket von https://[author]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/AEMFormsFSIRefsite_1_0.zip Wählen Sie das Package aus und importieren Sie es.

1. Wechseln Sie in Ihrer Microsoft Dynamics-Instanz zu **[!UICONTROL Lösungen]** im **[!UICONTROL Einstellungen]** Menü und klicken Sie auf **[!UICONTROL Import]**. Wählen Sie das Package aus und importieren Sie es.

So importieren Sie Kunden- und Versicherungsvertragsdatensätze:

1. Laden Sie die **We.Finance Customers.csv, We.Finance Auto Insurance Renewals.csv** und **Hypothek** Datendateien aus den folgenden Speicherorten in Ihrer AEM-Autoreninstanz:

   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Customers.csv`
   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Auto Insurance Renewals.csv`
   * `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/Sarah%20Rose%20Contact.csv`

1. Führen Sie in Ihrer Microsoft Dynamics-Instanz die folgenden Schritte aus:

   * Navigieren Sie zu **[!UICONTROL Sales > We.Finance-Kunden]** und klicken Sie auf **[!UICONTROL Import]**.
   * Navigieren Sie zu **[!UICONTROL Sales > We.Finance Auto Insurance]** und klicken Sie auf **[!UICONTROL Import]**.
   * Navigieren Sie zu **[!UICONTROL Verkauf > We.Finance-Hypothek]**  und klicken Sie auf **[!UICONTROL Import]**.

## Konfigurieren des OAuth-Cloud-Service für Microsoft Dynamics {#configure-oauth-cloud-service-for-microsoft-dynamics}

Konfigurieren Sie den OAuth-Cloud-Dienst in AEM Forms, um die Kommunikation zwischen AEM Forms und Microsoft Dynamics zu aktivieren. Führen Sie die folgenden Schritte aus, um den OAuth-Cloud Service in AEM Autoren- und Veröffentlichungsinstanzen zu konfigurieren:

1. Wechseln Sie in AEM Autoreninstanz zu **[!UICONTROL Tools > Cloud Services > Data Sources > global]**. Tippen **[!UICONTROL Integration von Refsite Dynamics]** Symbol und tippen Sie auf **[!UICONTROL Eigenschaften]**.
1. Wechseln Sie zum Microsoft Azure Active Directory-Konto. Fügen Sie die kopierte Cloud-Service-Konfigurations-URL in die **[!UICONTROL Antwort-URL]** -Einstellung für Ihre registrierte Anwendung. Speichern Sie die Konfiguration.
1. Geben Sie auf der Registerkarte Authentifizierungseinstellungen **[!UICONTROL Dienststamm]**, **[!UICONTROL Client-ID]**, **[!UICONTROL Client Secret]** und **[!UICONTROL Ressourcen-URL]** für Ihre Microsoft Dynamics-Instanz. Klicken **[!UICONTROL Mit OAuth verbinden]** , der zur Anmeldeseite von Microsoft Dynamics weiterleitet.
1. Geben Sie Ihre Anmeldedaten ein. Nach der Anmeldung werden Sie zur Konfigurationsseite für den AEM Forms Cloud Service weitergeleitet. Klicken Sie auf **[!UICONTROL Speichern und schließen]**. Die Cloud-Service-Konfiguration wird gespeichert.
1. Navigieren Sie zu **[!UICONTROL Forms > Datenintegrationen > We.Finance]**. Wählen Sie Auto Insurance (Dynamics) und klicken Sie auf Bearbeiten. Microsoft Dynamics-Entitäten werden auf der Registerkarte Data Sources aufgeführt. Warten Sie, bis alle Entitäten aus Microsoft Dynamics abgerufen und auf der Registerkarte &quot;Datenquellen&quot;aufgelistet sind.
1. Wählen Sie die **[!UICONTROL AutoInsuranceRenewal-Entität]** und klicken Sie auf **[!UICONTROL Testmodell-Objekt]**. Geben Sie im Abschnitt für die Eingabeanforderung den Wert für die Kunden-ID als &quot;900001&quot;an und klicken Sie auf **[!UICONTROL Test]**. Im Abschnitt &quot;Ausgabe&quot;werden die Datensätze angezeigt, die von Microsoft Dynamics für die Kunden-ID 90001 abgerufen wurden.
1. Geben Sie im Abschnitt für die Eingabeanforderung den Wert für die Kunden-ID als &quot;900001&quot;an und klicken Sie auf **[!UICONTROL Test]**. Im Abschnitt &quot;Ausgabe&quot;werden die Datensätze angezeigt, die von Microsoft Dynamics für die Kunden-ID 90001 abgerufen wurden.
1. Wiederholen Sie die Schritte 1 bis 6 für die Veröffentlichungsinstanz.

## Konfigurieren des Acrobat Sign-Planers {#scheduler}

Führen Sie Folgendes für Autoren- und Veröffentlichungsinstanzen aus:

1. Rufen Sie AEM Web-Konfigurationskonsole auf unter `https://[server]:[host]/system/console/configMgr`.
1. Suchen und Tippen **[!UICONTROL Acrobat Sign Configuration Service]** , um es zur Konfiguration zu öffnen.
1. Konfigurieren **[!UICONTROL Ausdruck für Status-Update-Planung]** as **0 0/2 &amp;ast; &amp;ast; &amp;ast; ?**.

   >[!NOTE]
   >
   >Die obige Planungskonfiguration überprüft den Status des Acrobat Sign-Dienstes alle zwei Minuten.

1. Tippen Sie auf **[!UICONTROL Speichern]**.

## Konfigurieren des Acrobat Sign-Cloud-Dienstes für Referenzsite {#sign-service}

Führen Sie Folgendes für Autoren- und Veröffentlichungsinstanzen aus:

1. Navigieren Sie zu **[!UICONTROL Tools > Cloud Services > Acrobat Sign > global]**. Auswählen **[!UICONTROL AEM Forms Reference Site Sign]** und tippen **[!UICONTROL Eigenschaften]**.

   >[!CAUTION]
   >
   >Stellen Sie sicher, dass https://[Host]:[ssl_port]Die URL /mnt/overlay/adobesign/cloudservices/adobesign/properties.html wird der Umleitungs-URL-Liste der OAuth-Konfiguration der Acrobat Sign-API-Anwendung hinzugefügt.

1. Geben Sie die Client-ID und den geheimen Schlüssel der OAuth-Konfiguration der Acrobat Sign-Anwendung an.
1. (Optional) Wählen Sie die **[!UICONTROL Acrobat Sign auch für Anlagen aktivieren]** und tippen Sie auf **[!UICONTROL Verbindung zu Acrobat Sign herstellen]**. Es hängt die Dateien an adaptive Formulare an das entsprechende Acrobat Sign-Dokument an, das zum Signieren gesendet wird.
1. Tippen **[!UICONTROL Verbindung zu Acrobat Sign herstellen]** und melden Sie sich mit Ihren Acrobat Sign-Anmeldedaten an.

## Konfigurieren des allgemeinen Forms-Konfigurationsdienstes {#anonymous}

Führen Sie in der Veröffentlichungsinstanz die folgenden Schritte aus, um den Zugriff auf anonyme Benutzer zuzulassen:

1. Rufen Sie AEM Web-Konfigurationskonsole auf unter `https://[server]:[port]/system/console/configMgr`.
1. Suchen und Tippen **[!UICONTROL Forms Common Configuration Service]** , um es zur Konfiguration zu öffnen.
1. Konfigurieren Sie die **[!UICONTROL Zulassen]** -Feld für **[!UICONTROL Alle Benutzer]**.
1. Tippen Sie auf **[!UICONTROL Speichern]**.

## REST-Dienst für Formulardatenmodell ändern {#fdm}

Führen Sie Folgendes für Autoren- und Veröffentlichungsinstanzen aus:

1. Wechseln Sie zu CRXDE unter `https://[server]:[port]/crx/de/index.jsp`.
1. Navigieren Sie zu **/conf/global/settings/cloudconfigs/fdm/roi-rest/jcr:content/swaggerFile** und öffnen Sie die Swagger-Datei.
1. Aktualisieren Sie die Host- und Port-Einstellungen gemäß Ihrer Umgebung.
1. Speichern Sie die Einstellungen.
1. (**Nur Autoreninstanz**) Gehen Sie zu **[!UICONTROL Instrumente]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Data Sources]** > **[!UICONTROL global]**. Auswählen **[!UICONTROL Ruhezeit]** und tippen **[!UICONTROL Eigenschaften]**. Tippen **[!UICONTROL Authentifizierungseinstellungen]** und **[!UICONTROL Authentifizierungstyp]** nach **[!UICONTROL Grundlegende Authentifizierung]**. Angeben `admin`/ `admin`als Benutzername/Kennwort für den Zugriff auf den Dienst. Tippen Sie auf **[!UICONTROL Speichern und schließen]**.

## Integration mit Marketing Cloud {#integrate-with-marketing-cloud}

Sie können die AEM Forms in Adobe Analytics und Adobe Target integrieren. Während Adobe Analytics Ihnen beim Generieren von Berichten und Analysieren der Leistung adaptiver Formulare hilft, hilft Adobe Target Ihnen bei der Bereitstellung personalisierter Erlebnisse und dem Durchführen von A/B-Tests für adaptive Formulare.

Führen Sie die folgenden Schritte aus, um Adobe Analytics und Adobe Target in AEM Forms zu konfigurieren.

### Konfigurieren von Adobe Analytics {#configure-adobe-analytics}

Durch die Integration von AEM Forms mit Adobe Analytics können Sie überwachen und analysieren, wie Ihre Kunden mit Ihren Formularen und Dokumenten interagieren. Es hilft Ihnen, Problembereiche zu identifizieren und zu beheben und zu handeln, um die Konversionsrate zu erhöhen.

Um diese Funktion auf der Referenz-Website zu nutzen, konfigurieren Sie Ihr Analytics-Konto wie unter [Konfigurieren von Analysen und Berichten](/help/forms/using/configure-analytics-forms-documents.md).

Um einen Bericht zu generieren, werden Seed-Daten mit den Referenz-Sites gebündelt. Bevor Sie Seed-Daten verwenden, gehen Sie wie folgt vor:

1. Stellen Sie sicher, dass die Analysekonfigurationen We.Finance und We.Gov in den AEM Cloud Services verfügbar sind. Sie finden Cloud-Services auf eine der folgenden Arten:

   * Navigieren Sie zu **[!UICONTROL Tools > Cloud Services > Veraltete Cloud Services]** oder navigieren Sie zu https://&lt;host>:&lt;port>/libs/cq/core/content/tools/cloudservices.html
   * Im **[!UICONTROL Cloud Services]** Seite, unter **[!UICONTROL Adobe Analytics]** Abschnitt, klicken Sie auf `Show Configurations`. Sie können die verfügbaren Konfigurationen We.Finance und We.Gov sehen. Klicken Sie auf , um die Konfiguration zu öffnen. Klicken Sie auf der Konfigurationsseite auf **[!UICONTROL Bearbeiten]**. Geben Sie gültige Angaben zu Unternehmen, Benutzername, Gemeinsamem geheimen Schlüssel (Kennwort) und Rechenzentrum ein und klicken Sie auf **[!UICONTROL Verbindung zu Analytics herstellen]**. Sobald das Dialogfeld Verbindung erfolgreich hergestellt wurde, klicken Sie auf **[!UICONTROL OK]** im Konfigurationsdialogfeld. Konfigurieren Sie das Framework unter der Analytics-Konfiguration, wie im Abschnitt [Konfigurieren von Analytics und Berichten](/help/forms/using/configure-analytics-forms-documents.md).

1. Navigieren Sie zu https://&lt;*Host*>:&lt;*port*>/system/console/configMgr und führen Sie die folgenden Schritte aus:

   * Im **[!UICONTROL Konfiguration der Web-Konsole]** Seite, suchen und klicken **[!UICONTROL AEM Forms Analytics-Konfiguration]**.
   * Im **[!UICONTROL SiteCatalyst Framework]** Wählen Sie im AEM Forms Analytics-Konfigurationsdialogfeld We-finance(we-finance) oder we-gov(we-gov) aus.
   * Klicken **[!UICONTROL Speichern]** und die Seite aktualisieren lassen.

1. Navigieren Sie zum Forms Manager unter https://&lt;host>:&lt;port>/aem/forms und führen Sie die folgenden Schritte aus:

   * Öffnen Sie den Ordner We.Finance oder We.Gov und wählen Sie das Formular aus, für das Sie den Bericht anzeigen möchten.
   * Klicken Sie in der Aktionssymbolleiste auf Analytics aktivieren . Nachdem Sie die Analyse für das Formular aktiviert haben, klicken Sie auf Analytics-Bericht. Es wird ein leerer Bericht generiert. Nachdem ein leerer Bericht generiert wurde, müssen Sie die mit refsite-Paket gelieferten Seed-Daten bereitstellen, um einen Analysebericht für Demozwecke zu generieren.

   Referenz-Sites bieten Analyseberichte mit Seed-Daten für Kreditkarten-, Hypotheken- und Kindergeld-Anwendungsfälle. Informationen zur Konfiguration von Seed-Daten finden Sie unter [Schrittweise Anleitung zur We.Finance-Referenz-Website](/help/forms/using/finance-reference-site-walkthrough.md) und [Schrittweise Anleitung zur We.Gov-Referenz-Website](/help/forms/using/gov-reference-site-walkthrough.md).

### Target konfigurieren {#configure-target}

Die Referenz-Website zeigt die Integration von AEM Forms mit Adobe Target, mit der Sie zielgerichtete und personalisierte Inhalte in adaptive Dokumente aufnehmen können. Sie ermöglicht auch die Erstellung von A/B-Tests für adaptive Formulare.

Um die Integration auf der Referenz-Website zu erleben, führen Sie folgende Schritte aus, um Target in AEM zu konfigurieren:

1. Starten Sie den Autoren-Schnellstart mit dem jvm-Argument. `-Dabtesting.enabled=true` , um A/B-Tests auf dem Server zu aktivieren.

   **Hinweis**: Wenn die AEM-Instanz auf JBoss ausgeführt wird, das von der Turnkey-Installation als Dienst gestartet wird, fügen Sie die `-Dabtesting.enabled=true` im folgenden Eintrag in der `jboss\bin\standalone.conf.bat` Datei, :

   `set "JAVA_OPTS=%JAVA_OPTS% -Dadobeidp.serverName=server1 -Dfile.encoding=utf8 -Djava.net.preferIPv4Stack=true -Dabtesting.enabled=true"`

1. Zugriff https://&lt;*hostname*>:&lt;*port*>/libs/cq/core/content/tools/cloudservices.html.

1. Im **[!UICONTROL Adobe Target]** Abschnitt, klicken Sie auf **[!UICONTROL Konfigurationen anzeigen]**. Sie können die verfügbare We.Finance-Target-Konfiguration sehen. Klicken Sie auf , um die Konfiguration zu öffnen. Klicken Sie auf der Konfigurationsseite auf **[!UICONTROL Bearbeiten]**. Die **[!UICONTROL Komponente bearbeiten]** -Dialogfeld für die Konfiguration geöffnet.

1. Geben Sie Ihren Clientcode, Ihre E-Mail-Adresse und Ihr Kennwort für Ihr Target-Konto an. Wählen Sie den API-Typ als **[!UICONTROL REST]**.
1. Klicken **[!UICONTROL Mit Adobe-Ziel verbinden]**. Nachdem das Target-Konto erfolgreich konfiguriert wurde, klicken Sie auf **[!UICONTROL OK]**. Sie können sehen, dass die gepackte Konfiguration über ein Target Framework verfügt.

1. Wechseln Sie zu „https://&lt;*hostname*>:&lt;*port*>/system/console/configMgr“.

1. Klicken **[!UICONTROL AEM Forms Target-Konfiguration]**.
1. Wählen Sie ein Target-Framework aus.
1. Im **[!UICONTROL Ziel-URLs]** Geben Sie die URL zu AEM Forms an. Beispiel: https://&lt;*hostname*>:&lt;*port*>.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

Anwendungsbeispiele für Kreditkartenanwendungen und Hypothekenanträge zeigen, wie A/B-Tests durchgeführt und ein Bericht zu Demozwecken präsentiert werden kann. Weitere Informationen finden Sie unter [Schrittweise Anleitung zur We.Finance-Referenz-Website](/help/forms/using/finance-reference-site-walkthrough.md).

## Nächster Schritt {#next-step}

Jetzt können Sie alle die Referenz-Website erkunden. Weitere Informationen zu Referenz-Website-Workflows und -Schritten finden Sie unter:

* [Schrittweise Anleitung zur We.Finance-Referenz-Website](/help/forms/using/finance-reference-site-walkthrough.md)
* [Schrittweise Anleitung zur We.Gov-Referenz-Website](/help/forms/using/gov-reference-site-walkthrough.md)

* [Anleitung zur Referenz-Website für Mitarbeiter-Self-Service](/help/forms/using/employee-self-service-reference-site.md)
