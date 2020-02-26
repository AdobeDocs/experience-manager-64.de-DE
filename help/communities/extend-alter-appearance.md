---
title: Erscheinungsbild ändern (HBS)
seo-title: Erscheinungsbild ändern
description: Ändern der HBS-Skripten
seo-description: Ändern der HBS-Skripten
uuid: 6e1030af-f170-4a60-9d3f-439afd05de57
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 70be208d-185b-4b27-8e01-74e62f656344
translation-type: tm+mt
source-git-commit: 2d1e39120d79de029927011d48f7397b53ad91bc

---


# Erscheinungsbild ändern (HBS) {#alter-the-appearance-hbs}

Nachdem die Komponenten für das benutzerdefinierte Kommentarsystem im Anwendungsverzeichnis (/apps) vorhanden sind, wobei ein resourceSuperType auf das Standard-Kommentarsystem verweist und das benutzerdefinierte Modell/View registriert ist, kann die Implementierung geändert werden.

Bei einer einfachen Demonstration wird der Avatar des angemeldeten Benutzers, der einen Kommentar veröffentlicht, entfernt.

>[!NOTE]
>
>Um die Erweiterung nutzen zu können, muss die Instanz des Kommentarsystems auf einer Website, die betroffen sein soll (/content), resourceType als benutzerdefiniertes Kommentarsystem festlegen.

## Ändern der HBS-Skripten {#modify-the-hbs-scripts}

Using [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Öffnen [/apps/custom/components/comments/comment/comment.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment/comment.hbs)

   * Kommentieren Sie das Tag aus, das den Avatar für einen Kommentar-Beitrag enthält (~ Zeile 21):

      ```
      <!--
       <<img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
       -->
      ```

* Öffnen [/apps/custom/components/comments/comments.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comments.hbs)

   * Kommentieren Sie das Tag aus, das den Avatar für den nächsten Kommentareintrag enthält (~ Zeile 44):

      ```
      <!--
       <img class="scf-composer-avatar" src="{{loggedInUser.avatarUrl}}"></img>
       -->
      ```

* Select **Save All**

## Benutzerdefinierte App replizieren {#replicate-custom-app}

Nachdem die Anwendung geändert wurde, muss die benutzerdefinierte Komponente erneut repliziert werden.

Eine Möglichkeit dazu ist

* Über das Hauptmenü

   * Wählen Sie **[!UICONTROL Werkzeuge > Vorgänge > Replikation]**
   * Wählen Sie nun eine der folgenden Optionen aus `Activate Tree`
   * Festlegen `Start Path`: nach `/apps/custom`
   * Deaktivieren `Only Modified`
   * Schaltfläche `Activate` auswählen

## Änderungskommentar auf der Seite &quot;Veröffentlichte Beispielseite&quot;anzeigen {#view-modified-comment-on-published-sample-page}

[Wenn Sie das Erlebnis](extend-sample-page.md#publish-sample-page) auf der Veröffentlichungsinstanz fortsetzen, die noch als derselbe Benutzer angemeldet ist, können Sie jetzt die Seite in der Veröffentlichungsumgebung aktualisieren, um die Änderung zum Entfernen des Avatars anzuzeigen:

![chlimage_1-81](assets/chlimage_1-81.png)

## Beispielkommentar-Erweiterungspaket {#sample-comment-extension-package}

Angehängt ist ein Paket der Anwendung für benutzerdefinierte Kommentare, die in diesem Lernprogramm erstellt wurde.

[Datei laden](assets/sample-comment-extension-6-1-fp3.zip)