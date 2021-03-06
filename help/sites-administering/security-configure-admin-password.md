---
title: Konfigurieren des Administratorkennworts bei der Installation
seo-title: Configure the Admin Password on Installation
description: Hier erfahren Sie, wie Sie das Administratorkennwort bei der AEM-Installation ändern.
seo-description: Learn how to change the Admin Password on AEM Installation.
uuid: 06da9890-ed63-4fb6-88d5-fd0e16bc4ceb
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 00806e6e-3578-4caa-bafa-064f200a871f
exl-id: 6dd289ee-13fd-46be-82cd-aa69852397c9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 86%

---

# Konfigurieren des Administratorkennworts bei der Installation{#configure-the-admin-password-on-installation}

## Übersicht {#overview}

Ab Version 6.3 kann bei der Installation einer neuen AEM-Instanz das Administratorkennwort über die Befehlszeile festgelegt werden.

In älteren Versionen von AEM musste das Kennwort für das Administratorkonto zusammen mit dem Kennwort für diverse andere Konsolen nach der Installation geändert werden.

Dieses Feature ermöglicht es, ein neues Administratorkennwort für das Repository und das Servlet-Modul während der Installation einer AEM-Instanz hinzuzufügen, sodass dieser Schritt nicht mehr manuell im Nachhinein ausgeführt werden muss.

>[!CAUTION]
>
>Beachten Sie, dass die Felix-Konsole von diesem Feature ausgenommen ist und das Kennwort für diese Konsole manuell geändert werden muss. Weitere Informationen finden Sie im entsprechenden [Abschnitt der Sicherheits-Checkliste](/help/sites-administering/security-checklist.md#change-default-passwords-for-the-aem-and-osgi-console-admin-accounts).

## Verwendung {#how-do-i-use-it}

Dieses Feature wird automatisch ausgelöst, wenn Sie AEM über die Befehlszeile installieren (anstatt in einem Dateisystem-Explorer auf die JAR-Datei doppelzuklicken).

Allgemeine Syntax zum Ausführen einer AEM-Instanz über die Befehlszeile:

```shell
java -jar aem6.3.jar
```

Wenn Sie die Instanz über die Befehlszeile ausführen, haben Sie während des Installationsprozesses die Möglichkeit, das Administratorkennwort zu ändern:

![chlimage_1-116](assets/chlimage_1-116.png)

>[!NOTE]
>
>Die Aufforderung zum Ändern des Administratorkennworts wird nur während der Installation einer neuen AEM-Instanz angezeigt.

## Verwenden des Flags „-nointeractive“ {#using-the-nointeractive-flag}

Das Kennwort kann auch über eine Eigenschaftendatei angegeben werden. Dies geschieht mithilfe der `-nointeractive` Markierung kombiniert mit `-Dadmin.password.file` Systemeigenschaft.

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
>Wenn Sie einfach die `-nointeractive` -Parameter ohne die `-Dadmin.password.file` -Systemeigenschaft verwenden AEM das standardmäßige Administratorkennwort, ohne dass Sie dazu aufgefordert werden, es zu ändern. Dies entspricht im Wesentlichen dem Verhalten früherer Versionen. Dieser nicht interaktive Modus kann für automatische Installationen unter Verwendung der Befehlszeile in einem Installationsskript verwendet werden.
