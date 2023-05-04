---
title: Entwickeln von Sandbox-Anwendungen
seo-title: Develop Sandbox Application
description: Entwickeln von Anwendungen mithilfe von Foundation-Skripten
seo-description: Develop application using foundation scripts
uuid: 572f68cd-9ecb-4b43-a7f8-4aa8feb6c64e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 910229a3-38b1-44f1-9c09-55f8fd6cbb1d
exl-id: cd036e4a-0884-4ba0-83e9-7013583bbbae
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '601'
ht-degree: 8%

---

# Entwickeln von Sandbox-Anwendungen {#develop-sandbox-application}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

In diesem Abschnitt wurde die Vorlage jetzt im [Erstanwendung](initial-app.md) und den in der [anfänglicher Inhalt](initial-content.md) kann die Anwendung mithilfe von Foundation-Skripten entwickelt werden, einschließlich der Möglichkeit, das Authoring mit Communities-Komponenten zu aktivieren. Am Ende dieses Abschnitts wird die Website funktionieren.

## Verwenden von Foundation-Seitenskripten {#using-foundation-page-scripts}

Das Standardskript, das erstellt wird, wenn die Komponente, die die PayPage-Vorlage rendert, hinzugefügt wurde, wird geändert, um die head.jsp der Foundation-Seite und eine lokale body.jsp einzuschließen.

### Superressourcentyp {#super-resource-type}

Der erste Schritt besteht darin, der Eigenschaft `/apps/an-scf-sandbox/components/playpage` -Knoten, damit er die Skripte und Eigenschaften des Supertyps übernimmt.

Verwenden von CRXDE Lite:

<!--Resolve steps below-->

* Name: `sling:resourceSuperType`
* Typ: `String`
* Wert: `foundation/components/page`

1. Klicken Sie auf Grün **[!UICONTROL [+] Hinzufügen]**
1. Klicken Sie auf **[!UICONTROL Alle speichern]**

![chlimage_1-231](assets/chlimage_1-231.png)

### Kopf- und Textskripte {#head-and-body-scripts}

1. In **CRXDE Lite** Explorer-Bereich, navigieren Sie zu `/apps/an-scf-sandbox/components/playpage` und doppelklicken Sie auf die Datei `playpage.jsp` , um es im Bearbeitungsfenster zu öffnen.

#### /apps/an-scf-sandbox/components/playpage/playpage.jsp {#apps-an-scf-sandbox-components-playpage-playpage-jsp}

```xml
<%--

  An SCF Sandbox Play Component component.

  This is the component which renders content for An SCF Sandbox page.

--%><%
%><%@include file="/libs/foundation/global.jsp"%><%
%><%@page session="false" %><%
%><%
 // TODO add your code here
%>
```

1. Da Sie Skript-Tags zum Öffnen/Schließen kennen, ersetzen Sie &quot; // TODO ...&quot;. mit Skripten für die Kopf- und Körperteile von &lt;html>.

   Mit einem Supertyp von `foundation/components/page`, wird jedes Skript, das nicht in diesem Ordner definiert ist, in ein Skript in `/apps/foundation/components/page` Ordner (sofern vorhanden), andernfalls ein Skript in `/libs/foundation/components/page` Ordner.

#### /apps/an-scf-sandbox/components/playpage/playpage.jsp {#apps-an-scf-sandbox-components-playpage-playpage-jsp-1}

```xml
<%--

    An SCF Sandbox Play Component component: playpage.jsp

  This is the component which renders content for An SCF Sandbox page.

--%><%
%><%@include file="/libs/foundation/global.jsp"%><%
%><%@page session="false" %>
<html>
  <cq:include script="head.jsp"/>
  <cq:include script="body.jsp"/>
</html>
```

