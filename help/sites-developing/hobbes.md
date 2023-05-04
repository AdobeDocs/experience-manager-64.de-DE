---
title: Testen der Benutzeroberfläche
seo-title: Testing Your UI
description: AEM bietet ein Framework für die Automatisierung von Tests für Ihre AEM-Benutzeroberfläche
seo-description: AEM provides a framework for automating tests for your AEM UI
uuid: b0280a70-643e-4455-82ea-fa7a90823b53
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: components, testing
discoiquuid: bc0130c3-826e-47dd-b18b-85e1a7bb9936
exl-id: 16b4088d-13b4-47b9-b89d-0c4a13676f12
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 59%

---

# Testen der Benutzeroberfläche{#testing-your-ui}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

AEM bietet ein Framework für die Automatisierung von Tests für Ihre AEM Benutzeroberfläche. Mit diesem Framework können Sie Tests der Benutzeroberfläche direkt in einem Webbrowser schreiben und ausführen. Das Framework umfasst eine JavaScript-API für das Erstellen von Tests.

Das AEM-Test-Framework nutzt Hobbes.js, eine Testbibliothek, die in JavaScript geschrieben wurde. Das Hobbes.js-Framework wurde für AEM-Tests als Teil des Entwicklungsprozesses entwickelt. Das Framework steht jetzt zur allgemeinen Verwendung zum Testen Ihrer AEM-Anwendungen zur Verfügung.

