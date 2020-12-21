---
title: Erstellen eines neuen Anmeldungsbildschirms
seo-title: Erstellen eines neuen Anmeldungsbildschirms
description: Gehen Sie wie folgt vor, um die Anmeldeseite von LiveCycle-Modulen zu ändern, beispielsweise AEM Forms oder Forms Manager.
seo-description: Gehen Sie wie folgt vor, um die Anmeldeseite von LiveCycle-Modulen zu ändern, beispielsweise AEM Forms oder Forms Manager.
uuid: c7643f87-4a08-4c63-b87c-f987dbe18ece
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: cfaa6b49-3fd0-4c08-84a2-e86c7e7e3532
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 62%

---


# Erstellen eines neuen Anmeldungsbildschirms {#creating-a-new-login-screen}

Sie können den Anmeldungsbildschirm aller Module von AEM Forms ändern, die den AEM Forms-Anmeldungsbildschirm verwenden. Die Änderungen wirken sich beispielsweise auf den Anmeldungsbildschirm, den Formularmanager und AEM Forms aus.

## Voraussetzung {#prerequisite}

1. Melden Sie sich mit Administratorberechtigungen bei `/lc/crx/de` an.
1. Führen Sie die folgenden Aktionen durch:

   1. Replizieren Sie die hierarchische Struktur: von `/libs/livecycle/core/content` bei `/apps/livecycle/core/content`. Behalten Sie die Eigenschaften (Knoten/Ordner) und Zugriffssteuerung bei.
   1. Kopieren Sie den Inhaltsordner: von `/libs/livecycle/core` bis `/apps/livecycle/core`.
   1. Löschen Sie den Inhalt des Ordners `/apps/livecycle/core`.

1. Führen Sie die folgenden Aktionen durch:

   1. Replizieren Sie die hierarchische Struktur: von `/libs/livecycle/core/components/login` bei `/apps/livecycle/core/components/login`. Behalten Sie die Eigenschaften (Knoten/Ordner) und Zugriffssteuerung bei.
   1. Kopieren Sie den Komponentenordner: von `/libs/livecycle/core` bis `/apps/livecycle/core`.
   1. Löschen Sie den Inhalt des Ordners: `/apps/livecycle/core/components/login`.

## Hinzufügen eines neuen Gebietsschemas {#adding-a-new-locale}

1. Kopieren Sie den Ordner `i18n`:

   * von `/libs/livecycle/core/components/login`
   * in `/apps/livecycle/core/components/login`

1. Löschen Sie alle Ordner innerhalb von `i18n`, mit Ausnahme von `en`.
1. Mit dem Ordner `en` führen Sie diese Schritte durch:

   1. Benennen Sie den Ordner nach dem Gebietsschema, das unterstützt werden soll. Beispiel: `ar`.
   1. Ändern Sie die Eigenschaft `jcr:language` in `ar`(für den Ordner `ar`).

   >[!NOTE]
   >
   >Wenn das Gebietsschema eine Sprach- und Ländercodekombination ist, beispielsweise `ar-DZ`, ändern Sie den Ordnernamen und den Eigenschaftswert zu `ar-DZ`.

1. Kopieren `login.jsp`:

   * von `/libs/livecycle/core/components/login`
   * in `/apps/livecycle/core/components/login`

1. Ändern Sie das folgende Codefragment für `/apps/livecycle/core/components/login/login.jsp`:

   ***Gebietsschema ist Sprachcode***

   ```
   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
   
   To
   
   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().startsWith("ar")) {
               browserLocale = "ar";
               break;
           }
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
   ```

   ***Gebietsschema ist Sprach- und Ländercode***

   ```
   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
   
   To
   
   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().equalsIgnoreCase("ar-DZ")) {
               browserLocale = "ar-DZ";
               break;
           }
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
   ```

   ***Standardgebietsschema ändern***

   ```
   String browserLocale = "en";
   for(int i=0; i<locales.length; i++)
   
   To
   
   String browserLocale = "ar";
   for(int i=0; i<locales.length; i++)
   ```

## Hinzufügen von neuem Text oder Ändern des vorhandenen Texts  {#adding-new-text-or-modifying-existing-text}

1. Kopieren Sie den Ordner `i18n`:

   * von `/libs/livecycle/core/components/login`
   * in `/apps/livecycle/core/components/login`

