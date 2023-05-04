---
title: Bereitstellung von großen Mengen geschützter Informationen
seo-title: High-volume secure information delivery
description: Document Security unterstützt die Zuordnung von Lizenzen zu Benutzern und nicht zu Dokumenten in Massenproduktionsumgebungen.
seo-description: Document security supports the association of licenses to users, rather than to the documents in mass production environments.
uuid: 9747d283-506c-434e-9850-e50b95290cc8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: b76d7d93-23a5-4c08-81f5-a56267b1556a
feature: Document Security
exl-id: 78fc7c4a-a634-4628-927a-c9622bdc13fc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 8%

---

# Bereitstellung von großen Mengen geschützter Informationen {#high-volume-secure-information-delivery}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

In einer Massenproduktionsumgebung, z. B. bei der Erstellung gesicherter monatlicher Rechnungen für ein Telekommunikationsunternehmen, kann die Erstellung von Lizenzen, die für jedes Dokument spezifisch sind, zu einem ressourcenintensiven Prozess werden. In solchen Fällen unterstützt Document Security die Zuordnung von Lizenzen zu Benutzern und nicht zu Dokumenten. Die für einen Benutzer generierte Lizenz wird für alle Dokumente verwendet, die für diesen Benutzer geschützt sind.

Ein Vorteil dieses Ansatzes besteht darin, dass die Größe der Document Security-Datenbank nicht linear mit den Dokumenten wächst, sondern mit der Anzahl der Benutzer. Da Sie die Lizenz nur einmal für einen Benutzer erstellen müssen, wird der anschließende Schutz von Dokumenten durch diese Richtlinien schneller. Funktionen wie Offline-Zugriff, Ablauf von Dokumenten und Sperrung werden für alle diese Dokumente unterstützt.

Document Security unterstützt auch abstrakte Richtlinien. Abstrakte Richtlinien sind Richtlinienvorlagen, die alle Richtlinienattribute wie Document Security-Einstellungen und Verwendungsrechte enthalten, jedoch keine Liste von Prinzipalen enthalten. Administratoren können eine beliebige Anzahl von Richtlinien aus der abstrakten Richtlinie mit verschiedenen Prinzipalen erstellen, die Zugriff auf die Dokumente haben sollten. Änderungen an der abstrakten Richtlinie wirken sich nicht auf die tatsächlichen Richtlinien aus, die aus den abstrakten Richtlinien generiert werden.

Bei der monatlichen Rechnungserstellung für ein Telekommunikationsunternehmen erstellen Sie eine abstrakte Richtlinie, erstellen Benutzer und generieren dann eindeutige Lizenzen für jeden Benutzer. Die Lizenzen werden später für jeden Benutzer auf Dokumente angewendet.

Die Erstellung einer abstrakten Richtlinie wird nur über das Document Security Java SDK unterstützt. Sie können jedoch die Richtlinien, die Sie aus der abstrakten Richtlinie erstellen, auf den Document Security-Webseiten verwalten. Richtlinien, die mit dieser Methode erstellt werden, sind im Verhalten mit denen identisch, die von Document Security-Webseiten erstellt wurden.

Weitere Informationen finden Sie unter [Programmieren mit AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63_de).
