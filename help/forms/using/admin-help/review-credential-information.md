---
title: Überprüfen der Informationen zur Verwendung von Anmeldedaten
seo-title: Review credential use information
description: Erfahren Sie, wie Sie Informationen zur Nutzung von Berechtigungen überprüfen.
seo-description: Learn how to review credential use information.
uuid: 02af75f9-c235-470d-a98b-a2102aa31381
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: cdf61cff-768b-49f7-9926-400bc96b0708
exl-id: abd62cca-edf0-4b44-94c3-7af3116b0c54
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 8%

---

# Überprüfen der Informationen zur Verwendung von Anmeldedaten {#review-credential-use-information}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die Berechtigung enthält Informationen zur Beschreibung der vorgesehenen Verwendung, auf die über die Acrobat Reader DC Extensions-Webanwendung für Endbenutzer zugegriffen werden kann. Mithilfe dieser Informationen können Sie den Typ der installierten Berechtigung (entweder Test oder Produktion) und deren Gültigkeitsdaten bestimmen.

1. Öffnen Sie einen Webbrowser und geben Sie diese URL ein:

   http://localhost:*[port]*/ReaderExtensions (wobei *[port]* die Anschlussnummer Ihres Anwendungsservers)

1. Melden Sie sich mit dem Standardbenutzernamen und -kennwort an:

   Benutzername: administrator

   Kennwort: password

   >[!NOTE]
   >
   >Sie müssen über Administrator- oder Superuser-Berechtigungen verfügen, um sich mit dem Standardbenutzernamen und -kennwort anzumelden. Um anderen Benutzern den Zugriff auf Acrobat Reader DC-Erweiterungen zu ermöglichen, erstellen Sie die Benutzerkonten in User Management und weisen Sie den Benutzern die Rolle Acrobat Reader DC Extensions-Webanwendung zu.

1. Wählen Sie den Berechtigungsalias aus der Liste &quot;Berechtigung auswählen&quot;aus und überprüfen Sie die Informationen in den Abschnitten &quot;Ablaufdatum&quot;und &quot;Hinweis zur vorgesehenen Verwendung&quot;.

>[!NOTE]
>
>Das Ablaufdatum der Berechtigung ist auch auf der Seite Einstellungen > Trust Store-Verwaltung > Lokale Berechtigungen in Administration Console unter &quot;Ablaufdatum&quot;verfügbar.
