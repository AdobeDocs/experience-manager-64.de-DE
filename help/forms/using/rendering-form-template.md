---
title: Rendern einer Formularvorlage für HTML5-Formulare
seo-title: Rendering form template for HTML5 forms
description: HTML5-Formularprofile sind mit Profilrendern verknüpft. Profil-Renderer sind JSP-Seiten, die für die Generierung der HTML-Darstellung des Formulars durch Aufruf des Forms OSGi-Dienstes verantwortlich sind.
seo-description: HTML5 forms profiles are associated with profile renders. Profile Renders are JSP pages responsible for generating HTML representation of the form by calling the Forms OSGi service.
uuid: 34daed78-0611-4355-9698-0d7f758e6b61
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: cb75b826-d044-44be-b364-790c046513e0
feature: Mobile Forms
exl-id: ccdb2045-9339-4f39-acb5-85999c4667b9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 39%

---

# Rendern einer Formularvorlage für HTML5-Formulare {#rendering-form-template-for-html-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Render Endpoint {#render-endpoint}

HTML5-Formulare umfassen das Konzept der **Profile**, die als REST-Endpunkte bereitgestellt werden, um Formularvorlagen auf Mobilgeräten rendern zu können. Diese Profile sind mit einem **Profile Renderer** verknüpft. Es handelt sich um JSP-Seiten, auf denen Formulare im HTML-Format generiert werden. Dazu werden Forms OSGi-Services aufgerufen. Der JCR-Pfad des Profilknotens bestimmt die URL des Render-Endpunkts. Der standardmäßige Rendering-Endpunkt des Formulars, der auf das Standardprofil verweist, sieht wie folgt aus:

https://&lt;*Host*>:&lt;*Port*>/content/xfaforms/profiles/default.html?contentRoot=&lt;*Pfad des Ordners mit der Formular-XDP*>&amp;template=&lt;*Name der XDP*>

Beispiel: `http://localhost:4502/content/xfaforms/profiles/default.html?contentRoot=c:/xdps&template=sampleForm.xdp`

Bei einem benutzerdefinierten Profil ändert sich der Endpunkt entsprechend. Der Endpunkt für das benutzerdefinierte Profil mit dem Namen hrforms lautet beispielsweise:

`http://localhost:4502/content/xfaforms/profiles/hrforms.html?contentRoot=c:/xdps&template=sampleForm.xdp`

Wenn sich die Vorlage im AEM-Repository in einer Anwendung namens FormSubmission befindet, lautet die URI:

```
http://localhost:4502/content/xfaforms/profiles/default.html?
 contentRoot=crx:///content/dam/formsanddocuments/FormSubmission/1.0
 &template=sampleForm.xdp
```

## Render-Parameter {#render-parameters}

Folgende Anforderungsparameter werden beim Rendern des Formulars als HTML unterstützt:

<table> 
 <tbody> 
  <tr> 
   <th><strong>Parameter </strong></th> 
   <th><strong>Beschreibung</strong></th> 
  </tr> 
  <tr> 
   <td>template<br /> </td> 
   <td>Dieser Parameter gibt den Namen der Vorlagendatei an.<br /> </td> 
  </tr> 
  <tr> 
   <td>contentRoot<br /> </td> 
   <td>Dieser Parameter gibt den Pfad an, in dem sich die Vorlage und die zugehörigen Ressourcen befinden. Dieser Pfad kann der Serverdateisystempfad, ein Repository-Pfad, ein HTTP- oder ein FTP-Pfad sein.<br /> </td> 
  </tr> 
  <tr> 
   <td>submitUrl<br /> </td> 
   <td>Dieser Parameter gibt die URL an, an die die Formulardaten-XML gesendet wird.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Zusammenführen von Daten mit einer Formularvorlage {#merge-data-with-form-template}

| Parameter | Beschreibung |
|---|---|
| dataRef | Dieser Parameter gibt den **absoluten Pfad** der Datendatei an, die mit der Vorlage zusammengeführt wird. Dieser Parameter kann eine URL eines REST-Services sein, der die Daten im XML-Format zurückgibt. |
| data | Dieser Parameter gibt die UTF-8-kodierten Datenbytes an, die mit der Vorlage zusammengeführt werden. Wenn dieser Parameter angegeben ist, ignoriert das HTML5-Formular den Parameter dataRef . |

### Übergeben des Render-Parameters {#passing-the-render-parameter}

HTML5-Formulare unterstützen drei Methoden zum Übergeben der Render-Parameter. Sie können Parameter über URLs, Schlüssel-Wert-Paare und Profilknoten übergeben. Im Renderparameter hat das Schlüssel-Wert-Paar die höchste Priorität, gefolgt vom Profilknoten. Der URL-Anforderungsparameter erhält die geringste Priorität.

* **URL-Anforderungsparameter**: Sie können die Render-Parameter in der URL angeben. In den URL-Anforderungsparametern sind die Parameter für den Endbenutzer sichtbar. Beispielsweise enthält die folgende Sende-URL die Vorlagenparameter in der URL: `http://localhost:4502/content/xfaforms/profiles/default.html?contentRoot=/Applications/FormSubmission/1.0&template=sampleForm.xdp`

* **SetAttribute-Anforderungsparameter**: Sie können die Render-Parameter als Schlüssel-Wert-Paar angeben. In den SetAttribute-Anforderungsparametern sind die Parameter für den Endbenutzer nicht sichtbar. Sie können eine Anforderung von einem beliebigen anderen JSP an den JSP des Profil-Renderers für HTML5-Formulare weiterleiten und als Anforderungsobjekt *setAttribute* verwenden, um alle Render-Parameter zu übergeben. Diese Methode hat die höchste Priorität.

* **Profilknoten-Anforderungsparameter:** Sie können die Render-Parameter als Knoteneigenschaften eines Profilknotens angeben. In den Profilknoten-Anforderungsparametern sind die Parameter für den Endbenutzer nicht sichtbar. Der Profilknoten ist der Knoten, an den die Anforderung gesendet wird. Um Parameter als Knoteneigenschaften anzugeben, verwenden Sie CRXDE Lite.

### Sendeparameter {#submit-parameters}

HTML5-Formulare senden Daten und führen serverseitige Skripte und Webdienste auf AEM-Servern aus. Ausführliche Informationen zu Parametern für die Ausführung von serverseitigen Skripten und Webdiensten auf AEM-Servern finden Sie unter [HTML5 forms Service Proxy](/help/forms/using/service-proxy.md).
