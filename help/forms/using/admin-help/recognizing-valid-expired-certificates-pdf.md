---
title: Erkennen von gültigen und abgelaufenen Zertifikaten in PDF-Dokumenten
seo-title: Recognizing valid and expired certificates in PDF documents
description: Erfahren Sie, wie Sie gültige und abgelaufene Zertifikate in PDF-Dokumenten erkennen.
seo-description: Learn how to recognize valid and expired certificates in PDF documents.
uuid: ceeff57a-586f-4f7b-852f-2a637f003d7e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 4559218a-65ba-4577-ad26-7721e28971bc
exl-id: 6e2c109c-381f-455d-bd1d-b08c37c0bd67
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 10%

---

# Erkennen von gültigen und abgelaufenen Zertifikaten in PDF-Dokumenten {#recognizing-valid-and-expired-certificates-in-pdf-documents}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Wenn in Adobe Reader ein PDF-Dokument geöffnet wird, auf das von Reader Extensions Verwendungsrechte angewendet werden, wird eine Statusleiste angezeigt, in der die spezifischen Verwendungsrechte beschrieben werden, die im PDF-Dokument aktiviert sind.

Wenn das digitale Zertifikat, das die Verwendungsrechte für ein PDF-Dokument angibt, abläuft und das PDF-Dokument in Adobe Reader geöffnet wird, wird ein Dialogfeld angezeigt, in dem der Benutzer darauf hingewiesen wird, dass das PDF-Dokument über Verwendungsrechte verfügt, diese Rechte jedoch deaktiviert sind. Obwohl die Meldung darauf hinweist, dass das PDF-Dokument geändert oder manipuliert wurde, ist dies nicht unbedingt der Fall. Adobe Reader zeigt diese Meldung an, wenn ein Zertifikat abläuft oder ein Dokument geändert wird. In Adobe Reader 7.0.x oder höher können Sie nicht ermitteln, welcher Fall derzeit das Problem ist.

Nachdem Sie das Dialogfeld geschlossen haben, öffnet Adobe Reader das PDF-Dokument. Die Verwendungsrechte, die mit Acrobat Reader DC-Erweiterungen angewendet wurden, sind nicht wie erwartet verfügbar. Wenn es sich beim PDF-Dokument um ein interaktives Formular handelt, sind die Formularfelder gesperrt und der Benutzer kann die Formulardaten nicht ändern.
