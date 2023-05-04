---
title: Verwalten lokaler Anmeldeinformationen
seo-title: Managing local credentials
description: Erfahren Sie, wie Sie lokale Anmeldeinformationen verwalten.
seo-description: Learn how to manage local credentials.
uuid: 3c4358e0-aaff-4e94-a6b2-04b463fca260
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 598a9a03-3773-4620-8867-1f754d8ca031
exl-id: f8c6f4e3-4c2d-4843-8f29-6d3297e57c89
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 21%

---

# Verwalten lokaler Anmeldeinformationen {#managing-local-credentials}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Lokale Anmeldeinformationen sind Anmeldedaten für private Schlüssel, die in der Trust Store-Verwaltung gehostet werden. A *lokale Berechtigungen* gibt an, wo die DES-Berechtigung eines Benutzers gespeichert ist. Mithilfe der Trust Store-Verwaltung können Sie Ihre lokalen Berechtigungen importieren und verwalten, indem Sie beispielsweise vorhandene PFX-Dateien verwenden, damit Sie lokale Berechtigungen importieren, bearbeiten und löschen können.

AEM Forms unterstützt RSA- und DSA-Anmeldeinformationen mit bis zu 4096 Bit im PKCS12-Standardformat (.pfx- und .p12-Dateien).

Sie können beliebig viele Anmeldeinformationen importieren und exportieren. Wenn Sie eine abgelaufene Berechtigung mit demselben Alias ersetzen möchten, löschen Sie die Berechtigung und importieren Sie dann die neue Berechtigung mit demselben Alias.

Informationen und Anweisungen zu Acrobat Reader DC-Erweiterungen finden Sie unter [Konfigurieren von Berechtigungen für die Verwendung mit Acrobat Reader DC Extensions](/help/forms/using/admin-help/configuring-credentials-acrobat-reader-dc.md#configuring-credentials-for-use-with-acrobat-reader-dc-extensions).

## Berechtigung importieren {#import-a-credential}

1. Klicken Sie in der Administration-Console auf „Einstellungen“ > „Trust Store-Verwaltung“ > „Lokale Berechtigungen“.
1. Klicken Sie auf Importieren. Wählen Sie unter &quot;Trust Store Type&quot;eine der folgenden Optionen aus:

   * **Berechtigung für die Dokumentsignierung:** Eine Berechtigung, die zum Hinzufügen einer digitalen Signatur zu einem Dokument dient.
   * **Berechtigung für Acrobat Reader DC Extensions:** Ein digitales Zertifikat, das speziell für Acrobat Reader DC Extensions gilt und die Aktivierung von Adobe Reader-Benutzerrechten in den erstellten PDF-Dokumenten ermöglicht.
   * **Standard:** Zeigt an, dass dies die Standardberechtigung ist, die mit Acrobat Reader DC Extensions verwendet werden soll.

   Informationen zum Abrufen einer Berechtigung finden Sie unter [Vorbereiten der Installation AEM Formulare](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_63_de).

1. Geben Sie in das Feld &quot;Alias&quot;eine Kennung für die Berechtigung ein. Diese Kennung wird als Anzeigename für die Berechtigung in Acrobat Reader DC Extensions und dem Signature-Dienst verwendet. Dieser Alias wird auch verwendet, um mithilfe des AEM Forms SDK programmgesteuert auf die Berechtigung zuzugreifen.

   >[!NOTE]
   >
   >Der Aliasname wird zu Anzeigezwecken automatisch in Großbuchstaben umgewandelt. Beim Aliasnamen wird nicht zwischen Groß- und Kleinschreibung unterschieden, wenn Sie in einem Prozess darauf verweisen.

1. Klicken Sie auf Durchsuchen , um die Berechtigung zu suchen, geben Sie das Kennwort der Berechtigung ein und klicken Sie auf OK.

   Wenn die Fehlermeldung &quot;Berechtigung konnte nicht importiert werden aufgrund eines falschen Dateiformats oder eines falschen Kennworts&quot;angezeigt wird, überprüfen Sie, ob das Kennwort gültig ist.

## Berechtigung exportieren {#export-a-credential}

Anmeldeinformationen werden als P12-Dateien im PKCS#12-Format exportiert.

1. Klicken Sie in der Administration-Console auf „Einstellungen“ > „Trust Store-Verwaltung“ > „Lokale Berechtigungen“.
1. Klicken Sie auf den Aliasnamen der Berechtigung, die Sie exportieren möchten, und dann auf &quot;Exportieren&quot;.
1. Geben Sie in das Feld &quot;Kennwort&quot;das Kennwort ein. Dieses Kennwort ist neu und wird zum Verschlüsseln der exportierten Berechtigung verwendet.
1. Klicken Sie auf &quot;Exportieren&quot;, befolgen Sie die Anweisungen zum Exportieren der Berechtigung und klicken Sie auf &quot;OK&quot;.

## Alias- oder Trust Store-Typ einer Berechtigung bearbeiten {#edit-a-credential-s-alias-or-trust-store-type}

Nachdem eine Berechtigung importiert wurde, können Sie den Aliasnamen und den Trust Store-Typ bearbeiten.

1. Klicken Sie in der Administration-Console auf „Einstellungen“ > „Trust Store-Verwaltung“ > „Lokale Berechtigungen“.
1. Klicken Sie auf den Aliasnamen der Berechtigung, die Sie bearbeiten möchten.
1. Klicken Sie auf Berechtigung aktualisieren.
1. Bearbeiten Sie den Aliasnamen und den Trust Store-Typ nach Bedarf und klicken Sie auf &quot;OK&quot;.

## Berechtigung löschen {#delete-a-credential}

1. Klicken Sie in der Administration-Console auf „Einstellungen“ > „Trust Store-Verwaltung“ > „Lokale Berechtigungen“.
1. Aktivieren Sie die Kontrollkästchen der zu löschenden Anmeldeinformationen.
1. Klicken Sie auf Löschen und dann auf OK.
