---
title: AEM Screens-Benachrichtigungsdienst
seo-title: AEM Screens-Benachrichtigungsdienst
description: Auf dieser Seite erfahren Sie mehr darüber, wie Sie Geräteaktivität überwachen können.
seo-description: Auf dieser Seite erfahren Sie mehr darüber, wie Sie Geräteaktivität überwachen können.
uuid: 9843219d-ed39-4e4f-bef4-e500528ff9f1
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: authoring
discoiquuid: 8879e510-4f0e-46da-87d2-77c5aaacb26e
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# AEM Screens-Benachrichtigungsdienst{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

Der ***AEM Screens-Benachrichtigungsdienst*** beschreibt die Funktion, mit der Sie Geräteaktivität überwachen können.

In diesem Abschnitt werden folgende Themen behandelt:

* **Überblick**
* **Konfigurieren der E-Mail-Einstellungen**
* **E-Mail-Benachrichtigung**
* **Anwendungsbeispiel**

>[!CAUTION]
>
>Diese AEM Screens-Funktion ist nur verfügbar, wenn Sie AEM 6.3.2 Feature Pack 3 oder AEM 6.4.1 Screens Feature Pack 1 installiert haben.
>
>Wenden Sie sich an den Adobe-Support, um Zugriff auf dieses Feature Pack zu erhalten. Wenn Sie die entsprechenden Berechtigungen erhalten haben, können Sie es von Package Share herunterladen.

## Überblick {#overview}

Der ***AEM Screens-Benachrichtigungsdienst*** bietet Administratoren die Möglichkeit, eine E-Mail zu empfangen, wenn ein AEM Screens-Player in einem konfigurierbaren Zeitraum nicht gepingt hat.

Der Dienst lässt sich in der OSGi-Web-Konsole einrichten.

## Konfigurieren der E-Mail-Einstellungen {#configuring-email-settings}

Gehen Sie wie folgt vor, um die Einstellungen für E-Mail-Benachrichtigungen zu konfigurieren:

1. Öffnen Sie die **Konfiguration der Adobe Experience Manager-Web-Konsole**.
1. Öffnen Sie den **Screens-E-Mail-Überwachungsdienst für Geräte**.

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. Definieren Sie die folgenden Felder, um Ihre Einstellungen für E-Mail zu konfigurieren:

   **Gerätepfad**: Geben Sie den Pfad zu den Screens-Projekten ein, die Sie überwachen möchten. Der Pfad heißt gewöhnlich `/home/users/screens/<Name of your project>`.

   Wenn Ihr Projekt beispielsweise **We.Retail** lautet, verwenden Sie ***/home/users/screens/we-retail*** als Projektpfad.

   >[!NOTE]
   >
   >Geben Sie den Projektpfad an, unter dem sich die Gerätebenutzer befinden.

   **Häufigkeit**: Geben Sie eine Zeit (z. B. 17.00 Uhr oder 23.00 Uhr) oder eine Häufigkeit in Stunden (z. B. 1) an, zu der der Dienst E-Mails senden soll.

   **Ping-Timeout**: Gibt das Intervall in Minuten an, nach dem ein Gerät als nicht erreichbar betrachtet werden soll.

   **SMTP-Server** Gibt den SMTP-Server an, der zum Senden von E-Mails verwendet werden soll.

   **SMTP-Port** Gibt den SMTP-Port an.

   **Mit TLS**: Mit Transport Layer Security (TLS) können Sie für eine sichere Kommunikation mit dem SMTP-Server sorgen.

   Es wird empfohlen, für sichere Verbindungen mit Unternehmens-E-Mail-Servern TLS zu verwenden. Fragen Sie Ihren E-Mail-Administrator nach geeigneten Werten.

   **Benutzername**: Geben Sie den Benutzernamen zum Senden von E-Mails an.

   **Kennwort**: Geben Sie das Kennwort zum Senden von E-Mails an.

   **Empfänger**: Geben Sie die E-Mail-Adresse des Empfängers an.

   >[!NOTE]
   >
   >Sie können nur eine E-Mail-Adresse eingeben. Um eine Massen-E-Mail zu senden, erstellen Sie eine Gruppen- oder Verteilerliste mit den gewünschten Benutzern.

1. Klicken Sie auf **Speichern**, um die Überwachungsaktivität per E-Mail für Ihr AEM Screens-Gerät zu konfigurieren.

## E-Mail-Benachrichtigung {#email-notification}

Nachdem Sie die E-Mail-Benachrichtigungen konfiguriert haben, erhalten Sie eine E-Mail-Benachrichtigung, die den Link zum eigentlichen Gerät enthält, auf dem die Inaktivität gemeldet wurde.

Durch Zugriff auf diesen Link gelangen Sie direkt zum Geräte-Dashboard.

E-Mails werden nur gesendet, wenn es mindestens ein Gerät gibt, das im angegebenen Ping-Zeitraum nicht gepingt hat und zum Zeitpunkt der Generierung der E-Mail immer noch nicht pingt.

### Anwendungsbeispiele {#example-use-cases}

Im folgenden Beispiel werden zur Referenz einige Szenarien beschrieben, in denen die Eigenschaften des E-Mail-Überwachungsdiensts für Screens-Geräte konfiguriert werden.

**Szenario 1**:

Wenn Sie die Häufigkeit auf 1.00 Uhr und das Ping-Timeout auf 60 setzen, erhalten Sie, sollte Ihr Screens-Gerät zwischen 12.00 Uhr und 13:00 Uhr nicht pingen, eine E-Mail-Benachrichtigung, mit der die Inaktivität des Geräts bestätigt wird.

**Szenario 2**:

Wenn Sie die Häufigkeit auf 1 und das Ping-Timeout auf 60 setzen, erhalten Sie, sollte das Screens-Gerät zu keiner beliebigen Tageszeit pingen, eine E-Mail-Benachrichtigung, mit der die Inaktivität des Geräts bestätigt wird.
