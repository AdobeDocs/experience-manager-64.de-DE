---
title: Verwalten von Zertifikaten
seo-title: Managing certificates
description: Erfahren Sie, wie Sie ein Zertifikat importieren und exportieren und seine Vertrauenseinstellungen bearbeiten.
seo-description: Learn how to import and export a certificate and edit its trust settings.
uuid: 46b1dbe5-517c-4294-bb52-cc6700a768e8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9fd531c0-5206-4be0-a450-13e0dc806068
exl-id: b8d4f35b-dc9c-4e0a-b855-f49275d4ac1f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '677'
ht-degree: 52%

---

# Verwalten von Zertifikaten {#managing-certificates}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mithilfe der Trust Store-Verwaltung können Sie Zertifikate importieren, bearbeiten und löschen, die Sie auf dem Server für die Validierung digitaler Signaturen und die Zertifikatauthentifizierung als vertrauenswürdig betrachten. Sie können eine beliebige Anzahl von Zertifikaten importieren und exportieren. Nachdem ein Zertifikat importiert wurde, können Sie die Vertrauenseinstellungen und den Trust Store-Typ bearbeiten. Beachten Sie beim Kombinieren von Trust Store-Typen die folgenden Optionen:

* **Trust für Zertifikatauthentifizierung mit CA:** Wählen Sie für die Prüfung der Zertifikatsperrliste auch die Option „Trust für Identität“.
* **Trust für Zertifikatauthentifizierung mit ICA:** Wählen Sie nur die Option „Trust für Identität“. Eine ICA sollte für die Zertifikatauthentifizierung nicht als vertrauenswürdig eingestuft werden. Wenn Sie der ICA für die Zertifikatauthentifizierung vertrauen, wird die ICA zur Zertifizierungsstelle für die Pfaderstellung. Wenn die ICA sowohl für die Zertifikatauthentifizierung als auch für die Identität als vertrauenswürdig eingestuft wird, wird das Zertifizierungsstellenzertifikat ignoriert, da die ICA zur Zertifizierungsstelle wird.
* **Trust für Online-Zertifikatstatusprotokoll-Server (OCSP) mit HTTPs:** Wenn sich der beim OCSP-Responder anfragende Server an einem HTTPs-Speicherort befindet, müssen Sie auch „Trust für SSL-Verbindungen“ auswählen. Ist für die bei OCSP anfragende Partei die Prüfung der Zertifikatsperrliste erforderlich, muss darüber hinaus „Trust für Identität“ ausgewählt werden.
* **Adobe-Stammzertifikat:** Wählen Sie nicht die Trust Store-Typen für SSL-Verbindungen und OCSP-Server. Adobe Root wird für SSL-Verbindungen und OCSP-Server nicht als vertrauenswürdig eingestuft. Adobe stellt keine OCSP- und SSL-Zertifikate aus. Adobe Root wird implizit mit einem Alias name=&quot;ADOBEROOT&quot; als vertrauenswürdig eingestuft.

Es werden nur X509v3-Zertifikate unterstützt. Dieser Zertifikatstyp kann in einer binären DER-kodierten Datei (.cer-Datei) oder einer Textdatei bereitgestellt werden, die eine Base64-kodierte Version desselben DER-kodierten Zertifikats enthält (einschließlich X509-Zertifikaten im PEM-Format (Privacy Enhanced Mail)).

Zertifikate, die zum Durchführen einer Signaturüberprüfung erforderlich sind, müssen sich im selben Speicher (HSM oder Datenbank) befinden.

