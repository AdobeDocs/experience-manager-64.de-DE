---
title: Komponente „Entwürfe und Sendungen“
seo-title: Drafts and submissions component
description: Mit der Komponente „Drafts and Submissions“ können Sie Formulare auflisten, die den Status „Entwurf“ aufweisen, und diejenigen, die bereits gesendet wurden. Sie können das Erscheinungsbild und den Stil der Komponente anpassen.
seo-description: Drafts and submissions component lists forms that are in the draft state and are already submitted. You can customize appearance and style of the component.
uuid: 351d6df5-0dc3-4f7a-8bdf-0f1c8dd80f34
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 219dd379-5bc9-40b0-bdc2-2fb347da29d8
exl-id: d95d3586-ea4b-4068-a8f2-a198c27a0096
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 77%

---

# Komponente „Entwürfe und Sendungen“ {#drafts-and-submissions-component}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mit der Komponente „Drafts &amp;Submissions“ können Sie alle Formulare auflisten, die den Status „Entwurf“ aufweisen, und diejenigen, die bereits gesendet wurden. Die Komponente bietet separate Bereiche (Registerkarten) für Entwürfe und für gesendete Formulare. Benutzer können nur ihre Entwürfe und gesendeten Formulare anzeigen.

## Konfigurieren der Komponente {#configuring-the-component}

Die Komponente &quot;Drafts &amp; Submissions&quot;verfügt über zwei Registerkarten: Entwürfe und Übermittlungen.

Damit ein übermitteltes adaptives Formular auf der Registerkarte für Übermittlungen angezeigt werden kann, definieren Sie als **Übermittlungsaktion** die Option **[Übermittlungsaktion für Formularportal](/help/forms/using/configuring-submit-actions.md).** Sie können stattdessen auch die Option „Forms Portal Submit“ aktivieren. Wenn ein Benutzer das Formular übermittelt, wird dieses der Registerkarte „Submissions“ hinzugefügt.

Die Entwurfsfunktion ist standardmäßig aktiviert. Wenn ein Benutzer auf **Speichern** in einem adaptiven Formular wird das Formular der Registerkarte Entwürfe hinzugefügt.

Führen Sie die folgenden Schritte aus, um eine Komponente &quot;Drafts &amp; Submissions&quot;hinzuzufügen und zu konfigurieren:

1. Ziehen Sie die **Entwürfe und Übermittlungen** -Komponente unter Document Services-Kategorie im Komponenten-Browser auf Ihrer Seite.
1. Tippen Sie auf die Komponente und dann auf ![settings_icon](assets/settings_icon.png), um das Dialogfeld „Bearbeiten“ für die Komponente zu öffnen.

   ![Komponente „Drafts &amp; Submissions“](assets/drafts-submissions-edit.png)

1. Geben Sie im Dialogfeld &quot;Bearbeiten&quot;die folgenden Details an und tippen Sie auf **Fertig** , um die Einstellungen zu speichern.

<table>
 <tbody>
  <tr>
   <th>Tab</th>
   <th>Konfiguration</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>Allgemein</td>
   <td>Gesamtergebnis</td>
   <td>Gibt die maximal mögliche Anzahl anzuzeigender Ergebnisse an. Sind mehr Ergebnisse vorhanden, als für Gesamtergebnis angegeben wurde, wird am unteren Ende der Komponente der Link <strong>Mehr</strong> angezeigt. Klicken Sie auf <strong>Mehr</strong>, um alle Formulare anzuzeigen. </td>
  </tr>
  <tr>
   <td> </td>
   <td>Stiltyp</td>
   <td>Legt den Stil der Komponente fest. Sie können entweder <strong>No Style</strong> (Kein Stil), <strong>Default Style</strong> (Standardstil) oder <strong>Custom Style </strong>(Benutzerdefinierter Stil) für die Liste der Formulare angeben. Für die Option „Custom Style“ können Sie den Pfad zu Ihrem benutzerdefinierten CSS im Feld <strong>Custom Style Path</strong> angeben<strong>.</strong></td>
  </tr>
  <tr>
   <td> </td>
   <td>Custom Style Path (Pfad für benutzerdefinierten Stil)</td>
   <td>Wenn Sie die Option <strong>Custom Style</strong> im Feld <strong>Style Type</strong> gewählt haben, geben Sie im Feld <strong>Custom Style Path</strong> den Pfad zu Ihrer benutzerdefinierten CSS-Datei an. </td>
  </tr>
  <tr>
   <td> </td>
   <td>Anzeigeoptionen</td>
   <td><p>Gibt die anzuzeigenden Registerkarten an. Sie können festlegen, ob Formularentwürfe, übermittelte Formulare oder beides angezeigt werden soll. </p> <p><strong>Hinweis</strong>:<em> Wenn Sie für <strong>Anzeigeoptionen</strong> eine andere Option als <strong>Beide</strong> wählen, wird die Feldoption <strong>Standardregisterkarte</strong> nicht verwendet.</em></p> </td>
  </tr>
  <tr>
   <td> </td>
   <td>Standardregisterkarte</td>
   <td>Gibt an, welche Registerkarte beim Laden der Forms Portal-Seite angezeigt werden soll. Sie können zwischen <strong>Registerkarte "Forms-Entwurf"</strong> und <strong>Registerkarte "Gesendete Forms"</strong>.</td>
  </tr>
  <tr>
   <td>Konfiguration der Registerkarte "Forms"</td>
   <td>Benutzerdefinierter Titel</td>
   <td>Geben Sie den Titel der Registerkarte für <strong>Formularentwürfe</strong> an. Der Standardwert ist <strong>Forms-Entwurf.</strong></td>
  </tr>
  <tr>
   <td> </td>
   <td>Layout-Vorlage</td>
   <td><p>Gibt das Layout an, das für die Liste "Entwurf Forms"verwendet werden soll.</p> <p><strong>Hinweis:</strong> Verwenden Sie nicht die Option Standard (veraltet) .<br /> </p> </td>
  </tr>
  <tr>
   <td>Konfig. für Registerkarte mit übermittelten Formularen</td>
   <td>Benutzerdefinierter Titel </td>
   <td>Geben Sie den Titel der Registerkarte für <strong>übermittelte Formulare</strong> an. Der Standardwert ist <strong>Gesendete Forms.</strong></td>
  </tr>
  <tr>
   <td> </td>
   <td>Layout-Vorlage</td>
   <td>Gibt das für die Liste der übermittelten Formulare zu verwendende Layout <strong> </strong>an.  </td>
  </tr>
 </tbody>
