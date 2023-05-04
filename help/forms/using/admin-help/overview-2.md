---
title: Grundlagen zum Verwalten von Zertifikaten und Anmeldeinformationen
seo-title: Basics of managing certificates and credentials
description: Erfahren Sie mehr über die Grundlagen der Verwaltung von Zertifikaten und Berechtigungen.
seo-description: Learn about the basics of managing certificates and credentials.
uuid: f421e206-e7b5-416c-b9fb-974094f10a66
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 986d16fc-4c81-4785-b1f3-fe8bd7ff669e
exl-id: 4817d150-9bfe-4cb9-8f06-6ff4eaaa6f55
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 21%

---

# Grundlagen zum Verwalten von Zertifikaten und Anmeldeinformationen {#basics-of-managing-certificates-and-credentials}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

A *credential* enthält Ihre Informationen zum privaten Schlüssel, die zum Signieren oder Identifizieren von Dokumenten benötigt werden. A *certificate* ist eine Information mit öffentlichem Schlüssel, die Sie für das Vertrauen konfigurieren. AEM Formulare verwenden Zertifikate und Berechtigungen für verschiedene Zwecke:

* Acrobat Reader DC Extensions verwendet Anmeldeinformationen zur Aktivierung von Adobe Reader-Verwendungsrechten in PDF-Dokumenten. (Siehe [Konfigurieren von Berechtigungen für die Verwendung mit Acrobat Reader DC Extensions](/help/forms/using/admin-help/configuring-credentials-acrobat-reader-dc.md#configuring-credentials-for-use-with-acrobat-reader-dc-extensions).
* Sie können Rights Management so konfigurieren, dass nur vertrauenswürdige Emittenten Anmeldeinformationen zur Verwendung in Acrobat anzeigen. (Siehe [Anzeigeeinstellungen für Rights Management konfigurieren](/help/forms/using/admin-help/configuring-client-server-options.md#configure-document-security-display-settings). Der Gemeinsame Name (CN) muss im Zertifikat vorhanden sein.
* Der Signature-Dienst greift auf Zertifikate und Berechtigungen zu. Weitere Informationen zum Signature-Dienst finden Sie unter [Dienstreferenz](https://www.adobe.com/go/learn_aemforms_services_63).

**Generieren eines Schlüsselpaars**

AEM Forms verwendet seinen Trust Store zum Speichern und Verwalten von Zertifikaten, Berechtigungen und Zertifikatsperrlisten (CRLs). Darüber hinaus können Sie ein unabhängiges HSM-Gerät (Hardware Security Module) verwenden, um private Schlüssel zu speichern.

AEM Formulare bieten keine Option zum Generieren eines Schlüsselpaars. Sie können sie jedoch mit Tools wie Java-Keytool generieren und in AEM Trust Store von Forms importieren. Weitere Informationen zum Java-Keytool finden Sie unter folgenden Themen:

[https://docs.oracle.com/javase/tutorial/security/toolsign/step3.html](https://docs.oracle.com/javase/tutorial/security/toolsign/step3.html)

[https://docs.oracle.com/cd/E19798-01/821-1841/gjrgy/index.html](https://docs.oracle.com/cd/E19798-01/821-1841/gjrgy/index.html)

[https://helpcenter.gsx.com/hc/en-us/articles/115015960428-How-to-Generate-a-Self-Signed-Certificate-and-Private-Key-using-OpenSSL](https://helpcenter.gsx.com/hc/en-us/articles/115015960428-How-to-Generate-a-Self-Signed-Certificate-and-Private-Key-using-OpenSSL)

Die folgenden Signaturtypen werden unterstützt und können in AEM Formulare importiert werden:

* XML-Signatur
* XMLTimeStampToken
* RFC 3161 TimeStampToken
* PKCS#7
* PKCS#1
* DSA Signatures

**Umgang mit verlorenem oder beschädigtem Schlüssel**

Wenn Sie vermuten, dass Ihr Schlüssel verloren geht oder beschädigt wurde, führen Sie die folgenden Schritte aus:

1. Informieren Sie die Zertifizierungsstelle, damit der beschädigte Schlüssel zur Zertifikatsperrliste hinzugefügt wird, um den Schlüssel zu widerrufen.
1. Rufen Sie einen neuen Schlüssel und die zugehörigen Zertifikate von der Zertifizierungsstelle ab.
1. Unterschreiben Sie die unterschriebenen Dokumente mit dem beschädigten Schlüssel erneut mithilfe des neuen Schlüssels.
