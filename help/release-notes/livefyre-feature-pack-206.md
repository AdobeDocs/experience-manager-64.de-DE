---
title: Livefyre Feature Pack 2.0.6 - Versionshinweise
seo-title: Livefyre Feature Pack 2.0.6 - Versionshinweise
description: Livefyre Feature Pack 2.0.6 - Versionshinweise
seo-description: Livefyre Feature Pack 2.0.6 - Versionshinweise
uuid: 81ee0527-72c3-4530-80f1-c802ddbe62d0
products: SG_EXPERIENCEMANAGER/6.4
contentOwner: alba
discoiquuid: d445bcfb-7712-472f-bfb4-a8811c2bc4f1
translation-type: tm+mt
source-git-commit: 715cff841252d79504d702817f91db92df919bfc

---


# Livefyre Feature Pack 2.0.6 Release Notes {#livefyre-feature-pack-release-notes}

## Versionshinweise {#release-information}

<table> 
 <tbody>
  <tr>
   <td>Produkte</td> 
   <td>Livefyre Feature Pack 2.0.6</td> 
  </tr>
  <tr>
   <td>Version</td> 
   <td>2.0.6</td> 
  </tr>
  <tr>
   <td>Typ</td> 
   <td>Neue Funktionen</td> 
  </tr>
  <tr>
   <td>Datum</td> 
   <td>31. August 2018</td> 
  </tr>
  <tr>
   <td>Download-URL<br /> </td> 
   <td>Wenden Sie sich an Ihren Administrator</td> 
  </tr>
  <tr>
   <td>Kompatibilität (*)</td> 
   <td>AEM 6.4 SP1, 6.4, 6.3 GA und 6.2 SP1</td> 
  </tr>
  <tr>
   <td>Beschreibung</td> 
   <td>Dieses Paket ermöglicht Ihnen die Integration der branchenführenden Kurationsfunktionen von Livefyre in Ihre AEM-Instanz. So können Sie innerhalb weniger Minuten wertvolle benutzergenerierte Inhalte (UGC) aus sozialen Netzwerken auf Ihrer Site veröffentlichen.</td> 
  </tr>
 </tbody>
</table>

## What is included in Livefyre Feature Pack 2.0.6 {#what-is-included-in-livefyre-feature-pack}

Dieses Paket integriert die branchenführenden Kurationsfunktionen von Livefyre in Ihre AEM-Instanz. So können Sie innerhalb weniger Minuten wertvolle benutzergenerierte Inhalte (UGC) aus sozialen Netzwerken auf Ihrer Site veröffentlichen. Dieses Paket umfasst drei verschiedene Komponenten:

**UGC-Inhalte in AEM-Assets importieren**

* Importieren Sie mit dem UGC Importer von Twitter und Instagram benutzerdefinierte Inhalte (UGC) aus Livefyre Studio in AEM Assets.
* Greifen Sie auf Ihre Livefyre-Bibliothek zu.
* Suchen Sie mithilfe der Livefyre Social-Suche in Echtzeit nach Twitter und Instagram.
* Verwaltung von Rechten auf dem UGC.

**Hinzufügen von Livefyre-Komponenten zu AEM-Sites oder -Communities**

* Erstellen und passen Sie dynamische und ansprechende Erlebnisse sofort mit einer Suite aus Social-Komponenten wie Karten, Galerien und Media Walls an.
* Veröffentlichen Sie UGC auf AEM-Sites oder -Communities.

**Importieren von Produktkatalogen in Livefyre mit AEM Commerce**

* Integrieren Sie nahtlos Ihren bestehenden Produktkatalog in Livefyre, um die Benutzerinteraktion und Konversion auf Ihren Sites zu fördern und einkaufsfähige UGC-Erlebnisse bereitzustellen.
* Bearbeiten oder löschen Sie Elemente im AEM Commerce-Produktkatalog und aktualisieren Sie automatisch Änderungen in Livefyre.

