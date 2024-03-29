---
title: Erstellen einer neuen Community-Site zur Aktivierung
seo-title: Author a New Community Site for Enablement
description: Erstellen einer Community-Site für die Aktivierung
seo-description: Create a community site for enablement
uuid: 6822cc99-e272-4661-bddf-aa0800b88c41
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: aff8b79f-dd4e-486e-9d59-5d09dfe34f27
exl-id: 5b16c775-3bd0-4a55-ba9e-f326224e8bae
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1767'
ht-degree: 4%

---

# Erstellen einer neuen Community-Site zur Aktivierung {#author-a-new-community-site-for-enablement}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Community-Site erstellen {#create-community-site}

[Community-Site-Erstellung](sites-console.md) verwendet einen Assistenten, der Sie durch die Schritte zum Erstellen einer Community-Site führt. Es ist möglich, `Next`Schritt oder `Back`in den vorherigen Schritt, bevor die Site im letzten Schritt übergeben wird.

Erste Schritte mit der Erstellung einer neuen Community-Site:

Verwenden der [Autoreninstanz](http://localhost:4502/)

* Anmelden mit Administratorrechten
* Navigieren Sie zu **[!UICONTROL Communities > Sites]**

* Wählen Sie **[!UICONTROL Erstellen]** aus

### Schritt 1: Site-Vorlage {#step-site-template}

![enablementsitetemplate](assets/enablementsitetemplate.png)

Im **Site-Vorlage** Schritt, geben Sie einen Titel, eine Beschreibung, den Namen für die URL ein und wählen Sie eine Community-Site-Vorlage aus, z. B.:

* **Community-Site-Titel**: `Enablement Tutorial`

* **Community-Site-Beschreibung**: `A site for enabling the community to learn.`

* **Community-Site-Stammordner**: (Leer lassen für Standardstamm `/content/sites`)

* **Cloud-Konfigurationen**: (Lassen Sie das Feld leer, wenn keine Cloud-Konfigurationen angegeben sind) geben Sie den Pfad zu den angegebenen Cloud-Konfigurationen an.
* **Community-Site-Basissprache**: (lassen Sie für eine einzelne Sprache unberührt: Englisch) verwenden Sie das Pulldown-Menü, um eine Auswahl zu treffen *oder mehr* Basissprachen aus den verfügbaren Sprachen: Deutsch, Italienisch, Französisch, Japanisch, Spanisch, Portugiesisch (Brasilien), Chinesisch (Traditionell) und Chinesisch (vereinfacht). Für jede hinzugefügte Sprache wird eine Community-Site erstellt, die gemäß den Best Practices unter [Übersetzen von Inhalten für mehrsprachige Sites](../../help/sites-administering/translation.md). Die Stammseite jeder Site enthält eine untergeordnete Seite mit dem Namen des Sprachcodes einer der ausgewählten Sprachen, z. B. &quot;en&quot;für Englisch oder &quot;fr&quot;für Französisch.

* **[!UICONTROL Community-Site-Name]**: `enable`

   * Die ursprüngliche URL wird unter dem Community-Site-Namen angezeigt.
   * für eine gültige URL einen Basissprachcode + &quot;.html&quot; anhängen.

      *Beispiel*, http://localhost:4502/content/sites/ `enable/en.html`

* **[!UICONTROL Referenz-Site-Vorlage]**: nach unten ziehen, um `Reference Structured Learning Site Template`

Wählen Sie **[!UICONTROL Weiter]** aus

### Schritt 2: Design {#step-design}

Der Schritt &quot;Design&quot;wird in zwei Abschnitten zur Auswahl des Designs und des Branding-Banners vorgestellt:

#### SITE-THEMA DER GEMEINSCHAFT {#community-site-theme}

Wählen Sie den gewünschten Stil aus, der auf die Vorlage angewendet werden soll. Wenn diese Option aktiviert ist, wird das Design mit einem Häkchen überlagert.

![enablementsitetheme](assets/enablementsitetheme.png)

#### GEMEINSCHAFTLICHE SITE-BRANCHE {#community-site-branding}

(Optional) Laden Sie ein Bannerbild hoch, das auf den Seiten der Site angezeigt werden soll. Das Banner wird zwischen der Community-Site-Kopfzeile und dem Menü (Navigationslinks) am linken Rand des Browsers fixiert. Die Bannerhöhe wird auf 120 Pixel zugeschnitten. Die Größe des Banners kann nicht an die Breite des Browsers und die Höhe von 120 Pixel angepasst werden.

![chlimage_1-284](assets/chlimage_1-284.png) ![chlimage_1](assets/chlimage_1.jpeg)

Wählen Sie **[!UICONTROL Weiter]** aus.

### Schritt 3: Einstellungen {#step-settings}

Im Schritt Einstellungen vor Auswahl von `Next`Beachten Sie, dass es sieben Abschnitte gibt, die Zugriff auf Konfigurationen bieten, die Benutzerverwaltung, Tagging, Rollen, Moderation, Analyse, Übersetzung und Aktivierung umfassen.

#### BENUTZERVERWALTUNG {#user-management}

Es wird empfohlen, [Aktivierungsgemeinschaften](overview.md#enablement-community) privat sein.

Eine Community-Site ist privat, wenn anonymen Site-Besuchern der Zugriff verweigert wird, sie sich möglicherweise nicht selbst registrieren und keine Anmeldung über soziale Netzwerke verwenden.

Stellen Sie sicher, dass die meisten Kontrollkästchen deaktiviert sind für [Benutzerverwaltung](sites-console.md#user-management):

* Website-Besuchern NICHT erlauben, sich selbst zu registrieren
* Anonyme Site-Besucher NICHT zum Anzeigen der Site zulassen
* Optional, ob Nachrichten unter Community-Mitgliedern zugelassen werden sollen oder nicht
* Anmeldung mit Facebook NICHT zulassen
* Anmeldung mit Twitter NICHT zulassen

![chlimage_1-285](assets/chlimage_1-285.png)

#### TAGGING {#tagging}

Die Tags, die auf Community-Inhalte angewendet werden können, werden durch die Auswahl AEM Namespaces gesteuert, die zuvor durch die [Tagging-Konsole](../../help/sites-administering/tags.md#tagging-console) (z. B. [Tutorial-Namespace](enablement-setup.md#create-tutorial-tags)).

Durch die Auswahl von Tag-Namespaces für die Community-Site wird außerdem die Auswahl eingeschränkt, die beim Definieren von Katalogen und Aktivierungsressourcen angezeigt wird. Siehe [Tagging von Aktivierungsressourcen](tag-resources.md) für wichtige Informationen.

Die Suche nach Namespaces ist mit der Typvorsuche einfach. Beispiel:

* Typ &#39;tut&#39;
* Klicken Sie auf `Tutorial`

![chlimage_1-286](assets/chlimage_1-286.png)

### ROLLEN {#roles}

[Community-Mitgliederrollen](users.md) werden über die Einstellungen im Abschnitt Rollen zugewiesen.

Damit ein Community-Mitglied (oder eine Gruppe von Mitgliedern) die Site als Community-Manager erleben kann, verwenden Sie die Typvorsuche und wählen Sie den Mitglied- oder Gruppennamen aus den Optionen in der Dropdown-Liste aus.

Beispiel:

* Typ &quot;q&quot;
* Auswählen [Quinn Harper](enablement-setup.md#publishcreateenablementmembers)

>[!NOTE]
>
>[Tunneldienst](deploy-communities.md#tunnel-service-on-author) ermöglicht die Auswahl von Mitgliedern und Gruppen, die nur in der Veröffentlichungsumgebung vorhanden sind.

![community_roles](assets/community_roles.png)

#### MODERATION {#moderation}

Globale Standardeinstellungen akzeptieren für [moderieren](sites-console.md#moderation) benutzergenerierte Inhalte (UGC).

![chlimage_1-287](assets/chlimage_1-287.png)

#### ANALYTICS {#analytics}

Wählen Sie aus dem Pulldown-Menü das für diese Community-Site konfigurierte Analytics Cloud Service-Framework aus.

Die im Screenshot angezeigte Auswahl, `Communities`, ist ein Framework-Beispiel aus der [Konfigurationsdokumentation.](analytics.md#aem-analytics-framework-configuration)

![chlimage_1-288](assets/chlimage_1-288.png)

#### ÜBERSETZUNG {#translation}

Die [Übersetzungsparameter](sites-console.md#translation) Geben Sie an, ob UGC übersetzt werden darf und in welche Sprache, falls ja.

* Überprüfen **[!UICONTROL Maschinelle Übersetzung zulassen]**
* Standardeinstellungen verwenden

![chlimage_1-289](assets/chlimage_1-289.png)

#### AKTIVIERUNG {#enablement}

Für eine Aktivierungs-Community ist es erforderlich, einen oder mehrere Community-Aktivierungsmanager zu identifizieren.

* **[!UICONTROL Aktivierungsmanager]**
(erforderlich) Mitglieder der 
`Community Enablement Managers` zur Verwaltung dieser Community-Site ausgewählt werden.

   * Typ &quot;s&quot;
   * Klicken Sie auf `Sirius Nilson`

* **[!UICONTROL Marketing Cloud-Organisations-ID]**
(optional) Die Kennung für ein Adobe Analytics-Konto, die erforderlich ist, wenn [Video Heartbeat Analytics](analytics.md#video-heartbeat-analytics) in der Aktivierungsberichterstellung.

![chlimage_1-290](assets/chlimage_1-290.png)

Wählen Sie **[!UICONTROL Weiter]** aus.

### Schritt 4: Community-Site erstellen {#step-create-community-site}

Wählen Sie **[!UICONTROL Erstellen]** aus.

![chlimage_1-291](assets/chlimage_1-291.png)

Nach Abschluss des Vorgangs wird der Ordner für die neue Site in der Konsole Communities - Sites angezeigt.

![enablementsitecreated](assets/enablementsitecreated.png)

### Veröffentlichen der neuen Community-Site {#publish-the-new-community-site}

Die erstellte Site sollte über die Konsole Communities - Sites verwaltet werden. Dieselbe Konsole, von der aus neue Sites erstellt werden können.

Nachdem Sie den Ordner der Community-Site ausgewählt haben, halten Sie den Mauszeiger über das Site-Symbol, sodass vier Aktionssymbole angezeigt werden:

![siteactionicons](assets/siteactionicons.png)

Bei Auswahl des Ellipsensymbols (Symbol &quot;Mehr Aktionen&quot;) werden die Optionen &quot;Site exportieren&quot;und &quot;Site löschen&quot;angezeigt.

![siteactionsnew](assets/siteactionsnew.png)

Von links nach rechts sind sie:

* **Seite öffnen**
Wählen Sie das Stiftsymbol aus, um die Community-Site im Bearbeitungsmodus für Autoren zu öffnen, um Seitenkomponenten hinzuzufügen und/oder zu konfigurieren

* **Site bearbeiten**
Wählen Sie das Eigenschaftensymbol aus, um die Community-Site zur Änderung von Eigenschaften wie dem Titel oder zum Ändern des Designs zu öffnen.

* **Website veröffentlichen**
Wählen Sie das Weltsymbol aus, um die Community-Site zu veröffentlichen (standardmäßig localhost:4503).

* **Export-Site**
Wählen Sie das Exportsymbol aus, um ein Paket der Community-Site zu erstellen, das beide in gespeichert ist. [Package Manager](../../help/sites-administering/package-manager.md) und heruntergeladen.

   Beachten Sie, dass UGC nicht im Site-Paket enthalten ist.

* **Site löschen**
Um die Community-Site zu löschen, wählen Sie das Symbol Site löschen aus, das angezeigt wird, wenn Sie den Mauszeiger über die Site in der Communities-Site-Konsole bewegen. Mit dieser Aktion werden alle mit der Site verknüpften Elemente entfernt, z. B. benutzergenerierte Inhalte, Benutzergruppen, Assets und Datenbankdatensätze.

![enablesiteactions](assets/enablesiteactions.png)

#### Veröffentlichung auswählen {#select-publish}

Wählen Sie das Weltsymbol aus, um die Community-Site zu veröffentlichen.

![chlimage_1-292](assets/chlimage_1-292.png)

Es wird ein Hinweis geben, dass die Website veröffentlicht wurde.

![chlimage_1-293](assets/chlimage_1-293.png)

## Community-Benutzer und Benutzergruppen {#community-users-user-groups}

### Neue Community-Benutzergruppen {#notice-new-community-user-groups}

Zusammen mit der neuen Community-Site werden neue Benutzergruppen erstellt, die über die entsprechenden Berechtigungen für verschiedene Verwaltungsfunktionen verfügen. Weitere Informationen finden Sie unter [Benutzergruppen für Community-Sites](users.md#usergroupsforcommunitysites).

Für diese neue Community-Site können die neuen Benutzergruppen, die in der Veröffentlichungsumgebung vorhanden sind, unter Berücksichtigung des Site-Namens &quot;Aktivieren&quot;in Schritt 1 aus dem [Communities Mitglieder &amp; Gruppen-Konsole](members.md#groups-console):

![chlimage_1-294](assets/chlimage_1-294.png)

### Zuweisen von Mitgliedern zur Community Aktivieren-Gruppe {#assign-members-to-community-enable-members-group}

Wenn der Tunnel-Dienst für die Autoreninstanz aktiviert ist, kann die [bei der Ersteinrichtung erstellte Benutzer](enablement-setup.md#publishcreateenablementmembers) zur Community-Mitgliedergruppe für die neu erstellte Community-Site.

Über die Community-Gruppenkonsole können Mitglieder einzeln hinzugefügt oder über die Mitgliedschaft in einer Gruppe hinzugefügt werden.

In diesem Beispiel wird die Gruppe `Community Ski Class` wird als Mitglied der Gruppe hinzugefügt `Community Enable Members` sowie Mitglied `Quinn Harper`.

* Navigieren Sie zu **[!UICONTROL Communities > Gruppen]** console
* Auswählen **[!UICONTROL Community-Aktivierte Mitglieder]** Gruppe
* Eingabe `ski` in **[!UICONTROL Mitglieder zu Gruppe hinzufügen]** Suchfeld
* Auswählen **[!UICONTROL Community-Ski-Klasse]** (Gruppe der Lernenden)
* Eingabe `quinn` in das Suchfeld
* Auswählen **[!UICONTROL Quinn Harper]** (Kontakt für Aktivierungsressource)

* Wählen Sie **[!UICONTROL Speichern]** aus

![chlimage_1-295](assets/chlimage_1-295.png)

## Veröffentlichungskonfigurationen {#configurations-on-publish}

### http://localhost:4503/content/sites/enable/en.html {#http-localhost-content-sites-enable-en-html}

![chlimage_1-296](assets/chlimage_1-296.png)

### Authentifizierungsfehler konfigurieren {#configure-for-authentication-error}

Sobald eine Site konfiguriert und zur Veröffentlichung gepusht wurde, [Anmeldezuordnung konfigurieren](sites-console.md#configure-for-authentication-error) ( `Adobe Granite Login Selector Authentication Handler`) in der Veröffentlichungsinstanz. Der Vorteil besteht darin, dass bei nicht korrekter Eingabe der Anmeldedaten der Authentifizierungsfehler die Anmeldeseite der Community-Site mit einer Fehlermeldung erneut anzeigt.

Hinzufügen einer `Login Page Mapping` as

* /content/sites/enable/en/signin:/content/sites/enable/en

### (Optional) Ändern der Standard-Startseite {#optional-change-the-default-home-page}

Wenn Sie zur Veranschaulichung mit der Veröffentlichungs-Site arbeiten, kann es nützlich sein, die standardmäßige Startseite auf die neue Site zu ändern.

Dazu müssen Sie Folgendes verwenden: [CRX|DE](http://localhost:4503/crx/de) Lite zum Bearbeiten [Ressourcenzuordnung](../../help/sites-deploying/resource-mapping.md) -Tabelle auf der Veröffentlichungsinstanz.

Erste Schritte

1. Greifen Sie beim Veröffentlichen auf CRXDE zu und melden Sie sich mit Administratorrechten an

   * Navigieren Sie beispielsweise zu [http://localhost:4503/crx/de](http://localhost:4503/crx/de) und melden Sie sich mit `admin/admin`

1. Erweitern Sie im Projektbrowser die `/etc/map`
1. Wählen Sie den `http`-Knoten aus

   * Auswählen **[!UICONTROL Knoten erstellen]**

      * **Name** localhost.4503

         (Do *not* use `:`)

      * **Typ** [sling:Mapping](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)

1. Mit neu erstellt `localhost.4503` Knoten ausgewählt

   * Eigenschaft hinzufügen

      * **Name** sling:match
      * **Typ** Zeichenfolge
      * **Wert** localhost.4503/\$

         (Muss mit &#39;$&#39; char enden)
   * Eigenschaft hinzufügen

      * **Name** sling:internalRedirect
      * **Typ** Zeichenfolge
      * **Wert** /content/sites/enable/en.html


1. Klicken Sie auf **[!UICONTROL Alle speichern]**
1. (optional) Löschen des Browser-Verlaufs
1. Navigieren Sie zu http://localhost:4503/

   * Ankunft unter http://localhost:4503/content/sites/enable/en.html

>[!NOTE]
>
>Um zu deaktivieren, fügen Sie einfach der `sling:match` Eigenschaftswert mit einem &quot;x&quot;- `xlocalhost.4503/$` - und **[!UICONTROL Alle speichern]**.

![chlimage_1-297](assets/chlimage_1-297.png)

#### Fehlerbehebung: Fehler beim Speichern der Karte {#troubleshooting-error-saving-map}

Wenn Änderungen nicht gespeichert werden können, stellen Sie sicher, dass der Knotenname `localhost.4503`, mit einem &quot;Punkt&quot;-Trennzeichen und nicht `localhost:4503` mit einem &quot;Doppelpunkt&quot;-Trennzeichen `localhost`ist kein gültiges Namespace-Präfix.

![chlimage_1-298](assets/chlimage_1-298.png)

#### Fehlerbehebung: Fehler bei Umleitung {#troubleshooting-fail-to-redirect}

Der **$**&quot; am Ende des regulären Ausdrucks `sling:match`Zeichenfolge ist von entscheidender Bedeutung, sodass nur genau `http://localhost:4503/` zugeordnet ist, wird der Umleitungswert ansonsten jedem Pfad vorangestellt, der nach der Datei server:port in der URL vorhanden sein könnte. Wenn AEM also versucht, zur Anmeldeseite umzuleiten, schlägt dies fehl.

## Ändern der Community-Site {#modifying-the-community-site}

Nachdem die Site ursprünglich erstellt wurde, können Autoren die [Symbol &quot;Site öffnen&quot;](sites-console.md#authoring-site-content) , um standardmäßige AEM zu erstellen.

Administratoren können außerdem die [Symbol &quot;Site bearbeiten&quot;](sites-console.md#modifying-site-properties) , um Eigenschaften der Site zu ändern, z. B. den Titel.

Denken Sie nach jeder Änderung daran, **Speichern** und erneute **Veröffentlichen** die Site.

>[!NOTE]
>
>Wenn Sie nicht mit AEM vertraut sind, lesen Sie die Dokumentation unter [grundlegende Handhabung](../../help/sites-authoring/basic-handling.md) und [Kurzanleitung zum Erstellen von Seiten](../../help/sites-authoring/qg-page-authoring.md).

### Hinzufügen eines Katalogs {#add-a-catalog}

Die für diese Community-Site ausgewählte Community-Site-Vorlage sollte die Katalogfunktion enthalten.

Ist dies nicht der Fall, kann die Katalogfunktion einfach hinzugefügt werden. Dadurch können andere Mitglieder der Community, die nicht Aktivierungsressourcen oder Lernpfaden zugewiesen sind, Aktivierungsressourcen aus einem Katalog auswählen.

Wenn die Site-Struktur bereits die Katalogfunktion enthält, kann deren Titel geändert werden.

Um die Struktur der Site zu ändern, navigieren Sie zum **[!UICONTROL Communities, Sites]** Konsole, öffnen Sie die `enable` und wählen Sie die **Site bearbeiten** -Symbol, um auf die Eigenschaften von `Enablement Tutorial`.

Wählen Sie das Bedienfeld STRUKTUR aus, um einen Katalog hinzuzufügen oder einen vorhandenen Katalog zu ändern:

* **Titel**: `Ski Catalog`

* **URL**: `catalog`

* **Alle Namespaces auswählen**: Behalten Sie die Standardeinstellung bei.
* Wählen Sie **[!UICONTROL Speichern]** aus

![chlimage_1-299](assets/chlimage_1-299.png)

Verwenden Sie das Symbol Position , um die Katalogfunktion nach den Zuweisungen an die zweite Position zu verschieben.

![chlimage_1-300](assets/chlimage_1-300.png)

Auswählen **[!UICONTROL Speichern]** in der oberen rechten Ecke, um die Änderungen an der Community-Site zu speichern.

Dann erneut **Veröffentlichen** die Site.
