---
title: Verwenden der SendToPrinter-API
seo-title: Using the sendToPrinter API
description: Verwenden des sendToPrinter-Dienstes, um ein Dokument an den Drucker zu senden.
seo-description: Using the sendToPrinter service to send a document to printer.
uuid: c6a3fe8d-ec19-4350-b4a6-4c3d1971b501
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: document_services
discoiquuid: c2d564ba-fa5a-4130-b7fe-7e2c64d92170
exl-id: 89b6c8b4-4872-4bf5-a543-f33a1660636e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 100%

---

# Verwenden der SendToPrinter-API {#using-the-sendtoprinter-api}

## Übersicht {#overview}

Sie können in AEM Forms den sendToPrinter-Dienst verwenden, um ein Dokument an den Drucker zu senden. Der SendToPrinter-Dienst unterstützt die folgenden Druckerzugriffsmechanismen:

* **Drucker mit direktem Zugriff** `: A printer that is installed on the same computer is called a direct accessible printer, and the computer is named printer host. This type of printer can be a local printer that is connected to the computer directly.`

* **Drucker mit indirektem Zugriff** `: The printer that is installed on a print server is accessed from other computers. Technologies such as the common UNIX® printing system (CUPS) and the Line Printer Daemon (LPD) protocol are available to connect to a network printer. To access an indirect accessible printer, specify the print server’s IP or host name. Using this mechanism, you can send a document to an LPD URI when the network has an LPD running. The mechanism lets you route the document to any printer that is connected to the network that has an LPD running.`

   Geben Sie eines der folgenden Druckprotokolle an, wenn Sie ein Dokument an einen Drucker senden:

   * **CUPS** `: A printing protocol named common UNIX printing system. This protocol is used for UNIX operating systems and enables a computer to function as a print server. The print server accepts print requests from client applications, processes them, and sends them to configured printers. On the IBM AIX® operating system, usage of CUPS is not recommended.`
   * ``**DirectIP** `: A standard protocol for remote printing and managing print jobs. This protocol can be used locally or remotely. Print queues are not required.`
   * ``**LPD** `: A printing protocol named Line Printer Daemon protocol or Line Printer Remote (LPR) protocol. This protocol provides network print server functionality for UNIX-based systems.`
   * **SharedPrinter** `: A printing protocol that enables a computer to use a printer that is configured for that computer.`
   * **CIFS**: Der Output-Service unterstützt das CIFS-Druckprotokoll (Common Internet File System).

## Verwenden des SendToPrinter-Service {#using-sendtoprinter-service}

In nachstehender Tabelle wird Folgendes aufgelistet:

* Informationen zu printerName oder printServer, die für verschiedene Protokolle verwendet werden.
* Wert oder Ausnahme, die ein Drucker für verschiedene Kombinationen von Drucker-Server-URI und Name des Druckers zurückgibt

| Protokoll (Zugriffsmechanismus) | Drucker-Server-URI (PrinterSpec.printServer) | Name des Druckers (PrinterSpec.printerName) | Ergebnis |
|--- |--- |--- |--- |
| SharedPrinter | Alle | Leer | Ausnahme: Das erforderliche Argument sPrinterName darf nicht leer sein. |
| SharedPrinter | Alle | Ungültig | Ausnahmefehler, der besagt, dass der Drucker nicht gefunden wurde. |
| SharedPrinter | Alle | Valid | Druckauftrag wird erfolgreich ausgeführt. |
| LPD | Leer | Alle | ein Ausnahmefehler, der besagt, dass das erforderliche sPrintServerUri-Argument nicht leer sein darf. |
| LPD | Ungültig | Leer | Ausnahmefehler, der besagt, dass das erforderliche sPrinterName-Argument nicht leer sein darf. |
| LPD | Ungültig | Nicht leer | Ausnahmefehler, der besagt, dass sPrintServerUri nicht gefunden wurde. |
| LPD | Gültig | Ungültig | Ausnahmefehler, der besagt, dass der Drucker nicht gefunden wurde. |
| LPD | Gültig | Gültig | Druckauftrag wird erfolgreich ausgeführt. |
| CUPS | Leer | Alle | ein Ausnahmefehler, der besagt, dass das erforderliche sPrintServerUri-Argument nicht leer sein darf. |
| CUPS | Ungültig | Alle | Ausnahmefehler, der besagt, dass der Drucker nicht gefunden wurde. |
| CUPS | Gültig | Alle | Druckauftrag wird erfolgreich ausgeführt. |
| DirectIP | Leer | Alle | ein Ausnahmefehler, der besagt, dass das erforderliche sPrintServerUri-Argument nicht leer sein darf. |
| DirectIP | Ungültig | Alle | Ausnahmefehler, der besagt, dass der Drucker nicht gefunden wurde. |
| DirectIP | Gültig | Alle | Druckauftrag wird erfolgreich ausgeführt. |
| CIFS | Gültig | Leer | Druckauftrag wird erfolgreich ausgeführt. |
| CIFS | Ungültig | Alle | Beim Drucken einen unbekannten Fehler bei Verwendung von CIFS aus. |
| CIFS | Leer | Alle | ein Ausnahmefehler, der besagt, dass das erforderliche sPrintServerUri-Argument nicht leer sein darf. |

## Authentifizierungsunterstützung {#authentication-support}

Authentifizierung wird nur für CIFS-Druck unterstützt. Geben Sie zur Authentifizierung in PrinterSpec Benutzername/Kennwort/Domain ein. Sie können ein Kennwort mit AEM Granite CyprtoSupport Service verschlüsseln, indem Sie die folgenden Schritte ausführen:

1. Wechseln Sie zu https://&lt;server>:&lt;port>/system/console.

1. Rufen Sie **[!UICONTROL Main]** > **[!UICONTROL Crypto Support]** auf.

1. Geben Sie Nur-Text ein und klicken Sie auf **[!UICONTROL Schützen]**.