</table>

## Anpassung des Speicherorts {#customizing-the-storage}

Wenn Sie die Forms Portal Aktion-Übermittlungsaktion verwenden oder die Store-Daten über die Forms-Portal-Optionen im adaptiven Formular aktivieren, werden die Formulardaten im AEM-Repository gespeichert. In einer Produktionsumgebung wird empfohlen, keine Entwurfs- oder gesendete Formulardaten nicht im AEM-Repository zu speichern. Stattdessen müssen Sie die Entwurfs- und Übermittlungskomponente mit einem sicheren Speicher wie der Unternehmensdatenbank integrieren, um Entwürfe und übermittelte Formulardaten zu speichern.

Mit dem Forms-Portal können Sie Daten im lokalen AEM-Repository, im Remote-AEM oder in einer Datenbank speichern. Mit AEM Forms können Sie den implementierten Speicherort für Benutzerdaten aus Entwürfen und Übermittlungen anpassen. Sie können Standardmethoden überschreiben, um festzulegen, wie Entwurfs- und Übermittlungsdaten an einem Speicherort Ihrer Wahl gespeichert werden. Beispiel: Sie können die Daten in einem Datenspeicher speichern, der derzeit in Ihrem Unternehmen implementiert ist.

Das Forms-Portal bietet vordefinierte Services (APIs) zum Speichern von Daten im CRX-Repository lokaler und entfernter Instanzen für die Veröffentlichung von AEM Forms. Sie können die Standardimplementierungen durch benutzerdefinierte Implementierungen ersetzen, wie es im Artikel [Konfiguration von Services für die Speicherung von Entwürfem und Übermittlungen](/help/forms/using/configuring-draft-submission-storage.md) beschrieben wird, um die standardmäßige Funkion zu ersetzen. Detaillierte Informationen zu den Methoden, die für eine benutzerdefinierte Implementierung zum Speichern von Inhalten an einem gesicherten Speicherort erforderlich sind, finden Sie unter [Anpassen von Services für Entwurfs- und Übermittlungsdaten](/help/forms/using/custom-draft-submission-data-services.md) und [Benutzerdefinierter Speicher für die Komponente der Entwürfe und Übermittlungen.](/help/forms/using/adding-custom-storage-provider-forms.md)

Die AEM Forms-Dokumentation bietet ein [Beispiel für die Integration der Komponente der Entwürfe und Übermittlungen in die Datenbank](https://helpx.adobe.com/in/experience-manager/6-4/forms/using/integrate-draft-submission-database.html). Sie können die als Beispiel dargestellte Implementierung verwenden, um Ihre eigene Implementierung zu entwickeln.

## Ähnliche Artikel

* [Aktivieren von Formularportalkomponenten](/help/forms/using/enabling-forms-portal-components.md)
* [Erstellen einer Formularportalseite](/help/forms/using/creating-form-portal-page.md)
* [Auflisten von Formularen auf einer Webseite mithilfe von APIs](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Verwenden der Komponente „Entwurf und Übermittlung“](/help/forms/using/draft-submission-component.md)
* [Anpassen der Speicherung von Entwürfen und gesendeten Formularen](/help/forms/using/draft-submission-component.md)
* [Beispiel zur Integrierung der Komponente für Entwurf und Übermittlung in die Datenbank](/help/forms/using/integrate-draft-submission-database.md)
* [Anpassen von Vorlagen für Forms Portal-Komponenten](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Einführung in das Veröffentlichen von Formularen in einem Portal](/help/forms/using/introduction-publishing-forms.md)
