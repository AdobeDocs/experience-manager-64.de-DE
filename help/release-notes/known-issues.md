---
title: Bekannte Probleme in AEM 6.4
seo-title: Bekannte Probleme in AEM 6.4
description: Bekannte Probleme in Adobe Experience Manager 6.4
seo-description: Bekannte Probleme in Adobe Experience Manager 6.4.
uuid: 1733f15e-9c4f-4db3-98ee-25c2ea606f0d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 266634ab-21d3-4aac-acfa-b799a7485507
exl-id: ba65e853-d69a-4341-93c3-5628c60c403b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 44%

---

# Bekannte Probleme {#known-issues}

Auf dieser Seite finden Sie eine Liste der bekannten Probleme, die Adobe Experience Manager 6.4 am April 2018 veröffentlicht hat. Weitere Informationen zu bekannten Problemen finden Sie unter [Support kontaktieren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=de).

## Hybrid-Geräte {#hybrid-devices}

Hybrid-Geräte werden nicht unterstützt. Bei der Verwendung dieser Art von Geräten können verschiedene Probleme auftreten. Die folgenden empfohlenen Verfahren helfen bei der Lösung vieler Probleme:

Wenn Sie Google Chrome als Browser verwenden:

* Geben Sie `chrome://flags/` in die Adressleiste ein und drücken Sie die Eingabetaste.
* Klicken Sie auf Touch-Ereignisse aktivieren > Deaktiviert .
* Starten Sie den Browser (alle Registerkarten und Fenster) neu.

Wenn Sie Mozilla Firefox als Browser verwenden:

* Geben Sie `about:config` in die Adressleiste ein und drücken Sie die Eingabetaste.
* Filtern Sie die Einstellungen nach `dom.w3c`.
* Stellen Sie sicher, dass die Einstellungen `0` und `false` sind.
* Starten Sie den Browser neu.

Wenn Sie Microsoft Edge als Browser verwenden:

* Geben Sie `about:flags` in die Adressleiste ein und drücken Sie die Eingabetaste.
* Scrollen Sie zu den experimentellen Funktionen und dann zu **[!UICONTROL Touch]**.
* Klicken Sie auf **[!UICONTROL Touch-Ereignisse aktivieren]**.
* Wählen Sie **[!UICONTROL Immer aus]**.
* Starten Sie den Browser neu.

## Plattform {#platform}

* **Vorgangs-Dashboard:** Bei einer Sicherungsdatei ohne die Erweiterung „.zip“ wird die Fortschrittsleiste nicht angezeigt. (GRANITE-10713)
* **HTL:** Java Use-Objekt mit nachstehendem Leerzeichen in der Paketdeklaration friert den SightlyJavaCompilerService ein (GRANITE-20836)
* **Apache Felix/Sling:** Konfigurationsdatei ist auch nach configuration.delete() noch im Repository vorhanden (GRANITE-20618)
* **Cloud-Einstellungen:** Die Konsole wird nach der Bearbeitung des Konfigurations-Containers beschädigt. (GRANITE-20726)
* **Sicherheit:** Die IMS-Integration schlägt mit dem benutzerdefinierten Kontextpfad fehl. (GRANITE-20639)
* **Sicherheit:** Verbessern der standardmäßigen JAAS-Rangfolge von SSO, externen und standardmäßigen Anmeldemodulen (GRANITE-20590)
* **Tools - CRX DE Lite:** Der Rand der Ansicht &quot;Properties&quot;bewegt sich weiter nach oben. (GRANITE-12040)
* **Tooling - CRX DE Lite:**  Änderungen an &quot;Long&quot;-Werttypen können nur gespeichert werden, wenn Sie auf Eigenschaftsname doppelklicken. (GRANITE-12351)

* **Tooling - CRX DE Lite:** Strg+F-Suche in offenen Textdateien hängt bei der Suche nach RegExp hängen (GRANITE-5996).

