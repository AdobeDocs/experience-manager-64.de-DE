---
title: Communities-Benutzersynchronisierung
seo-title: Communities-Benutzersynchronisierung
description: Funktionsweise der Benutzersynchronisierung
seo-description: Funktionsweise der Benutzersynchronisierung
uuid: 5b9bb7b6-9238-41f6-81da-84b9a303b9e2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 32b56b48-75cb-4cc9-a077-10e335f01a35
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '2508'
ht-degree: 13%

---


# Communities-Benutzersynchronisierung {#communities-user-synchronization}

## Einführung {#introduction}

In AEM Communities können *Site-Besucher* aus der Umgebung &quot;Veröffentlichen&quot;(je nach konfigurierter Berechtigung) *Mitglieder* werden, *Benutzergruppen* erstellen und ihr *Profil* bearbeiten.

*Benutzerdaten* sind Begriffe, mit denen auf  *Benutzer*,  *Benutzerprofile und* Benutzergruppen ** verwiesen wird.

** Membersis ist ein Begriff, der sich auf in der Umgebung &quot;Veröffentlichen&quot;registrierte  ** Benutzer bezieht, im Gegensatz zu in der Umgebung &quot;Autor&quot;registrierten Benutzern.

Weitere Informationen zu Benutzerdaten finden Sie unter [Verwalten von Benutzern und Benutzergruppen](users.md).

## Synchronisieren von Benutzern auf einer Veröffentlichungsfarm {#synchronizing-users-across-a-publish-farm}

Standardmäßig werden in der Umgebung &quot;Veröffentlichen&quot;erstellte Benutzerdaten nicht in der Umgebung &quot;Autor&quot;angezeigt.

Die meisten in der Authoring-Umgebung erstellten Benutzerdaten bleiben in der Autoreninstanz und werden nicht synchronisiert oder auf Veröffentlichungsinstanzen repliziert.

