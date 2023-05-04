---
title: Aktualisieren des Lizenztyps für die Bereitstellung
seo-title: Update the license type for the deployment
description: Aktualisieren Sie den Lizenztyp für die Bereitstellung mithilfe der Seite Lizenz ändern in Administration Console.
seo-description: Update the license type for the deployment by using the Change License page in administration console.
uuid: 0152635e-2c00-4944-b9b6-64b368589a91
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/get_started_with_administering_aem_forms_on_jee
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e4f31377-ccc9-4986-a3bf-ef2e83d12448
exl-id: 07671470-59dd-4290-be9a-465fcd89ac2d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 16%

---

# Aktualisieren des Lizenztyps für die Bereitstellung {#update-the-license-type-for-the-deployment}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Als Teil des Installationsprozesses von AEM Forms haben Sie mithilfe von Configuration Manager die erforderlichen AEM Forms-Module konfiguriert und bereitgestellt. Standardmäßig sind diese Module mit einer Testlizenz für 60 Tage konfiguriert. Auf der Seite &quot;Lizenz ändern&quot;in Administration Console können Sie den Lizenztyp für die Bereitstellung ändern. Die derzeit bereitgestellten Module werden auf der Seite Lizenz ändern angezeigt.

Auf der Seite Lizenz ändern werden Informationen zu Ihrer Lizenz angezeigt:

* Der aktuelle Lizenztyp
* Datum und Uhrzeit der letzten Aktualisierung der Lizenz
* Wer das letzte Update durchgeführt hat
* Der aktuelle Status der Lizenz
* Das Datum, an dem AEM Formulare installiert wurden
* Das Datum, an dem die aktuelle Lizenz abläuft

>[!NOTE]
>
>Die Lizenzänderung gilt für alle bereitgestellten Module. Bevor Sie den Lizenztyp ändern, heben Sie die Bereitstellung aller Module auf, die nicht lizenziert sind. Wählen Sie nicht den Lizenztyp Produktion aus, wenn die Liste der bereitgestellten Module andere Module enthält als die, die Sie von Adobe erworben haben.

## Lizenztyp aktualisieren {#update-the-license-type}

1. Klicken Sie in Administration Console auf &quot;Lizenzierung&quot;.
1. Lesen Sie die Lizenzvereinbarung für Endbenutzer in AEM Formularen, wählen Sie Ich akzeptiere , wenn Sie mit den Bedingungen der Vereinbarung einverstanden sind, und klicken Sie auf Weiter.
1. Wählen Sie auf der Seite Lizenz ändern einen Lizenztyp aus:

   * **EVAL:** Testlizenz für 60 Tage
   * **DEV:** Permanente Entwicklungslizenz
   * **NFR:** 2-Jahres-Evaluierungslizenz
   * **IDEV:** 1-Jahres-Abo für das Adobe Developer-Programm
   * **Production:** Permanente Lizenz

1. Wählen Sie Ja, Lizenzänderung ist für alle bereitgestellten Module gültig.
1. Klicken Sie auf Lizenzänderung bestätigen . Es wird eine Meldung angezeigt, die besagt, dass die Lizenz erfolgreich aktualisiert wurde.
