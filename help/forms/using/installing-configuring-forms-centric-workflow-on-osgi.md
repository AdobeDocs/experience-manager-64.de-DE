---
title: Installieren und Konfigurieren eines Forms-zentrierten Workflows auf OSGi
seo-title: Installing and Configuring Forms-centric workflow on OSGi
description: 'Installieren und konfigurieren Sie AEM Forms Interaktive Kommunikation, um Geschäftskorrespondenzen, Dokumente, Kontoauszüge, Mitteilungen über finanzielle Leistungen, Marketing-E-Mails, Rechnungen und Willkommenskits zu erstellen. '
seo-description: Install and configure AEM Forms Interactive Communications to create business correspondences, documents, statements, benefit notices, marketing mails, bills, and welcome kits.
uuid: 847c3351-dc46-4e60-a023-0f4e9e057c7c
topic-tags: installing
discoiquuid: 7333641e-8c8c-4b52-a7da-a2976c88592c
role: Admin
exl-id: 308b106f-4c5a-49d6-a7f6-c1e8a0bf62e9
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '1611'
ht-degree: 59%

---

# Installieren und Konfigurieren eines Forms-zentrierten Workflows auf OSGi {#installing-and-configuring-forms-centric-workflow-on-osgi}

## Einführung {#introduction}

Unternehmen erfassen und verarbeiten Daten aus mehreren Formularen, Back-End-Systemen und anderen Datenquellen. Die Datenverarbeitung umfasst Überprüfungs- und Validierungsverfahren, sich wiederholende Aufgaben und die Datenarchivierung. Überprüfen Sie beispielsweise ein Formular und konvertieren Sie es in ein PDF-Dokument. Wenn die sich wiederholenden Aufgaben manuell durchgeführt werden, kann es viel Zeit und Ressourcen in Anspruch nehmen.

Sie können [Forms-orientierter Workflow auf OSGi](/help/forms/using/aem-forms-workflow.md) um schnell adaptive formularbasierte Workflows zu erstellen. Diese Workflows können Ihnen dabei helfen, Prüfungs- und Genehmigungs-Workflows, Geschäftsprozess-Workflows und andere sich wiederholende Aufgaben zu automatisieren. Diese Workflows helfen auch bei der Verarbeitung von Dokumenten (Erstellen, Zusammenführen, Verteilen und Archivieren von PDF-Dokumenten, Hinzufügen digitaler Signaturen, um den Zugriff auf-Dokumente zu beschränken, Dekodierung von mit Strichcode versehenen Formularen und mehr) sowie bei der Verwendung des Adobe Sign-Signatur-Workflows mit Formularen und Dokumenten.

Nach der Einrichtung können diese Workflows manuell ausgelöst werden, um einen definierten Prozess abzuschließen oder programmgesteuert auszuführen, wenn Benutzer ein Formular oder eine interaktive Kommunikation senden. Die Funktion ist im AEM Forms Add-On-Paket enthalten.

AEM Forms ist eine leistungsstarke Plattform der Enterprise-Klasse. Forms-zentrierte Workflows in OSGi sind nur eine der Funktionen von AEM Forms. Eine vollständige Liste der Funktionen finden Sie unter [Einführung in AEM Forms](/help/forms/using/introduction-aem-forms.md).

>[!NOTE]
>
>Mit formularzentrierten Workflows in OSGi können Sie schnell Workflows für verschiedene Aufgaben auf dem OSGi-Stapel erstellen und bereitstellen, ohne die komplette Prozessverwaltungsfunktion auf dem JEE-Stapel zu installieren. Siehe [Vergleich](/help/forms/using/capabilities-osgi-jee-workflows.md) der Forms-orientierten AEM Workflows für OSGi und Process Management on JEE, um die Unterschiede und Ähnlichkeiten in den Funktionen zu ermitteln.
>
>Wenn Sie nach dem Vergleich die Prozessverwaltungsfunktion auf dem JEE-Stapel installieren möchten, lesen Sie [Installieren oder Aktualisieren von AEM Forms on JEE](/help/forms/home.md) für detaillierte Informationen zum Installieren und Konfigurieren des JEE-Stacks und der Prozessverwaltungsfunktionen.

## Bereitstellungstopologie {#deployment-topology}

AEM Forms-Add-On-Paket ist eine Anwendung, die auf AEM bereitgestellt wird. Sie benötigen nur mindestens eine AEM-Autoren- oder Verarbeitungsinstanz (Produktionsautor), um den Forms-orientierten Workflow für die OSGi-Funktion auszuführen. Eine Verarbeitungsinstanz ist [gehärtete AEM-Autoreninstanz](/help/forms/using/hardening-securing-aem-forms-environment.md) -Instanz. Führen Sie auf dem Produktionsautor keine tatsächlichen Authoring durch, z. B. keine Workflows oder adaptiven Formulare.

