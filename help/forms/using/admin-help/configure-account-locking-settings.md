---
title: Einstellungen für die Kontosperrung konfigurieren
seo-title: Configure account-locking settings
description: Verwenden Sie die Option „Kontosperrung aktivieren“, um Benutzerkonten nach einer bestimmten Anzahl aufeinanderfolgender Authentifizierungsfehler zu sperren.
seo-description: Use the Enable Account Locking option to lock user accounts after a specified number of consecutive authentication failures.
uuid: 5ff3fb76-8b11-4818-9a75-40ed8e121da5
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d4409c6b-f4ef-499c-8daa-e93a163ff8ab
exl-id: e407c643-5753-447e-ad4e-deb7b9eb2b55
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 95%

---

# Einstellungen für die Kontosperrung konfigurieren {#configure-account-locking-settings}

Wenn Sie eine Domäne hinzufügen, geben Sie an, ob die Kontosperrung aktiviert werden soll. Wenn die Option „Kontosperrung aktivieren“ aktiviert ist, werden Benutzerkonten nach einer bestimmten Anzahl aufeinander folgender Authentifizierungsfehler gesperrt. Nach einem bestimmten Zeitraum kann der Benutzer eine erneute Authentifizierung versuchen. Dies verhindert, dass Benutzer verschiedene Berechtigungskombinationen für den Systemzugriff zu verwenden versuchen.

Geben Sie mithilfe der Einstellungen auf der Seite „Domänenverwaltung“ die maximale Anzahl von Authentifizierungsfehlern sowie die Länge des Zeitraums, für den Konten gesperrt werden, an. Diese Einstellungen gelten für alle Domänen, bei denen die Kontosperrung aktiviert ist.

1. Klicken Sie in Administration Console auf **[!UICONTROL Einstellungen > Benutzerverwaltung > Domänenverwaltung]**.
1. Geben Sie in das Feld „Maximale Anzahl aufeinanderfolgender Authentifizierungsfehler“ ein, wie oft sich ein Benutzer aufeinanderfolgend fehlerhaft anmelden darf, bevor sein Konto gesperrt wird. Der Standardwert ist 20.
1. Geben Sie in das Feld „Sperre für Konto aufheben nach (Minuten)“ die Minutenzahl ein, für die das Benutzerkonto gesperrt wird. Nach einer bestimmten Minutenzahl kann der Benutzer eine erneute Anmeldung versuchen. Der Standardwert ist 30.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
