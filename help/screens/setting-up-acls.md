---
title: Einrichten von ACLs
seo-title: Einrichten von ACLs
description: Auf dieser Seite erfahren Sie, wie Sie Projekte mithilfe von ACLs separieren können, sodass jede Person bzw. jedes Team ein eigenes Projekt erhält.
seo-description: Auf dieser Seite erfahren Sie, wie Sie Projekte mithilfe von ACLs separieren können, sodass jede Person bzw. jedes Team ein eigenes Projekt erhält.
uuid: d5609bd9-3f13-4f11-ad4f-23c2ac3aa8fc
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: administering
discoiquuid: 64e4d6ae-3fd3-41ec-84e1-cc2cac7b2519
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Einrichten von ACLs {#setting-up-acls}

Im folgenden Abschnitt wird erläutert, wie Sie Projekte mithilfe von ACLs separieren können, sodass jede Person bzw. jedes Team ein eigenes Projekt erhält.

Als AEM-Administrator möchten Sie sicherstellen, dass für ein bestimmtes Projekt zuständige Teammitglieder nicht in andere Projekte eingreifen und dass den Benutzern je nach den Projektanforderungen spezifische Rollen zugewiesen werden.

## Einrichten von Berechtigungen    {#setting-up-permissions}

Die folgenden Schritte fassen die Vorgehensweise zum Einrichten von ACLs für ein Projekt zusammen:

1. Melden Sie sich bei AEM an und navigieren Sie zu **Tools** > **Sicherheit**.

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. Klicken Sie auf **Gruppen** und geben Sie eine ID ein (zum Beispiel „Acme“).

   Alternativ dazu können Sie auch den Link [http://localhost:4502/libs/granite/security/content/groupadmin.html](http://localhost:4502/libs/granite/security/content/groupadmin.html) verwenden.

   Klicken Sie anschließend auf **Speichern**.

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. Wählen Sie **Mitarbeiter** aus der Liste aus und doppelklicken Sie darauf.

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. Add the **Acme** (project you created) to** Add Members to Group**. Klicken Sie auf **Speichern**.

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >Wenn Sie möchten, dass Mitglieder aus Projekt-Teams Player registrieren (was die Erstellung eines Benutzers für jeden Player umfasst), suchen Sie nach der Gruppe „user-administrators“ und fügen Sie die ACME-Gruppe zu „user-administrators“ hinzu.

1. Fügen Sie die Benutzer, die am Projekt **Acme** arbeiten, zur Gruppe **Acme** hinzu.

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. Setup the permissions for the group **Acme** using this [link](http://localhost:4502/useradmin).

   Wählen Sie die Gruppe **Acme** aus und klicken Sie auf die **Berechtigungen**.

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### Berechtigungen {#permissions}

Die folgende Tabelle fasst den Pfad mit den Berechtigungen auf Projektebene zusammen:

| **Pfad** | **Berechtigung** | **Beschreibung** |
|---|---|---|
| `/apps/<project>` | READ | Stellt Zugriff auf Projektdateien bereit (falls anwendbar) |
| `/content/dam/<project>` | ALL | Stellt Zugriff für die Speicherung von Assets zum Projekt bereit, wie zum Beispiel von Bildern oder Videos in DAM |
| `/content/screens/<project>` | ALL | Hebt den Zugriff auf alle anderen Projekte unter /content/screens auf. |
| `/content/screens/svc` | READ | Stellt den Zugriff auf den Registrierungsservice bereit |
| `/libs/screens` | READ | Stellt den Zugriff auf DCC bereit |
| `/var/contentsync/content/screens/` | ALL | Ermöglicht die Aktualisierung von Offlineinhalten |

>[!NOTE]
>
>In einigen Fällen können Sie separate Autorenfunktionen (wie das Verwalten von Assets und das Erstellen von Kanälen) von den Administratorfunktionen (wie dem Registrieren von Playern) trennen. Erstellen Sie bei solchen Szenarien zwei Gruppen, fügen Sie die Gruppe „authors“ zu „contributors“ hinzu und fügen Sie die Gruppe „admin“ sowohl zu „contributors“ als auch zu „user-administrators“ hinzu.

### Erstellen von Gruppen    {#creating-groups}

Bei der Erstellung eines neuen Projekts sollten auch Standardbenutzergruppen erstellt werden, denen eine Reihe von Berechtigungen zugewiesen ist. Sie sollten die Berechtigungen auf die typischen Rollen erweitern, über die wir bei AEM Screens verfügen.

Sie können beispielsweise folgende projektspezifische Gruppen erstellen:

* Screens-Projektadministratoren
* Screens-Projektoperatoren (registrieren Player und verwalten Standorte und Geräte)
* Screens-Projektbenutzer (arbeiten mit Kanälen, Zeitplänen und Kanalzuweisungen)

Die folgende Tabelle fasst bei einem AEM Screens-Projekt die Gruppen mit Beschreibungen und Berechtigungen zusammen:

<table> 
 <tbody>
  <tr>
   <td><strong>Gruppenname</strong></td> 
   <td><strong>Beschreibung</strong></td> 
   <td><strong>Berechtigungen</strong></td> 
  </tr>
  <tr>
   <td>Screens-Administratoren<br /> <em>screens-admins</em></td> 
   <td>Zugriff auf AEM Screens-Funktionen auf Administratorebene</td> 
   <td>
    <ul> 
     <li>Mitglied von „contributors“</li> 
     <li>Mitglied von „user-administrators“</li> 
     <li>ALL /content/screens</li> 
     <li>ALL /content/dam</li> 
     <li>ALL /content/experience-fragments</li> 
     <li>ALL /etc/design/screens</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>Screens-Benutzer<br /> <em>screens-users</em></td> 
   <td>Erstellen und Aktualisieren von Kanälen und Zeitplänen und Zuordnung zum Speicherort in AEM Screens</td> 
   <td>
    <ul> 
     <li>Mitglied von „contributors“</li> 
     <li>&lt;Projekt&gt; /content/screens</li> 
     <li>&lt;Projekt&gt; /content/dam</li> 
     <li>&lt;Projekt&gt; /content/experience-fragments</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>Screens-Operatoren<br /> <em>screens-operators</em></td> 
   <td>Erstellen und Aktualisieren der Speicherortstruktur und Registrieren der Player in AEM Screens</td> 
   <td>
    <ul> 
     <li>Mitglied von „contributors“</li> 
     <li>jcr:all /home/users/screens</li> 
     <li>jcr:all /home/groups/screens</li> 
     <li>&lt;Projekt&gt; /content/screens</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>Screens Player<br /> <em>screens-we-retail-devices</em></td> 
   <td>Gruppiert alle Player und alle Player/Geräte sind automatisch Mitglied von „contributors“</td> 
   <td><p> Mitglied von „contributors“</p> </td> 
  </tr>
 </tbody>
</table>

