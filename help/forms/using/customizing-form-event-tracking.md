---
title: Anpassen der Formular-Ereignisverfolgung
seo-title: Customizing form event tracking
description: Wenn ein Benutzer mehr als 60 Sekunden in ein Feld verbringt, wird ein fieldvisit -Ereignis ausgelöst und die Felddetails werden an Adobe SiteCatalyst gesendet.
seo-description: If a user spends more than 60 seconds on a field, a fieldvisit event is triggered and the details of the field are sent to Adobe SiteCatalyst.
uuid: 2f790085-2f1a-45be-9a69-6100c76dcae0
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: 60d67c6b-5994-42ef-b159-ed6edf5cf9d4
exl-id: e07adddb-e904-4a80-9b1c-8028b12c0e37
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 46%

---

# Anpassen der Formular-Ereignisverfolgung {#customizing-form-event-tracking}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Standardmäßig werden die folgenden Ereignisse in einem adaptiven Formular verfolgt, das für Analysen aktiviert ist:

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
   <td>Abbruch</td> 
   <td>formName, formTitle, formInstance, panelName, panelTitle</td> 
  </tr> 
  <tr> 
   <td>Speichern</td> 
   <td>formName, formTitle, formInstance, panelName, source</td> 
  </tr> 
  <tr> 
   <td>absenden</td> 
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

## Anpassen des Zeitlimits für Feldbesuche {#customizing-the-field-visit-event-timeout}

Wenn ein Benutzer bei der standardmäßigen AEM-Formularkonfiguration mehr als 60 Sekunden in einem Feld verbleibt, wird ein `fieldvisit`-Ereignis ausgelöst, und die Details des Feldes werden an Adobe Analytics gesendet. Sie können die Zeitgrundlinie für Feldverfolgung unter AEM Forms Analytics-Konfiguration in AEM Konfigurationskonsole (/system/console/configMgr) anpassen, um die Zeitüberschreitungsbegrenzung zu erhöhen oder zu verringern.

## Anpassen der Tracking-Ereignisse {#customizing-the-tracking-events}

Sie können die Funktion `trackEvent`, die in der Datei `/libs/afanalytics/js/custom.js` verfügbar ist, ändern, um die Ereignisverfolgung anzupassen. Wenn ein verfolgtes Ereignis in einem adaptiven Formular auftritt, wird die Funktion `trackEvent` aufgerufen. Die Funktion `trackEvent` akzeptiert zwei Parameter: `eventName`und `variableValueMap`.

Sie können den Wert von *eventName *und *variableValueMap* -Argumente, um das Tracking-Verhalten von Ereignissen zu ändern. Beispielsweise können Sie die Informationen nach einer bestimmten Anzahl von Fehlerereignissen an den Analytics-Server senden. Sie können auch eine der folgenden Anpassungen vornehmen:

* Sie können eine Schwellenwertzeit festlegen, bevor das Ereignis gesendet wird.
* Sie können einen Status beibehalten, um die Aktion festzulegen (*fieldVisit* überträgt zum Beispiel ein Platzhalterereignis basierend auf dem Zeitstempel des letzten Ereignisses).
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

Nach jeweils 60 Sekunden wird beim Standardsetup von AEM Forms überprüft, ob das Fenster mit dem adaptiven Formular aktiv ist. Wenn das Fenster aktiv ist, ist ein `panelVisit`-Ereignis ausgelöst, das an Adobe Analytics gesendet wird. Es hilft dabei, zu ermitteln, ob das Dokument oder das Formular aktiv ist, und die für das entsprechende Formular oder Dokument verbrachte Zeit zu berechnen.

>[!NOTE]
>
>Der Ereignisname, der zur Speicherung der Aktivität und zur Berechnung der Besuchszeit verwendet wird, lautet &quot;panelVisit&quot;. Dieses Ereignis unterscheidet sich vom Bereichsbesuchsereignis, das in der oben aufgeführten Tabelle aufgeführt ist.

Sie können die Funktion scheduleHeartBeatCheck modifizieren, die in der Datei `/libs/afanalytics/js/custom.js` verfügbar ist, um dieses Ereignis zu ändern und anzuhalten, das regelmäßig an Adobe Analytics gesendet wird.
