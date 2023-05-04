---
title: Erscheinungsbild ändern (HBS)
seo-title: Alter the Appearance
description: Ändern der HBS-Skripte
seo-description: Modify the HBS scripts
uuid: 6e1030af-f170-4a60-9d3f-439afd05de57
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 70be208d-185b-4b27-8e01-74e62f656344
exl-id: 358b70b8-8122-4eda-baa7-d9a58d6901f9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 4%

---

# Erscheinungsbild ändern (HBS) {#alter-the-appearance-hbs}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Nachdem die Komponenten für das benutzerdefinierte Kommentarsystem im Anwendungsverzeichnis (/apps) vorhanden sind, wobei ein resourceSuperType auf das standardmäßige Kommentarsystem verweist und das benutzerdefinierte Modell/die benutzerdefinierte Ansicht registriert ist, können Sie die Implementierung ändern.

Für eine einfache Demonstration, eine visuelle Funktion, wird der Avatar des angemeldeten Benutzers entfernt, der einen Kommentar veröffentlicht.

>[!NOTE]
>
>Um die Erweiterung nutzen zu können, muss die Instanz des Kommentarsystems auf einer Website, auf die sich die Auswirkungen auswirken sollen (/content), seinen resourceType als benutzerdefiniertes Kommentarsystem festlegen.

## HBS-Skripte ändern {#modify-the-hbs-scripts}

Verwenden [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Öffnen [/apps/custom/components/comments/comment/comment.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment/comment.hbs)

   * Kommentieren Sie das Tag aus, das den Avatar für einen Kommentar-Beitrag enthält (~ Zeile 21):

      ```
      <!--
       <<img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
       -->
      ```

* Öffnen [/apps/custom/components/comments/comments.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comments.hbs)

   * Kommentieren Sie das Tag aus, das den Avatar für den nächsten Kommentar-Eintrag enthält (~ Zeile 44):

      ```
      <!--
       <img class="scf-composer-avatar" src="{{loggedInUser.avatarUrl}}"></img>
       -->
      ```

* Klicken Sie auf **Alle speichern**

## Benutzerdefinierte App replizieren {#replicate-custom-app}

Nachdem die Anwendung geändert wurde, muss die benutzerdefinierte Komponente erneut repliziert werden.

Eine Möglichkeit ist, dies zu tun

* Im Hauptmenü

   * Auswählen **[!UICONTROL Tools > Vorgänge > Replikation]**
   * Klicken Sie auf `Activate Tree`
   * Satz `Start Path`: nach `/apps/custom`
   * Deaktivieren `Only Modified`
   * Auswählen `Activate` button

## Anzeigen geänderter Kommentare auf der veröffentlichten Beispielseite {#view-modified-comment-on-published-sample-page}

[Fortführen des Erlebnisses](extend-sample-page.md#publish-sample-page) In der Veröffentlichungsinstanz, die noch als derselbe Benutzer angemeldet ist, ist es jetzt möglich, die Seite in der Veröffentlichungsumgebung zu aktualisieren, um die Änderung zum Entfernen des Avatars anzuzeigen:

![chlimage_1-81](assets/chlimage_1-81.png)

## Beispielpaket für Kommentar-Erweiterung {#sample-comment-extension-package}

Angehängt ist ein Paket der benutzerdefinierten Kommentaranwendung, die in diesem Tutorial erstellt wurde.

[Datei abrufen](assets/sample-comment-extension-6-1-fp3.zip)