* **Tooling - CRX DE Lite:** Die Knoteneigenschaft wird nach dem Umbenennen des Knotens nicht angezeigt. (GRANITE-7160)
* **Benutzeroberfläche:** Pulldown &quot;mehr...&quot; zeigt nicht alle Elemente an, wenn sie in einem Popover-Element in IE und Firefox geöffnet wurden. (GRANITE-16326)
* **Benutzeroberfläche:** Die Info-QuickInfo wird ausgeblendet, wenn das feste Spaltenlayout mit zwei nebeneinander liegenden Spalten verwendet wird. (GRANITE-16869)
* **Benutzeroberfläche:** Es tritt ein unbehandelter Fehler auf, wenn stellvertretend für einen Benutzer agiert wird, der nicht vorhanden ist (GRANITE-23228). Dies kann durch [Implementieren eines Fehlerhandlers](/help/sites-developing/customizing-errorhandler-pages.md) zum Anpassen der Fehlermeldung umgangen werden.

* **Omnisearch:** Suchvorgänge mit umgekehrtem Schrägstrich verursachen eine Ausnahme. (GRANITE-11769)
* **Omnisearch:** Wenn Sie &quot;Anzeigeeinstellungen&quot;in der Listenansicht öffnen, ändert sich der Suchfilter. (GRANITE-16524)
* **Omnisearch:** Falsche Liste von Spaltenkonfigurationen, die bei der Asset-Suche von Sites angezeigt werden (GRANITE-16527)

* **Omnisearch**: Eigenschaften von linker Seitenleiste stehen in Zusammenhang mit der Omnisearch-Serveranforderung. (GRANITE-20524)
* **Omnisearch:** Omnisearch unterstützt keine Kontextpfade. (GRANITE-16044)

## Assets {#assets}

