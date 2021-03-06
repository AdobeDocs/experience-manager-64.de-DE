---
title: Aktivieren von Anlagen für ein HTML5-Formular
seo-title: Enabling attachments for an HTML5 form
description: Standardmäßig ist die Unterstützung der Anlage für HTML5-Formulare deaktiviert.
seo-description: By default, the attachment support for HTML5 forms is disabled.
uuid: 2c62ac3e-4b27-46c7-a61d-a805fb5d26fb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 8eebfcd6-0597-44ed-b718-bf9a1baa6c12
feature: Mobile Forms
exl-id: 82a843c4-5cb2-4f5e-ad4d-cf2e9ea6cdb8
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 78%

---

# Aktivieren von Anlagen für ein HTML5-Formular {#enabling-attachments-for-an-html-form}

Sie können Anlagen mit HTML5-Formularen hochladen, anzeigen und senden. Standardmäßig ist die Unterstützung der Anlage deaktiviert. Gehen Sie wie folgt vor, um die Unterstützung der Anlage zu aktivieren:

1. Erstellen Sie ein [benutzerdefiniertes Profil](/help/forms/using/custom-profile.md) mit der Eigenschaft Mehrfachauswahlzeichenfolge`mfAttachmentOptions` .
1. Geben Sie im benutzerdefinierten Profil Eigenschaften an `fileSizeLimit`, `multiSelect`und `buttonTex`um Optionen des Dateianhang-Widgets zu konfigurieren. Bei Bedarf können Sie auch weitere benutzerdefinierte Eigenschaften angeben.

1. Verwenden Sie im benutzerdefinierten Profil die folgenden Konfigurationen:

   * **multiSelect** -> „true“ oder „false“ (true standardmäßig ausgewählt)
   * **fileSizeLimit** -> value_in_mb (z. B. 5) (standardmäßig 2 MB)
   * **buttonText** -> Schaltflächentext für Popup-Fenster (standardmäßig &quot;Anhängen&quot;)
   * **accept** -> zu akzeptierende Dateitypen (&quot;audio/&amp;ast;, video/&amp;ast;, image/&amp;ast;, text/&amp;ast;, .pdf&quot; standardmäßig)

   >[!NOTE]
   >
   >In Microsoft Internet Explorer 9 können Benutzer Dateien anfügen, die größer sind, als der angegebene Grenzwert. Hierbei handelt es sich um ein bekanntes Problem.

1. Verwenden Sie den [Metadaten-Editor](/help/forms/using/manage-form-metadata.md), um das benutzerdefinierte Profil auszuwählen, das Sie oben für HTML-5-Formulare erstellt haben.
1. Sie können die Formularvorlage mit dem benutzerdefinierten Profil wiedergeben und das Anlagensymbol würde in der Symbolleiste „Formulare“ angezeigt.

   >[!NOTE]
   >
   >Standardmäßig bietet das Forms Portal ein benutzerdefiniertes Profil mit einer aktivierten Entwurfs- und Anlagenfunktion. Weitere Informationen zum Profil **Als Entwurf speichern** finden Sie unter [HTML5 Forms als Entwurf speichern](/help/forms/using/saving-html5-form-draft.md).

1. Klicken Sie auf das Anlagensymbol. Es wird ein Dialogfeld zur Anlagenauswahl angezeigt. Suchen Sie nach der Anlage, wählen Sie sie aus und klicken Sie auf **Anhängen**.

   >[!NOTE]
   >
   >Klicken Sie zum Anzeigen einer Anlage in der Vorschau auf den Anlagennamen.

   >[!NOTE]
   >
   >Die Option „Dateivorschau“ ist nicht für anonyme Benutzer verfügbar.

## Format der Anlage bei Einsendung {#attachment-submission-format}

Wenn Anlagen aktiviert sind, sendet das HTML5-Formular mehrteilige Daten. Die mehrteiligen Übermittlungsdaten bestehen aus zwei Teilen **dataXml** und **Anhängen**.

>[!NOTE]
>
>Wenn die Option `mfAllowAttachments` deaktiviert ist, senden die HTML5-Formulare aus Gründen der Abwärtskompatibilität keine mehrteiligen Daten. Es sendet einfache Daten-XML im Format **application/xml**.

Wenn das Flag „mfAllowAttachments“ aktiviert ist, werden die mehrteiligen Daten vom [Sendedienst Proxydienst](/help/forms/using/service-proxy.md) mit dataXml und Anlagen gesendet.
