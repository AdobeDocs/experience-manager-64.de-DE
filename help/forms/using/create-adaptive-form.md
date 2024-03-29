---
title: '„Tutorial: Erstellen eines adaptiven Formulars“'
seo-title: Create an adaptive form
description: Erfahren Sie, wie Sie ein adaptives Formular erstellen, anordnen und in der Vorschau anzeigen. Erfahren Sie auch, wie Sie Sendeaktionen konfigurieren.
seo-description: Learn to create, layout, and preview an adaptive form. Also, learn to configure submit actions.
page-status-flag: de-activated
uuid: 0010d274-a683-499e-9fa6-ce355d7898a0
discoiquuid: 55c08940-8c25-4938-8e49-25bce20aaf22
feature: Adaptive Forms
exl-id: 144f7c0a-66af-4a8f-8d8c-f960cb612104
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1433'
ht-degree: 59%

---

# Schulung: Erstellen eines adaptiven Formulars {#do-not-publish-tutorial-create-an-adaptive-form}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

![02-create-adaptive-form-main-image](assets/02-create-adaptive-form-main-image.png)

Dieses Tutorial ist ein Schritt im [Erstellen Ihres ersten adaptiven Formulars](/help/forms/using/create-your-first-adaptive-form.md) Reihe. Es wird empfohlen, der Reihe in chronologischer Reihenfolge zu folgen, um den vollständigen Anwendungsfall des Tutorials zu verstehen, auszuführen und zu demonstrieren.

## Über das Tutorial {#about-the-tutorial}

Adaptive Formulare sind Formulare der neuen Generation, die dynamisch und responsiv sind. Sie können adaptive Formulare verwenden, um ein personalisiertes Benutzererlebnis zu schaffen. Sie können adaptive Formulare auch in Adobe Analytics für Nutzungsstatistiken und Adobe Campaign für die Kampagnenverwaltung integrieren. Weitere Informationen zu den Funktionen adaptiver Formulare finden Sie unter [Einführung in das Bearbeiten adaptiver Formulare](/help/forms/using/introduction-forms-authoring.md).

Es ist einfacher, Formulare zu erstellen und zu verwalten, wenn ein ordnungsgemäßer Prozess eingehalten wird. In diesem Artikel lernen Sie Folgendes: 

