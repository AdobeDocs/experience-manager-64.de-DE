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
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 1%

---


# Erscheinungsbild (HBS) {#alter-the-appearance-hbs} ändern

Nachdem die Komponenten für das benutzerdefinierte Kommentarsystem im Anwendungsordner (/apps) vorhanden sind, wobei ein resourceSuperType auf das Standardkommentarsystem verweist und das benutzerdefinierte Modell/die benutzerdefinierte Ansicht registriert ist, kann die Implementierung geändert werden.

Bei einer einfachen Demonstration wird der Avatar des angemeldeten Benutzers, der einen Kommentar veröffentlicht, entfernt.

>[!NOTE]
>
>Um die Erweiterung nutzen zu können, muss die Instanz des Kommentarsystems auf einer Website, die betroffen sein soll (/content), resourceType als benutzerdefiniertes Kommentarsystem festlegen.

## Ändern Sie die HBS-Skripte {#modify-the-hbs-scripts}

Verwenden von [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Öffnen Sie [/apps/custom/components/comments/comment/comment.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment/comment.hbs)

   * Kommentieren Sie das Tag aus, das den Avatar für einen Kommentar-Beitrag enthält (~ Zeile 21):

      ```
      <!--
       <<img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
       -->
      ```

* Öffnen Sie [/apps/custom/components/comments/comments.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comments.hbs)

   * Kommentieren Sie das Tag aus, das den Avatar für den nächsten Kommentareintrag enthält (~ Zeile 44):

      ```
      <!--
       <img class="scf-composer-avatar" src="{{loggedInUser.avatarUrl}}"></img>
       -->
      ```

* Wählen Sie **Alle speichern**

## Benutzerdefinierte App replizieren {#replicate-custom-app}

Nachdem die Anwendung geändert wurde, muss die benutzerdefinierte Komponente erneut repliziert werden.

Eine Möglichkeit dazu ist

* Über das Hauptmenü

   * Wählen Sie **[!UICONTROL Tools > Vorgänge > Replikation]**
   * Wählen Sie nun eine der folgenden Optionen aus `Activate Tree`
   * Setzen Sie `Start Path`: nach `/apps/custom`
   * Deaktivieren Sie `Only Modified`
   * Schaltfläche `Activate` auswählen

## Ansicht - Modifizierter Kommentar auf der Seite mit veröffentlichten Beispielen {#view-modified-comment-on-published-sample-page}

[Wenn Sie das ](extend-sample-page.md#publish-sample-page) Erlebnis in der Veröffentlichungsinstanz fortsetzen und sich dennoch als derselbe Benutzer angemeldet haben, können Sie jetzt die Seite in der Umgebung &quot;Veröffentlichen&quot;aktualisieren, um die Änderung zum Entfernen des Avatars Ansicht:

![chlimage_1-81](assets/chlimage_1-81.png)

## Beispiel für ein Kommentar-Erweiterungspaket {#sample-comment-extension-package}

Angehängt ist ein Paket der Anwendung für benutzerdefinierte Kommentare, die in diesem Lernprogramm erstellt wurde.

[Datei laden](assets/sample-comment-extension-6-1-fp3.zip)