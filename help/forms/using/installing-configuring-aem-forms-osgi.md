---
title: Installieren und konfigurieren Sie Datenerfassungsfunktionen
seo-title: Install and configure data capture capabilities
description: Installieren und konfigurieren Sie adaptive Formulare, PDF-Formulare und HTML5-Formulare. Konfigurieren Sie Adobe Analytics und Adobe Target für adaptive Formulare, um die Verwendung von Formularen und Zielbenutzern anhand ihres Profils zu analysieren.
seo-description: Install and configure adaptive forms, PDF Forms, and HTML5 Forms. Configure Adobe Analytics and Adobe Target for adaptive forms to analyze usage of forms and target users based on their profile.
uuid: ce253b5a-eeb2-47d2-a6c9-e6f59384159a
contentOwner: khsingh
topic-tags: installing
discoiquuid: 1bb8360c-5543-484e-9712-590822211298
role: Admin
exl-id: 45b0fb99-9f7f-47e6-a4de-4db321867f8f
source-git-commit: f8b19b6723d333e76fed111b9fde376b3bb13a1d
workflow-type: tm+mt
source-wordcount: '1799'
ht-degree: 93%

---

# Installieren und konfigurieren Sie Datenerfassungsfunktionen {#install-and-configure-data-capture-capabilities}

Installieren und konfigurieren Sie adaptive Formulare, PDF-Formulare und HTML5-Formulare. Konfigurieren Sie Adobe Analytics und Adobe Target für adaptive Formulare, um die Verwendung von Formularen und Zielbenutzern anhand ihres Profils zu analysieren.

## Einführung {#introduction}

AEM Forms bietet eine Reihe von Formularen, um Daten vom Endbenutzer zu erhalten: adaptive Formulare, HTML5-Formulare und PDF-Formulare. Darüber hinaus bietet es Tools zum Auflisten aller verfügbaren Formulare auf einer Webseite, Analysieren der Verwendung von Formularen und Targeting von Benutzern anhand ihres Profils. Diese Funktionen sind im Add-On-Paket für AEM Forms enthalten. Das Add-On-Paket wird auf einer Autor- oder Veröffentlichungsinstanz von AEM bereitgestellt.

**Adaptive Formulare:** Diese Formulare ändern Aussehen aufgrund der Bildschirmgröße des Geräts, sind ansprechend und interaktiv. Adaptive Forms kann auch in Adobe Analytics, Acrobat Sign und Adobe Target integriert werden. Es ermöglichte Ihnen, basierend auf der Demografie und anderen Funktionen, personalisierte Formulare und prozessorientierte Benutzererfahrungen bereitzustellen. Sie können auch adaptive Formulare in Acrobat Sign integrieren.

**PDF-Formulare** eignen sich für pixelgenaues Drucken und digitale Informationserfassung in einem PDF-Dokument. Im digitalen Avatar können Sie Adobe Acrobat oder Acrobat Reader verwenden, um diese Formulare zu füllen. Sie können diese Formulare auf Ihrer Website hosten oder das Formularportal verwenden, um diese Formulare auf einer AEM-Site aufzulisten. Sie können diese Formulare auch als Anhang an andere senden. Diese Formulare eignen sich am besten für Desktopumgebungen.

**HTML5-Forms** sind die browserfreundliche Version von PDF-Formularen. HTML5-Forms eignen sich für Umgebungen, in denen PDF-Plug-Ins nicht unterstützt werden. HTML5-Forms ermöglichen das Anzeigen von Formularen auf mobilen Geräten und Desktop-Browsern, auf denen XFA-basierte PDF nicht unterstützt werden. Diese Formulare sind für Tablets und Desktops am besten geeignet.

AEM Forms ist eine leistungsstarke Plattform der Enterprise-Klasse und die Datenerfassung (adaptive Formulare, PDF-Formulare und HTML5-Formulare) ist nur eine der Möglichkeiten von AEM Forms. Eine vollständige Liste der Funktionen finden Sie unter [Einführung in AEM Forms](/help/forms/using/introduction-aem-forms.md).

## Bereitstellungstopologie {#deployment-topology}

