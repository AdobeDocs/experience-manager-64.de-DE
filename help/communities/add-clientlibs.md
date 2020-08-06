---
title: Hinzufügen Clientlibs
seo-title: Hinzufügen Clientlibs
description: Hinzufügen eines ClientLibraryFolder
seo-description: Hinzufügen eines ClientLibraryFolder
uuid: cdc1d258-2011-4517-9206-dd2b5d1f7e0d
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: c84040b0-7850-4960-b676-ffa0a74c8cb2
translation-type: tm+mt
source-git-commit: 2d1e39120d79de029927011d48f7397b53ad91bc
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 8%

---


# Hinzufügen Clientlibs {#add-clientlibs}

## Hinzufügen eines ClientLibraryFolder (clientlibs) {#add-a-clientlibraryfolder-clientlibs}

Erstellen Sie einen ClientLibraryFolder-Namen, `clientlibs`der die JS- und CSS-Dateien enthält, die zum Rendern der Seiten Ihrer Site verwendet werden.

Der `categories`Eigenschaftswert, der dieser Client-Bibliothek gegeben wird, ist der Bezeichner, der verwendet wird, um diese clientlib direkt von einer Inhaltsseite einzubeziehen oder sie in andere clientlibs einzubetten.

1. Using **[!UICONTROL CRXDE Lite]**, expand `/etc/designs`

1. Klicken Sie mit der rechten Maustaste `an-scf-sandbox` und wählen Sie `Create Node`

   * Name: `clientlibs`
   * Typ: `cq:ClientLibraryFolder`

1. Klicken Sie auf **[!UICONTROL OK]**

![chlimage_1-220](assets/chlimage_1-220.png)

Geben Sie auf der Registerkarte **[!UICONTROL Eigenschaften]** für den neuen `clientlibs` Knoten die **`categories`** Eigenschaft ein:

* Name:**[!UICONTROL Kategorien]**
* Typ:**[!UICONTROL String]**
* Wert: **[!UICONTROL apps.an-scf-sandbox]**
* Klicken Sie auf **[!UICONTROL Hinzufügen]**
* Klicken Sie auf **[!UICONTROL Alle speichern]**

Hinweis: dem Wert &quot;Kategorien&quot;mit &quot;Apps&quot;voranstellen. ist eine Konvention, die &#39;besitzende Anwendung&#39; als im Ordner /apps, nicht als /libs identifiziert.  WICHTIG: Hinzufügen Platzhalter `js.txt` und `css.txt` Dateien. (Es handelt sich nicht offiziell um cq:ClientLibraryFolder ohne diese.)


1. Rechtsklick auf **`/etc/designs/an-scf-sandbox/clientlibs`**
1. Wählen Sie Datei **[!UICONTROL erstellen...]**
1. Enter **[!UICONTROL Name]**: `css.txt`

1. Wählen Sie Datei **[!UICONTROL erstellen...]**
1. Enter **[!UICONTROL Name]**: `js.txt`

1. Klicken Sie auf **[!UICONTROL Alle speichern]**

![chlimage_1-221](assets/chlimage_1-221.png)

Die erste Zeile der Dateien &quot;css.txt&quot;und &quot;js.txt&quot;gibt den Basisspeicherort an, von dem aus die folgenden Listen zu finden sind.

Versuchen Sie, den Inhalt von css.txt auf Folgendes festzulegen:

```
#base=.
 style.css
```

Erstellen Sie dann eine Datei unter clientlibs mit dem Namen style.css und stellen Sie den Inhalt auf Folgendes ein:

`body {`

`background-color: #b0c4de;`

`}`

## SCF Clientlibs einbetten {#embed-scf-clientlibs}

