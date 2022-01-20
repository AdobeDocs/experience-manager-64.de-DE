---
title: Aktivieren der Protokollierung für HTML5-Formulare
seo-title: Enable logging for HTML5 forms
description: Das Dienstprogramm der Protokollfunktion aktiviert die Protokollierung von Formularen und hilft beim Debugging von Problemen mit Formularen.
seo-description: The logger utility enables logging for a form and helps you debug form-related issues.
uuid: d6279092-57f3-4fc6-b41b-9caf65459d4d
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 23bc7cd2-7d06-4ef8-977a-778e290daef9
feature: Mobile Forms
exl-id: c7953d1b-a332-4138-b744-516f3881cd4d
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 70%

---

# Aktivieren der Protokollierung für HTML5-Formulare {#enable-logging-for-html-forms}

Sie können das Dienstprogramm der Protokollfunktion konfigurieren, um mit der Erstellung von Protokollen für HTML5-Formularen zu beginnen. Das Dienstprogramm der Protokollfunktion bietet mehrere Stufen, unter denen Sie die für Ihre Zwecke geeignete wählen können. Für HTML5-Formulare sind Server- und Client-Komponenten vorhanden. Sie können Protokolle für beide Komponenten konfigurieren.

## Serverseitige Protokollierung konfigurieren {#configuring-server-side-logging}

Führen Sie die folgenden Schritte aus, um serverseitige Protokolle zu konfigurieren:

1. Rufen Sie `https://[server]:[port]/system/console/configMgr` auf. Suchen und öffnen Sie die *Apache Sling Logging Logger-Konfiguration* -Option. Folgendes Dialogfeld wird angezeigt:

   ![ Dialogfeld mit Apache Sling Logging Logger-Konfigurations-Optionen](assets/logconfig.png)

   Apache Sling Logging Logger-Konfigurations-Option

1. Ändern Sie die **Protokollierungsstufe** in **Debug**.

1. Geben Sie den Namen und Pfad der **Protokolldatei**.

   >[!NOTE]
   >
   >Wenn Sie Protokolle im Protokollordner für HTML5-Formulare generieren möchten, stellen Sie dem Dateinamen „../logs/“ voran.

1. Ändern Sie **Logger** in **HTMLFormsPerfLogger.** Klicken Sie auf **Speichern**.

## Konfigurieren der Client-Protokollierung {#configuring-client-logging}

Um die clientseitige Protokollierung in HTML5-Formularen zu aktivieren, können Sie die folgenden Verfahren verwenden:

* Mithilfe des Anforderungsparameters `log`
* Mithilfe des CQ Configuration Managers

### Aktivieren der Protokollierung mithilfe des Anforderungsparameters {#enabling-logging-using-request-parameter}

Mit dieser Methode können Sie Protokolle für eine bestimmte Anforderung generieren. Der Name des Anforderungsparameters ist **log**. Die Protokoll-URL lautet wie folgt:

`https://<server>:<port>/content/xfaforms/profiles/test.html?contentRoot=<path of the folder containing form xdp>&template=<name of the xdp>&log=<log configuration>.`

Die Protokollkonfiguration besteht aus der Protokollebene und der Protokollfunktionskategorie.

#### Protokollziel {#log-destination}

<table> 
 <tbody> 
  <tr> 
   <th><strong>Protokollziel</strong></th> 
   <th><strong>Beschreibung</strong></th> 
  </tr> 
  <tr> 
   <td>1</td> 
   <td>Protokolle werden an den Browser <strong>Console</strong> weitergeleitet</td> 
  </tr> 
  <tr> 
   <td>2</td> 
   <td>Protokolle werden in einem JavaScript-Objekt auf Clientseite erfasst und können an <strong>Server</strong> </td> 
  </tr> 
  <tr> 
   <td>3</td> 
   <td>Beide der oben genannten Optionen<br /> </td> 
  </tr> 
 </tbody> 
</table>

#### Protokollebenen {#log-levels}

<table> 
 <tbody> 
  <tr> 
   <th>Protokollebene</th> 
   <th>Beschreibung</th> 
  </tr> 
  <tr> 
   <td>0</td> 
   <td>AUS<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>1</td> 
   <td>FATAL<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>2</td> 
   <td>ERROR<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>3</td> 
   <td>WARN<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>4</td> 
   <td>INFO<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>5</td> 
   <td>DEBUG<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>6</td> 
   <td>TRACE<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>7</td> 
   <td>ALL<br type="_moz" /> </td> 
  </tr> 
 </tbody> 