AEM Forms-Add-On-Paket ist eine Anwendung, die auf AEM bereitgestellt wird. Sie benötigen nur ein Minimum einer AEM Autor- oder Veröffentlichungsinstanz, um AEM Forms-Datenerfassungsfunktionen auszuführen. Die folgende Topologie wird zum Ausführen von AEM Forms-Datenerfassungsfunktionen von AEM Forms empfohlen. Detaillierte Informationen zu Topologien finden Sie unter [Architektur und Bereitstellungstopologien für AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

![empfohlene-Topologie](assets/recommended-topology.png)

## Systemanforderungen {#system-requirements}

Bevor Sie AEM Forms-Datenerfassungsfunktionen installieren und konfigurieren, stellen Sie Folgendes sicher:

* Hardware- und Software-Infrastruktur ist eingerichtet. Eine detaillierte Liste der unterstützten Hardware und Software finden Sie unter [Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

* Der Installationspfad der AEM-Instanz enthält keine Leerzeichen.
* Eine AEM-Instanz wird ausgeführt. In der AEM-Terminologie entspricht eine „Instanz“ einer Kopie von AEM, die auf einem Server im Autor- oder Veröffentlichungsmodus ausgeführt wird. Sie benötigen mindestens zwei[ AEM-Instanzen (eine Autor- und Veröffentlichungsinstanz),](/help/sites-deploying/deploy.md) um AEM Forms-Datenerfassungsfunktionen auszuführen:

   * **Autor**: Eine zum Erstellen, Hochladen und Bearbeiten von Inhalten sowie zum Verwalten der Website verwendete AEM-Instanz. Sobald der Inhalt für die Veröffentlichung bereit ist, wird er an die Veröffentlichungsinstanz repliziert.
   * **Veröffentlichen**: Eine AEM-Instanz, die den Inhalt über das Internet oder ein internes Netzwerk veröffentlicht.

* Speicheranforderungen werden erfüllt. Für das Add-on-Paket für AEM Forms ist Folgendes erforderlich:

   * 15 GB temporärer Speicherplatz für Microsoft Windows-basierte Installationen.
   * 6 GB temporärer Speicherplatz für UNIX-basierte Installationen.

* Die Replikation und die umgekehrte Replikation für die Autor- und die Veröffentlichungsinstanz werden festgelegt. Weitere Details finden Sie unter [Replikation](/help/sites-deploying/replication.md).
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

AEM Forms-Add-On-Paket ist eine Anwendung, die auf AEM bereitgestellt wird. Das Paket enthält AEM Forms bildet Datenerfassung und andere Funktionen. Führen Sie die folgenden Schritte aus, um das Add-On-Paket zu installieren:

1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Tippen Sie im Kopfzeilenmenü auf **[!UICONTROL Adobe Experience Manager]**.
1. Im Abschnitt **[!UICONTROL Filter]**:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]**.
   2. Wählen Sie die Version und den Typ für das Paket aus. Sie können auch die Option **[!UICONTROL Downloads durchsuchen]** verwenden, um die Ergebnisse zu filtern.
1. Tippen Sie auf den für Ihr Betriebssystem zutreffenden Paketnamen, wählen Sie **[!UICONTROL EULA-Bedingungen akzeptieren]** und tippen Sie auf **[!UICONTROL Herunterladen]**.
1. Öffnen Sie [Package Manager](https://docs.adobe.com/content/help/de-DE/experience-manager-65/administering/contentmanagement/package-manager.html) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

   Sie können das Paket auch über den direkten Link herunterladen, der im Artikel [AEM Forms-Versionen](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html) aufgeführt ist.

1. Sobald das Paket installiert ist, werden Sie aufgefordert, die AEM-Instanz neu zu starten. **Starten Sie den Server nicht sofort neu.** Warten Sie vor dem Anhalten des AEM Forms-Servers, bis die Meldungen „ServiceEvent REGISTERED“ und „ServiceEvent UNREGISTERED“ nicht mehr in der Datei „[AEM-Installationsverzeichnis]/crx-quickstart/logs/error.log“ angezeigt werden und das Protokoll stabil ist.
1. Wiederholen Sie Schritten 1-7 für alle Autor- und Veröffentlichungsinstanzen. 

## Auf die Installation folgende Konfigurationen {#post-installation-configurations}

AEM Forms verfügt über einige obligatorische und optionale Konfigurationen. Zu den obligatorischen Konfigurationen gehören die Konfiguration von BouncyCastle-Bibliotheken und des Serialisierungsagenten. Die optionalen Konfigurationen umfassen die Konfiguration von Dispatcher, Forms Portal, Acrobat Sign, Adobe Analytics und Adobe Target.

### Obligatorisch Konfigurationen nach der Installation {#mandatory-post-installation-configurations}

#### Konfigurieren von RSA- und BouncyCastle-Bibliotheken  {#configure-rsa-and-bouncycastle-libraries}

Führen Sie sowohl auf der Autor- als auch auf der Veröffentlichungsinstanz folgende Schritte zum Boot-Delegate der Bibliotheken aus:

1. Beenden Sie die zugrunde liegenden AEM-Instanz.
1. Öffnen Sie die Datei „[AEM-Installationsverzeichnis]\crx-quickstart\conf\sling.properties“ zur Bearbeitung.

   Wenn Sie AEM mit „[AEM-Installationsverzeichnis]\crx-quickstart\bin\start.bat“ gestartet haben, bearbeiten Sie die Datei „sling.properties“ unter [AEM_root]\crx-quickstart\.

1. Fügen Sie die folgenden Eigenschaften der sling.properties-Datei hinzu:

   ```
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*
   sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*
   ```

1. (Nur AIX) Fügen Sie die folgenden Eigenschaften zur Datei „sling.properties“ hinzu:

   ```
   sling.bootdelegation.xerces=org.apache.xerces.*
   ```

1. Speichern und schließen Sie die Datei und starten Sie die AEM-Instanz.
1. Wiederholen Sie Schritte 1-4 für alle Autor- und Veröffentlichungsinstanzen.

#### Konfigurieren Sie den Serialisierungsagenten {#configure-the-serialization-agent}

Führen Sie auf allen Autoren- und Veröffentlichungsinstanzen folgende Schritte aus, um das Paket zur Zulassungsliste hinzuzufügen:

1. Öffnen Sie AEM Configuration Manager in einem Browserfenster. Die Standardeinstellung ist `https://[server]:[port]/system/console/configMgr`.
1. Suchen und öffnen Sie die **[!UICONTROL Deserialisierungs-Firewallkonfiguration]**.
1. Fügen Sie das Paket **[!UICONTROL sun.util.calendar]** zum Feld **[!UICONTROL Zulassungsliste]** hinzu. Klicken Sie auf **[!UICONTROL Speichern]**.
1. Wiederholen Sie Schritte 1-3 für alle Autor- und Veröffentlichungsinstanzen.

### Optionale Konfigurationen nach der Installation {#optional-post-installation-configurations}

#### Konfiguration des Dispatchers {#configure-dispatcher}

Dispatcher ist ein Tool zum Zwischenspeichern und für den Lastenausgleich für AEM. Durch Anwendung von AEM Dispatcher können Sie auch den AEM-Server vor Angriffen schützen. Somit können Sie die Sicherheit Ihrer AEM-Instanz verbessern, indem Sie den Dispatcher in Verbindung mit einem Webserver der Unternehmensklasse verwenden. Wenn Sie [Dispatcher](https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher-configuration.html) verwenden, führen Sie die folgenden Konfigurationen für AEM Forms durch:

1. Konfigurieren des Zugriffs für AEM Forms:

   Öffnen Sie die Datei „dispatcher.any“, um sie zu bearbeiten. Navigieren Sie zum Filterabschnitt und fügen Sie den folgenden Filter dem Filterabschnitt hinzu:

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   Speichern und schließen Sie die Datei. Ausführliche Informationen zu Filtern finden Sie in der [Dispatcher-Dokumentation](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html).

1. Konfigurieren des Referrer-Filterservice:

   Melden Sie sich beim Apache Felix Configuration Manager als Administrator an. Die Standard-URL für den Configuration Manager lautet `https://[server]:[port_number]/system/console/configMgr`. Wählen Sie im Menü **[!UICONTROL Configurations]** die Option **[!UICONTROL Apache Sling Referrer Filter.]** Geben Sie im Feld „Hosts zulassen“ den Hostnamen des Dispatchers ein, um ihn als Referrer zuzulassen, und klicken Sie auf **[!UICONTROL Speichern]**. Das Format des Eintrags ist `https://[server]:[port]`.

#### Konfigurieren des Cache {#configure-cache}

Caching ist ein Vorgang, um Datenzugriffszeiten zu verkürzen, die Wartezeit zu reduzieren, und die Geschwindigkeit von Eingabe/Ausgabe (I/A) zu verbessern. Cache für adaptive Formulare speichert nur HTML-Inhalte und JSON-Strukturen eines adaptiven Formulars, ohne die vorausgefüllten Daten zu speichern. Die Zeit, die benötigt wird, um ein adaptives Formular oder ein Dokument auf dem Client zu rendern, wird reduziert.

* Wenn Sie den Cache für adaptive Formulare verwenden, nutzen Sie den [AEM-Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html), um Client-Bibliotheken (CSS und JavaScript) eines adaptiven Formulars oder Dokuments zwischenzuspeichern.
* Beim Entwickeln der benutzerdefinierten Komponenten muss auf dem für die Entwicklung verwendeten Server der Cache für adaptive Formulare deaktiviert bleiben.

Führen Sie die folgenden Schritte aus, um den Cache für adaptive Formulare zu konfigurieren:

1. Wechseln Sie zum Konfigurations-Manager der AEM-Web-Konsole unter `https://[server]:[port]/system/console/configMgr`.
1. Klicken Sie auf **[!UICONTROL Konfiguration für adaptive Formulare und interaktiven Kommunikations-Web-Kanal]**, um die Konfigurationswerte zu bearbeiten. Geben Sie im Dialogfeld „Konfigurationswerte bearbeiten“ die maximale Anzahl von Formularen oder Dokumenten an, die eine Instanz des AEM Forms-Servers im Feld **[!UICONTROL Anzahl adaptiver Formulare]** zwischenspeichern kann. Der Standardwert ist 100. Klicken Sie auf **[!UICONTROL Speichern]**.

   >[!NOTE]
   >
   >Um den Cache zu deaktivieren, legen Sie den Wert für die Anzahl adaptiver Formulare auf **0** fest. Der Cache wird zurückgesetzt, und alle Formulare und Dokumente werden aus dem Cache entfernt, wenn Sie die Cachekonfiguration deaktivieren oder ändern.

#### Konfigurieren Sie die SSL-Kommunikation für das Formulardatenmodell {#configure-ssl-communcation-for-form-data-model}

Sie können die SSL-Kommunikation für das Formulardatenmodell aktivieren. Um die SSL-Kommunikation für das Formulardatenmodell zu aktivieren, fügen Sie vor dem Starten einer AEM Forms-Instanz Zertifikate zum Java Trust Store aller Instanzen hinzu. Sie können den folgenden Befehl ausführen, um die Zertifikate hinzuzufügen: 

`keytool -import -alias <alias-name> -file <pathTo .cer certificate file> -keystore <<pathToJRE>\lib\security\cacerts>`

#### Konfigurieren von Acrobat Sign {#configure-adobe-sign}

Acrobat Sign ermöglicht Workflows für die elektronische Signatur für adaptive Formulare. E-Signaturen verbessern die Workflows bei der Verarbeitung von Dokumenten in den Bereichen Recht, Vertrieb, Gehaltsabrechnung, Personalverwaltung u. v. a..

In einem typischen Szenario mit Acrobat Sign und adaptiven Formularen füllt ein Benutzer ein adaptives Formular aus, um einen Dienst zu beantragen. Dies könnte beispielsweise ein Antrag für eine Kreditkarte oder ein Formular für Dienstleistungen für Bürger sein. Wenn ein Benutzer das Antragsformular ausfüllt und signiert, wird dieses zur Bearbeitung an den Dienstleister gesendet. Der Dienstanbieter überprüft die Anwendung und verwendet Acrobat Sign, um die Anwendung zu kennzeichnen. Um ähnliche Workflows für elektronische Signaturen zu aktivieren, können Sie Acrobat Sign in AEM Forms integrieren.

So verwenden Sie Acrobat Sign mit AEM Forms: [Integrieren von Acrobat Sign mit AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

#### Konfigurieren von Adobe Analytics {#configure-adobe-analytics}

AEM Forms ermöglicht die Integration mit Adobe Analytics, sodass Sie Leistungsmetriken für Ihre veröffentlichten Formulare und Dokumente erfassen und verfolgen können. Ziel dieser Analyse ist es, informierte, auf Daten basierende Entscheidungen zu erforderlichen Formularänderungen treffen zu können, durch die Formulare oder Dokumente benutzerfreundlicher werden.

Adobe Analytics mit AEM Forms finden Sie unter [Konfigurieren von Analytics und Berichte](/help/forms/using/configure-analytics-forms-documents.md).

#### Integrieren von Adobe Target {#integrate-adobe-target}

Ihre Kunden werden ein Formular wahrscheinlich verlassen, wenn sie nicht davon angesprochen fühlen. Für die Kunden ist dies ein frustrierendes Erlebnis. Für Ihr Unternehmen kann es zusätzlichen Supportaufwand und Mehrkosten bedeuten. Das Kundenerlebnis optimal zu gestalten und dadurch eine höhere Konvertierungsrate zu erzielen, ist absolut unverzichtbar und stellt zugleich eine große Herausforderung dar. Mit AEM forms erhalten Sie das entscheidende Werkzeug.

AEM forms kann mit der Adobe Marketing Cloud-Lösung Adobe Target integriert werden, um den Kunden ein personalisiertes und ansprechendes Erlebnis über verschiedene digitale Kanäle zu bieten. Um Adobe Target für A/B-Tests für adaptive Formulare zu verwenden, [integrieren Sie Adobe Target in AEM Forms](/help/forms/using/ab-testing-adaptive-forms.md#setupandintegratetargetinaemforms).

## Nächste Schritte {#next-steps}

Sie haben eine Umgebung für die Verwendung der AEM Forms-Datenerfassungsfunktionen konfiguriert. Die nächsten Schritte zur Verwendung der Funktionen, sind Folgende:

* [Erstellen Sie Ihr erstes adaptives Formular](/help/forms/using/create-your-first-adaptive-form.md)
* [Erstellen Sie Ihr erstes PDF Formular](https://helpx.adobe.com/content/dam/help/de/experience-manager/6-4/forms/pdf/designer-quickstart.pdf)
* [Einführung in HTML5-Formulare](/help/forms/using/introduction.md)
