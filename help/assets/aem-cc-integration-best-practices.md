---
title: Best Practices für die Integration von AEM und Creative Cloud
description: Best Practices zur Integration einer AEM-Bereitstellung mit Adobe Creative Cloud, um die Workflows der Asset-Übertragung zu optimieren und eine maximale Effizienz zu erzielen
contentOwner: AG
feature: Collaboration,Adobe Asset Link,Desktop App
role: Business Practitioner,Administrator
exl-id: cb9bea05-3359-4fb4-b935-59e522a5f387
translation-type: tm+mt
source-git-commit: 257355371068cdb47f75a0a17ea4831e10dc6a69
workflow-type: tm+mt
source-wordcount: '3578'
ht-degree: 85%

---

# Best Practices für die Integration von AEM und Creative Cloud {#aem-and-creative-cloud-integration-best-practices}

<!-- TBD: Reconcile with 6.5 article that's ahead of this article now in terms of content streamlining and structuring.
-->

Adobe Experience Manager Assets ist eine DAM-Lösung (Digital Asset Management), die in Adobe Creative Cloud integriert werden kann, um DAM-Benutzer bei der Zusammenarbeit mit Kreativteams zu unterstützen und so die Zusammenarbeit bei der Inhaltserstellung zu optimieren.

Adobe Creative Cloud bietet Kreativ-Teams ein System von Lösungen und Services, um digitale Assets zu erstellen. Dieses Angebot enthält Desktop-Programme und Mobile Apps, Cloud-Services wie Speicher mit Desktop-Synchronisierung oder Web-Erlebnis sowie Marktplätze wie Adobe Stock.

Lesen Sie weiter, um mehr darüber zu erfahren, welche Integration Sie zwischen Desktop und DAM-Enterprise-System abhängig vom Nutzungsszenario und von den entsprechenden Best Practices für die Verbindungs-Workflows wählen sollten.

>[!NOTE]
>
>Die Freigabe von AEM zum Creative Cloud-Ordner wird nicht mehr unterstützt und in diesem Handbuch nicht mehr behandelt. Adobe empfiehlt die Verwendung neuerer Funktionen wie [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html) oder [AEM Desktop-App](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html?lang=de), um kreativen Benutzern Zugriff auf in AEM verwaltete Assets zu gewähren.

## Anforderungen an die Zusammenarbeit von Kreativen, Marketingexperten und DAM-Benutzern {#collaboration-needs-of-creatives-marketers-and-dam-users}

| Voraussetzungen | Anwendungsfall | Betroffene Oberflächen |
|---|---|---|
| Vereinfachtes Desktop-Erlebnis für Kreative | Für Kreativprofis oder, ganz allgemein, für Desktop-Benutzer, die mit nativen Programmen zur Asset-Erstellung arbeiten, soll der Zugriff auf Assets von einem DAM-System (AEM Assets) optimiert werden. Sie benötigen eine einfache und unkomplizierte Möglichkeit zum Entdecken, Verwenden (Öffnen), Bearbeiten und Speichern von Änderungen in AEM sowie zum Hochladen neuer Dateien. | Windows- oder Mac-Desktop, Creative Cloud-Programme |
| Bereitstellen von hochwertigen, gebrauchsfertigen Assets aus Adobe Stock | Marketer tragen zu einer schnelleren Inhaltserstellung bei, indem sie beim Beschaffen von und Suchen nach Assets helfen. Kreativprofis verwenden die genehmigten Assets direkt in ihren Kreativ-Tools. | AEM Assets, Adobe Stock Marketplace, Metadatenfelder |
| Verteilen und Freigeben von Assets nach Organisationen | Interne Abteilungen/Zweigstellen und externe Partner, Distributoren und Agenturen verwenden die genehmigten Assets, die von der übergeordneten Organisation freigegeben wurden. Die Organisation möchte die erstellten Assets sicher und nahtlos für eine größere Wiederverwendung freigeben. | Brand Portal, Asset Share Commons |

## Adobe-Angebote zur Unterstützung von Kooperationsbedarf {#adobe-offerings-to-support-the-collaboration-need}

