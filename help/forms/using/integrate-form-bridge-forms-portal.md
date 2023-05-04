---
title: Integrieren von Form Bridge in das benutzerdefinierte Portal für HTML5-Formulare
seo-title: Integrating Form Bridge with custom portal for HTML5 forms
description: Sie können die FormBridge-API verwenden, um die Werte von Formularfeldern von der HTML-Seite abzurufen oder festzulegen und das Formular zu senden.
seo-description: You can use the FormBridge API to get or set the values of form fields from the HTML page and submit the form.
uuid: 09f2189f-d584-4b84-895e-22833b6b17e3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: e0608649-bd49-4f40-bc1b-821c9b208883
feature: Mobile Forms
exl-id: bf4ae163-5d89-48fb-9bc4-182281b28f35
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 27%

---

# Integrieren von Form Bridge in das benutzerdefinierte Portal für HTML5-Formulare {#integrating-form-bridge-with-custom-portal-for-html-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

FormBridge ist eine Brücken-API für HTML5-Formulare, die es Ihnen ermöglicht, mit einem Formular zu interagieren. Die FormBridge-API-Referenz finden Sie unter [FormBridge-API-Referenz](/help/forms/using/form-bridge-apis.md).

Sie können die FormBridge-API verwenden, um die Werte von Formularfeldern von der HTML-Seite abzurufen oder festzulegen und das Formular zu senden. Sie können beispielsweise die API verwenden, um ein assistentenähnliches Erlebnis zu erstellen.

Eine bestehende HTML-Anwendung kann die FormBridge-API nutzen, um mit einem Formular zu interagieren und es in die HTML-Seite einzubetten. Sie können die folgenden Schritte ausführen, um den Wert eines Felds mithilfe der Form Bridge-API festzulegen.

## Integrieren von HTML5-Formularen in eine Webseite {#integrating-html-forms-to-a-web-page}

1. **Wählen oder erstellen Sie ein Profil.**

   1. Navigieren Sie in der CRX DE-Benutzeroberfläche zu `https://[server]:[port]/crx/de`.
   1. Melden Sie sich mit Administratorberechtigungen an.
   1. Erstellen Sie ein Profil oder wählen Sie ein vorhandenes Profil aus.

      Weitere Informationen zum Erstellen eines Profils finden Sie unter [Erstellen eines neuen Profils](/help/forms/using/custom-profile.md).

1. **Ändern des HTML-Profils**

   Schließen Sie die XFA-Laufzeitumgebung, die XFA-Gebietsschema-Bibliothek und das XFA-Formular-HTML-Snippet in den Profil-Renderer ein, entwerfen Sie Ihre Webseite und platzieren Sie das Formular auf der Webseite.

   Verwenden Sie beispielsweise das folgende Codefragment, um eine App mit zwei Eingabefeldern und einem Formular zu erstellen, um die Interaktion zwischen dem Formular und einer externen App zu demonstrieren.

   ```xml
   <%@ page session="false"
                  contentType="text/html; charset=utf-8"%><%
   %><%@ taglib prefix="cq" uri="https://www.day.com/taglibs/cq/1.0" %><%
   %><!DOCTYPE html>
   <html manifest="${param.offlineSpec}">
       <head>
          <cq:include script="formRuntime.jsp"/>
           <!-- Portal Scripts and Styles -->
          <cq:include script="portalheader.jsp"/> 
       </head>
       <body>
           <div id="leftdiv" >
               <div id="leftdivcontentarea">   
                   <!-- Portal Body -->
                 <cq:include script="portalbody.jsp"/>  
               </div>
           </div>
           <div id="rightdiv">
               <div id="formBody">
               <cq:include script="config.jsp"/>
               <!-- Form body -->
               <cq:include script="formBody.jsp"/>
               <!  --To assist in page transitions -- add navigation, based on scrolling -->
               <cq:include  script="../nav/scroll/nav_footer.jsp"/>
               <cq:include script="footer.jsp"/>
               </div>    
           </div>
       </body>
   </html>
   ```

   >[!NOTE]
   >
   >In **Zeile 9** befinden sich zusätzliche JSP-Verweise für CSS-Stile und JavaScript-Dateien für das Seiten-Design.
   >
   >Die &lt;div id=&quot;rightdiv&quot;> Tag auf **Zeile 18** enthält das HTML-Snippet des XFA-Formulars.
   Die Seite ist in zwei Container formatiert: **left** und **right**. Der rechte Container enthält das Formular. Der linke Container enthält zwei Eingabefelder und einen Teil der externen HTML-Seite.
   Der folgende Screenshot zeigt, wie das Formular in einem Browser angezeigt wird.

   ![Portal](assets/portal.jpg)

   Die linke Seite ist Teil der **HTML-Seite**. Die rechte Seite, die die Felder enthält, ist die **xfa form**.

1. **Zugriff auf die Formularfelder von der Seite aus**

   Im Folgenden finden Sie ein Beispielskript, das Sie hinzufügen können, um Werte in einem Formularfeld festzulegen.

   Wenn Sie beispielsweise den **Mitarbeiternamen** anhand der Werte in den Feldern **Vorname** und **Nachname** festlegen möchten, rufen Sie die Funktion **window.formBridge.setFieldValue** auf.

   Auf ähnliche Weise können Sie den Wert lesen, indem Sie die API **window.formBridge.getFieldValue**aufrufen.

   ```
   $(function() {
               $(".input").blur(function() {
                   window.formBridge.setFieldValue(
                               'xfa.form.form1.#subform[0].EmployeeName',
                                $("#lname").val()+' '+$("#fname").val()
                              )
                   });
           });
   ```