Geben Sie auf der Registerkarte &quot; **[!UICONTROL Eigenschaften]** &quot;für den `clientlibs` Knoten die Eigenschaft &quot;String mit mehreren Werten&quot; **[!UICONTROL embed]** ein. Dadurch werden die erforderlichen [clientseitigen Bibliotheken (clientlibs) für SCF-Komponenten](client-customize.md#clientlibs-for-scf)eingebettet. Für dieses Tutorial fügen wir viele clientlibs hinzu, die für die Communities-Komponenten notwendig sind.

**Beachten Sie** , dass dies der gewünschte Ansatz für eine Produktionssite sein kann oder nicht, da es Hinweise zur Bequemlichkeit im Vergleich zur Größe/Geschwindigkeit der für jede Seite heruntergeladenen clientlibs gibt.

Wenn Sie nur eine Funktion auf einer Seite verwenden, könnten Sie die vollständige clientlib dieser Funktion direkt auf der Seite einfügen, z. B. &lt;% ui:includeClientLib-Kategorien=cq.social.hbs.forum&quot; %>

In diesem Fall schließen wir sie alle ein und würden daher die einfacheren SCF clientlibs bevorzugen, die der Autor clientlibs sind:

* Name: **`embed`**
* Typ: **`String`**

* Klicken Sie auf **`Multi`**
* Wert: **`cq.social.scf`**

   *&lt;enter> öffnet ein Dialogfeld*

   *Klicken Sie nach jedem Eintrag auf **[+]**, um die folgenden clientlib-Kategorien hinzuzufügen:*

   * **`cq.ckeditor`**
   * **`cq.social.author.hbs.comments`**
   * **`cq.social.author.hbs.forum`**
   * **`cq.social.author.hbs.rating`**
   * **`cq.social.author.hbs.reviews`**
   * **`cq.social.author.hbs.voting`**
   * Klicken Sie auf **[!UICONTROL OK]**

* Klicken Sie auf **[!UICONTROL Alle speichern]**

![chlimage_1-222](assets/chlimage_1-222.png)

So `/etc/designs/an-scf-sandbox/clientlibs` sollte es nun im Repository angezeigt werden:

![chlimage_1-223](assets/chlimage_1-223.png)

## Clientlibs in PlayPage-Vorlage einschließen {#include-clientlibs-in-playpage-template}

Ohne die `apps.an-scf-sandbox` ClientLibraryFolder-Kategorie auf der Seite einzuschließen, sind die SCF-Komponenten nicht funktionsfähig und werden nicht gestylt, da die erforderlichen JavaScript(s) und Stile(s) nicht verfügbar sind.

Beispielsweise wird die Komponente &quot;SCF-Kommentare&quot;ohne Einbeziehung der clientlibs unformatiert angezeigt:

![chlimage_1-224](assets/chlimage_1-224.png)

Sobald apps.an-scf-sandbox clientlibs enthalten ist, wird die Komponente &quot;SCF-Kommentare&quot;mit einem Stil angezeigt:

![chlimage_1-225](assets/chlimage_1-225.png)

Die Include-Anweisung gehört zum <head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8"> Abschnitt <html> script. Die Standardeinstellung **`foundation head.jsp`** enthält ein Skript, das überlagert werden kann: **`headlibs.jsp`**.

**Kopieren Sie die Datei &quot;headlibs.jsp&quot;und schließen Sie clientlibs ein:**

1. Using **[!UICONTROL CRXDE Lite]**, select **`/libs/foundation/components/page/headlibs.jsp`**
1. Klicken Sie mit der rechten Maustaste und wählen Sie &quot; **[!UICONTROL Kopieren]** &quot;(oder wählen Sie in der Symbolleiste &quot;Kopieren&quot;)
1. Wählen Sie nun eine der folgenden Optionen aus **`/apps/an-scf-sandbox/components/playpage`**
1. Klicken Sie mit der rechten Maustaste und wählen Sie **[!UICONTROL Einfügen]** (oder wählen Sie in der Symbolleiste die Option Einfügen)
1. Dublette klicken Sie auf **`headlibs.jsp`** , um sie zu öffnen
1. Fügen Sie die folgende Zeile an das Dateiende an

   **`<ui:includeClientLib categories="apps.an-scf-sandbox"/>`**

1. Klicken Sie auf **[!UICONTROL Alle speichern]**


```xml
<%@ page session="false" %><%
%><%@include file="/libs/foundation/global.jsp" %><%
%><ui:includeClientLib categories="cq.foundation-main"/><%
%>
<cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>
<% currentDesign.writeCssIncludes(pageContext); %>
<ui:includeClientLib categories="apps.an-scf-sandbox"/>
```

Laden Sie Ihre Website in den Browser und sehen Sie, ob der Hintergrund kein Schatten von Blau ist.

[http://localhost:4502/content/an-scf-sandbox/en/play.html](http://localhost:4502/content/an-scf-sandbox/en/play.html)

![chlimage_1-226](assets/chlimage_1-226.png)

## Bisher sparen Sie Ihre Arbeit {#saving-your-work-so-far}

An dieser Stelle gibt es eine minimalistische Sandbox, und es könnte sich lohnen, als Paket zu speichern, sodass Sie beim Abspielen, wenn Ihr Resppositionieren beschädigt wird und Sie Beginn zu beenden wünschen, Ihren Server ausschalten, umbenennen oder löschen können, den Server einschalten, das gespeicherte Paket hochladen und installieren können und diese grundlegenden Schritte nicht wiederholen müssen.

Dieses Paket existiert im Tutorial [Create a Sample Page](create-sample-page.md) für diejenigen, die nicht warten können, einfach zu springen und Beginn spielen!...

So erstellen Sie ein Paket:


* Klicken Sie in der **[!UICONTROL CRXDE Lite]** auf das Symbol [Paket](http://localhost:4502/crx/packmgr/)
* Klicken Sie auf **[!UICONTROL Paket erstellen]**

   * Paket-Name: `an-scf-sandbox-minimal-pkg`
   * Version: `0.1`
   * Gruppe: &lt;Als Standard beibehalten>
   * Klicken Sie auf **[!UICONTROL OK]**

* Klicken Sie auf **[!UICONTROL Bearbeiten]**.

   * Registerkarte **[!UICONTROL Filter]** auswählen

      * Click **[!UICONTROL Add filter]**
      * Stammpfad: &lt;suchen nach `/apps/an-scf-sandbox`>
      * Klicken Sie auf **[!UICONTROL Fertig]**
      * Click **[!UICONTROL Add filter]**
      * Stammpfad: &lt;suchen nach `/etc/designs/an-scf-sandbox`>
      * Klicken Sie auf **[!UICONTROL Fertig]**
      * Click **[!UICONTROL Add filter]**
      * Stammpfad: &lt;suchen nach `/content/an-scf-sandbox`>
      * Klicken Sie auf **[!UICONTROL Fertig]**
   * Klicken Sie auf **[!UICONTROL Speichern]**.


* Klicken Sie auf **[!UICONTROL Erstellen]**

Jetzt können Sie &quot; **[!UICONTROL Herunterladen]** &quot;auswählen, um es auf der Festplatte zu speichern und Paket **[!UICONTROL an anderer Stelle]** hochzuladen, sowie **[!UICONTROL Mehr > Replizieren]** wählen, um die Sandbox an eine Instanz im Veröffentlichungsmodus von localhost zu verschieben, um den Bereich Ihrer Sandbox zu erweitern.
