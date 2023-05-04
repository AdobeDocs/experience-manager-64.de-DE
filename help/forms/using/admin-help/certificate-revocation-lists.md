---
title: Zertifikatsperrlisten verwalten
seo-title: Managing certificate revocationlists
description: Erfahren Sie, wie Sie Zertifikatsperrlisten verwalten.
seo-description: Learn how to manage certificate revocation lists.
uuid: d8c4b64c-a273-4f5d-8b71-f6ea455c0f0a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9744cc2d-5e6b-4341-9270-43d479bdca04
exl-id: 45741270-2d57-4d6d-92ef-65b6c1deb448
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 5%

---

# Zertifikatsperrlisten verwalten{#managing-certificate-revocationlists}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mithilfe der Trust Store-Verwaltung können Sie Zertifikatsperrlisten importieren, bearbeiten und löschen. Base64- und DER-kodierte Zertifikatsperrlisten werden unterstützt.

## Zertifikatsperrliste importieren {#import-a-crl}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;Trust Store-Verwaltung&quot;> &quot;Zertifikatsperrlisten&quot;und dann auf &quot;Importieren&quot;.
1. Geben Sie in das Feld &quot;Alias&quot;eine Kennung für die Zertifikatsperrliste ein.
1. Klicken Sie auf Durchsuchen , um die Zertifikatsperrliste zu suchen, und klicken Sie dann auf OK.

## Zertifikatsperrliste exportieren {#export-a-crl}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;Trust Store-Verwaltung&quot;> &quot;Zertifikatsperrlisten&quot;.
1. Klicken Sie auf den Aliasnamen der zu exportierenden Zertifikatsperrliste und dann auf &quot;Exportieren&quot;.
1. Befolgen Sie die Anweisungen zum Exportieren der Zertifikatsperrliste. Zertifikatsperrlisten werden in der Base64-Kodierung exportiert.
1. Klicken Sie auf OK.

## Zertifikatsperrliste löschen {#delete-a-crl}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;Trust Store-Verwaltung&quot;> &quot;Zertifikatsperrlisten&quot;.
1. Aktivieren Sie die Kontrollkästchen der zu löschenden Zertifikatsperrlisten, klicken Sie auf &quot;Löschen&quot;und anschließend auf &quot;OK&quot;.