</table>

#### Protokollfunktionskategorien {#logger-categories}

<table> 
 <tbody> 
  <tr> 
   <th>Protokollkategorie</th> 
   <th>Beschreibung</th> 
  </tr> 
  <tr> 
   <td>eine</td> 
   <td>xfa (auf Scripting-Engine bezogene Protokolle)</td> 
  </tr> 
  <tr> 
   <td>b</td> 
   <td>xfaView (auf Layout-Engine bezogene Protokolle)<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>c</td> 
   <td>xfaPerf (leistungsbezogene Protokolle)<br type="_moz" /> </td> 
  </tr> 
 </tbody> 
</table>

#### Protokollkonfiguration {#log-configuration}

In der Protokoll-URL wird der Abfragezeichenfolgen-Parameter zur Protokollkonfiguration wie folgt definiert:

`{destination}-{a level}-{b level}-{c level}`

Beispiel:

<table> 
 <tbody> 
  <tr> 
   <th>Protokollkonfiguration</th> 
   <th>Beschreibung</th> 
  </tr> 
  <tr> 
   <td>2-a4-b5-c6<br type="_moz" /> </td> 
   <td>Ziel: Server<br /> xfa-Ebene: INFO<br /> xfaView-Ebene: DEBUG<br /> xfaPerf-Ebene: TRACE</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Die Standardprotokollebene für jede Protokollkategorie – a (xfa), b (xfaView) und c (xfaPerf) – ist 2 (ERROR). Entsprechend lauten bei der Protokollkonfiguration 2-b6 die Protokollebenen für die verschiedenen Kategorien:\
>a (xfa): 2 (FEHLER DER Standardebene)\
>b (xfaView): 6 (vom Benutzer angegebenes TRACE)\
>a (xfaPerf): 2 (FEHLER DER Standardebene)

### Aktivieren der Protokollierung über den Configuration Manager {#enabling-logging-using-configuration-manager}

Wenn Sie Configuration Manager zum Aktivieren der Protokollierung verwenden, werden Protokolle für jede Rendering-Anforderung generiert, bis die Protokollierung erneut deaktiviert wird.

1. Melden Sie sich bei CQ Configuration Manager unter an. `https://[server]:[port]/system/console/configMgr` und melden Sie sich mit Administratorberechtigungen an.
1. Suchen Sie nach **Mobile Forms Configurations** und klicken Sie darauf.
1. Geben Sie im Textfeld &quot;Debug Options&quot; die Protokollkonfigurationen ein, wie sie im letzten Abschnitt beschrieben sind, z. B. **2a4-b5-c6**

   ![Formularkonfiguration](assets/forms_configuration.png)

   Formularkonfiguration

## Hochladen von Protokollen {#uploading-logs}

Wenn als Ziel 1 eingestellt ist, werden alle clientseitigen Skriptprotokollmeldungen an die Konsole geleitet. Wenn ein Administrator diese Protokolle zusammen mit Serverprotokollen benötigt, setzen Sie die Zielebene auf 2. Auf dieser Ebene werden alle Protokolle in einem JS-Objekt auf Clientseite erfasst. Wenn das Formular mit dem Standardprofil wiedergegeben wird, wird ein **Protokolle senden** Schaltfläche links von **Vorhandene Felder markieren** in der Symbolleiste. Wenn der Benutzer auf den Link klickt, werden alle erfassten Protokolle an den Server gesendet und in der konfigurierten Fehlerprotokolldatei auf dem Server protokolliert.

Standardmäßig werden alle Daten der Datei „error.log“ im Ordner „/crx-repository/logs/“ hinzugefügt.

Speicherort und Namen der Protokolldatei ändern:

1. Melden Sie sich beim Configuration Manager als Administrator an. Die Standard-URL von Configuration Manager lautet `https://[*Server*]:[*Port*]/system/console/configMgr`.
1. Klicken Sie auf **Apache Sling Logging Logger-Konfiguration**. Folgendes Dialogfeld wird angezeigt.

   ![logconfig-1](assets/logconfig-1.png)

1. Ändern Sie die **Protokollierungsstufe** in Debug.

1. Pfad und Namen der **Protokolldatei**.

   >[!NOTE]
   >
   >Um Protokolle im selben Ordner zu erstellen, in dem bereits andere Protokolldateien enthalten sind, geben Sie in den Eigenschaften der Protokolldateien ../logs/&lt;filename> an.

1. Ändern Sie die **Logger** nach **HTMLFormsPerfLogger** und klicken Sie auf **Speichern**.
