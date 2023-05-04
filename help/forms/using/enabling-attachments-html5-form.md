---
title: Aktivieren von Anlagen für ein HTML5-Formular
seo-title: Enabling attachments for an HTML5 form
description: Standardmäßig ist die Anlagenunterstützung für HTML5-Formulare deaktiviert.
seo-description: By default, the attachment support for HTML5 forms is disabled.
uuid: 2c62ac3e-4b27-46c7-a61d-a805fb5d26fb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 8eebfcd6-0597-44ed-b718-bf9a1baa6c12
feature: Mobile Forms
exl-id: 82a843c4-5cb2-4f5e-ad4d-cf2e9ea6cdb8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 42%

---

# Aktivieren von Anlagen für ein HTML5-Formular {#enabling-attachments-for-an-html-form}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können Anhänge mit HTML5-Formularen hochladen, in der Vorschau anzeigen und senden. Standardmäßig ist die Unterstützung für Anlagen deaktiviert. Gehen Sie wie folgt vor, um die Unterstützung der Anlage zu aktivieren:

1. Erstellen Sie eine [Benutzerdefiniertes Profil](/help/forms/using/custom-profile.md) mit der String-Eigenschaft &quot;mutiselect&quot; `mfAttachmentOptions`.
1. Geben Sie im benutzerdefinierten Profil Eigenschaften an `fileSizeLimit`, `multiSelect`und `buttonTex`um Optionen des Dateianhang-Widgets zu konfigurieren. Bei Bedarf können Sie auch weitere benutzerdefinierte Eigenschaften angeben.

1. Verwenden Sie im benutzerdefinierten Profil die folgenden Konfigurationen:

   * **multiSelect** -> true oder false (standardmäßig true)
   * **fileSizeLimit** -> value_in_mb (z. B. 5) (standardmäßig 2 MB)
   * **buttonText** -> Schaltflächentext für Popup-Fenster (standardmäßig &quot;Anhängen&quot;)
   * **accept** -> zu akzeptierende Dateitypen (&quot;audio/&amp;ast;, video/&amp;ast;, image/&amp;ast;, text/&amp;ast;, .pdf&quot; standardmäßig)

   >[!NOTE]
   >
   >In Microsoft Internet Explorer 9 können Benutzer Dateien anhängen, die größer als die angegebene Grenze sind. Es ist ein bekanntes Problem.

1. Verwenden Sie den [Metadaten-Editor](/help/forms/using/manage-form-metadata.md), um das benutzerdefinierte Profil auszuwählen, das Sie oben für HTML-5-Formulare erstellt haben.
1. Rendern Sie die Formularvorlage mit dem benutzerdefinierten Profil und das Anlagensymbol wird in der Symbolleiste &quot;Formulare&quot;angezeigt.

   >[!NOTE]
   >
   >Standardmäßig bietet das Forms Portal ein benutzerdefiniertes Profil mit aktivierten Funktionen für Entwürfe und Anlagen. Weitere Informationen zum Profil **Als Entwurf speichern** finden Sie unter [HTML5 Forms als Entwurf speichern](/help/forms/using/saving-html5-form-draft.md).

1. Klicken Sie auf das Anlagensymbol. Es wird ein Dialogfeld zur Anlagenauswahl angezeigt. Suchen Sie nach der Anlage, wählen Sie sie aus und klicken Sie auf **Anhängen**.

   >[!NOTE]
   >
   >Klicken Sie zum Anzeigen einer Anlage in der Vorschau auf den Anlagennamen.

   >[!NOTE]
   >
   >Die Option „Dateivorschau“ ist nicht für anonyme Benutzer verfügbar.

## Format der Anlagenübermittlung {#attachment-submission-format}

Wenn Anlagen aktiviert sind, sendet das HTML5-Formular mehrteilige Daten. Die mehrteiligen Übermittlungsdaten bestehen aus zwei Teilen **dataXml** und **Anhängen**.

>[!NOTE]
>
>Wenn die Option `mfAllowAttachments` deaktiviert ist, senden die HTML5-Formulare aus Gründen der Abwärtskompatibilität keine mehrteiligen Daten. Es sendet einfache Daten-XML im Format **application/xml**.

Wenn das Flag „mfAllowAttachments“ aktiviert ist, werden die mehrteiligen Daten vom [Sendedienst Proxydienst](/help/forms/using/service-proxy.md) mit dataXml und Anlagen gesendet.