Die folgende Topologie ist eine indikative Topologie zum Ausführen von AEM Forms Interactive Communications, Correspondence Management, AEM Forms-Datenerfassung und Forms-Centric-Workflow für OSGi-Funktionen. Detaillierte Informationen zu Topologien finden Sie unter [Architektur und Bereitstellungstopologien für AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

![recommended-topology](assets/recommended-topology.png)

AEM Forms Forms-zentrierte Workflows in OSGi werden AEM Benutzeroberfläche für die Erstellung des Posteingangs- und AEM Workflow-Modells auf den Autoreninstanzen von AEM Forms ausgeführt.

## Systemanforderungen {#system-requirements}

>[!NOTE]
>
>Zum [Nächste Schritte](#next-steps) Abschnitt des Dokuments, wenn Sie AEM Forms bereits auf OSGi installiert haben, wie im Abschnitt [Datenerfassungsfunktionen installieren und konfigurieren](/help/forms/using/installing-configuring-aem-forms-osgi.md) Artikel.

Bevor Sie mit der Installation und Konfiguration eines Forms-zentrierten Workflows auf OSGi beginnen, stellen Sie Folgendes sicher:

* Hardware- und Software-Infrastruktur ist eingerichtet. Eine detaillierte Liste der unterstützten Hardware und Software finden Sie unter [Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

* Der Installationspfad der AEM-Instanz enthält keine Leerzeichen.
* Eine AEM-Instanz wird ausgeführt. In der AEM-Terminologie entspricht eine „Instanz“ einer Kopie von AEM, die auf einem Server im Autor- oder Veröffentlichungsmodus ausgeführt wird. Sie benötigen mindestens eine AEM Instanz (Autor oder Verarbeitung), um einen Forms-orientierten Workflow unter OSGi auszuführen:

   * **Autor**: Eine zum Erstellen, Hochladen und Bearbeiten von Inhalten sowie zum Verwalten der Website verwendete AEM-Instanz. Sobald der Inhalt für die Veröffentlichung bereit ist, wird er an die Veröffentlichungsinstanz repliziert.
   * **Verarbeitung:** Eine Verarbeitungsinstanz ist eine [extrasichere Instanz von AEM Autor](/help/forms/using/hardening-securing-aem-forms-environment.md). Sie können eine Autoreninstanz einrichten und nach der Installation härten.
   * **Veröffentlichen**: Eine AEM-Instanz, die den Inhalt über das Internet oder ein internes Netzwerk veröffentlicht.

* Speicheranforderungen werden erfüllt. Für das Add-on-Paket für AEM Forms ist Folgendes erforderlich:

   * 15 GB temporärer Speicherplatz für Microsoft Windows-basierte Installationen.
   * 6 GB temporärer Speicherplatz für UNIX-basierte Installationen.

* Wenn Sie das UNIX-basierte Betriebssystem verwenden, installieren Sie die folgenden-Pakete aus den Installationsmedien des jeweiligen Betriebssystems.

<table> 
 <tbody>
  <tr>
   <td>expat</td> 
   <td>libxcb</td> 
   <td>freetype</td> 
   <td>libXau</td> 
  </tr>
  <tr>
   <td>libSM</td> 
   <td>zlib</td> 
   <td>libICE</td> 
   <td>libuuid</td> 
  </tr>
  <tr>
   <td>glibc</td> 
   <td>libXext</td> 
   <td><p>nss-softokn-freebl</p> </td> 
   <td>fontconfig</td> 
  </tr>
  <tr>
   <td>libX11</td> 
   <td>libXrender</td> 
   <td>libXrandr</td> 
   <td>libXinerama</td> 
  </tr>
 </tbody>
</table>

## Installieren des AEM Forms-Add-on-Pakets {#install-aem-forms-add-on-package}

AEM Forms-Add-On-Paket ist eine Anwendung, die auf AEM bereitgestellt wird. Das Paket enthält einen Forms-orientierten Workflow für OSGi und andere Funktionen. Führen Sie die folgenden Schritte aus, um das Add-On-Paket zu installieren:

1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Tippen Sie im Kopfzeilenmenü auf **[!UICONTROL Adobe Experience Manager]**.
1. Im Abschnitt **[!UICONTROL Filter]**:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]**.
   2. Wählen Sie die Version und den Typ für das Paket aus. Sie können auch die **[!UICONTROL Suchdownloads]** Option zum Filtern der Ergebnisse.
1. Tippen Sie auf den Paketnamen für Ihr Betriebssystem und wählen Sie **[!UICONTROL EULA-Bedingungen akzeptieren]** und tippen Sie auf **[!UICONTROL Download]**.
1. Öffnen Sie [Package Manager](https://docs.adobe.com/content/help/de-DE/experience-manager-65/administering/contentmanagement/package-manager.html) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

   Sie können das Paket auch über den direkten Link herunterladen, der im Abschnitt [AEM Forms-Versionen](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html) Artikel.

1. Sobald das Paket installiert ist, werden Sie aufgefordert, die AEM-Instanz neu zu starten. **Starten Sie den Server nicht sofort neu.** Warten Sie vor dem Anhalten des AEM Forms-Servers, bis die Meldungen ServiceEvent REGISTERED und ServiceEvent UNREGISTERED nicht mehr in der [AEM-Installationsverzeichnis]/crx-quickstart/logs/error.log und das Protokoll ist stabil.
1. Wiederholen Sie Schritten 1-7 für alle Autor- und Veröffentlichungsinstanzen.  

## Auf die Installation folgende Konfigurationen {#post-installation-configurations}

AEM Forms verfügt über einige obligatorische und optionale Konfigurationen. Zu den obligatorischen Konfigurationen gehören die Konfiguration von BouncyCastle-Bibliotheken und des Serialisierungsagenten. Zu den optionalen Konfigurationen gehören die Konfiguration von Dispatcher und Adobe Target.

### Obligatorisch Konfigurationen nach der Installation {#mandatory-post-installation-configurations}

#### Konfigurieren von RSA- und BouncyCastle-Bibliotheken  {#configure-rsa-and-bouncycastle-libraries}

Führen Sie sowohl auf der Autor- als auch auf der Veröffentlichungsinstanz folgende Schritte zum Boot-Delegate der Bibliotheken aus:

1. Beenden Sie die zugrunde liegenden AEM-Instanz.
1. Öffnen Sie die [AEM Installationsverzeichnis]\crx-quickstart\conf\sling.properties Datei zur Bearbeitung.

   Wenn Sie [AEM Installationsverzeichnis]\crx-quickstart\bin\start.bat , um AEM zu starten, und bearbeiten Sie dann die sling.properties-Datei unter [AEM_root]\crx-quickstart\.

1. Fügen Sie die folgenden Eigenschaften der sling.properties-Datei hinzu:

   ```
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*
   sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*
   ```

1. (Nur AIX) Fügen Sie der Datei sling.properties die folgenden Eigenschaften hinzu:

   ```
   sling.bootdelegation.xerces=org.apache.xerces.*
   ```

1. Speichern und schließen Sie die Datei und starten Sie die AEM-Instanz.
1. Wiederholen Sie Schritten 1-4 für alle Autor- und Veröffentlichungsinstanzen.  

#### Konfigurieren Sie den Serialisierungsagenten {#configure-the-serialization-agent}

Führen Sie die folgenden Schritte für alle Autoren- und Veröffentlichungsinstanzen aus, um das Paket zur Zulassungsliste hinzuzufügen:

1. Öffnen Sie AEM Configuration Manager in einem Browserfenster. Die Standardeinstellung ist `https://[server]:[port]/system/console/configMgr`.
1. Suchen und öffnen Sie die **Deserialisierungs-Firewallkonfiguration**.
1. Fügen Sie die **sun.util.calendar** -Paket zu **Zulassungsliste** -Feld. Klicken Sie auf Speichern.
1. Wiederholen Sie Schritten 1-3 für alle Autor- und Veröffentlichungsinstanzen.  

### Optionale Konfigurationen nach der Installation {#optional-post-installation-configurations}

#### Konfiguration des Dispatchers {#configure-dispatcher}

Dispatcher·ist ein·Tool zum Zwischenspeichern und für den Lastenausgleich für AEM. Durch Anwendung von AEM Dispatcher können Sie auch den AEM-Server vor Angriffen schützen. Somit können Sie die Sicherheit Ihrer AEM-Instanz verbessern, indem Sie den Dispatcher in Verbindung mit einem Webserver der Unternehmensklasse verwenden. Wenn Sie [Dispatcher](https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher-configuration.html) verwenden, führen Sie die folgenden Konfigurationen für AEM Forms durch:

1. Konfigurieren des Zugriffs für AEM Forms:

   Öffnen Sie die Datei „dispatcher.any“, um sie zu bearbeiten. Navigieren Sie zum Filterabschnitt und fügen Sie den folgenden Filter dem Filterabschnitt hinzu:

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   Speichern und schließen Sie die Datei. Ausführliche Informationen zu Filtern finden Sie in der [Dispatcher-Dokumentation](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html).

1. Konfigurieren des Referrer-Filterservice:

   Melden Sie sich beim Apache Felix Configuration Manager als Administrator an. Die Standard-URL des Konfigurationsmanagers lautet `https://[server]:[port_number]/system/console/configMgr`. Wählen Sie im Menü **Configurations** die Option **Apache Sling Referrer Filter.** Geben Sie im Feld „Hosts zulassen“ den Hostnamen des Dispatchers ein, um ihn als Referrer zuzulassen, und klicken Sie auf **Speichern**. Das Format des Eintrags ist `https://[server]:[port]`.

#### Konfigurieren des Cache {#configure-cache}

Caching ist ein Vorgang, um Datenzugriffszeiten zu verkürzen, die Wartezeit zu reduzieren, und die Geschwindigkeit von Eingabe/Ausgabe (I/A) zu verbessern. Cache für adaptive Formulare speichert nur HTML-Inhalte und JSON-Strukturen eines adaptiven Formulars, ohne die vorausgefüllten Daten zu speichern. Die Zeit, die benötigt wird, um ein adaptives Formular oder ein Dokument auf dem Client zu rendern, wird reduziert.

* Wenn Sie den Cache für adaptive Formulare verwenden, nutzen Sie den [AEM-Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html), um Client-Bibliotheken (CSS und JavaScript) eines adaptiven Formulars oder Dokuments zwischenzuspeichern.
* Beim Entwickeln der benutzerdefinierten Komponenten muss auf dem für die Entwicklung verwendeten Server der Cache für adaptive Formulare deaktiviert bleiben.

Führen Sie die folgenden Schritte aus, um den Cache für adaptive Formulare zu konfigurieren:

1. Wechseln Sie zum Konfigurations-Manager der AEM-Web-Konsole unter `https://[server]:[port]/system/console/configMgr`.
1. Klicken Sie auf **[!UICONTROL Konfiguration für adaptive Formulare und interaktiven Kommunikations-Web-Kanal]**, um die Konfigurationswerte zu bearbeiten. Geben Sie im Dialogfeld &quot;Konfigurationswerte bearbeiten&quot;die maximale Anzahl von Formularen oder Dokumenten an, die eine Instanz des AEM Forms-Servers im **Anzahl der adaptiven Forms** -Feld. Der Standardwert ist 100. Klicken Sie auf **Speichern**.

   >[!NOTE]
   >
   >Um den Cache zu deaktivieren, legen Sie den Wert für die Anzahl adaptiver Formulare auf **0** fest. Der Cache wird zurückgesetzt, und alle Formulare und Dokumente werden aus dem Cache entfernt, wenn Sie die Cachekonfiguration deaktivieren oder ändern.

#### Adobe Sign konfigurieren {#configure-adobe-sign}

Adobe Sign aktiviert Arbeitsabläufe für E-Signaturen für adaptive Formulare. E-Signaturen verbessern die Workflows bei der Verarbeitung von Dokumenten in den Bereichen Recht, Vertrieb, Gehaltsabrechnung, Personalverwaltung u. v. a..

In einem typischen Adobe Sign- und Forms-orientierten Workflow auf OSGi-Szenario füllt ein Benutzer ein adaptives Formular aus, um einen Dienst zu beantragen. Dies könnte beispielsweise ein Antrag für eine Kreditkarte oder ein Formular für Dienstleistungen für Bürger sein. Wenn ein Benutzer das Antragsformular ausfüllt, sendet und signiert, wird ein Genehmigungs-/Zurückweisungs-Workflow gestartet. Der Dienstleister prüft die Anwendung im AEM Posteingang und verwendet Adobe Sign, um die Anwendung elektronisch zu signieren. Sie können ähnliche Workflows für elektronische Signaturen ermöglichen, indem Sie Adobe Sign in AEM Forms integrieren.

Um Adobe Sign mit AEM Forms zu verwenden, [integrieren Sie Adobe Sign mit AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

## Nächste Schritte {#next-steps}

Sie haben eine Umgebung für die Verwendung eines Forms-zentrierten Workflows für OSGi-Funktionen konfiguriert. Die Schritte zur Nutzung der Funktion sind nun:

* [Verwenden eines Forms-zentrierten Workflows auf OSGi](/help/forms/using/aem-forms-workflow.md)
* [Referenz für Workflow-Schritte](/help/sites-developing/workflows-step-ref.md)
* [Nachbearbeitung von Briefen und interaktiver Kommunikation](/help/forms/using/submit-letter-topostprocess.md)