Sie können Zertifikate auch mithilfe der Trust Manager-API importieren und löschen. Weitere Informationen finden Sie unter &quot;Importieren von Zertifikaten mit der Trust Manager-API&quot;und unter &quot;Löschen von Zertifikaten mit der Trust Manager-API&quot;in [Programmieren mit AEM Formularen](https://www.adobe.com/go/learn_aemforms_programming_63_de).

## Importieren eines Zertifikats {#import-a-certificate}

1. Klicken Sie in Administration Console auf **[!UICONTROL Einstellungen > Trust Store-Verwaltung > Zertifikate]**.
1. Klicken Sie auf „Importieren“ und wählen Sie unter „Trust Store-Typ“ eine der folgenden Optionen:

   * **Trust für SSL-Verbindungen:** Gibt an, dass AEM Forms Zertifikate verwenden kann, um über SSL Verbindungen zu externen Systemen herzustellen.
   * **Trust für Signaturzertifizierung:** Gibt an, dass Zertifikaten bei Dokumentsignierungsvorgängen für die Zertifizierung autorbezogener digitaler Signaturen vertraut wird.
   * **Trust für Signatur:** Gibt an, dass Zertifikaten bei Dokumentsignierungsvorgängen für die Zertifizierung nicht autorbezogener digitaler Signaturen vertraut wird.
   * **Trust für Zertifikatauthentifizierung:** Gibt an, dass AEM Forms Zertifikate zum Authentifizieren von Benutzern mit Zertifikat- oder Smartcard-Authentifizierung verwendet.
   * **Trust für Online-Zertifikatstatusprotokoll-Server (OCSP):** Gibt an, dass AEM Forms Zertifikate verwenden kann, um Verbindungen zu externen OCSP-Respondern herzustellen.
   * **Trust für Identität:** Dieser Trust Store-Typ gibt an, dass Zertifikate verwendet werden können, um von den zuvor genannten Typen abweichenden Informationen zu vertrauen.

   >[!NOTE]
   >
   >Der Trust Store vertraut implizit einem Adobe-Stammzertifikat für Zertifikatauthentifizierung, -signatur, -zertifizierung und -identität.

1. Geben Sie in das Feld &quot;Alias&quot;die Kennung für das Zertifikat ein.
1. Klicken Sie auf **[!UICONTROL Durchsuchen]**, um das Zertifikat zu finden, und anschließend auf **[!UICONTROL OK]**.

## Zertifikat exportieren {#export-a-certificate}

1. Klicken Sie in Administration Console auf **[!UICONTROL Einstellungen > Trust Store-Verwaltung > Zertifikate]**.
1. Klicken Sie auf den Aliasnamen des Zertifikats, das exportiert werden soll. Die Seite **[!UICONTROL Zertifikatdetails]** wird angezeigt.
1. Klicken Sie auf **[!UICONTROL Exportieren]**, befolgen Sie die Anweisungen zum Exportieren des Zertifikats und klicken Sie anschließend auf **[!UICONTROL OK]**.

## Trust-Einstellungen und Trust Store-Typ eines Zertifikats bearbeiten {#edit-a-certificate-s-trust-settings-and-trust-store-type}

1. Klicken Sie in Administration Console auf **[!UICONTROL Einstellungen > Trust Store-Verwaltung > Zertifikate]**.
1. Klicken Sie auf den Aliasnamen des Zertifikats, das bearbeitet werden soll.
1. Klicken Sie auf **[!UICONTROL Zertifikat aktualisieren]**.
1. Um den Alias-Namen des Zertifikats zu ändern, geben Sie einen neuen Namen in das Feld &quot;Alias&quot;ein.
1. Um den Trust Store-Typ für das Zertifikat zu aktualisieren, wählen Sie den entsprechenden Trust Store-Typ aus.
1. Um die Richtlinienbeschränkungen zu aktualisieren, geben Sie die Richtlinieninformationen in das Feld „Zertifikatrichtlinien“ ein und klicken Sie auf **[!UICONTROL OK]**.

## Zertifikat löschen {#delete-a-certificate}

1. Klicken Sie in Administration Console auf **[!UICONTROL Einstellungen > Trust Store-Verwaltung > Berechtigungen]**.
1. Aktivieren Sie die Kontrollkästchen der zu löschenden Zertifikate und klicken Sie erst auf **[!UICONTROL Löschen]** und anschließend auf **[!UICONTROL OK]**.
