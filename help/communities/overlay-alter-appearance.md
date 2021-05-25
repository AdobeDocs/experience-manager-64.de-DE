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
exl-id: 01a20578-56c3-41b3-8a0e-281104af2481
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 1%

---

# Erscheinungsbild ändern {#alter-the-appearance}

## Skript {#modify-the-script} ändern

Das Skript comment.hbs ist für die Erstellung des gesamten HTML-Codes für jeden Kommentar verantwortlich.

So zeigen Sie den Avatar nicht neben jedem veröffentlichten Kommentar an:

1. Kopieren Sie `comment.hbs`von `libs`nach `apps`
   1. Wählen Sie nun eine der folgenden Optionen aus `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. Wählen Sie **[!UICONTROL Copy]**
   1. Wählen Sie nun eine der folgenden Optionen aus `/apps/social/commons/components/hbs/comments/comment`
   1. Wählen Sie **[!UICONTROL Paste]** aus.
1. Öffnen Sie die überlagerte `comment.hbs`
   * Doppelklicken Sie auf den Knoten `comment.hbs`in `/apps/social/commons/components/hbs/comments/comment folder`
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

## Replizieren Sie die Überlagerung {#replicate-the-overlay}

Pushen Sie die überlagerte Kommentar-Komponente mithilfe des Replikations-Tools an die Veröffentlichungsinstanz.

>[!NOTE]
>
>Eine robustere Form der Replikation wäre, ein Paket in Package Manager zu erstellen und [zu aktivieren](../../help/sites-administering/package-manager.md#replicating-packages). Ein Package kann exportiert und archiviert werden.

Wählen Sie in der globalen Navigation **[!UICONTROL Tools > Bereitstellung > Replikation]** und dann **[!UICONTROL Tree aktivieren]**.

Geben Sie für den Startpfad `/apps/social/commons` ein und wählen Sie **[!UICONTROL Aktivieren]**.

![chlimage_1-42](assets/chlimage_1-42.png)

## Ergebnisse anzeigen {#view-results}

Wenn Sie sich als Administrator bei der Veröffentlichungsinstanz anmelden, z. B. http://localhost:4503/crx/de als Administrator/Administrator, können Sie überprüfen, ob die überlagerten Komponenten vorhanden sind.

Wenn Sie sich abmelden und sich erneut als `aaron.mcdonald@mailinator.com/password` anmelden und die Seite aktualisieren, werden Sie feststellen, dass der veröffentlichte Kommentar nicht mehr mit einem Avatar angezeigt wird, stattdessen wird eine einfache &quot;xxx&quot;angezeigt.

![chlimage_1-43](assets/chlimage_1-43.png)
