---
title: Ausführen von AEM Forms im Wartungsmodus
seo-title: Running AEM forms in maintenance mode
description: Der Wartungsmodus ist nützlich, wenn Aufgaben wie das Patchen eines DSC, das Aktualisieren AEM Formulare oder das Anwenden eines Service Packs ausgeführt werden. Erfahren Sie mehr über das Ausführen AEM Formulare im Wartungsmodus.
seo-description: Maintenance mode is useful when performing tasks such as patching a DSC, upgrading AEM forms, or applying a service pack. Learn more about running AEM forms in maintenance mode.
uuid: 9aa3be20-f17e-4384-b4ce-daaee2898c96
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 94047c12-ba3d-457a-954f-e035c7cc3ecd
exl-id: 2f56bbc7-5e23-4c84-ac0a-03f0b01150b3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 14%

---

# Ausführen von AEM Forms im Wartungsmodus {#running-aem-forms-in-maintenance-mode}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Der Wartungsmodus ist nützlich, wenn Aufgaben wie das Patchen eines DSC, das Aktualisieren AEM Formulare oder das Anwenden eines Service Packs ausgeführt werden.

Vermeiden Sie das Aufrufen von Prozessen, während sich der Server im Wartungsmodus befindet. Dies geschieht, wenn ein Prozess aufgerufen wird, während sich der Server im Wartungsmodus befindet:

* Wenn der Prozess langlebig ist, wird er der Auftragsdatenbank hinzugefügt, aber nicht gestartet. Wenn Sie den Wartungsmodus beenden, verarbeitet AEM Forms die Aufträge mit langer Lebensdauer in der Warteschlange, auch wenn der Server im Wartungsmodus neu gestartet wurde.
* Wenn der Prozess kurzlebig ist, wird er sofort verarbeitet.

**AEM Formulare in den Wartungsmodus versetzen**

1. Geben Sie in einem Webbrowser Folgendes ein:

   `https://`*[hostname ]*`:`*[port]* `/dsc/servlet/DSCStartupServlet?maintenanceMode=pause&user=`*[Administrator-Benutzername ]*`&password=`*[password]*

   Im Browserfenster wird die Meldung &quot;Jetzt angehalten&quot; angezeigt.

   >[!NOTE]
   >
   >Wenn Sie den Server herunterfahren, während er sich im Wartungsmodus befindet, befindet er sich beim Neustart weiterhin im Wartungsmodus. Sie müssen den Wartungsmodus deaktivieren, wenn Sie Ihre Wartungsaufgaben abgeschlossen haben.

**Überprüfen, ob AEM Formulare im Wartungsmodus ausgeführt werden**

1. Geben Sie in einem Webbrowser Folgendes ein:

   `https://`*[hostname]:[port ]*`/dsc/servlet/DSCStartupServlet?maintenanceMode=isPaused&user=`*[Administrator-Benutzername]* `&password=`*[password ]*

   Der Status wird im Browserfenster angezeigt. Der Status &quot;true&quot;zeigt an, dass der Server im Wartungsmodus ausgeführt wird, und &quot;false&quot;zeigt an, dass sich der Server nicht im Wartungsmodus befindet.

**Wartungsmodus deaktivieren**

1. Geben Sie in einem Webbrowser Folgendes ein:

   `https://`*[hostname]:[port ]*`/dsc/servlet/DSCStartupServlet?maintenanceMode=resume&user=`*[Administrator-Benutzername]* `&password=`*[password ]*

   Die Meldung „Wird ausgeführt“ wird im Browserfenster angezeigt.
