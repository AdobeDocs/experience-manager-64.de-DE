---
title: Überblick über die Konfiguration von SSL
seo-title: Overview of configuring SSL
description: Erfahren Sie, wie Sie die Kommunikationssicherheit durch die Konfiguration von SSL verbessern können.
seo-description: Learn about how to enhance security of communication by configuring SSL.
uuid: 3e99d2bf-137b-45ba-8384-309624094623
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 8e107abb-861f-4063-b600-c87e34639019
exl-id: 5dc68401-f6bc-42cb-84db-1db805b045c5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 6%

---

# Überblick über die Konfiguration von SSL {#overview-of-configuring-ssl}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können SSL-Anmeldedaten (Secure Sockets Layer) erstellen und SSL auf dem Anwendungsserver konfigurieren, um die Sicherheit der Kommunikation mit Ihrem Anwendungsserver zu erhöhen.

Als Sicherheitsprodukt erfordert Rights Management die Konfiguration von SSL. Stellen Sie beim Konfigurieren von SSL-Zertifikaten sicher, dass Sie nur RSA-Schlüssel verwenden. SSL-Zertifikate mit DSA-Schlüsseln werden nicht unterstützt.

Die bereitgestellten Informationen gelten für Turnkey-, Automatisch- und manuelle Installationen. Es bietet ein Beispiel für eine Methode zur Konfiguration von SSL. Sie können auch andere Methoden verwenden, die für Ihr Netzwerk oder Ihre Organisation besser geeignet sind.

>[!NOTE]
>
>Es wird empfohlen, die Installation, Konfiguration und Bereitstellung Ihrer AEM Formularmodule abzuschließen und sicherzustellen, dass die Produkte ordnungsgemäß ausgeführt werden, bevor Sie SSL auf dem Anwendungsserver konfigurieren.

>[!NOTE]
>
>Verwenden Sie beim Erstellen von SSL-Sicherheitszertifikaten und -berechtigungen dieselben Benutzerkontoberechtigungen wie beim Ausführen des Anwendungsservers. Wenn der Anwendungsserver mit anderen Benutzerberechtigungen ausgeführt wird, wird das Formular für PDFForm-Ausgabeformate möglicherweise nicht ordnungsgemäß wiedergegeben, wenn der ContentRootURI auf HTTPS verweist.

Wenn Sie über einen SSL-aktivierten LDAP-Server verfügen, konfigurieren Sie User Management für die Verwendung mit diesem Server. (Siehe [User Management für einen SSL-aktivierten LDAP-Server konfigurieren](/help/forms/using/admin-help/configure-user-management-ssl-enabled.md#configure-user-management-for-an-ssl-enabled-ldap-server).
