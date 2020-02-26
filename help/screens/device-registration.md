---
title: Geräteregistrierung
seo-title: Geräteregistrierung
description: Auf dieser Seite wird der Prozess zur Geräteregistrierung in einem AEM Screens-Projekt beschrieben.
seo-description: Auf dieser Seite wird der Prozess zur Geräteregistrierung in einem AEM Screens-Projekt beschrieben.
uuid: babf0de1-1f39-4e22-82aa-ce7fa7052659
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: a1534cfd-66a1-4e28-8938-e09a24dec8ee
translation-type: tm+mt
source-git-commit: 3addef2141ebb831f8677d011d68faf88e648dc2

---


# Geräteregistrierung{#device-registration}

Auf der folgenden Seite wird der Prozess zur Geräteregistrierung in einem AEM Screens-Projekt beschrieben.

## Registrieren von Geräten {#registering-a-device}

Der Prozess zur Geräteregistrierung erfolgt auf 2 separaten Geräten:

* dem Gerät, das registriert werden soll, etwa einem Digital-Signage-Display;
* dem zur Registrierung des Geräts verwendeten AEM-Server.

>[!NOTE]
>
>Nachdem Sie die neueste Version von Windows Player (*.exe*) von der Seite [**AEM 6.4 Player-Downloads **](https://download.macromedia.com/screens/)heruntergeladen haben, führen Sie die Schritte auf dem Player aus, um die AEM-hoc-Installation abzuschließen:
>
>1. Halten Sie die linke obere Ecke gedrückt, um den Admin-Bereich zu öffnen.
>1. Navigieren Sie im linken Aktionsmenü zu **Konfiguration**, geben Sie die Standortadresse der AEM-Instanz unter **Server** ein und klicken Sie auf **Speichern**.
   >
   >
1. Klicken Sie im linken Aktionsmenü auf den Link **Registrierung** und führen Sie die folgenden Schritte aus, um die Geräteregistrierung abzuschließen.
>



![screen_shot_2018-11-26at12118pm](assets/screen_shot_2018-11-26at12118pm.png)

1. Starten Sie AEM Screens Player auf dem Gerät. Daraufhin wird die Benutzeroberfläche für die Registrierung angezeigt.

   ![screen_shot_2018-11-26at104230am](assets/screen_shot_2018-11-26at104230am.png)

1. Navigieren Sie in AEM zum Ordner **Geräte** Ihres Projekts.

   >[!NOTE]
   >
   >Weitere Informationen zum Erstellen eines neuen Projekts für Screens im AEM-Dashboard finden Sie unter [Erstellen und Verwalten von Screens-Projekten](/help/screens/creating-a-screens-project.md).

1. Tippen/klicken Sie in der Aktionsleiste auf die Schaltfläche **Geräte-Manager**.

   ![screen_shot_2018-11-26at104702am](assets/screen_shot_2018-11-26at104702am.png)

1. Tippen/klicken Sie oben rechts auf die Schaltfläche **Geräteregistrierung**.

   ![screen_shot_2018-11-26at104815am](assets/screen_shot_2018-11-26at104815am.png)

1. Wählen Sie das erforderliche Gerät (dasselbe wie in Schritt 1) aus und tippen/klicken Sie auf **Gerät registrieren**.

   ![screen_shot_2018-11-26at105112am](assets/screen_shot_2018-11-26at105112am.png)

1. Warten Sie in AEM darauf, dass das Gerät seinen Registrierungs-Code sendet.

   ![screen_shot_2018-11-26at105150am](assets/screen_shot_2018-11-26at105150am.png)

1. Prüfen Sie den **Registrierungs-Code** auf Ihrem Gerät.

   ![screen_shot_2018-11-26at105227am](assets/screen_shot_2018-11-26at105227am.png)

1. Wenn der **Registrierungs-Code** auf beiden Geräten identisch ist, tippen/klicken Sie in AEM auf die Schaltfläche **Validieren**, wie in Schritt (6) gezeigt.
1. Legen Sie den gewünschten Namen für das Gerät fest und wählen Sie die Schaltfläche „Registrieren“ aus.

   ![screen_shot_2018-11-26at105357am](assets/screen_shot_2018-11-26at105357am.png)

1. Tippen/klicken Sie auf „Beenden“, um den Registrierungsprozess abzuschließen.

   ![screen_shot_2018-11-26at105456am](assets/screen_shot_2018-11-26at105456am.png)

   >[!NOTE]
   >
   >Mit **Neu registrieren** können Sie ein neues Gerät registrieren.
   >
   >Mit **Anzeige zuweisen** können Sie das Gerät direkt einer Anzeige hinzufügen.

   Wenn Sie auf **Beenden** klicken, müssen Sie das Gerät einer Anzeige zuweisen.

   ![screen_shot_2018-11-26at105740am](assets/screen_shot_2018-11-26at105740am.png)

   >[!NOTE]
   >
   >Weitere Informationen zum Erstellen und Verwalten einer Anzeige für Ihr Screens-Projekt finden Sie unter [Erstellen und Verwalten von Anzeigen](/help/screens/managing-displays.md).

### Zuweisen eines Geräts zu einer Anzeige {#assigning-device-to-a-display}

Wenn Sie das Gerät nicht einer Anzeige zugewiesen haben, führen Sie die folgenden Schritte aus, um das Gerät einer Anzeige in Ihrem AEM Screens-Projekt zuzuweisen:

1. Wählen Sie das Gerät aus und klicken Sie in der Aktionsleiste auf **Gerät zuweisen**.

   ![screen_shot_2018-11-26at111026am](assets/screen_shot_2018-11-26at111026am.png)

1. Wählen Sie den Pfad der Anzeige unter **Anzeige-/Gerätekonfiguration** aus.

   ![screen_shot_2018-11-26at111252am](assets/screen_shot_2018-11-26at111252am.png)

1. Klicken Sie auf **Zuweisen**, wenn Sie den Pfad auswählen.

   ![screen_shot_2018-11-26at111722am](assets/screen_shot_2018-11-26at111722am.png)

1. Klicken Sie auf **Beenden**, sobald das Gerät erfolgreich zugewiesen wurde, wie in der folgenden Abbildung dargestellt.

   ![screen_shot_2018-11-26at112041am](assets/screen_shot_2018-11-26at112041am.png)

   Außerdem können Sie das Anzeigen-Dashboard anzeigen, wenn Sie auf **Beenden** klicken.

   ![screen_shot_2018-11-26at112154am](assets/screen_shot_2018-11-26at112154am.png)

## Einschränkungen bei der Geräteregistrierung  {#limitations-on-device-registration}

Systemweite Einschränkungen für Benutzerkennwörter verursachen möglicherweise einen Fehler bei der Geräteregistrierung. Bei der Geräteregistrierung wird ein zufällig generiertes Kennwort verwendet, um den Gerätebenutzer zu erstellen.

Wenn das Kennwort durch die Konfiguration von *AuthorizableActionProvider* eingeschränkt ist, kann der Gerätebenutzer möglicherweise nicht erstellt werden.

>[!NOTE]
>
>Das zufällig generierte Kennwort besteht zurzeit aus 36 ASCII-Zeichen aus dem Bereich von 33 bis 122 (enthält fast alle Sonderzeichen).

```java
25.09.2016 16:54:03.140 *ERROR* [59.100.121.82 [1474844043109] POST /content/screens/svc/registration HTTP/1.1] com.adobe.cq.screens.device.registration.impl.RegistrationServlet Error during device registration
javax.jcr.nodetype.ConstraintViolationException: Password violates password constraint (^(?=.*\d).{7,9}$).
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.validatePassword(PasswordValidationAction.java:105)
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.onPasswordChange(PasswordValidationAction.java:76)
        at org.apache.jackrabbit.oak.security.user.UserManagerImpl.onPasswordChange(UserManagerImpl.java:308)
```

### Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zum AEM Screens-Player finden Sie unter [AEM Screens-Player](/help/screens/working-with-screens-player.md).
