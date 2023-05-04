---
title: NICHT auf Rollen basierende Benutzeroberfläche in Correspondence Management VERÖFFENTLICHEN
seo-title: DO NOT PUBLISH Role based user interface in Correspondence Management
description: NICHT auf Rollen basierende Benutzeroberfläche in Correspondence Management VERÖFFENTLICHEN
seo-description: DO NOT PUBLISH Role based user interface in Correspondence Management
page-status-flag: de-activated
uuid: 60808852-f63f-4c0a-badb-b0af93c995a8
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 342f111e-f15a-4f9a-8993-f90760363c02
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 9%

---


# NICHT auf Rollen basierende Benutzeroberfläche in Correspondence Management VERÖFFENTLICHEN {#do-not-publish-role-based-user-interface-in-correspondence-management}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

In AEM kann der Administrator rollenbasierten Zugriff für verschiedene Benutzergruppen bereitstellen und verschiedene Aktionen für verschiedene Ressourcen durchführen. Beispielsweise kann die Funktion zum Erstellen oder Bearbeiten von Datenwörterbüchern nur Benutzern in einer bestimmten Benutzergruppe zur Verfügung stehen, während andere Benutzer nur die Datenwörterbücher anzeigen und verwenden können.

In der AEM-Benutzeroberfläche werden die Optionen angezeigt, z. B. zum Erstellen oder Bearbeiten eines Asset-Typs, basierend auf der Zugriffsebene eines Benutzers. Wenn ein Benutzer beispielsweise nicht über die Berechtigungen zum Erstellen eines Datenwörterbuchs verfügt, wird die Option zum Erstellen eines Datenwörterbuchs nicht in der Benutzeroberfläche angezeigt.

Obwohl CRX Ihnen ermöglicht, die Zugriffsberechtigungen für Benutzer- und Gruppenkonten zu konfigurieren, geht es in diesem Artikel um rollenbasierte oder gruppenbasierte Zugriffsberechtigungen.

Weitere Informationen zu Gruppen, Berechtigungen, Zugriffssteuerungslisten und zum Verwalten von Benutzern und Gruppen finden Sie unter [Benutzerverwaltung und Sicherheit](/help/sites-administering/security.md).

## Verwalten von Berechtigungen {#managing-permissions}

1. Stellen Sie sicher, dass der Benutzer, für den Sie die Berechtigungen verwalten möchten, zur entsprechenden Benutzergruppe hinzugefügt wird.

   Beispielsweise wird der Benutzer John Doe den Gruppen hinzugefügt `agents` und `cm-creditcard`. Weitere Informationen finden Sie unter Hinzufügen von Benutzern oder Gruppen zu einer Gruppe. Weitere Informationen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md).

   ![]()

1. Erstellen Sie die Ordner, die für das Zulassen der gewünschten Berechtigungen geeignet sind.

   Wenn beispielsweise ein Unternehmen über Hypotheken-, Kreditkarten- und Versicherungsabteilungen verfügt, kann es Ordner mit dem Namen `HomeMortgage`, `CreditCard,`und `Insurance` die entsprechenden Assets beizubehalten und den Zugriff selektiv auf Agenten für Assets zu gewähren, die nur für ihre Abteilungen relevant sind.

1. Führen Sie einen der folgenden Schritte aus, um auf AEM WCM-Sicherheit zuzugreifen:

   1. Klicken Sie im Begrüßungsbildschirm oder in verschiedenen anderen Bereichen in AEM auf das Sicherheitssymbol:

   1. Navigieren Sie direkt zu `https://[server]:[port]/useradmin`. Achten Sie darauf, sich als Admin bei AEM anzumelden.

      ![]()
   In der linken Struktur werden alle Benutzer und Gruppen aufgelistet, die sich derzeit im System befinden. Sie können die anzuzeigenden Spalten auswählen, den Inhalt der Spalten sortieren und die Anzeigereihenfolge der Spalten ändern, indem Sie die Spaltenüberschrift an eine neue Position ziehen.

   Über die Registerkarten können Sie auf verschiedene Konfigurationen zugreifen:

1. Doppeltippen Sie in der linken Strukturliste auf den Namen der entsprechenden Gruppe und wählen Sie dann die Registerkarte Berechtigungen aus.

   Um den Namen der Gruppe zu finden, können Sie den Namen der Gruppe in das bereitgestellte Leerzeichen eingeben.

1. Navigieren Sie auf der Registerkarte Berechtigungen zu dem Pfad, dem Sie Berechtigungen hinzufügen möchten. Die Correspondence Management-Ordner befinden sich unter der `content/apps/cm/` Ordner.

   Aktivieren Sie das Kontrollkästchen in der Spalte Mitglied für die Mitglieder, die Berechtigungen für diesen Pfad erhalten sollen. Deaktivieren Sie das Kontrollkästchen für Mitglieder, für die Sie Berechtigungen entfernen möchten. In der Zelle, an der Sie Änderungen vorgenommen haben, wird ein rotes Dreieck angezeigt.

   ![useradmin-creditcard](assets/useradmin-creditcard.png)

   >[!NOTE]
   >
   >Die in einem Ordner angegebenen Berechtigungen ersetzen die in den Unterordnern angegebenen Berechtigungen.

1. Tippen Sie auf Speichern.
1. Schritttext
1. Schritttext
1. Schritttext

