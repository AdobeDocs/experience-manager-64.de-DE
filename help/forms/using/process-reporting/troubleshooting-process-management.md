---
title: Fehlerbehebung bei Process Reporting
seo-title: Troubleshooting Process Reporting
description: Fehlerbehebung bei Problemen in Process Reporting von AEM Forms on JEE
seo-description: Troubleshoot issues in AEM Forms on JEE Process Reporting
page-status-flag: de-activated
uuid: 1c1cc27c-fbed-4366-bffe-e1581d269a93
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 0a818d19-8804-4c69-b721-31c347c593c0
exl-id: 57ddfead-22bb-4a99-925e-11d71fc61669
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 80%

---

# Fehlerbehebung bei Process Reporting {#troubleshooting-process-reporting}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Probleme beim Erstellen von Filtern in Internet Explorer 9 unter Microsoft Windows 7 {#issues-faced-in-creating-filters-on-internet-explorer-on-microsoft-windows}

Wenn Sie Filter für vordefinierte Berichte erstellen, treten bei **Internet Explorer 9** in einer **Microsoft Windows 7**-Umgebung gelegentlich die folgenden Probleme auf:

* In der Dropdown-Liste im Feld „Wert“ werden eindeutige Kennungen anstelle der Werte angezeigt.
* Das Kalendersteuerelement im Feld „Wert“ zeigt japanische Zeichen an.
* Das Feld „Bedingung“ wird nicht angezeigt.
* Das Kalendersteuerelement im Feld „Wert“ wird nicht angezeigt.

### Auflösung {#resolution}

Tun Sie Folgendes, während Sie noch bei Process Reporting angemeldet sind:

1. Löschen Sie den Browsercache.
1. Aktualisieren Sie das Browser-Fenster.