* [Erstellen Sie ein adaptives Formular, mit dem ein Kunde eine Versandadresse hinzufügen kann](/help/forms/using/create-adaptive-form.md#step-create-the-adaptive-form)

* [Layout-Felder eines adaptiven Formulars zum Anzeigen und Akzeptieren von Informationen eines Kunden](/help/forms/using/create-adaptive-form.md#step-add-header-and-footer)

* [Erstellen Sie eine Sendeaktion zum Senden einer E-Mail mit Formularinhalt](/help/forms/using/create-adaptive-form.md#step-add-components-to-capture-and-display-information)
* [Anzeigen und Senden eines adaptiven Formulars in der Vorschau](/help/forms/using/create-adaptive-form.md)

Am Ende des Artikels haben Sie ein Formular, was so ähnlich wie Folgendes aussieht:

    [ ![](do-not-localize/form-preview-mobile.gif)](assets/form-preview-mobile.gif)

## Schritt 1: Adaptives Formular erstellen {#step-create-the-adaptive-form}

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an und navigieren Sie zu **Adobe Experience Manager** > **Formulare** > **Formulare und Dokumente**. Die Standard-URL lautet [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments).
1. Tippen Sie auf **Erstellen** und wählen Sie **Adaptives Formular**. Eine Option zum Auswählen einer Vorlage wird angezeigt. Tippen Sie auf die **leere** Vorlage, um sie auszuwählen, und dann auf **Weiter**.

1. Eine Option **Eigenschaften hinzufügen** wird angezeigt. Die Felder **Titel** und **Name** sind obligatorisch.

   * **Titel:** Geben Sie `Add new or update shipping address` im Feld Titel an. Das Feld „Titel“: Gibt den Anzeigenamen des Formulars an. Der Titel erleichtert Ihnen die Identifizierung des Formulars in der Benutzeroberfläche von AEM Forms.
   * **Name:** Geben Sie `shipping-address-add-update-form` in das Feld Name ein. Das Feld Name gibt den Namen des Formulars an. Im Repository wird ein Knoten mit dem angegebenen Namen erstellt. Wenn Sie mit der Eingabe des Titels beginnen, wird automatisch ein Wert für das Feld „Name“ vorgeschlagen. Sie können den vorgeschlagenen Wert gegebenenfalls ändern. Im Feld „Name“ dürfen nur alphanumerische Zeichen, Bindestriche und Unterstriche eingegeben werden. Alle ungültigen Eingaben werden durch Bindestriche ersetzt.

1. Tippen Sie auf **Erstellen**. Ein adaptives Formular wird erstellt und es wird ein Dialogfeld zum Öffnen des Formulars zur Bearbeitung angezeigt. Tippen Sie auf **Öffnen**, um das neu erstellte Formular in einer neuen Registerkarte zu öffnen. Das Formular wird zur Bearbeitung geöffnet. Er zeigt auch die Seitenleiste an, um das neu erstellte Formular entsprechend den Anforderungen anzupassen.

   Informationen zur Authoring-Oberfläche für adaptive Formulare und zu verfügbaren Komponenten finden Sie unter [Einführung in das Authoring adaptiver Formulare](/help/forms/using/creating-adaptive-form.md).

   ![newly-created-adaptive-form](assets/newly-created-adaptive-form.png)

## Schritt 2: Kopf- und Fußzeile hinzufügen {#step-add-header-and-footer}

AEM Forms bietet viele Komponenten zum Anzeigen von Informationen in einem adaptiven Formular. Die Kopf- und Fußzeilenkomponenten ermöglichen ein einheitliches Erscheinungsbild des Formulars. Eine Kopfzeile enthält normalerweise das Logo eines Unternehmens, den Titel des Formulars und die Zusammenfassung. Eine Fußzeile enthält meist Copyright-Informationen und Links zu anderen Seiten.

1. Tippen Sie auf ![toggle-side-panel](assets/toggle-side-panel.png) > ![treeexpandall](assets/treeexpandall.png). Der Komponentenbrowser wird geöffnet. Ziehen Sie die Komponente **Kopfzeile** aus dem Komponentenbrowser in das adaptive Formular.
1. Tippen **Logo**. Die Symbolleiste wird angezeigt. Tippen Sie in der Werkzeugleiste auf ![aem_6_3_edit](assets/aem_6_3_edit.png). Geben Sie **We.Retail** ein und tippen Sie anschließend auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

1. Tippen Sie auf Bild. Die Symbolleiste wird angezeigt. Tippen Sie auf ![cmppr](assets/cmppr.png). Der Eigenschaften-Browser wird auf der linken Seite des Bildschirms geöffnet. **Suchen Sie** das Logo und laden Sie es hoch. Tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png). Das Bild wird in der Kopfzeile angezeigt.

   Sie können auf Datei laden tippen, um das in diesem Artikel verwendete Logo herunterzuladen, wenn Sie keines haben.

[Datei laden](assets/logo.png)

1. Ziehen Sie die Komponente **Fußzeile** aus ![treeexpandall](assets/treeexpandall.png) in das adaptive Formular. Nach diesem Schritt sieht das Formular wie folgt aus:

   ![adaptive-form-with-headers-and-footers](assets/adaptive-form-with-headers-and-footers.png)

## Schritt 3: Komponenten hinzufügen, um Informationen zu erfassen und anzuzeigen {#step-add-components-to-capture-and-display-information}

Komponenten sind Bausteine &#x200B;&#x200B;eines adaptiven Formulars. AEM Forms bietet viele Komponenten zum Erfassen und Anzeigen von Informationen in einem adaptiven Formular. Sie können die Komponenten von ![treeexpandall](assets/treeexpandall.png) in ein Formular ziehen. Informationen zu verfügbaren Komponenten und entsprechenden Funktionen finden Sie in [Einführung in die Bearbeitung von adaptiven Formularen](/help/forms/using/introduction-forms-authoring.md). 

1. Ziehen Sie die numerische Feldkomponente in das adaptive Formular. Platzieren Sie sie vor der Fußzeilenkomponente. Öffnen Sie die Eigenschaften der Komponente. Ändern Sie den **Titel** der Komponente in **`Customer ID`** und den **Elementnamen** in **`customer_ID`**. Aktivieren Sie die Option **Erforderliches Feld**, aktivieren Sie die Option **HTML5-Zahleneingabetyp verwenden** und tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).
1. Ziehen Sie drei Textfeldkomponenten in das adaptive Formular. Platzieren Sie diese vor der Fußzeilenkomponente. Legen Sie die folgenden Eigenschaften für diese Textfelder fest.:

<table> 
 <tbody> 
  <tr> 
   <td>Eigenschaft</td> 
   <td>Textfeld 1<br /> </td> 
   <td>Textfeld 2<br /> </td> 
   <td>Textfeld 3</td> 
  </tr> 
  <tr> 
   <td>Titel</td> 
   <td>Name<br /> </td> 
   <td>Lieferadresse</td> 
   <td>Status</td> 
  </tr> 
  <tr> 
   <td>Elementname</td> 
   <td>customer_Name<br /> </td> 
   <td>customer_Shipping_Address</td> 
   <td>customer_State</td> 
  </tr> 
  <tr> 
   <td>Erforderliches Feld</td> 
   <td>Aktiviert</td> 
   <td>Aktiviert</td> 
   <td>Aktiviert</td> 
  </tr> 
  <tr> 
   <td>Mehrere Zeilen zulassen<br /> </td> 
   <td>Deaktiviert</td> 
   <td>Aktiviert</td> 
   <td>Deaktiviert</td> 
  </tr> 
 </tbody> 
</table>

1. Ziehen Sie eine **Numerisches Feld**-Komponente vor die Fußzeilenkomponente. Öffnen Sie die Eigenschaften der Komponente, legen Sie die in der folgenden Tabelle aufgeführten Werte fest und tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Eigenschaft | Wert |
   |---|---|
   | Titel | Postleitzahl |
   | Elementname | customer_ZIPCode |
   | Maximale Anzahl von Ziffern | 6 |
   | Erforderliches Feld | Aktiviert |
   | Anzeigemuster Typ | Kein Muster |

1. Ziehen Sie eine **E-Mail**-Komponente vor die Fußzeilenkomponente. Öffnen Sie die Eigenschaften der Komponente, legen Sie die in der folgenden Tabelle aufgeführen Werte fest und tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Eigenschaft | Wert |
   |---|---|
   | Titel | E-Mail |
   | Elementname | customer_Email |
   | Erforderliches Feld | Aktiviert |

1. Ziehen Sie eine **Dateianhang** -Komponente vor der Fußzeilenkomponente. Öffnen Sie die Eigenschaften der Komponente, legen Sie die in der folgenden Tabelle aufgeführen Werte fest und tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

<table> 
 <tbody> 
  <tr> 
   <td>Eigenschaft</td> 
   <td>Wert</td> 
  </tr> 
  <tr> 
   <td>Titel</td> 
   <td>Von Behörden anerkannter Adressnachweis<br /> </td> 
  </tr> 
  <tr> 
   <td>Elementname</td> 
   <td>customer_Address_Proof</td> 
  </tr> 
  <tr> 
   <td>Erforderliches Feld</td> 
   <td>Aktiviert</td> 
  </tr> 
 </tbody> 
</table>

1. Ziehen Sie eine **Senden-Schaltfläche** -Komponente in das adaptive Formular ein. Platzieren Sie sie vor der Fußzeilenkomponente. Öffnen Sie die Eigenschaften der Komponente und ändern Sie den Elementnamen in **address_additional_update_submit** Tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png). Das Layout des Formulars ist vollständig und das Formular sieht wie folgt aus:

   ![adaptive-form-with-all-the-components](assets/adaptive-form-with-all-the-components.png)

