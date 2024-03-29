---
title: Regeleditor für adaptive Formulare
seo-title: Adaptive forms rule editor
description: Mit dem Regeleditor für adaptive Formulare können Sie dynamische Verhaltensweisen hinzufügen und komplexe Logiken in Formularen ohne Programmierung oder Skripterstellung erstellen.
seo-description: Adaptive forms rule editor allows you to add dynamic behavior and build complex logic into forms without coding or scripting.
uuid: 15c9bb41-ddae-4d3e-b130-5eb1b7572e6e
content-type: reference
topic-tags: adaptive_forms, develop
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 66a3528a-489b-4fd0-be6c-b8c4b9b1f908
feature: Adaptive Forms
exl-id: 7cd73bdf-6717-4923-91ca-e8b6d44429ca
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '6364'
ht-degree: 53%

---

# Regeleditor für adaptive Formulare  {#adaptive-forms-rule-editor}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht {#overview}

Mit der Regeleditor-Funktion in Adobe Experience Manager Forms können Benutzer und Entwickler von Formularen Regeln für adaptive Formularobjekte schreiben. Diese Regeln definieren Aktionen für Formularobjekte, die durch voreingestellte Bedingungen, Benutzereingaben und Benutzeraktionen im Formular ausgelöst werden. Dadurch wird das Ausfüllen von Formularen optimiert, was Genauigkeit und Geschwindigkeit gewährleistet.

Der Regeleditor bietet eine intuitive und vereinfachte Benutzeroberfläche zum Schreiben von Regeln. Der Regeleditor bietet einen visuellen Editor für alle Benutzer. Darüber hinaus bietet der Regeleditor nur für Benutzer mit Formularleistung einen Code-Editor zum Schreiben von Regeln und Skripten. Einige der wichtigsten Aktionen, die Sie mithilfe von Regeln für Objekte in adaptiven Formularen durchführen können, sind:

* Ein Objekt ein- oder ausblenden
* Ein Objekt aktivieren oder deaktivieren
* Einen Wert für ein Objekt festlegen
* Den Wert eines Objekts validieren
* Funktionen zur Berechnung des Werts eines Objekts ausführen
* Rufen Sie einen Formular-Datenmodell-Service auf und führen Sie einen Vorgang aus
* Festlegen einer Eigenschaft eines Objekts

