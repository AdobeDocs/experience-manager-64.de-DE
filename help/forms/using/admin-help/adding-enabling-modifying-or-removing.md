---
title: Hinzufügen, Aktivieren, Ändern oder Entfernen von Endpunkten
seo-title: Adding, enabling, modifying, or removing endpoints
description: Erfahren Sie, wie Sie Endpunkte hinzufügen, aktivieren, ändern und entfernen können.
seo-description: Learn how to add, enable, modify and remove endpoints.
uuid: c53f225b-3d55-42f6-8982-0cd7dde0c4f5
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 7d0d4f96-fc72-4e2b-a2cc-5741b0a30f74
exl-id: 8aed1439-aa39-4f75-909b-6a7ad7840a08
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 11%

---

# Hinzufügen, Aktivieren, Ändern oder Entfernen von Endpunkten {#adding-enabling-modifying-or-removing-endpoints}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Endpunkt zu einem Dienst hinzufügen {#add-an-endpoint-to-a-service}

Endpunkte können nur zu Diensten hinzugefügt werden. Ein Endpunkt kann nicht allein vorhanden sein. muss mit einem Dienst verknüpft sein.

>[!NOTE]
>
>Es wird empfohlen, beim Hinzufügen von Endpunkten eindeutige Namen zu verwenden.

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Anwendungen und Dienste“ > „Dienstverwaltung“.
1. Klicken Sie auf der Seite &quot;Dienstverwaltung&quot;auf den zu konfigurierenden Dienst.
1. Wählen Sie in der Liste auf der Registerkarte &quot;Endpunkte&quot;den Typ des hinzuzufügenden Endpunkts aus und klicken Sie auf &quot;Hinzufügen&quot;.
1. Konfigurieren Sie abhängig vom Endpunkttyp zusätzliche Endpunkteinstellungen.

[Einstellungen für Endpunkte des Typs „Überwachter Ordner“](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#watched-folder-endpoint-settings)

[E-Mail-Endpunkteinstellungen](/help/forms/using/admin-help/configuring-email-endpoints.md#email-endpoint-settings)

[Task Manager-Endpunkte konfigurieren](/help/forms/using/admin-help/configuring-task-manager-endpoints.md#configuring-task-manager-endpoints)

[Remoting-Endpunkteinstellungen](/help/forms/using/admin-help/configuring-remoting-endpoints.md#remoting-endpoint-settings)

1. Klicken Sie auf Hinzufügen.

## Endpunkt aktivieren oder deaktivieren {#enable-or-disable-an-endpoint}

Standardmäßig werden neue Endpunkte automatisch aktiviert. Wenn Sie einen Endpunkt deaktiviert haben, müssen Sie ihn aktivieren, damit er funktioniert.

Wenn Probleme mit Diensten auftreten, deaktivieren Sie die zugehörigen Endpunkte, um das Problem besser zu beheben. Sie können Endpunkte auch während der regulären Systemwartung oder beim Aktualisieren eines Dienstes deaktivieren.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Anwendungen und Dienste&quot;> &quot;Endpunktverwaltung&quot;.
1. Aktivieren Sie auf der Seite &quot;Endpunktverwaltung&quot;das Kontrollkästchen für den Endpunkt, der aktiviert oder deaktiviert werden soll, und klicken Sie auf &quot;Aktivieren&quot;oder &quot;Deaktivieren&quot;.

## Endpunkt ändern {#modify-an-endpoint}

>[!NOTE]
>
>Die Änderungen, die Sie mit Administration Console an einer Endpunktkonfiguration vornehmen, werden nicht in den Entwurfszeitkopien Ihrer Anwendungen übernommen. Wenn Sie eine Anwendung erneut bereitstellen, gehen alle Änderungen verloren, die Sie mithilfe von Administration Console an ihren Endpunkten vorgenommen haben.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Anwendungen und Dienste&quot;> &quot;Endpunktverwaltung&quot;.
1. Klicken Sie auf der Seite &quot;Endpunktverwaltung&quot;auf den zu ändernden Endpunkt.
1. Ändern Sie auf der Seite &quot;Endpunkt aktualisieren&quot;den Namen, die Beschreibung und die Einstellungen des Endpunkts.

   >[!NOTE]
   >
   >Der Name oder die Beschreibung darf kein &lt; -Zeichen enthalten, da dadurch der in Workspace angezeigte Name oder die Beschreibung abgeschnitten wird.

1. Klicken Sie auf Aktualisieren , um Ihre Änderungen zu speichern.

Sie können diese Aufgabe auch auf der Seite Dienstverwaltung durchführen, indem Sie einen Dienst auswählen und dann auf die Registerkarte Endpunkte klicken.

## Endpunkt entfernen {#remove-an-endpoint}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Anwendungen und Dienste&quot;> &quot;Endpunktverwaltung&quot;.
1. Aktivieren Sie auf der Seite &quot;Endpunktverwaltung&quot;das Kontrollkästchen für den zu entfernenden Endpunkt und klicken Sie auf &quot;Entfernen&quot;. Der Endpunkt wird nicht mehr angezeigt.
