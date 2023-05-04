---
title: Konfigurieren von AEM Formularen für Vorabrufdomäneninformationen
seo-title: Configure AEM forms to prefetchdomain information
description: Konfigurieren Sie AEM Forms, um Domain-Informationen zuvor abzurufen, wenn es zu einer langsameren Reaktionszeit kommt, aufgrund der tief verschachtelten Gruppen oder wenn Sie ein Mitglied mehrerer Gruppen sind.
seo-description: Configure AEM forms to prefetch domain information if you experience a slower response time due to deeply nested groups or if you are a member of many groups.
uuid: 53c8995e-3f9d-42e8-9f75-cee7debe6ce1
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: f9a3f897-90c6-4942-8a86-aae510298f2a
exl-id: 6b431cbd-2cea-4ae2-ad26-587ba524d2f5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 58%

---

# Konfigurieren von AEM Formularen für Vorabrufdomäneninformationen {#configure-aem-forms-to-prefetchdomain-information}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Für Benutzer kann es zu einer langsameren Reaktionszeit kommen, wenn sie vielen Gruppen angehören (z. B. 500 oder mehr) oder wenn die Gruppen tief verschachtelt sind (z. B. 30 Ebenen). Wenn dieses Problem auftritt, können Sie AEM Forms so konfigurieren, dass Informationen aus bestimmten Domains vorher abgerufen werden.

1. Klicken Sie in Administration Console auf **[!UICONTROL Einstellungen > Benutzerverwaltung > Konfiguration > Konfigurationsdateien importieren und exportieren]**.
1. Um die aktuellen Konfigurationseinstellungen in eine Datei zu exportieren, klicken Sie auf **[!UICONTROL Exportieren]** und speichern die Konfigurationsdatei an einem anderen Speicherort.
1. Fügen Sie den folgenden Knoten hinzu (fettgedruckt markiert):

   ```as3
    <node name="UM"> 
    <map/>  
    <node name="PrincipalCache"> 
        <map> 
            <entry key="principalCacheSize" value="1000"/> 
            <entry key="principalCacheBatchFetchSize" value="10"/> 
            <entry key="rebuildCacheAfterSync" value="true /> 
            <entry key="enableFullPrefetch" value="false"/> 
            <entry key="principalCacheDomains" value="Domain_Name1/Domain_Name2/Domain_Name3"/> 
        <map> 
    </node> 
    <node name="APSAuditService">
   ```

   In diesem Beispiel werden mehrere Domains zum vorherigen Abrufen konfiguriert. Die Domain-Namen werden durch ein „/“ getrennt. Dies wird im obigen Beispiel mit *Domäne_Name1*, *Domain_Name2* und *Domain_Name3*.

1. Um die aktualisierte Datei zu importieren, klicken Sie in „Benutzerverwaltung“ auf **[!UICONTROL Konfiguration > Konfigurationsdateien im- und exportieren]**.
1. Klicken Sie auf **[!UICONTROL Durchsuchen]**, um die Datei zu suchen, klicken Sie dann auf „Importieren“ und anschließend auf **[!UICONTROL OK]**.
