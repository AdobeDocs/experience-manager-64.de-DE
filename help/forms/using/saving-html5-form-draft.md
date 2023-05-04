---
title: Speichern eines HTML5-Formulars als Entwurf
seo-title: Saving an HTML5 form as a draft
description: Speichern Sie ein HTML5-Formular als Entwurf und nehmen Sie das Ausfüllen des Formulars zu einem späteren Zeitpunkt wieder auf.
seo-description: Save an HTML5 form as a draft and resume filling the form at a later stage.
uuid: 70cd5f6f-f125-470c-8cee-ee14d2127713
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 445e24af-cd1a-414d-bd01-9feb6631bbef
feature: Mobile Forms
exl-id: 8e4ffda9-ea92-4abc-8746-5d1852e4599b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 50%

---

# Speichern eines HTML5-Formulars als Entwurf {#saving-an-html-form-as-a-draft}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können ein HTML5-Formular als Entwurf speichern und das Formular zu einem späteren Zeitpunkt ausfüllen. Forms Portal ermöglicht jedem Benutzer das Speichern und Wiederherstellen eines HTML5-Formulars. Fügen Sie zum Aktivieren der Funktion „Als Entwurf speichern“ die folgenden Konfigurationen zum Profilknoten hinzu:

## Benutzerdefiniertes Profil zum Aktivieren der Funktion „Als Entwurf speichern“ {#custom-profile-to-allow-save-as-draft-feature}

In AEM Forms gibt es standardmäßig das Profil **Als Entwurf speichern**. Sie können ein Formular mit dem Profil Als Entwurf speichern wiedergeben, um die Entwurfsfunktion für ein HTML5-Formular zu aktivieren. Sie können ein HTML-Renderprofil für ein Formular in [Forms Manager](/help/forms/using/introduction-managing-forms.md).

Fügen Sie zum Aktivieren der Funktion „Als Entwurf speichern“ für Ihr bestehendes [benutzerdefiniertes Profil](/help/forms/using/custom-profile.md) die folgenden Eigenschaften zu Ihrem benutzerdefinierten Profilknoten hinzu: 

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
   <td><p>Aktiviert die Funktion "Als Entwurf speichern"</p> <p>für dieses Profil.</p> </td> 
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

Nach Aktivierung der Funktion &quot;Als Entwurf speichern&quot;für ein Formular; Wenn das Formular gespeichert wird, wird es im [Komponente &quot;Drafts and Submissions&quot;](/help/forms/using/draft-submission-component.md). Sie können das gespeicherte Formular aus der Komponente &quot;Drafts and Submissions&quot;abrufen und mit dem Ausfüllen beginnen.

Fügen Sie zum Aktivieren der Formularauflistung für die Komponente „Entwürfe und Übermittlungen“ die folgende Eigenschaft zum Profilknoten hinzu:

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
   <td>Gehen Sie wie folgt vor, um Entwürfe und Formulare nach dem Übermitteln in<br /> der Komponente „Entwürfe und Übermittlungen“ des Formularportals aufzulisten</td> 
  </tr> 
 </tbody> 
</table>

Standardmäßig speichert AEM Forms die Benutzerdaten, die mit dem Entwurf und der Übermittlung eines Formulars im Knoten /content/forms/fp in der Veröffentlichungsinstanz verknüpft sind. Sie können einen benutzerdefinierten Speicheranbieter hinzufügen. Weitere Informationen finden Sie unter [Benutzerdefinierter Speicher für Komponenten „Drafts and Submissions (Entwurf und Übermittlung)“](/help/forms/using/adding-custom-storage-provider-forms.md).
