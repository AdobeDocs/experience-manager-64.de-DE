---
title: Schwellenwert für die Anzahl maximal geöffneter Cursor für Oracle-Datenbank
seo-title: Oracle database maximum open cursors threshold
description: Erfahren Sie, wie Sie einen Maximalwert für geöffnete Cursor in Oracle konfigurieren.
seo-description: Learn about configuring a maximum value for open cursors in Oracle.
uuid: c1d20997-f853-4772-b1c6-8cea73221d0a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d3565776-1b7d-498c-9840-b17f80170d9b
exl-id: ad14ff27-964f-481f-a8ef-052d9cfb7734
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 25%

---

# Schwellenwert für die Anzahl maximal geöffneter Cursor für Oracle-Datenbank {#oracle-database-maximum-open-cursors-threshold}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Um einen Maximalwert für geöffnete Cursor in Oracle zu konfigurieren, müssen Sie diesen Wert möglicherweise auf eine Zahl einstellen, die für Ihre Anwendung geeignet ist. Es ist offensichtlich, dass unter moderater Belastung die durchschnittlich geöffneten Cursor 2700 waren. Es wird empfohlen, mit einer Obergrenze von 3000 zu beginnen. Weitere Informationen finden Sie unter [https://www.orafaq.com/node/758](https://www.orafaq.com/node/758).