Hilfe zur Installation finden Sie unter [Integration mit Livefyre](https://https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/livefyre.html).

### Zusätzliche Versionsinformationen {#additional-release-information}

Aufgrund von Aktualisierungen, die sich auf die Aggregation von Inhalten von Instagram-Benutzerkonten für Nichtgeschäftskunden auswirken, können wir keine Kommentare mehr in Ihrem Namen veröffentlichen oder automatisch nach Antworten des Autors suchen. [Klicken Sie hier, um mehr zu erfahren](https://developers.facebook.com/blog/post/2018/04/04/facebook-api-platform-product-changes/).

>[!NOTE]
>
>Livefyre Feature Pack 2.0.6 unterstützt keine AEM Classic-Benutzeroberfläche.

#### Neue Funktion oder Verbesserung {#new-feature-or-improvement}

* Es wurde die Möglichkeit hinzugefügt, UGC zu durchsuchen, bevor Sie Rechte einrichten und soziale Konten in Livefyre anfordern. Sie müssen soziale Konten einrichten, um Rechte anzufordern, oder die Berechtigungsanforderung überschreiben, wenn Sie Eigentümer des Inhalts sind.
* Der Arbeitsablauf[ für Anfragen zu Instagram- und Twitter- ](https://https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/livefyre.html)UGC-Rechten wurde aktualisiert, um die neuesten APIs zu erfüllen.
* Der Rights-Status und entsprechende Aktionen werden jetzt im Bildschirm &quot;Rights Request&quot;angezeigt.

#### Fehlerbehebungen {#bug-fixes}

* Es wurde ein Problem behoben, bei dem das Löschen eines sozialen Kontos in Livefyre Studio, das für die Berechtigungsanforderung verwendet wurde, einen Fehler verursachte, wenn die UGC-Bibliothek in AEM geladen wurde.
* Es wurde ein Problem behoben, bei dem die Asset-Anzahl im Livefyre-Studio nicht mit der Asset-Anzahl in der AEM UGC-Bibliothek übereinstimmte.
* Es wurde ein Problem in der UGC-Bibliothek behoben, bei dem gefilterte Ergebnisse angezeigt wurden, nachdem die Filteroptionen zurückgesetzt wurden.
* Es wurde ein Problem mit AEM Commerce behoben, bei dem durch Aktionsaufruf-Schaltflächen Benutzer zur falschen URL weitergeleitet wurden.
* Es wurde ein Problem in AEM-Sites behoben, bei dem das Ziehen und Ablegen mehrerer Komponenten in den parsys-Platzhalter dazu führte, dass sie nicht mehr angezeigt wurden.
* Es wurde ein Problem behoben, durch das deaktivierte soziale Konten beim Senden einer Berechtigungsanfrage zur Auswahl verfügbar waren.
* Es wurde ein Problem behoben, bei dem beim Ziehen und Ablegen von UGC aus Assets in Sites ein Fehler auftrat.
* Es wurde ein Problem behoben, bei dem durch Ziehen und Ablegen von Chat- und Liveblog-Komponenten in Sites die App nicht erstellt wurde.
* Es wurde ein Problem behoben, bei dem die Kommentaranwendung einen Fehler verursachte, wenn Benutzer versuchten, einen Kommentar abzugeben.
* Es wurde ein Problem behoben, bei dem beim Hinzufügen der Livefyre Media Wall App zu einer Site ein zusätzlicher Knoten im Java Content Repository erstellt wurde.
* Es wurde ein Problem behoben, das Seitenumbrüche und Konsolenfehler in der Instagram UGC-Suche verursachte.
* Es wurde ein Problem behoben, bei dem Instagram-Benutzersymbole API-Fehler in Assets generierten.
* Es wurde ein Problem behoben, bei dem die Reviews-App einer Site ohne vordefiniertes Format hinzugefügt wurde.
* Es wurde ein Problem mit der Touch-Benutzeroberfläche und der Inline-Bearbeitung behoben.
* Es wurde ein Fehler behoben, der beim Importieren bestimmter Instagram-Bild-Assets zu einem Fehler führte.
* Es wurde ein Problem behoben, bei dem der Livefyre-HTTP-Client in AEM keine Proxykonfiguration unterstützte.

