---
title: Verwaltung von Benutzern, Gruppen und Zugriffsrechten
seo-title: User, Group and Access Rights Administration
description: Erfahren Sie mehr über die Verwaltung von Benutzern, Gruppen und Zugriffsrechten in AEM.
feature: Security
seo-description: Learn about user, group and access rights administration in AEM.
uuid: 30e0d4dc-261d-4dc2-aff7-29179eca1cc2
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: cc0637ef-4a9e-454f-899d-655c9caebe2b
exl-id: 9c14e57b-019e-45ae-9e96-40424fa609c2
source-git-commit: 31d6111a82a3cbfef22970d05280b0d3fd1c0de7
workflow-type: tm+mt
source-wordcount: '3120'
ht-degree: 81%

---

# Verwaltung von Benutzern, Gruppen und Zugriffsrechten{#user-group-and-access-rights-administration}

Die Aktivierung des Zugriffs auf ein CRX-Repository umfasst mehrere Themen:

* [Zugriffsrechte](#how-access-rights-are-evaluated): die Konzepte, wie sie definiert und ausgewertet werden
* [Benutzerverwaltung](#user-administration): Verwaltung der einzelnen für den Zugriff verwendeten Konten
* [Gruppenverwaltung](#group-administration): vereinfacht die Benutzerverwaltung durch die Bildung von Gruppen

* [Zugriffsrechteverwaltung](#access-right-management): Definition von Richtlinien, die steuern, wie diese Benutzer und Gruppen auf Ressourcen zugreifen können

Nachfolgend sind die grundlegenden Elemente aufgeführt:

**Benutzerkonten** CRX authentifiziert den Zugriff durch Identifizieren und Überprüfen eines Benutzers (durch diese Person oder eine andere Anwendung) entsprechend den im Benutzerkonto gespeicherten Details.

In CRX stellt jedes Benutzerkonto einen Knoten im Workspace dar. Ein CRX-Benutzerkonto weist die folgenden Eigenschaften auf:

* Es repräsentiert einen Benutzer von CRX.
* In ihm sind ein Benutzername und ein Kennwort gespeichert.
* Es gilt für diesen Workspace.
* Es kann keine Unterbenutzer haben. Verwenden Sie für hierarchische Zugriffsrechte Gruppen.

* Sie können Zugriffsrechte für das Benutzerkonto festlegen.

   Zur Vereinfachung der Verwaltung raten wir jedoch, (in der Mehrzahl der Fälle) Zugriffsrechte zu Gruppenkonten zuzuweisen. Bei der Zuweisung von Zugriffsrechten zu jedem einzelnen Benutzer kann die Verwaltung schnell sehr schwierig werden (Ausnahmen sind bestimmte Systembenutzer, wenn nur ein oder zwei Instanzen vorhanden sind).

**Gruppenkonten** Gruppenkonten sind Sammlungen von Benutzern und/oder anderen Gruppen. Sie dienen zur Vereinfachung der Verwaltung, da eine Änderung der einer Gruppe zugewiesenen Zugriffsrechte automatisch auf alle Benutzer in dieser Gruppe angewendet wird. Ein Benutzer muss nicht unbedingt Mitglied einer Gruppe sein, gehört aber häufig zu mehreren.

In CRX verfügt eine Gruppe über die folgenden Eigenschaften:

* Sie repräsentiert eine Gruppe von Benutzern mit gemeinsamen Zugriffsrechten. Beispiel: Autoren oder Entwickler
* Sie gilt für diesen Workspace.
* Sie kann Mitglieder enthalten. Dabei kann es sich um einzelne Benutzer oder andere Gruppen handeln.
* Eine hierarchische Gruppierung kann mithilfe von Mitgliedsbeziehungen erzielt werden. Sie können eine Gruppe nicht direkt unter einer anderen Gruppe im Repository platzieren.

* Sie können die Zugriffsrechte für alle Gruppenmitglieder definieren.

**Zugriffsberechtigungen** CRX verwendet Zugriffsrechte, um den Zugriff auf bestimmte Bereiche des Repositorys zu steuern.

Dies erfolgt über die Zuweisung von Berechtigungen, um den Zugriff auf eine Ressource (Knoten oder Pfad) im Repository zuzulassen oder abzulehnen. Da zahlreiche Berechtigungen zugewiesen werden können, müssen sie ausgewertet werden, um festzustellen, welche Kombination für die aktuelle Anfrage relevant ist.

CRX ermöglicht es Ihnen, die Zugriffsrechte für Benutzer- und Gruppenkonten zu konfigurieren. Es werden dann dieselben grundlegenden Auswertungsprinzipien auf beide angewendet.

## Auswerten von Zugriffsrechten {#how-access-rights-are-evaluated}

>[!NOTE]
>
>In CRX wird die [Zugriffssteuerung gemäß der Definition in JSR-283](https://www.adobe.io/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html) implementiert.
>
>Die Standardinstallation eines CRX-Repositorys ist so konfiguriert, dass sie die ressourcenbasierten Zugriffssteuerungslisten verwendet. Dies ist eine mögliche Implementierung der JSR-283-Zugriffssteuerung und eine der Implementierungen in Jackrabbit.

### Objekte und Prinzipale {#subjects-and-principals}

CRX verwendet zwei Hauptkonzepte zur Bewertung der Zugriffsrechte:

* Ein **Prinzipal** ist eine Entität, die die Zugriffsrechte enthält. Prinzipale beinhalten:

   * Ein Benutzerkonto
   * Ein Gruppenkonto

      Wenn ein Benutzerkonto zu einer oder mehreren Gruppen gehört, ist es auch mit jedem dieser Gruppenprinzipale verknüpft.

* Ein **Objekt** repräsentiert die Quelle einer Anfrage.

   Es dient zur Konsolidierung der für diese Anfrage relevanten Zugriffsrechte. Diese stammen von:

   * Benutzerprinzipal

      Die Rechte, die Sie dem Benutzerkonto direkt zuweisen.

   * Alle mit diesem Benutzer verknüpften Gruppenprinzipale

      Alle Rechte, die einer der Gruppen zugewiesen sind, zu denen der Benutzer gehört.
   Das Ergebnis wird anschließend verwendet, um den Zugriff auf die angeforderte Ressource zuzulassen oder abzulehnen.

#### Kompilieren der Liste der Zugriffsrechte für ein Objekt {#compiling-the-list-of-access-rights-for-a-subject}

In CRX ist das Objekt abhängig von:

* dem Benutzerprinzipal
* allen Gruppenprinzipalen, die mit diesem Benutzer verknüpft sind

Die Liste der Zugriffsrechte, die für das Objekt relevant sind, wird erstellt aus:

* den Rechten, die Sie dem Benutzerkonto direkt zuweisen
* sowie allen Rechten, die Sie jeder der Gruppen zugewiesen haben, zu denen der Benutzer gehört

![chlimage_1-307](assets/chlimage_1-307.png)

>[!NOTE]
>
>* CRX berücksichtigt keine Benutzerhierarchie bei der Kompilierung der Liste.
>* CRX verwendet nur dann eine Gruppenhierarchie, wenn Sie eine Gruppe als Mitglied einer anderen Gruppe einfügen. Es gibt keine automatische Vererbung (Übernahme) von Gruppenberechtigungen.
>* Die Reihenfolge, in der Sie die Gruppen festlegen, hat keinen Einfluss auf die Zugriffsrechte.

>


### Auflösen von Anfragen und Zugriffsrechten {#resolving-request-and-access-rights}

Wenn CRX die Anfrage verarbeitet, vergleicht es die Zugriffsanfrage des Objekts mit der Liste der Zugriffssteuerung im Repository-Knoten:

Wenn Linda also eine Aktualisierung der `/features` Knoten in der folgenden Repository-Struktur:

![chlimage_1-308](assets/chlimage_1-308.png)

### Rangfolge {#order-of-precedence}

Zugriffsrechte in CRX werden wie folgt bewertet:

* Benutzerprinzipale haben stets Vorrang vor Gruppenprinzipalen – unabhängig von:

   * ihrer Reihenfolge in der Zugriffsteuerungsliste
   * ihrer Position in der Knotenhierarchie

* Bei einem gegebenen Prinzipal ist (maximal) 1 Ablehnungs- und 1 Zulassungseintrag in einem gegebenen Knoten vorhanden. Die Implementierung löscht immer redundante Einträge und stellt sicher, dass dieselbe Berechtigung nicht sowohl in den Zulassungs- als auch in den Ablehnungseinträgen aufgeführt wird.

>[!NOTE]
>
>Dieser Bewertungsprozess ist für die ressourcenbasierte Zugriffssteuerung einer CRX-Standardinstallation geeignet.

Nachfolgend sehen Sie zwei Beispiele, in denen der Benutzer `aUser` Mitglied der Gruppe `aGroup` ist:

```xml
   + parentNode
     + acl
       + ace: aUser - deny - write
     + childNode
       + acl
         + ace: aGroup - allow - write
       + grandChildNode
```

Im obigen Fall:

* `aUser` keine Schreibberechtigung für `grandChildNode`.

```xml
   + parentNode
     + acl
       + ace: aUser - deny - write
     + childNode
       + acl
         + ace: aGroup - allow - write
         + ace: aUser - deny - write
       + grandChildNode
```

In diesem Fall:

* `aUser` keine Schreibberechtigung für `grandChildNode`.

* Der zweite ACE-Eintrag für den Benutzer `aUser` ist redundant.

Zugriffsrechte von mehreren Gruppenprinzipalen werden basierend auf ihrer Reihenfolge innerhalb der Hierarchie und innerhalb einer einzigen Zugriffssteuerungsliste bewertet.

### Best Practices {#best-practices}

Die nachfolgende Tabelle enthält einige Empfehlungen und Best Practices:

<table> 
 <tbody> 
  <tr> 
   <td>Empfehlung...</td> 
   <td>Grund...</td> 
  </tr> 
  <tr> 
   <td><i>Benutzergruppen</i></td> 
   <td><p>Vermeiden Sie die Zuweisung von Zugriffsrechten für einzelne Benutzer. Dafür gibt es mehrere Gründe:</p> 
    <ul> 
     <li>Da Sie viel mehr Benutzer als Gruppen haben, vereinfachen Gruppen die Struktur.</li> 
     <li>Gruppen bieten einen Überblick über alle Konten.</li> 
     <li>Die Vererbung ist bei Gruppen einfacher.</li> 
     <li>Benutzer kommen und gehen. Gruppen sind auf Langfristigkeit ausgelegt.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><i>Positiv sein</i></td> 
   <td><p>Verwenden Sie immer Anweisungen vom Typ Zulassen , um die Zugriffsrechte des Gruppenprinzipals anzugeben (sofern möglich). Vermeiden Sie Anweisungen vom Typ „Ablehnen“.</p> <p>Gruppenprinzipale werden der Reihenfolge nach innerhalb der Hierarchie und innerhalb einer einzelnen Zugriffssteuerungsliste bewertet.</p> </td> 
  </tr> 
  <tr> 
   <td><i>Einfach halten</i></td> 
   <td><p>Wenn Sie bei der Konfiguration einer Neuinstallation etwas Zeit investieren und nachdenken, wird dies gut bezahlt.</p> <p>Eine klare Struktur vereinfacht die fortlaufende Wartung und Verwaltung, sodass sowohl aktuelle Kollegen als auch Nachfolger die Implementierung problemlos verstehen können.</p> </td> 
  </tr> 
  <tr> 
   <td><i>Testen</i></td> 
   <td>Verwenden Sie eine Testinstallation, um zu üben und sicherzustellen, dass Sie die Beziehungen zwischen den verschiedenen Benutzern und Gruppen verstehen.</td> 
  </tr> 
  <tr> 
   <td><i>Standardbenutzer/Gruppen</i></td> 
   <td>Aktualisieren Sie die Standardbenutzer und -gruppen immer sofort nach der Installation, um Sicherheitsprobleme zu vermeiden.</td> 
  </tr> 
 </tbody> 
</table>

## Benutzerverwaltung {#user-administration}

Für die **Benutzerverwaltung** wird ein Standard-Dialogfeld verwendet.

Sie müssen sich beim jeweiligen Workspace anmelden und können dann wie folgt auf das Dialogfeld zugreifen:

* über den Link **Benutzerverwaltung** in der Hauptkonsole von CRX
* über das Menü **Sicherheit** des CRX Explorers

![chlimage_1-309](assets/chlimage_1-309.png)

**Eigenschaften**

* **Benutzer-ID** Kurzname für das Konto, der beim Zugriff auf CRX verwendet wird

* **Prinzipalname** Vollständiger Name des Kontos

* **Kennwort** Erforderlich, wenn mit diesem Konto auf CRX zugegriffen wird

* **** ntlmhash Wird automatisch jedem neuen Konto zugewiesen und bei Änderung des Kennworts aktualisiert

* Sie können neue Eigenschaften hinzufügen, indem Sie einen Namen, einen Typ und den Wert definieren. Klicken Sie auf „Speichern“ (grünes Häkchen-Symbol) für jede neue Eigenschaft.

**Gruppenmitgliedschaft** Dadurch werden alle Gruppen angezeigt, zu denen das Konto gehört. Die Spalte Übernommen zeigt Mitgliedschaften an, die durch eine Mitgliedschaft bei einer anderen Gruppe übernommen wurden.

Durch Klicken auf eine Gruppen-ID (falls verfügbar) wird die [Gruppenverwaltung](#group-administration) für diese Gruppe geöffnet.

**Darsteller** Mit der Funktion &quot;Identität annehmen&quot;kann ein Benutzer im Namen eines anderen Benutzers arbeiten.

Dies bedeutet, dass über ein Benutzerkonto andere Konten (Benutzer oder Gruppe) festgelegt werden können, die mit ihrem Konto arbeiten können. Anders ausgedrückt: Wenn Benutzer B stellvertretend für Benutzer A agieren darf, kann Benutzer B Aktionen unter Verwendung aller Kontodetails des Benutzers A (einschließlich ID, Name und Zugriffsrechte) ausführen.

Hierdurch kann der Stellvertreter (Darsteller) Aufgaben so abschließen, als würde er das Konto verwenden, für das er stellvertretend agiert, etwa bei Abwesenheit oder zur kurzfristigen Entlastung anderer überlasteter Benutzer.

Wenn ein Konto stellvertretend für ein anderes agiert, ist dies sehr schwierig zu erkennen. In den Protokolldateien werden keine Informationen dazu gespeichert, ob bei den Ereignissen jemand stellvertretend agiert hat. Wenn also Benutzer B stellvertretend für Benutzer A agiert, sehen alle Ereignisse so aus, als ob sie von Benutzer A persönlich ausgeführt wurden.

### Erstellen von Benutzerkonten {#creating-a-user-account}

1. Öffnen Sie das Dialogfeld **Benutzerverwaltung**.
1. Klicken Sie auf **Benutzer erstellen**.
1. Sie können dann die Eigenschaften eingeben:

   * **Benutzer-ID** – wird als Kontoname verwendet
   * **Kennwort** – wird bei der Anmeldung benötigt
   * **Prinzipalname** – dient zur Eingabe des vollständigen Textnamens
   * **Zwischenpfad** – kann zum Erstellen einer hierarchischen Struktur verwendet werden

1. Klicken Sie auf die Schaltfläche „Speichern“ (grünes Häkchen-Symbol).
1. Daraufhin wird das Dialogfeld erweitert und Sie können Folgendes tun:

   1. Konfigurieren Sie **Eigenschaften**.
   1. Zeigen Sie die **Gruppenmitgliedschaft** an.
   1. Definieren Sie **Darsteller**.

>[!NOTE]
>
>Es kann manchmal zu einer Beeinträchtigung der Leistung kommen, wenn neue Benutzer in Installationen registriert werden, die eine hohe Anzahl haben an:
>
>* Benutzer
>* Gruppen mit vielen Mitgliedern

>


### Aktualisieren von Benutzerkonten {#updating-a-user-account}

1. Öffnen Sie mithilfe des Dialogfelds **Benutzerverwaltung** die Listenansicht aller Konten.

1. Navigieren Sie in der hierarchischen Struktur nach oben.
1. Klicken Sie auf das gewünschte Konto, um es zur Bearbeitung zu öffnen.
1. Nehmen Sie eine Änderung vor und klicken Sie anschließend auf „Speichern“ (grünes Häkchen-Symbol) für diesen Eintrag.
1. Klicken Sie zum Fertigstellen auf **Schließen** oder auf **Liste…**, um zur Liste aller Benutzerkonten zurückzukehren.

### Entfernen von Benutzerkonten {#removing-a-user-account}

1. Öffnen Sie mithilfe des Dialogfelds **Benutzerverwaltung** die Listenansicht aller Konten.

1. Navigieren Sie in der hierarchischen Struktur nach oben.
1. Wählen Sie das gewünschte Konto aus und klicken Sie auf **Benutzer entfernen**. Das Konto wird sofort gelöscht.

>[!NOTE]
>
>Dadurch wird der Knoten für diesen Prinzipal aus dem Repository entfernt.
>
>Zugriffsrechte-Einträge werden hingegen nicht entfernt. So wird die historische Integrität gesichert.

### Definieren von Eigenschaften {#defining-properties}

Sie können **Eigenschaften** für neue oder vorhandene Konten definieren:

1. Öffnen Sie das Dialogfeld **Benutzerverwaltung** für das entsprechende Konto.
1. Geben Sie einen Namen für die **Eigenschaft** an.
1. Wählen Sie den **Typ** aus der Dropdown-Liste aus.
1. Legen Sie einen **Wert** fest.
1. Klicken Sie auf „Speichern“ (grünes Häkchen-Symbol) für die neue Eigenschaft.

Vorhandene Eigenschaften können mit dem Papierkorb-Symbol gelöscht werden.

Mit Ausnahme des Kennworts können Eigenschaften nicht bearbeitet werden, sie müssen gelöscht und neu erstellt werden.

#### Ändern von Kennwörtern {#changing-the-password}

Das **Kennwort** ist eine spezielle Eigenschaft, die durch Klicken auf den Link **Kennwort ändern** geändert werden kann.

Sie können über das Menü **Sicherheit** im CRX Explorer auch das Kennwort für Ihr eigenes Benutzerkonto ändern.

### Definieren von Darstellern {#defining-an-impersonator}

Sie können Darsteller für neue oder vorhandene Konten definieren:

1. Öffnen Sie das Dialogfeld **Benutzerverwaltung** für das entsprechende Konto.
1. Geben Sie das Konto an, dem es gestattet sein soll, stellvertretend für dieses Konto zu agieren.

   Mit Durchsuchen... können Sie ein vorhandenes Konto auswählen.

1. Klicken Sie auf „Speichern“ (grünes Häkchen-Symbol) für die neue Eigenschaft.

## Gruppenverwaltung {#group-administration}

Für die **Gruppenverwaltung** wird ein Standard-Dialogfeld verwendet.

Sie müssen sich beim jeweiligen Workspace anmelden und können dann wie folgt auf das Dialogfeld zugreifen:

* über den Link **Gruppenverwaltung** in der Hauptkonsole von CRX
* über das Menü **Sicherheit** des CRX Explorers

![chlimage_1-47](assets/chlimage_1-47.jpeg)

**Eigenschaften**

* **Gruppen-ID** Kurzname für das Gruppenkonto.

* **Prinzipalname** Vollständiger Name des Gruppenkontos

* Sie können neue Eigenschaften hinzufügen, indem Sie einen Namen, einen Typ und den Wert definieren. Klicken Sie auf „Speichern“ (grünes Häkchen-Symbol) für jede neue Eigenschaft.
* **Mitglieder** Sie können Benutzer oder andere Gruppen als Mitglieder dieser Gruppe hinzufügen.

**Gruppenmitgliedschaft** Dadurch werden alle Gruppen angezeigt, zu denen das aktuelle Gruppenkonto gehört. Die Spalte Übernommen zeigt Mitgliedschaften an, die durch eine Mitgliedschaft bei einer anderen Gruppe übernommen wurden.

Wenn Sie auf eine Gruppen-ID klicken, wird das Dialogfeld für diese Gruppe geöffnet.

**Mitglieder** Listet alle Konten (Benutzer und/oder Gruppen) auf, die Mitglieder der aktuellen Gruppe sind.

Die Spalte **Übernommen** zeigt Mitgliedschaften an, die durch eine Mitgliedschaft bei einer anderen Gruppe übernommen wurden.

>[!NOTE]
>
>Wenn die Eigentümer-, Bearbeiter- oder Betrachterrolle einem Benutzer in einem beliebigen Asset-Ordner zugewiesen wird, wird eine neue Gruppe erstellt. Der Gruppenname entspricht dem Format `mac-default-<foldername>` für jeden Ordner, für den die Rollen definiert sind.

### Erstellen von Gruppenkonten {#creating-a-group-account}

1. Öffnen Sie das Dialogfeld **Gruppenverwaltung**.
1. Klicken Sie auf **Gruppe erstellen**.
1. Sie können dann die Eigenschaften eingeben:

   * **Prinzipalname** – dient zur Eingabe des vollständigen Textnamens
   * **Zwischenpfad** – kann zum Erstellen einer hierarchischen Struktur verwendet werden

1. Klicken Sie auf die Schaltfläche „Speichern“ (grünes Häkchen-Symbol).
1. Daraufhin wird das Dialogfeld erweitert und Sie können Folgendes tun:

   1. Konfigurieren Sie **Eigenschaften**.
   1. Zeigen Sie die **Gruppenmitgliedschaft** an.
   1. Verwalten Sie die **Mitglieder**.

### Aktualisieren von Gruppenkonten {#updating-a-group-account}

1. Öffnen Sie mithilfe des Dialogfelds **Gruppenverwaltung** die Listenansicht aller Konten.

1. Navigieren Sie in der hierarchischen Struktur nach oben.
1. Klicken Sie auf das gewünschte Konto, um es zur Bearbeitung zu öffnen.
1. Nehmen Sie eine Änderung vor und klicken Sie anschließend auf „Speichern“ (grünes Häkchen-Symbol) für diesen Eintrag.
1. Klicken Sie zum Fertigstellen auf **Schließen** oder auf **Liste…**, um zur Liste aller Gruppenkonten zurückzukehren.

### Entfernen von Gruppenkonten {#removing-a-group-account}

1. Öffnen Sie mithilfe des Dialogfelds **Gruppenverwaltung** die Listenansicht aller Konten.

1. Navigieren Sie in der hierarchischen Struktur nach oben.
1. Wählen Sie das gewünschte Konto aus und klicken Sie auf **Gruppe entfernen**. Das Konto wird sofort gelöscht.

>[!NOTE]
>
>Dadurch wird der Knoten für diesen Prinzipal aus dem Repository entfernt.
>
>Zugriffsrechte-Einträge werden hingegen nicht entfernt. So wird die historische Integrität gesichert.

### Definieren von Eigenschaften {#defining-properties-1}

Sie können Eigenschaften für neue oder vorhandene Konten definieren:

1. Öffnen Sie das Dialogfeld **Gruppenverwaltung** für das entsprechende Konto.
1. Geben Sie einen Namen für die **Eigenschaft** an.
1. Wählen Sie den **Typ** aus der Dropdown-Liste aus.
1. Legen Sie einen **Wert** fest.
1. Klicken Sie auf „Speichern“ (grünes Häkchen-Symbol) für die neue Eigenschaft.

Vorhandene Eigenschaften können mit dem Papierkorb-Symbol gelöscht werden.

### Mitglieder {#members}

Sie können der aktuellen Gruppe Mitglieder hinzufügen:

1. Öffnen Sie das Dialogfeld **Gruppenverwaltung** für das entsprechende Konto.
1. Führen Sie einen der folgenden Schritte durch:

   * Geben Sie den Namen des gewünschten Mitglieds (Benutzer- oder Gruppenkonto) ein.
   * Alternativ können Sie über die Option **Durchsuchen…** nach dem hinzuzufügenden Prinzipal (Benutzer- oder Gruppenkonto) suchen und diesen auswählen.

1. Klicken Sie auf „Speichern“ (grünes Häkchen-Symbol) für die neue Eigenschaft.

Alternativ können Sie ein vorhandenes Mitglied über das Papierkorb-Symbol löschen.

## Verwalten von Zugriffsrechten {#access-right-management}

Mit dem **Zugriffssteuerung** -Registerkarte der CRXDE Lite können Sie die Zugriffssteuerungsrichtlinien definieren und die entsprechenden Berechtigungen zuweisen.

Wählen Sie beispielsweise auf der Registerkarte „Zugangssteuerung“ im unteren rechten Bereich für die Option **Aktueller Pfad** die gewünschte Ressource im linken Bereich aus:

![crx_access_control_tab](assets/crx_accesscontrol_tab.png)

Die Richtlinien sind wie folgt kategorisiert:

* **Gültige Richtlinie für die Zugriffssteuerung** Diese Richtlinien können angewendet werden.

   Dies sind Richtlinien, die für die Erstellung einer lokalen Richtlinie zur Verfügung stehen. Nachdem Sie eine gültige Richtlinie ausgewählt und hinzugefügt haben, wird sie zu einer lokalen Richtlinie.

* **Richtlinien zur lokalen Zugriffssteuerung** Dies sind Richtlinien zur Zugriffssteuerung, die Sie angewendet haben. Sie können sie dann aktualisieren, sortieren oder entfernen.

   Eine lokale Richtlinie überschreibt jedwede Richtlinien, die vom übergeordneten Element übernommen werden.

* **Gültige Richtlinien zur Zugriffssteuerung** Dies sind Richtlinien zur Zugriffssteuerung, die jetzt auf alle Zugriffsanfragen angewendet werden. Sie zeigen die aggregierten Richtlinien an, die von den lokalen Richtlinien abgeleitet bzw. vom übergeordneten Element übernommenen werden.

### Auswählen von Richtlinien {#policy-selection}

Sie können Richtlinien für Folgendes auswählen:

* **Aktueller Pfad**: Wählen Sie wie im vorherigen Beispiel eine Ressource innerhalb des Repositorys aus. Die Richtlinien für diesen aktuellen Pfad werden angezeigt.

* **Repository**: Wählt die Zugriffssteuerung auf Repository-Ebene aus. Wenn Sie beispielsweise 
`jcr:namespaceManagement` -Berechtigung, die nur für das Repository relevant ist, nicht für einen Knoten.

* **Prinzipal** Ein Prinzipal, der im Repository registriert ist

   Sie können entweder den **Prinzipal**-Namen eingeben oder auf das Symbol rechts neben dem Feld klicken, um das Dialogfeld **Prinzipal auswählen** zu öffnen.

   Dort können Sie nach einem **Benutzer** oder einer **Gruppe** **suchen**. Wählen Sie den gewünschten Prinzipal aus der angezeigten Liste aus und klicken Sie dann auf **OK**, um den Wert in das vorherige Dialogfeld zu übernehmen.

![crx_access_control_selectprincipal](assets/crx_accesscontrol_selectprincipal.png)

>[!NOTE]
>
>Zur Vereinfachung der Verwaltung empfehlen wir, dass Sie Gruppenkonten und nicht einzelnen Benutzerkonten Zugriffsrechte zuweisen.
>
>Es ist einfacher, einige wenige Gruppen anstatt vieler Benutzerkonten zu verwalten. 

### Berechtigungen {#privileges}

Die folgenden Berechtigungen können beim Hinzufügen eines Zugangssteuerungseintrags ausgewählt werden (umfassende Details finden Sie in [Sicherheits-API](https://docs.adobe.com/docs/en/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/security/Privilege.html)).

<table> 
 <tbody> 
  <tr> 
   <th><strong>Berechtigungsname</strong></th> 
   <th><strong>Das steuert die Berechtigung für ...</strong></th> 
  </tr> 
  <tr> 
   <td><code>jcr:read</code></td> 
   <td>Rufen Sie einen Knoten ab und lesen Sie dessen Eigenschaften und deren Werte.</td> 
  </tr> 
  <tr> 
   <td><code>rep:write</code></td> 
   <td>Dies ist eine Jackrabbit-spezifische Aggregat-Berechtigung von jcr:write und jcr:nodeTypeManagement.<br /> </td> 
  </tr> 
  <tr> 
   <td><code>jcr:all</code></td> 
   <td>Dies ist eine aggregierte Berechtigung, die alle anderen vordefinierten Berechtigungen enthält.</td> 
  </tr> 
  <tr> 
   <td><strong>Erweitert</strong></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><code>crx:replicate</code></td> 
   <td>Führen Sie die Replikation eines Knotens durch.</td> 
  </tr> 
  <tr> 
   <td><code>jcr:addChildNodes</code></td> 
   <td>Erstellen Sie untergeordnete Knoten eines Knotens.</td> 
  </tr> 
  <tr> 
   <td><code>jcr:lifecycleManagement</code></td> 
   <td>Ausführen von Lebenszyklusvorgängen für einen Knoten.</td> 
  </tr> 
  <tr> 
   <td><code>jcr:lockManagement</code></td> 
   <td>Knoten sperren und entsperren; Sperren aktualisieren.</td> 
  </tr> 
  <tr> 
   <td><code>jcr:modifyAccessControl</code></td> 
   <td>Ändern Sie die Zugriffssteuerungsrichtlinien eines Knotens.</td> 
  </tr> 
  <tr> 
   <td><code>jcr:modifyProperties</code></td> 
   <td>Erstellen, ändern und entfernen Sie die Eigenschaften eines Knotens.</td> 
  </tr> 
  <tr> 
   <td><code>jcr:namespaceManagement</code></td> 
   <td>Registrieren, Aufheben der Registrierung und Ändern von Namespace-Definitionen.</td> 
  </tr> 
  <tr> 
   <td><code>jcr:nodeTypeDefinitionManagement</code></td> 
   <td>Importieren Sie Knotentypdefinitionen in das Repository.</td> 
  </tr> 
  <tr> 
   <td><code>jcr:nodeTypeManagement</code></td> 
   <td>Fügen Sie Mixin-Knotentypen hinzu, entfernen Sie sie und ändern Sie den primären Knotentyp eines Knotens. Dies schließt auch alle Aufrufe der Node.addNode- und XML-Importmethoden ein, bei denen der Mixin-Typ oder primäre Typ des neuen Knotens explizit festgelegt ist.</td> 
  </tr> 
  <tr> 
   <td><code>jcr:readAccessControl</code></td> 
   <td>Lesen Sie die Richtlinie zur Zugriffskontrolle eines Knotens.</td> 
  </tr> 
  <tr> 
   <td><code>jcr:removeChildNodes</code></td> 
   <td>Entfernen Sie untergeordnete Knoten eines Knotens.</td> 
  </tr> 
  <tr> 
   <td><code>jcr:removeNode</code></td> 
   <td>Entfernen Sie einen Knoten.</td> 
  </tr> 
  <tr> 
   <td><code>jcr:retentionManagement</code></td> 
   <td>Führen Sie Aufbewahrungsverwaltungsvorgänge für einen Knoten durch.</td> 
  </tr> 
  <tr> 
   <td><code>jcr:versionManagement</code></td> 
   <td>Ausführen von Versionierungsvorgängen für einen Knoten.</td> 
  </tr> 
  <tr> 
   <td><code>jcr:workspaceManagement</code></td> 
   <td>Das Erstellen und Löschen von Arbeitsbereichen über die JCR-API.</td> 
  </tr> 
  <tr> 
   <td><code>jcr:write</code></td> 
   <td>Dies ist eine aggregierte Berechtigung, die Folgendes enthält:<br /> - jcr:modifyProperties<br /> - jcr:addChildNodes<br /> - jcr:removeNode<br /> - jcr:removeChildNodes</td> 
  </tr> 
  <tr> 
   <td><code>rep:privilegeManagement</code></td> 
   <td>Registrieren Sie neue Berechtigungen.</td> 
  </tr> 
 </tbody> 
</table>

### Registrieren von neuen Berechtigungen {#registering-new-privileges}

Sie können auch neue Berechtigungen registrieren:

1. Wählen Sie in der Symbolleiste **Tools** und dann **Berechtigungen** aus, um die aktuell registrierten Berechtigungen anzuzeigen.

   ![ac_permissions](assets/ac_privileges.png)

1. Öffnen Sie mithilfe des Symbols **Berechtigung registrieren** (**+**) das entsprechende Dialogfeld und legen Sie eine neue Berechtigung fest:

   ![ac_privilegeregister](assets/ac_privilegeregister.png)

1. Klicken Sie zum Speichern auf **OK**. Die Berechtigung steht jetzt zur Auswahl zur Verfügung.

### Hinzufügen von Zugriffssteuerungseinträgen {#adding-an-access-control-entry}

1. Wählen Sie die Ressource aus und öffnen Sie die Registerkarte **Zugriffssteuerung**.

1. Um neue **Richtlinien zur lokalen Zugriffssteuerung** hinzuzufügen, klicken Sie auf das **+**-Symbol rechts neben der Liste **Gültige Richtlinie für die Zugriffssteuerung**:

   ![crx_access_control_apply](assets/crx_accesscontrol_applicable.png)

1. Es wird ein neuer Eintrag unter **Richtlinien zur lokalen Zugriffssteuerung** angezeigt:

   ![crx_access_control_newlocal](assets/crx_accesscontrol_newlocal.png)

1. Klicken Sie auf das **+**-Symbol, um einen neuen Eintrag hinzuzufügen:

   ![crx_access_control_addentry](assets/crx_accesscontrol_addentry.png)

   >[!NOTE]
   >
   >Derzeit ist es nur mithilfe einer Übergangslösung möglich, eine leere Zeichenfolge festzulegen.
   >
   >Geben Sie einfach &quot;&quot; ein.

1. Definieren Sie Ihre Richtlinie zur Zugriffssteuerung und klicken Sie dann zum Speichern auf **OK**. Die neue Richtlinie:

   * wird unter **Richtlinien zur lokalen Zugriffssteuerung** aufgeführt; 
   * reflektiert die Änderungen unter **Gültige Richtlinien zur Zugriffssteuerung**.

CRX überprüft Ihre Auswahl. Bei einem gegebenen Prinzipal ist (maximal) 1 Ablehnungs- und 1 Zulassungseintrag in einem gegebenen Knoten vorhanden. Die Implementierung löscht immer redundante Einträge und stellt sicher, dass dieselbe Berechtigung nicht sowohl in den Zulassungs- als auch in den Ablehnungseinträgen aufgeführt wird.

### Sortieren von Richtlinien zur lokalen Zugriffssteuerung {#ordering-local-access-control-policies}

Die Reihenfolge in der Liste zeigt die Reihenfolge an, in der die Richtlinien angewendet werden.

1. Wählen Sie in der Tabelle **Richtlinien zur lokalen Zugriffssteuerung** den gewünschten Eintrag aus und ziehen Sie ihn an die neue Position in der Tabelle.

   ![crx_access_control_reorder](assets/crx_accesscontrol_reorder.png)

1. Die Änderungen werden in den Tabellen **Richtlinien zur lokalen Zugriffssteuerung** und **Gültige Richtlinien zur Zugriffssteuerung** angezeigt.

### Entfernen von Richtlinien zur Zugriffssteuerung {#removing-an-access-control-policy}

1. Klicken Sie in der Tabelle **Richtlinien zur lokalen Zugriffssteuerung** auf das rote Symbol (-) rechts neben dem Eintrag.

1. Der Eintrag wird aus den Tabellen **Richtlinien zur lokalen Zugriffssteuerung** und **Gültige Richtlinien zur Zugriffssteuerung** entfernt.

### Testen von Richtlinien zur Zugriffssteuerung {#testing-an-access-control-policy}

1. Wählen Sie in der CRXDE Lite-Symbolleiste **Tools** und dann **Zugriffssteuerung testen...** aus.

1. Daraufhin wird ein neues Dialogfeld im Bereich rechts oben geöffnet. Wählen Sie den **Pfad** und/oder den **Prinzipal** aus, den Sie testen möchten.

1. Klicken Sie auf **Testen**, um die Ergebnisse für Ihre Auswahl zu sehen:

   ![crx_access_control_test](assets/crx_accesscontrol_test.png)
