---
title: Erscheinungsbild ändern
seo-title: Erscheinungsbild ändern
description: Skript ändern
seo-description: Skript ändern
uuid: 6930381b-74c1-4e63-9621-621dbedbc25e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: da3891d3-fa07-4c88-b4ac-077926b3a674
translation-type: tm+mt
source-git-commit: 1ae2d7f99286e0b958d343778159e2d35095510e
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 1%

---


# Erscheinungsbild ändern {#alter-the-appearance}

## Skript {#modify-the-script} ändern

Das Skript &quot;comment.hbs&quot;ist für die Erstellung des gesamten HTML für jeden Kommentar zuständig.

So zeigen Sie den Avatar nicht neben jedem veröffentlichten Kommentar an:

1. Kopieren Sie `comment.hbs`von `libs`nach `apps`
   1. Wählen Sie nun eine der folgenden Optionen aus `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. Wählen Sie **[!UICONTROL Kopieren]**
   1. Wählen Sie nun eine der folgenden Optionen aus `/apps/social/commons/components/hbs/comments/comment`
   1. Wählen Sie **[!UICONTROL Einfügen]**
1. Öffnen Sie das überlappende `comment.hbs`
   * Dublette-Klick auf Knoten `comment.hbs`in `/apps/social/commons/components/hbs/comments/comment folder`
1. Suchen Sie die folgenden Zeilen und löschen oder kommentieren Sie sie aus:

   ```xml
   <aside class="scf-comment-author">
           <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
   ```

Löschen Sie die Zeilen oder umschließen Sie sie mit &#39;&lt;!—&#39; und &#39;—>&#39;, um sie zu kommentieren. Außerdem werden die Zeichen &quot;xxx&quot;als visueller Indikator hinzugefügt, wo der Avatar gewesen wäre.

```xml
<!-- do not display avatar with comment
    <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

## Die Überlagerung replizieren {#replicate-the-overlay}

Schieben Sie die überlagerte Kommentarkomponente mithilfe des Replizierungswerkzeugs an die Veröffentlichungsinstanz.

>[!NOTE]
>
>Eine stabilere Form der Replikation wäre, ein Paket im Package Manager zu erstellen und [zu aktivieren](../../help/sites-administering/package-manager.md#replicating-packages). Ein Paket kann exportiert und archiviert werden.

Wählen Sie in der globalen Navigation **[!UICONTROL Werkzeuge > Bereitstellung > Replikation]** und dann **[!UICONTROL Baum aktivieren]**.

Geben Sie für den Pfad des Beginns `/apps/social/commons` ein und wählen Sie **[!UICONTROL Aktivieren]**.

![chlimage_1-42](assets/chlimage_1-42.png)

## Ansicht Ergebnisse {#view-results}

Wenn Sie sich als Administrator bei der Veröffentlichungsinstanz anmelden, z. B. http://localhost:4503/crx/de als Administrator/Administrator, können Sie überprüfen, ob die überlagerten Komponenten vorhanden sind.

Wenn Sie sich abmelden und sich erneut als `aaron.mcdonald@mailinator.com/password` anmelden und die Seite aktualisieren, werden Sie feststellen, dass der gepostete Kommentar nicht mehr mit einem Avatar angezeigt wird, sondern eine einfache &quot;xxx&quot;.

![chlimage_1-43](assets/chlimage_1-43.png)

