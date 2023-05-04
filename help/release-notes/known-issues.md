---
title: Bekannte Probleme in AEM 6.4
seo-title: Known Issues in AEM 6.4
description: Bekannte Probleme in Adobe Experience Manager 6.4
seo-description: Known Issues in Adobe Experience Manager 6.4.
uuid: 1733f15e-9c4f-4db3-98ee-25c2ea606f0d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 266634ab-21d3-4aac-acfa-b799a7485507
exl-id: ba65e853-d69a-4341-93c3-5628c60c403b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1109'
ht-degree: 10%

---

# Bekannte Probleme {#known-issues}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Auf dieser Seite finden Sie eine Liste der bekannten Probleme, die Adobe Experience Manager 6.4 am April 2018 veröffentlicht hat. Weitere Informationen zu bekannten Problemen finden Sie unter [Support kontaktieren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=de).

## Hybrid-Geräte {#hybrid-devices}

Hybridgeräte werden nicht unterstützt. Bei der Verwendung solcher Geräte können verschiedene Probleme auftreten. Die folgenden empfohlenen Verfahren helfen bei der Lösung vieler Probleme:

Wenn Sie Google Chrome als Browser verwenden:

* Typ `chrome://flags/` in der Adressleiste und drücken Sie die Eingabetaste.
* Klicken Sie auf Touch-Ereignisse aktivieren > Deaktiviert .
* Starten Sie den Browser (alle Registerkarten und Fenster) neu.

Wenn Sie Mozilla Firefox als Browser verwenden:

* Typ `about:config` in der Adressleiste und drücken Sie die Eingabetaste.
* Filtern Sie die Einstellungen nach `dom.w3c`.
* Stellen Sie sicher, dass die Einstellungen `0` und `false`.
* Starten Sie den Browser neu.

Wenn Sie Microsoft Edge als Browser verwenden:

* Typ `about:flags` in der Adressleiste und drücken Sie die Eingabetaste.
* Scrollen Sie dann zu den experimentellen Funktionen und **[!UICONTROL Touch]**.
* Klicken **[!UICONTROL Aktivieren von Touch-Ereignissen]**.
* Auswählen **[!UICONTROL Immer deaktiviert]**.
* Starten Sie den Browser neu.

## Platform {#platform}

* **Vorgangs-Dashboard:** Die Fortschrittsleiste wird nicht angezeigt, wenn in der Sicherungsdatei die ZIP-Erweiterung fehlt. (GRANITE-10713)
* **HTL:** Java Use -Objekt mit nachstehendem Leerzeichen in der Paketdeklaration friert den SightlyJavaCompilerService ein. (GRANITE-20836)
* **Apache Felix/Sling:** Konfigurationsdatei nach configuration.delete() weiterhin im Repository vorhanden (GRANITE-20618)
* **Cloud-Einstellungen:** Konsole wird nach der Bearbeitung des Konfigurations-Containers beschädigt. (GRANITE-20726)
* **Sicherheit:** Die IMS-Integration schlägt mit dem benutzerdefinierten Kontextpfad fehl. (GRANITE-20639)
* **Sicherheit:** Verbessern der standardmäßigen JAAS-Rangfolge von SSO, externen und standardmäßigen Anmeldemodulen (GRANITE-20590)
* **Tooling - CRX DE Lite:** Die Ansicht &quot;Ridge of Properties&quot;bewegt sich weiter nach oben (GRANITE-12040)
* **Tooling - CRX DE Lite:** Änderungen an &quot;Long&quot;-Werttypen können nur gespeichert werden, wenn Sie auf Eigenschaftsname doppelklicken. (GRANITE-12351)

* **Tooling - CRX DE Lite:** Strg+F-Suche in geöffneten Textdateien hängt bei der RegExp-Suche hängen (GRANITE-5996).

