---
title: Festlegen der Internationalisierungsoptionen
seo-title: Setting internationalization options
description: Erfahren Sie, wie Sie das Gebietsschema angeben, das zum Rendern von Formularen verwendet wird, und wie Sie den Zeichensatz angeben, der zum Kodieren des Ausgabestreams verwendet wird.
seo-description: Learn how to specify the locale used to render forms and how to specify the character set used to encode the output stream.
uuid: bb77f5f3-634f-4285-9b10-c4dd40085e69
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e845d13f-bef2-442d-af9a-4f92d7616a46
exl-id: 1fb51e4a-e0e8-4a58-8877-98337fe29fac
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 31%

---

# Festlegen der Internationalisierungsoptionen{#setting-internationalization-options}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Festlegen des Gebietsschemas zum Rendern von Formularen {#specify-the-locale-used-to-render-forms}

Sie können das Gebietsschema angeben, das beim Rendern eines PDF-Formulars verwendet wird. Die Felder in einem PDF-Formular verwenden das angegebene Gebietsschema, um Daten anzuzeigen. Wenn das Gebietsschema beispielsweise auf Deutsch festgelegt ist, verwendet das Formular deutsche Dezimaltrennzeichen für numerische Werte. Das Gebietsschema wird auch zum Senden von Validierungsmeldungen an Clientgeräte wie Webbrowser im Rahmen von HTML-Transformationen verwendet.

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Formulare“.
1. Wählen Sie unter &quot;Internationalisierung&quot;in der Liste &quot;Sprache&quot;das Gebietsschema aus, das zum Rendern eines Formulars verwendet wird. Der Standardwert ist Englisch (USA).
1. Klicken Sie auf Speichern.

## Geben Sie den Zeichensatz an, der zum Kodieren des Ausgabe-Streams verwendet wird {#specify-the-character-set-used-to-encode-the-output-stream}

1. Wählen Sie unter „Internationalisierung“ in der Liste „Zeichensatz“ einen Zeichensatz aus. Diese Einstellung hängt von der verwendeten API ab, entweder renderHTMLForm oder renderPDFForm. Um einen anderen Zeichensatz als die aufgelisteten anzugeben, wählen Sie „Benutzerdefiniert“ aus und geben Sie in dem angezeigten Feld einen Codierungswert ein.

   Bei HTML-Transformationen unterstützt AEM Forms Zeichenkodierungswerte, die vom Paket `java.nio.charset` definiert werden. Wenn sFormPreference auf PDFForm festgelegt ist, werden nur bestimmte Zeichensätze unterstützt. Der Zeichensatz muss ein gültiger kanonischer Name sein. Der Standardwert ist ISO-8859-1.

1. Klicken Sie auf Speichern.
