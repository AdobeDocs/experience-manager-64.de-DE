---
title: Konfigurieren der Einstellungen für die Kontosperrung
seo-title: Configure account-locking settings
description: Verwenden Sie die Option Kontosperrung aktivieren , um Benutzerkonten nach einer bestimmten Anzahl aufeinander folgender Authentifizierungsfehler zu sperren.
seo-description: Use the Enable Account Locking option to lock user accounts after a specified number of consecutive authentication failures.
uuid: 5ff3fb76-8b11-4818-9a75-40ed8e121da5
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d4409c6b-f4ef-499c-8daa-e93a163ff8ab
exl-id: e407c643-5753-447e-ad4e-deb7b9eb2b55
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 34%

---

# Konfigurieren der Einstellungen für die Kontosperrung {#configure-account-locking-settings}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Wenn Sie eine Domain hinzufügen, geben Sie an, ob die Kontosperrung aktiviert werden soll. Wenn die Option Kontosperrung aktivieren ausgewählt ist, werden Benutzerkonten nach einer bestimmten Anzahl aufeinander folgender Authentifizierungsfehler gesperrt. Nach einer bestimmten Zeitdauer kann der Benutzer versuchen, sich erneut zu authentifizieren. Diese Funktion verhindert, dass Benutzer verschiedene Berechtigungskombinationen für den Zugriff auf das System ausprobieren.

Geben Sie mithilfe der Einstellungen auf der Seite „Domain-Verwaltung“ die maximale Anzahl von Authentifizierungsfehlern sowie die Länge des Zeitraums, für den Konten gesperrt werden, an. Diese Einstellungen gelten für alle Domains, bei denen die Kontosperrung aktiviert ist.

1. Klicken Sie in der Administration-Console auf **[!UICONTROL Einstellungen > User Management > Domain-Verwaltung]**.
1. Geben Sie in das Feld Maximale Anzahl aufeinander folgender Authentifizierungsfehler an, wie oft ein Benutzer nacheinander nicht erfolgreich versuchen kann, sich anzumelden, bevor sein Konto gesperrt wird. Der Standardwert ist 20.
1. Geben Sie in das Feld &quot;Konto entsperren nach (Minuten)&quot;die Anzahl der Minuten ein, nach denen das Benutzerkonto gesperrt ist. Nach der angegebenen Anzahl von Minuten kann der Benutzer versuchen, sich erneut anzumelden. Der Standardwert ist 30.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