1. Ändern Sie nun den Wert der Eigenschaft `sling:message` des Knotens (unter dem Codeordner des gewünschten Gebietsschemas) für den Sie den Text ändern möchten. Die Übersetzung wird mit dem Schlüssel durchgeführt, der im Wert der Eigenschaft `sling:key` des Knotens aufgeführt ist.
1. Zum Hinzufügen des neuen Schlüssel-Wert-Paars führen Sie die folgenden Schritte aus. Überprüfen Sie ein Beispiel auf dem darauffolgenden Screenshot.

   1. Erstellen Sie unter den Gebietsschemaordnern einen Knoten vom Typ `sling:MessageEntry` oder kopieren Sie einen vorhandenen Knoten und benennen Sie ihn um.
   1. Kopieren `login.jsp` :

      * von `/libs/livecycle/core/components/login`
      * in `/apps/livecycle/core/components/login`
   1. Ändern Sie `/apps/livecycle/core/components/login/login.jsp`, um den neu hinzugefügten Text einzufügen.

   ![erfassen](assets/capture.png)

   ```
   div class="loginContent">
                       <span class="loginFlow"></span>
                       <span class="loginVersion"><%= i18n.get("Version: 11.0.0") %></span>
                       <span class="loginTitle"><%= i18n.get("Login") %></span>
                       <% if (loginFailed) {%>
   
   To
   
   div class="loginContent">
                       <span class="loginFlow"></span>
                       <span class="loginVersion"><%= i18n.get("My Welcome Message") %></span>
                       <span class="loginVersion"><%= i18n.get("Version: 11.0.0") %></span>
                       <span class="loginTitle"><%= i18n.get("Login") %></span>
                       <% if (loginFailed) {%>
   ```

## Hinzufügen eines neuen Stils oder Ändern des vorhandenen Stils {#adding-new-style-or-modifying-existing-style}

1. Kopieren Sie den Knoten `login`:

   * von `/libs/livecycle/core/content`
   * in `/apps/livecycle/core/content`

1. Löschen Sie die Dateien `login.js` und `jquery-1.8.0.min.js` aus dem Knoten `/apps/livecycle/core/content/login.`
1. Ändern Sie die Stile in der CSS-Datei.
1. Neue Stile hinzufügen:

   1. Neue Stile Hinzufügen `/apps/livecycle/core/content/login/login.css`
   1. Kopieren `login.jsp`

      * von `/libs/livecycle/core/components/login`
      * in `/apps/livecycle/core/components/login`
   1. Ändern Sie `/apps/livecycle/core/components/login/login.jsp`, um die neu hinzugefügten Stile einzubinden.


1. Beispiel:

   * hinzufügen Sie Folgendes zu `/apps/livecycle/core/content/login/login.css`.

   ```css
   .newLoginContentArea {
    width: 700px;
    padding: 100px 0px 0px 100px;
   }
   ```

   * Ändern Sie Folgendes in /apps/livecycle/core/components/login.jsp.

   ```
   <div class="loginContentArea">
   
   To
   
   <div class="newLoginContentArea">
   ```

>[!NOTE]
>
>Wenn die vorhandenen Bilder in `/apps/livecycle/core/content/login` (kopiert von `/libs/livecycle/core/content/login`) entfernt werden, entfernen Sie die entsprechenden Verweise in CSS.

## Fügen Sie neue Bilder hinzu {#add-new-images}

1. Führen Sie die Schritte zum Hinzufügen eines neuen Stils oder zum Ändern eines vorhandenen Stils aus (siehe oben).
1. hinzufügen neue Bilder in `/apps/livecycle/core/content/login`. Bild hinzufügen:

   1. Installieren Sie den WebDAV-Client.
   1. Navigieren Sie mit dem WebDAV-Client zum Ordner `/apps/livecycle/core/content/login`. Weitere Informationen finden Sie unter: [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/en/crx/current/how_to/webdav_access.html).
   1. Fügen Sie neue Bilder hinzu.

1. hinzufügen neue Stile in `/apps/livecycle/core/content/login/login.css,` entsprechend den neuen Bildern, die in `/apps/livecycle/core/content/login` hinzugefügt wurden.
1. Verwenden Sie die neuen Stile in `login.jsp` bei `/apps/livecycle/core/components`.
1. Beispiel:

   * hinzufügen Sie Folgendes zu `/apps/livecycle/core/content/login/login.css`

   ```css
   .newLoginContainerBkg {
    background-image: url(my_Bg.gif);
    background-repeat: no-repeat;
    background-position: left top;
    width: 727px;
   }
   ```

   * Ändern Sie Folgendes in /apps/livecycle/core/components/login.jsp.

   ```
   <div class="loginContainerBkg">
   
   To
   
   <div class="newLginContainerBkg">
   ```
