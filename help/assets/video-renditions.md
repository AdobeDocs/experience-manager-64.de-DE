---
title: Videoausgabeformate
description: Videoausgabeformate
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Videoausgabeformate {#video-renditions}

Adobe Experience Manager (AEM) Assets erstellt Videoausgabeformate für Video-Assets verschiedener Formate, einschließlich OGG, FLV usw.

AEM Assets unterstützt statische und dynamische Ausgabeformate (DM-kodierte Ausgabeformate) für Medien-Assets.

Statische Ausgabeformate werden nativ mit FFMPEG (im Systempfad installiert und verfügbar) generiert und im Inhalts-Repository gespeichert.

Die DM-kodierten Darstellungen werden im Proxyserver gespeichert und zur Laufzeit bereitgestellt.

AEM Assets bietet Wiedergabeunterstützung für diese Ausgabeformate auf Clientseite.

Um die Darstellungen eines bestimmten Video-Assets anzuzeigen, öffnen Sie dessen Asset-Seite und tippen Sie auf das Symbol für globale Navigation. Then, choose **[!UICONTROL Renditions]** from the list.

![chlimage_1-478](assets/chlimage_1-478.png)

Die Liste mit Videoausgabeformaten wird im Bereich **[!UICONTROL Ausgabeformate]** angezeigt.

![chlimage_1-479](assets/chlimage_1-479.png)

Konfigurieren Sie den Proxyserver für DM-kodierte Ausgabeformate, indem Sie [Cloud-Dienste für Dynamic Media konfigurieren](config-dynamic.md).

Generieren Sie Videoausgabeformate mit gewünschten Parametern, [indem Sie ein entsprechendes Videoprofil erstellen](video-profiles.md).

Nachdem Sie den Proxyserver konfiguriert und Videoprofile erstellt haben, können Sie diese Videovorlage in ein Verarbeitungsprofil aufnehmen und dieses Verarbeitungsprofil auf einen Ordner anwenden.

>[!NOTE]
>
>Die Audiowiedergabe funktioniert nicht für OGG- und WAV-Dateien in Internet Explorer 11. Auf der Seite mit den Asset-Details wird für Assets mit der Erweiterung OGG oder WAV der Fehler „Ungültige Quelle“ angezeigt.
>
>Auf MS Edge und iPad werden die OGG-Dateien nicht abgespielt und lösen den Fehler „Format nicht unterstützt“ aus.
