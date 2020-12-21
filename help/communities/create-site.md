---
title: Erstellen einer neuen Community-Site
seo-title: Erstellen einer neuen Community-Site
description: Erstellen einer neuen AEM Communities-Site
seo-description: Erstellen einer neuen AEM Communities-Site
uuid: b8557416-cae4-489e-ab3b-e94d56686b7a
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: bf182bb7-e305-45be-aadb-d71efd70f8cb
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c
workflow-type: tm+mt
source-wordcount: '1649'
ht-degree: 3%

---


# Erstellen einer neuen Community-Site {#author-a-new-community-site}

## Neue Community-Site {#create-a-new-community-site} erstellen

Verwenden Sie die Autoreninstanz, um eine neue Community-Site zu erstellen

* Anmelden mit Administratorberechtigungen
* Aus globaler Navigation: **[!UICONTROL Navigation > Communities > Sites]**

Die Communities Sites-Konsole bietet einen Assistenten, der Sie durch die Schritte zum Erstellen einer Community-Site führt. Es ist möglich, zum Schritt `Next`oder `Back`zum vorherigen Schritt vorzugehen, bevor Sie die Site im letzten Schritt verpflichten.

So erstellen Sie eine neue Community-Site:

* Klicken Sie auf die Schaltfläche `Create`

![createcommunitysite](assets/createcommunitysite.png)

### Schritt 1: Site-Vorlage {#step-site-template}

![createsitetemplate63](assets/createsitetemplate63.png)

