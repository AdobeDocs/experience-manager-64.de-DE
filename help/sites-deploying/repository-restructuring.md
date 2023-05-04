---
title: Repository-Neustrukturierung in AEM 6.4
seo-title: Repository Restructuring in AEM 6.4
description: Informieren Sie sich über die Grundlagen und die Logik hinter der Repository-Neustrukturierung in AEM 6.4
seo-description: Learn about the basics and reasoning behind the repository restructuring in AEM 6.4
uuid: e9cd3e88-e352-44a8-9b97-69488d3267cb
contentOwner: chaikels
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: fc879b0b-823b-4bdc-aaa6-36f53a33fb22
feature: Upgrading
exl-id: 6ff5a23a-c9b5-49ca-87b2-ba01eaf48a9f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 74%

---

# Repository-Neustrukturierung in AEM 6.4{#repository-restructuring-in-aem}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Einführung {#introduction}

In Versionen vor AEM 6.4 wurde Kunden-Code teilweise in JCR-Bereichen bereitgestellt, die bei Aktualisierungen geändert werden konnten. Aus diesem Grund war es üblich, dass formale AEM-Versionen benutzerdefinierten Code, Konfigurationen oder Inhalte überschrieben haben. Darüber hinaus wurden durch Kundenänderungen manchmal AEM Produktcode oder -inhalt überschrieben, was die Produktfunktionalität beeinträchtigte.

Durch klare Abgrenzungshierarchien für AEM-Produkt-Code und Kunden-Code können diese Konflikte vermieden werden.

Aus diesem Grund wird ab AEM 6.4 und in zukünftigen Versionen der Inhalt aus „/etc“ in andere Ordner im Repository verschoben und es gibt Richtlinien dafür, welcher Inhalt wo gespeichert wird. Dabei kommen die folgenden Regeln zur Anwendung:

* AEM-Produkt-Code wird immer im Ordner „/libs“ abgelegt, der nicht durch benutzerdefinierten Code überschrieben werden darf.
* Benutzerdefinierter Code sollte in „/apps“, „/content“ und „/conf“ gespeichert werden.

## Auswirkungen auf Aktualisierungen auf 6.4 {#impact-on-upgrades}

Beim Aktualisieren auf AEM 6.4 wird eine große Teilmenge des Inhalts unter „/etc“ in andere Ordner im Repository dupliziert. Diese neuen Speicherorte sind die bevorzugten Stellen, an denen der Inhalt referenziert wird. Allerdings ist die Aktualisierung auf AEM 6.4 abwärtskompatibel mit den früheren Speicherorten im Ordner „/etc“, sodass der AEM-Code in den meisten Fällen weiterhin auf die alten Speicherorte verweist, bis Änderungen im Programm eines Kunden aktiv –- und in vielen Fällen manuell – vorgenommen werden. Hinsichtlich des Zeitrahmens gibt es zwei Kategorien von Änderungen:

* Mit der Aktualisierung auf 6.4: Einige der Neustrukturierungsänderungen für „/etc“ sind nicht abwärtskompatibel und entsprechend sollten Änderungen im Rahmen der Aktualisierung auf AEM 6.4 geplant und umgesetzt werden.
* Vor der Aktualisierung auf Version 6.5 - die überwiegende Mehrheit der Änderungen der /etc-Umstrukturierung kann bis zu einem späteren Zeitpunkt nach der Aktualisierung verschoben werden. Wie bereits erwähnt, verweist der AEM 6.4-Code weiterhin auf die alten Speicherorte, bis die Änderungen im Rahmen einer Kundenfreigabe implementiert werden. Es gibt zwar keinen erzwungenen Zeitrahmen, für den die Änderungen vorgenommen werden sollten, es wird jedoch empfohlen, sie vor der Aktualisierung auf 6.5 vorzunehmen, da zukünftige Funktionen darauf angewiesen sein können, auf die neuen Speicherorte verwiesen wird. Auch verweist die Dokumentation für eine bestimmte Funktion standardmäßig auf die neuen Speicherorte, weswegen die Verwendung alter Speicherorte verwirrend sein könnte.

### Leitfaden für die Neustrukturierung {#restructuring-guidance}

Bei der Planung einer Aktualisierung auf AEM 6.4 sollten die folgenden Seiten zur Abschätzung des Arbeitsaufwands herangezogen werden:

* [Repository-Neustrukturierung für alle AEM-Lösungen](/help/sites-deploying/all-repository-restructuring-in-aem-6-4.md)
* [Repository-Neustrukturierung für AEM Sites](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md)
* [Repository-Neustrukturierung für AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/repository-restructuring.html?lang=de)
* [Repository-Neustrukturierung für AEM Assets Dynamic Media](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md)
* [Repository-Neustrukturierung für AEM Forms](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md)
* [Repository-Neustrukturierung für AEM Communities](/help/sites-deploying/communities-repository-restructuring-in-aem-6-4.md)
* [Repository-Neustrukturierung für AEM Commerce](/help/sites-deploying/ecommerce-repository-restructuring-in-aem-6-4.md)

Jede Seite enthält zwei Bereiche entsprechend der Dringlichkeit der erforderlichen Änderungen. Alle Punkte im Abschnitt „Mit der Aktualisierung auf 6.4“ sollten im Rahmen des AEM 6.4-Aktualisierungsprojekts behandelt werden. Alles unter &quot;Vor der Aktualisierung auf 6.5&quot;kann optional bis nach der Aktualisierung verschoben werden.

Jeder Eintrag auf der Seite enthält ein Feld &quot;Anleitung zur Umstrukturierung&quot;, in dem die empfohlene technische Strategie für die Ausrichtung an dem neuen 6.4-Repository-Modell beschrieben wird, sodass die neuen Speicherorte für Inhalte referenziert werden, die sich zuvor im Ordner /etc befinden. Ein zusätzliches Feld „Hinweise“ bietet zusätzlichen nützlichen Kontext.
