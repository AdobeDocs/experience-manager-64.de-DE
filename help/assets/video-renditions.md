---
title: Videoausgabeformate
description: Videoausgabeformate
contentOwner: AG
feature: Video,Renditions
role: User
exl-id: 9fc93034-e83a-42b5-901d-7867b4a850a8
source-git-commit: 1e3cd6ce3138113721183439f7cfb9daed6e0e58
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 91%

---

# Videoausgabeformate {#video-renditions}

Adobe Experience Manager Assets generiert Videoausgabeformate für Video-Assets verschiedener Formate wie OGG, FLV usw.

AEM Assets unterstützt statische und dynamische Ausgabeformate (DM-kodierte Ausgabeformate) für Medien-Assets.

Statische Ausgabeformate werden nativ mit FFMPEG (im Systempfad installiert und verfügbar) generiert und im Inhalts-Repository gespeichert.

Die DM-kodierten Ausgabeformate werden im Proxyserver gespeichert und zur Laufzeit bereitgestellt.

AEM Assets bietet Wiedergabeunterstützung für diese Ausgabeformate auf Client-Seite.

Um die Ausgabeformate eines bestimmten Video-Assets anzuzeigen, öffnen Sie die entsprechende Asset-Seite und klicken oder tippen Sie auf das GlobalNav-Symbol. Wählen Sie dann **[!UICONTROL Ausgabeformate]** aus der Liste aus.

![chlimage_1-478](assets/chlimage_1-478.png)

Die Liste mit Videoausgabeformate wird im Bereich **[!UICONTROL Wiedergaben]** angezeigt.

![chlimage_1-479](assets/chlimage_1-479.png)

Konfigurieren Sie den Proxyserver für DM-kodierte Ausgabeformate, indem Sie [Cloud-Dienste für Dynamic Media konfigurieren](config-dynamic.md).

Generieren Sie Videoausgabeformate mit gewünschten Parametern, [indem Sie ein entsprechendes Videoprofil erstellen](video-profiles.md).

Nachdem Sie den Proxyserver konfiguriert und Videoprofile erstellt haben, können Sie diese Videovorlage in ein Verarbeitungsprofil aufnehmen und dieses Verarbeitungsprofil auf einen Ordner anwenden.

>[!NOTE]
>
>Die Audiowiedergabe funktioniert nicht für OGG- und WAV-Dateien in Internet Explorer 11. Auf der Seite mit den Asset-Details wird für Assets mit der Erweiterung OGG oder WAV der Fehler „Ungültige Quelle“ angezeigt.
>
>Auf MS Edge und iPad werden die OGG-Dateien nicht abgespielt und lösen den Fehler „Format nicht unterstützt“ aus.
