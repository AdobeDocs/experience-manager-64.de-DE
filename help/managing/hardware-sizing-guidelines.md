---
title: Hardware-Skalierungsrichtlinien
seo-title: Hardware-Skalierungsrichtlinien
description: Diese Skalierungsrichtlinien bieten eine Annäherung an die Hardware-Erfordernisse, die für die Implementierung eines AEM-Projekts erforderlich sind.
seo-description: Diese Skalierungsrichtlinien bieten eine Annäherung an die Hardware-Erfordernisse, die für die Implementierung eines AEM-Projekts erforderlich sind.
uuid: 83f928e3-986b-461b-8b3e-8faacd11172e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/MANAGING
topic-tags: managing
content-type: reference
discoiquuid: 3f4feb38-eca0-4852-88f8-9b20625e18ad
exl-id: 34e4edd5-9e67-44ed-8c4c-bcdd3e161a35
source-git-commit: 8665f708a336134340a3f1abe2aa17622fa142f1
workflow-type: tm+mt
source-wordcount: '2850'
ht-degree: 78%

---

# Hardware-Skalierungsrichtlinien {#hardware-sizing-guidelines}

Diese Skalierungsrichtlinien bieten eine Annäherung an die Hardware-Erfordernisse, die für die Implementierung eines AEM-Projekts erforderlich sind. Die Größenschätzungen hängen von der Architektur des Projekts, der Komplexität der Lösung, dem erwarteten Traffic und den Projektanforderungen ab. Dieser Leitfaden hilft Ihnen, den Hardwarebedarf für eine bestimmte Lösung zu ermitteln oder eine obere und untere Schätzung für die Hardwareanforderungen zu finden.

Zu berücksichtigende Grundfaktoren sind (in dieser Reihenfolge):

* **Netzwerkgeschwindigkeit**

   * Netzwerklatenz
   * Verfügbare Bandbreite

* **Rechengeschwindigkeit**

   * Caching-Effizienz
   * Erwartetes Traffic-Volumen
   * Komplexität von Vorlagen, Anwendungen und Komponenten
   * Gleichzeitige Autoren
   * Komplexität der Erstellungsvorgangs (einfache Inhaltsbearbeitung, MSM-Rollout usw.)

* **E/A-Leistung**

   * Performance und Effizienz der Datei- oder Datenbankspeicherung

* **Festplatte**

   * mindestens zwei- oder dreimal größer als die Größe des Repositorys

* **Arbeitsspeicher**

   * Größe der Website (Anzahl der Inhalts-Objekte, Seiten und Benutzer)
   * Anzahl der gleichzeitig aktiven Benutzer/Sitzungen

## Architektur {#architecture}

