---
title: Arten von Endpunkten
seo-title: Types of endpoints
description: Erfahren Sie mehr über die verschiedenen Arten von Endpunkten.
seo-description: Learn about the different types of endpoints.
uuid: c899245c-14cc-4035-9440-95a5b6c1e47f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 8fe572e0-8a53-4129-940f-3fdb990073fe
exl-id: 7c6b9b6c-d4b5-46a8-8a6a-3b8802ac392d
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 100%

---

# Arten von Endpunkten {#types-of-endpoints}

Bevor ein Dienst verwendet werden kann, müssen Sie einen Endpunkt konfigurieren und aktivieren. Ein Endpunkt gibt an, wie ein Dienst aufgerufen werden soll.

>[!NOTE]
>
>In Workbench werden Endpunkte als „Startpunkte“ bezeichnet.

Einem Dienst können die folgenden Typen von Endpunkten hinzugefügt werden: Nicht alle Dienste unterstützen alle Endpunkte:

**E-Mail**: Ermöglicht es einem Benutzer, einen Service durch Senden einer E-Mail mit einer oder mehreren Dateianlagen an ein angegebenes E-Mail-Konto aufzurufen. Bevor Sie einen Email-Endpunkt konfigurieren können, müssen Sie die erforderlichen E-Mail-Konten konfigurieren. (Siehe E-Mail-Endpunkte konfigurieren.)

**Überwachter Ordner**: Ermöglicht es einem Benutzer, einen Service aufzurufen, indem er eine Datei in einem Ordner ablegt, der in einem bestimmten Intervall überprüft wird. (Siehe Endpunkte für überwachte Ordner konfigurieren.)

**TaskManager**: Ermöglicht es einem Workspace-Benutzer, den Service aufzurufen.

**Remoting**: Ermöglicht es einem Programm, das mit Flex erstellt wurde, den Service mithilfe von AEM Forms Remoting (für AEM Forms nicht mehr unterstützt) aufzurufen. Ein Remoting-Endpunkt wird automatisch für jeden aktivierten Dienst erstellt. Ein Flex-Ziel mit demselben Namen wie der Endpunkt wird erstellt und Flex-Clients können Remoteobjekte erstellen, die auf dieses Ziel verweisen, um Vorgänge für den entsprechenden Dienst aufzurufen.

**SOAP**: Ermöglicht es einem Client-Programm, das mit den AEM Forms-Programmierungs-APIs entwickelt wurde, den Service mithilfe des SOAP-Modus aufzurufen. Ein SOAP-Endpunkt wird automatisch für jeden aktivierten Dienst erstellt. 

**Hinweis**: *Die Sicherheit kann aus Sicherheitsdokumenten entfernt werden, wenn der SOAP-Endpunkt verwendet wird, während die Dokumente in Adobe Acrobat oder Adobe Reader angezeigt werden. Detailinformationen zum Deaktivieren von SOAP-Endpunkten für LCRM-Dokumente finden Sie unter [SOAP-Endpunkte für Document Security-Dokumente deaktivieren](/help/forms/using/admin-help/configuring-client-server-options.md#disable-soap-endpoints-for-document-security-documents)*.

**EJB**: Ermöglicht es einem Client-Programm, das mit den AEM Forms-Programmierungs-APIs entwickelt wurde, den Service mithilfe des Enterprise JavaBeans-Modus (EJB) aufzurufen. Ein EJB-Endpunkt wird automatisch für jeden aktivierten Dienst erstellt.

**WSDL**: Ermöglicht es einem Client-Programm, das mit den AEM Forms-Programmierungs-APIs entwickelt wurde, den Service mithilfe der Web Service Definition Language (WSDL) aufzurufen. Die Seite „Core-Konfigurationen“ enthält eine Option zum Aktivieren der WSDL-Generierung für alle AEM Forms-Dienste. (Siehe Allgemeine AEM Forms-Einstellungen konfigurieren.)

**REST**: In Workbench erstellte Prozesse können so konfiguriert werden, dass sie über Representational State Transfer-Anforderungen (REST) aufgerufen werden können. REST-Anforderungen werden von HTML-Seiten aus gesendet. Das heißt, Sie können einen AEM Forms-Prozess direkt von einer Webseite mithilfe einer REST-Anforderung aufrufen.

Die Endpunkte E-Mail, TaskManager, überwachter Ordner und Remoting stellen nur einen bestimmten Vorgang des Dienstes zur Verfügung. Beim Hinzufügen dieser Endpunkte muss in einem zweiten Konfigurationsschritt eine Methode zum Aufrufen des Dienstes, zum Festlegen von Konfigurationsparametern und zum Angeben der Zuordnungen von Eingabe- und Ausgabeparameter ausgewählt werden.
