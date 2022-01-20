---
title: Speichern eines HTML5-Formulars als Entwurf
seo-title: Saving an HTML5 form as a draft
description: Sie können ein HTML5-Formular als Entwurf speichern und das Formular zu einem späteren Zeitpunkt ausfüllen.
seo-description: Save an HTML5 form as a draft and resume filling the form at a later stage.
uuid: 70cd5f6f-f125-470c-8cee-ee14d2127713
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 445e24af-cd1a-414d-bd01-9feb6631bbef
feature: Mobile Forms
exl-id: 8e4ffda9-ea92-4abc-8746-5d1852e4599b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 64%

---

# Speichern eines HTML5-Formulars als Entwurf {#saving-an-html-form-as-a-draft}

Sie können ein HTML5-Formular als Entwurf speichern, und das Formular zu einem späteren Zeitpunkt ausfüllen. Im Forms Portal können Benutzer HTML5-Formulare speichern und wiederherstellen. Um die Funktion &quot;Als Entwurf speichern&quot;zu aktivieren, fügen Sie die folgenden Konfigurationen zum Profilknoten hinzu:

## Benutzerdefiniertes Profil zum Aktivieren der Funktion „Als Entwurf speichern“ {#custom-profile-to-allow-save-as-draft-feature}

AEM Forms bietet standardmäßig eine **Als Entwurf speichern** Profil. Sie können ein Formular mit dem Profil „Als Entwurf speichern“ wiedergeben, um für ein HTML5-Formular die Entwurffunktion zu aktivieren. Sie können HTML-Renderprofile für ein Formular in [Forms Manager](/help/forms/using/introduction-managing-forms.md) angeben.

So aktivieren Sie die Funktion &quot;Als Entwurf speichern&quot;für vorhandene [Benutzerdefiniertes Profil](/help/forms/using/custom-profile.md)Fügen Sie Ihrem benutzerdefinierten Profilknoten die folgenden Eigenschaften hinzu:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Eigenschaftsname</strong></td> 
   <td><strong>Typ</strong></td> 
   <td><strong>Wert</strong></td> 
   <td><strong>Beschreibung</strong></td> 
  </tr> 
  <tr> 
   <td>mfAllowFPDraft</td> 
   <td>Zeichenfolge</td> 
   <td>Ja</td> 
   <td><p>Aktiviert die Funktion „Als Entwurf speichern“</p> <p>für dieses Profil.</p> </td> 
  </tr> 
  <tr> 
   <td>mfAllowAttachments</td> 
   <td>Zeichenfolge</td> 
   <td>Ja</td> 
   <td><p>Ermöglicht das Hochladen von Anlagen</p> <p>mit diesem Profil.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Speicherung und Auflistung von Entwürfen {#drafts-storage-and-listing}

Nach der Aktivierung der Funktion „Als Entwurf speichern“ wird das Formular, wenn es gespeichert wurde, in der Komponente [Drafts and Submission (Entwurf und Übermittlung)](/help/forms/using/draft-submission-component.md) aufgelistet. Sie können das gespeicherte Formular aus der Komponente „Drafts and Submissions“ abrufen und mit dem Ausfüllen beginnen.

Um die Formularauflistung für die Komponente &quot;Drafts and Submissions&quot;zu aktivieren, fügen Sie dem Profilknoten die folgende Eigenschaft hinzu:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Eigenschaftsname</strong></td> 
   <td><strong>Typ</strong></td> 
   <td><strong>Wert</strong></td> 
   <td><strong>Beschreibung</strong></td> 
  </tr> 
  <tr> 
   <td>fp.enablePortalSubmit</td> 
   <td>Zeichenfolge</td> 
   <td>Ja</td> 
   <td>So aktivieren Sie die Auflistung von Entwürfen und Formularen in<br /> Forms Portal-Komponente "Drafts &amp; Submissions"nach der Übermittlung</td> 
  </tr> 
 </tbody> 
</table>

Standardmäßig speichert AEM Forms die Benutzerdaten, die mit dem Entwurf und der Übermittlung eines Formulars im Knoten /content/forms/fp in der Veröffentlichungsinstanz verknüpft sind. Sie können einen benutzerdefinierten Speicheranbieter hinzufügen. Weitere Informationen finden Sie unter [Benutzerdefinierter Speicher für Komponenten „Drafts and Submissions (Entwurf und Übermittlung)“](/help/forms/using/adding-custom-storage-provider-forms.md).
