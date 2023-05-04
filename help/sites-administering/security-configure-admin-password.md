---
title: Konfigurieren des Administratorkennworts bei der Installation
seo-title: Configure the Admin Password on Installation
description: Erfahren Sie, wie Sie das Administratorkennwort bei AEM Installation ändern.
seo-description: Learn how to change the Admin Password on AEM Installation.
uuid: 06da9890-ed63-4fb6-88d5-fd0e16bc4ceb
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 00806e6e-3578-4caa-bafa-064f200a871f
exl-id: 6dd289ee-13fd-46be-82cd-aa69852397c9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 24%

---

# Konfigurieren des Administratorkennworts bei der Installation{#configure-the-admin-password-on-installation}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht {#overview}

Seit Version 6.3 erlaubt AEM das Festlegen des Administratorkennworts über die Befehlszeile bei der Installation einer neuen Instanz.

Bei früheren Versionen von AEM musste das Kennwort für das Administratorkonto zusammen mit dem Kennwort für verschiedene andere Konsolen nach der Installation geändert werden.

Diese Funktion bietet die Möglichkeit, während der Installation einer AEM-Instanz ein neues Administratorkennwort für das Repository und die Servlet-Engine festzulegen, sodass die manuelle Ausführung später entfällt.

>[!CAUTION]
>
>Beachten Sie, dass die Felix Console nicht von dieser Funktion abgedeckt wird, für die das Kennwort manuell geändert werden muss. Weitere Informationen finden Sie in der entsprechenden [Abschnitt &quot;Sicherheitscheckliste&quot;](/help/sites-administering/security-checklist.md#change-default-passwords-for-the-aem-and-osgi-console-admin-accounts).

## Wie benutze ich es? {#how-do-i-use-it}

Diese Funktion wird automatisch Trigger, wenn Sie AEM über die Befehlszeile installieren, anstatt auf die JAR-Datei in einem Dateisystem-Explorer zu doppelklicken.

Die allgemeine Syntax zum Ausführen einer AEM-Instanz über die Befehlszeile lautet:

```shell
java -jar aem6.3.jar
```

Wenn Sie die Instanz über die Befehlszeile ausführen, erhalten Sie die Option, das Administratorkennwort während des Installationsprozesses zu ändern:

![chlimage_1-116](assets/chlimage_1-116.png)

>[!NOTE]
>
>Die Aufforderung zur Änderung des Administratorkennworts wird nur während der Installation einer neuen AEM angezeigt.

## Verwenden des Flag -nointeractive {#using-the-nointeractive-flag}

Sie können das Kennwort auch in einer Eigenschaftendatei angeben. Dies geschieht mithilfe der `-nointeractive` Markierung kombiniert mit `-Dadmin.password.file` Systemeigenschaft.

Beispiel:

```shell
java -Dadmin.password.file =/path/to/passwordfile.properties -jar aem6.3.jar -nointeractive
```

Das Kennwort in der Datei `passwordfile.properties` muss im folgenden Format angegeben werden:

```xml
admin.password = 12345678
```

>[!NOTE]
>
>Wenn Sie den Parameter `-nointeractive`- ohne die Systemeigenschaft `-Dadmin.password.file` verwenden, verwendet AEM das standardmäßige Administratorkennwort und fordert Sie nicht zur Änderung des Kennworts auf, was im Wesentlichen dem Verhalten älterer Versionen entspricht. Dieser nicht interaktive Modus kann für automatische Installationen unter Verwendung der Befehlszeile in einem Installationsskript verwendet werden.
