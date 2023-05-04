---
title: Konfigurieren des LDAP-Bindungskennworts
seo-title: Configure the LDAP bind password
description: Erfahren Sie, wie Sie das Feld für das Bindungskennwort konfigurieren, bevor Sie die Konfigurationsdatei in ein anderes System importieren.
seo-description: Learn how to configure the bind password field before you import the configuration file into another system.
uuid: 1ab1907c-8b55-4b6f-bd5b-49f22d78b8a8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 165b3950-b03f-4848-8361-ffb0a26d2658
exl-id: eaa2c889-d116-4209-9063-0c0b32dd8849
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 54%

---

# Konfigurieren des LDAP-Bindungskennworts{#configure-the-ldap-bind-password}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Um Sicherheitsrisiken zu vermeiden, ist das Feld für das Bindungskennwort in der exportierten Konfigurationsdatei (config.xml) nicht konfiguriert. Bevor Sie die Konfigurationsdatei in ein anderes System importieren, müssen Sie dieses Kennwort konfigurieren. Dieses Kennwort setzt ein vorhandenes Kennwort außer Kraft, das in der Datenbank gespeichert ist. Ein Null-Kennwort überschreibt keinen vorhandenen Kennwortwert, der nicht null ist.

1. Klicken Sie in der Administration-Console auf „Einstellungen“ > „Benutzerverwaltung“ > „Konfiguration“ > „Konfigurationsdateien importieren und exportieren“.
1. Um die aktuellen Konfigurationseinstellungen in eine Datei zu exportieren, klicken Sie auf „Exportieren“ und speichern die Konfigurationsdatei an einem anderen Speicherort.
1. Suchen Sie in der Datei den Knoten `Domains` > *[Ihr Domain-Name]* > `DirectoryConfigs` > `LDAPGroupConfig`. Beispiel:

   ```as3
    <node name="LDAPGroupConfig"> 
        <map> 
            <entry key="bindanonymously" value="false" />  
            <entry key="basedn" value="dc=corp,dc=adobe,dc=com" />  
            <entry key="batchSize" value="200" />  
            <entry key="binduser" value="cn=Directory Manager" />  
            <entry key="bindpassword" value="" /> 
        </map>
   ```

   Geben Sie einen Wert für `bindpassword` ein und speichern Sie die Änderungen.

1. Suchen Sie in der Datei den Knoten `Domains` > *[Ihr Domain-Name]* > `DirectoryConfigs` > `LDAPGroupConfig` > `LDAPUserConfig`. Beispiel:

   ```as3
    <node name="LDAPUserConfig"> 
        <map> 
            <entry key="bindanonymously" value="false" />  
            <entry key="batchSize" value="200" />  
            <entry key="basedn" value="dc=corp,dc=adobe,dc=com" />  
            <entry key="bindpassword" value="" /> 
            <entry key="binduser" value="cn=Directory Manager" />  
        </map>
   ```

   Geben Sie einen Wert für `bindpassword` ein und speichern Sie die Änderungen.

1. Um die aktualisierte Datei zu importieren, klicken Sie in „Benutzerverwaltung“ auf „Konfiguration“ > „Konfigurationsdateien importieren und exportieren“.
1. Klicken Sie auf „Durchsuchen“, um die Datei zu suchen, dann auf „Importieren“ und anschließend auf „OK“.
