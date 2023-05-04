---
title: Tipps zum Programmieren
seo-title: Coding Tips
description: Tipps zum Programmieren für AEM
seo-description: Tips for coding for AEM
uuid: 1bb1cc6a-3606-4ef4-a8dd-7c08a7cf5189
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 4adce3b4-f209-4a01-b116-a5e01c4cc123
exl-id: edc06f41-d0ee-45b0-b2f9-a8fa80e6a8d2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 79%

---

# Tipps zum Programmieren{#coding-tips}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Verwenden Sie so weit wie möglich Taglibs oder HTL {#use-taglibs-or-htl-as-much-as-possible}

Das Einschließen von Scriptlets in JSPs erschwert das Debugging von Fehlern im Code. Auch wird es dadurch schwierig, die Geschäftslogik von der Ansichtsebene zu trennen, was gegen das Single-Responsibility-Prinzip und das MVC-Design-Muster verstößt.

### Schreiben von lesbarem Code {#write-readable-code}

Code wird einmal geschrieben, aber viele Male gelesen. Es zahlt sich aus, von Anfang an darauf zu achten, übersichtlichen Code zu schreiben, da wir und andere Entwickler ihn später lesen und nachvollziehen können müssen.

### Auswählen von Namen, die den Zweck beschreiben {#choose-intention-revealing-names}

Idealerweise sollten andere Programmierer kein Modul öffnen müssen, um zu verstehen, was es tut. Ebenso sollten sie sagen können, was eine Methode macht, ohne sie zu lesen. Je besser wir diesen Ansatz verinnerlichen, desto einfacher lesbar wird unser Code und desto schneller können wir unseren Code schreiben und verändern.

Für AEM-Codes gelten die folgenden Konventionen:


* Eine einzige Implementierung einer Schnittstelle wird `<Interface>Impl` genannt, d. h. `ReaderImpl`.
* Mehrere Implementierungen einer Schnittstelle werden `<Variant><Interface>` genannt, d. h. `JcrReader` und `FileSystemReader`.
* Abstrakte Basisklassen werden `Abstract<Interface>` oder `Abstract<Variant><Interface>` genannt.
* Pakete werden `com.adobe.product.module` genannt.  Jedes Maven-Artefakt oder OSGi-Bundle muss ein eigenes Paket aufweisen.
* Java-Implementierungen werden in einem impl-Paket unter ihrer API platziert.


Beachten Sie, dass diese Konventionen nicht unbedingt für Kundenimplementierungen gelten müssen. Es ist jedoch wichtig, Konventionen zu definieren und einzuhalten, damit der Code aufrechterhalten werden kann.

Idealerweise sollten Namen den Zweck beschreiben. Ein guter Hinweis darauf, dass Namen nicht so deutlich sind wie gewünscht, ist das Vorhandensein von Kommentaren, die erklären, wozu die Variable oder die Methode dient:

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Unklar</strong></p> </td> 
   <td><p><strong>Klar</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>int d; //Verstrichene Zeit in Tagen</p> </td> 
   <td><p>int elapsedTimeInDays;</p> </td> 
  </tr> 
  <tr> 
   <td><p>//getaggte Bilder abrufen<br /> public List getItems() {}</p> </td> 
   <td><p>public List getTaggedImages() {}</p> </td> 
  </tr> 
 </tbody> 
</table>

### Wiederholen Sie sich nicht  {#don-t-repeat-yourself}

Dieses Prinzip sieht vor, dass derselbe Codesatz niemals dupliziert werden sollte. Dies gilt auch für Elemente wie Zeichenfolgentexte. Code-Duplikate erhöhen die Fehleranfälligkeit, wenn etwas geändert werden muss, und sollten gesucht und entfernt werden.

### Blanke CSS-Regeln vermeiden {#avoid-naked-css-rules}

CSS-Regeln sollten speziell auf das Zielelement im Kontext Ihrer Anwendung ausgerichtet sein. Eine CSS-Regel, die auf *.content .center* angewendet wird, wäre beispielsweise zu breit angelegt und könnte sich auf viele Inhalte in Ihrem System auswirken, weshalb andere diesen Stil zukünftig überschreiben müssten. Dagegen wäre *.myapp-centertext* eine spezifischere Regel, da sie zentrierten *Text* im Kontext Ihrer Anwendung festlegt.