## Schritt 4: Konfigurieren der Sendeaktion für das adaptive Formular {#step-configure-submit-action-for-the-adaptive-form}

Eine Übermittlungsaktion wird ausgelöst, wenn ein Benutzer in einem adaptiven Formular auf die Schaltfläche &quot;Senden&quot;tippt. Sie können eine Übermittlungsaktion verwenden, um Formulardaten in das lokale Repository zu speichern, Formulardaten an einen REST-Endpunkt zu senden, Formulardaten als E-Mail zu senden und vieles mehr. Adaptive Formulare bieten einige weitere vordefinierte Übermittlungsaktionen. Detaillierte Informationen finden Sie unter [Konfigurieren der Sendeaktion](/help/forms/using/configuring-submit-actions.md).

Mit den folgenden Schritten können Sie die E-Mail-Sendeaktion und die Demo-Sendeaktion des Formulars konfigurieren:

1. Konfigurieren Sie den E-Mail-Server. Weitere Informationen finden Sie unter [Konfigurieren von E-Mail-Benachrichtigungen.](/help/sites-administering/notification.md).

   /content/help/en/experience-manager/6-4/sites-administering/notification.html

1. Tippen Sie im Inhalts-Browser auf **Formular-Container** und dann auf ![cmppr](assets/cmppr.png). Der Eigenschaften-Browser wird auf der linken Seite geöffnet.
1. Navigieren Sie zu **Übermittlung** > **Übermittlungsaktion**. Wählen Sie **E-Mail senden**. Geben Sie die folgenden Werte an und tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Eigenschaft | Wert |
   |--- |--- |
   | Von | `donotreply@weretail.com` |
   | To | `${customer_Email}` |
   | Betreff | Bestätigung: Sie haben die Lieferadresse auf der We.Retail-Website hinzugefügt. |
   | E-Mail-Vorlage | Hallo `${customer_Name}`, die folgende Adresse wurde als Lieferadresse für Ihr Konto hinzugefügt: <br>`${customer_Name}`, `${customer_Shipping_Address}`, `${customer_State}`, `${customer_ZIPCode}`<br> Mit freundlichen Grüßen, We.Retail |
   | Anlagen einschließen | Aktiviert |

   Ihr Formular ist bereit. Jetzt können Sie eine Vorschau des Formulars anzeigen und die Funktionalität testen. Wenn Sie den im Tutorial erwähnten Namen verwendet haben und auf das Formular auf dem Computer zugreifen, auf dem der AEM Forms-Server ausgeführt wird, ist das Formular verfügbar unter [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html).