| Wertangebot für die betroffenen Benutzer | Adobe-Angebot | Betroffene Oberflächen |
|---|---|---|
| Kreativbenutzer entdecken Assets aus AEM, öffnen und verwenden diese, führen Bearbeitungen durch und laden AEM-Änderungen sowie neue Dateien in AEM hoch, ohne Creative Cloud-Programme verlassen zu müssen. | [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) | Photoshop, Illustrator und InDesign |
| Geschäftsbenutzer vereinfachen das Öffnen und Verwenden von Assets, führen Bearbeitungen durch und laden AEM-Änderungen sowie neue Dateien aus der Desktop-Umgebung in AEM hoch. Sie nutzen eine generische Integration, um jeden Asset-Typ in nativen Desktop-Applikationen, auch Adobe-fremden, zu öffnen. | [AEM-Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de) | AEM-Desktop-Programm auf Windows- und Mac-Desktop |
| Marketer und Geschäftsbenutzer können Adobe Stock-Assets in AEM entdecken, in einer Vorschau anzeigen, lizenzieren sowie speichern und verwalten. Lizenzierte und gespeicherte Assets liefern ausgewählte Adobe Stock-Metadaten für eine bessere Governance. | [Integration von Experience Manager und Adobe Stock](aem-assets-adobe-stock.md) | AEM-Web-Oberfläche |

