---
title: Konfigurieren der Task Manager-Endpunkte
seo-title: Configuring Task Manager endpoints
description: Erfahren Sie, wie Sie Task Manager-Endpunkte konfigurieren.
seo-description: Learn how to configure Task Manager endpoints.
uuid: 07604b10-0bd7-4bce-9624-7ebac4754f56
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9c55feb9-23d8-4798-a3c5-70ec736df3ad
exl-id: 546a699e-975f-42a1-8ab5-0de4bd7f4a8f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 77%

---

# Konfigurieren der Task Manager-Endpunkte {#configuring-task-manager-endpoints}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Task Manager-Endpunkte ermöglichen es Workspace-Benutzern, den Dienst aufzurufen.

**Task Manager-Endpunkteinstellungen**

Verwenden Sie die folgenden Einstellungen, um einen Task Manager-Endpunkt zu konfigurieren.

**Name:** (Obligatorisch) Identifiziert den Endpunkt. Der Name wird in Workspace in der Kartenansicht angezeigt. Der Name darf kein &lt;-Zeichen enthalten, weil dadurch die Anzeige des Namens in Workspace abgeschnitten wird. Wenn Sie eine URL als Name des Endpunktes angeben, vergewissern Sie sich, dass sie den in RFC1738 angegebenen Syntaxregeln entspricht.

**Beschreibung**: Eine Beschreibung des Endpunkts. Der Name darf kein &lt;-Zeichen enthalten, weil dadurch die Anzeige des Namens in Workspace abgeschnitten wird.

**Aufgabenanweisungen:** Anweisungen für den Benutzer, der diesen Workflow startet.

**Prozesseigentümer:** Der Name der für den Prozess verantwortlichen Person.

**Benutzer kann Aufgabe weiterleiten:** Ermöglicht dem Benutzer die Weiterleitung der ursprünglichen Aufgabe.

**Anlagenfenster anzeigen:** Ermöglicht dem Benutzer, das Anlagenfenster zu sehen.

**Hinzufügen von Anhängen zulassen:** Ermöglicht dem Benutzer das Hinzufügen von Anlagen und Notizen.

**Aufgabe ursprünglich gesperrt:** Sperrt die ursprüngliche Aufgabe.

**ACLs für freigegebene Warteschlangen hinzufügen:** Die ursprüngliche Aufgabe wird mit ACLs für Benutzer freigegebener Warteschlangen erstellt.

**Kategorsierung:** (Obligatorisch) Die Kategorie, in der das Formular in Workspace dem Benutzer angezeigt wird. Wählen Sie eine Kategorie aus der Liste aus oder wählen Sie „Neue Kategorie“, um eine Kategorie hinzuzufügen.

**Vorgangsname:** (Obligatorisch) Eine Liste von Vorgängen, die dem Endpunkt zugewiesen werden können.
