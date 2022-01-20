---
title: Grundlagen zu AEM Forms-Prozessen
seo-title: Understanding AEM Forms Processes
description: Erfahren Sie, wie Sie mit AEM Forms-Geschäftsprozessen Vorgänge automatisieren können. Aktivieren Sie die Prozesse, um einen Dienst zu erstellen, damit Sie ihn wie andere Dienste aufrufen können. Prozesse können kurzlebig oder langlebig sein.
seo-description: Learn how to use AEM Forms business processes to automate operations. Activate the processes to create a service so that you can invoke it like other services. Processes can be short-lived or long-lived.
uuid: 7cbebe7d-f222-42fa-8eb6-d2443458a791
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: development-tools, coding
discoiquuid: ac9fe461-63e7-442b-bd1c-eb9576ef55aa
role: Developer
exl-id: 0ae0ddbf-ded6-4494-bf94-bf6cf7f1fd46
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 2%

---

# Grundlagen zu AEM Forms-Prozessen {#understanding-aem-forms-processes}

Ein gängiges Anwendungsbeispiel besteht darin, dass eine Reihe von AEM Forms-Diensten mit einem einzigen Dokument arbeiten kann. Sie können eine Anforderung an den Dienstcontainer senden, indem Sie einen Prozess mithilfe von Workbench erstellen. Ein Prozess stellt einen Geschäftsprozess dar, den Sie automatisieren. Informationen zum Erstellen von Prozessen finden Sie unter [Workbench verwenden](https://www.adobe.com/go/learn_aemforms_workbench_63).

Sobald ein Prozess aktiviert wird, wird er zu einem Dienst und kann wie andere Dienste aufgerufen werden. Ein Unterschied zwischen einem Standarddienst wie dem Encryption-Dienst und einem Dienst, der von einem Prozess stammt, besteht darin, dass dieser einen Vorgang hat, der viele Aktionen ausführt. Ein Standarddienst weist dagegen viele Vorgänge auf. Jeder Vorgang führt in der Regel eine Aktion durch, z. B. das Anwenden einer Richtlinie auf ein Dokument oder das Verschlüsseln eines Dokuments.

Prozesse können kurzlebig oder langlebig sein. Ein kurzlebiger Prozess ist ein Vorgang, der synchron und in demselben Ausführungs-Thread ausgeführt wird, von dem aus er aufgerufen wurde. Kurzlebige Vorgänge sind mit dem Standardverhalten in den meisten Programmiersprachen vergleichbar, bei dem eine Client-Anwendung eine Methode aufruft und auf einen Rückgabewert wartet.

Es gibt jedoch Situationen, in denen ein Prozess aufgrund von Faktoren wie diesen nicht synchron abgeschlossen werden kann:

* Ein Prozess kann eine erhebliche Zeitspanne umfassen.
* Ein Prozess kann organisatorische Grenzen überschreiten.
* Ein Prozess benötigt eine externe Eingabe, damit er abgeschlossen werden kann. Angenommen, ein Formular wird an einen Manager gesendet, der nicht im Büro ist. In diesem Fall ist der Prozess erst abgeschlossen, wenn der Manager das Formular zurückgibt und ausfüllt.

   Diese Arten von Prozessen werden als langlebige Prozesse bezeichnet. Ein langlebiger Prozess wird asynchron ausgeführt, sodass Systeme so interagieren können, wie es die Ressourcen zulassen, und das Tracking und die Überwachung des Vorgangs ermöglichen. Wenn ein langlebiger Prozess aufgerufen wird, erstellt AEM Forms einen Aufrufkennungswert als Teil eines Datensatzes, der den langlebigen Prozessstatus verfolgt. Der Datensatz wird in der AEM Forms-Datenbank gespeichert. Sie können langlebige Prozessdatensätze bereinigen, wenn sie nicht mehr benötigt werden.

>[!NOTE]
>
>AEM Forms erstellt keinen Datensatz, wenn ein kurzlebiger Prozess aufgerufen wird.

Mithilfe des Werts für die Kennung des Aufrufs können Sie den Status des langlebigen Prozesses verfolgen. Beispielsweise können Sie den Wert für die Prozessaufruf-ID verwenden, um Prozesse in Manager auszuführen, z. B. um eine laufende Prozessinstanz zu beenden.

**Beispiel für einen kurzlebigen Prozess**

Die folgende Abbildung zeigt ein Beispiel für einen kurzlebigen Prozess mit dem Namen *MyApplication/EncryptDocument*.

>[!NOTE]
>
>Dieser Prozess basiert nicht auf einem vorhandenen AEM Forms-Prozess. Erstellen Sie einen Prozess mit dem Namen `MyApplication/EncryptDocument` Workbench verwenden. (Siehe [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).)

Wenn dieser kurzlebige Prozess aufgerufen wird, führt er die folgenden Aktionen aus:

1. Ruft das ungesicherte PDF-Dokument ab, das als Eingabewert an den Prozess übergeben wird.
1. Sie verschlüsselt das PDF-Dokument mit einem Kennwort. Der Name des Eingabeparameters für diesen Prozess lautet `inDoc` und der Datentyp document ist.
1. Speichert das kennwortverschlüsselte PDF-Dokument als PDF-Datei im lokalen Dateisystem. Dieser Prozess gibt das verschlüsselte PDF-Dokument als Ausgabewert zurück. Der Name des Ausgabeparameters für diesen Prozess lautet `outDoc` und der Datentyp document ist.

   Dieser Prozess wird synchron im selben Ausführungs-Thread abgeschlossen, von dem aus er aufgerufen wurde. Der Name dieses kurzlebigen Prozesses lautet `MyApplication/EncryptDocument`und der Betrieb `invoke`.

   >[!NOTE]
   >
   >In der Regel besteht ein kurzlebiger Prozess aus mehr als drei Aktionen. Sie erstellen einen Prozess mit Workbench. (Siehe [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).)

   *Programmieren mit AEM Formularen* beschreibt die folgenden Methoden, mit denen Sie diesen kurzlebigen Prozess programmgesteuert aufrufen können:

   * [Aufrufen eines kurzlebigen Prozesses durch Übergeben eines unsicheren Dokuments mit AEM Forms Remoting](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-a-short-lived-process-by-passing-an-unsecure-document-using-remoting) (Verwenden einer Flex-Anwendung)
   * [Aufrufen eines kurzlebigen Prozesses mithilfe der Aufruf-API](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-a-short-lived-process-using-the-invocation-api) (Java Invocation API)
   * [Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding) (Beispiel für einen Webdienst)
   * [AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom) (Beispiel für einen Webdienst)
   * [Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref) (Beispiel für einen Webdienst)
   * [Aufrufen von AEM Forms mithilfe von BLOB-Daten über HTTP](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-blob-data-over-http) (Beispiel für einen Webdienst)
   * [AEM Forms mithilfe von DIME aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-dime) (Beispiel für einen Webdienst)
   * [Aufrufen des Prozesses MyApplication/EncryptDocument mithilfe von REST](/help/forms/developing/invoking-aem-forms-using-rest.md)

**Beispiel für langlebige Prozesse**

Die folgende Abbildung zeigt ein Beispiel für einen langlebigen Prozess.

Dieser Prozess wird aufgerufen, wenn ein Antragsteller ein Darlehensformular einreicht. Das Verfahren ist erst abgeschlossen, wenn ein Kreditsachbearbeiter den Kreditantrag genehmigt oder ablehnt. Der Name dieses langlebigen Prozesses lautet &quot;FirstAppSolution/PreLoanProcess&quot;und sein Vorgang lautet `invoke_Async`. Dieser Prozess muss asynchron aufgerufen werden. Informationen zum programmgesteuerten Aufrufen dieses langlebigen Prozesses finden Sie unter [Menschen orientierte langlebige Prozesse aufrufen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).

>[!NOTE]
>
>Dieser Prozess kann durch Befolgen des in [Erstellen der ersten AEM Forms-Anwendung](https://www.adobe.com/go/learn_aemforms_firstapp_ds_63).
