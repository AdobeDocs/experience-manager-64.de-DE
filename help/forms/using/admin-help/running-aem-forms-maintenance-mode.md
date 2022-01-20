---
title: Ausführen von AEM Forms im Wartungsmodus
seo-title: Running AEM forms in maintenance mode
description: Der Wartungsmodus bietet sich beim Ausführen von Aufgaben wie dem Hinzufügen von Patches zu DSC, dem Aktualisieren von AEM Forms oder dem Anwenden eines Service Packs an. Erfahren Sie mehr über die Ausführung von AEM Forms im Wartungsmodus.
seo-description: Maintenance mode is useful when performing tasks such as patching a DSC, upgrading AEM forms, or applying a service pack. Learn more about running AEM forms in maintenance mode.
uuid: 9aa3be20-f17e-4384-b4ce-daaee2898c96
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 94047c12-ba3d-457a-954f-e035c7cc3ecd
exl-id: 2f56bbc7-5e23-4c84-ac0a-03f0b01150b3
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 94%

---

# Ausführen von AEM Forms im Wartungsmodus {#running-aem-forms-in-maintenance-mode}

Der Wartungsmodus bietet sich beim Ausführen von Aufgaben wie dem Hinzufügen von Patches zu DSC, dem Aktualisieren von AEM Forms oder dem Anwenden eines Service Packs an.

Es sollten keine Prozesse aufgerufen werden, während sich der Server im Wartungsmodus befindet. Folgendes erfolgt, wenn ein Prozess aufgerufen wird, während sich der Server im Wartungsmodus befindet:

* Bei einem Prozess mit langer Lebensdauer wird dieser der Auftragsdatenbank hinzugefügt, jedoch nicht gestartet. Wenn Sie den Wartungsmodus beenden, verarbeitet AEM Forms die Prozesse mit langer Lebensdauer in der Warteschlange, auch wenn der Server während des Wartungsmodus neu gestartet wurde.
* Prozesse mit kurzer Lebensdauer werden sofort verarbeitet.

**AEM Forms in den Wartungsmodus versetzen**

1. Geben Sie in einem Webbrowser Folgendes ein:

   `https://`*[hostname ]*`:`*[port]* `/dsc/servlet/DSCStartupServlet?maintenanceMode=pause&user=`*[Administrator-Benutzername ]*`&password=`*[password]*

   Die Meldung „Jetzt angehalten“ wird im Browserfenster angezeigt.

   >[!NOTE]
   >
   >Wenn Sie den Server herunterfahren, während er sich im Wartungsmodus befindet, befindet sich der Server auch nach dem Neustart weiterhin im Wartungsmodus. Wenn Sie Ihre Wartungsaufgaben ausgeführt haben, müssen Sie den Wartungsmodus deaktivieren.

**Überprüfen, ob AEM Forms im Wartungsmodus ausgeführt wird**

1. Geben Sie in einem Webbrowser Folgendes ein:

   `https://`*[hostname]:[port ]*`/dsc/servlet/DSCStartupServlet?maintenanceMode=isPaused&user=`*[Administrator-Benutzername]* `&password=`*[password ]*

   Der Status wird im Browserfenster angezeigt. Der Status „true“ zeigt an, dass der Server im Wartungsmodus ausgeführt wird, und „false“ zeigt an, dass sich der Server nicht im Wartungsmodus befindet.

**Wartungsmodus deaktivieren**

1. Geben Sie in einem Webbrowser Folgendes ein:

   `https://`*[hostname]:[port ]*`/dsc/servlet/DSCStartupServlet?maintenanceMode=resume&user=`*[Administrator-Benutzername]* `&password=`*[password ]*

   Die Meldung „Wird ausgeführt“ wird im Browserfenster angezeigt.
