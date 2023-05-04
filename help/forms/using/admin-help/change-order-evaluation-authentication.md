---
title: Ändern der Reihenfolge der Auswertung für die Authentifizierung
seo-title: Change the order of evaluation for authentication
description: Sie können die Reihenfolge ändern, in der AEM Formulare mehrere Authentifizierungsanbieter auswertet.
seo-description: You can change the order in which AEM forms evaluates multiple authentication providers.
uuid: c2693e5b-cf09-4bb8-815a-2b20ebf6eea0
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 5434df9c-ecf6-450a-aa7e-d9ab69b66fe6
exl-id: cac16c50-a85d-4e40-a590-8a0a52be893c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 52%

---

# Ändern der Reihenfolge der Auswertung für die Authentifizierung {#change-the-order-of-evaluation-for-authentication}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Wenn Sie mehrere Authentifizierungsanbieter konfiguriert haben, können Sie die Reihenfolge ändern, in der AEM Formulare sie zur Authentifizierung auswertet. Die Reihenfolge der Authentifizierungsanbieter, die in der Datei config.xml aufgeführt sind, bestimmt die Reihenfolge der Auswertung für die Authentifizierung.

1. Klicken Sie in der Administration-Console auf „Einstellungen“ > „Benutzerverwaltung“ > „Konfiguration“ > „Konfigurationsdateien importieren und exportieren“.
1. Um die aktuellen Konfigurationseinstellungen in eine Datei zu exportieren, klicken Sie auf „Exportieren“ und speichern Sie die Konfigurationsdatei an einem anderen Speicherort.
1. Suchen Sie den folgenden Knoten in der Datei:

   ```as3
    <node name="AuthSchemes"> 
        <map />  
            <node name="CertificateAuth"> 
                <map> 
                    <entry key="order" value="3" />  
                    <entry key="name" value="edc.server.auth.scheme.certificate" />  
                </map> 
        </node> 
        <node name="Kerberos"> 
            <map> 
                <entry key="kerberosSPN" value="defaultSPN" />  
                <entry key="order" value="1" />  
                <entry key="name" value="edc.server.auth.scheme.kerberos" />  
            </map> 
    </node>
   ```

   Bearbeiten Sie unter `<entry key="order" value="3" />` den Wert für jeden Knoten, um die Reihenfolge der Authentifizierungsbewertung festzulegen.

1. Um die aktualisierte Datei zu importieren, klicken Sie in „Benutzerverwaltung“ auf „Konfiguration“ > „Konfigurationsdateien importieren und exportieren“.
1. Klicken Sie auf „Durchsuchen“, um die Datei zu suchen, dann auf „Importieren“ und anschließend auf „OK“.