### Verwendung veralteter APIs vermeiden {#eliminate-usage-of-deprecated-apis}

Wenn eine API veraltet ist, ist es besser, den neuen empfohlenen Ansatz zu suchen anstatt die veraltete API zu verwenden. Diese Vorgehensweise vereinfacht zukünftige Upgrades.

### Lokalisierbaren Code schreiben {#write-localizable-code}

Alle Zeichenfolgen, die nicht von einem Autor bereitgestellt werden, sollten in einem Aufruf des i18n-Wörterbuchs von AEM über *I18n.get()* in JSP/Java und *CQ.I18n.get()* in JavaScript zusammengefasst werden. Diese Implementierung gibt die Zeichenfolge zurück, die an sie übergeben wurde, wenn keine Implementierung gefunden wird. Dies bietet die Flexibilität, die Lokalisierung zu implementieren, nachdem die Funktionen in der primären Sprache implementiert wurden.

### Ressourcenpfade für Sicherheit maskieren {#escape-resource-paths-for-safety}

Während Pfade im JCR keine Leerzeichen enthalten sollten, sollte das Vorhandensein von Leerzeichen nicht dazu führen, dass der Code umbrochen wird. Jackrabbit stellt eine Text-Hilfsklasse mit den Methoden *escape()* und *escapePath()* bereit. Für JSPs stellt die Granite-Benutzeroberfläche die Funktion *granite:encodeURIPath() EL* bereit.

### Zur Absicherung vor Cross-Site-Scripting-Angriffen die XSS-API und/oder HTL nutzen {#use-the-xss-api-and-or-htl-to-protect-against-cross-site-scripting-attacks}

AEM stellt eine XSS-API bereit, mit der Sie Parameter einfach bereinigen und die Absicherung vor Cross-Site-Scripting-Angriffen gewährleisten können. Darüber hinaus sind diese Schutzmechanismen bei HTL direkt in der Vorlagensprache integriert. Ein API-Cheat-Sheet können Sie unter [Entwicklung – Richtlinien und Best Practices](/help/sites-developing/dev-guidelines-bestpractices.md) herunterladen.

### Angemessene Protokollierung implementieren {#implement-appropriate-logging}

Für Java-Code unterstützt AEM slf4j als Standard-API für die Protokollierung von Meldungen. Für eine konsistente Administration sollte die API in Verbindung mit den Konfigurationen genutzt werden, die über die OSGi-Konsole verfügbar sind. Slf4j umfasst fünf verschiedene Protokollierungsebenen. Wir empfehlen, bei der Auswahl der Ebene, auf der eine Meldung protokolliert werden soll, die folgenden Richtlinien anzuwenden:

* ERROR: Wenn etwas im Code nicht funktioniert und die Verarbeitung nicht fortgesetzt werden kann. Dies geschieht häufig in Folge eines unerwarteten Ausnahmefehlers. In der Regel ist es hilfreich, bei solchen Szenarien Stacktraces einzuschließen.
* WARN: Wenn etwas nicht richtig funktioniert hat, aber die Verarbeitung fortgesetzt werden kann. Dies geschieht oft in Folge eines Ausnahmefehlers, mit dem gerechnet wurde, z. B. *PathNotFoundException*.
* INFO: Informationen, die bei der Überwachung eines Systems hilfreich sein dürften. Denken Sie daran, dass dies der Standard ist und die meisten Kunden ihn in ihren Umgebungen beibehalten. Verwenden Sie sie daher nicht übermäßig.
* DEBUG: Informationen der unteren Ebene zur Verarbeitung. Nützlich beim Debugging eines Problems mit Unterstützung.
* TRACE: Die Informationen der niedrigsten Ebene, Dinge wie Einstieg/Ausstieg-Methoden. Dies wird normalerweise nur von Entwicklern verwendet.

Im Falle von JavaScript *console.log* sollten nur während der Entwicklung verwendet werden und alle Protokollanweisungen sollten vor der Veröffentlichung entfernt werden.

### Vermeiden von Frachtschnitt-Programmierung {#avoid-cargo-cult-programming}

Vermeiden Sie es, Code zu kopieren, ohne zu wissen, was er tut. Im Zweifelsfall ist es ratsam, jemanden zu fragen, der über größere Erfahrung mit dem Modul oder der API verfügt, bei dem/der Sie sich nicht sicher sind.