Ein typisches AEM-Setup besteht aus einer Autoren- und einer Veröffentlichungsumgebung. Diese Umgebungen haben unterschiedliche Anforderungen bezüglich der zugrunde liegenden Hardwaregröße und der Systemkonfiguration. Detaillierte Überlegungen zu beiden Umgebungen finden Sie in den Abschnitten [Autorenumgebung](/help/managing/hardware-sizing-guidelines.md#author-environment-specific-calculations) und [Veröffentlichungsumgebung](/help/managing/hardware-sizing-guidelines.md#publish-environment-specific-calculations) .

In einem typischen Projekt-Setup stehen Ihnen mehrere Umgebungen zur Verfügung, in denen Sie Projektphasen inszenieren können:

* **Entwicklungsumgebung** Um neue Funktionen zu entwickeln oder wesentliche Änderungen vorzunehmen. Am besten arbeitet man mit einer Entwicklungsumgebung pro Entwickler (in der Regel lokale Installationen auf dem individuellen System).

* **Autorentest-**
UmgebungÜberprüfen von Änderungen. Die Anzahl der Testumgebungen kann je nach Projektanforderungen variieren (z. B. getrennt für QA, Integrationstests oder Benutzerakzeptanztests).

* **Veröffentlichungs-Testumgebung** Hauptsächlich zum Testen von Anwendungsfällen der Zusammenarbeit in sozialen Netzwerken und/oder der Interaktion zwischen Autor und mehreren Veröffentlichungsinstanzen.

* **Autoren-Bearbeitungsumgebung** Für Autoren zum Bearbeiten von Inhalten

* **Veröffentlichungs-Bearbeitungsumgebung** Um veröffentlichte Inhalte bereitzustellen.

Die Umgebungen variieren zudem, von einem Single-Server-System mit AEM und einem Anwendungsserver bis hin zu einem hochskalierten Satz von Multi-Server- und Multi-CPU-Clustern. Es wird empfohlen, je einen separaten Computer für ein Produktionssystem zu verwenden und keine anderen Anwendungen auf diesen Rechnern auszuführen.

## Hinweise zur Skalierung generischer Hardware {#generic-hardware-sizing-considerations}

Die folgenden Abschnitte enthalten Hinweise zur Berechnung der Hardwareanforderungen unter Berücksichtigung verschiedener Überlegungen. Für große Systeme empfehlen wir Ihnen, einen einfachen Satz von internen Benchmarktests an einer Referenzkonfiguration durchzuführen.

Performance-Optimierung ist eine grundlegende Aufgabe, die durchgeführt werden muss, bevor ein Benchmarking für ein bestimmtes Projekt durchgeführt werden kann. Beachten Sie die Hinweise in der [Dokumentation zur Performance-Optimierung](/help/sites-deploying/configuring-performance.md), bevor Sie Benchmarktests durchführen und deren Ergebnisse für Hardware-Auslegungsberechnungen umsetzen.

Hardware-Skalierung für fortgeschrittene Anwendungsfälle sollte auf einer detaillierten Leistungsbewertung des Projekts basieren. Zu den Merkmalen fortgeschrittener Anwendungsfälle, die außergewöhnliche Hardware-Ressourcen erfordern, gehören Kombinationen von:

* hohe Nutzlast/Durchsatzleistung
* umfangreicher Einsatz von kundenspezifischem Code, eigenen Workflows oder Softwarebibliotheken von Drittanbietern
* Integration mit nicht unterstützten externen Systemen

### Festplattenspeicher/Festplatte {#disk-space-hard-drive}

Der benötigte Speicherplatz hängt stark vom Volumen und vom Typ Ihrer Web-Anwendung ab. Die Berechnungen sollten berücksichtigen:

* die Anzahl und Größe von Seiten, Assets und anderen im Repository gespeicherten Inhalten wie Workflows, Profilen usw.
* die geschätzte Häufigkeit von Inhalts-Änderungen und damit die Erstellung von Inhalts-Versionen
* das Volumen der DAM-Ausgaben, die generiert werden sollen
* das Wachstum aller Inhalte im Laufe der Zeit

Der Speicherplatz wird während der Online- und Offline-Revisionsbereinigung kontinuierlich überwacht. Falls der verfügbare Speicherplatz unter einen kritischen Wert sinkt, wird der Vorgang abgebrochen. Der kritische Wert beträgt 25 % der aktuellen Festplattengröße auf dem Repository und kann nicht konfiguriert werden. Es wird empfohlen, eine Festplatte zu verwenden, die mindestens zwei- bis dreimal größer als das Repository ist, einschließlich erwartetem Wachstum.

Für die Datenredundanz sind redundante Arrays unabhängiger Festplatten (RAID, z. B. RAID10) eine gute Wahl.

>[!NOTE]
>
>Das temporäre Verzeichnis einer Produktionsinstanz sollte mindestens 6 GB freien Speicherplatz vorhalten.

### Virtualisierung {#virtualization}

AEM läuft gut in virtualisierten Umgebungen, aber es kann Faktoren wie CPU oder E/A geben, die nicht direkt mit physischer Hardware gleichgesetzt werden können. Allgemein empfehlenswert ist die Wahl einer höheren E/A-Geschwindigkeit, da dies in den meisten Fällen ein kritischer Faktor ist. Vergleichswerte für Ihre Umgebung sind erforderlich, um ein genaues Verständnis dafür zu erhalten, welche Ressourcen erforderlich sind.

### Parallelisierung von AEM-Instanzen {#parallelization-of-aem-instances}

#### Ausfallsicherheit {#fail-safeness}

Eine ausfallsichere Website wird auf mindestens zwei getrennten Systemen eingesetzt. Fällt ein System aus, kann ein anderes System übernehmen und so den Systemausfall kompensieren.

#### Skalierbarkeit der Systemressourcen {#system-resources-scalability}

Während alle Systeme laufen, steht eine erhöhte Rechenleistung zur Verfügung. Diese zusätzliche Leistung ist nicht unbedingt linear mit der Anzahl der Clusterknoten, da die Beziehung in hohem Maße von der technischen Umgebung abhängig ist. Weitere Informationen finden Sie in der [Cluster-Dokumentation](/help/sites-deploying/recommended-deploys.md) .

Die Abschätzung, wie viele Cluster-Knoten notwendig sind, basiert auf den grundlegenden Anforderungen und spezifischen Anwendungsfällen des jeweiligen Webprojektes:

* Aus Sicht der Ausfallsicherheit ist es notwendig, für alle Umgebungen zu bestimmen, wie kritisch ein Ausfall ist und wie lange es dauert, bis ein Clusterknoten wiederhergestellt ist.
* Für den Aspekt der Skalierbarkeit ist die Anzahl der Schreiboperationen grundsätzlich der wichtigste Faktor; siehe [Paralleles Arbeiten von Autoren](/help/managing/hardware-sizing-guidelines.md#authors-working-in-parallel) für die Autorenumgebung, und [Zusammenarbeit in sozialen Netzwerken](/help/managing/hardware-sizing-guidelines.md#aem-communities-sizing-considerations) für die Veröffentlichungsumgebung. Der Lastausgleich kann für Operationen eingerichtet werden, die nur auf das System zugreifen, um Lesevorgänge zu verarbeiten; siehe [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/user-guide.html) für Details.

## Spezielle Berechnungen für die Autorenumgebung {#author-environment-specific-calculations}

Für Benchmarkingzwecke hat Adobe einige Benchmarktests für eigenständige Autoreninstanzen entwickelt.

* **Benchmarktest 1**

   Berechnen Sie den maximalen Durchsatz eines Lastprofils, bei dem Benutzer zusätzlich zu einer Grundlast von 300 vorhandenen Seiten eine einfache Seitenübung zum Erstellen durchführen, die alle ähnlicher Art ist. Die Schritte bestanden darin, sich bei der Website anzumelden, eine Seite mit einer SWF und Bild/Text zu erstellen, eine Tag-Cloud hinzuzufügen und die Seite zu aktivieren.

   * **Ergebnis**

      Der maximale Durchsatz für eine einfache Seitenerstellung wie oben (als eine Transaktion betrachtet) betrug 1730 Transaktionen/Stunde.

* **Benchmarktest 2**

   Berechnen Sie den maximalen Durchsatz, wenn das Lastprofil eine Mischung aus neuer Seitenerstellung (10 %), Änderung einer vorhandenen Seite (80 %) und anschließender Änderung einer Seite in Folge (10 %) aufweist. Die Komplexität der Seiten bleibt gleich wie im Profil des Benchmarktests 1. Die grundlegende Änderung der Seite erfolgt durch Hinzufügen eines Bildes und Ändern des Textinhalts. Die Übung wurde wiederum auf einer Grundlast von 300 Seiten mit der gleichen Komplexität wie in Benchmarktest 1 durchgeführt.

   * **Ergebnis**

      Der maximale Durchsatz für ein solches Mischbetriebsszenario betrug 3252 Transaktionen pro Stunde.

>[!NOTE]
>
>Die Durchsatzrate unterscheidet nicht zwischen Bewegungsarten innerhalb eines Lastprofils. Der Ansatz zur Messung des Durchsatzes stellt sicher, dass ein fester Anteil jeder Art von Transaktion in die Arbeitslast einbezogen wird.

Die beiden oben genannten Tests zeigen deutlich, dass der Durchsatz je nach Betriebsart variiert. Verwenden Sie die Aktivitäten in Ihrer Umgebung als Grundlage für die Dimensionierung Ihres Systems. Sie erhalten einen besseren Durchsatz mit weniger intensiven Aktionen wie z. B. Modifizieren (was auch häufiger vorkommt).

### Caching {#caching}

In der Autorenumgebung ist die Effizienz der Zwischenspeicherung in der Regel deutlich geringer, da Änderungen an der Website häufiger auftreten und auch die Inhalte sehr interaktiv und personalisiert sind. Mit dem Dispatcher können Sie AEM-Bibliotheken, JavaScripts, CSS-Dateien und Layoutbilder zwischenspeichern. Dies beschleunigt manche Aspekte des Bearbeitungsprozesses. Die Konfiguration des Webservers, um zusätzliche Header für das Browser-Caching auf diesen Ressourcen zu setzen, reduziert die Anzahl der HTTP-Anfragen und verbessert somit die Reaktionsfähigkeit des Systems, wie sie von den Autoren erfahren wird.

### Paralleles Arbeiten von Autoren {#authors-working-in-parallel}

In der Autorenumgebung sind die Anzahl der parallel arbeitenden Autoren und die Belastung des Systems durch ihre Interaktionen die wichtigsten limitierenden Faktoren. Wir empfehlen Ihnen daher, Ihr System auf Basis des gemeinsamen Datendurchsatzes zu skalieren.

Für solche Szenarien führte Adobe Benchmarktests auf einem Shared-Nothing-Cluster von Autoreninstanzen mit zwei Knoten durch.

* **Benchmarktest 1a**

   Mit einem aktiv-aktiven &quot;shared-nichts&quot;-Cluster von 2 Autoreninstanzen berechnen Sie den maximalen Durchsatz mit einem Lastprofil, bei dem Benutzer zusätzlich zu einer Grundlast von 300 vorhandenen Seiten eine einfache Seitenübung zum Erstellen durchführen - alles ähnlich.

   * **Ergebnis**

      Der maximale Durchsatz für eine einfache Seitenerstellungs-Übung (wie oben gezeigt (als eine Transaktion betrachtet) beträgt 2016 Transaktionen/Stunde. Dies ist eine Steigerung von ca. 16 % im Vergleich zu einer eigenständigen Autoreninstanz für den gleichen Benchmarktest.

* **Benchmarktest 2b**

   Mit einem aktiv-aktiven Shared-Nothing-Cluster von 2 Autoreninstanzen berechnen Sie den maximalen Durchsatz, wenn das Lastprofil eine Mischung aus neuer Seitenerstellung (10 %), Änderung vorhandener Seiten (80 %) und Erstellung und Änderung einer Seite nacheinander (10 %) aufweist. Die Komplexität der Seite bleibt gleich wie im Profil des Benchmarktests 1. Die grundlegende Änderung der Seite erfolgt durch Hinzufügen eines Bildes und Ändern des Textinhalts. Auch hier wurde die Übung auf einer Grundlast von 300 Seiten mit derselben Komplexität wie im Benchmarktest 1 durchgeführt.

   * **Ergebnis**

      Der maximale Durchsatz für ein solches Mischbetriebsszenario betrug 6288 Transaktionen/Stunde. Dies ist eine Steigerung von ca. 93 % im Vergleich zu einer eigenständigen Autoreninstanz für denselben Benchmarktest.

>[!NOTE]
>
>Die Durchsatzrate unterscheidet nicht zwischen Bewegungsarten innerhalb eines Lastprofils. Der Ansatz zur Messung des Durchsatzes stellt sicher, dass ein fester Anteil jeder Art von Transaktion in die Arbeitslast einbezogen wird.

Die beiden oben genannten Tests zeigen deutlich, dass AEM für Autoren, die grundlegende Bearbeitungen mit AEM durchführen, gut skalierbar ist. Im Allgemeinen ist AEM am effektivsten bei der Skalierung von Leseoperationen.


Auf einer typischen Website geschieht das meiste Authoring während der Projektphase. Nach dem Start der Website sinkt die Anzahl der parallel arbeitenden Autoren in der Regel auf einen niedrigeren (Regelbetriebs-)Durchschnitt.

Sie können die Anzahl der Computer (oder CPUs), die für die Autorenumgebung erforderlich sind, wie folgt berechnen:

`n = numberOfParallelAuthors / 30`

Diese Formel kann als allgemeine Richtlinie für die Skalierung von CPUs dienen, wenn Autoren grundlegende Operationen mit AEM durchführen. Es wird davon ausgegangen, dass das System und die Anwendung optimiert sind. Die Formel gilt jedoch nicht für erweiterte Funktionen wie MSM oder Assets (siehe unten).

Weitere Informationen finden Sie in den zusätzlichen Kommentaren zu [Parallelisierung](/help/managing/hardware-sizing-guidelines.md#parallelization-of-aem-instances) und [Leistungsoptimierung](/help/sites-deploying/configuring-performance.md).

### Hardware-Empfehlungen {#hardware-recommendations}

Normalerweise können Sie für Ihre Autorenumgebung die gleiche Hardware verwenden, die für Ihre Veröffentlichungsumgebung empfohlen wird. Normalerweise ist der Website-Traffic auf Autorensystemen viel geringer, aber auch die Cache-Effizienz ist geringer. Entscheidend ist jedoch die Anzahl der parallel arbeitenden Autoren und die Art der Aktionen, die am System vorgenommen werden. Im Allgemeinen ist AEM-Clustering (der Autorenumgebung) am effektivsten bei der Skalierung von Leseoperationen; mit anderen Worten, ein AEM-Cluster skaliert gut mit Autoren, die grundlegende Bearbeitungsoperationen durchführen.

Die Benchmarktests an Adobe wurden mit dem Betriebssystem RedHat 5.5 durchgeführt, das auf einer Hewlett-Packard ProLiant DL380 G5-Hardwareplattform mit folgender Konfiguration ausgeführt wird:

* Zwei Quad-Core Intel Xeon X5450 CPUs mit 3,00 GHz
* 8 GB RAM
* Broadcom NetXtreme II BCM5708 Gigabit Ethernet
* HP Smart Array RAID-Controller, 256 MB Cache
* Zwei 146 GB 10.000 RPM SAS-Festplatten, die als RAID0-Streifenset konfiguriert sind
* SPEC CINT2006 Raten-Benchmark-Score ist 110

AEM-Instanzen liefen mit einer minimalen Heap-Größe von 256M und einer maximalen Heap-Größe von 1024M.

## Veröffentlichung von umgebungsspezifischen Berechnungen {#publish-environment-specific-calculations}

### Effizienz der Zwischenspeicherung und Traffic {#caching-efficiency-and-traffic}

Die Effizienz der Zwischenspeicherung ist entscheidend für die Geschwindigkeit der Website. Die folgende Tabelle zeigt, wie viele Seiten pro Sekunde ein optimiertes AEM-System mit einem Reverse-Proxy wie dem Dispatcher verarbeiten kann:

| Cache-Verhältnis | Seiten/s (Spitzenwert) | Millionen Seiten/Tag (Durchschnitt) |
|---|---|---|
| 100% | 1000-2000 | 35-70 |
| 99% | 910 | 32 |
| 95% | 690 | 25 |
| 90 % | 520 | 18 |
| 60% | 220 | 8 |
| 0% | 100 | 3.5 |

>[!CAUTION]
>
>Anmerkung: Die Zahlen basieren auf einer Standard-Hardwarekonfiguration und können je nach verwendeter Hardware variieren.

Die Zwischenspeicher-Quote gibt den Prozentsatz an Seiten an, die der Dispatcher zurückgeben kann, ohne auf AEM zuzugreifen. 100 % bedeutet, dass der Dispatcher alle Anfragen beantwortet, 0 % bedeutet, dass AEM jede einzelne Seite berechnet.

### Komplexität von Vorlagen und Anwendungen {#complexity-of-templates-and-applications}

Wenn Sie komplexe Vorlagen verwenden, benötigt AEM mehr Zeit, um eine Seite zu rendern. Seiten aus dem Zwischenspeicher sind davon nicht betroffen, aber die Seitengröße ist für die gesamte Antwortzeit relevant. Das Rendern einer komplexen Seite kann leicht zehnmal länger dauern als das Rendern einer einfachen Seite.

### Formel {#formula}

Mithilfe der folgenden Formel können Sie eine Schätzung der Gesamtkomplexität Ihrer AEM berechnen:

`complexity = applicationComplexity + ((1-cacheRatio) * templateComplexity)`

Basierend auf der Komplexität können Sie die Anzahl der Server (oder CPU-Kerne), die Sie für die Veröffentlichungsumgebung benötigen, wie folgt bestimmen:

`n = (traffic * complexity / 1000 ) * activations`

Die Variablen in der Gleichung lauten wie folgt:

<table>
 <tbody>
  <tr>
   <td>traffic</td>
   <td>Der erwartete Spitzentraffic pro Sekunde. Man kann dies als die Anzahl der Seitenaufrufe pro Tag, geteilt durch 35.000, schätzen.</td>
  </tr>
  <tr>
   <td>applicationComplexity</td>
   <td><p>Verwenden Sie 1 für eine einfache Anwendung, 2 für eine komplexe Anwendung oder einen Wert dazwischen:</p>
    <ul>
     <li>1 - eine vollständig anonyme, inhaltsorientierte Site</li>
     <li>1.1 - eine vollständig anonyme, inhaltsorientierte Site mit Client-seitiger/Target-Personalisierung</li>
     <li>1.5 - eine inhaltsorientierte Site mit sowohl anonymen als auch angemeldeten Abschnitten, Client-seitig/Target-Personalisierung</li>
     <li>1.7 - für eine inhaltsorientierte Site mit sowohl anonymen als auch angemeldeten Abschnitten, Client-seitige/Target-Personalisierung und einigen benutzergenerierten Inhalten</li>
     <li>2 - wo sich die gesamte Site anmelden muss, mit umfangreichem Einsatz benutzergenerierter Inhalte und einer Vielzahl von Personalisierungstechniken</li>
    </ul> </td>
  </tr>
  <tr>
   <td>cacheRatio</td>
   <td>Der Prozentsatz der Seiten, die aus dem Dispatcher-Cache stammen. Verwenden Sie 1, wenn alle Seiten aus dem Cache kommen, oder 0, wenn jede Seite von AEM berechnet wird.</td>
  </tr>
  <tr>
   <td>templateComplexity</td>
   <td>Verwenden Sie einen Wert zwischen 1 und 10, um die Komplexität Ihrer Vorlagen anzugeben. Höhere Zahlen zeigen komplexere Vorlagen an, wobei der Wert 1 für Sites mit durchschnittlich 10 Komponenten pro Seite, der Wert 5 für einen Seitendurchschnitt von 40 Komponenten und 10 für einen Durchschnitt von über 100 Komponenten verwendet wird.</td>
  </tr>
  <tr>
   <td>Aktivierungen</td>
   <td>Anzahl der durchschnittlichen Aktivierungen (Replikation von durchschnittlich großen Seiten und Assets vom Autor zur Veröffentlichungsstufe) pro Stunde dividiert durch x, wobei x die Anzahl der Aktivierungen ist, die auf einem System durchgeführt werden, ohne dass sich dies auf die Leistung auswirkt, die auf andere vom System verarbeitete Aufgaben entfällt. Sie können einen pessimistischen Anfangswert wie x = 100 vordefinieren.<br /> </td>
  </tr>
 </tbody>
</table>

Wenn Sie eine komplexere Website haben, benötigen Sie auch leistungsfähigere Webserver, damit AEM eine Anfrage in akzeptabler Zeit beantworten kann.

* Komplexität unter 4:
   * 1024 MB JVM RAM&amp;ast;
   * Geringe bis mittlere CPU-Leistung

* Komplexität zwischen 4 und 8:
   * 2048 MB JVM RAM&amp;ast;
   * Mid to high-performance CPU

* Komplexität über 8:
   * 4096 MB JVM RAM&amp;ast;
   * CPU mit hoher bis hoher Leistung

>[!NOTE]
>
>&amp;ast; Reservieren Sie zusätzlich zum für Ihre JVM benötigten Speicher genügend RAM für Ihr Betriebssystem.

## Zusätzliche anwendungsspezifische Berechnungen {#additional-use-case-specific-calculations}

Neben der Berechnung für eine Standard-Webanwendung müssen Sie ggf. spezifische Faktoren für die folgenden Anwendungsfälle berücksichtigen. Die berechneten Werte sind der Standardberechnung hinzuzufügen.

### Asset-spezifische Hinweise {#assets-specific-considerations}

Zur umfangreichen Verarbeitung digitaler Assets sind optimierte Hardwareressourcen erforderlich; die wichtigsten Faktoren hierbei sind die Bildgröße und der Spitzendurchsatz verarbeiteter Bilder.

Weisen Sie mindestens 16 GB Heap zu und konfigurieren Sie den Workflow „DAM-Update-Asset“ so, dass Rohbilder mit dem [Camera Raw-Paket](/help/assets/camera-raw.md) aufgenommen werden.

>[!NOTE]
>
>Ein höherer Datendurchsatz bedeutet, dass die Rechnerressourcen mit den System-E/As Schritt halten müssen und umgekehrt. Wenn beispielsweise Workflows durch den Import von Bildern gestartet werden, kann das Hochladen vieler Bilder über WebDAV zu einem Rückstau von Workflows führen.
>
>Die Verwendung von separaten Festplatten für TarPM, Datenspeicher und Suchindex kann helfen, das E/A-Verhalten des Systems zu optimieren (in der Regel ist es jedoch sinnvoll, den Suchindex lokal zu halten).

>[!NOTE]
>
>Siehe auch [Richtlinien zur Asset-Leistung](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/configuring/assets-performance-sizing.html).

### Multi-Site-Manager {#multi-site-manager}

Der Ressourcenverbrauch beim Einsatz von MSM in AEM in einer Autorenumgebung hängt stark von den spezifischen Anwendungsfällen ab. Grundlegende Faktoren sind:

* Anzahl der Live Copies
* Häufigkeit des Rollouts
* Größe des Inhaltsbaums, der bereitgestellt werden soll
* Verbundene Funktionalität der Rollout-Aktionen

Das Testen des geplanten Anwendungsfalles mit einem repräsentativen Inhaltsauszug kann Ihnen helfen, den Ressourcenverbrauch besser zu verstehen. Wenn Sie die Ergebnisse mit dem geplanten Durchsatz hochrechnen, können Sie den zusätzlichen Ressourcenbedarf für das MSM in AEM einschätzen.

Bitte beachten Sie auch, dass parallel arbeitende Autoren Performance-Nebenwirkungen wahrnehmen, wenn MSM-Anwendungsfälle für AEM mehr Ressourcen verbrauchen, als geplant.

### Überlegungen zur Dimensionierung von AEM Communities {#aem-communities-sizing-considerations}

AEM Sites, die Funktionen von AEM Communities (Community-Sites) enthalten, erleben ein hohes Maß an Interaktion von Seitenbesuchern (Mitgliedern) in der Veröffentlichungsumgebung.

Die Größenüberlegungen für eine Community-Site hängen von der zu erwartenden Interaktion der Community-Mitglieder ab und davon, ob eine optimale Leistung für den Seiteninhalt von höherer Bedeutung ist.

Benutzergenerierte Inhalte (UGC = User generated content) werden getrennt vom Seiteninhalt gespeichert. Während die AEM-Plattform einen Knotenspeicher verwendet, der Website-Inhalte von der Autoren- in die Veröffentlichungsumgebung repliziert, verwendet AEM Communities einen einzigen, gemeinsamen Speicher für UGC, der nie repliziert wird.

Für den UGC-Speicher ist es notwendig, einen Speicherressourcenanbieter (SRP = Storage Resource Provider) zu wählen, der die gewählte Bereitstellung beeinflusst.\
Siehe

* [Speicherung von Community-Inhalten](/help/communities/working-with-srp.md)
* [Empfohlene Topologien für Communities](/help/communities/topologies.md)