Wenn die [Topologie](topologies.md) eine [Veröffentlichungsfarm](../../help/sites-deploying/recommended-deploys.md#tarmk-farm) ist, müssen die Registrierung und die an einer Veröffentlichungsinstanz vorgenommenen Änderungen mit anderen Instanzen im Veröffentlichungsmodus synchronisiert werden. Mitglieder müssen sich anmelden und ihre Daten auf jedem Veröffentlichungsknoten anzeigen können.

Wenn die Benutzersynchronisierung aktiviert ist, werden die Benutzerdaten automatisch über die Instanzen im Veröffentlichungsmodus in der Farm hinweg synchronisiert.

### Anweisungen für die Benutzersynchronisierung {#user-sync-setup-instructions}

Detaillierte Anweisungen zum Aktivieren der Synchronisierung über eine Veröffentlichungsfarm hinweg finden Sie unter

* [Benutzersynchronisierung](../../help/sites-administering/sync.md)

## Benutzersynchronisierung im Hintergrund {#user-sync-in-the-background}

![sling-dist-workflow](assets/sling-dist-workflow.png)

* **VLT-Paket**: ist eine ZIP-Datei mit allen Änderungen, die an einem Herausgeber vorgenommen wurden und über Herausgeber verteilt werden müssen. Änderungen an einem Herausgeber generieren Ereignis, die vom Ereignis-Listener change ausgewählt werden. Dadurch wird ein vlt-Paket erstellt, das alle Änderungen enthält.

* **Verteilungspaket**: enthält Verteilungsinformationen für Sling. Das sind Informationen darüber, wo der Inhalt verteilt werden muss und wann er zuletzt verteilt wurde.

## Was passiert, wenn ... {#what-happens-when}

### Site aus Communities-Sites-Konsole {#publish-site-from-communities-sites-console} veröffentlichen

Wenn beim Autor eine Community-Site über die [Communities Sites Console](sites-console.md) veröffentlicht wird, hat dies zur Folge, dass [die verknüpften Seiten repliziert und Sling die dynamisch erstellten Community-Benutzergruppen einschließlich ihrer Mitgliedschaft verteilt.](../../help/sites-deploying/configuring.md#replication-reverse-replication-and-replication-agents)

### Profil &quot;Benutzer erstellt&quot;oder &quot;Bearbeitung&quot;bei Veröffentlichung {#user-is-created-or-edits-profile-on-publish}

Standardmäßig werden in der Umgebung &quot;Veröffentlichen&quot;erstellte Benutzer und Profil (z. B. durch Selbstregistrierung, Social-Login oder LDAP-Authentifizierung) nicht in der Umgebung &quot;Autor&quot;angezeigt.

Wenn die Topologie eine [Veröffentlichungsfarm](topologies.md) ist und die Benutzersynchronisierung korrekt konfiguriert wurde, werden das *user*- und *user-Profil* mithilfe der Sling-Distribution über die Veröffentlichungsfarm hinweg synchronisiert.

### Neue Community-Gruppe wird unter Veröffentlichen {#new-community-group-is-created-on-publish} erstellt

Obwohl sie von einer Instanz im Veröffentlichungsmodus initiiert wird, erfolgt die Erstellung einer Community-Gruppe, die zu neuen Site-Seiten und einer neuen Benutzergruppe führt, tatsächlich in der Autoreninstanz.

Während des Prozesses werden die neuen Siteseiten in alle Veröffentlichungsinstanzen repliziert. Die dynamisch erstellte Community-Benutzergruppe und ihre Mitgliedschaft werden an alle Veröffentlichungsinstanzen verteilt.

### Erstellung von Benutzern oder Benutzergruppen über die Sicherheitskonsole {#users-or-user-groups-are-created-using-security-console}

Per Design werden die in der Veröffentlichungsumgebung erstellten Benutzerdaten nicht in der Autorenumgebung angezeigt (und umgekehrt).

Wenn in der Veröffentlichungsumgebung neue Benutzer über die Konsole [Benutzerverwaltung und Sicherheit](../../help/sites-administering/security.md) hinzugefügt werden, werden die neuen Benutzer und ihre Gruppenmitgliedschaft im Rahmen der Benutzersynchronisierung ggf. mit anderen Veröffentlichungsinstanzen synchronisiert. Bei der Benutzersynchronisierung werden auch die über die Sicherheitskonsole erstellten Benutzergruppen synchronisiert.

### Inhalt von Benutzerbeiträgen bei der Veröffentlichung {#user-posts-content-on-publish}

Bei benutzergenerierten Inhalten (UGC) wird auf die in einer Veröffentlichungsinstanz eingegebenen Daten über das [konfigurierte SRP](srp-config.md) zugegriffen.

## Best Practices {#bestpractices}

Standardmäßig ist die Benutzersynchronisierung **deaktiviert**. Die Aktivierung der Benutzersynchronisierung beinhaltet die Änderung *vorhandener* OSGi-Konfigurationen. Aufgrund der Aktivierung der Benutzersynchronisierung sollten keine neuen Konfigurationen hinzugefügt werden.

Die Benutzersynchronisierung ist davon abhängig, dass die Autorenumgebung die Verteilung der Benutzerdaten verwaltet, auch wenn die Benutzerdaten nicht in der Autoreninstanz erstellt werden .

**Voraussetzungen**

1. Wenn Benutzer und Benutzergruppen bereits auf einem Herausgeber erstellt wurden, wird empfohlen, die Benutzerdaten vor der Konfiguration und Aktivierung der Benutzersynchronisierung [manuell zu synchronisieren](../../help/sites-administering/sync.md#manually-syncing-users-and-user-groups).

   Sobald die Benutzersynchronisierung aktiviert wurde, werden nur neu erstellte Benutzer und Gruppen synchronisiert .

1. Stellen Sie sicher, dass der neueste Code installiert wurde:

   * [AEM-Plattformupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=de)
   * [AEM Communities-Updates](deploy-communities.md#latestfeaturepack)

Die folgenden Konfigurationen sind erforderlich, um die Benutzersynchronisierung auf AEM Communities zu aktivieren. Stellen Sie sicher, dass diese Konfigurationen korrekt sind, damit die Verteilung von Sling-Inhalten nicht fehlschlägt.

### Apache Sling Distribution Agent – Sync Agents Factory {#apache-sling-distribution-agent-sync-agents-factory}

Diese Konfiguration ruft die Inhalte ab, die über die Herausgeber hinweg synchronisiert werden sollen. Die Konfiguration befindet sich in der Autoreninstanz. Der Autor muss alle Herausgeber, die vorhanden sind, verfolgen und alle Informationen synchronisieren.

Die Standardwerte in der Konfiguration beziehen sich auf eine einzelne Instanz im Veröffentlichungsmodus. Da die Benutzersynchronisierung zum Synchronisieren mehrerer Instanzen im Veröffentlichungsmodus nützlich ist, z. B. für eine Veröffentlichungsfarm, müssen der Konfiguration zusätzliche Instanzen im Veröffentlichungsmodus hinzugefügt werden.

**Wie werden die Inhalte synchronisiert?**

Die Autoreninstanz fügt den Endpunkt des Exporteurs von Herausgebern ein. Wenn ein Benutzer auf bestimmten Herausgebern (n) erstellt oder aktualisiert wird, ruft der Autor den Inhalt von seinen Exporteuren-Endpunkten ab und [schiebt den Inhalt](sync.md#main-pars-image-1413756164) in andere Herausgeber (n-1, d. h. nicht in die Herausgeber, von denen der Inhalt abgerufen wird).

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Konfigurieren der Konfiguration von Apache Sling Sync Agents

AEM Autoreninstanz:

1. Melden Sie sich mit Administratorrechten an.
1. Rufen Sie die [Webkonsole](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/configuring-osgi.html) auf.

   Beispiel: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
1. Suchen Sie nach **[!UICONTROL Apache Sling Distribution Agent - Sync Agents Factory]**.

   * Wählen Sie die vorhandene Konfiguration aus, die zur Bearbeitung geöffnet werden soll (Stiftsymbol).
   * Überprüfungsname: **`socialpubsync`.**
   * Aktivieren Sie das Kontrollkästchen **[!UICONTROL Aktiviert]**.
   * Wählen Sie **[!UICONTROL Mehrere Warteschlangen]** verwenden.
   * Geben Sie **[!UICONTROL Exporter-Endpunkte]** und **[!UICONTROL Importer-Endpunkte]** an (Sie können weitere Exporteur- und Importer-Endpunkte hinzufügen).

      Diese Endpunkte definieren, woher der Inhalt abgerufen werden soll und wohin der Inhalt verschoben werden soll. Der Autor ruft den Inhalt vom angegebenen Exporteur-Endpunkt ab und gibt den Inhalt an die Herausgeber weiter (mit Ausnahme des Herausgebers, von dem er den Inhalt abgerufen hat).
   ![sync-agent-fact](assets/sync-agent-fact.png)

### Adobe Granite Distribution – Encrypted Password Transport Secret Provider {#adobe-granite-distribution-encrypted-password-transport-secret-provider}

Dadurch kann der Autor den autorisierten Benutzer identifizieren, da er berechtigt ist, Benutzerdaten vom Autor zur Veröffentlichung zu synchronisieren.

Der auf allen Instanzen im Veröffentlichungsmodus erstellte [autorisierte Benutzer hilft Herausgebern, eine Verbindung mit dem Autor herzustellen und die Sling-Distribution für den Autor zu konfigurieren. ](../../help/sites-administering/sync.md#createauthuser) Dieser autorisierte Benutzer hat alle erforderlichen [ACLs](../../help/sites-administering/sync.md#howtoaddacl).

Wenn Daten auf Herausgebern installiert oder von diesen abgerufen werden sollen, stellt der Autor eine Verbindung mit den Herausgebern her, wobei die in dieser Konfiguration festgelegten Anmeldeinformationen (Benutzername und Kennwort) verwendet werden.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### So verbinden Sie Autoren mit Herausgebern mit autorisierten Benutzern

AEM Autoreninstanz:

1. Melden Sie sich mit Administratorrechten an.
1. Rufen Sie die [Webkonsole](../../help/sites-deploying/configuring-osgi.md) auf.

   Beispiel: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
1. Suchen Sie nach **[!UICONTROL Adobe Granite Distribution - Encrypted Password Transport Secret Provider]**.
1. Wählen Sie die vorhandene Konfiguration aus, die zur Bearbeitung geöffnet werden soll (Stiftsymbol).

   Überprüfungseigenschaft `name:` **`socialpubsync`\- `publishUser` .**
1. Legen Sie Benutzername und Kennwort auf [autorisierter Benutzer](../../help/sites-administering/sync.md#createauthorizeduser) fest.

   Beispiel: **`usersync`\-admin**

   ![granite-paswrd-trans](assets/granite-paswrd-trans.png)

### Apache Sling Distribution Agent – Queue Agents Factory {#apache-sling-distribution-agent-queue-agents-factory}

Diese Konfiguration wird verwendet, um die Daten zu konfigurieren, die Sie über Herausgeber hinweg synchronisieren möchten. Wenn Daten in Pfaden erstellt/aktualisiert werden, die unter **[!UICONTROL Zulässige Stammordner]** angegeben sind, wird &quot;var/community/distribution/diff&quot;aktiviert und der erstellte Replikator ruft die Daten von einem Herausgeber ab und installiert sie auf anderen Herausgebern.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### So konfigurieren Sie die zu synchronisierenden Daten (Knotenpfade)

In AEM Veröffentlichungsinstanz:

1. Melden Sie sich mit Administratorrechten an.
1. Rufen Sie die [Webkonsole](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/configuring-osgi.html) auf.

   Beispiel: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr).
1. Suchen Sie nach **[!UICONTROL Apache Sling Distribution Agent - Queue Agents Factory]**.
1. Wählen Sie die vorhandene Konfiguration aus, die zur Bearbeitung geöffnet werden soll (Stiftsymbol).

   Überprüfungsname: `socialpubsync` \-reverse.
1. Aktivieren Sie das Kontrollkästchen **[!UICONTROL Aktiviert]** und speichern Sie.
1. Geben Sie die Knotenpfade an, die in **[!UICONTROL Zulässige Wurzeln]** repliziert werden sollen.
1. Wiederholen Sie diese Schritte für jede `publish`-Instanz.

   ![queue-agents-fact](assets/queue-agents-fact.png)

### Adobe Granite Distribution – Diff Observer Factory {#adobe-granite-distribution-diff-observer-factory}

Bei dieser Konfiguration wird die Gruppenmitgliedschaft über Herausgeber hinweg synchronisiert.\
Wenn die Mitgliedschaft einer Gruppe in einem Herausgeber nicht auf andere Herausgeber aktualisiert wird, stellen Sie sicher, dass **ref:members** zu **ausgesuchten Eigenschaftennamen** hinzugefügt wird.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### So stellen Sie die Mitgliedersynchronisierung sicher

Auf jeder AEM Veröffentlichungsinstanz:

1. Melden Sie sich mit Administratorrechten an.
1. Rufen Sie die [Webkonsole](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/configuring-osgi.html) auf.

   Beispiel: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr).
1. Suchen Sie nach **[!UICONTROL Granite-Verteilung der Adobe - Diff Observer Factory]**.
1. Wählen Sie die vorhandene Konfiguration aus, die zur Bearbeitung geöffnet werden soll (Stiftsymbol).

   **[!UICONTROL Agentenname]** überprüfen: `socialpubsync` \-reverse&amp;ast;&amp;ast;.
1. Aktivieren Sie das Kontrollkästchen **[!UICONTROL Aktiviert]**.
1. Geben Sie **rep`:members`** als `description` für propertyName in **[!UICONTROL den Namen der gesuchten Eigenschaften]** an und speichern Sie.

   ![diff-obs](assets/diff-obs.png)

### Apache Sling Distribution Trigger – Scheduled Triggers Factory {#apache-sling-distribution-trigger-scheduled-triggers-factory}

Mit dieser Konfiguration können Sie das Abfrageintervall konfigurieren (nach dem Herausgeber gepingt und Änderungen vom Autor gezogen werden), um die Änderungen zwischen Herausgebern zu synchronisieren.

Der Autor fragt Herausgeber alle 30 Sekunden ab (Standard). Wenn Pakete im Ordner */var/sling/distribution/packages/ socialpubsync - vlt /shared* vorhanden sind, werden diese Pakete abgerufen und auf anderen Herausgebern installiert.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### So ändern Sie das Abfrageintervall

AEM Autoreninstanz:

1. Melden Sie sich mit Administratorrechten an.
1. Rufen Sie die [Webkonsole](../../help/sites-deploying/configuring-osgi.md) auf, z. B. [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
1. Suchen Sie nach **[!UICONTROL Apache Sling Distribution Trigger - Geplante Trigger Factory]**

   * Wählen Sie die vorhandene Konfiguration aus, die zur Bearbeitung geöffnet werden soll (Stiftsymbol)
   * `Name:` **`socialpubsync`\-geplanten-Trigger**
   * Legen Sie das Intervall in Sekunden auf das gewünschte Intervall fest und speichern Sie es.

   ![scheduled-trigger](assets/scheduled-trigger.png)

### AEM Communities User Sync Listener {#aem-communities-user-sync-listener}

Bei Problemen mit der Sling-Distribution, bei denen es zu einer Diskrepanz bei Abonnements und folgenden kommt, prüfen Sie, ob die folgenden Eigenschaften in den Konfigurationen für den AEM Communities-Benutzersynchronisierungs-Listener ]**festgelegt sind:**[!UICONTROL 

* NodeTypes
* IgnorableProperties
* IgnorableNodes
* DistributedFolders

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### So synchronisieren Sie Abonnements, Follower und Benachrichtigungen

Auf jeder AEM Veröffentlichungsinstanz:

1. Melden Sie sich mit Administratorrechten an.
1. Rufen Sie die [Webkonsole](../../help/sites-deploying/configuring-osgi.md) auf. Beispiel: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr).
1. Suchen Sie nach **[!UICONTROL AEM Communities User Sync Listener]**.
1. Wählen Sie die vorhandene Konfiguration aus, die zur Bearbeitung geöffnet werden soll (Stiftsymbol).

   Überprüfungsname: **`socialpubsync`\-geplanten-Trigger**
1. Legen Sie folgende **`NodeTypes`** fest:

   rep:User

   `nt` :unstructured

   `nt` :resource

   rep:ACL

   sling:Folder

   sling:OrderedFolder

   Die in dieser Eigenschaft angegebenen Node-Typen werden synchronisiert und die Benachrichtigungsinformationen (Blogs und Konfigurationen folgen) werden zwischen verschiedenen Herausgebern synchronisiert.
1. hinzufügen alle zu synchronisierenden Ordner in **[!UICONTROL DistributedFolders]**. Beispiel:

   segments/scoring

   social/relationships

   activities

1. Setzen Sie **`ignorablenodes`** auf:

   .tokens

   system

   rep `:cache` (da wir persistente Sitzungen verwenden, müssen wir diesen Knoten nicht mit anderen Herausgebern synchronisieren)

   ![user-sync-listner](assets/user-sync-listner.png)

### Eindeutige Sling-ID {#unique-sling-id}

AEM Autoreninstanz verwendet Sling-ID, um herauszufinden, woher die Daten kommen und an welche Herausgeber das Paket zurückgesendet werden muss (oder muss).

Vergewissern Sie sich, dass alle Herausgeber in einer Veröffentlichungsfarm über eine eindeutige Sling-ID verfügen. Wenn die Sling-ID für mehrere Instanzen im Veröffentlichungsmodus identisch ist, schlägt die Benutzersynchronisierung fehl. Da der Autor nicht wissen, wo das Paket abgeholt und wo das Paket installiert werden soll.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### So stellen Sie eine eindeutige Sling-ID für Herausgeber in der Veröffentlichungsfarm sicher

Bei jeder Veröffentlichungsinstanz:

1. Gehen Sie zu [https://_host:port_/system/console/status-slingsettings](http://localhost:4503/system/console/status-slingsettings).
1. Überprüfen Sie den Wert von **[!UICONTROL Sling-ID]**.

   ![slingid](assets/slingid.png)

   Wenn die Sling-ID einer Veröffentlichungsinstanz der Sling-ID einer anderen Veröffentlichungsinstanz entspricht, gehen Sie wie folgt vor:

1. Beenden Sie eine der Instanzen im Veröffentlichungsmodus, die über eine entsprechende Sling-ID verfügen.
1. Suchen und löschen Sie im Ordner `crx-quickstart/launchpad/felix` die Datei _sling.id.file.

   *zum Beispiel auf einem Linux-System:*

   `rm -i $(find . -type f -name sling.id.file)`

   *z. B. auf einem Windows-System:*

   `use windows explorer and search for _sling.id.file_`

1. Starten Sie die Veröffentlichungsinstanz. Beim Start wird ihm eine neue Sling-ID zugewiesen.
1. Überprüfen Sie, ob die **[!UICONTROL Sling-ID]** jetzt eindeutig ist.

Wiederholen Sie diese Schritte, bis alle Veröffentlichungsinstanzen über eine eindeutige Sling-ID verfügen.

### Vault Package Builder Factory {#vault-package-builder-factory}

Damit Updates ordnungsgemäß synchronisiert werden, müssen Sie den Vault Package Builder für die Benutzersynchronisierung ändern.\
In `/home/users` wird ein `/rep:cache`-Knoten erstellt. Es ist ein Cache, der verwendet wird, um zu finden, dass, wenn wir Abfrage auf den Hauptnamen eines Knotens, dann dieser Cache direkt verwendet werden kann.

Die Benutzersynchronisierung kann beendet werden, wenn `rep:cache `Knoten über Herausgeber hinweg synchronisiert werden.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### So stellen Sie sicher, dass Updates ordnungsgemäß über Herausgeber hinweg synchronisiert werden

Auf jeder AEM Veröffentlichungsinstanz:

1. Rufen Sie die [Webkonsole](../../help/sites-deploying/configuring-osgi.md) auf, z. B. [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr).
1. Suchen Sie den Namen **[!UICONTROL Apache Sling Distribution Packaging - Vault Package Builder Factory Builder]**: socialpubsync-vlt.
1. Wählen Sie das Bearbeitungssymbol aus.
1. hinzufügen zwei Filter des Pakets:

   * `/home/users|-.\*/.tokens`
   * `/home/users|**+**.\*/rep:cache`
1. Richtlinienverwaltung
   * Um vorhandene rep `:policy`-Knoten mit neuen zu überschreiben, fügen Sie einen dritten Paketfilter hinzu:

      `/home/users|**+**.\*/rep:policy`
   * Um zu verhindern, dass Richtlinien verteilt werden, setzen Sie

      Aktive Handhabung: IGNORE

![vault-package-builder-factory](assets/vault-package-builder-factory.png)

## Fehlerbehebung bei der Sling-Distribution in AEM Communities {#troubleshoot-sling-distribution-in-aem-communities}

Wenn die Sling-Verteilung fehlschlägt, führen Sie die folgenden Debugging-Schritte aus:

1. **Überprüfen Sie, ob  [falsche Konfigurationen](../../help/sites-administering/sync.md#improperconfig) hinzugefügt wurden.** Vergewissern Sie sich, dass nicht mehrere Konfigurationen hinzugefügt oder bearbeitet werden. Stattdessen sollten die vorhandenen Standardkonfigurationen bearbeitet werden.
1. **Konfigurationen** überprüfen. Stellen Sie sicher, dass alle [Konfigurationen](sync.md#bestpractices) in Ihrer AEM-Autoreninstanz entsprechend eingestellt sind, wie in [Best Practices](sync.md#main-pars-header-863110628) beschrieben.
1. **Überprüfen Sie die Berechtigungen** autorisierter Benutzer. Wenn die Pakete nicht ordnungsgemäß installiert sind, überprüfen Sie, ob der [autorisierte Benutzer](../../help/sites-administering/sync.md#createauthuser), der in der ersten Instanz im Veröffentlichungsmodus erstellt wurde, die richtigen ACLs aufweist.

   Um dies zu validieren, ändern Sie anstelle des erstellten [autorisierten Benutzers](../../help/sites-administering/sync.md#createauthuser) die [Granite Distribution - Encrypted Password Transport Secret Provider](../../help/sites-administering/sync.md#adobegraniteencpasswrd)-Konfiguration auf der Autoreninstanz, um Administratorbenutzer-Anmeldedaten zu verwenden. Versuchen Sie nun, die Pakete erneut zu installieren. Wenn die Benutzersynchronisierung mit Administratorberechtigungen ordnungsgemäß funktioniert, bedeutet dies, dass der erstellte Veröffentlichungsbenutzer nicht über entsprechende Zugriffssteuerungslisten verfügte.

1. **Überprüfen Sie die Konfiguration** des Werks des Beobachters. Wenn nur bestimmte Knoten nicht über die Veröffentlichungsfarm synchronisiert werden - z. B. sind Gruppenmitglieder nicht synchronisiert - stellen Sie sicher, dass die Konfiguration [Adobe Granite Distribution - Diff Observer Factory](../../help/sites-administering/sync.md#diffobserver) aktiviert ist und **rep:members** unter **Aussehbare Eigenschaftennamen** eingestellt ist.
1. **Überprüfen Sie die AEM Communities User Sync Listener-Konfiguration.** Wenn die erstellten Benutzer synchronisiert werden, Abonnement und folgende Elemente jedoch nicht funktionieren, stellen Sie sicher, dass die AEM Communities User Sync Listener-Konfiguration über Folgendes verfügt:

   * Knotentypen - festgelegt auf **rep:User, nt:unstructured**, **nt:resource**, **rep:ACL**, **sling:Folder** und **sling:OrderedFolder**
   * Ignorierbare Knoten - auf **.tokens**, **system** und **rep:cache** eingestellt
   * Verteilte Ordner - auf die Ordner festlegen, die verteilt werden sollen

1. **Überprüfen Sie die Protokolle, die bei der Benutzererstellung in der Veröffentlichungsinstanz** generiert werden. Wenn die oben genannten Konfigurationen angemessen eingestellt sind und die Benutzersynchronisierung nicht funktioniert, überprüfen Sie die Protokolle, die bei der Benutzererstellung generiert wurden.

   Überprüfen Sie, ob die Reihenfolge der Protokolle wie folgt ist:

   ```shell
   15.05.2016 18:33:01.523 *INFO* [sling-oak-observation-7422] com.adobe.cq.social.sync.impl.PublisherSyncServiceImpl Handing these paths to the distribution subsystem: [/home/users/C, /home/users/C/Cw-5avWqilmqsNn5hCvK]
   15.05.2016 18:33:01.523 *INFO* [sling-oak-observation-7422] org.apache.sling.distribution.agent.impl.SimpleDistributionAgent [agent][socialpubsync-reverse] REQUEST-START DSTRQ2: ADD paths=[/home/users/C, /home/users/C/Cw-5avWqilmqsNn5hCvK], user=communities-user-admin
   15.05.2016 18:33:01.523 *INFO* [sling-oak-observation-7431] com.adobe.cq.social.sync.impl.PublisherSyncServiceImpl Handing these paths to the distribution subsystem: [/home/users/C/Cw-5avWqilmqsNn5hCvK, /home/users/C/Cw-5avWqilmqsNn5hCvK/profile, /home/users/C/Cw-5avWqilmqsNn5hCvK/rep:policy]
   15.05.2016 18:33:01.523 *INFO* [sling-oak-observation-7431] org.apache.sling.distribution.agent.impl.SimpleDistributionAgent [agent][socialpubsync-reverse] REQUEST-START DSTRQ3: ADD paths=[/home/users/C/Cw-5avWqilmqsNn5hCvK, /home/users/C/Cw-5avWqilmqsNn5hCvK/profile, /home/users/C/Cw-5avWqilmqsNn5hCvK/rep:policy], user=communities-user-admin
   15.05.2016 18:33:01.757 *INFO* [sling-oak-observation-7431] org.apache.jackrabbit.vault.packaging.impl.JcrPackageDefinitionImpl unwrapping package sling/distribution:socialpubsync-vlt_1463337181554_ebb27ad9-a861-4405-9342-d64c916654e2:0.0.1
   15.05.2016 18:33:01.820 *INFO* [sling-oak-observation-7422] org.apache.jackrabbit.vault.packaging.impl.JcrPackageDefinitionImpl unwrapping package sling/distribution:socialpubsync-vlt_1463337181554_58811273-5861-48fe-95d2-4aff367b99c3:0.0.1
   15.05.2016 18:33:02.023 *INFO* [sling-oak-observation-7430] com.adobe.cq.social.sync.impl.PublisherSyncServiceImpl Handing these paths to the distribution subsystem: [/home/users/C/Cw-5avWqilmqsNn5hCvK/profile]
   15.05.2016 18:33:02.023 *INFO* [sling-oak-observation-7430] org.apache.sling.distribution.agent.impl.SimpleDistributionAgent [agent][socialpubsync-reverse] REQUEST-START DSTRQ4: ADD paths=[/home/users/C/Cw-5avWqilmqsNn5hCvK/profile], user=communities-user-admin
   15.05.2016 18:33:02.273 *INFO* [sling-oak-observation-7430] org.apache.jackrabbit.vault.packaging.impl.JcrPackageDefinitionImpl unwrapping package sling/distribution:socialpubsync-vlt_1463337182039_f34f4fa6-10b9-42eb-8740-4da9d4d38f99:0.0.1
   ```

   Debugging:

   1. Deaktivieren Sie die Benutzersynchronisierung:
   1. Melden Sie sich bei AEM Autoreninstanz mit Administratorrechten an.

      1. Rufen Sie die [Webkonsole](../../help/sites-deploying/configuring-osgi.md) auf. Beispiel: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
      1. Suchen Sie die Konfiguration **[!UICONTROL Apache Sling Distribution Agent - Sync Agents Factory]**.

      1. Deaktivieren Sie das Kontrollkästchen **[!UICONTROL Aktiviert]**.
      Beim Deaktivieren der Benutzersynchronisierung in der Autoreninstanz sind (Exporteur und Importeur) Endpunkte deaktiviert und die Autoreninstanz ist statisch. Die **[!UICONTROL vlt]**-Pakete werden nicht vom Autor gepingelt oder abgerufen.

      Wenn nun ein Benutzer in der Veröffentlichungsinstanz erstellt wird, wird das Paket **[!UICONTROL vlt]** unter dem Knoten */var/sling/distribution/packages/ socialpubsync - vlt /data* erstellt. Und wenn diese Pakete vom Autor an einen anderen Dienst gesendet werden. Sie können diese Daten herunterladen und extrahieren, um zu überprüfen, welche Eigenschaften an andere Dienste gesendet werden.

   1. Wechseln Sie zu einem Herausgeber und erstellen Sie einen Benutzer im Herausgeber. Daher werden Ereignis erstellt.
   1. Überprüfen Sie die [Reihenfolge der Protokolle](sync.md#troubleshoot-sling-distribution-in-aem-communities), die bei der Benutzererstellung erstellt wurden.
   1. Überprüfen Sie, ob ein **[!UICONTROL vlt]**-Paket auf `/var/sling/distribution/packages/socialpubsync-vlt/data` erstellt wurde.
   1. Aktivieren Sie jetzt die Benutzersynchronisierung in AEM Autoreninstanz.
   1. Ändern Sie beim Herausgeber die Endpunkte für Exporteur oder Importeur in **[!UICONTROL Apache Sling Distribution Agent - Sync Agents Factory]**.

      Wir können Paketdaten herunterladen und extrahieren, um zu überprüfen, welche Eigenschaften an andere Herausgeber gesendet werden und welche Daten verloren gehen.