## Schritt 5: Adaptives Formular in der Vorschau ansehen und senden {#step-preview-and-submit-the-adaptive-form}

Sie können die Option **Vorschau** verwenden, um das Erscheinungsbild und Verhalten eines Formulars zu bewerten. Sie können ein Formular im Vorschaumodus senden und auch auf ein Formular angewendete Validierungen überprüfen. Wenn beispielsweise ein Fehler angezeigt wird, wenn ein Pflichtfeld leer gelassen wird.

Adaptive Formulare bieten auch eine Option zum Emulieren von Erlebnissen eines Formulars für verschiedene Geräte. Beispiel: iPhone, iPad und Desktop. Sie können die beiden Optionen **Vorschau** und **Emulator**-![Lineal](assets/ruler.png) in Verbindung miteinander verwenden, um eine Vorschau eines Formulars für Geräte mit unterschiedlichen Bildschirmgrößen anzuzeigen.

1. Tippen Sie auf die Option **Vorschau** auf der rechten Seite des Formulareditors. Das Formular wird im Bearbeitungsmodus geöffnet. Wenn Sie den Namen verwendet haben, der in der Schulung benutzt wird, dann lautet die Vorschau-URL des Formulars [http://localhost:4502/content/dam/formsanddocuments/shipping-address-add-update-form/jcr:content?wcmmode=disabled](http://localhost:4502/content/dam/formsanddocuments/shipping-address-addition-updation-form/jcr:content?wcmmode=disabled)
1. Verwenden Sie ![Lineal](assets/ruler.png), um zu sehen, wie das Formular auf verschiedenen Geräten aussieht.
1. Füllen Sie die Felder des Formulars aus und tippen Sie auf **Einsenden**. Das Formular wird gesendet und Sie werden zur Standardeinstellung weitergeleitet **Vielen Dank** Seite. Sie können auch eine benutzerdefinierte Dankeseite angeben. Einzelheiten finden Sie unter [Konfigurieren der Weiterleitungsseite](/help/forms/using/configuring-redirect-page.md).

Das adaptive Formular zum Hinzufügen einer Adresse ist fertig. Wenn Sie den im Tutorial erwähnten Namen verwendet haben und auf das Formular auf dem Computer zugreifen, auf dem der AEM Forms-Server ausgeführt wird, ist das Formular verfügbar unter [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html).