* **Tooling - CRX DE Lite:** Knoteneigenschaft wird nach dem Umbenennen des Knotens nicht angezeigt (GRANITE-7160)
* **Benutzeroberfläche:** Pulldown &quot;mehr...&quot; zeigt nicht alle Elemente an, wenn sie in einem Popover-Element in IE und Firefox geöffnet wurden. (GRANITE-16326)
* **Benutzeroberfläche:** Die Info-QuickInfo wird ausgeblendet, wenn das Layout fester Spalten mit zwei nebeneinander liegenden Spalten verwendet wird. (GRANITE-16869)
* **Benutzeroberfläche:** Unbehandelter Fehler beim stellvertretenden Benutzer, der nicht vorhanden ist (GRANITE-23228). Problemumgehung durch [Implementierung eines Fehler-Handlers](/help/sites-developing/customizing-errorhandler-pages.md) , um die Fehlermeldung anzupassen.

* **Omnisearch:** Suchvorgänge mit umgekehrtem Schrägstrich verursachen eine Ausnahme. (GRANITE-11769)
* **Omnisearch:** Öffnen Sie &quot;Anzeigeeinstellungen&quot;in der Listenansicht, wodurch sich der Suchfilter ändert. (GRANITE-16524)
* **Omnisearch:** Falsche Liste von Spaltenkonfigurationen bei der Asset-Suche von Sites angezeigt (GRANITE-16527)

* **Omnisearch:** Die Eigenschaften der linken Leiste stimmen mit der Omnisearch-Serveranforderung überein (GRANITE-20524).
* **Omnisearch:** Omnisearch unterstützt keine Kontextpfade. (GRANITE-16044)

## Assets {#assets}