>[!NOTE]
>
>Detaillierte Angaben zur API finden Sie in der [Dokumentation](https://helpx.adobe.com/de/experience-manager/6-4/sites/developing/using/reference-materials/test-api/index.html) zu Hobbes.js.

## Struktur von Tests {#structure-of-tests}

Bei der Verwendung automatisierter Tests in AEM sind die folgenden Begriffe wichtig, um sie zu verstehen:

|  |  |
|---|---|
| Aktion | Eine **Aktion** ist eine bestimmte Aktivität auf einer Web-Seite, z. B. das Klicken auf einen Link oder eine Schaltfläche. |
| Testfall | Ein **Testfall** ist eine bestimmte Situation, die aus einer oder mehreren **Aktionen** bestehen kann. |
| Testsuite | Eine **Test-Suite** ist eine Gruppe verwandter **Testfälle**, die zusammen einen bestimmten Anwendungsfall testen. |

## Ausführen von Tests {#executing-tests}

### Anzeigen von Test-Suites {#viewing-test-suites}

Öffnen Sie die Testkonsole , um die registrierten Test-Suites anzuzeigen. Das Testbedienfeld enthält eine Liste von Test-Suites und deren Testfälle.

Navigieren Sie zur Tools-Konsole über **Globale Navigation -> Tools > Vorgänge -> Tests**.

![chlimage_1-26](assets/chlimage_1-26.png)

Beim Öffnen der Konsole werden die Test-Suites links neben einer Option aufgeführt, mit der sie alle nacheinander ausgeführt werden können. Der rechts angezeigte Bereich mit einem gecheckten Hintergrund ist ein Platzhalter für die Anzeige des Seiteninhalts während der Testausführung.

![chlimage_1-27](assets/chlimage_1-27.png)

### Ausführen einer einzelnen Test-Suite {#running-a-single-test-suite}

Testsuiten können einzeln ausgeführt werden. Wenn Sie eine Test-Suite ausführen, ändert sich die Seite, während die Testfälle und ihre Aktionen ausgeführt werden. Die Ergebnisse werden nach Abschluss des Tests angezeigt. Die Ergebnisse werden durch Symbole gekennzeichnet.

Das Häkchen-Symbol kennzeichnet einen erfolgreichen Test: 

![](do-not-localize/chlimage_1-5.png)

Eine X-Symbol zeigt einen fehlgeschlagenen Test an:

![](do-not-localize/chlimage_1-6.png)

So führen Sie eine Test Suite aus:

1. Klicken oder tippen Sie im Testfeld auf den Namen des Testfalls, den Sie ausführen möchten, um die Details der Aktionen zu erweitern.

   ![chlimage_1-28](assets/chlimage_1-28.png)

1. Klicken oder tippen Sie auf **Ausführen eines Tests** Schaltfläche.

   ![](do-not-localize/chlimage_1-7.png)

1. Der Platzhalter wird durch Seiteninhalte ersetzt, wenn der Test ausgeführt wird.

   ![chlimage_1-29](assets/chlimage_1-29.png)

1. Überprüfen Sie die Ergebnisse des Testfalls, indem Sie auf die Beschreibung tippen oder klicken, um die **Ergebnis** Bereich. Tippen oder klicken Sie auf den Namen Ihres Testfalls im **Ergebnis** -Bedienfeld werden alle Details angezeigt.

   ![chlimage_1-30](assets/chlimage_1-30.png)

### Ausführen mehrerer Tests {#running-multiple-tests}

Test-Suites werden nacheinander in der Reihenfolge ausgeführt, in der sie in der Konsole angezeigt werden. Sie können einen Test detailliert untersuchen, um die detaillierten Ergebnisse anzuzeigen.

![chlimage_1-31](assets/chlimage_1-31.png)

1. Tippen oder klicken Sie im Testfeld auf die Schaltfläche **Alle Tests ausführen** oder auf die Schaltfläche **Tests ausführen** unter dem Titel der Test-Suite, die Sie ausführen möchten.

   ![](do-not-localize/chlimage_1-8.png)

1. Um die Ergebnisse jedes Testfalls anzuzeigen, tippen oder klicken Sie auf den Titel des Testfalls. Wenn Sie im Bedienfeld **Ergebnis** auf den Namen des Tests tippen oder klicken, werden alle Details angezeigt.

   ![chlimage_1-32](assets/chlimage_1-32.png)

## Erstellen und Verwenden einer einfachen Test-Suite {#creating-and-using-a-simple-test-suite}

Die folgenden Schritte erläutern die Erstellung und Ausführung einer Test-Suite mit [We.Retail-Inhalten](/help/sites-developing/we-retail.md). Sie können den Test jedoch auch einfach für eine andere Web-Seite anpassen.

Vollständige Informationen zum Erstellen eigener Test-Suites finden Sie in der [Dokumentation zur Hobbes.js-API](https://helpx.adobe.com/de/experience-manager/6-4/sites/developing/using/reference-materials/test-api/index.html).

1. Öffnen Sie CRXDE Lite. ([http://localhost:4502/crx/de](http://localhost:4502/crx/de))
1. Klicken Sie mit der rechten Maustaste auf den Ordner `/etc/clientlibs` und klicken Sie auf **Erstellen > Ordner erstellen**. Geben Sie als Namen `myTests` ein und klicken Sie auf **OK**.
1. Klicken Sie mit der rechten Maustaste auf den Ordner `/etc/clientlibs/myTests` und klicken Sie auf **Erstellen > Knoten erstellen**. Geben Sie die folgenden Eigenschaftswerte ein und klicken Sie dann auf **OK**:

   * Name: `myFirstTest`
   * Typ: `cq:ClientLibraryFolder`

1. Fügen Sie dem Knoten „myFirstTest“ die folgenden Eigenschaften hinzu:

   | Name | Typ | Wert |
   |---|---|---|
   | `categories` | `String[]` | `granite.testing.hobbes.tests` |
   | `dependencies` | `String[]` | `granite.testing.hobbes.testrunner` |

   >[!NOTE]
   >
   >**Nur AEM Forms**
   >
   >Fügen Sie den Kategorien und Abhängigkeiten die folgenden Werte hinzu, um adaptive Formulare zu testen. Beispiel:
   >
   >**categories:**: `granite.testing.hobbes.tests, granite.testing.hobbes.af.commons`
   >
   >**dependencies**: `granite.testing.hobbes.testrunner, granite.testing.hobbes.af`

1. Klicken Sie auf **Alle speichern**.
1. Klicken Sie mit der rechten Maustaste auf den Knoten `myFirstTest` und klicken Sie auf **Erstellen > Datei erstellen**. Nennen Sie die Datei `js.txt` und klicken Sie auf **OK**.
1. Geben Sie in der Datei `js.txt` den folgenden Text ein:

   ```
   #base=.
   myTestSuite.js
   ```

1. Klicken Sie auf **Alle speichern** und schließen Sie dann die Datei `js.txt`
1. Klicken Sie mit der rechten Maustaste auf den Knoten `myFirstTest` und klicken Sie auf **Erstellen > Datei erstellen**. Nennen Sie die Datei `myTestSuite.js` und klicken Sie auf **OK**.
1. Kopieren Sie den folgenden Code in die Datei `myTestSuite.js` und speichern Sie die Datei anschließend:

   ```
   new hobs.TestSuite("Experience Content Test Suite", {path:"/etc/clientlibs/myTests/myFirstTest/myTestSuite.js"})
      .addTestCase(new hobs.TestCase("Navigate to Experience Content")
         .navigateTo("/content/we-retail/us/en/experience/arctic-surfing-in-lofoten.html")
      )
      .addTestCase(new hobs.TestCase("Hover Over Topnav")
         .mouseover("li.visible-xs")
      )
      .addTestCase(new hobs.TestCase("Click Topnav Link")
         .click("li.active a")
   );
   ```

1. Navigieren Sie zur **Testkonsole**, um die Test-Suite zu testen.