* **Suchen**: Die Suche gibt keine Ergebnisse zurück, wenn die Suchzeichenfolge mit einem Leerzeichen  [OAK-4786 beginnt.](https://issues.apache.org/jira/browse/OAK-4786)

* **Suchen**: In der klassischen Benutzeroberfläche sind Tags in der Suche nicht sichtbar (CQ-4235239).

* **Benutzeroberfläche**: Die Asset-Benutzeroberfläche reagiert nach dem Kopieren/Einfügen und Auswählen-Alle nicht mehr. (CQ-4236142)

* **Benutzeroberfläche**: Assets können nach verzögertem Laden nicht verschoben werden. (CQ-4236134)

* **Berichte**: Fehler bei der Erstellung von Berichten zur Asset-Änderung (CQ-4239744)

* **Berichte**: Geplant: Die regelmäßige Erstellung von Asset-Berichten schlägt inkonsistent fehl (einige Berichte bleiben in der Warteschlange). (CQ-4239089)

* **Metadaten**: Beim Hinzufügen eines Textfelds mit mehreren Werten zum Asset-Schema funktioniert die erforderliche Regel zum Kaskadieren von Feldern nicht. (CQ-4239333)

* **Brand Portal**: Die Veröffentlichung in Brand Portal funktioniert nicht für Sammlungen. (CQ-4238731)

* **Upload:** Beim Hochladen von Assets mit Sonderzeichen im Dateinamen wird die Validierungsfehlermeldung über die unzulässigen Zeichen nicht für alle Assets angezeigt. Während die Fehlermeldung nur für das erste Asset angezeigt wird, zeigt die Benutzeroberfläche dem Benutzer eindeutig an, dass der Dateiname des bereitgestellten Assets nicht zulässig ist. (CQ-4256876)

## Communities {#communities}

* **Moderation**: Es ist nicht möglich, den übergeordneten Beitrag in einem einzelnen Löschvorgang aus der Massenmoderationsoberfläche zu löschen. (CQ-4236797)

* **Konsole**  - Der Link &quot;Benutzername vergessen&quot;oder &quot;Kennwort vergessen&quot;leitet zur Anmeldeseite um, anstatt zum entsprechenden Kennwortabfrageformular. (CQ-4237682)

## Formulare {#forms}

### Installation und Entwicklung

* (Nur AEM Forms JEE) Beim Bootstrapping von JBoss Application Server während der Ausführung von Configuration Manager werden EJB-Aufruf- und Bootstrap-Fehler zurückgegeben. Diese können jedoch ignoriert werden. (Referenznummer CQ-4229793)
* Wenn AEM Forms gestartet wird, wird die `SAX Security Manager could not be setup`-Warnung angezeigt. (CQ-4297403)

### Interaktive Kommunikation

* Beim Laden der interaktiven Kommunikation mit Diagramm- oder Bildelementen über die Agenten-Benutzeroberfläche treten Verzögerungen auf. (CQ-4236630)
* Das Datenanzeigeformat in der Druckvorschau ist TT-MM-JJJJ, während es in der Webvorschau `dd-mmm-yy` ist. (CQ-4237045)
* Der Webkanal „Interaktive Kommunikation“ unterstützt nur sortierte und unsortierte Listen. In Listen-Dokumentfragmenten werden ebenenübergreifende Listen und Einzüge für den Webkanal der interaktiven Kommunikation nicht unterstützt. (CQ-4233672)
* Beim Synchronisieren des Web-Kanals mit dem Print-Kanal können die folgenden Probleme auftreten:

   * Beim Synchronisierung des Web-Kanals treten beim ersten Wechsel vom Print-Kanal Verzögerungen auf.
   * Der Web-Kanal wird nicht synchronisiert, wenn der Print-Kanal eine nicht konfigurierte Diagramm-Komponente enthält. Löschen Sie die Diagramm-Komponente und führen Sie die Synchronisierung erneut durch, um das Problem zu beheben.
   * Die Synchronisierung schlägt manchmal mit dem Fehler &quot;Beim Synchronisieren der Live Copy ist ein Fehler aufgetreten&quot;fehl. Aktualisieren Sie die Seite, um das Problem zu beheben.
   * Der statische Text in einem Layout-Fragment wird durch den Namen der Tabellenzelle ersetzt, wenn die erste Spalte der Tabelle eine Headerspalte in der Vorlage für den Print-Kanal ist.
   * Komponenten oder Assets können ausschließlich am Ende einer Web-Kanal-Kommunikation hinzugefügt werden. Um sie an einer anderen Stelle zu platzieren, fügen Sie ein Feld am unteren Rand des Web-Kanals hinzu und ordnen Sie sie mithilfe der Inhaltsstruktur neu an.
   * Inhalte lassen sich in den vererbten Zielbereich des Web-Kanals verschieben, ohne die Live Copy-Vererbung zu entfernen.

(CQ-4239780)

### Datenintegration

* Authentifizierungskonfigurationen für SOAP-basierte Webservices sind nicht sichtbar und können daher nicht in Cloud-Services konfiguriert werden. Gehen Sie folgendermaßen vor, um das Problem zu lösen:

   1. Wechseln Sie in der CRXDE Lite Console zum folgenden Knoten.\
      /libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices/\
      wsdlauthenticationSettings/items/fixedcolumns/items/container/items/wsdl/items/\
      selectAuthentication/items/custom.
   1. Aktualisieren Sie den Wert der Eigenschaft value auf denselben Wert wie die Eigenschaft text .
   1. Klicken Sie auf Alle speichern, um die Konfiguration zu speichern.

(CQ-4238462)

### Adobe Sign-Integration

* Der Adobe Sign-Planer setzt zwischenzeitlich aus, deshalb werden noch zu unterzeichnende Formulare nicht zur Übermittlung weitergeleitet. Um das Problem zu beheben, starten Sie das Bundle **Apache Sling Scheduler Support** von AEM Web Console unter https://[*server*]:[*port*]/system/console/bundles neu.

### Bearbeitung adaptiver Formulare

* In adaptiven Formularen nimmt die Diagramm-Komponente mehr Platz ein, als es normalerweise der Fall ist.
* Beim Speichern von Eigenschaften für adaptive Formulare, adaptive Formularfragmente oder interaktive Kommunikation in der Forms Manager-Benutzeroberfläche wird eine Ausnahme zurückgegeben.
* Die angegebene maximale Zeichenanzahl für ein adaptives Formulartextfeld wird auf Samsung-Geräten mit Android 6.0 nicht berücksichtigt. (Referenznummer CQ-4235205)