* **Suche**: Die Suche gibt keine Ergebnisse zurück, wenn die Suchzeichenfolge mit einem Leerzeichen beginnt [OAK-4786](https://issues.apache.org/jira/browse/OAK-4786)

* **Suche**: In der klassischen Benutzeroberfläche sind Tags in der Suche nicht sichtbar (CQ-4235239).

* **Benutzeroberfläche**: Die Asset-Benutzeroberfläche reagiert nach dem Kopieren/Einfügen und Auswählen-Alle nicht mehr. (CQ-4236142)

* **Benutzeroberfläche**: Assets können nach verzögertem Laden nicht verschoben werden. (CQ-4236134)

* **Berichte**: Fehler bei der Erstellung von Berichten zur Asset-Änderung (CQ-4239744)

* **Berichte**: Geplant: Die regelmäßige Erstellung von Asset-Berichten schlägt inkonsistent fehl (einige Berichte bleiben in der Warteschlange). (CQ-4239089)

* **Metadaten**: Beim Hinzufügen eines Textfelds mit mehreren Werten zum Asset-Schema funktioniert die erforderliche Regel zum Kaskadieren von Feldern nicht. (CQ-4239333)

* **Brand Portal**: Die Veröffentlichung in Brand Portal funktioniert nicht für Sammlungen. (CQ-4238731)

* **Hochladen**: Beim Hochladen von Assets mit Sonderzeichen im Dateinamen wird die Überprüfungsfehlermeldung zu den unzulässigen Zeichen nicht für jedes Asset angezeigt. Während sie nur für das erste Asset angezeigt wird, zeigt die Benutzeroberfläche dem Benutzer eindeutig an, dass der Dateiname des bereitgestellten Assets nicht zulässig ist. (CQ-4256876)

## Communities {#communities}

* **Moderation** - Übergeordneter Beitrag kann nicht als einzelner Löschvorgang aus der Massenmoderations-Benutzeroberfläche gelöscht werden. (CQ-4236797)

* **Konsole** - Der Link &quot;Benutzername vergessen&quot;oder &quot;Passwort vergessen&quot;leitet zur Anmeldeseite um, anstatt zum entsprechenden Kennwortabfrageformular. (CQ-4237682)

## Formulare {#forms}

### Installation und Bereitstellung

* (Nur AEM Forms JEE) Beim Bootstrapping von JBoss Application Server beim Ausführen von Configuration Manager werden EJB-Aufruf- und Bootstrap-Fehler zurückgegeben. Sie können sie jedoch ignorieren. (Referenznummer CQ-4229793)
* Wenn AEM Forms gestartet wird, wird die Meldung `SAX Security Manager could not be setup` angezeigt. (CQ-4297403)

### Interaktive Kommunikation

* Das Laden interaktiver Kommunikation, die Diagramm- oder Bildelemente enthalten, über die Benutzeroberfläche für Agenten dauert eine Weile. (CQ-4236630)
* Das Anzeigeformat der Daten in der Druckvorschau ist TT-MM-JJJJ, während sich die Webvorschau befindet `dd-mmm-yy` (CQ-4237045)
* Der Webkanal für die interaktive Kommunikation unterstützt nur geordnete und ungeordnete Listen. In Listendokumentfragmenten werden zusammengesetzte Auflistung und Einzüge für den Webkanal der interaktiven Kommunikation nicht unterstützt. (CQ-4233672)
* Die folgenden Probleme werden beobachtet, wenn der Webkanal mit dem Druckkanal synchronisiert wird:

   * Beim erstmaligen Wechsel vom Druckkanal dauert es eine Weile, bis der Webkanal synchronisiert wird.
   * Der Webkanal wird nicht synchronisiert, wenn der Druckkanal eine nicht konfigurierte Diagrammkomponente enthält. Um das Problem zu beheben, löschen Sie die Diagrammkomponente und synchronisieren Sie erneut.
   * Die Synchronisierung schlägt manchmal mit dem Fehler &quot;Beim Synchronisieren der Live Copy ist ein Fehler aufgetreten&quot;fehl. Um das Problem zu beheben, aktualisieren Sie die Seite.
   * Der statische Text in einem Layout-Fragment wird durch den Tabellenzellennamen ersetzt, wenn die erste Spalte in der Tabelle eine Kopfzeilenspalte in der Druckkanalvorlage ist.
   * Komponenten oder Assets können nicht an einem anderen Ort als am unteren Rand einer Webkanalkommunikation hinzugefügt werden. Um ihn an einer anderen Stelle zu platzieren, fügen Sie ein Bedienfeld am unteren Rand des Webkanals hinzu und ordnen Sie es mithilfe der Inhaltsstruktur neu an.
   * Kann Inhalte in den vererbten Zielbereich des Webkanals verschieben, ohne die Live Copy-Vererbung zu entfernen.

(CQ-4239780)

### Datenintegration

* Authentifizierungskonfigurationen für SOAP-basierte Webdienste sind nicht sichtbar und können daher nicht in Cloud Services konfiguriert werden. Gehen Sie folgendermaßen vor, um das Problem zu lösen:

   1. Wechseln Sie in der CRXDE Lite Console zum folgenden Knoten.\
      /libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices/\
      wsdlauthenticationSettings/items/fixedcolumns/items/container/items/wsdl/items/\
      selectAuthentication/items/custom.
   1. Aktualisieren Sie den Wert der Eigenschaft value auf denselben Wert wie die Eigenschaft text .
   1. Klicken Sie auf Alle speichern , um die Konfiguration zu speichern.

(CQ-4238462)

### Acrobat Sign-Integration

* Acrobat Sign Scheduler funktioniert nicht mehr zwischenzeitlich, weshalb das Zeichen für ausstehende Formulare nicht zur Übermittlung verschoben wird. Um das Problem zu beheben, starten Sie den **Unterstützung für Apache Sling Scheduler** Bundle von AEM Web Console unter https://[*server*]:[*port*]/system/console/bundles.

### Adaptives Forms-Authoring

* Die Diagrammkomponente in adaptiven Formularen nimmt mehr Platz in Anspruch als normalerweise.
* Beim Speichern von Eigenschaften für adaptive Formulare, adaptive Formularfragmente oder interaktive Kommunikation in der Forms Manager-Benutzeroberfläche wird eine Ausnahme zurückgegeben.
* Die angegebene maximale Zeichenanzahl für ein adaptives Formulartextfeld wird auf Samsung-Geräten mit Android 6.0 nicht berücksichtigt. (Referenznummer CQ-4235205)
* Wenn Sie ein Formular mit einem Standard-HTML-Upload-Feld von einem Apple iOS-Gerät aus übermitteln, wird der Inhalt der Datei manchmal nicht gesendet und eine 0-Byte-Datei wird am anderen Ende empfangen. Apple iOS 15.1 bietet eine Korrektur für das Problem.

