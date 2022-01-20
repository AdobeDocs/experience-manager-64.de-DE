---
title: Anpassen der Formular-Ereignisverfolgung
seo-title: Customizing form event tracking
description: Wenn ein Benutzer mehr als 60 Sekunden in einem Feld verbleibt, wird ein fieldvisit-Ereignis ausgelöst, und die Details des Feldes werden an Adobe SiteCatalyst gesendet.
seo-description: If a user spends more than 60 seconds on a field, a fieldvisit event is triggered and the details of the field are sent to Adobe SiteCatalyst.
uuid: 2f790085-2f1a-45be-9a69-6100c76dcae0
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: 60d67c6b-5994-42ef-b159-ed6edf5cf9d4
exl-id: e07adddb-e904-4a80-9b1c-8028b12c0e37
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 75%

---

# Anpassen der Formular-Ereignisverfolgung {#customizing-form-event-tracking}

Standardmäßig werden die folgenden Ereignisse in einem adaptiven Formular verfolgt, in dem die Analytik aktiviert ist:

<table> 
 <tbody> 
  <tr> 
   <th>Ereignis</th> 
   <th>Verfügbare Variablen</th> 
  </tr> 
  <tr> 
   <td>render</td> 
   <td>formName, formTitle, formInstance, source</td> 
  </tr> 
  <tr> 
   <td>abandon</td> 
   <td>formName, formTitle, formInstance, panelName, panelTitle</td> 
  </tr> 
  <tr> 
   <td>Speichern</td> 
   <td>formName, formTitle, formInstance, panelName, source</td> 
  </tr> 
  <tr> 
   <td>submit</td> 
   <td>formName, formTitle, formInstance, source</td> 
  </tr> 
  <tr> 
   <td>Fehler</td> 
   <td>formName, formTitle, fieldName, fieldTitle, panelTitle</td> 
  </tr> 
  <tr> 
   <td>help</td> 
   <td>formName, formTitle, fieldName, fieldTitle, panelTitle</td> 
  </tr> 
  <tr> 
   <td>fieldVisit</td> 
   <td>formName, formTitle, fieldName, fieldTitle, panelTitle<br /> </td> 
  </tr> 
  <tr> 
   <td>panelVisit</td> 
   <td>formName, formTitle, panelName, panelTitle</td> 
  </tr> 
 </tbody> 
</table>

## Anpassen der Zeitüberschreitung für Feldbesuche {#customizing-the-field-visit-event-timeout}

Wenn ein Benutzer bei der standardmäßigen AEM-Formularkonfiguration mehr als 60 Sekunden in einem Feld verbleibt, wird ein `fieldvisit`-Ereignis ausgelöst, und die Details des Feldes werden an Adobe Analytics gesendet. Sie können den Zeitschwellenwert für Feldverfolgung unter AEM forms-Analytics-Konfiguration in der AEM Configuration-Konsole (/system/console/configMgr) anpassen, um den Timeout-Wert zu erhöhen oder zu verringern.

## Anpassen der Verfolgungsereignisse {#customizing-the-tracking-events}

Sie können die `trackEvent`-Funktion verfügbar in `/libs/afanalytics/js/custom.js` -Datei, um die Ereignisverfolgung anzupassen. Wenn ein verfolgtes Ereignis in einem adaptiven Formular auftritt, wird die Funktion `trackEvent` aufgerufen. Die `trackEvent` -Funktion akzeptiert zwei Parameter: `eventName`und `variableValueMap`.

Sie können den Wert von *eventName *und *variableValueMap* -Argumente, um das Tracking-Verhalten von Ereignissen zu ändern. Sie können beispielsweise festlegen, dass die Informationen an den Analytics-Server gesendet werden, nachdem eine bestimmte Anzahl an Fehlerereignissen aufgetreten ist. Sie können außerdem die folgenden Anpassungen ausführen:

* Sie können eine Schwellenwertzeit festlegen, bevor das Ereignis gesendet wird.
* Sie können einen Status beibehalten, um beispielsweise eine Aktion festzulegen. *fieldVisit* sendet ein Platzhalterereignis basierend auf dem Zeitstempel des letzten Ereignisses.
* Sie können die Funktion `pushEvent` verwenden, um das Ereignis an den Analytics-Server zu senden *.*

* Sie können festlegen, das Ereignis nicht an den Analytics-Server zu senden.

### Beispiel {#sample}

Im folgenden Beispiel wird der Status für die *error* -Ereignis jedes *fieldName *beibehalten*. *Das Ereignis wird nur dann an den Analytics-Server gesendet, wenn ein Fehler erneut auftritt.

```
case 'error':
        if(errorOccurred[variableValueMap.fieldName] == true) {
            pushEvent(eventName, variableValueMap)
        }
        errorOccurred[variableValueMap.fieldName] = true;
        break;
```

## Anpassen des panelvisit-Ereignisses {#customizing-the-panelvisit-event}

Nach jeweils 60 Sekunden wird beim Standardsetup von AEM Forms überprüft, ob das Fenster mit dem adaptiven Formular aktiv ist. Wenn das Fenster aktiv ist, wird ein `panelVisit`-Ereignis wird in Adobe Analytics ausgelöst. Es ermittelt, of das Dokument oder das Formular aktiv ist und berechnet die Zeit, die für da entsprechende Formular oder Dokument verwendet wird.

>[!NOTE]
>
>Der Ereignisname, der zur Ermittlung der Aktivität und Berechnung der Zeit verwendet wird lautet „panelVisit“. Dieses Ereignis unterscheidet sich vom Bereichsbesuchsereignis, das in der obigen Tabelle aufgelistet ist.

Sie können die scheduleHeartBeatCheck-Funktion ändern, die in der `/libs/afanalytics/js/custom.js` -Datei, um dieses Ereignis zu ändern oder anzuhalten, das regelmäßig an Adobe Analytics gesendet wird.