Der Regeleditor ersetzt die Skipterstellungs-Funktionen aus AEM 6.1 Forms und früheren Versionen. Ihre vorhandenen Skripte werden jedoch im neuen Regeleditor beibehalten. Weitere Informationen zum Arbeiten mit vorhandenen Skripten im Regeleditor finden Sie unter [Auswirkung des Regeleditors auf vorhandene Skripte](#impact-of-rule-editor-on-existing-scripts)

Benutzer, die der Gruppe &quot;forms-power-users&quot;hinzugefügt wurden, können neue Skripte erstellen und vorhandene bearbeiten. Benutzer in der Gruppe &quot;forms-users&quot;können die Skripte verwenden, aber keine Skripte erstellen oder bearbeiten.

## Grundlegendes zu Regeln {#understanding-a-rule}

Eine Regel ist eine Kombination aus Aktionen und Bedingungen. Im Regeleditor umfassen Aktionen Aktivitäten wie das Ausblenden, Anzeigen, Aktivieren, Deaktivieren oder Berechnen des Werts eines Objekts in einem Formular. Bedingungen sind boolesche Ausdrücke, die durch Prüfungen und Vorgänge für den Status, den Wert oder die Eigenschaft eines Formularobjekts ausgewertet werden. Aktionen werden basierend auf dem bei der Auswertung einer Bedingung zurückgegebenen Wert (`True` oder `False`) ausgeführt.

Der Regeleditor bietet eine Reihe vordefinierter Regeltypen, z. B. &quot;Wann&quot;, &quot;Anzeigen&quot;, &quot;Ausblenden&quot;, &quot;Aktivieren&quot;, &quot;Deaktivieren&quot;, &quot;Wert einstellen&quot;und &quot;Validieren&quot;, um Ihnen beim Schreiben von Regeln zu helfen. Mit jedem Regeltyp können Sie Bedingungen und Aktionen in einer Regel definieren. In diesem Dokument sind die einzelnen Regeltypen im Detail beschrieben.

Eine Regel folgt normalerweise einem der folgenden Konstrukte:

**Bedingung-Aktion** In diesem Konstrukt definiert die Regel zuerst eine Bedingung und dann die auszulösende Aktion. Dieses Konstrukt ist mit einer if-then-Anweisung in Programmiersprachen vergleichbar.

Im Regeleditor wird das Bedingung-Aktion-Konstrukt durch den Regeltyp **Wenn** durchgesetzt.

**Aktion-Bedingung** In diesem Konstrukt definiert die Regel zuerst eine auszulösende Aktion und dann die auszuwertenden Bedingungen. Eine weitere Variante dieses Konstrukts ist Aktion-Bedingung-alternative Aktion, wobei auch dann eine alternative Aktion angegeben wird, die ausgelöst wird, wenn die Bedingung den Wert „False“ zurückgibt.

Die Regeltypen „Anzeigen“, „Ausblenden“, „Aktivieren“, „Deaktivieren“, „Wert festlegen“ und „Validieren“ im Regeleditor setzen das Aktion-Bedingung-Regelkonstrukt um. Standardmäßig lautet die alternative Aktion für &quot;Anzeigen&quot;Ausblenden und für &quot;Aktivieren&quot;Deaktivieren und umgekehrt. Sie können die standardmäßige alternative Aktion nicht ändern.

>[!NOTE]
>
>Die verfügbaren Regeltypen, einschließlich der Bedingungen und Aktionen, die Sie im Regeleditor definieren, hängen auch vom Typ des Formularobjekts ab, für das Sie eine Regel erstellen. Der Regeleditor zeigt nur gültige Regeltypen und Optionen zum Schreiben von Bedingungs- und Aktionsanweisungen für einen bestimmten Formularobjekttyp an. So werden für ein Bereichsobjekt beispielsweise keine Regeln vom Typ „Validieren“, „Wert festlegen“ oder „Deaktivieren“ angezeigt.

Weitere Informationen über die im Regeleditor verfügbaren Regeltypen finden Sie unter [Verfügbare Regeltypen im Regeleditor](#available-rule-types-in-rule-editor).

### Richtlinien für die Auswahl eines Regelkonstrukts {#guidelines-for-choosing-a-rule-construct}

Für die meisten Anwendungsfälle können Sie ein beliebiges Regelkonstrukt verwenden. Nachfolgend finden Sie jedoch einige Richtlinien für die Wahl des am besten geeigneten Konstrukts für Ihre Zwecke. Weitere Informationen über die verfügbaren Regeln im Regeleditor finden Sie unter [Verfügbare Regeltypen im Regeleditor](#available-rule-types-in-rule-editor).

* Eine typische Faustregel beim Erstellen einer Regel besteht darin, im Kontext des Objekts, für das Sie eine Regel erstellen, darüber nachzudenken. Angenommen, das Feld B soll basierend auf dem Wert, den ein Benutzer in Feld A angibt, ausgeblendet oder angezeigt werden. In diesem Fall wird eine Bedingung für Feld A ausgewertet und basierend auf dem zurückgegebenen Wert eine Aktion für Feld B ausgelöst.

   Wenn Sie daher eine Regel für Feld B (das Objekt, für das Sie eine Bedingung auswerten) schreiben, verwenden Sie das Konstrukt &quot;Bedingung-Aktion&quot;oder den Regeltyp &quot;Wenn&quot;. Verwenden Sie auf ähnliche Weise das Konstrukt Aktion-Bedingung oder den Regeltyp Anzeigen oder Ausblenden für Feld A.

* Manchmal müssen Sie mehrere Aktionen ausführen, die auf einer Bedingung basieren. In solchen Fällen wird empfohlen, das Konstrukt &quot;Bedingung-Aktion&quot;zu verwenden. In diesem Konstrukt können Sie eine Bedingung einmal auswerten und mehrere Aktionsanweisungen angeben.

   Um beispielsweise die Felder B, C und D anhand der Bedingung auszublenden, die nach dem Wert sucht, den ein Benutzer in Feld A angibt, schreiben Sie eine Regel mit Bedingungsaktionskonstrukt oder Wenn Regeltyp für Feld A und geben Sie Aktionen an, um die Sichtbarkeit der Felder B, C und D zu steuern. Andernfalls benötigen Sie drei separate Regeln für die Felder B, C und D, bei denen jede Regel die Bedingung überprüft und das entsprechende Feld ein- oder ausblendet. In diesem Beispiel ist es effizienter, den Wenn-Regeltyp für ein Objekt zu schreiben, anstatt für drei Objekte den Regeltyp &quot;Anzeigen&quot;oder &quot;Ausblenden&quot;.

* Für den Trigger einer Aktion, die auf mehreren Bedingungen basiert, wird empfohlen, das Konstrukt &quot;action-condition&quot;zu verwenden. Um beispielsweise Feld A durch Auswertung der Bedingungen für die Felder B, C und D ein- und auszublenden, verwenden Sie Regeltyp &quot;Anzeigen&quot;oder &quot;Ausblenden&quot;für Feld A.
* Verwenden Sie das Konstrukt Bedingung-Aktion oder Aktion-Bedingung , wenn die Regel eine Aktion für eine Bedingung enthält.
* Wenn eine Regel nach einer Bedingung sucht und sofort eine Aktion ausführt, wenn ein Wert in einem Feld bereitgestellt oder ein Feld beendet wird, wird empfohlen, eine Regel mit dem Konstrukt &quot;Bedingung-Aktion&quot;oder dem Regeltyp &quot;Wenn&quot;für das Feld zu schreiben, für das die Bedingung ausgewertet wird.
* Die Bedingung in der Wenn-Regel wird ausgewertet, wenn ein Benutzer den Wert des Objekts ändert, auf das die Wenn-Regel angewendet wird. Wenn die Aktion jedoch Trigger werden soll, wenn sich der Wert serverseitig ändert (z. B. wenn der Wert vorausgefüllt wird), wird empfohlen, eine Wenn-Regel zu schreiben, die die Aktion beim Initialisieren des Felds Trigger.
* Beim Schreiben von Regeln für Dropdown-Elemente, Optionsfelder oder Kontrollkästchenobjekte werden die Optionen oder Werte dieser Formularobjekte im Formular im Regeleditor vorbefüllt.

## Verfügbare Typen von Operatoren und Ereignissen im Regeleditor {#available-operator-types-and-events-in-rule-editor}

Der Regeleditor bietet die folgenden logischen Operatoren und Ereignisse, mit denen Sie Regeln erstellen können.

* **ist gleich**
* **ist nicht gleich**
* **Beginnt mit**
* **Endet mit**
* **Enthält**
* **Ist leer**
* **Ist nicht leer**
* **Hat ausgewählt:** Gibt „true“ zurück, wenn der Benutzer eine bestimmte Option für ein Kontrollkästchen, ein Dropdown-Element oder ein Optionsfeld auswählt.
* **Ist initialisiert (Ereignis):** Gibt „true“ zurück, wenn ein Formularobjekt im Browser dargestellt wird.
* **Wird geändert (Ereignis):** Gibt „true“ zurück, wenn der Benutzer den eingegebenen Wert oder die ausgewählte Option für ein Formularobjekt ändert.

## Verfügbare Typen von Regeln im Regeleditor {#available-rule-types-in-rule-editor}

Der Regeleditor bietet eine Reihe vordefinierter Regeltypen, mit denen Sie Regeln schreiben können. Im Folgenden werden die einzelnen Regeltypen detailliert dargestellt. Weitere Informationen zum Erstellen von Regeln im Regeleditor finden Sie unter [Regeln schreiben](#write-rules).

### Wenn {#when}

Der **Wenn**-Regeltyp nutzt das Konstrukt **Bedingung-Aktion-Alternative Aktion**, in manchen Fällen auch nur das Konstrukt **Bedingung-Aktion**. Für diesen Regeltyp geben Sie zunächst eine auszuwertende Bedingung an und dann eine Aktion, die ausgelöst werden soll, wenn die Bedingung erfüllt ist (`True`). Bei Einsatz der Wenn-Regel können Sie mehrere UND- und ODER-Operatoren verwenden, um [verschachtelte Ausdrücke](#nestedexpressions) zu erstellen.

Mit dem Wenn-Regeltyp können Sie eine Bedingung für ein Formularobjekt auswerten und Aktionen für ein oder mehrere Objekte ausführen.

Einfach ausgedrückt: Eine typische Wenn-Regel ist wie folgt aufgebaut:

```bash
When on Object A:

(Condition 1 AND Condition 2 OR Condition 3) is TRUE;

Then, do the following:

Action 2 on Object B;  
AND  
Action 3 on Object C;
```

Beim Erstellen einer Regel für Komponenten mit mehreren Werten (z. B. Optionsfelder oder Listen) werden die Optionen automatisch abgerufen und dem Regelersteller zur Verfügung gestellt. Sie müssen die Optionswerte nicht erneut eingeben.

Eine Liste hat beispielsweise vier Optionen: Rot, Blau, Grün und Gelb. Beim Erstellen der Regel werden die Optionen (Optionsfelder) automatisch abgerufen und dem Regelersteller wie folgt zur Verfügung gestellt:

![multivaluefcdisplayOptions](assets/multivaluefcdisplaysoptions.png)

Beim Schreiben der Wenn-Regel können Sie die Aktion „Wert löschen von“ auslösen. Die Aktion „Wert löschen von“ löscht den Wert des angegebenen Objekts. Mit „Wert löschen von“ als Option in der Wenn-Anweisung können Sie komplexe Bedingungen mit mehreren Feldern erstellen.

![clearvalue](assets/clearvalueof.png)

**Ausblenden**: Blendet das angegebene Objekt aus.

**Anzeigen**: Blendet das angegebene Objekt ein.

**Aktivieren**: Aktiviert das angegebene Objekt.

**Deaktivieren**: Deaktiviert das angegebene Objekt.

**Service aufrufen** Ruft einen Service auf, der in einem Formulardatenmodell konfiguriert ist. Wenn Sie den Vorgang „Service aufrufen“ wählen, wird ein Feld angezeigt. Beim Tippen auf das Feld werden alle Dienste angezeigt, die in allen Formulardatenmodellen auf Ihrer AEM konfiguriert sind. Bei der Auswahl eines Formulardatenmodell-Services erscheinen zusätzliche Felder, in denen Sie Formularobjekte mit Ein- und Ausgabeparametern für den angegebenen Service zuordnen können. Siehe Beispielregel für den Aufruf von Formulardatenmodell-Services.

Zusätzlich zum Formulardatenmodelldienst können Sie eine direkte WSDL-URL angeben, um einen Webdienst aufzurufen. Ein Formulardatenmodelldienst bietet jedoch viele Vorteile und den empfohlenen Ansatz zum Aufrufen eines Dienstes.

Weitere Informationen zum Konfigurieren von Services im Formulardatenmodell finden Sie unter [Datenintegration für AEM Forms](/help/forms/using/data-integration.md).

**Wert festlegen**: Berechnet den Wert des angegebenen Objekts und legt ihn fest. Als Objektwert können Sie eine Zeichenfolge, den Wert eines anderen Objekts, den mithilfe eines mathematischem Ausdrucks oder einer Funktion berechneten Wert oder den Wert einer Eigenschaft eines Objekts oder den Ausgabewert von einem konfigurierten Formulardatenmodell-Service festlegen. Wenn Sie die Option „Webservice“ wählen, werden alle in allen Formulardatenmodellen konfigurierten Services auf Ihrer AEM-Instanz angezeigt. Bei der Auswahl eines Formulardatenmodell-Service erscheinen zusätzliche Felder, in denen Sie Formularobjekte mit Ein- und Ausgabeparametern für den angegebenen Service zuordnen können.

Weitere Informationen zum Konfigurieren von Services im Formulardatenmodell finden Sie unter [Datenintegration für AEM Forms](/help/forms/using/data-integration.md).

**Eigenschaft festlegen** Legt den Wert einer Eigenschaft des angegebenen Objekts fest.

**Wert löschen von**: Löscht den Wert des angegebenen Objekts.

**Fokus festlegen**: Legt den Fokus auf das angegebene Objekt.

**Formular speichern**: Speichert das Formular.

**Formulare senden**: Sendet das Formular.

**Formular zurücksetzen**: Setzt das Formular zurück.

**Formular validieren**: Überprüft das Formular.

**Instanz hinzufügen**: Fügt eine Instanz des angegebenen wiederholbaren Bereichs oder der Tabellenzeile hinzu.

**Instanz entfernen**: Entfernt eine Instanz des angegebenen wiederholbaren Bereichs oder der Tabellenzeile.

### Wert festlegen {#set-value-of}

Regeln vom Typ **[!UICONTROL Wert festlegen]** ermöglichen es, den Wert eines Formularobjekts abhängig davon festzulegen, ob die angegebene Bedingung erfüllt ist oder nicht. Als Wert kann der Wert eines anderen Objekts, ein Literal-String, ein aus einem mathematischen Ausdruck oder einer Funktion abgeleiteter Wert oder der Wert einer Eigenschaft eines anderen Objekts oder die Ausgabe eines Formulardatenmodelldiensts sein. In ähnlicher Weise können Sie auf eine Bedingung bei Komponenten, Zeichenfolgen, Eigenschaften oder Werten prüfen, die von Funktionen oder mathematischen Ausdrücken abgeleitet wurden.

Beachten Sie, dass der Regeltyp Wert einstellen nicht für alle Formularobjekte wie Bereiche und Symbolleisten-Schaltflächen verfügbar ist. Eine standardmäßige Regel vom Typ „Wert festlegen“ hat die folgende Struktur:

Wert von Objekt A festlegen auf:

(Zeichenfolge ABC) ODER\
(Objekteigenschaft X des Objekts C) ODER\
(Wert aus einer Funktion) ODER\
(Wert aus einem mathematischen Ausdruck) ODER\
(Ausgabewert eines Datenmodelldienstes oder Webdienstes);

When (optional):

(Bedingung 1 UND Bedingung 2 UND Bedingung 3) TRUE zurückgibt;

Im folgenden Beispiel wird der Wert im Feld `dependentid` als Eingabe genommen und der Wert des Feldes `Relation` auf die Ausgabe des Arguments `Relation` des Formulardatenmodell-Service `getDependent` festgelegt.

![set-value-web-service](assets/set-value-web-service.png)

Beispiel einer Regel zum Festlegen eines Werts mit dem Formulardatenmodelldienst

>[!NOTE]
>
>Darüber hinaus können Sie mithilfe der Regel Wert einstellen alle Werte in einer Dropdown-Listenkomponente aus der Ausgabe eines Formulardatenmodelldienstes oder eines Webdiensts ausfüllen. Stellen Sie jedoch sicher, dass das von Ihnen ausgewählte Ausgabeargument einen Array-Typ aufweist. Alle in einem Array zurückgegebenen Werte werden in der angegebenen Dropdown-Liste verfügbar.

### Anzeigen {#show}

Mithilfe des Regeltyps **Anzeigen** können Sie eine Regel schreiben, die ein Formularobjekt je nachdem, ob eine Bedingung erfüllt ist oder nicht, anzeigt oder ausblendet. Der Regeltyp „Anzeigen“ löst auch die Aktion „Ausblenden“ aus, falls die Bedingung nicht erfüllt ist oder `False` zurückgibt.

Eine typische Regel vom Typ „Anzeigen“ ist wie folgt strukturiert:

`Show Object A;`

`When:`

`(Condition 1 OR Condition 2 OR Condition 3) is TRUE;`

`Else:`

`Hide Object A;`

### Ausblenden {#hide}

Regeln vom Typ **Ausblenden** können ähnlich wie Regeln vom Typ „Anzeigen“ dazu verwendet werden, Formularobjekte je nachdem, ob eine Bedingung erfüllt ist oder nicht, anzuzeigen oder auszublenden. Der Regeltyp „Ausblenden“ löst auch die Aktion „Anzeigen“ aus, falls die Bedingung nicht erfüllt ist oder `False` zurückgibt.

Eine typische Regel vom Typ „Ausblenden“ ist wie folgt strukturiert:

`Hide Object A;`

`When:`

`(Condition 1 AND Condition 2 AND Condition 3) is TRUE;`

`Else:`

`Show Object A;`

### Aktivieren {#enable}

Mithilfe des Regeltyps **Aktivieren** können Sie ein Formularobjekt in Abhängigkeit davon aktivieren oder deaktivieren, ob eine Bedingung erfüllt ist oder nicht. Der Regeltyp „Aktivieren“ löst auch die Aktion „Deaktivieren“ aus, falls die Bedingung nicht erfüllt ist oder `False` zurückgibt.

Eine typische Regel vom Typ „Aktivieren“ ist wie folgt strukturiert:

`Enable Object A;`

`When:`

`(Condition 1 AND Condition 2 AND Condition 3) is TRUE;`

`Else:`

`Disable Object A;`

### Deaktivieren {#disable}

Regeln vom Typ **Deaktivieren** können ähnlich wie Regeln vom Typ „Aktivieren“ dazu verwendet werden, Formularobjekte in Abhängigkeit davon, ob eine Bedingung erfüllt ist oder nicht, zu aktivieren oder zu deaktivieren. Der Regeltyp „Deaktivieren“ löst auch die Aktion „Aktivieren“ aus, falls die Bedingung nicht erfüllt ist oder `False` zurückgibt.

Eine typische Regel vom Typ „Deaktivieren“ ist wie folgt strukturiert:

`Disable Object A;`

`When:`

`(Condition 1 OR Condition 2 OR Condition 3) is TRUE;`

`Else:`

`Enable Object A;`

### Validieren {#validate}

Regeln vom Typ **Validieren** überprüfen den Wert in einem Feld mithilfe eines Ausdrucks. So können Sie beispielsweise einen Ausdruck erstellen, der ein Textfeld zur Eingabe eines Namens daraufhin überprüft, dass dort keine Sonderzeichen oder Zahlen eingegeben wurden.

Eine typische Regel vom Typ „Validieren“ ist wie folgt strukturiert:

`Validate Object A;`

`Using:`

`(Expression 1 AND Expression 2 AND Expression 3) is TRUE;`

>[!NOTE]
>
>Wenn der angegebene Wert nicht der Validierungsregel entspricht, können Sie eine Validierungsmeldung für den Benutzer anzeigen lassen. Sie können die Meldung im Feld **[!UICONTROL Skriptüberprüfungsmeldung]** in den Komponenteneigenschaften in der Seitenleiste angeben.

![script-validation](assets/script-validation.png)

## Grundlegendes zur Benutzeroberfläche des Regeleditors {#understanding-the-rule-editor-user-interface}

Der Regeleditor bietet eine umfangreiche und dennoch einfache Benutzeroberfläche zum Erstellen und Verwalten von Regeln. Sie können die Benutzeroberfläche des Regeleditors in einem adaptiven Formular im Authoring-Modus starten.

So starten Sie die Benutzeroberfläche des Regeleditors:

1. Öffnen Sie ein adaptives Formular im Authoring-Modus.
1. Tippen Sie auf das Formularobjekt, für das Sie eine Regel erstellen möchten, und tippen Sie in der Symbolleiste „Komponente“ auf ![edit-rules](assets/edit-rules.png). Die Benutzeroberfläche des Regeleditors wird angezeigt.

   ![create-rules](assets/create-rules.png)

   Alle vorhandenen Regeln für die ausgewählten Formularobjekte werden in dieser Ansicht aufgelistet. Weitere Informationen zum Verwalten vorhandener Regeln finden Sie unter [Verwalten von Regeln](/help/forms/using/rule-editor.md#p-manage-rules-p).

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um eine neue Regel zu erstellen. Wenn Sie den Regeleditor zum ersten Mal starten, wird standardmäßig der Visual Editor der Regeleditor-Benutzeroberfläche geöffnet.
   ![Benutzeroberfläche des Regeleditors](assets/rule-editor-ui.png)

   [Klicken Sie zum Vergrößern auf](assets/rule-editor-ui-1.png)
 
Im Folgenden werden die einzelnen Komponenten der Benutzeroberfläche des Regeleditors im Detail vorgestellt.

### A. Ansicht „Komponente und Regel“ {#a-component-rule-display}

Zeigt den Titel des adaptiven Formularobjekts an, über das Sie den Regeleditor gestartet haben, und den derzeit ausgewählten Regeltyp. Im oben gezeigten Beispiel wurde der Regeleditor über ein adaptives Formularobjekt namens „Salary“ gestartet und der Wenn-Regeltyp ist ausgewählt.

### B. Formularobjekte und Funktionen {#b-form-objects-and-functions-br}

Im linken Bereich der Benutzeroberfläche des Regeleditors stehen zwei Registerkarten zur Verfügung: **[!UICONTROL Formularobjekte]** und **[!UICONTROL Funktionen]**.

Die Registerkarte &quot;Formularobjekte&quot;zeigt eine hierarchische Ansicht aller Objekte im adaptiven Formular an. Angezeigt werden Titel und Typ der Objekte. Wenn Sie eine Regel erstellen, können Sie Formularobjekte in den Regeleditor ziehen und dort ablegen. Wenn Sie beim Erstellen oder Bearbeiten einer Regel ein Objekt oder eine Funktion in einen Platzhalter ziehen, übernimmt dieser Platzhalter automatisch den entsprechenden Wertetyp.

Die Formularobjekte, auf die eine oder mehrere gültige Regeln angewendet wurden, sind mit einem grünen Punkt markiert. Wenn eine der auf ein Formularobjekt angewendeten Regeln ungültig ist, wird das Formularobjekt mit einem gelben Punkt markiert.

Die Registerkarte „Funktionen“ enthält eine Reihe integrierter Funktionen (z. B. „Summe von“, „Minimum von“, „Maximum von“, „Durchschnitt von“, „Anzahl von“ und „Formular validieren“). Sie können diese Funktionen verwenden, um Werte in wiederholbaren Bereichen und Tabellenzeilen zu berechnen und sie beim Erstellen von Regeln in den Aktions- und Bedingungsanweisungen zu verwenden. Sie können jedoch auch [benutzerdefinierte Funktionen](/help/forms/using/rule-editor.md#custom-functions) erstellen.

![Die Registerkarte „Funktionen“](assets/functions.png)

>[!NOTE]
>
>Sie können auf den Registerkarten „Formularobjekte“ und „Funktionen“ eine Textsuche nach den Namen und Titeln von Objekten und Funktionen durchführen.

In der linken Struktur der Formularobjekte können Sie auf die Formularobjekte tippen, um die Regeln anzuzeigen, die auf die einzelnen Objekte angewendet werden. Sie können nicht nur durch die Regeln der verschiedenen Formularobjekte navigieren, sondern auch Regeln zwischen den Formularobjekten kopieren und einfügen. Weitere Informationen finden Sie unter [Regeln kopieren und einfügen](#copy-paste-rules).

### C. Umschalten zwischen Formularobjekten und Funktionen {#c-form-objects-and-functions-toggle-br}

Durch Tippen auf die Schaltfläche schalten Sie zwischen den Bereichen für Formularobjekte und Funktionen um.

### D. Visueller Regeleditor {#d-visual-rule-editor}

Der visuelle Regeleditor ist der Bereich im Visual Editor-Modus der Benutzeroberfläche des Regeleditors, in dem Sie Regeln schreiben. Damit können Sie einen Regeltyp auswählen und dementsprechend Bedingungen und Aktionen definieren. Beim Definieren von Bedingungen und Aktionen in einer Regel können Sie Formularobjekte und -funktionen aus dem Bereich &quot;Formularobjekte und -funktionen&quot;ziehen und dort ablegen.

Weitere Informationen zur Verwendung des visuellen Regeleditors finden Sie unter [Regeln schreiben](#write-rules).

### E. Umschalter zwischen Visual Code-Editoren {#e-visual-code-editors-switcher}

Benutzer in der Gruppe forms-power-users können auf den Code-Editor zugreifen. Für andere Benutzer ist der Code-Editor nicht verfügbar. Mithilfe des Umschalters rechts oberhalb des Regeleditors können Sie zwischen Visual Editor- und Codeeditormodus für den Regeleditor wechseln, wenn Sie dazu berechtigt sind. Wenn Sie den Regeleditor zum ersten Mal starten, wird er im Visual Editor-Modus geöffnet. Sie können Regeln im Visual Editor-Modus schreiben oder in den Code-Editor-Modus wechseln, um ein Regelskript zu schreiben. Beachten Sie jedoch, dass Sie beim Ändern einer Regel oder Schreiben einer Regel im Code-Editor nicht zum Visual Editor für diese Regel wechseln können, es sei denn, Sie löschen den Code-Editor.

AEM Forms verfolgt den Regeleditormodus, den Sie zuletzt zum Erstellen einer Regel verwendet haben. Wenn Sie den Regeleditor das nächste Mal starten, wird er in diesem Modus geöffnet. Sie können jedoch auch einen Standardmodus konfigurieren, um den Regeleditor im angegebenen Modus zu öffnen. Gehen Sie dazu wie folgt vor:

1. Rufen Sie AEM Webkonsole unter https:// auf.[Host]:[port]/system/console/configMgr.
1. Zum Bearbeiten klicken Sie auf **[!UICONTROL Konfiguration von adaptiven Formularen und Web-Kanälen für interaktive Kommunikation]**.
1. Wählen Sie **[!UICONTROL Visual Editor]** oder **[!UICONTROL Codeeditor]** aus der Dropdownliste für den **[!UICONTROL Standardmodus für den Regeleditor]**.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

### F. Schaltflächen &quot;Fertig&quot;und &quot;Abbrechen&quot; {#f-done-and-cancel-buttons}

Die Schaltfläche **[!UICONTROL Fertig]** wird verwendet, um eine Regel zu speichern. Sie können eine unvollständige Regel speichern. Unvollständige Elemente sind jedoch ungültig und werden nicht ausgeführt. Gespeicherte Regeln für ein Formularobjekt werden aufgelistet, wenn Sie den Regeleditor das nächste Mal von demselben Formularobjekt aus starten. In dieser Ansicht können Sie vorhandene Regeln verwalten. Weitere Informationen finden Sie unter [Regeln verwalten](#manage-rules).

Die **[!UICONTROL Abbrechen]** -Schaltfläche verwirft alle Änderungen, die Sie an einer Regel vorgenommen haben, und schließt den Regeleditor.

## Regeln schreiben {#write-rules}

Sie können Regeln mit dem visuellen Regeleditor oder dem Code-Editor schreiben. Wenn Sie den Regeleditor zum ersten Mal starten, wird er im Visual Editor-Modus geöffnet. Sie können zum Code-Editormodus wechseln und Regeln schreiben. Beachten Sie jedoch, dass Sie beim Schreiben oder Ändern einer Regel im Code-Editor nur dann zum Visual Editor für diese Regel wechseln können, wenn Sie den Code-Editor löschen. Wenn Sie den Regeleditor das nächste Mal starten, wird er in dem Modus geöffnet, mit dem Sie zuletzt die Regel erstellt haben.

Sehen wir uns zunächst an, wie Regeln mit dem Visual Editor geschrieben werden.

### Verwenden des Visual Editor {#using-visual-editor}

Anhand des folgenden Beispielformulars soll das Erstellen von Regeln im visuellen Editor verständlich gemacht werden.

![create-rule-example](assets/create-rule-example.png)

Im Abschnitt &quot;Kreditanforderungen&quot;im Beispielformular für einen Kreditantrag müssen Antragsteller ihren Familienstand, ihr Gehalt und, falls verheiratet, das Gehalt ihres Ehepartners angeben. Basierend auf den Benutzereingaben berechnet die Regel den Kreditanspruchsbetrag und wird im Feld Kreditanspruch angezeigt. Wenden Sie die folgenden Regeln an, um das Szenario zu implementieren:

* Das Feld für das Gehalt des Partners/der Partnerin wird nur angezeigt, wenn der Familienstand Verheiratet ist.
* Der Kreditanspruchsbetrag beträgt 50 % des Gesamtgehalts.

Führen Sie die folgenden Schritte aus, um Regeln zu schreiben:

1. Schreiben Sie zuerst die Regel, mit der die Sichtbarkeit des Felds „Gehalt des Partners“ entsprechend der vom Benutzer über das Optionsfeld „Familienstand“ gewählten Option gesteuert wird.

   Öffnen Sie das Kreditantragsformular im Autorenmodus. Tippen Sie auf die Komponente **Familienstand** und dann auf ![edit-rules](assets/edit-rules.png). Tippen Sie als Nächstes auf **[!UICONTROL Erstellen]**, um den Regeleditor zu starten.

   ![write-rules-visual-editor-1](assets/write-rules-visual-editor-1.png)

   Wenn Sie den Regeleditor starten, ist die Wenn -Regel standardmäßig ausgewählt. Außerdem wird das Formularobjekt (in diesem Fall Familienstand), von dem aus Sie den Regeleditor gestartet haben, in der Wenn-Anweisung angegeben.

   Sie können zwar das ausgewählte Objekt nicht bearbeiten oder ändern, es ist jedoch möglich, über die Dropdown-Liste für Regeln einen anderen Regeltyp wählen (siehe unten). Wenn Sie eine Regel für ein anderes Objekt erstellen möchten, tippen Sie auf Abbrechen , um den Regeleditor zu beenden und erneut über das gewünschte Formularobjekt zu starten.

1. Tippen Sie auf die Dropdown-Liste **[!UICONTROL Status auswählen]** und wählen Sie **[!UICONTROL Ist gleich]** aus. Das Feld **[!UICONTROL Eine Zeichenfolge eingeben]** wird angezeigt.

   ![write-rules-visual-editor-2](assets/write-rules-visual-editor-2.png)

   In dem Optionsfeld „Familienstand“ werden den Optionen **Verheiratet** und **Ledig** die Werte **0** bzw. **1** zugewiesen. Sie können die zugewiesenen Werte auf der Registerkarte „Titel“ des Dialogfelds zum Bearbeiten des Optionsfelds überprüfen, wie unten gezeigt.

   ![Optionsfeldwerte im Regeleditor](assets/radio-button-values.png)

1. Geben Sie in der Regel im Feld **Eine Zeichenfolge eingeben** den Wert **0** an.

   ![write-rules-visual-editor-4](assets/write-rules-visual-editor-4.png)

   Sie haben die Bedingung als `When Marital Status is equal to Married` definiert. Definieren Sie anschließend die Aktion, die ausgeführt werden soll, wenn diese Bedingung &quot;True&quot;lautet.

1. Wählen Sie für die Dann-Anweisung die Option **[!UICONTROL Anzeigen]** aus der Dropdown-Liste **[!UICONTROL Aktion auswählen]**.

   ![write-rules-visual-editor-5](assets/write-rules-visual-editor-5.png)

1. Ziehen Sie das Feld **Gehalt des Partners** aus der Registerkarte „Formularobjekte“ in das Feld **Legen Sie das Objekt ab oder wählen Sie hier aus**. Stattdessen können Sie auch auf das Feld **Legen Sie das Objekt ab oder wählen Sie hier aus** tippen und das Feld **Gehalt des Partners** aus dem Popupmenü wählen, in dem sämtliche Formularobjekte im Formular aufgeführt sind.

   ![write-rules-visual-editor-6](assets/write-rules-visual-editor-6.png)

   Die Regel wird im Regeleditor wie folgt angezeigt.

   ![write-rules-visual-editor-7](assets/write-rules-visual-editor-7.png)

   Tippen Sie auf **Fertig**, um die Regel zu speichern.

1. Wiederholen Sie die Schritte 1 bis 5, um eine weitere Regel zu definieren, mit der das Feld für das Gehalt des Partners/der Partnerin ausgeblendet wird, wenn der Familienstand Single ist. Die Regel wird im Regeleditor wie folgt angezeigt.

   ![write-rules-visual-editor-8](assets/write-rules-visual-editor-8.png)

   >[!NOTE]
   >
   >Alternativ zu diesem Verfahren können Sie dieses Verhalten auch implementieren, indem Sie für das Feld „Gehalt des Partners“ lediglich eine Regel vom Typ „Anzeigen“ anstelle zweier Wenn-Regeln für das Feld „Familienstand“ erstellen.

   ![write-rules-visual-editor-9](assets/write-rules-visual-editor-9.png)

1. Als Nächstes erstellen Sie eine Regel für die Berechnung des Kreditanspruchsbetrags (50 % des Gesamtgehalts) und zur Anzeige des Betrags im Feld für den Kreditanspruch. Erstellen Sie dazu **Wert einstellen von** Regeln für das Feld &quot;Kreditanspruch&quot;.

   Klicken Sie im Autorenmodus auf das Feld **[!UICONTROL Kreditanspruch]** und dann auf ![edit-rules](assets/edit-rules.png). Tippen Sie als Nächstes auf **[!UICONTROL Erstellen]**, um den Regeleditor zu starten.

1. Wählen Sie in der Dropdown-Liste „Regeln“ die Regel **[!UICONTROL Wert festlegen]** aus.

   ![write-rules-visual-editor-10](assets/write-rules-visual-editor-10.png)

1. Tippen Sie auf **[!UICONTROL Option auswählen]** und wählen Sie **[!UICONTROL Mathematischer Ausdruck]** aus. Ein Feld, in dem Sie mathematische Ausdrücke schreiben können, wird geöffnet.

   ![write-rules-visual-editor-11](assets/write-rules-visual-editor-11.png)

1. Im Ausdrucksfeld:

   * Wählen Sie die Registerkarte Forms-Objekt aus oder ziehen Sie sie per Drag-and-Drop aus der Registerkarte **Gehalt** im ersten Feld **Objekt ablegen oder hier auswählen** -Feld.
   * Auswählen **Plus** von **Operator auswählen** -Feld.
   * Wählen Sie das Feld **Gehalt des Partners** auf der Registerkarte „Formularobjekt“ aus oder ziehen Sie es in das zweite Feld **Legen Sie das Objekt ab oder wählen Sie hier aus** und legen Sie es dort ab.

   ![write-rules-visual-editor-12](assets/write-rules-visual-editor-12.png)

1. Tippen Sie als Nächstes in den hervorgehobenen Bereich um das Ausdrucksfeld und tippen Sie dann auf **Ausdruck erweitern**.

   ![write-rules-visual-editor-13](assets/write-rules-visual-editor-13.png)

   Wählen Sie im Feld erweiterter Ausdruck die Option **dividiert durch** von **Operator auswählen** und **Zahl** von **Option auswählen** -Feld. Geben Sie **2** in das Zahlenfeld ein.

   ![write-rules-visual-editor-14](assets/write-rules-visual-editor-14.png)

   >[!NOTE]
   >
   >Sie können komplexe Ausdrücke mithilfe von Komponenten, Funktionen, mathematischen Ausdrücken und Eigenschaftswerten aus dem Feld Option auswählen erstellen.

   Als Nächstes erstellen Sie eine Bedingung, die bei der Rückgabe von True den Ausdruck ausführt.

1. Tippen Sie auf **Bedingung hinzufügen**, um eine Wenn-Anweisung hinzuzufügen.

   ![write-rules-visual-editor-15](assets/write-rules-visual-editor-15.png)

   In der When-Anweisung:

   * Wählen Sie die Registerkarte Forms-Objekt aus oder ziehen Sie sie per Drag-and-Drop aus der Registerkarte **Familienstand** im ersten Feld **Objekt ablegen oder hier auswählen** -Feld.
   * Wählen Sie i **ist gleich** von **Operator auswählen** -Feld.
   * Wählen Sie in dem anderen Feld **Legen Sie das Objekt ab oder wählen Sie hier aus** den Eintrag „String“ (Zeichenfolge) aus und geben Sie **Verheiratet** in das Feld **Geben Sie eine Zeichenfolge ein** ein.

   Die Regel wird schließlich wie folgt im Regeleditor angezeigt.  ![write-rules-visual-editor-16](assets/write-rules-visual-editor-16.png)

   Tippen Sie auf **Fertig**, um die Regel zu speichern.

1. Folgen Sie wiederum Schritt 7 bis 12, um eine andere Regel zu definieren, mit deren Hilfe der Kreditanspruch berechnet wird, sofern der Familienstand „Ledig“ ist. Die Regel wird im Regeleditor wie folgt angezeigt.

   ![write-rules-visual-editor-17](assets/write-rules-visual-editor-17.png)

>[!NOTE]
>
>Alternativ können Sie die Regel Wert einstellen verwenden, um die Kreditanspruchsberechtigung in der Wenn-Regel zu berechnen, die Sie erstellt haben, um das Feld für das Gehalt des Partners/der Partnerin ein- und auszublenden. Die resultierende kombinierte Regel, bei der der Familienstand &quot;Ledig&quot;lautet, wird im Regeleditor wie folgt angezeigt:
>
>Auf ähnliche Weise können Sie eine kombinierte Regel erstellen, um die Sichtbarkeit des Felds für das Gehalt des Partners oder der Partnerin zu steuern und die Kreditanspruchsberechtigung zu berechnen, wenn der Familienstand Verheiratet ist.

![write-rules-visual-editor-18](assets/write-rules-visual-editor-18.png)

### Verwenden des Code-Editors {#using-code-editor}

Benutzer, die zur Gruppe der Formular-Power-User hinzugefügt wurden, können den Code-Editor verwenden. Der Regeleditor generiert automatisch den JavaScript-Code für alle Regeln, die Sie mit dem Visual Editor erstellen. Sie können vom Visual Editor zum Code-Editor wechseln, um den generierten Code anzuzeigen. Wenn Sie jedoch den Regel-Code im Code-Editor ändern, können Sie nicht zum Visual Editor zurückkehren. Wenn Sie Regeln lieber im Code-Editor als im Visual Editor schreiben möchten, können Sie Regeln im Code-Editor neu schreiben. Der Umschalter für Visual Code-Editoren hilft Ihnen beim Umschalten zwischen den beiden Modi.

Das im Code-Editor verwendete JavaScript ist die Ausdruckssprache für adaptive Formulare. Alle Ausdrücke sind gültige JavaScript-Ausdrücke und verwenden Skriptmodell-APIs für adaptive Formulare. Diese Ausdrücke geben Werte bestimmter Typen zurück. Eine vollständige Liste der Klassen, Ereignisse, Objekte und öffentlichen APIs für adaptive Formulare finden Sie unter [JavaScript-Bibliotheks-API-Referenz für adaptive Formulare](https://helpx.adobe.com/de/experience-manager/6-4/forms/javascript-api/index.html).

Weitere Informationen zu Richtlinien zum Schreiben von Regeln im Code-Editor finden Sie unter [Adaptive Formularausdrücke](/help/forms/using/adaptive-form-expressions.md).

Beim Schreiben von JavaScript-Code im Regeleditor helfen Ihnen die folgenden visuellen Hinweise bei der Struktur und Syntax:

* Syntaxhervorhebung
* Automatischer Einzug
* Hinweise und Vorschläge für Formularobjekte, Funktionen und deren Eigenschaften
* Automatisches Ausfüllen der Namen von Formularkomponenten und gängigen JavaScript-Funktionen

![javascriptruleeditor](assets/javascriptruleeditor.png)

#### Benutzerdefinierte Funktionen im Regeleditor {#custom-functions}

Zusätzlich zu den vordefinierten Funktionen wie *Summe von, *die unter &quot;Funktionenausgabe&quot;aufgeführt sind, können Sie benutzerdefinierte Funktionen schreiben, die Sie häufig benötigen. Stellen Sie sicher, dass für die Funktion, die Sie schreiben, ein `jsdoc` vorhanden ist.

Dieses dazugehörige `jsdoc` ist aus den folgenden Gründen erforderlich:

* Wenn Sie benutzerdefinierte Konfigurationen und Beschreibungen verwenden möchten.
* Da Funktionen in `JavaScript,` auf unterschiedliche Weise deklariert werden können und Sie mithilfe der Kommentare den Überblick über die Funktionen behalten.

Weitere Informationen finden Sie unter [usejsdoc.org](https://usejsdoc.org/).

Unterstützte `jsdoc`-Tags:

* **Privat**

   Syntax: `@private`

   Eine private Funktion ist nicht als benutzerdefinierte Funktion enthalten.

* **Name**

   Syntax: `@name funcName <Function Name>`

   Alternativ `,` Sie können Folgendes verwenden: `@function funcName <Function Name>` **oder** `@func` `funcName <Function Name>`.

   `funcName` ist der Name der Funktion (Leerzeichen sind nicht zulässig).

   `<Function Name>` ist der Anzeigename der Funktion.

* **Mitglied**

   Syntax: `@memberof namespace`

   Fügt der Funktion einen Namespace an.

* **Parameter**

   Syntax: `@param {type} name <Parameter Description>`

   Alternativ können Sie Folgendes verwenden: `@argument` `{type} name <Parameter Description>` **oder** `@arg` `{type}` `name <Parameter Description>`.

   Zeigt die von der Funktion verwendeten Parameter an. In einer Funktion können mehrere Parameter-Tags vorhanden sein (je ein Tag für jeden Parameter in der Reihenfolge ihres Auftretens).

   `{type}` gibt den Parametertyp an. Zulässige Parametertypen sind:

   1. String (Zeichenfolge)
   1. Number (Zahl)
   1. Boolean (Boolesch)

   Alle anderen Parametertypen fallen in eine der oben genannten Kategorien. Keine wird nicht unterstützt. Achten Sie darauf, einen der oben genannten Typen zu wählen. Bei Typen wird nicht zwischen Groß- und Kleinschreibung unterschieden. Leerzeichen sind im Parameter `name` unzulässig. `<Parameter Descrption>` 

* **Rückgabetyp**

   Syntax: `@return {type}`

   Alternativ können Sie `@returns {type}`.

   Fügt Informationen über die Funktion hinzu (z. B. ihren Zweck).


   Die Zeichenfolge „{type}“ gibt den Rückgabetyp der Funktion an. Zulässige Rückgabetypen sind:

   1. String (Zeichenfolge)
   1. Number (Zahl)
   1. Boolean (Boolesch)
   1. Datum
   1. array

   Alle anderen Rückgabetypen werden in eine der oben genannten Kategorien eingeordnet. Keine wird nicht unterstützt. Achten Sie darauf, einen der oben genannten Typen zu wählen. Bei Rückgabetypen wird nicht zwischen Groß- und Kleinschreibung unterschieden.

>[!NOTE]
>
>Kommentare vor benutzerdefinierten Funktionen werden für die Zusammenfassung verwendet. Die Zusammenfassung kann sich auf mehrere Zeilen erstrecken, bis ein Tag gefunden wird. Beschränken Sie die Größe für eine kurze Beschreibung im Regel-Builder auf eine einzelne.

**Hinzufügen einer benutzerdefinierten Funktion**

Sie möchten beispielsweise eine benutzerdefinierte Funktion hinzufügen, mit der der Bereich eines Quadrats berechnet wird. Die Seitenlänge ist die Benutzereingabe für die benutzerdefinierte Funktion, die mithilfe eines numerischen Felds in Ihrem Formular akzeptiert wird. Die berechnete Ausgabe wird in einem anderen numerischen Feld im Formular angezeigt. Um eine benutzerdefinierte Funktion hinzuzufügen, müssen Sie zunächst eine Client-Bibliothek erstellen und sie dann zum CRX-Repository hinzufügen.

Führen Sie die folgenden Schritte aus, um eine Client-Bibliothek zu erstellen und sie zum CRX-Repository hinzuzufügen.

1. Erstellen Sie eine Client-Bibliothek. Weitere Informationen finden Sie unter [Verwenden Client-seitiger Bibliotheken](/help/sites-developing/clientlibs.md).
1. Fügen Sie in CRXDE die Eigenschaft `categories` mit dem Wert `customfunction` (vom Typ „String“ (Zeichenfolge)) zum Ordner `clientlib` hinzu.

   >[!NOTE]
   >
   >`customfunction` ist eine Beispielkategorie. Sie können einen beliebigen Namen für die Kategorie wählen, die Sie im Ordner `clientlib`erstellen.

Nachdem Sie die Client-Bibliothek im CRX-Repository hinzugefügt haben, verwenden Sie sie in Ihrem adaptiven Formular. Sie ermöglicht die Verwendung der benutzerdefinierten Funktion als Regel im Formular. Führen Sie die folgenden Schritte durch, um die Client-Bibliothek dem adaptiven Formular hinzuzufügen:

1. Öffnen Sie das Formular im Bearbeitungsmodus.

   Um ein Formular im Bearbeitungsmodus zu öffnen, wählen Sie das Formular aus und klicken Sie auf **Öffnen**.

1. Wählen Sie im Bearbeitungsmodus eine Komponente aus und tippen Sie anschließend auf ![field-level](assets/field-level.png) > **Container für ein adaptives Formular** und dann auf ![cmppr](assets/cmppr.png).
1. Fügen Sie in der Seitenleiste unter „Name der Client-Bibliothek“ Ihre Client-Bibliothek hinzu. (In diesem Beispiel wäre das `customfunction`.)

   ![Hinzufügen der benutzerdefinierten Funktion zur Client-Bibliothek](assets/clientlib.png)

1. Wählen Sie das numerische Eingabefeld aus und tippen Sie auf ![edit-rules](assets/edit-rules.png), um den Regeleditor zu öffnen.
1. Tippen Sie auf **Regel erstellen**. Erstellen Sie mithilfe der unten gezeigten Optionen eine Regel zum Speichern des Quadratwerts der Eingabe im Ausgabefeld des Formulars.
   [ ![Verwenden von benutzerdefinierten Funktionen zum Erstellen einer Regel](assets/add-custom-rule.png)](assets/add-custom-rule-1.png)Tippen Sie auf **Fertig**. Ihre benutzerdefinierte Funktion wird hinzugefügt.

#### Unterstützte Typen von Funktionsdeklarationen {#function-declaration-supported-types}

**Funktionsanweisung**

```
function area(len) {
    return len*len;
}
```

Diese Funktion wird ohne `jsdoc`-Kommentare eingefügt.

**Funktionsausdruck**

```
var area;
//Some codes later
/** */
area = function(len) {
    return len*len;
};
```

**Funktionsausdruck und -anweisung**

```
var b={};
/** */
b.area = function(len) {
    return len*len;
}
```

**Funktionsdeklaration als Variable**

```
/** */
var x1,
    area = function(len) {
        return len*len;
    },
    x2 =5, x3 =true;
```

Einschränkung: Die benutzerdefinierte Funktion wählt nur die erste Funktionsdeklaration aus der Variablenliste aus, wenn sie zusammen vorhanden ist. Sie können den Funktionsausdruck für jede deklarierte Funktion verwenden.

**Funktionsdeklaration als Objekt**

```
var c = {
    b : {
        /** */
        area : function(len) {
            return len*len;
        }
    }
};
```

>[!NOTE]
>
>Stellen Sie sicher, dass Sie `jsdoc` für jede benutzerdefinierte Funktion verwenden. Obwohl `jsdoc`-Kommentare empfohlen werden, sollten Sie einen leeren `jsdoc`-Kommentar einfügen, um eine Funktion als benutzerdefinierte Funktion zu kennzeichnen. Dies ermöglicht eine standardmäßige Behandlung Ihrer benutzerdefinierten Funktion.

## Verwalten von Regeln {#manage-rules}

Wenn Sie auf das Objekt und dann auf ![edit-rules1](assets/edit-rules1.png) tippen, werden alle vorhandenen Regeln für ein Formularobjekt aufgelistet. Sie können den Titel und eine Vorschau der Regelzusammenfassung anzeigen. Darüber hinaus können Sie über die Benutzeroberfläche die vollständige Regelzusammenfassung erweitern und anzeigen, die Reihenfolge der Regeln ändern, Regeln bearbeiten und Regeln löschen.

![list-rules](assets/list-rules.png)

Sie können die folgenden Aktionen für Regeln ausführen:

* **Anzeigen/Reduzieren**: Die Inhaltsspalte in der Regelliste zeigt den Regelinhalt an. Wenn in der Standardansicht nicht der gesamte Regelinhalt sichtbar ist, tippen Sie auf ![expand-rule-content](assets/expand-rule-content.png), um die Ansicht zu erweitern.

* **Neu anordnen**: Jede neue Regel, die Sie erstellen, wird am unteren Rand der Regelliste gestapelt. Die Regeln werden von oben nach unten ausgeführt. Die Regel oben wird zuerst ausgeführt, gefolgt von anderen Regeln desselben Typs. Wenn beispielsweise die Regeln &quot;Wann&quot;, &quot;Anzeigen&quot;, &quot;Aktivieren&quot;und &quot;Wann&quot;an der ersten, zweiten, dritten und vierten Position oben stehen, wird zuerst die Wenn-Regel am oberen Rand und dann die Wenn-Regel an der vierten Position ausgeführt. Danach werden die Regeln „Anzeigen“ und „Aktivieren“ ausgeführt.

   Sie können die Position einer Regel in der Reihenfolge ändern, indem Sie auf ![sort-rules](assets/sort-rules.png) für die Regel tippen oder die Regel an die gewünschte Stelle in der Liste ziehen und dort ablegen.

* **Bearbeiten**: Zum Bearbeiten einer Regel aktivieren Sie das Kontrollkästchen neben ihrem Titel. Zusätzliche Optionen zum Bearbeiten und Löschen der Regel werden angezeigt. Tippen Sie auf **Bearbeiten**, um die ausgewählte Regel im Regeleditor im Visual Editor- oder im Code-Editormodus zu öffnen. Dies ist davon abhängig, welcher Modus zum Erstellen der Regel verwendet wurde.

* **Löschen**: Zum Löschen einer Regel wählen Sie die Regel aus und tippen Sie dann auf **Löschen**.

* **Aktivieren/Deaktivieren**: Möglicherweise müssen Sie die Verwendung einer Regel vorübergehend aussetzen. Sie können eine oder mehrere Regeln auswählen und in der Aktionssymbolleiste auf Deaktivieren tippen, um sie zu deaktivieren. Wenn eine Regel deaktiviert ist, wird sie zur Laufzeit nicht ausgeführt. Um eine Regel zu aktivieren, die deaktiviert ist, können Sie sie auswählen und in der Aktionssymbolleiste auf Aktivieren tippen. Die Statusspalte der Regel zeigt an, ob die Regel aktiviert oder deaktiviert ist.

![disablerrule](assets/disablerule.png)

## Kopieren und Einfügen von Regeln {#copy-paste-rules}

Sie können eine Regel aus einem Feld kopieren und in andere ähnliche Felder einfügen, um Zeit zu sparen.

Gehen Sie wie folgt vor, um Regeln zu kopieren und einzufügen:

1. Tippen Sie auf das Formularobjekt, von dem Sie eine Regel kopieren möchten, und tippen Sie in der Komponenten-Symbolleiste auf ![Regel bearbeiten](assets/editrule.png). Die Benutzeroberfläche des Regeleditors wird angezeigt, wobei das Formularobjekt ausgewählt ist und die vorhandenen Regeln angezeigt werden.

   ![copyrule](assets/copyrule.png)

   Weitere Informationen zum Verwalten vorhandener Regeln finden Sie unter [Verwalten von Regeln](#manage-rules).

1. Aktivieren Sie das Kontrollkästchen neben dem Regeltitel. Es werden zusätzliche Optionen zur Verwaltung der Regel angezeigt. Tippen Sie auf **Kopieren**.

   ![copyrule2](assets/copyrule2.png)

1. Wählen Sie ein anderes Formularobjekt aus, in das Sie die Regel einfügen möchten, und tippen Sie auf **Einfügen**. Außerdem können Sie die Regel bearbeiten, um Änderungen daran vorzunehmen.

   >[!NOTE]
   >
   >Sie können eine Regel nur dann in ein anderes Formularobjekt einfügen, wenn dieses Formularobjekt das Ereignis der kopierten Regel unterstützt. Beispielsweise unterstützt eine Schaltfläche das Klickereignis. Sie können eine Regel mit einem Klick-Ereignis in eine Schaltfläche, nicht aber in ein Kontrollkästchen einfügen.

1. Tippen Sie auf **Fertig**, um die Regel zu speichern.

## Verschachtelte Ausdrücke {#nestedexpressions}

Mit dem Regeleditor können Sie mehrere UND- und ODER-Operatoren verwenden, um verschachtelte Regeln zu erstellen. Sie können mehrere UND- und ODER-Operatoren in Regeln kombinieren.

Das folgende Beispiel zeigt eine verschachtelte Regel, die dem Benutzer eine Meldung über den Anspruch auf das Sorgerecht für ein Kind anzeigt, wenn die entsprechenden Bedingungen erfüllt sind.

![complexexpression](assets/complexexpression.png)

Sie können Bedingungen innerhalb einer Regel auch mittels Drag-and-Drop ziehen, um sie zu bearbeiten. Tippen Sie auf den Ziehgriff und halten Sie den Mauszeiger auf den Griff (![handle](assets/handle.png)) vor einer Bedingung. Sobald der Zeiger in das Handsymbol umgewandelt wurde, wie unten dargestellt, ziehen Sie die Bedingung an eine beliebige Stelle innerhalb der Regel. Die Regelstruktur ändert sich.

![drag-and-drop](assets/drag-and-drop.png)

## Bedingungen für Datumsausdrücke {#dateexpression}

Im Regeleditor können Sie Vergleiche von Datumsangaben verwenden, um Bedingungen zu erstellen.

Nachfolgend ist eine Beispielbedingung dargestellt, die ein statisches Textobjekt anzeigt, wenn die Hypothek für das Haus bereits abgeschlossen ist, was der Benutzer durch Ausfüllen des Datumsfelds angibt.

Wenn das Datum der Hypothek, das vom Benutzer ausgefüllt wurde, in der Vergangenheit liegt, wird im adaptiven Formular ein Hinweis über die Einkommensberechnung angezeigt. Die folgende Regel vergleicht das Datum, das vom Benutzer eingetragen wurde, mit dem aktuellen Datum. Wenn dieses Datum vor dem aktuellen Datum liegt, zeigt das Formular die Textmeldung (mit der Bezeichnung „Einkommen“) an.

![dateexpressioncondition](assets/dateexpressioncondition.png)

Wenn das eingetragene Datum vor dem aktuellen Datum liegt, zeigt das Formular die Textmeldung (Einkommen) an, wie hier dargestellt:

![dateexpressionconditionmet](assets/dateexpressionconditionmet.png)

## Bedingungen für den Vergleich von Zahlen {#number-comparison-conditions}

Im Regeleditor können Sie Bedingungen erstellen, die zwei Zahlen vergleichen.

Im Folgenden wird eine Beispielbedingung angezeigt, die ein statisches Textobjekt anzeigt, wenn die Anzahl von Monaten, die ein aktueller Benutzer an seiner gegenwärtigen Adresse gewohnt hat, weniger als 36 ist.

![numbercomparisoncondition](assets/numbercomparisoncondition.png)

Wenn der Benutzer angibt, dass er unter seiner derzeitigen Adresse weniger als 36 Monate gewohnt hat, wird im Formular ein Hinweis angezeigt, dass ein zusätzlicher Aufenthaltsnachweis erforderlich ist.

![additionalproofrequent](assets/additionalproofrequested.png)

## Auswirkung des Regeleditors auf vorhandene Skripte {#impact-of-rule-editor-on-existing-scripts}

In AEM Forms-Versionen vor AEM 6.1 Forms Feature Pack 1 schreiben Formularverfasser und -entwickler Ausdrücke auf der Registerkarte &quot;Skripte&quot;des Dialogfelds &quot;Komponente bearbeiten&quot;, um adaptiven Formularen dynamisches Verhalten hinzuzufügen. Die Registerkarte &quot;Skripte&quot;wird jetzt durch den Regeleditor ersetzt.

Alle Skripte oder Ausdrücke, die Sie auf der Registerkarte &quot;Skripte&quot;geschrieben haben, sind im Regeleditor verfügbar. Sie können sie zwar nicht im Visual Editor anzeigen oder bearbeiten, aber wenn Sie Teil der Gruppe der Formular-Hauptbenutzer sind, können Sie Skripte im Code-Editor bearbeiten.

## Beispielregeln {#example}

### Formulardatenmodelldienst aufrufen {#invoke}

Stellen Sie sich einen Webservice `GetInterestRates` vor, der den Darlehensbetrag, die Beschäftigungsdauer und die Kreditwürdigkeit des Antragstellers als Eingabe entgegennimmt und einen Darlehensplan einschließlich EMI-Betrag und Zinssatz zurückgibt. Sie erstellen ein Formulardatenmodell, indem Sie den Web-Service als Datenquelle verwenden. Sie fügen dem Formularmodell Datenmodellobjekte und einen `get`-Service hinzu. Der Service wird auf der Registerkarte „Services“ des Formulardatenmodells angezeigt. Erstellen Sie dann ein adaptives Formular, das Felder aus Datenmodellobjekten enthält, um Benutzereingaben für Darlehensbetrag, Laufzeit und Kreditwürdigkeit zu erfassen. Fügen Sie eine Schaltfläche hinzu, die den Webservice auslöst, um Plandetails abzurufen. Die Ausgabe wird in entsprechende Felder ausgefüllt.

Die folgende Regel zeigt, wie Sie die Aktion &quot;Dienst aufrufen&quot;konfigurieren, um das Beispielszenario auszuführen.

![example-invoke-services](assets/example-invoke-services.png)

### Auslösen mehrerer Aktionen mithilfe einer Wenn-Regel {#triggering-multiple-actions-using-the-when-rule}

In einem Kreditantragsformular möchten Sie erfassen, ob der Kreditantrag ein bestehender Kunde ist oder nicht. Basierend auf den vom Benutzer bereitgestellten Informationen sollte das Feld Kunden-ID ein- oder ausgeblendet werden. Außerdem möchten Sie den Fokus auf das Feld Kunden-ID legen, wenn der Benutzer ein bestehender Kunde ist. Das Antragsformular für ein Darlehen umfasst die folgenden Komponenten:

* Ein Optionsfeld **Sind Sie bereits Geometrixx-Kunde?**, das die Optionen „Ja“ und „Nein“ anbietet. Der Wert für „Ja“ ist **0**, und der Wert „Nein“ ist **1**.

* ein Textfeld, **Geometrixx-ID**, um die Kunden-ID anzugeben.

Wenn Sie eine Wenn-Regel für das Optionsfeld schreiben, um dieses Verhalten zu implementieren, wird die Regel wie folgt im visuellen Regeleditor angezeigt.  ![when-rule-example](assets/when-rule-example.png)

In der Beispielregel ist die Anweisung im Abschnitt Wenn die Bedingung, die bei der Rückgabe von True die im Abschnitt Then angegebenen Aktionen ausführt.

Die Regel wird wie folgt im Code-Editor angezeigt.

![when-rule-example-code](assets/when-rule-example-code.png)

### Verwenden einer Funktionsausgabe in einer Regel {#using-a-function-output-in-a-rule}

In einem Bestellformular haben Sie die folgende Tabelle, in der Benutzer ihre Bestellungen ausfüllen. In dieser Tabelle:

* Die erste Zeile ist wiederholbar, sodass Benutzer mehrere Produkte bestellen und unterschiedliche Mengen angeben können. Ihr Elementname ist `Row1`.
* Der Titel der Zelle in der Spalte „Produktmenge“ der wiederholbaren Zeile lautet „Menge“. Der Elementname für diese Zelle lautet `productquantity`.
* Die zweite Zeile der Tabelle ist nicht wiederholbar, und der Titel der Zelle in der Spalte „Produktmenge“ in dieser Zeile lautet „Menge insgesamt“.

![example-function-table](assets/example-function-table.png)

**A.** Zeile 1 **B.** Menge **C.** Menge insgesamt

Als Nächstes sollen die in der Spalte „Produktmenge“ angegebenen Mengen für alle Produkte addiert und die Summe in der Zelle „Menge insgesamt“ angezeigt werden. Sie können dies erreichen, indem Sie wie unten gezeigt eine Regel zum Festlegen eines Werts für die Zelle &quot;Menge insgesamt&quot;schreiben.

![example-function-output](assets/example-function-output.png)

![example-function-output-code](assets/example-function-output-code.png)

### Validieren eines Feldwerts mithilfe eines Ausdrucks {#validating-a-field-value-using-expression}

Sie möchten verhindern, dass in dem Bestellformular aus dem vorigen Abschnitt Benutzer mehr als eine Einheit jedes beliebigen Produkts mit einem Preis über 10.000 bestellen. Dazu können Sie wie unten gezeigt eine Validierungsregel schreiben.

![Example-validate](assets/example-validate.png)

![example-validate-code](assets/example-validate-code.png)
