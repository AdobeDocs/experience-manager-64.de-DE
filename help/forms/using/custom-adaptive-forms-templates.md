---
title: Erstellen einer benutzerdefinierten adaptiven Formularvorlage
seo-title: Creating a custom adaptive form template
description: Dieser Artikel beschreibt die Erstellung benutzerdefinierter adaptiver Formularvorlagen.
seo-description: This article describes how to create custom adaptive form templates.
uuid: 8f8c770f-984c-48e8-978c-7cdfcd1af95b
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: c6115b64-e06f-4b5e-b7f9-876553c7627f
exl-id: 83f978ca-d451-4d27-820f-3620331285cf
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 76%

---

# Erstellen einer benutzerdefinierten adaptiven Formularvorlage {#creating-a-custom-adaptive-form-template}

## Voraussetzungen {#prerequisites}

* Grundlegendes zu AEM [Seitenvorlage](/help/sites-authoring/templates.md) und [Authoring adaptiver Formulare](https://helpx.adobe.com/aem-forms/6-1/introduction-forms-authoring.html)

* Grundlagen zu den [clientseitigen Bibliotheken](/help/sites-developing/clientlibs.md) in AEM

## Adaptive Formularvorlage {#adaptive-form-template}

Eine adaptive Formularvorlage ist eine spezielle AEM-Seitenvorlage mit bestimmten Eigenschaften und einer vorgegebenen Inhaltsstruktur, aus denen ein adaptives Formular erstellt wird. Die Vorlage hat vorkonfigurierte Layouts, Stile und eine einfache, bereits vorgegebene Inhaltsstruktur.

Nach der Erstellung eines Formulars werden Änderungen an der Inhaltsstruktur der ursprünglichen Vorlage nicht im Formular übernommen.

## Adaptive Standardformularvorlagen {#default-adaptive-form-templates}

AEM Erste Schritte bietet die folgenden adaptiven Formularvorlagen:

* Allgemein: Ermöglicht die Erstellung eines aus mehreren Registerkarten bestehenden adaptiven Formulars mit einem Layout, in dem sich links Registerkarten befinden, über die Sie Registerkarten in beliebiger Reihenfolge aufrufen können.
* Einfach mit Adobe Sign: Hiermit können Sie ein Formular mit mehreren Registerkarten und Assistenten erstellen. Es wird ein Layout, bei dem sich die Registerkarten links befinden, verwendet. Dabei können die Registerkarten in beliebiger Reihenfolge aufgerufen werden. Es werden Adobe Document Cloud eSign-Dienste zum Signieren und zur Prüfung verwendet.
* Leere Vorlage: Hiermit können Sie ein Formular ohne Kopf- und Fußzeile sowie ohne Anfangsinhalt erstellen. Sie können Komponenten wie Textfelder, Schaltflächen und Bilder hinzufügen. Mit der leeren Vorlage können Sie ein Formular erstellen, das Sie [in AEM Site-Seiten einbetten](/help/forms/using/embed-adaptive-form-aem-sites.md) können.

Außerdem ist für diese Vorlagen die Eigenschaft `sling:resourceType` auf die entsprechende Seitenkomponente gesetzt. Die Seitenkomponente rendert die CQ-Seite mit dem Container des adaptiven Formulars, der seinerseits das adaptive Formular rendert.

Folgende Tabelle zeigt die Zuordnung zwischen Vorlagen und Seitenkomponenten:

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

Sie können die Struktur und den anfänglichen Inhalt eines adaptiven Formulars mithilfe des Vorlagen-Editors angeben. Beispiel: Sie möchten, dass alle Formularersteller in einem Registrierungsformular einige Textfelder, Navigationsschaltflächen und eine Schaltfläche zum Senden verwenden. Sie können eine Vorlage erstellen, die Formularersteller verwenden können, damit ihr Formular konsistent mit anderen Registrierungsformularen ist. Mit dem AEM-Vorlagen-Editor können Sie:

* Hinzufügen von Kopf- und Fußzeilenkomponenten eines Formulars in der Strukturebene
* Den anfänglichen Inhalt für das Formular angeben.
* Legen Sie ein Design fest.
* Geben Sie Aktionen wie Senden, Zurücksetzen und Navigation fest.

Weitere Informationen finden Sie unter [Vorlagen-Editor](/help/forms/using/template-editor.md).

## Erstellen einer Vorlage für ein adaptives Formular aus CRXDE {#creating-an-adaptive-form-template-from-crxde}

Statt der mit dem Produkt bereitgestellten Vorlagen können Sie für Ihre adaptiven Formulare auch selbst erstellte Vorlagen verwenden. Diese benutzerdefinierten Vorlagen basieren auf verschiedenen Seitenkomponenten, die Container für adaptive Formulare und Seitenelemente wie Kopf- und Fußzeilen referenzieren.

Diese Komponenten können Sie aus der Basisseitenkomponente Ihrer Website erstellen. Alternativ können Sie die Seitenkomponente des adaptiven Formulars erweitern, das von vordefinierten Vorlagen verwendet wird.

Führen Sie die folgenden Schritte aus, um eine benutzerdefinierte Vorlage wie die Vorlage „simpleEnrollmentTemplate“ zu erstellen.

1. Navigieren Sie auf Ihrer Authoring-Instanz zu CRXDE Lite.

1. Erstellen Sie im Verzeichnis „/apps“ die Ordnerstruktur für Ihre Anwendung. Lautet der Anwendungsname beispielsweise „mycompany“, so erstellen Sie einen Ordner mit diesem Namen. In der Regel enthält das Anwendungsverzeichnis die Ordner „components“, „configuration“, „templates“, „src“ und „installation“. Für dieses Beispiel reicht es aus, wenn Sie die Ordner „components“, „configuration“ und „templates“ erstellen.

1. Navigieren Sie zum Ordner „/libs/fd/af/templates“.
1. Kopieren Sie die `simpleEnrollmentTemplate` Knoten.
1. Navigieren Sie zum Ordner „/apps/mycompany/templates“. Klicken Sie mit der rechten Maustaste darauf und wählen Sie **[!UICONTROL Einfügen]** aus.
1. Benennen Sie den kopierten Vorlagenknoten gegebenenfalls um. Nennen Sie ihn zum Beispiel „enrollment-template“. 

1. Navigieren Sie zu „/apps/mycompany/templates/enrollment-template.

1. Ändern Sie die `jcr:title` und `jcr:description` -Eigenschaften für `jcr:content` -Knoten, um die Vorlage von der kopierten Vorlage zu unterscheiden.

1. Die `jcr:content` Der Knoten der modifizierten Vorlage enthält die `guideContainer` und `guideformtitle` Komponenten. Der Container `guideContainer` enthält das adaptive Formular. Die Komponente `guideformtitle` zeigt den Anwendungsnamen, die Beschreibung und ähnliche Details an.

   Statt der Komponente `guideformtitle` können Sie eine benutzerdefinierte Komponente oder die Komponente `parsys` einfügen. Entfernen Sie zum Beispiel `guideformtitle` und fügen Sie eine benutzerdefinierte Komponente oder den Komponentenknoten `parsys` hinzu. Vergewissern Sie sich, dass die Eigenschaft `sling:resourceType` der Komponente auf die Komponente verweist und das Gleiche auch in der Datei `component.jsp` der Seite definiert ist.

1. Navigieren Sie zu „/apps/mycompany/templates/enrollment-template/jcr:content“. 

1. Öffnen Sie die Registerkarte **[!UICONTROL Eigenschaften]** und setzen Sie die Eigenschaft `cq:designPath` auf „/etc/designs/mycompany“. 

1. Erstellen Sie nun für den Typ `cq:Page` den Knoten „/etc/designs/mycompany“. 

## Erstellen einer adaptiven Formularseitenkomponente {#create-an-adaptive-form-page-component}

Die benutzerdefinierte Vorlage hat den gleichen Stil wie die Standardvorlage, da die Vorlage auf die Seitenkomponente „/libs/fd/af/components/page/base“ verweist. Der Komponentenverweis befindet sich in der Eigenschaft `sling:resourceType` unter dem Knoten „/apps/mycompany/templates/enrollment-template/jcr:content“. Da base eine Kernproduktkomponente ist, dürfen Sie diese Komponente nicht ändern.

1. Navigieren Sie zum Knoten /apps/mycompany/templates/enrollment-template/jcr:content und ändern Sie den Wert der Eigenschaft `sling:resourceType` nach /apps/mycompany/components/page/enrollmentpage
1. Kopieren Sie den Knoten „/libs/fd/af/components/page/base“ in den Ordner „/apps/mycompany/components/page“. 

1. Benennen Sie die kopierte Komponente in `enrollmentpage` um.

1. **(Nur wenn Sie bereits über eine Inhaltsseite verfügen)** Führen Sie die folgenden Schritte aus (a-d), falls Sie bereits über eine `contentpage`-Komponente für Ihre Website. Wenn die Komponente `contentpage` noch nicht für Ihre Website vorhanden ist, können Sie die Eigenschaft `resourceSuperType` so einstellen, dass sie auf die OOTB-Basisseite verweist.

   1. Für `enrollmentpage` node, legen Sie den Wert der Eigenschaft fest `sling:resourceSuperType` zu &quot;mycompany/components/page/contentpage&quot;. Die Komponente `contentpage` ist die Basisseitenkomponente Ihrer Site. Sie kann durch andere Seitenkomponenten erweitert werden. Entfernen Sie Skriptdateien unter `enrollmentpage`, außer `head.jsp`, `content.jsp`und `library.jsp`. Die `sling:resourceSuperType` Komponente, die `contentpage` in diesem Fall enthält alle solchen Skripte. Kopf- und Fußzeile sowie Navigationsleiste werden aus der Komponente `contentpage` übernommen.

   1. Öffnen Sie die Datei `head.jsp`.

      Die JSP-Datei enthält die Zeile `<cq.include script="library.jsp"/>`.

      Die Datei `library.jsp` enthält die Client-Bibliothek `guide.theme.simpleEnrollment`, die wiederum den Stil für das adaptive Formular enthält.

      Die Seitenkomponente `enrollmentpage` verfügt über eine exklusive `head.jsp` -Datei, die die `head.jsp` der `contentpage` -Komponente.

   1. Schließen Sie alle Skripte in die `head.jsp` -Datei für `contentpage` -Komponente `head.jsp` -Datei für `enrollmentpage` -Komponente.
   1. Dem Skript `content.jsp` können Sie weiteren Seiteninhalt oder Verweise auf andere Komponenten hinzufügen, die beim Rendern einer Seite wiedergegeben werden. Beispiel: Wenn Sie die benutzerdefinierte Komponente `applicationformheader` hinzufügen, fügen Sie der Komponente den folgenden Verweis in der JSP-Datei hinzu:

      `<cq:include path="applicationformheader" resourceType="mycompany/components/applicationformheader"/>`

      Die benutzerdefinierte Komponente müssen Sie ebenso einfügen, wenn Sie der Vorlagenknotenstruktur eine `parsys`-Komponente hinzufügen.

## Erstellen einer Client-Bibliothek für adaptive Formulare {#creating-an-adaptive-form-client-library}

Die `head.jsp` der `enrollmentpage` -Komponente für die neue Vorlage enthält eine Client-Bibliothek `guide.theme.simpleEnrollment`. Diese Client-Bibliothek wird auch von der Standardvorlage verwendet. Den Stil in der neuen Vorlage können Sie mit einer der folgenden Methoden ändern:

* Definieren Sie ein benutzerdefiniertes Design, durch das Sie das Standarddesign`guide.theme.simpleEnrollment` ersetzen. 
* Definieren Sie unter „/etc/designs/mycompany“ eine neue Client-Bibliothek. Schließen Sie die Client-Bibliothek nach dem Eintrag des Standarddesigns in der JSP-Seite ein. Schließen Sie alle überschriebenen Stile und zusätzlichen JavaScript-Dateien in diese Client-Bibliothek ein.

>[!NOTE]
>
>Mit Design wird eine Client-Bibliothek bezeichnet, die in einer zum Rendern eines adaptiven Formulars verwendeten Seitenkomponente enthalten ist. Die Client-Bibliothek bestimmt hauptsächlich das Erscheinungsbild eines adaptiven Formulars.
