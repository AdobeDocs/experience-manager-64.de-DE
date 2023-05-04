---
title: Erscheinungsbild ändern
seo-title: Alter the Appearance
description: Skript ändern
seo-description: Modify the script
uuid: 6930381b-74c1-4e63-9621-621dbedbc25e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: da3891d3-fa07-4c88-b4ac-077926b3a674
exl-id: 01a20578-56c3-41b3-8a0e-281104af2481
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 5%

---

# Erscheinungsbild ändern {#alter-the-appearance}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Skript ändern {#modify-the-script}

Das Skript comment.hbs ist für die Erstellung der gesamten HTML für jeden Kommentar verantwortlich.

So zeigen Sie den Avatar nicht neben jedem veröffentlichten Kommentar an:

1. Kopieren `comment.hbs`von `libs`nach `apps`
   1. Klicken Sie auf `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. Klicken Sie auf **[!UICONTROL Kopieren]**
   1. Klicken Sie auf `/apps/social/commons/components/hbs/comments/comment`
   1. Auswählen **[!UICONTROL Einfügen]**
1. Öffnen Sie die überlagerte `comment.hbs`
   * Doppelklicken auf Knoten  `comment.hbs`in `/apps/social/commons/components/hbs/comments/comment folder`
1. Suchen Sie die folgenden Zeilen und löschen oder kommentieren Sie sie aus:

   ```xml
   <aside class="scf-comment-author">
           <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
   ```

Löschen Sie die Zeilen oder umschließen Sie sie mit &quot;&lt;!>—&#39; und &#39;—>&#39;, um sie zu kommentieren. Außerdem werden die Zeichen &quot;xxx&quot;als visueller Indikator hinzugefügt, wo der Avatar gewesen wäre.

```xml
<!-- do not display avatar with comment
    <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

## Überlagerung replizieren {#replicate-the-overlay}

Pushen Sie die überlagerte Kommentar-Komponente mithilfe des Replikations-Tools an die Veröffentlichungsinstanz.

>[!NOTE]
>
>Eine robustere Form der Replikation wäre, ein Paket in Package Manager zu erstellen und [Aktivieren](../../help/sites-administering/package-manager.md#replicating-packages) es. Ein Package kann exportiert und archiviert werden.

Wählen Sie in der globalen Navigation die Option **[!UICONTROL Tools > Bereitstellung > Replikation]** und dann **[!UICONTROL Baum aktivieren]**.

Geben Sie für den Startpfad ein. `/apps/social/commons` und wählen Sie **[!UICONTROL Aktivieren]**.

![chlimage_1-42](assets/chlimage_1-42.png)

## Ergebnisse anzeigen {#view-results}

Wenn Sie sich als Administrator bei der Veröffentlichungsinstanz anmelden, z. B. http://localhost:4503/crx/de als Administrator/Administrator, können Sie überprüfen, ob die überlagerten Komponenten vorhanden sind.

Wenn Sie sich abmelden und sich erneut als `aaron.mcdonald@mailinator.com/password` und die Seite aktualisieren, werden Sie feststellen, dass der veröffentlichte Kommentar nicht mehr mit einem Avatar angezeigt wird, sondern eine einfache &quot;xxx&quot; angezeigt wird.

![chlimage_1-43](assets/chlimage_1-43.png)
