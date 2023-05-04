---
title: AEM Forms für OSGi-Gruppen und -Berechtigungen
seo-title: AEM Forms on OSGi Groups and Privileges
description: Weisen Sie den Gruppen Benutzer zu, um AEM Forms auf OSGi zu verwalten
seo-description: Assign users to the groups to manage AEM Forms on OSGi
uuid: 9ebb3a4e-4c0e-4105-921f-58077fc45281
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-type: reference
topic-tags: Configuration
discoiquuid: 71412f5d-ff34-415f-baf8-d300756b93a9
role: Admin
exl-id: a79e863e-c316-422e-a565-b0ffdeffcc00
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 29%

---

# AEM Forms für OSGi-Gruppen und -Berechtigungen {#aem-forms-on-osgi-groups-and-privileges}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Weisen Sie den Gruppen Benutzer zu, um AEM Forms auf OSGi zu verwalten

Sie können [Gruppen erstellen](/help/sites-administering/user-group-ac-admin.md#group-administration) und Richtlinien zuweisen und [Benutzer](/help/sites-administering/user-group-ac-admin.md#user-administration) zu den Gruppen in AEM. Diese Richtlinien steuern Berechtigungen der Benutzer, die Teil der Gruppe sind.

Nach der Installation [AEM Forms Add-On-Paket](/help/forms/using/installing-configuring-aem-forms-osgi.md), sind die in diesem Artikel erwähnten Gruppen, wie z. B. Formularbenutzer und Formular-Power-Benutzer, automatisch für die Zuweisung verfügbar. In der folgenden Tabelle sind die Aufgaben aufgeführt, die ein Benutzer für AEM Forms auf OSGi basierend auf den Gruppenzuweisungen ausführen kann:

<table> 
 <tbody>
  <tr>
   <td>Gruppe</td> 
   <td>Aufgaben</td> 
  </tr>
  <tr>
   <td>forms-user <sup>[1]</sup></td> 
   <td>
    <ul> 
     <li>Erstellen, Anzeigen einer Vorschau, Veröffentlichen und Senden adaptiver Formulare</li> 
     <li>Interaktive Kommunikation und Dokumentfragmente erstellen, in der Vorschau anzeigen und veröffentlichen</li> 
     <li>Hochladen von Assets in eine AEM-Instanz</li> 
     <li>Erstellen von Designs</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>forms-power-users</td> 
   <td>
    <ul> 
     <li>Erstellen, Anzeigen einer Vorschau, Veröffentlichen und Senden adaptiver Formulare</li> 
     <li>Interaktive Kommunikation und Dokumentfragmente erstellen, in der Vorschau anzeigen und veröffentlichen</li> 
     <li>Erstellen von Skripten für adaptive Formulare mithilfe des Code-Editors</li> 
     <li>Hochladen von Assets einschließlich Skripten</li> 
     <li>Erstellen von Designs</li> 
     <li>Importieren von Paketen, die XDP enthalten</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>forms-submission-reviewers</td> 
   <td>
    <ul> 
     <li>Übermittlungen überprüfen</li> 
     <li>Übermittlungen genehmigen oder ablehnen</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>template-authors <sup>[2]</sup></td> 
   <td>
    <ul> 
     <li>Adaptive Formulare oder interaktive Kommunikationsvorlagen erstellen oder in der Vorschau anzeigen</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>fdm-authors</p> </td> 
   <td>
    <ul> 
     <li>Erstellen und Ändern des Formulardatenmodells</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>cm-user-agent</td> 
   <td>
    <ul> 
     <li>Zugriff auf Correspondence Management-Briefe oder interaktive Kommunikation über die Benutzeroberfläche für Agenten</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>workflow-editors</p> </td> 
   <td>
    <ul> 
     <li>Posteingangsanwendung erstellen</li> 
     <li>Erstellen Sie ein Workflow-Modell</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>workflow-user</td> 
   <td>
    <ul> 
     <li>Verwenden AEM Posteingangsanwendungen</li> 
     <li>Verwalten von Workflow-Instanzen</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>fd-administrators</td> 
   <td>
    <ul> 
     <li>PDF Generator konfigurieren</li> 
     <li>Überwachten Ordner konfigurieren</li> 
     <li>Verwalten von Workflow-Programmen</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

1. Benutzer mit Gruppenberechtigungen für Formularbenutzer können keine Skripte für adaptive Formulare schreiben.
1. Der Benutzer mit Gruppenberechtigungen für Vorlagenautoren kann keine Skripte für Vorlagen schreiben.
