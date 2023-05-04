---
title: Erstellen einer benutzerdefinierten adaptiven Formularvorlage
seo-title: Creating a custom adaptive form template
description: In diesem Artikel wird beschrieben, wie Sie benutzerdefinierte adaptive Formularvorlagen erstellen.
seo-description: This article describes how to create custom adaptive form templates.
uuid: 8f8c770f-984c-48e8-978c-7cdfcd1af95b
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: c6115b64-e06f-4b5e-b7f9-876553c7627f
exl-id: 83f978ca-d451-4d27-820f-3620331285cf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1181'
ht-degree: 59%

---

# Erstellen einer benutzerdefinierten adaptiven Formularvorlage {#creating-a-custom-adaptive-form-template}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Voraussetzungen {#prerequisites}

* Grundlagen zu den [Seitenvorlagen](/help/sites-authoring/templates.md) und zum [Authoring adaptiver Formulare](https://helpx.adobe.com/de/aem-forms/6-1/introduction-forms-authoring.html?lang=de-DE)

* Grundlegendes zu AEM [Client-seitige Bibliotheken](/help/sites-developing/clientlibs.md)

## Adaptive Formularvorlage {#adaptive-form-template}

Eine Vorlage für adaptive Formulare ist AEM Seitenvorlage mit bestimmten Eigenschaften und Inhaltsstruktur spezialisiert, die zum Erstellen adaptiver Formulare verwendet werden. Die Vorlage verfügt über vorkonfigurierte Layouts, Stile und eine grundlegende anfängliche Inhaltsstruktur.

Änderungen an der Inhaltsstruktur einer Formularvorlage werden nicht in das aus der Vorlage erstellte Formular übernommen.

## Adaptive Standardformularvorlagen {#default-adaptive-form-templates}

AEM QuickStart bietet die folgenden adaptiven Formularvorlagen:

* Allgemein: Ermöglicht die Erstellung eines aus mehreren Registerkarten bestehenden adaptiven Formulars mit einem Layout, in dem sich links Registerkarten befinden, über die Sie Registerkarten in beliebiger Reihenfolge aufrufen können.
* Einfach mit Acrobat Sign: Ermöglicht die Erstellung eines Formulars mit mehreren Registerkarten und einem Assistenten. Es verwendet ein Layout mit Registerkarten auf der linken Seite, mit dem Sie Registerkarten in beliebiger Reihenfolge aufrufen können. Es werden Adobe Document Cloud eSign-Dienste zum Signieren und zur Prüfung verwendet.
* Leere Vorlage: Ermöglicht die Erstellung eines Formulars ohne Kopf- und Fußzeile sowie anfänglichen Inhalt. Sie können Komponenten wie Textfelder, Schaltflächen und Bilder hinzufügen. Mit der leeren Vorlage können Sie ein Formular erstellen, das Sie [in AEM Site-Seiten einbetten](/help/forms/using/embed-adaptive-form-aem-sites.md) können.

Außerdem ist für diese Vorlagen die Eigenschaft `sling:resourceType` auf die entsprechende Seitenkomponente gesetzt. Die Seitenkomponente rendert die CQ-Seite mit dem Container für adaptive Formulare, der wiederum adaptive Formulare rendert.

In der folgenden Tabelle wird die Verknüpfung zwischen Vorlagen und Seitenkomponenten aufgezählt:

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Vorlage</strong></p> </td> 
   <td><p><strong>Seitenkomponente </strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>/libs/fd/af/templates/surveyTemplate</p> </td> 
   <td><p>/libs/fd/af/components/page/survey</p> </td> 
  </tr> 
  <tr> 
   <td><p>/libs/fd/af/templates/simpleEnrollmentTemplate</p> </td> 
   <td><p>/libs/fd/af/components/page/base</p> </td> 
  </tr> 
  <tr> 
   <td><p>/libs/fd/af/templates/tabbedEnrollmentTemplate</p> </td> 
   <td><p>/libs/fd/af/components/page/tabbedenrollment</p> </td> 
  </tr> 
  <tr> 
   <td><p>/libs/fd/afaddon/templates/advancedEnrollmentTemplate</p> </td> 
   <td><p>/libs/fd/afaddon/components/page/advancedenrollment</p> </td> 
  </tr> 
 </tbody> 
</table>

## Erstellen einer Vorlage für ein adaptives Formular mithilfe des Vorlageneditors {#creating-an-adaptive-form-template-using-template-editor}

Sie können die Struktur und den anfänglichen Inhalt eines adaptiven Formulars unter Verwendung des Vorlagen-Editors angeben. Sie möchten beispielsweise, dass alle Formularautoren nur über wenige Textfelder, Navigationsschaltflächen und eine Senden-Schaltfläche in einem Registrierungsformular verfügen. Sie können eine Vorlage erstellen, mit der Autoren ein Formular erstellen können, das mit anderen Registrierungsformularen konsistent ist. Mit dem AEM Vorlagen-Editor können Sie:

* Kopf- und Fußzeilenkomponenten eines Formulars in der Strukturebene hinzufügen
* Den anfänglichen Inhalt für das Formular angeben.
* Legen Sie ein Design fest.
* Geben Sie Aktionen wie Senden, Zurücksetzen und Navigation fest.

Weitere Informationen finden Sie unter [Vorlagen-Editor](/help/forms/using/template-editor.md).

## Erstellen einer adaptiven Formularvorlage aus CRXDE {#creating-an-adaptive-form-template-from-crxde}

Anstatt die verfügbaren Vorlagen zu verwenden, können Sie eine Vorlage erstellen und sie zum Erstellen adaptiver Formulare verwenden. Benutzerdefinierte Vorlagen basieren auf verschiedenen Seitenkomponenten, die Container für adaptive Formulare und Seitenelemente wie Kopf- und Fußzeilen referenzieren.

Diese Komponenten können Sie aus der Basisseitenkomponente Ihrer Website erstellen. Alternativ können Sie auch die Seitenkomponente des adaptiven Formulars erweitern, das in den mitgelieferten Vorlagen verwendet wird.

Führen Sie die folgenden Schritte aus, um eine benutzerdefinierte Vorlage wie die Vorlage „simpleEnrollmentTemplate“ zu erstellen.

1. Navigieren Sie auf Ihrer Authoring-Instanz zu CRXDE Lite.

1. Erstellen Sie im Ordner /apps die Ordnerstruktur für Ihre Anwendung. Wenn der Anwendungsname beispielsweise &quot;mycompany&quot;lautet, erstellen Sie einen Ordner mit diesem Namen. Normalerweise enthält der Anwendungsordner Komponenten, Konfigurationen, Vorlagen, src und Installationsordner. Für dieses Beispiel reicht es aus, wenn Sie die Ordner „components“, „configuration“ und „templates“ erstellen.

1. Navigieren Sie zum Ordner „/libs/fd/af/templates“.
1. Kopieren Sie den Knoten `simpleEnrollmentTemplate`.
1. Navigieren Sie zum Ordner /apps/mycompany/templates . Klicken Sie mit der rechten Maustaste darauf und wählen Sie **[!UICONTROL Einfügen]**.
1. Benennen Sie bei Bedarf den kopierten Vorlagenknoten um. Nennen Sie ihn zum Beispiel „enrollment-template“. 

1. Navigieren Sie zu „/apps/mycompany/templates/enrollment-template“.

1. Ändern Sie die Eigenschaften `jcr:title` und `jcr:description` für den Knoten `jcr:content`, um die Vorlage von der kopierten Vorlage zu unterscheiden.

1. Der Knoten `jcr:content` der geänderten Vorlage enthält die Komponenten `guideContainer` und `guideformtitle`. Der Container `guideContainer` enthält das adaptive Formular. Die Komponente `guideformtitle` zeigt den Anwendungsnamen, die Beschreibung und ähnliche Details an.

   Statt der Komponente `guideformtitle` können Sie eine benutzerdefinierte Komponente oder die Komponente `parsys` einfügen. Entfernen Sie zum Beispiel `guideformtitle` und fügen Sie eine benutzerdefinierte Komponente oder den Komponentenknoten `parsys` hinzu. Vergewissern Sie sich, dass die Eigenschaft `sling:resourceType` der Komponente auf die Komponente verweist und das Gleiche auch in der Datei `component.jsp` der Seite definiert ist.

1. Navigieren Sie zu „/apps/mycompany/templates/enrollment-template/jcr:content“. 

1. Öffnen Sie die Registerkarte **[!UICONTROL Eigenschaften]** und setzen Sie die Eigenschaft `cq:designPath` auf „/etc/designs/mycompany“. 

1. Erstellen Sie nun für den Typ `cq:Page` den Knoten „/etc/designs/mycompany“. 

## Erstellen einer Seitenkomponente für adaptive Formulare {#create-an-adaptive-form-page-component}

Die benutzerdefinierte Vorlage hat denselben Stil wie die Standardvorlage, da die Vorlage auf die Seitenkomponente /libs/fd/af/components/page/base verweist. Der Komponentenverweis befindet sich in der Eigenschaft `sling:resourceType` unter dem Knoten „/apps/mycompany/templates/enrollment-template/jcr:content“. Da es sich bei der Basis um eine Kernproduktkomponente handelt, sollten Sie diese Komponente nicht ändern.

1. Navigieren Sie zum Knoten /apps/mycompany/templates/enrollment-template/jcr:content und setzen Sie die Eigenschaft `sling:resourceType` auf „/apps/mycompany/components/page/enrollmentpage“.
1. Kopieren Sie den Knoten „/libs/fd/af/components/page/base“ in den Ordner „/apps/mycompany/components/page“. 

1. Benennen Sie die kopierte Komponente in `enrollmentpage` um.

1. **(Nur bei bereits vorhandener Inhaltsseite)** Führen Sie die folgenden Schritte (a-d) aus, wenn die Komponente `contentpage` bereits für Ihre Website vorhanden ist. Wenn die Komponente `contentpage` noch nicht für Ihre Website vorhanden ist, können Sie die Eigenschaft `resourceSuperType` so einstellen, dass sie auf die OOTB-Basisseite verweist.

   1. Setzen Sie die Eigenschaft `sling:resourceSuperType` für den Knoten `enrollmentpage` auf „mycompany/components/page/contentpage“. Die Komponente `contentpage` ist die Basisseitenkomponente Ihrer Site. Sie kann durch andere Seitenkomponenten erweitert werden. Entfernen Sie Skriptdateien unter `enrollmentpage`, außer `head.jsp`, `content.jsp` und `library.jsp`. Die Komponente `sling:resourceSuperType`, in diesem Fall `contentpage`, enthält alle diese Skripte. Kopf- und Fußzeile sowie Navigationsleiste werden aus der Komponente `contentpage` übernommen.

   1. Öffnen Sie die Datei `head.jsp`.

      Die JSP-Datei enthält die Zeile `<cq.include script="library.jsp"/>`.

      Die Datei `library.jsp` enthält die Client-Bibliothek `guide.theme.simpleEnrollment`, die wiederum den Stil für das adaptive Formular enthält.

      Die Seitenkomponente `enrollmentpage` enthält eine exklusive `head.jsp`-Datei, durch die die `head.jsp`-Datei der Komponente `contentpage` überschrieben wird.

   1. Binden Sie alle Skripte in der Datei `head.jsp` für die Komponente `contentpage` in die Datei `head.jsp` für die Komponente `enrollmentpage` ein.
   1. Dem Skript `content.jsp` können Sie weiteren Seiteninhalt oder Verweise auf andere Komponenten hinzufügen, die beim Rendern einer Seite wiedergegeben werden. Beispiel: Wenn Sie die benutzerdefinierte Komponente `applicationformheader` hinzufügen, fügen Sie der Komponente den folgenden Verweis in der JSP-Datei hinzu:

      `<cq:include path="applicationformheader" resourceType="mycompany/components/applicationformheader"/>`

      Die benutzerdefinierte Komponente müssen Sie ebenso einfügen, wenn Sie der Vorlagenknotenstruktur eine `parsys`-Komponente hinzufügen.

## Erstellen einer Client-Bibliothek für adaptive Formulare {#creating-an-adaptive-form-client-library}

Die `head.jsp`-Datei der Komponente `enrollmentpage` der neuen Vorlage enthält eine Client-Bibliothek namens `guide.theme.simpleEnrollment`. Die Standardvorlage verwendet auch diese Client-Bibliothek. Ändern Sie den Stil in der neuen Vorlage mit einer der folgenden Methoden:

* Definieren Sie ein benutzerdefiniertes Design, durch das Sie das Standarddesign`guide.theme.simpleEnrollment` ersetzen. 
* Definieren Sie eine neue Client-Bibliothek unter /etc/designs/mycompany. Schließen Sie die Client-Bibliothek nach dem Eintrag des Standarddesigns auf der JSP-Seite ein. Binden Sie alle überschriebenen Stile und zusätzlichen JavaScript-Dateien in dieser Client-Bibliothek ein.

>[!NOTE]
>
>Mit Design wird eine Client-Bibliothek bezeichnet, die in einer zum Rendern eines adaptiven Formulars verwendeten Seitenkomponente enthalten ist. Die Client-Bibliothek wirkt sich in erster Linie auf das Erscheinungsbild des adaptiven Formulars aus.
