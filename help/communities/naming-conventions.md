---
title: Benennungskonventionen
seo-title: Naming Conventions
description: Bindestriche in Java-Paketname
seo-description: Hyphens in Java Package Name
uuid: 48086e6c-c35b-4ffc-b216-d01feca7bf9a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 5271feb9-70c6-4c82-8ac7-34a63d80e3aa
exl-id: f5a63642-9f2c-436f-bd40-4459545a0ddf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 7%

---

# Benennungskonventionen {#naming-conventions}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Bindestriche in Java-Paketname {#hyphens-in-java-package-name}

Beachten Sie beim Erstellen eines Speicherorts für eine Java-Klasse, dass der Paketname mit dem Paketnamen des Repository-Ordnerspeicherorts übereinstimmen muss und alle Bindestriche im Pfad ordnungsgemäß maskiert sind.

Die Verwendung von Bindestrichen in den Namen von Repository-Elementen ist eine empfohlene Vorgehensweise bei AEM Entwicklung, aber Bindestriche sind in Java-Paketnamen unzulässig.

Die zugrunde liegende CRX-Plattform muss in der Lage sein, zwischen einem tatsächlichen Unterstrich zu unterscheiden _&#39; und ein Bindestrich &#39;-&#39;. Daher muss der Bindestrich in JCR durch den Unicode-Wert (u002d) ersetzt und mit einem Unterstrich (&quot;_&quot;.

Wenn der Repository-Pfad beispielsweise **/apps/my-example/component/info/Info.java**, sollte der Paketname `java package apps.my_002dexample.component.info;`

Beachten Sie, dass ein Unterstrich in ähnlicher Weise maskiert werden muss, sodass `_` wird `_005f`.
