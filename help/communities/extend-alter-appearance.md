---
title: Erscheinungsbild ändern (HBS)
seo-title: Erscheinungsbild ändern
description: Ändern der HBS-Skripte
seo-description: Ändern der HBS-Skripte
uuid: 6e1030af-f170-4a60-9d3f-439afd05de57
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 70be208d-185b-4b27-8e01-74e62f656344
exl-id: 358b70b8-8122-4eda-baa7-d9a58d6901f9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 1%

---

# Ändern des Erscheinungsbilds (HBS) {#alter-the-appearance-hbs}

Nachdem die Komponenten für das benutzerdefinierte Kommentarsystem im Anwendungsverzeichnis (/apps) vorhanden sind, wobei ein resourceSuperType auf das standardmäßige Kommentarsystem verweist und das benutzerdefinierte Modell/die benutzerdefinierte Ansicht registriert ist, können Sie die Implementierung ändern.

Für eine einfache Demonstration, eine visuelle Funktion, wird der Avatar des angemeldeten Benutzers entfernt, der einen Kommentar veröffentlicht.

>[!NOTE]
>
>Um die Erweiterung nutzen zu können, muss die Instanz des Kommentarsystems auf einer Website, auf die sich die Auswirkungen auswirken sollen (/content), seinen resourceType als benutzerdefiniertes Kommentarsystem festlegen.

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

   * Kommentieren Sie das Tag aus, das den Avatar für den nächsten Kommentar-Eintrag enthält (~ Zeile 44):

      ```
      <!--
       <img class="scf-composer-avatar" src="{{loggedInUser.avatarUrl}}"></img>
       -->
      ```

* Wählen Sie **Alle speichern**

## Benutzerdefinierte App replizieren {#replicate-custom-app}

Nachdem die Anwendung geändert wurde, muss die benutzerdefinierte Komponente erneut repliziert werden.

Eine Möglichkeit ist, dies zu tun

* Im Hauptmenü

   * Wählen Sie **[!UICONTROL Tools > Vorgänge > Replikation]** aus.
   * Wählen Sie nun eine der folgenden Optionen aus `Activate Tree`
   * Legen Sie `Start Path` fest: nach `/apps/custom`
   * Deaktivieren Sie `Only Modified`
   * Schaltfläche `Activate` auswählen

## Anzeigen von geänderten Kommentaren auf der veröffentlichten Beispielseite {#view-modified-comment-on-published-sample-page}

[Wenn Sie das ](extend-sample-page.md#publish-sample-page) Erlebnis auf der Veröffentlichungsinstanz fortsetzen, die noch als derselbe Benutzer angemeldet ist, ist es jetzt möglich, die Seite in der Veröffentlichungsumgebung zu aktualisieren, um die Änderung zum Entfernen des Avatars anzuzeigen:

![chlimage_1-81](assets/chlimage_1-81.png)

## Beispiel für Kommentar-Erweiterungspaket {#sample-comment-extension-package}

Angehängt ist ein Paket der benutzerdefinierten Kommentaranwendung, die in diesem Tutorial erstellt wurde.

[Datei laden](assets/sample-comment-extension-6-1-fp3.zip)
