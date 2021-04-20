---
title: Repository-Neustrukturierung in AEM 6.4
seo-title: Repository-Neustrukturierung in AEM 6.4
description: Informieren Sie sich über die Grundlagen und die Logik hinter der Repository-Neustrukturierung in AEM 6.4
seo-description: Informieren Sie sich über die Grundlagen und die Logik hinter der Repository-Neustrukturierung in AEM 6.4
uuid: e9cd3e88-e352-44a8-9b97-69488d3267cb
contentOwner: chaikels
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: fc879b0b-823b-4bdc-aaa6-36f53a33fb22
feature: Upgrading
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 78%

---


# Repository-Neustrukturierung in AEM 6.4{#repository-restructuring-in-aem}

## Einführung {#introduction}

Vor AEM 6.4 wurde Kundencode in unvorhersehbaren Bereichen der JCR bereitgestellt, die bei Aktualisierungen geändert werden mussten. Aus diesem Grund wurde in formellen AEM Versionen häufig der benutzerdefinierte Code, die Konfiguration oder der Inhalt überschrieben. Darüber hinaus kam es vor, dass durch Kunden vorgenommene Änderungen den AEM-Produktcode oder AEM-Inhalte überschrieben und dadurch die Produktfunktionen beeinträchtigten.

Durch klare Abgrenzungshierarchien für AEM-Produktcode und Kundencode können diese Konflikte vermieden werden.

Zu diesem Zweck werden ab AEM 6.4 und um in zukünftigen Versionen fortgeführt zu werden, Inhalte aus /etc in andere Ordner im Repository umstrukturiert, zusammen mit Richtlinien darüber, welche Inhalte wohin geleitet werden, wobei die folgenden Regeln auf hoher Ebene beachtet werden:

* AEM-Produktcode wird immer im Ordner /libs abgelegt, der nicht durch benutzerdefinierten Code überschrieben werden darf.
* Benutzerdefinierter Code sollte in /apps, /content und /conf platziert werden

## Auswirkungen auf Aktualisierungen auf 6.4 {#impact-on-upgrades}

Beim Aktualisieren auf AEM 6.4 wird eine große Teilmenge des Inhalts unter /etc in andere Ordner im Repository dupliziert. Diese neuen Speicherorte sind die bevorzugten Stellen, an denen der Inhalt referenziert wird. Allerdings ist die Aktualisierung auf AEM 6.4 abwärtskompatibel mit den früheren Speicherorten im /etc-Ordner, sodass der AEM-Code in den meisten Fällen weiterhin auf die alten Speicherorte verweist, bis Änderungen in der Applikation eines Kunden aktiv - und in vielen Fällen manuell - vorgenommen werden. Hinsichtlich der Timeline gibt es zwei Kategorien von Änderungen:

* Mit der Aktualisierung auf 6.4: Einige der Neustrukturierungsänderungen für /etc sind nicht abwärtskompatibel und entsprechend sollten Änderungen im Rahmen der Aktualisierung auf AEM 6.4 geplant und umgesetzt werden.
* Vor der Aktualisierung auf 6.5: Die überwiegende Mehrheit der Neustrukturierungsänderungen für /etc kann auf einen späteren Zeitpunkt nach der Aktualisierung verschoben werden. Wie bereits erwähnt, verweist der AEM 6.4-Code weiterhin auf die alten Speicherorte, bis die Änderungen im Rahmen eines Kundenrelease implementiert werden. Es gibt zwar keinen erforderlichen Zeitrahmen für die Änderungen, es wird jedoch empfohlen, sie vor der Aktualisierung auf 6.5 durchzuführen, da zukünftige Funktionen davon abhängen können, dass die neuen Speicherorte referenziert werden. Auch veweist die Dokumentation für ein bestimmtes Merkmal standardmäßig auf die neuen Speicherorte, weswegen die Verwendung alter Speicherorte verwirrend sein könnte.

### Umstrukturierungsleitlinien {#restructuring-guidance}

Bei der Planung einer Aktualisierung auf AEM 6.4 sollten die folgenden Seiten zur Abschätzung des Arbeitsaufwands herangezogen werden:

* [Repository-Neustrukturierung für alle AEM-Lösungen](/help/sites-deploying/all-repository-restructuring-in-aem-6-4.md)
* [Repository-Neustrukturierung für AEM Sites](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md)
* [AEM Assets-Repository-Umstrukturierung](/help/sites-deploying/assets-repository-restructuring-in-aem-6-4.md)
* [Repository-Neustrukturierung für AEM Assets Dynamic Media](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md)
* [AEM Forms-Repository-Umstrukturierung](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md)
* [AEM Communities-Repository-Umstrukturierung](/help/sites-deploying/communities-repository-restructuring-in-aem-6-4.md)
* [Repository-Neustrukturierung für AEM Commerce](/help/sites-deploying/ecommerce-repository-restructuring-in-aem-6-4.md)

Jede Seite enthält zwei Bereiche entsprechend der Dringlichkeit der erforderlichen Änderungen. Alle Punkte im Abschnitt „Mit der Aktualisierung auf 6.4“ sollten im Rahmen des AEM 6.4-Aktualisierungsprojekts behandelt werden. Alles, was unter „Vor der Aktualisierung auf 6.5“ steht, kann optional auf nach der Aktualisierung verschoben werden.

Jeder Eintrag auf der Seite enthält ein Feld „Leitfaden für die Neustrukturierung“, in dem die empfohlene technische Strategie für die Anpassung an die neue 6.4 beschrieben ist.  respository-Modell, sodass auf die neuen Speicherorte für Inhalte verwiesen wird, die sich zuvor im Ordner &quot;/etc&quot;befanden. Ein zusätzliches Feld „Hinweise“ bietet zusätzlichen nützlichen Kontext.
