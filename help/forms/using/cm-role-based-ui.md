---
title: AUF DER Rolle basierende Benutzeroberfläche in Correspondence Management NICHT VERÖFFENTLICHEN
seo-title: AUF DER Rolle basierende Benutzeroberfläche in Correspondence Management NICHT VERÖFFENTLICHEN
description: 'null'
seo-description: 'null'
page-status-flag: de-activated
uuid: 60808852-f63f-4c0a-badb-b0af93c995a8
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 342f111e-f15a-4f9a-8993-f90760363c02
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 28%

---


# AUF DER Rolle basierende Benutzeroberfläche in Correspondence Management NICHT VERÖFFENTLICHEN {#do-not-publish-role-based-user-interface-in-correspondence-management}

In AEM kann der Admin rollenbasierten Zugriff auf verschiedene Benutzergruppen bereitstellen und verschiedene Aktionen für verschiedene Ressourcen ausführen. Die Funktion zum Erstellen oder Bearbeiten von Datenwörterbüchern kann beispielsweise nur Benutzern einer bestimmten Benutzergruppe zur Verfügung stehen, während andere Benutzer nur die Datenwörterbücher Ansicht und verwenden können.

Auf der AEM-Oberfläche werden die Optionen angezeigt, z. B. zum Erstellen oder Bearbeiten eines Asset-Typs, basierend auf der Zugriffsebene eines Benutzers. Wenn ein Benutzer beispielsweise nicht berechtigt ist, ein Datenwörterbuch zu erstellen, wird die Option zum Erstellen eines Datenwörterbuchs nicht in der Benutzeroberfläche angezeigt.

Obwohl CRX Ihnen erlaubt, die Zugriffsrechte für Benutzer- und Gruppenkonten zu konfigurieren, geht es in diesem Artikel um Rollen- oder Benutzergruppenbasierte Zugriffsrechte.

Weitere Informationen zu Gruppen, Berechtigungen, Listen zur Zugriffskontrolle und zum Verwalten von Benutzern und Gruppen finden Sie unter [Benutzerverwaltung und Sicherheit](/help/sites-administering/security.md).

## Verwalten von Berechtigungen {#managing-permissions}

1. Stellen Sie sicher, dass der Benutzer, für den Sie die Berechtigungen verwalten möchten, der entsprechenden Benutzergruppe hinzugefügt wird.

   Beispielsweise wird der Benutzer John Doe den Gruppen `agents` und `cm-creditcard`hinzugefügt. Weitere Informationen finden Sie unter Hinzufügen von Benutzern oder Gruppen zu einer Gruppe. For more information, see [Managing Users and User Groups](/help/communities/users.md).

   ![]()

1. Erstellen Sie die Ordner, die für das Zulassen der gewünschten Berechtigungen geeignet sind.

   Wenn ein Unternehmen beispielsweise über Hypotheken-, Kreditkarten- und Versicherungsabteilungen verfügt, kann es Ordner mit Namen erstellen `HomeMortgage`und die entsprechenden Vermögenswerte behalten `CreditCard,``Insurance` und selektiv Zugriff auf Vermögenswerte gewähren, die nur für seine Abteilungen relevant sind.

1. Um auf die AEM WCM-Sicherheit zuzugreifen, führen Sie einen der folgenden Schritte aus:

   1. Klicken Sie im Begrüßungsbildschirm oder in verschiedenen anderen Bereichen in AEM auf das Sicherheitssymbol:

   1. Navigieren Sie direkt zu `https://[server]:[port]/useradmin`. Achten Sie darauf, sich als Administrator bei AEM anzumelden.

      ![]()
   In der linken Struktur sehen Sie alle aktuell im System vorhandenen Benutzer und Gruppen. Sie können die anzuzeigenden Spalten auswählen, den Inhalt der Spalten sortieren und sogar die Reihenfolge ändern, in der die Spalten angezeigt werden, indem Sie die Spaltenüberschrift an eine neue Position ziehen.

   Über die Registerkarten können Sie auf verschiedene Konfigurationen zugreifen:

1. Tippen Sie in der linken Liste der Baumstruktur mit der Dublette auf den Namen der entsprechenden Gruppe und wählen Sie dann die Registerkarte &quot;Berechtigungen&quot;aus.

   Um den Namen der Gruppe zu suchen, können Sie den Namen der Gruppe in den entsprechenden Bereich eingeben.

1. Navigieren Sie auf der Registerkarte &quot;Berechtigungen&quot;zu dem Pfad, dem Sie Berechtigungen hinzufügen möchten. Die Correspondence Management-Ordner befinden sich im `content/apps/cm/` Ordner.

   Aktivieren Sie das Kontrollkästchen in der Spalte Mitglied für die Mitglieder, die Berechtigungen für diesen Pfad erhalten sollen. Deaktivieren Sie das Kontrollkästchen für die Mitglieder, denen Berechtigungen entzogen werden sollen. In der von Ihnen geänderten Zelle wird ein rotes Dreieck angezeigt.

   ![useradmin-creditcard](assets/useradmin-creditcard.png)

   >[!NOTE]
   >
   >Die in einem Ordner angegebenen Berechtigungen ersetzen die in seinen Unterordnern angegebenen Berechtigungen.

1. Tippen Sie auf Speichern.
1. Schritttext
1. Schritttext
1. Schritttext