Geben Sie im Schritt [Site-Vorlage](sites-console.md#step2013asitetemplate) einen Titel, eine Beschreibung und den Namen für die URL ein und wählen Sie eine Community-Site-Vorlage aus, z. B.:

* **[!UICONTROL Community-Site-Titel]**: `Getting Started Tutorial`

* **[!UICONTROL Community-Site-Beschreibung]**: `A site for engaging with the community.`

* **[!UICONTROL Community-Site-Stammordner]**: (Leer lassen für Standard-Stammordner  `/content/sites`)

* **[!UICONTROL Cloud-Konfigurationen]**: (leer lassen, wenn keine Cloud-Konfigurationen angegeben wurden) Geben Sie den Pfad zu den angegebenen Cloud-Konfigurationen an.
* **[!UICONTROL Community-Site-Basissprache]**: (Für eine Sprache unberührt lassen: Englisch) verwenden Sie das Pulldown-Menü, um eine  *oder* mehr Basissprachen aus den verfügbaren Sprachen Deutsch, Italienisch, Französisch, Japanisch, Spanisch, Portugiesisch (Brasilien), Chinesisch (Traditionell) und Chinesisch (vereinfacht) auszuwählen. Eine Community-Site wird für jede hinzugefügte Sprache erstellt und befindet sich im selben Site-Ordner, wie unter [Übersetzung von Inhalten für mehrsprachige Sites](../../help/sites-administering/translation.md) beschrieben. Die Stammseite jeder Site enthält eine untergeordnete Seite, die nach dem Sprachcode einer der ausgewählten Sprachen benannt ist, wie z.B. &quot;en&quot; für Englisch oder &quot;fr&quot; für Französisch.

* **[!UICONTROL Community-Site-Name]**: take

   * Überprüfen Sie die Dublette, da der Name nach der Erstellung der Site nicht leicht geändert werden kann.
   * Die anfängliche URL wird unter dem Site-Namen der Community angezeigt
   * Für eine gültige URL hängen Sie einen Basissprachcode an + &quot;.html&quot;
   * *Beispiel*: http://localhost:4502/content/sites/  `engage/en.html`

* **[!UICONTROL Vorlage]**: nach unten ziehen  `Reference Site`

Wählen Sie **[!UICONTROL Weiter]** aus

### Schritt 2: Design {#step-design}

Der Schritt &quot;Design&quot;wird in zwei Abschnitten zur Auswahl des Designs und des Branding-Banners angezeigt:

#### COMMUNITY SITE-THEMA {#community-site-theme}

Wählen Sie den gewünschten Stil aus, der auf die Vorlage angewendet werden soll. Wenn diese Option aktiviert ist, wird das Design mit einem Häkchen überlagert.

![sitetheme](assets/sitetheme.png)

#### COMMUNITY SITE BRANDING {#community-site-branding}

(Optional) Laden Sie ein Bannerbild hoch, das auf den Seiten der Site angezeigt wird. Das Banner wird am linken Rand des Browsers zwischen dem Community-Site-Header und dem Menü (Navigationslinks) fixiert. Die Bannerhöhe wird auf 120 Pixel zugeschnitten. Die Größe des Banners wird nicht an die Breite des Browsers und die Höhe von 120 Pixel angepasst.

![chlimage_1-353](assets/chlimage_1-353.png) ![chlimage_1-354](assets/chlimage_1-354.png)

Wählen Sie **[!UICONTROL Weiter]** aus.

### Schritt 3: Einstellungen {#step-settings}

Beachten Sie, dass im Schritt &quot;Einstellungen&quot;vor der Auswahl von `Next` sieben Abschnitte den Zugriff auf Konfigurationen bieten, die unter anderem Benutzerverwaltung, Tagging, Moderation, Gruppenverwaltung, Analyse, Übersetzung und Aktivierung umfassen.

Besuchen Sie das Tutorial [Erste Schritte mit AEM Communities für Aktivierung](getting-started-enablement.md), um mehr über die Arbeit mit den Aktivierungsfunktionen zu erfahren.

#### BENUTZERVERWALTUNG {#user-management}

Aktivieren Sie alle Kontrollkästchen für [Benutzerverwaltung](sites-console.md#user-management)

* So erlauben Sie Site-Besuchern, sich selbst zu registrieren
* So können Site-Besucher die Site anzeigen, ohne sich anmelden zu müssen
* So ermöglichen Sie es Mitgliedern, Nachrichten von anderen Community-Mitgliedern zu senden und zu empfangen
* So lassen Sie die Anmeldung bei Facebook zu, anstatt sich zu registrieren und ein Profil zu erstellen
* So lassen Sie die Anmeldung bei Twitter statt der Registrierung und Erstellung eines Profils zu

>[!NOTE]
>
>Für eine Produktions-Umgebung ist es erforderlich, benutzerdefinierte Facebook- und Twitter-Anwendungen zu erstellen. Siehe [Social-Anmeldung bei Facebook und Twitter](social-login.md).

![createsitesettings](assets/createsitesettings.png)

#### TAGGGING {#tagging}

Die Tags, die auf Community-Inhalte angewendet werden können, werden gesteuert, indem Sie AEM Namensraum auswählen, die zuvor über die [Tagging-Konsole](../../help/sites-administering/tags.md#tagging-console) definiert wurden (z. B. den [Tutorial-Namensraum](setup.md#create-tutorial-tags)).

Die Suche nach Namensräumen ist mit der Typenvorschau einfach. Beispiel:

* Typ &#39;tut&#39;
* Wählen Sie nun eine der folgenden Optionen aus `Tutorial`

![chlimage_1-355](assets/chlimage_1-355.png)

#### ROLLEN {#roles}

[Community-Mitglieder ](users.md) Rollen werden über die Einstellungen im Abschnitt Rollen zugewiesen.

Damit ein Community-Mitglied (oder eine Gruppe von Mitgliedern) die Site als Community-Manager erleben kann, verwenden Sie die &quot;Type-ahead&quot;-Suche und wählen Sie den Mitglieds- oder Gruppennamen aus den Optionen in der Dropdown-Liste aus.

Beispiel:

* Typ &quot;q&quot;
* Wählen Sie [Quinn Harper](enablement-setup.md#publishcreateenablementmembers)

>[!NOTE]
>
>[Der Tunnel-](https://helpx.adobe.com/experience-manager/6-3/communities/using/deploy-communities.html#tunnel-service-on-author) Dienst ermöglicht die Auswahl von Mitgliedern und Gruppen, die nur in der Umgebung &quot;Veröffentlichen&quot;vorhanden sind.

![community_roles-1](assets/community_roles-1.png)

#### MODERATION {#moderation}

Übernehmen Sie die globalen Standardeinstellungen für [Moderation](sites-console.md#moderation) Benutzergenerierte Inhalte (UGC).

![chlimage_1-356](assets/chlimage_1-356.png)

#### ANALYTICS {#analytics}

Wenn Adobe Analytics lizenziert ist und ein Analytics-Cloud-Dienst und -Framework konfiguriert wurden, können Sie Analytics aktivieren und das Framework auswählen.

Siehe [Analytics-Konfiguration für Communities-Funktionen](analytics.md).

![chlimage_1-357](assets/chlimage_1-357.png)

#### TRANSLATION {#translation}

Die [Übersetzungseinstellungen](sites-console.md#translation) geben die Basissprache für die Site sowie ggf. an, ob UGC übersetzt werden darf und in welche Sprache.

* **[!UICONTROL Maschinelle Übersetzung zulassen]**
* Lassen Sie Standardsprachen für die Übersetzung vom standardmäßigen maschinellen Übersetzungsdienst ausgewählt
* Übersetzungsdienstleister und Konfiguration beibehalten
* Ein globaler Store ist nicht erforderlich, da es keine Sprachkopien gibt
* Wählen Sie **[!UICONTROL Gesamte Seite]**
* Standardpersistenzoption deaktivieren

![chlimage_1-358](assets/chlimage_1-358.png)

#### AKTIVIERUNG {#enablement}

Lassen Sie beim Erstellen einer Interaktionsgemeinschaft leer.

Eine ähnliche Übung zum schnellen Erstellen einer [Aktivierungs-Community](overview.md#enablement-community) finden Sie unter [Erste Schritte mit AEM Communities für Aktivierung](getting-started-enablement.md).

Wählen Sie **[!UICONTROL Weiter]** aus.

### Schritt 4: Communities-Site {#step-create-communities-site} erstellen

Wählen Sie **[!UICONTROL Erstellen]**.

![chlimage_1-359](assets/chlimage_1-359.png)

Nach Abschluss des Prozesses wird der Ordner für die neue Site in der Konsole Communities - Sites angezeigt.

![communitiessitesconsole](assets/communitiessitesconsole.png)

## Veröffentlichen der neuen Community-Site {#publish-the-new-community-site}

Die erstellte Site sollte über die Communities - Sites-Konsole verwaltet werden, in der auch neue Sites erstellt werden können.

Nachdem Sie den Ordner der Community-Site ausgewählt haben, um ihn zu öffnen, halten Sie den Mauszeiger über das Site-Symbol, sodass vier Aktionssymbole angezeigt werden:

![siteactionicons-1](assets/siteactionicons-1.png)

Wenn Sie das vierte Auslassungszeichen auswählen (Mehr Aktionen), werden die Optionen &quot;Site exportieren&quot;und &quot;Site löschen&quot;angezeigt.

![sitteactionsnew-1](assets/siteactionsnew-1.png)

Von links nach rechts:

* **Öffnen Sie**
SiteWählen Sie das Stiftsymbol, um die Community-Site im Autorenbearbeitungsmodus zu öffnen, um Seitenkomponenten hinzuzufügen und/oder zu konfigurieren

* **Bearbeiten**
von SiteWählen Sie das Symbol Eigenschaften, um die Community-Site zum Ändern von Eigenschaften wie dem Titel oder zum Ändern des Designs zu öffnen

* **Veröffentlichen**
von SiteWählen Sie das Symbol Welt, um die Community-Site zu veröffentlichen (z. B. wenn Ihr Veröffentlichungsserver auf Ihrem lokalen Computer ausgeführt wird, dann standardmäßig auf localhost:4503)

* **Exportieren**
von SiteWählen Sie das Exportsymbol, um ein Paket der Community-Site zu erstellen, das sowohl im  [Paket-Management gespeichert als auch ](../../help/sites-administering/package-manager.md) heruntergeladen wird.

   Beachten Sie, dass UGC nicht im Site-Paket enthalten ist.

* **Site löschen**

   Wählen Sie das Symbol zum Löschen aus, um die Community-Site in **[!UICONTROL Communities > Sites console]** zu löschen. Durch diese Aktion werden alle mit der Site verknüpften Elemente entfernt, z. B. UGC, Benutzergruppen, Assets und Datenbankdatensätze.

![siteactions-1](assets/siteactions-1.png)

>[!NOTE]
>
>Wenn Sie nicht den Standardanschluss 4503 für die Instanz im Veröffentlichungsmodus verwenden, bearbeiten Sie den standardmäßigen Replizierungsagenten, um die Anschlussnummer auf den richtigen Wert festzulegen.
>
>Auf der Autoreninstanz über das Hauptmenü
>
>1. Navigieren Sie zum Menü **[!UICONTROL Tools > Vorgänge > Replikation]**
>1. Wählen Sie **[!UICONTROL Agenten auf Autor]**
>1. Wählen Sie **[!UICONTROL Standardagent (publish)]**
>1. Wählen Sie neben **[!UICONTROL Einstellungen]** **[!UICONTROL Bearbeiten]**
>1. Wählen Sie im Popup-Dialogfeld für Agenteneinstellungen die Registerkarte Transport.
>1. Ändern Sie im URI die Anschlussnummer 4503 in die gewünschte Anschlussnummer.

>
>
So verwenden Sie z. B. Port 6103: `http://localhost:6103/bin/receive?sling:authRequestLogin=1`
>
>1. Wählen Sie **[!UICONTROL OK]** aus
>1. (Optional) Wählen Sie `Clear` oder `Force Retry` aus, um die Replikationswarteschlange zurückzusetzen


### Wählen Sie Veröffentlichen {#select-publish}

Nachdem Sie sichergestellt haben, dass der Veröffentlichungsserver ausgeführt wird, wählen Sie das Symbol Welt, um die Community-Site zu veröffentlichen.

![chlimage_1-360](assets/chlimage_1-360.png)

Wenn die Community-Site erfolgreich veröffentlicht wurde, wird eine kurze Nachricht angezeigt:

![chlimage_1-361](assets/chlimage_1-361.png)

### Neue Community-Benutzergruppen {#notice-new-community-user-groups}

Neben der neuen Community-Site werden neue Benutzergruppen erstellt, die über die entsprechenden Berechtigungen für verschiedene Verwaltungsfunktionen verfügen. Weitere Informationen finden Sie unter [Benutzergruppen für Community-Sites](users.md#usergroupsforcommunitysites).

Für diese neue Community-Site können die vier neuen Benutzergruppen unter dem Site-Namen &quot;locken&quot;in Schritt 1 aus der [Gruppenkonsole](members.md) (globale Navigation: Communities, Gruppen):

* Community-Manager für Interaktionen
* Community-Gruppenadministratoren
* Community-Interaktionsmitglieder
* Community-Interaktionsmoderatoren
* Community-Interaktion mit privilegierten Mitgliedern
* Community Interagieren von SiteContent Manager

Beachten Sie, dass [Aaron McDonald](tutorials.md#demo-users) Mitglied von

* Community-Manager für Interaktionen
* Community-Interaktionsmoderatoren
* Community-Interage-Mitglieder (indirekt als Mitglied der Moderatoren-Gruppe)

![chlimage_1-362](assets/chlimage_1-362.png)

#### http://localhost:4503/content/sites/engage/en.html {#http-localhost-content-sites-engage-en-html}

![chlimage_1-363](assets/chlimage_1-363.png)

## Konfigurieren für Authentifizierungsfehler {#configure-for-authentication-error}

Nachdem eine Site konfiguriert und zur Veröffentlichung gesendet wurde, konfigurieren Sie die Anmeldezuordnung [für die Veröffentlichungsinstanz ](sites-console.md#configure-for-authentication-error) ( `Adobe Granite Login Selector Authentication Handler`). Der Vorteil besteht darin, dass bei nicht korrekter Eingabe der Anmeldedaten der Authentifizierungsfehler die Anmeldeseite der Community-Site mit einer Fehlermeldung erneut anzeigt.

hinzufügen ein `Login Page Mapping` als

* /content/sites/engagement/de/signin:/content/sites/engagement/de

## Optionale Schritte {#optional-steps}

### Standardmäßige Startseite {#change-the-default-home-page} ändern

Wenn Sie zu Demonstrationszwecken mit der Veröffentlichungs-Site arbeiten, ist es ggf. sinnvoll, die standardmäßige Startseite auf die neue Site zu ändern.

Hierzu müssen Sie [CRXDE](http://localhost:4503/crx/de) Lite verwenden, um die [Ressourcenzuordnung](../../help/sites-deploying/resource-mapping.md)-Tabelle bei der Veröffentlichung zu bearbeiten.

Erste Schritte:

1. Melden Sie sich bei der Veröffentlichung mit Administratorrechten an
1. Gehen Sie zu [http://localhost:4503/crx/de](http://localhost:4503/crx/de)
1. Erweitern Sie im Projektbrowser `/etc/map`
1. Wählen Sie den Knoten `http`

   * Wählen Sie **[!UICONTROL Knoten erstellen]**

      * **** Namelocalhost.4503

         (do *not* use `:`)

      * **** [Typisierung:Zuordnung](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)

1. Mit neu erstelltem `localhost.4503`-Knoten ausgewählt

   * hinzufügen

      * **Name** sling:match
      * **** TypeString
      * **Wert** localhost.4503/\$

         (muss mit &#39;$&#39; Zeichen enden)
   * hinzufügen

      * **Name** sling:internalRedirect
      * **** TypeString
      * **Wert** /content/sites/engage/en.html


1. Wählen Sie **[!UICONTROL Alle speichern]**
1. (Optional) Löschen des Browserverlaufs
1. Navigieren Sie zu http://localhost:4503/

   * Ankunft unter http://localhost:4503/content/sites/engage/en.html

>[!NOTE]
>
>Um diese Option zu deaktivieren, setzen Sie einfach den Wert der Eigenschaft `sling:match` mit einem Wert &#39;x&#39; - `xlocalhost.4503/$` - und **[!UICONTROL Alle speichern]** voran.

![chlimage_1-364](assets/chlimage_1-364.png)

#### Fehlerbehebung: Fehler beim Speichern der Map {#troubleshooting-error-saving-map}

Wenn Änderungen nicht gespeichert werden können, stellen Sie sicher, dass der Knotenname `localhost.4503` mit einem Punkt-Trennzeichen und nicht `localhost:4503` mit einem Doppelpunkt-Trennzeichen ist, da `localhost`kein gültiges Namensraum-Präfix ist.

![chlimage_1-365](assets/chlimage_1-365.png)

#### Fehlerbehebung: Fehler bei Umleitung {#troubleshooting-fail-to-redirect}

Die Zeichenfolge &quot;**$**&quot;am Ende des regulären Ausdrucks `sling:match`ist ausschlaggebend, sodass nur genau `http://localhost:4503/` zugeordnet wird. Andernfalls wird der Umleitungswert jedem Pfad vorangestellt, der nach dem server:port in der URL existieren könnte. Wenn AEM also versucht, zur Anmeldeseite umzuleiten, schlägt sie fehl.

### Ändern Sie die Site {#modify-the-site}

Nachdem die Site zum ersten Mal erstellt wurde, können Autoren das [Symbol &quot;Site öffnen](sites-console.md#authoring-site-content)&quot;verwenden, um standardmäßige AEM Authoring-Aktivitäten durchzuführen.

Administratoren können außerdem das Symbol [Site bearbeiten](sites-console.md#modifying-site-properties) verwenden, um Eigenschaften der Site wie den Titel zu ändern.

Denken Sie nach jeder Änderung daran, **save** und **re-publish** die Site erneut zu veröffentlichen.

>[!NOTE]
>
>Wenn Sie mit AEM nicht vertraut sind, Ansicht der Dokumentation unter [basic handling](../../help/sites-authoring/basic-handling.md) und [quick guide to authoring pages](../../help/sites-authoring/qg-page-authoring.md).