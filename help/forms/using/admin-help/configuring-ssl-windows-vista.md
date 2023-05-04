---
title: Konfigurieren von SSL unter Windows Vista
seo-title: Configuring SSL on Windows Vista
description: Erfahren Sie, wie Sie SSL unter Windows Vista konfigurieren.
seo-description: Learn how to configure SSL on Windows Vista.
uuid: 20bfcefb-ec84-4c55-bceb-6af106d883d7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 667645a0-53d0-4f9b-a0ba-cc7e366a23a1
exl-id: 8eee2ed2-8263-47f2-b928-214fd9ab5f6e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 20%

---

# Konfigurieren von SSL unter Windows Vista {#configuring-ssl-on-windows-vista}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Zum Konfigurieren von SSL unter Windows Vista™ benötigen Sie ein SSL-Zertifikat mit RSA-Schlüsseln für die Authentifizierung. Sie können das Java-Keytool verwenden, um das Zertifikat zu erstellen.

>[!NOTE]
>
>Windows Vista funktioniert nicht mit DSA-Schlüsseln.

Sie können Keytool mit einem einzelnen Befehl ausführen, der alle zum Erstellen des Zertifikats und Keystore erforderlichen Informationen enthält.

**Erstellen eines SSL-Zertifikats**

1. Wechseln Sie an einer Eingabeaufforderung zum *[JAVA HOME]*/bin und geben Sie den folgenden Befehl ein, um das Zertifikat und den Keystore zu erstellen:

   `keytool -genkey -keyalg RSA -dname "CN=`*Hostname* `, OU=`*Gruppenname* `, O=`*Firmenname* `,L=`*Ort******Name* `, S=`*state* `, C=`*Ländercode* `" -alias`*&quot;LC Cert&quot;* `-keypass` `*key*`*_**password* `-keystore`*keystorename* `.keystore`

   >[!NOTE]
   >
   >Ersetzen *[JAVA_HOME] durch den Ordner, in dem das JDK installiert ist, und ersetzen Sie kursiv den Text durch die Werte, die Ihrer Umgebung entsprechen.*

1. Geben Sie `changeit` als Kennwort ein. Dies ist das Standardkennwort für Java-Installationen. Eventuell wurde es von Ihrem Systemadministrator geändert.