Dieser Artikel konzentriert sich in erster Linie auf die ersten beiden Aspekte der Zusammenarbeit. Die Verteilung und Beschaffung von Vermögenswerten im entsprechende Maß wird kurz als Verwendungsfall genannt. Für solche Lösungen sollten Sie Adobe Brand Portal oder Asset Share Commons beachten. Alternativlösungen wie [Markenportal](https://helpx.adobe.com/de/experience-manager/brand-portal/user-guide.html), Lösungen, die basierend auf [Asset-Freigabe-Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/)-Komponenten erstellt werden können, [Linkfreigabe](/help/assets/link-sharing.md), unter Verwendung von [Experience Manager-Assets](/help/assets/managing-assets-touch-ui.md) sollten auf der Grundlage spezifischer Anforderungen überprüft werden.

![Creative Cloud-Verbindungen für AEM: Festlegen der zu verwendenden Funktion](assets/creative-connections-aem.png)

<!-- 
## Terms and definitions {#terms-and-definitions}

The terms used in this document may have a different meaning in other contexts. In particular, the following terms pertaining to the digital asset lifecycle are used when referring to workflows between a creative professional's desktop and DAM:

* **Work-in-progress or creative work-in-progress (WIP):** A phase in asset lifecycle where an asset undergoes multiple changes and is typically not yet ready to be shared with broader teams.
* **Creative-ready assets:** Assets that are ready to be shared with a broader team, or have been  selected / approved  by the creative team for sharing with marketing or LOB teams.
* **Asset approvals:** The approval process that runs for assets already uploaded to DAM, which typically includes brand approvals, legal approvals, and so on.
* **Final asset:** An asset that has gone through all  approvals/metadata  tagging and is ready to be used by the broader team. Such an asset is stored in DAM and made available to all (or all interested) users. It can be used in marketing channels or by creative teams to create designs.
* **Minor asset  update/change:** A quick and small change to a digital asset. It is often made in response to a retouching or minor editing request, asset review, or approval (for example, reposition, change text size, adjust saturation/brightness, color, and so on).
* **Major asset  update/change:** A change to a digital asset that requires considerable work, and sometimes must be done over a longer period of time. It typically includes multiple changes. The asset must be saved multiple times while being updated. Major asset updates typically cause the asset to enter a WIP stage.
* **DAM:** Digital asset management. In this document, it is synonymous with AEM Experience Manager Assets, unless specifically mentioned otherwise.
* **Creative user:** A creative professional, who creates digital assets using Creative Cloud apps and services. In some cases, a creative user may be a member of a creative team who may use Creative Cloud, but does not create digital assets (like a creative director or creative team manager).
* **DAM user:** A typical user of a DAM system. Depending on the organization, a DAM user can be a marketing or a non-marketing user, for example a Line-of-Business (LOB) user, librarian, sales person, and so on.
-->

### Zuordnung von Anwendungsfällen

| Anwendungsfall | AEM-Desktop-Programm | Ordnerfreigabe | Andere Lösungen |
|---|---|---|---|
| Freigeben einer kleineren Anzahl (1) von DAM-Assets für einen Creative-Benutzer | ✔ | they |  |
| Freigeben einer größeren Anzahl (2) von DAM-Assets für einen Creative-Benutzer | ✔ | ✘ | [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) <br> [Asset-Freigabe](assets-finder-editor.md) |
| Freigabe von DAM-Assets für Benutzer, die Zugriff auf DAM haben | ✔ | they | [Link-Freigabe](link-sharing.md) |
| Freigabe von DAM-Assets für Benutzer, die keinen Zugriff auf DAM haben | ✘ | ✔ | [Markenportal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) <br> [Asset-Freigabe](assets-finder-editor.md) |
| Speichern einer kleineren Anzahl/Menge von Assets in DAM | ✔ | they | [Hochladen über die Web-Benutzeroberfläche](managing-assets-touch-ui.md) |
| Speichern Sie mehr Assets in DAM (3) | ✔ | ✘ | [Hochladen über die Web-Benutzeroberfläche](managing-assets-touch-ui.md)  <br> Benutzerdefiniertes Skript/Tool |
| Migrieren einer sehr großen Anzahl von Assets zu DAM | ✘ | ✘ | [Migrationshandbuch](assets-migration-guide.md) |
| Schnelles Öffnen eines Assets auf dem Desktop | ✔ | ✘ |  |
| Schnelles Öffnen und Ändern eines Assets auf dem Desktop | ✔ | ✘ |  |

Die Legende für die Symbole:

* ✔✔: bevorzugte Lösung
* ✔: akzeptable Lösung
* ✘: sollte nicht für das Nutzungsszenario verwendet werden

Zusätzliche Hinweise:

* (1) Kleinere Anzahl von Assets: z. B. ein kleiner Satz von Assets, die mit einem Projekt oder einer Kampagne zusammenhängen
* (2) Größere Anzahl von Vermögenswerten: zum Beispiel alle genehmigten Assets in der Organisation
* (3) Verwenden Sie AEM Funktion zum Hochladen von Ordnern für Desktopanwendungen

Um Nutzungsszenarien zum Verteilen von Assets zu unterstützen, sollten andere Lösungen in Betracht gezogen werden:

* [ Brand Portal](https://helpx.adobe.com/experience-manager/brand-portal/user-guide.html) für ein konfigurierbares SaaS-Add-on für AEM Assets, um Assets zu veröffentlichen
* Benutzerdefinierte Lösungen, erstellt auf Grundlage der [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/)-Code-Basis
* AEM-[Linkfreigabe](/help/assets/link-sharing.md), um Assets ad hoc mithilfe von Links freizugeben
* [AEM Assets-Web-Oberfläche](/help/assets/managing-assets-touch-ui.md) mit Bereichen für externe Parteien, die durch Einrichtung einer AEM-Zugriffssteuerung abgesichert sind, und mit notwendigem IT-/Netzwerkkonfigurationsanpassungen, wodurch diese externen Benutzer Zugriff auf AEM erhalten

## Grundlegende Konzepte und Nutzungsszenarien {#key-concepts-and-use-cases}

### Glossar der allgemeinen Begriffe {#glossary-of-common-terms}

* **Laufende Arbeit oder laufende kreative Arbeit (Work-In-Progress, WIP):** Eine Phase im Asset-Lebenszyklus, in der ein Asset mehrfach geändert wird und in der Regel noch nicht zur Freigabe für breitere Teams bereit ist.
* **Fertige Kreativ-Assets:** Assets, die für ein breiteres Team freigegeben werden können oder die vom Kreativ-Team für die Freigabe mit Marketing- oder LOB-Teams ausgewählt/genehmigt wurden.
* **Asset-Genehmigungen:** Der Genehmigungsprozess, der für Assets ausgeführt wird, die bereits auf DAM hochgeladen wurden. Dazu gehören in der Regel Markengenehmigungen, Genehmigungen usw.
* **Abgeschlossenes Asset:** Ein Asset, für das alle    Genehmigungen/Metadaten-Tagging durchgeführt wurden und das bereit für die Verwendung durch das breitere Team ist. Ein solches Asset wird in DAM gespeichert und allen (bzw. allen interessierten) Benutzern zur Verfügung gestellt. Es kann in Marketing-Kanälen oder von Kreativ-Teams verwendet werden, um Designs zu erstellen.
* **Kleinere Asset-Aktualisierung/-Änderung:** Schnelle, kleine Änderung an einem digitalen Asset. Diese wird häufig aufgrund einer Retuschieranfrage oder einer kleineren Bearbeitungsanfrage, einer Asset-Überprüfung oder einer Genehmigung (z. B. Neupositionierung, Änderung der Textgröße, Anpassung der Sättigung/Helligkeit, Farbe usw.) durchgeführt.
* **Größere Asset-Aktualisierung/-Änderung:** Änderung eines digitalen Assets, die viel Arbeit erfordert und manchmal über einen längeren Zeitraum erfolgen muss. Diese umfasst in der Regel mehrere Änderungen. Das Asset muss während der Aktualisierung mehrmals gespeichert werden. Bei umfangreichen Asset-Aktualisierungen wird das Asset in der Regel in eine WIP-Phase versetzt.
* **DAM:** Digital Asset Management. In diesem Dokument wird der Begriff synonym mit AEM Experience Manager-Assets verwendet, sofern nicht ausdrücklich anders angegeben.
* **Kreativer Benutzer:** Kreativprofi, der digitale Assets mit Creative Cloud-Programmen und -Services erstellt. In einigen Fällen kann ein kreativer Benutzer Mitglied eines Kreativ-Teams sein, das möglicherweise Creative Cloud verwendet, aber keine digitalen Assets erstellt (z. B. Creative Director oder Creative Team Manager).
* **DAM-Benutzer:** Ein typischer Benutzer eines DAM-Systems. Je nach Organisation kann ein DAM-Benutzer ein Marketing- oder Nicht-Marketing-Benutzer sein, z. B. Branchenbenutzer, Bibliothekar, Vertriebsmitarbeiter usw.

### Überlegungen zur Integration von AEM und Creative Cloud {#considerations-when-using-aem-and-creative-cloud-integration}

* Siehe [Best Practices für die Desktop-App](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/troubleshoot.html?lang=en#best-practices-to-prevent-troubles)
* Siehe [Adobe Stock-Integration](aem-assets-adobe-stock.md)
* Weitere Informationen finden Sie unter [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)

Dies ist eine kurze Zusammenfassung der Best Practices für die Integration von Experience Manager und Creative Cloud. Lesen Sie den Rest dieses Dokuments, um detaillierte Informationen dazu zu erhalten.

* **Für kreative Benutzer, die in Photoshop, InDesign oder Illustrator arbeiten:** Adobe Asset Link bietet ein optimales Benutzererlebnis, einschließlich der ordnungsgemäßen Abwicklung laufender Arbeiten von aus AEM ausgecheckten Assets.
* **Für einen vereinfachten Desktop-Zugriff auf Assets bei beliebigen allgemeinen Dateiformaten oder Programmen:** Verwenden Sie das AEM-Desktop-Programm.
* **Verstehen, warum und wann Assets in DAM gespeichert werden:** Aktualisierungen, die dem breiteren Team in Ihrer Organisation zur Verfügung zu stellen sind.
* **Beachten des Volumens freigegebener Assets:** Wenn Ihr Anwendungsfall die Asset-Verteilung ist, könnten Governance und Sicherheit die wichtigsten Aspekte sein. Erwägen Sie die Verwendung von Tools, die für eine skalierte Vorgehensweise entwickelt wurden, wie z. B. Brand Portal.
* **Wissenswertes über den Asset-Lebenszyklus:** Sie müssen wissen, welche Assets in Ihrer Organisation von den verschiedenen Teams genutzt werden.
* **Sorgfältige Verarbeitung häufiger Asset-Speichervorgänge:** Adobe Asset Link übernimmt diese Aufgabe für Sie – mit PS, AI und ID. Führen Sie für andere Programme keine laufenden Arbeitsaufgaben im zugeordneten/freigegebenen Ordner aus, es sei denn, Sie benötigen alle Änderungen in DAM.

### Zugreifen auf Adobe Stock Assets über AEM Assets {#access-to-adobe-stock-assets-from-aem-assets}

[Die Integration von AEM und Adobe Stock](/help/assets/aem-assets-adobe-stock.md) ermöglicht AEM-Anwendern die Suche, Vorschau, Lizenzierung und Speicherung von Assets aus Adobe Stock in AEM. Lizenzierte und gespeicherte Adobe Stock-Assets verfügen über ausgewählte Adobe Stock-Metadaten, mit denen Suchvorgänge über zusätzliche Filter durchgeführt werden können.

Einige wichtige Punkte zu dieser Integration:

* Wenn Assets aus Adobe Stock in AEM gespeichert werden, werden sie zu regulären AEM Assets. Die Binärdateien werden dabei im AEM-Repository gespeichert. Einige zu Adobe Stock gehörige Metadaten werden für das Asset in AEM gespeichert. Ansonsten verläuft die Erfassung wie bei jeder anderen Datei. Wenn beispielsweise Smart-Tags aktiv sind, werden die Tags beim Speichern diesen Assets hinzugefügt.
* Das in AEM gespeicherte Asset ist eine Kopie, kein Link zurück zu Adobe Stock.

**Arbeiten mit Assets in Creative Cloud, die aus Adobe Stock in AEM gespeichert wurden.** Diese Integration ist zwar unabhängig von Adobe Asset Link, aber Adobe Asset Link erkennt diese so aus Adobe Stock gespeicherten Assets und zeigt zusätzliche Metadaten sowie ein Adobe Stock-Symbol auf diesen Assets in der Adobe Asset Link-Erweiterungsoberfläche in Photoshop, Illustrator bzw. InDesign an. Die Dateien sind zum Durchsuchen, Öffnen usw. verfügbar, da sie durch Speichern in AEM zu regulären AEM Assets werden.
Kreative Benutzer, die in Creative Cloud-Programmen mit vorhandener Adobe Asset Link-Erweiterung arbeiten, haben zusätzlich zum Zugriff auf bereits lizenzierte Assets von Adobe Stock in AEM auch Zugriff auf das Creative Cloud Libraries-Bedienfeld, um Adobe Stock-Assets zu suchen, in einer Vorschau anzuzeigen und zu lizenzieren.
Lizenzierte und in AEM gespeicherte Assets aus Adobe Stock werden breiter gefassten Teams zur Verfügung gestellt, die auf die AEM Assets-Implementierung zugreifen. Kreative hingegen, die Assets aus Adobe Stock über das Creative Cloud Libraries-Bedienfeld lizenzieren, können sich die Assets selbst lediglich standardmäßig in ihrem Creative Cloud-Konto zur Verfügung stellen.

<!-- 
TBD: A condensed version of the below content is better placed in the Adobe DAM article.
-->

## Informationen zum Speichern von Assets in DAM {#about-storing-assets-in-a-dam}

Für das Entwickeln eines effizienten Workflows zwischen Kreativ-Teams und Marketing-/Branchen-Teams sowie für die Auswahl der besten Begleitfunktionen ist es wichtig zu verstehen, wann und warum Assets in DAM gespeichert werden.

### Warum Assets in DAM gespeichert werden  {#why-assets-are-stored-in-dam}

Das Speichern von Assets in DAM macht sie leicht zugänglich und auffindbar. Es wird sichergestellt, dass die Assets von verschiedenen Benutzern in der gesamten Organisation oder im gesamten System genutzt werden, z. B. von Kunden, Partnern usw.

Die meisten Organisationen entscheiden sich dafür, nur Assets zu speichern, die relevant sind für die nachgelagerten Marketing-/Branchenprozesse (Veröffentlichen in Kanälen wie dem Internet über AEM Sites oder anderen Kanälen wie Marketing Cloud oder Advertising Cloud, die von Adobe Experience Cloud bereitgestellt und von Analytics Cloud bewertet werden, Bereitstellung für Benutzer/Partner usw.). Außerdem speichern Organisationen Assets, für die möglicherweise ein Prüfungs-/Genehmigungsprozess in DAM erfolgt. Auf diese Weise werden hauptsächlich Assets in DAM gespeichert, die mit hoher Wahrscheinlichkeiten genutzt werden, und das Speichern von Assets im Leerlauf wird vermieden.

Die Speicherung von Assets hängt außerdem von Überlegungen zu technischen Aspekten und zur Ressourcennutzung ab. DAM bietet zusätzliche Services rund um gespeicherte Assets, darunter Extrahieren von Metadaten, Versionierung, Erstellen von Vorschauen/Transcodierung, Verwalten von Referenzen und Hinzufügen von Informationen zur Zugriffssteuerung. Diese Services erfordern zusätzlich Zeit und Infrastrukturressourcen.

Häufig ist das Speichern aller Assets und Aktualisierungen nicht empfehlenswert. Beispiel: Wenn Aktualisierungen von schlechter Qualität sind und einen unverhältnismäßigen Ressourcenverbrauch aufweisen, sollten die Assets nicht in DAM gespeichert werden.

### Wann Assets in DAM gespeichert werden   {#when-assets-are-stored-in-dam}

Kreativ-Teams (und Organisationen) sind in der Regel nicht daran interessiert, Assets in jeder Phase des Asset-Lebenszyklus zu speichern. Beispielsweise vermeiden sie das Speichern von Assets in den folgenden Fällen:

* Assets, die noch nicht abgeschlossen sind, oder zum Experimentieren verwendet werden
* Assets, die den Prüfungszyklus des Kreativ-Teams/internen Teams nicht bestehen
* Verglichen mit dem betreffenden Asset verfügt das Team über bessere Beispiele für seine Arbeit, um sie externen Teams vorzustellen.

In der Regel werden Assets der folgenden Klassen in DAM gespeichert:

* Assets, die einen bestimmten Reifegrad erreicht haben und als bereit zur Freigabe für andere Benutzer gelten
* Assets, die vorab vom Kreativ-Team ausgewählt wurden
* Bestimmte Asset-Formate, die vom Marketing-Team verwendet werden können oder abhängig von einem bestimmten Vertrag bzw. einer Vereinbarung angefordert wurden (z. B. aus RAW-Dateien konvertierte JPG-Dateien, TIFF-Dateien/-Bilder aus PSD-Originaldateien)

### Wann Aktualisierungen von Assets in DAM gespeichert werden   {#when-updates-to-assets-are-stored-in-dam}

In der Regel sollten nur Aktualisierungen von Assets in DAM gespeichert werden, die für den Großteil der DAM-Benutzer relevant sind. Dadurch wird sichergestellt, dass Benutzern (Marketing- und ähnliche Funktionen) in der DAM-Asset-Zeitleiste nur relevante Versionen angezeigt werden.

Normalerweise handelt es sich dabei um Änderungen in Bezug auf die wichtigsten Meilensteine im Asset-Lebenszyklus. Beispielsweise sollte das ursprüngliche fertige Kreativ-Asset oder eine offizielle Aktualisierung basierend auf einer Anforderung/Überprüfung durch das Kreativteam in DAM gespeichert und versioniert werden.

Die Aktualisierung des Kreativ-Teams zur Überprüfung durch das Marketing-Team nach einer Änderungsanfrage für ein vorhandenes Asset in DAM ist ein Beispiel für eine relevante Aktualisierung. Diese sollte als Referenzmaterial oder zum Zurücksetzen auf die letzte Version in DAM gespeichert und versioniert werden.

Es folgen Beispiele für Updates, die normalerweise nicht relevant sind:

* Frühe Versionen von Assets, die hochgeladen wurden, bevor sie für die Marketingüberprüfung bereit waren
* Häufige kreative Änderungen am Asset in der WIP-Phase, bevor das Kreativteam das Asset für fertig erklärt

### Benutzerzugriff auf DAM {#user-access-to-dam}

AEM Assets unterstützt zwei Arten von Benutzern, die auf deren Zugriff auf die AEM Assets-Implementierung basieren. Normalerweise haben Benutzer innerhalb des Unternehmensnetzwerks (Firewall) direkten Zugriff auf DAM. Andere Benutzer außerhalb des Unternehmensnetzwerks haben dagegen keinen direkten Zugriff. Der Benutzertyp bestimmt, welche Integrationen aus technischer Sicht verwendet werden können.

#### Kreative Benutzer mit direktem Zugriff auf DAM   {#creative-users-with-direct-access-to-dam}

In der Regel haben interne Kreativ-Teams oder Agenturen/Kreativprofis, die an das interne Netzwerk angeschlossen sind, Zugriff auf die DAM-Instanz, einschließlich AEM-Anmeldung.

In solchen Fällen bietet AEM Desktop-App einfachen Zugriff auf endgültige/genehmigte Assets und ermöglicht Ihnen das Speichern kreativer Assets in DAM.

#### Kreative Benutzer ohne Zugriff auf DAM {#creative-users-without-access-to-dam}

Externe Agenturen oder Freiberufler ohne direkten Zugriff auf die DAM-Instanz benötigen möglicherweise Zugriff auf genehmigte Assets oder möchten ihre neuen Designs in DAM hinzufügen.

In solchen Fällen können Sie die AEM-/Creative Cloud-Integration nutzen, um den Workflow zu verbessern. Die Voraussetzung ist, dass die kreativen Benutzer über eine Adobe ID und ein Creative Cloud-Konto mit Speicherdienst verfügen.

Stellen Sie mit den folgenden Strategien Zugriff auf abgeschlossene/genehmigte Assets bereit:

* So erhalten Sie Zugriff auf eine große Anzahl von Assets: Verwenden Sie [AEM Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html?lang=de) oder die Implementierung von [Asset Share](assets-finder-editor.md) durch den Kunden in AEM Veröffentlichungsinfrastruktur

* So stellen Sie Zugriff auf einige Assets bereit: AEM Freigabe von Ordnern mit Adobe Creative Cloud kann zusätzlich zu AEM Assets Brand Portal oder Asset Share verwendet werden. Bitte beachten Sie, dass es bestimmte Einschränkungen in Bezug auf diese Integration gibt, die in diesem Artikel ausführlicher behandelt werden.

### Anwendungsfälle {#use-cases}

In den folgenden Nutzungsszenarios werden verschiedene Arten von Workflows zwischen DAM und dem Desktop des Designers beschrieben.

#### Erstellen Sie neue Entwürfe mit Assets aus DAM {#creating-new-designs-using-assets-from-dam}

Das folgende Diagramm illustriert den Lebenszyklus von digitalen Assets. Es veranschaulicht, wie kreative Benutzer und DAM-Benutzer (Marketingexperten, Branchenbenutzer) vorhandene Assets nutzen, zur Erstellung weiterer Assets verwenden und zur Genehmigung senden.

![chlimage_1-301](assets/chlimage_1-301.png)

Der Asset-Lebenszyklus umfasst die folgenden Phasen:

1. Freigabe genehmigter Assets in Creative Desktop: Abgeschlossene Assets aus DAM werden kreativen Benutzern (auf dem Desktop) zur Verfügung gestellt.
1. Erstellen eines neuen Designs (kreatives digitales Asset): Eine neue Datei wird im Bereich für laufende Arbeit (WIP) gespeichert.
1. Verwenden (platzieren) Sie genehmigte Assets in einem neuen Entwurf: Der kreative Benutzer erstellt ein neues Asset mit vorhandenen genehmigten Assets in Creative Cloud-Apps
1. Häufiges Speichern von WIP-Aktualisierungen: Der kreative Benutzer iteriert schnell und speichert die Datei häufig. In dieser Phase kann der kreative Benutzer mit anderen zusammenarbeiten, aber die häufig gespeicherten Aktualisierungen sind  für DAM-Benutzer in der Regel uninteressant.
1. Das Asset erreicht den Status „fertiges Kreativ-Asset“ und wird im entsprechenden Ordner gespeichert.
1. Asset-  update : Eine Asset-Aktualisierung oder eine neue Datei steht Benutzern in DAM zur Verfügung
1. Das Asset wird produziert: Dies ist ein DAM-Prozess, der je nach Organisation Tagging, Genehmigungen und eine sich ändernde Zugriffskontrolle umfassen kann. In dieser Phase gilt das Asset als abgeschlossen und kann von größeren Teams verwendet werden, die DAM nutzen. Es kann auch von kreativen Benutzern zum Erstellen weiterer Assets verwendet werden.

Hier finden Sie einige allgemeine Empfehlungen zur Verwaltung von Assets während dieses Prozesses:

* Verwenden Sie einen dedizierten Speicherbereich bzw. ein dediziertes Speichersystem wie den synchronisierten Ordner von Adobe Creative Cloud Assets für die WIP-Dateien: Häufige Aktualisierungen, die für DAM-Benutzer nicht relevant sind, werden am besten in einem dedizierten System anstatt in AEM Assets verarbeitet. WIP-Assets können mit der Adobe Creative Cloud-Desktopanwendung auf eine lokale Festplatte synchronisiert, auf einer lokalen Datenspeicherung gespeichert usw. werden.
* Verwenden Sie getrennte Ordner/Freigaben für abgeschlossene Assets und Assets, die in DAM hochgeladen werden: Der Übersichtlichkeit wegen sollten sich abgeschlossene Assets (Beispiel „Final“ oben) als auch Assets, die wieder in DAM hochgeladen werden („Creative Ready“ oben), in einem eigenen zugeordneten/freigegebenen Ordner befinden.

#### Vorhandene Assets ändern, die in DAM verwaltet werden{#changing-existing-assets-managed-in-dam}

In einigen Fällen können Assets in DAM Änderungen erfordern. Beispiele dafür sind:

* Anforderung von Änderungen an Assets nach der Überprüfung und Genehmigung in AEM Assets
* Wesentliche Aktualisierungen von vorhandenen abgeschlossenen Assets
* Schnelle Bearbeitungen einer vorhandenen Datei (insbesondere bevor diese abschließend genehmigt wird)

In solchen Fällen bietet die AEM Desktop App die einfachste Methode, diese Aufgaben zu erledigen.

![chlimage_1-302](assets/chlimage_1-302.png)

Hier wird der Ereignisablauf im Diagramm dargestellt:

<!-- TBD for formatting. 
This article will get fixed automatically when 6.5 content is ported to it.
And 6.5 content will be ported after updating it for AEM desktop app 2.0 best practices.
And it will be updated for DA2.0 best practices after 6.5 repo is available for writers to edit content in.
-->

* **1:** Geben Sie das Asset von DAM auf den Desktop frei oder öffnen Sie es direkt auf dem Desktop in der gewünschten Anwendung (z. B. Adobe Photoshop usw.). Das Auschecken wird empfohlen, um die Datei zu sperren.
* **2:** Geringfügige Aktualisierung: Bearbeiten Sie die Datei und speichern Sie die Änderungen.
* Alternativer Ablauf zu Schritt 2

   * **A:** Wesentliche Aktualisierung: Wenn die Datei mehrere aufwendige Änderungen erfordert, sollte sie von Zeit zu Zeit gespeichert und in einen Ordner/Bereich für laufende Arbeit kopiert werden.
   * **B:** Die Arbeit an der Datei wird in den WIP-Ordnern fortgesetzt. Die gespeicherten Änderungen werden nicht mit der Version in DAM synchronisiert.
   * **C:** Nach Abschluss der Aktualisierungen wird die Datei wieder in den zugeordneten Ordner kopiert oder dort gespeichert.

* **3:** Asset-Aktualisierungen werden in DAM übernommen. Checken Sie das Asset ein, um es zu entsperren.
* **4:** Asset wird produziert.

Hier finden Sie einige allgemeine Empfehlungen zur Verwaltung von Assets während dieses Prozesses:

* Vermeiden Sie das direkte Speichern einer Datei, die Sie in einer von AEM Desktop App zugeordneten Netzwerkfreigabe geöffnet haben, es sei denn, Sie haben nur kleine Änderungen an der Datei vorgenommen.
* Kopieren Sie die Datei in einen separaten WIP-Ordner, wenn Sie weitere Änderungen daran vornehmen möchten, speichern Sie gelegentlich oder arbeiten Sie mit dem Kreativteam zusammen.

#### Massen-Upload in DAM {#bulk-upload-to-dam}

In einigen Szenarien müssen Sie möglicherweise eine größere Anzahl von Dateien gleichzeitig in DAM hochladen. Beispiele dafür sind:

* Hochladen der Ergebnisse von  Fotoschuhe oder größere Projekte
* Hochladen von Assets von Kreativagenturen
* Hochladen von Assets aus einem größeren Satz, wenn die Auswahl außerhalb von DAM erfolgt

Hinweis: Diese Beschreibung bezieht sich auf das betriebsbedingte Hochladen von Dateien (z. B. jede Woche oder bei jedem  Fotoshot usw.), als normaler Teil des Arbeitsablaufs des Desktop-Benutzers. Das Migrieren großer Assets wird hier nicht behandelt.

Für den Massenupload von Assets können Sie die folgenden Funktionen nutzen:

* Um große/hierarchische Ordner hochzuladen, verwenden Sie AEM Desktop-App, die die Funktion [Ordner-Upload](https://helpx.adobe.com/de/experience-manager/desktop-app/aem-desktop-app.html#bulkupload) bietet. Sie können auch hierarchische Ordnerstrukturen hochladen. Das Hochladen von Assets erfolgt im Hintergrund und ist daher nicht an eine Webbrowser-Sitzung gebunden.
* Wenn Sie einige Dateien aus einem einzelnen Ordner hochladen möchten, ziehen Sie diese direkt vom Desktop auf die Web-Benutzeroberfläche oder verwenden Sie die Option „Erstellen“ auf der Web-Benutzeroberfläche von AEM Assets.

>[!NOTE]
>
>Je nach Ihren Geschäftsanforderungen können Sie auch benutzerdefinierte Upload-Programme verwenden.

#### Digitale Assets direkt vom Desktop aus verwalten{#managing-digital-assets-directly-from-desktop}

Wenn Sie digitale Assets in Netzwerk-Dateifreigaben verwalten, kann stattdessen einfach die vom AEM-Desktop-Programm zugeordnete Netzwerkfreigabe verwendet werden. Denken Sie beim Übergang von Netzwerk-Dateifreigaben daran, dass die Web-Benutzeroberfläche von AEM einen umfangreichen Satz von Digital Asset Management-Funktionen bereitstellt, die weit über die Möglichkeiten einer Netzwerkfreigabe hinausgehen (Suche, Sammlungen, Metadaten, Zusammenarbeit, Vorschauen usw.). Die AEM Desktop App bietet einen praktischen Link zur Verbindung des serverseitigen DAM-Repositorys mit der Arbeit auf dem Desktop.

Verwenden Sie das AEM-Desktop-Programm nicht für die direkte Verwaltung von Assets in der Netzwerkfreigabe von AEM Assets. Vermeiden Sie beispielsweise die Nutzung des AEM-Desktop-Programms zum Verschieben/Kopieren mehrerer Dateien. Verwenden Sie stattdessen die Web-Benutzeroberfläche von AEM Assets, um Ordner aus dem Finder/Explorer in die Netzwerkfreigabe zu ziehen, oder verwenden Sie die Funktion „Ordner hochladen“ von AEM Assets.

#### Asset-Migration {#asset-migration}

Informationen zum Planen und Ausführen von Asset-Migrationen von vorhandenen Systemen in ein neues System oder Migrieren großer Mengen von auf Servern gespeicherten Assets finden Sie im [Migrationshandbuch](/help/assets/assets-migration-guide.md). AEM Desktop App und Integrationen aus AEM in Creative Cloud unterstützen keine derartigen Migrationen. Aufgrund der großen Menge an aufzunehmenden Assets und der zusätzlichen Anforderungen rund um Metadatenzuordnungen, Transformationen und Aufnahmen sollten Migrationen mithilfe anderer Tools und Ansätze erfolgen.

>[!MORELIKETHIS]
>
>* [Adobe-Asset-Link](https://helpx.adobe.com/in/enterprise/admin-guide.html/in/enterprise/using/adobe-asset-link.ug.html)
>* [Optimale Vorgehensweise für AEM Desktop App](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/archive/best-practices-for-v1.html)
>* [AEM Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal.html?lang=de)
>* [Integration von AEM und Adobe Stock](aem-assets-adobe-stock.md)

