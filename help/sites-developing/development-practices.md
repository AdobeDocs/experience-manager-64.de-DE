---
title: Entwicklungspraktiken
seo-title: Development Practices
description: Best Practices für die Entwicklung auf AEM
seo-description: Best practices for developing on AEM
uuid: 27a75f7f-6e2c-4113-9e9f-c5013a4594c2
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 8b0297a1-d922-410f-9aaf-3a6b87e11dc0
exl-id: 32fb6479-ae53-4bb3-8827-db15d7f5705e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 75%

---

# Entwicklungspraktiken{#development-practices}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Arbeiten gemäß einer Definition von &quot;Fertig&quot; {#work-according-to-a-definition-of-done}

Jedes Team hat eine andere Definition, was &quot;getan&quot;bedeutet, aber es ist wichtig, eine zu haben und sicherzustellen, dass eine Geschichte die definierten Kriterien erfüllt, bevor sie akzeptiert wird.

Einige häufig von Teams festgelegte Kriterien sind:

* Für die Formatierung überarbeiteter Code
* Kommentare/Javadoc hinzugefügt
* Erfüllt die erforderlichen Testabdeckung
* Übergibt Unit- und Integrationstests
* In der QS-Umgebung validiert
* Lokalisierung implementiert

Ohne ein klar definiertes DoD ist es einfach, in einer Situation zu landen, in der viele Dinge auf halbem Weg erledigt sind und nichts wirklich vollständig ist.

### Kodierungs- und Formatierungskonventionen definieren und einhalten {#define-and-adhere-to-coding-and-formatting-conventions}

Dinge wie Einzüge und Leerräume erscheinen möglicherweise nicht wichtig, aber korrekt formatierter Code trägt erheblich zur Lesbarkeit und Pflegeleichtigkeit bei. Konventionen sollten im Team abgesprochen und beim Programmieren befolgt werden.

### Auf hohe Testabdeckung abzielen  {#aim-for-high-test-coverage}

Je größer eine Projektimplementierung, desto mehr Zeit ist auch erforderlich, um sie zu testen. Ohne entsprechende Testabdeckung kann das Test-Team nicht skalieren und die Entwicklerinnen und Entwickler kommen irgendwann vor lauter Bugs nicht mehr hinterher.

Entwickler sollten TDD praktizieren und fehlschlagende Einheitstests vor dem Produktions-Code schreiben, der ihre Anforderungen erfüllt. Die Qualitätssicherung sollte einen automatisierten Satz von Abnahmeprüfungen erstellen, um sicherzustellen, dass das System von einer hohen Ebene aus wie erwartet funktioniert.

Es stehen benutzerdefinierte Frameworks wie Jackalope und Prosper zur Verfügung, um die Nachahmung von JCR-APIs zu vereinfachen, um die Produktivität der Entwickler beim Schreiben von Komponententests sicherzustellen.

### Demo bereit halten {#stay-demo-ready}

Das System sollte am Ende jeder Iteration für Demos im Unternehmen zur Verfügung stehen. Indem das System immer bereit für Demos gehalten wird, ist das Team immer nur eine Iteration von Produktionsbereitschaft entfernt und technische Rückstände werden auf ein vertretbares Maß beschränkt.

### Kontinuierliche Integrationsumgebung implementieren und verwenden {#implement-a-continuous-integration-environment-and-use-it}

Das Implementieren einer kontinuierlichen Integrationsumgebung ermöglicht das einfache und wiederholte Durchführen von Einheits- und Integrationstests. Außerdem werden so Bereitstellungen vom Entwicklungs-Team entkoppelt, was andere Teile des Teams effizienter und Bereitstellungen stabiler sowie vorhersehbarer macht.

### Entwicklungszyklus durch niedrige Erstellungszeiten beschleunigen {#keep-the-development-cycle-fast-by-keeping-build-times-low}

Wenn Einheitstests zu viel Zeit beanspruchen, lassen Entwickler sie aus, wodurch sie ihren Wert verlieren. Wenn es viel Zeit in Anspruch nimmt, den Code zu erstellen und bereitzustellen, werden diese Aufgaben seltener durchgeführt. Indem Sie kurze Erstellungszeiten zur Priorität machen, wird sichergestellt, dass die Zeit, die wir in unsere Testabdeckung und CI-Infrastruktur investiert haben, weiterhin der Produktivität des Teams zugutekommt.

### „Sonar“ sowie andere statische Codeanalysewerkzeuge optimieren und ihre Berichte verwerten {#fine-tune-sonar-and-other-static-code-analysis-tools-and-act-on-their-reports}

Code-Analysewerkzeuge haben nur dann einen Wert, wenn ihre Berichte vom Entwickler-Team verwertet werden. Ohne die Optimierung der Analysen, die diese Tools bieten, sind die generierten Empfehlungen nicht relevant und verlieren ihren Wert.

### Der Pfadfinderregel folgen {#follow-the-boy-scout-rule}

Pfadfinder haben eine Regel: „Hinterlass es besser, als du es vorgefunden hast.“ Sofern sich alle Mitglieder des Entwickler-Teams an diese Regel halten und eine Verbesserung vornehmen, wenn sie einen Fehler sehen, wird der Code konstant verbessert.

### Implementierung von YAGNI-Funktionen vermeiden {#avoid-implementing-yagni-features}

YAGNI (für „You Aren’t Gonna Need It“, zu deutsch: „Du wirst es nicht brauchen“)-Funktionen sind Dinge, die implementiert werden, wenn erwartet wird, dass sie in der Zukunft benötigt werden, momentan aber nicht benötigt werden. Idealerweise sollte der einfachste Code implementiert werden, der heute funktioniert, und anhand konstanter Refaktorierung sichergestellt werden, dass sich die Architektur des Systems mit den Anforderungen und der Zeit weiterentwickelt. Dies ermöglicht eine Konzentration auf das Wesentliche und verhindert das Aufblähen des Codes sowie das Einschleichen von Funktionen.
