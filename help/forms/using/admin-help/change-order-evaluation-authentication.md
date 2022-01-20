---
title: Die Reihenfolge der Auswertung für die Authentifizierung ändern
seo-title: Change the order of evaluation for authentication
description: 'Sie können die Reihenfolge ändern, in der AEM Forms mehrere Anbieter zur Authentifizierung auswertet. '
seo-description: You can change the order in which AEM forms evaluates multiple authentication providers.
uuid: c2693e5b-cf09-4bb8-815a-2b20ebf6eea0
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 5434df9c-ecf6-450a-aa7e-d9ab69b66fe6
exl-id: cac16c50-a85d-4e40-a590-8a0a52be893c
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 89%

---

# Die Reihenfolge der Auswertung für die Authentifizierung ändern {#change-the-order-of-evaluation-for-authentication}

Wenn Sie mehrere Authentifizierungsanbieter konfiguriert haben, können Sie die Reihenfolge ändern, in der AEM Forms diese Anbieter zur Authentifizierung auswertet. Die Reihenfolge, in der die Authentifizierungsanbieter in der Datei „config.xml“ aufgelistet werden, bestimmt die Reihenfolge der Auswertung für die Authentifizierung.

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Konfiguration“ > „Konfigurationsdateien importieren und exportieren“.
1. Um die aktuellen Konfigurationseinstellungen in eine Datei zu exportieren, klicken Sie auf „Exportieren“ und speichern die Konfigurationsdatei an einem anderen Speicherort.
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

   In `<entry key="order" value="3" />`bearbeiten Sie den Wert für jeden Knoten, um die Reihenfolge der Authentifizierungsauswertung festzulegen.

1. Um die aktualisierte Datei zu importieren, klicken Sie in User Management auf „Konfiguration“ > „Konfigurationsdateien im- und exportieren“.
1. Klicken Sie auf „Durchsuchen“, um die Datei zu suchen, klicken Sie dann auf „Importieren“ und anschließend auf „OK“.
