---
title: Informationen zur Verwendung der Berechtigung überprüfen
seo-title: Review credential use information
description: Erfahren Sie, wie Sie die Informationen zur Verwendung der Berechtigung überprüfen.
seo-description: Learn how to review credential use information.
uuid: 02af75f9-c235-470d-a98b-a2102aa31381
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: cdf61cff-768b-49f7-9926-400bc96b0708
exl-id: abd62cca-edf0-4b44-94c3-7af3116b0c54
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 93%

---

# Informationen zur Verwendung der Berechtigung überprüfen {#review-credential-use-information}

Die Berechtigung enthält Informationen zu ihrem vorgesehenen Zweck, auf die über die Acrobat Reader DC Extensions-Webanwendung für Endbenutzer zugegriffen werden kann. Anhand dieser Informationen können Sie den Typ der installierten Berechtigung (entweder Test oder Produktion) und die Gültigkeitsdauer bestimmen.

1. Öffnen Sie einen Webbrowser und geben Sie diese URL ein:

   http://localhost:*[port]*/ReaderExtensions (wobei *[port]* die Anschlussnummer Ihres Anwendungsservers)

1. Melden Sie sich mit dem standardmäßigen Benutzernamen und Kennwort an:

   Benutzername: administrator

   Kennwort: password

   >[!NOTE]
   >
   >Sie benötigen Administrator- oder Hauptbenutzerberechtigungen, um sich mit dem standardmäßigen Benutzernamen und Kennwort anmelden zu können. Um anderen Benutzern den Zugriff auf Acrobat Reader DC Extensions zu erlauben, erstellen Sie die Benutzerkonten in User Management und weisen Sie ihnen die Rolle „Acrobat Reader DC Extensions-Webanwendung“ zu.

1. Wählen Sie den Berechtigungsalias in der Liste „Berechtigung auswählen“ aus und überprüfen Sie die Informationen in den Feldern „Ablaufdatum“ und „Hinweis zur bestimmungsgemäßen Verwendung“.

>[!NOTE]
>
>Das Ablaufdatum finden Sie auch in Administration Console auf der Seite „Einstellungen“ > „Trust Store-Verwaltung“ > „Lokale Berechtigungen“ unter „Ablaufdatum“.
