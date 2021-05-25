---
title: Clientlibs hinzufügen
seo-title: Clientlibs hinzufügen
description: Hinzufügen eines ClientLibraryFolder
seo-description: Hinzufügen eines ClientLibraryFolder
uuid: cdc1d258-2011-4517-9206-dd2b5d1f7e0d
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: c84040b0-7850-4960-b676-ffa0a74c8cb2
exl-id: 9b8c3d1c-a9b1-4dde-9044-46c8f2b22c22
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 8%

---

# Clientlibs hinzufügen {#add-clientlibs}

## Hinzufügen eines ClientLibraryFolder (clientlibs) {#add-a-clientlibraryfolder-clientlibs}

Erstellen Sie einen ClientLibraryFolder mit dem Namen `clientlibs`der die JS- und CSS-Dateien enthält, die zum Rendern der Seiten Ihrer Site verwendet werden.

Der `categories`Eigenschaftswert, der dieser Client-Bibliothek zugewiesen wird, ist der Bezeichner, der verwendet wird, um diese Client-Bibliothek direkt von einer Inhaltsseite aus oder in andere Client-Bibliotheken einzubetten.

1. Erweitern Sie `/etc/designs` mithilfe von **[!UICONTROL CRXDE Lite]**.

1. Klicken Sie mit der rechten Maustaste auf `an-scf-sandbox` und wählen Sie `Create Node` aus.

   * Name: `clientlibs`
   * Typ: `cq:ClientLibraryFolder`

1. Klicken Sie auf **[!UICONTROL OK]**

![chlimage_1-220](assets/chlimage_1-220.png)

Geben Sie auf der Registerkarte **[!UICONTROL Properties]** für den neuen Knoten `clientlibs` die Eigenschaft **`categories`** ein:

* Name:**[!UICONTROL Kategorien]**
* Typ:**[!UICONTROL String]**
* Wert: **[!UICONTROL apps.an-scf-sandbox]**
* Klicken Sie auf **[!UICONTROL Hinzufügen]**
* Klicken Sie auf **[!UICONTROL Alle speichern]**

Hinweis: dem Kategoriewert &quot;apps&quot;voranstellen. ist eine Konvention, die die &#39;owning application&#39; als im Ordner /apps, nicht /libs identifiziert.  WICHTIG: Fügen Sie Platzhalter für `js.txt`- und `css.txt`-Dateien hinzu. (Es handelt sich nicht offiziell um einen cq:ClientLibraryFolder ohne diese Ordner.)


1. Rechtsklick auf **`/etc/designs/an-scf-sandbox/clientlibs`**
1. Wählen Sie **[!UICONTROL Datei erstellen...]**
1. Geben Sie **[!UICONTROL Name]** ein: `css.txt`

1. Wählen Sie **[!UICONTROL Datei erstellen...]**
1. Geben Sie **[!UICONTROL Name]** ein: `js.txt`

1. Klicken Sie auf **[!UICONTROL Alle speichern]**

![chlimage_1-221](assets/chlimage_1-221.png)

Die erste Zeile von css.txt und js.txt identifiziert den Basisspeicherort, von dem aus die folgenden Dateilisten zu finden sind.

Versuchen Sie, den Inhalt von css.txt auf Folgendes festzulegen:

```
#base=.
 style.css
```

Erstellen Sie dann eine Datei unter clientlibs namens style.css und setzen Sie den Inhalt auf:

`body {`

`background-color: #b0c4de;`

`}`

## Einbetten von SCF Clientlibs {#embed-scf-clientlibs}

