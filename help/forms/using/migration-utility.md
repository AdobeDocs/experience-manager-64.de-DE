---
title: Migration der Assets und Dokumente von AEM Forms
seo-title: Migrate AEM Forms assets and documents
description: Mit dem Migrationsdienstprogramm können Sie AEM Forms-Assets und -Dokumente aus AEM 6.3 Forms oder früheren Versionen in AEM 6.4 Forms migrieren.
seo-description: The Migration utility allows you to Migrate AEM Forms assets and documents from AEM 6.3 Forms or prior versions to AEM 6.4 Forms.
uuid: 593fc421-b70e-4dbe-87bc-ea49ff025368
content-type: reference
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-strategy: max-2018
discoiquuid: a8b1f7df-e36f-4d02-883a-72120fea7046
role: Admin
exl-id: 72ead30c-648d-43ad-9826-9c8945a8860d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1865'
ht-degree: 60%

---

# Migration der Assets und Dokumente von AEM Forms {#migrate-aem-forms-assets-and-documents}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Das Migrationsdienstprogramm konvertiert die [Assets von adaptiven Formularen](/help/forms/using/introduction-forms-authoring.md), [Cloud-Konfigurationen](/help/sites-developing/extending-cloud-config.md) und [Correspondence Management-Assets](/help/forms/using/cm-overview.md) von dem in früheren Versionen verwendeten Format in das in AEM 6.4 Forms verwendete Format. Wenn Sie das Migrationsdienstprogramm ausführen, werden folgende Elemente migriert:

* Benutzerdefinierte Komponenten für adaptive Formulare
* Adaptive Formulare und Correspondence Management-Vorlagen
* Cloud-Konfigurationen
* Assets für Correspondence Management und adaptive Formulare

>[!NOTE]
>
>Im Falle einer nicht ersetzenden Aktualisierung können Sie für Correspondence Management-Assets die Migration jedes Mal ausführen, wenn Sie die Assets importieren. Für die Correspondence Management-Migration muss das Forms-Kompatibilitätspaket installiert sein.

## Migrationsansatz {#approach-to-migration}

Sie können [Upgrade](/help/forms/using/upgrade.md) oder führen Sie eine Neuinstallation durch. Je nachdem, ob Sie Ihre vorherige Installation aktualisiert oder eine Neuinstallation durchgeführt haben, müssen Sie einen der folgenden Schritte ausführen:

**Im Falle einer ersetzenden Aktualisierung**

Wenn Sie eine ersetzende Aktualisierung durchgeführt haben, verfügt die aktualisierte Instanz bereits über die Assets und Dokumente. Bevor Sie jedoch die Assets und Dokumente verwenden können, müssen Sie das [AEMFD-Kompatibilitätspaket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) installieren (enthält das Correspondence-Management-Kompatibilitätspaket).