1. Das Foundation-Skript `head.jsp` müssen nicht überlagert werden, aber das Foundation-Skript `body.jsp` leer ist.

   So richten Sie für das Authoring eine Überlagerung ein `body.jsp` mit einem lokalen Skript und ein Absatzsystem (parsys) im Text einschließen:

   1. navigieren zu `/apps/an-scf-sandbox/components`
   1. wählen Sie die `playpage`Knoten
   1. Rechtsklick und Auswahl `Create > Create File...`

      * Name: **body.jsp**
   1. Klicken Sie auf **[!UICONTROL Alle speichern]**

   Öffnen `/apps/an-scf-sandbox/components/playpage/body.jsp` und fügen Sie Folgendes ein:

   ```xml
   <%--
   
       An SCF Sandbox Play Component component: body.jsp
   
     This is the component which renders content for An SCF Sandbox page.
   
   --%><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   %><%@page session="false" %>
   <body>
       <h2>Community Play</h2>
       <cq:include path="par" resourceType="foundation/components/parsys" />
   </body>
   ```

1. Klicken Sie auf **[!UICONTROL Alle speichern]**

**Zeigen Sie die Seite in einem Browser im Bearbeitungsmodus an:**

* Standard-Benutzeroberfläche: `http://localhost:4502/editor.html/content/an-scf-sandbox/en/play.html`

Sie sollten nicht nur die Überschrift sehen **Community Play**, aber auch die Benutzeroberfläche zum Bearbeiten des Seiteninhalts.

Das seitliche Bedienfeld &quot;Assets/Komponente&quot;wird angezeigt, wenn das seitliche Bedienfeld geöffnet ist und das Fenster breit genug ist, um sowohl den Seiteninhalt als auch den Seiteninhalt anzuzeigen.

![chlimage_1-232](assets/chlimage_1-232.png)

* Klassische Benutzeroberfläche: `http://localhost:4502/cf#/content/an-scf-sandbox/en/play.html`

Im Folgenden wird gezeigt, wie die Wiedergabeseite in der klassischen Benutzeroberfläche einschließlich des Content Finders (cf) angezeigt wird:

![chlimage_1-233](assets/chlimage_1-233.png)

## Communities-Komponenten {#communities-components}

Um Communities-Komponenten für das Authoring zu aktivieren, befolgen Sie die folgenden Anweisungen:

* [Zugreifen auf Communities-Komponenten](basics.md#accessing-communities-components)

Beginnen Sie für diese Sandbox mit diesen **Communities** Komponenten (aktivieren, indem Sie das Kontrollkästchen aktivieren):

* Kommentare
* Forum
* Bewertung
* Bewertungen
* Bewertungszusammenfassung (Anzeige)
* Abstimmung

Wählen Sie außerdem **[!UICONTROL Allgemein]** Komponenten wie

* Bild
* Tabelle
* Text
* Titel (Fundament)

>[!NOTE]
>
>Die für die Seitenpar aktivierten Komponenten werden im Repository als Wert der Variablen `components` -Eigenschaft der\
>`/etc/designs/an-scf-sandbox/jcr:content/playpage/par` Knoten.

## Landingpage {#landing-page}

In einer mehrsprachigen Umgebung würde die Stammseite ein Skript enthalten, das die Anfrage vom Client analysiert, um die bevorzugte Sprache zu bestimmen.

In diesem einfachen Beispiel wird die Stammseite statisch so eingestellt, dass sie zur englischen Seite weitergeleitet wird, die in Zukunft als Haupt-Landingpage mit einem Link zur Wiedergabeseite entwickelt werden kann.

Ändern Sie die Browser-URL in die Stammseite: `http://localhost:4502/editor.html/content/an-scf-sandbox.html`

* Symbol Seiteninformationen auswählen
* Auswählen **[!UICONTROL Eigenschaften öffnen]**
* Auf der Registerkarte ERWEITERT

   * Navigieren Sie zum Eintrag Umleiten zu **[!UICONTROL Websites > SCF-Sandbox-Site > SCF-Sandbox]**
   * Klicken Sie auf **[!UICONTROL OK]**

* Klicken Sie auf **[!UICONTROL OK]**

Sobald die Site veröffentlicht wurde, wird das Browsen zur Stammseite in einer Veröffentlichungsinstanz zur englischen Seite weitergeleitet.

Der letzte Schritt vor dem Abspielen mit den SCF-Communities-Komponenten besteht darin, einen Client-Bibliotheksordner (clientlibs) hinzuzufügen .... **[imetrisch](add-clientlibs.md)**
