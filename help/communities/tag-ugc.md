---
title: Tagging benutzergenerierter Inhalte
seo-title: Tagging benutzergenerierter Inhalte
description: Durch das Tagging benutzergenerierter Inhalte (UGC) können Community-Mitglieder anderen Mitgliedern bei der Suche nach Inhalten helfen.
seo-description: Durch das Tagging benutzergenerierter Inhalte (UGC) können Community-Mitglieder anderen Mitgliedern bei der Suche nach Inhalten helfen.
uuid: ce125d7c-6fc1-44c7-9f67-eca6f599d8e3
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 1cc8ce66-2c03-44e4-9ddd-8d6944d85c99
role: Administrator
exl-id: 834df392-df38-498c-9e2a-489484e20e0a
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 9%

---

# Tagging benutzergenerierter Inhalte {#tagging-user-generated-content}

## Überblick {#overview}

Das Tagging benutzergenerierter Inhalte (UGC) ist das Mittel, mit dem Community-Mitglieder anderen Mitgliedern bei der Suche nach Inhalten helfen können.

In der Regel werden Tags von Autoren und Administratoren in der Autorenumgebung angewendet. Das Tagging von UGC ist insofern einzigartig, als UGC-Tags von Community-Mitgliedern in der Veröffentlichungsumgebung angewendet werden.

Die Tag-Namespaces und Taxonomien sind für beide Anwendungen gleich.

## Communities-Funktionen {#communities-features}

Die AEM Communities-Funktionen, die so konfiguriert werden können, dass Tagging möglich ist, sind

* [Blog](blog-feature.md)
* [Kalender](calendar.md)
* [Dateibibliothek](file-library.md)
* [Forum](forum.md#configuretheaddedforum)
* [Fragen und Antworten](working-with-qna.md)

## Verwalten von Tags {#administering-tags}

Informationen zum Erstellen und Verwalten von Tag-Namespaces und Taxonomien finden Sie unter [Verwalten von Tags](../../help/sites-administering/tags.md#tagging-console) .

Entwicklerinformationen finden Sie unter [Tag Essentials](tag.md) .

Informationen zum Hinzufügen einer Social Tag Cloud-Komponente zur Seite finden Sie unter [Social Tag Cloud verwenden](tagcloud.md) , um die Suche nach veröffentlichten UGC-Inhalten mithilfe der angewendeten Tags zu erleichtern.

### Tag-Berechtigungen {#tag-permissions}

Die Standardberechtigungen sind so eingestellt, dass Tag-Namespaces nicht von allen in der Veröffentlichungsumgebung gelesen werden können.

Da Tags in der Veröffentlichungsumgebung auf UGC angewendet werden, muss die Leseberechtigung für Community-Mitglieder aktiviert sein, damit sie Tags auswählen können, die angewendet werden sollen.

Siehe [Festlegen von Tag-Berechtigungen](../../help/sites-administering/tags.md#setting-tag-permissions).

Im Folgenden sehen Sie, wie es in CRXDE angezeigt wird, wenn ein Administrator Leseberechtigungen für `/etc/tag/discussions` für die Gruppe `*Community Engage Members*` auf  anwendet.

![chlimage_1-74](assets/chlimage_1-74.png)