Geben Sie auf der Registerkarte **[!UICONTROL Eigenschaften]** für den Knoten `clientlibs` die String-Eigenschaft mit mehreren Werten **[!UICONTROL embed]** ein. Dadurch werden die erforderlichen [Client-seitigen Bibliotheken (clientlibs) für SCF-Komponenten](client-customize.md#clientlibs-for-scf) eingebettet. Für dieses Tutorial fügen wir viele der clientlibs hinzu, die für die Communities-Komponenten erforderlich sind.

**** Beachten Sie, dass dies möglicherweise der gewünschte Ansatz für eine Produktions-Site ist oder nicht, da Überlegungen zur Benutzerfreundlichkeit im Vergleich zur Größe/Geschwindigkeit der für jede Seite heruntergeladenen Clientlibs vorliegen.

Wenn Sie nur eine Funktion auf einer Seite verwenden, können Sie die vollständige clientlib dieser Funktion direkt auf der Seite einbeziehen, z. B. &lt;% ui:includeClientLib categories=cq.social.hbs.forum&quot; %>

In diesem Fall schließen wir alle ein und bevorzugen daher die grundlegenderen SCF-Clientlibs, die die Autoren-Clientlibs sind:

* Name: **`embed`**
* Typ: **`String`**

* Klicken Sie auf **`Multi`**
* Wert: **`cq.social.scf`**

   *&lt;enter> öffnet ein Dialogfeld*

   *Klicken Sie auf **[+]**nach jedem Eintrag, um die folgenden clientlib-Kategorien hinzuzufügen:*

   * **`cq.ckeditor`**
   * **`cq.social.author.hbs.comments`**
   * **`cq.social.author.hbs.forum`**
   * **`cq.social.author.hbs.rating`**
   * **`cq.social.author.hbs.reviews`**
   * **`cq.social.author.hbs.voting`**
   * Klicken Sie auf **[!UICONTROL OK]**

* Klicken Sie auf **[!UICONTROL Alle speichern]**

![chlimage_1-222](assets/chlimage_1-222.png)

So sollte `/etc/designs/an-scf-sandbox/clientlibs` jetzt im Repository angezeigt werden:

![chlimage_1-223](assets/chlimage_1-223.png)

## Clientlibs in PlayPage-Vorlage einschließen {#include-clientlibs-in-playpage-template}

Ohne Einbeziehung der Kategorie `apps.an-scf-sandbox` ClientLibraryFolder auf der Seite sind die SCF-Komponenten nicht funktionsfähig und gestylt, da die erforderlichen JavaScript(s) und Stile(s) nicht verfügbar sind.

Ohne die clientlibs einschließen zu müssen, wird die SCF-Kommentar-Komponente beispielsweise nicht formatiert angezeigt:

![chlimage_1-224](assets/chlimage_1-224.png)

Sobald apps.an-scf-sandbox clientlibs enthalten ist, wird die SCF-Kommentar-Komponente formatiert angezeigt:

![chlimage_1-225](assets/chlimage_1-225.png)

Die Include-Anweisung gehört zum Abschnitt `<head>` des Skripts `<html>` . Der Standard **`foundation head.jsp`** enthält ein Skript, das überlagert werden kann: **`headlibs.jsp`**.

**Kopieren Sie headlibs.jsp und fügen Sie clientlibs ein:**

1. Wählen Sie **[!UICONTROL CRXDE Lite]** **`/libs/foundation/components/page/headlibs.jsp`** aus.
1. Klicken Sie mit der rechten Maustaste und wählen Sie **[!UICONTROL Kopieren]** aus (oder wählen Sie in der Symbolleiste die Option Kopieren aus).
1. Wählen Sie nun eine der folgenden Optionen aus **`/apps/an-scf-sandbox/components/playpage`**
1. Klicken Sie mit der rechten Maustaste und wählen Sie **[!UICONTROL Einfügen]** aus (oder wählen Sie in der Symbolleiste Einfügen aus).
1. Doppelklicken Sie auf **`headlibs.jsp`**, um es zu öffnen.
1. Hängen Sie die folgende Zeile an das Ende der Datei an

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

Laden Sie Ihre Website in den Browser und überprüfen Sie, ob der Hintergrund kein Blau ist.

[http://localhost:4502/content/an-scf-sandbox/en/play.html](http://localhost:4502/content/an-scf-sandbox/en/play.html)

![chlimage_1-226](assets/chlimage_1-226.png)

## Speichern Sie Ihre Arbeit bisher {#saving-your-work-so-far}

An dieser Stelle gibt es eine minimalistische Sandbox, und es kann sich lohnen, als Paket zu speichern, damit Sie während der Wiedergabe den Server deaktivieren, umbenennen oder löschen können, wenn Ihr Repository beschädigt wird und Sie ihn neu starten möchten, den Server einschalten, hochladen und installieren können, ohne diese grundlegenden Schritte wiederholen zu müssen.

Dieses Paket existiert im Tutorial [Erstellen einer Beispielseite](create-sample-page.md) für diejenigen, die nicht warten können, einfach hineinzuspringen und mit dem Spielen zu beginnen...

So erstellen Sie ein Paket:


* Klicken Sie in **[!UICONTROL CRXDE Lite]** auf das [Paketsymbol](http://localhost:4502/crx/packmgr/).
* Klicken Sie auf **[!UICONTROL Paket erstellen]**

   * Paket-Name: `an-scf-sandbox-minimal-pkg`
   * Version: `0.1`
   * Gruppe: &lt;Als Standard beibehalten>
   * Klicken Sie auf **[!UICONTROL OK]**

* Klicken Sie auf **[!UICONTROL Bearbeiten]**.

   * Registerkarte **[!UICONTROL Filter]** auswählen

      * Klicken Sie auf **[!UICONTROL Filter]** hinzufügen
      * Stammpfad: &lt;Durchsuchen Sie `/apps/an-scf-sandbox`>
      * Klicken Sie auf **[!UICONTROL Fertig]**
      * Klicken Sie auf **[!UICONTROL Filter]** hinzufügen
      * Stammpfad: &lt;Durchsuchen Sie `/etc/designs/an-scf-sandbox`>
      * Klicken Sie auf **[!UICONTROL Fertig]**
      * Klicken Sie auf **[!UICONTROL Filter]** hinzufügen
      * Stammpfad: &lt;Durchsuchen Sie `/content/an-scf-sandbox`>
      * Klicken Sie auf **[!UICONTROL Fertig]**
   * Klicken Sie auf **[!UICONTROL Speichern]**.


* Klicken Sie auf **[!UICONTROL Erstellen]**

Jetzt können Sie **[!UICONTROL Herunterladen]** auswählen, um es auf der Festplatte und **[!UICONTROL Paket]** an einer anderen Stelle hochzuladen, und **[!UICONTROL Mehr > Replizieren]** auswählen, um die Sandbox an eine localhost-Veröffentlichungsinstanz zu senden, um den Bereich Ihrer Sandbox zu erweitern.
