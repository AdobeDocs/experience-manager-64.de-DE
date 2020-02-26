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
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Erstellen eines neuen Anmeldungsbildschirms {#creating-a-new-login-screen}

Sie können den Anmeldungsbildschirm aller Module von AEM Forms ändern, die den AEM Forms-Anmeldungsbildschirm verwenden. Die Änderungen wirken sich beispielsweise auf den Anmeldungsbildschirm, den Formularmanager und AEM Forms aus.

## Voraussetzung {#prerequisite}

1. Log in at `/lc/crx/de` with Administrator permissions.
1. Führen Sie die folgenden Aktionen durch:

   1. Replizieren Sie die hierarchische Struktur: von `/libs/livecycle/core/content` at `/apps/livecycle/core/content`. Behalten Sie die Eigenschaften (Knoten/Ordner) und Zugriffssteuerung bei.
   1. Copy the content folder: from `/libs/livecycle/core` to `/apps/livecycle/core`.
   1. Delete the contents of `/apps/livecycle/core` folder.

1. Führen Sie die folgenden Aktionen durch:

   1. Replizieren Sie die hierarchische Struktur: von `/libs/livecycle/core/components/login` at `/apps/livecycle/core/components/login`. Behalten Sie die Eigenschaften (Knoten/Ordner) und Zugriffssteuerung bei.
   1. Copy the components folder: from `/libs/livecycle/core` to `/apps/livecycle/core`.
   1. Delete the contents of the folder: `/apps/livecycle/core/components/login`.

## Hinzufügen eines neuen Gebietsschemas {#adding-a-new-locale}

1. Kopieren Sie den `i18n` Ordner:

   * from `/libs/livecycle/core/components/login`
   * in `/apps/livecycle/core/components/login`

1. Delete all the folders inside `i18n` except one, say `en`.
1. Mit dem Ordner `en` führen Sie diese Schritte durch:

   1. Benennen Sie den Ordner nach dem Gebietsschema, das unterstützt werden soll. Beispiel, `ar`.
   1. Change the property `jcr:language` value to `ar`(for the `ar` folder).
   >[!NOTE]
   >
   >Wenn das Gebietsschema eine Sprach- und Ländercodekombination ist, beispielsweise `ar-DZ`, ändern Sie den Ordnernamen und den Eigenschaftswert zu `ar-DZ`.

1. Kopieren `login.jsp`:

   * from `/libs/livecycle/core/components/login`
   * in `/apps/livecycle/core/components/login`

1. Modify the following snippet of code for `/apps/livecycle/core/components/login/login.jsp`:

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

## Hinzufügen von neuem Text oder Ändern des vorhandenen Texts {#adding-new-text-or-modifying-existing-text}

1. Ordner `i18n` kopieren:

   * from `/libs/livecycle/core/components/login`
   * in `/apps/livecycle/core/components/login`

1. Ändern Sie nun den Wert der Eigenschaft `sling:message` des Knotens (unter dem Codeordner des gewünschten Gebietsschemas) für den Sie den Text ändern möchten. Die Übersetzung wird mit dem Schlüssel durchgeführt, der im Wert der Eigenschaft `sling:key` des Knotens aufgeführt ist.
1. Zum Hinzufügen des neuen Schlüssel-Wert-Paars führen Sie die folgenden Schritte aus. Überprüfen Sie ein Beispiel auf dem darauffolgenden Screenshot.

   1. Erstellen Sie unter den Gebietsschemaordnern einen Knoten vom Typ `sling:MessageEntry` oder kopieren Sie einen vorhandenen Knoten und benennen Sie ihn um.
   1. Kopieren `login.jsp` :

      * from `/libs/livecycle/core/components/login`
      * in `/apps/livecycle/core/components/login`
   1. Modify `/apps/livecycle/core/components/login/login.jsp` to incorporate the newly added text.
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

1. Copy `login` node:

   * from `/libs/livecycle/core/content`
   * in `/apps/livecycle/core/content`

1. Löschen von Dateien `login.js` und `jquery-1.8.0.min.js`von der Node `/apps/livecycle/core/content/login.`
1. Ändern Sie die Stile in der CSS-Datei.
1. Neue Stile hinzufügen:

   1. Neue Stile hinzufügen zu `/apps/livecycle/core/content/login/login.css`
   1. Kopieren `login.jsp`

      * from `/libs/livecycle/core/components/login`
      * in `/apps/livecycle/core/components/login`
   1. Modify `/apps/livecycle/core/components/login/login.jsp` to incorporate the newly added styles.


1. Beispiel:

   * Add the following to `/apps/livecycle/core/content/login/login.css`.

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
>If the existing images in `/apps/livecycle/core/content/login` (copied from `/libs/livecycle/core/content/login`) are removed, then remove the corresponding references in CSS.

## Fügen Sie neue Bilder hinzu {#add-new-images}

1. Führen Sie die Schritte zum Hinzufügen eines neuen Stils oder zum Ändern eines vorhandenen Stils aus (siehe oben).
1. Add new images in `/apps/livecycle/core/content/login`. Bild hinzufügen:

   1. Installieren Sie den WebDAV-Client.
   1. Navigate to `/apps/livecycle/core/content/login` folder, using webDAV client. For more information, see: [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/en/crx/current/how_to/webdav_access.html).
   1. Fügen Sie neue Bilder hinzu.

1. Fügen Sie neue Stile in `/apps/livecycle/core/content/login/login.css,` Übereinstimmung mit neuen Bildern in `/apps/livecycle/core/content/login`.
1. Use the new styles in `login.jsp` at `/apps/livecycle/core/components`.
1. Beispiel:

   * Add the following to `/apps/livecycle/core/content/login/login.css`

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

[Support kontaktieren](https://www.adobe.com/account/sign-in.supportportal.html)
