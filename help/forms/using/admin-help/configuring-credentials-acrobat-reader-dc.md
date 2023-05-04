---
title: Konfigurieren von Berechtigungen für die Verwendung mit Acrobat Reader DC Extensions
seo-title: Configuring credentials for use with Acrobat Reader DC extensions
description: Erfahren Sie, wie Sie Anmeldeinformationen für die Verwendung mit Acrobat Reader DC-Erweiterungen konfigurieren.
seo-description: Learn how to configure credentials for use with Acrobat Reader DC extensions.
uuid: 9210e6c9-6f5c-402d-b355-b104cdffd5eb
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 5bb32fb1-4b6e-412f-aa16-f60db9dcaba1
exl-id: 40c2e205-0115-4ebe-ab24-66c8ee0663fa
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 15%

---

# Konfigurieren von Berechtigungen für die Verwendung mit Acrobat Reader DC Extensions{#configuring-credentials-for-use-with-acrobat-reader-dc-extensions}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Um Verwendungsrechte auf PDF-Dokumente anzuwenden, konfigurieren Sie AEM Formulare mit einer gültigen Berechtigung für Acrobat Reader DC-Erweiterungen. Während der Installation von AEM Formularen wurden möglicherweise Anmeldedaten konfiguriert. Wenn Sie Ihre Acrobat Reader DC Extensions-Berechtigung nicht während der Ausführung von Configuration Manager konfiguriert haben oder wenn Sie neue oder Ersatzberechtigungen importieren müssen, können Sie dies über die Seiten für die Trust Store-Verwaltung tun.

Wenn Sie eine Testberechtigung verwenden, ersetzen Sie sie beim Wechsel in Ihre Produktionsumgebung durch eine Produktionsberechtigung. Um eine abgelaufene Berechtigung oder Testberechtigung zu aktualisieren, löschen Sie zunächst die alte Berechtigung für Acrobat Reader DC Extensions.

Informationen zum Abrufen einer Berechtigung finden Sie unter [Vorbereiten der Installation von AEM Forms (Einzelserver)](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_63_de).

Der Trust Store kann mehr als eine Berechtigung für Acrobat Reader DC Extensions enthalten. Sie müssen eine dieser Anmeldedaten als Standardberechtigung für Reader Extensions festlegen. Die Standardberechtigung wird verwendet, wenn ein Workbench-Benutzer nicht ermitteln kann, welche Berechtigung bei der Prozesserstellung verwendet werden soll. Diese Regeln gelten für Standardanmeldedaten:

* Wenn Sie eine Acrobat Reader DC Extensions-Berechtigung importieren und der Trust Store keine anderen Acrobat Reader DC Extensions-Anmeldeinformationen enthält, wird diese als Standard festgelegt.
* Wenn Sie eine Acrobat Reader DC Extensions-Berechtigung importieren und die Option Standard ausgewählt ist, wird der Standardtyp aus einer vorhandenen Standardberechtigung entfernt. Die importierte Berechtigung wird die Standardberechtigung.
* Sie können keine standardmäßigen Acrobat Reader DC Extensions-Berechtigungen löschen. Um die Standardberechtigung zu löschen, legen Sie zunächst eine andere Berechtigung als Standard fest. Eine Ausnahme von dieser Regel besteht darin, dass Sie, wenn nur eine Berechtigung vorhanden ist, diese löschen können, auch wenn es sich um die Standardberechtigung handelt.
* Sie können keine standardmäßigen Acrobat Reader DC Extensions-Anmeldedaten aktualisieren.

>[!NOTE]
>
>Sie können Berechtigungen auch programmgesteuert importieren und löschen. (Siehe [Programmieren mit AEM Formularen](https://www.adobe.com/go/learn_aemforms_programming_63_de).

## Acrobat Reader DC Extensions-Berechtigung importieren {#import-a-acrobat-reader-dc-extensions-credential}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „Trust Store-Verwaltung“ > „Lokale Berechtigungen“.
1. Klicken Sie auf &quot;Importieren&quot;und wählen Sie unter &quot;Trust Store-Typ&quot;die Option &quot;Acrobat Reader DC Extensions-Berechtigung&quot;aus.
1. (Optional) Um anzugeben, dass diese Berechtigung die Standardberechtigung für die Verwendung mit Acrobat Reader DC-Erweiterungen ist, wählen Sie &quot;Standard&quot;aus.
1. Geben Sie in das Feld &quot;Alias&quot;eine Kennung für die Berechtigung ein. Diese Kennung wird als Anzeigename für die Berechtigung in Acrobat Reader DC-Erweiterungen verwendet. Dieser Alias wird auch verwendet, um mithilfe des AEM Forms SDK programmgesteuert auf die Berechtigung zuzugreifen.

   >[!NOTE]
   >
   >Der Aliasname wird zu Anzeigezwecken automatisch in Großbuchstaben umgewandelt. Beim Aliasnamen wird nicht zwischen Groß- und Kleinschreibung unterschieden, wenn Sie in einem Prozess darauf verweisen.

1. Klicken Sie auf „Eine Datei auswählen“, um die Berechtigung zu suchen. Geben Sie das Kennwort der Berechtigung ein und klicken Sie auf „OK“.

   Wenn die Fehlermeldung &quot;Berechtigung konnte nicht importiert werden aufgrund eines falschen Dateiformats oder eines falschen Kennworts&quot;angezeigt wird, überprüfen Sie, ob das Kennwort gültig ist.

## Berechtigung für Acrobat Reader DC Extensions entfernen {#remove-a-acrobat-reader-dc-extensions-credential}

1. Klicken Sie in der Administration-Console auf „Einstellungen“ > „Trust Store-Verwaltung“ > „Lokale Berechtigungen“.
1. Wählen Sie die Berechtigung aus und klicken Sie auf &quot;Löschen&quot;.

## Acrobat Reader DC Extensions-Berechtigung ersetzen {#replace-a-acrobat-reader-dc-extensions-credential}

1. Klicken Sie in der Administration-Console auf „Einstellungen“ > „Trust Store-Verwaltung“ > „Lokale Berechtigungen“.
1. Notieren Sie sich den Alias der vorhandenen Berechtigung, wählen Sie ihn aus und klicken Sie auf &quot;Löschen&quot;.
1. Importieren Sie die neue Berechtigung mit exakt demselben Aliasnamen.