Dann müssen Sie die Assets und Dokumente aktualisieren, indem Sie das [Migrationsprogramm ausführen](#runningmigrationutility).

**Bei nicht ersetzender Installation**

Bevor Sie die Assets und Dokumente verwenden können, müssen Sie das [AEMFD-Kompatibilitätspaket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) (einschließlich des Correspondence Management-Kompatibilitätspakets) installieren, wenn es sich um eine dezentrale (neue) Installation handelt.

Dann müssen Sie Ihr Asset-Paket (zip oder cmp) in das neue Setup importieren und dann die Assets und Dokumente aktualisieren, indem Sie das [Migrationsprogramm ausführen](#runningmigrationutility). Aufgrund der [Abwärtskompatibilität-bezogenen](/help/sites-deploying/backward-compatibility.md) Änderungen werden Speicherorte von einigen Ordnern im CRX-Repository geändert. Exportieren und importieren Sie Abhängigkeiten (benutzerdefinierte Bibliotheken und Assets) vom vorherigen Setup in eine neue Umgebung manuell.

## Vor dem Start der Migration lesen {#prerequisites}

Für Correspondence Management-Assets:

* Für die Assets, die von der vorherigen Plattform importiert werden, wird eine Eigenschaft hinzugefügt: **fd:version=1.0**.
* Seit AEM 6.1 Forms sind Kommentare nicht standardmäßig verfügbar. Die zuvor hinzugefügten Kommentare stehen in den Assets zur Verfügung, sind jedoch nicht automatisch auf der Oberfläche sichtbar. Sie müssen die Eigenschaft „extendedProperties“ in der AEM Forms-Benutzeroberfläche anpassen, um die Kommentare sichtbar zu machen.
* In einigen früheren Versionen wie LiveCycle ES4 wurde Text mit dem Flex RichTextEditor bearbeitet. Seit AEM 6.1 Forms wird jedoch der HTML-Editor verwendet. Aufgrund dieser Darstellung und des Erscheinungsbilds der Schriftarten, Schriftgrößen und Schriftartränder können sich von den vorherigen Versionen in der Autorenbenutzeroberfläche unterscheiden. Die Buchstaben sehen jedoch beim Rendern gleich aus.
* Listen in Textmodulen wurden verbessert und werden jetzt anders dargestellt. Es kann visuelle Unterschiede geben. Es wird empfohlen, die Buchstaben dort anzuzeigen, wo Sie Listen in Textmodulen verwenden.
* Da Bildinhaltsmodule in DAM-Assets konvertiert werden und Layouts und Fragmente während der Migration zu Formularen hinzugefügt werden, wird die Eigenschaft &quot;Aktualisiert von&quot;für diese Module in &quot;admin&quot;geändert.
* Der Versionsverlauf der Assets wird nicht migriert und steht nach der Migration nicht zur Verfügung. Der nachfolgende Versionsverlauf nach der Migration wird beibehalten.
* Der Status „Veröffentlichungsbereit“ wird seit AEM 6.1 Forms nicht mehr unterstützt, sodass alle Assets mit dem Status „Veröffentlichungsbereit“ den Status „Geändert“ erhalten.
* Da die Benutzeroberfläche auf AEM Forms 6.3 aktualisiert wird, sind die Schritte für die Anpassung ebenfalls unterschiedlich. Sie müssen die Anpassung erneut durchführen, wenn Sie von einer Version vor 6.3 migrieren.
* Layout-Fragmente wurden von /content/apps/cm/layouts/fragmentlayouts/1001 in /content/apps/cm/modules/fragmentlayouts verschoben. Der Datenwörterbuchverweis in Assets zeigt Pfad des Datenwörterbuchs anstatt des Namens an.
* Alle Tabulatorbereiche, die für die Ausrichtung in Textmodulen verwendet werden, müssen angepasst werden. Weitere Informationen finden Sie unter [Correspondence Management - Anordnen von Text mit Tabulatorabständen](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html).
* Die Asset Composer-Konfigurationen ändern sich zu Correspondence Management-Konfigurationen.
* Assets werden in Ordner mit einem Namen wie „Existing Text“ oder „Existing List“ verschoben.

## Verwenden des Migrationsdienstprogramms {#using-the-migration-utility}

### Ausführen des Migrationsdienstprogramms {#runningmigrationutility}

Führen Sie das Migrationsdienstprogramm aus, bevor Sie Änderungen an den Assets vornehmen oder Assets erstellen. Es wird empfohlen, das Dienstprogramm nicht auszuführen, nachdem Sie Änderungen vorgenommen oder Assets erstellt haben. Stellen Sie sicher, dass die Benutzeroberfläche von Correspondence Management oder Adaptive Forms-Assets nicht geöffnet ist, während die Migration ausgeführt wird.

Wenn Sie das Migrationsdienstprogramm zum ersten Mal ausführen, wird ein Protokoll unter dem folgenden Pfad und mit dem folgenden Namen erstellt: `\[aem-installation-directory]\cq-quickstart\logs\aem-forms-migration.log`. Dieses Protokoll wird weiterhin mit Correspondence Management- und Adaptive Forms-Migrationsinformationen aktualisiert, z. B. zum Verschieben von Assets.

>[!NOTE]
>
>Bevor Sie das Migrationsdienstprogramm ausführen, stellen Sie sicher, dass Sie eine Sicherung Ihres CRX-Repositorys durchgeführt haben.

1. Melden Sie sich in einer Browsersitzung bei der AEM-Autoreninstanz als Administrator an.

1. Öffnen Sie die folgende URL im Browser:

   https://[*hostname*]:[*port*]/[*context_path*]/libs/fd/foundation/gui/content/migration.html

   Der Browser zeigt vier Optionen an:

   * AEM Forms-Assets-Migration
   * Migration von benutzerdefinierten adaptiven Formularkomponenten
   * Migration von adaptiven Formularvorlagen
   * Migration von AEM Forms-Cloud-Konfigurationen

1. Führen Sie die folgenden Schritte aus, um die Migration durchzuführen:

   * Um **Assets** zu migrieren, tippen Sie auf „AEM Forms – Asset-Migration“ und auf dem nächsten Bildschirm auf **Migration beginnen**. Die folgenden Elemente werden migriert:

      * Adaptive Formulare
      * Dokumentfragmente
      * Designs
      * Briefe
      * Datenwörterbücher

   >[!NOTE]
   >
   >Während der Migration von Assets werden möglicherweise Warnmeldungen wie &quot;Konflikt gefunden für ...&quot;angezeigt. Solche Benachrichtigungen bedeuten, dass Regeln für einige Komponenten in adaptiven Formularen nicht migriert werden konnten. Beispiel: Wenn bei einer Komponente ein Ereignis auftritt, das sowohl Regeln als auch Skripte umfasst und wenn die Regeln nach einem Skript angewendet werden, wird keine der Regeln für die Komponente migriert. Solche Regeln können jedoch migriert werden, indem der Regeleditor beim Authoring adaptiver Formulare geöffnet wird.
   >
   >Diese Komponenten können migriert werden, indem sie im Regeleditor im Editor für adaptive Formulare geöffnet werden.
   >
   >* Um Regeln und Skripte (für die Aktualisierung von 6.3 nicht erforderlich) in benutzerdefinierten Komponenten zu migrieren, tippen Sie auf „Migration von benutzerdefinierten Adaptive Forms-Komponenten“ und auf dem nächsten Bildschirm auf „Migration beginnen“. Die folgenden Elemente werden migriert:
   >
   >  * Regeln und Skripten, erstellt mithilfe des Regel-Editors (6.1 FP1 und höher)
   >  * Skripte, erstellt mithilfe der Skript-Registerkarte in der Benutzeroberfläche von Version 6.1 oder niedriger
   >* Um Vorlagen zu migrieren (bei einer Aktualisierung von 6.3 nicht erforderlich), tippen Sie auf Adaptive Forms-Vorlagenmigration und tippen Sie im nächsten Bildschirm auf Migration starten . Die folgenden Elemente werden migriert:
   >
   >  * Alte Vorlagen – Vorlagen für adaptive Formulare, erstellt unter /apps mithilfe von AEM 6.1 Forms oder niedriger. Dazu gehören die Skripten, die in den Vorlagenkomponenten definiert wurden.
   >  * Neue Vorlagen – Vorlagen für adaptive Formulare, erstellt mithilfe des Vorlagen-Editors unter /conf. Das umfasst die Migration von Regeln und Skripten, die mithilfe des Regel-Editors erstellt wurden.


   * Um benutzerdefinierte Komponenten für adaptive Formulare zu migrieren, tippen Sie auf **Migration benutzerdefinierter Komponenten für adaptive Formulare** und auf der Seite „Migration von benutzerdefinierten Komponenten“ auf **Migration beginnen**. Die folgenden Elemente werden migriert:

      * Benutzerdefinierte Komponenten, die für Adaptive Forms geschrieben wurden
      * Komponentenüberlagerungen, falls vorhanden.
   * Um Vorlagen für adaptive Formulare zu migrieren, tippen Sie auf **Migration von Vorlagen für adaptive Formulare** und auf der Seite „Migration von benutzerdefinierten Komponenten“ auf **Migration beginnen**. Die folgenden Elemente werden migriert:

      * Adaptive Formularvorlagen, die mit dem Vorlagen-Editor unter /apps oder /conf erstellt wurden AEM.
   * Migrieren Sie die AEM Forms Cloud-Konfigurationsdienste, um das neue kontextbezogene Cloud-Dienst-Paradigma zu nutzen, das die Benutzeroberfläche mit Touch-Funktion (unter/conf) umfasst. Wenn Sie Services der Cloud-Konfiguration von AEM Forms migrieren, werden die Cloud-Services in /etc nach /conf verschoben. Wenn Sie keine Anpassungen von Cloud-Services haben, die von den veralteten Pfaden (/etc) abhängen, wird empfohlen, dass Sie das Migrationsdienstprogramm direkt nach dem Upgrade auf 6.4 ausführen und die Cloud-Konfigurations-Benutzeroberfläche mit Touch-Funktion für alle weiteren Arbeiten verwenden. Wenn Sie über Anpassungen für die bereits vorhandene Cloud-Dienste verfügen, setzen Sie die klassische Benutzeroberfläche bei der Aktualisierung fort, bis die Anpassungen für die migrierten Pfaden (/conf) abgeschlossen sind, und führen Sie das Migrationshilfsprogramm aus.

   Um **AEM Forms-Cloud-Dienste** zu migrieren, die Folgendes umfassen, tippen Sie auf „AEM Forms-Cloud-Konfigurationsmigration“ (die Cloud-Konfigurationsmigration ist unabhängig vom AEMFD-Kompatibilitätspaket) und dann auf der Seite „Konfigurationsmigration“ auf **Migration starten**:

   * Cloud-Services für das Formulardatenmodell

      * Quellpfad: /etc/cloudservices/fdm
      * Zielpfad: /conf/global/settings/cloudconfigs/fdm
   * reCAPTCHA

      * Quellpfad: /etc/cloudservices/recaptcha
      * Zielpfad: /conf/global/settings/cloudconfigs/recaptcha
   * Acrobat Sign

      * Quellpfad: /etc/cloudservices/echosign
      * Zielpfad: /conf/global/settings/cloudconfigs/echosign
   * Cloud-Dienste für Typekit

      * Quellpfad: /etc/cloudservices/typekit
      * Zielpfad: /conf/global/settings/cloudconfigs/typekit

   Im Browserfenster wird während der Migration Folgendes ausgeführt: 

   * Wenn die Assets aktualisiert werden: Assets wurden erfolgreich aktualisiert.
   * Nach Abschluss der Migration: Die Migration für Assets wurde abgeschlossen.

   Wenn das Migrationsdienstprogramm ausgeführt wird, führt es Folgendes aus:

   * **Fügt die Tags zu den Assets hinzu**: Fügt das Tag &quot;Correspondence Management: Migrierte Assets&quot;/ &quot;Adaptive Forms : Migrierte Assets&quot;. zu den migrierten Assets hinzu, damit Benutzende die migrierten Assets ermitteln können. Wenn Sie das Migrationsdienstprogramm ausführen, werden alle im System vorhandenen Assets mit „Migriert“ markiert. 
   * **Erstellt Tags**: Die Kategorien und Unterkategorien, die im Vorgängersystem vorhanden sind, werden als Tags erstellt, und dann werden diese Tags den entsprechenden Correspondence Management-Assets in AEM zugeordnet. Beispielsweise werden eine Kategorie (Schadensmeldungen) und eine Unterkategorie (Schadensmeldungen) einer Briefvorlage als Tags generiert.
   * **Verschiebt Layouts und Layout-Fragmente auf die Benutzeroberfläche AEM 6.4 Forms**: Wenn Sie von 6.2 auf 6.4 aktualisieren, werden die Layout-Vorlagen und Layout-Fragmente als Formulare in der Benutzeroberfläche von AEM Forms 6.4 hinzugefügt.

   >[!NOTE]
   >
   >Wenn Sie ein Upgrade von 6.2 auf 6.4 durchführen, werden in der Benutzeroberfläche unter Umständen neue Ordner angezeigt, die Ihre Assets enthalten. Möglicherweise müssen Sie diese Ordner überprüfen, um Ihre Assets zu finden.

1. Fahren Sie nach der Ausführung des Migrationsdienstprogramms mit den [Systemverwaltungsaufgaben](#housekeepingtasks) fort.

### Systemverwaltungsaufgaben nach Ausführung des Migrationsdienstprogramms {#housekeepingtasks}

Nachdem Sie das Migrationsdienstprogramm ausgeführt haben, führen Sie die folgenden Systemverwaltungsaufgaben durch:

1. Stellen Sie sicher, dass die XFA-Version 3.3 oder eine spätere Version von Layouts und Fragment-Layouts verwendet wird. Wenn Sie Layouts und Fragment-Layouts einer älteren Version benutzen, könnte es Probleme beim Rendern des Briefs geben. Um ein älteres XFA auf die neueste Version zu aktualisieren, führen Sie folgende Schritte aus:

   1. [Herunterladen von XFA- als ZIP-Datei](/help/forms/using/import-export-forms-templates.md#p-import-and-export-assets-in-correspondence-management-p) aus der Forms-Benutzeroberfläche.
   1. Extrahieren Sie die Datei.
   1. Öffnen Sie die XFA-Datei im neuesten Designer und speichern Sie sie. Die Version des XFA wird auf die neueste Version aktualisiert.
   1. Laden Sie die XFA in die Forms-Benutzeroberfläche hoch.

1. Veröffentlichen Sie alle Assets, die vor der Migration im vorherigen System veröffentlicht wurden. Das Migrationsdienstprogramm aktualisiert die Assets nur im Autorenmodus. Um die Assets in der Veröffentlichungsinstanz (s) zu aktualisieren, müssen Sie die Assets veröffentlichen. 
1. In AEM Forms 6.4 werden einige Rechte der Benutzergruppen für Formulare geändert. Wenn Sie möchten, dass Ihre Benutzer XDPs und adaptive Forms mit Skripten hochladen oder den Code-Editor verwenden können, müssen Sie diese zur Gruppe der Formularbenutzer hinzufügen. Ebenso können Vorlagenautoren den Code-Editor im Regeleditor nicht mehr verwenden. Damit Benutzer den Code-Editor verwenden können, fügen Sie sie der Gruppe „af-template-script-writers“ hinzu. Anweisungen zum Hinzufügen von Benutzern zu Gruppen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md).
