---
title: E-Commerce-Repository-Neustrukturierung in AEM 6.4
seo-title: E-Commerce Repository Restructuring in AEM 6.4
description: Erfahren Sie, wie Sie die notwendigen Änderungen vornehmen können, um in AEM 6.4 für E-Commerce zur neuen Repository-Struktur zu migrieren.
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.4 for E-Commerce.
uuid: 1fff1a4b-c8d0-4016-92fb-e2ea26e3a302
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 28c92e7d-2106-4333-afa6-c5528a00d7b4
feature: Upgrading
exl-id: 6adcc1a4-eb0f-4410-8219-dbd7e6bbe469
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 42%

---

# E-Commerce-Repository-Neustrukturierung in AEM 6.4{#e-commerce-repository-restructuring-in-aem}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Wie auf der übergeordneten Seite [Repository-Neustrukturierung in AEM 6.4](/help/sites-deploying/repository-restructuring.md) beschrieben, sollten Kunden, die auf AEM 6.4 aktualisieren, diese Seite verwenden, um den Arbeitsaufwand im Zusammenhang mit Repository-Neustrukturierungen einzuschätzen, die sich auf die AEM E-Commerce-Lösung auswirken. Einige Änderungen erfordern während des Aktualisierungsprozesses von AEM 6.4 Arbeitsaufwand, während andere bis zu einem Upgrade auf 6.5 verschoben werden können.

## Mit der Aktualisierung auf 6.4 {#with-upgrade}

### Produkt-, Auftrags-, Sammlungs-, Klassifizierungs-, Versand- und Zahlungsartendaten {#product-order-collections-classifications-shipping-methods-and-payment-methods-data}

<table> 
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td> 
   <td><p><code>/etc/commerce/products</code></p> <p><code>/etc/commerce/orders</code></p> <p><code>/etc/commerce/collections</code></p> <p><code>/etc/commerce/classifications</code></p> <p><code>/etc/commerce/shipping-methods</code></p> <p><code>/etc/commerce/payment-methods</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td> 
   <td><p><code>/var/commerce/products</code></p> <p><code>/var/commerce/orders</code></p> <p><code>/var/commerce/collections</code></p> <p><code>/var/commerce/classifications</code></p> <p><code>/var/commerce/shipping-methods</code></p> <p><code>/var/commerce/payment-methods</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td> 
   <td><p>Sie können eine <a href="/help/sites-deploying/lazy-content-migration.md" target="_blank">Lazy Migration</a> Aufgabe zum Migrieren von E-Commerce-Daten.</p> <p>Sie führt die folgenden Schritte aus:</p> 
    <ul> 
     <li>passt Verweise auf den alten Speicherort an, um auf den neuen Speicherort zu verweisen</li> 
     <li>verschiebt Inhalte von einem alten Speicherort zum neuen Speicherort</li> 
     <li>entfernt den alten Speicherort, um schließlich die Verwendung des neuen Speicherorts im gesamten System zu aktivieren.</li> 
    </ul> <p>Folgende Orte werden von der Aufgabe abgedeckt:</p> 
    <ul> 
     <li>/etc/commerce/products</li> 
     <li>/etc/commerce/collections<br /> </li> 
     <li>/etc/commerce/orders<br /> </li> 
     <li>/etc/commerce/payment-methods<br /> </li> 
     <li>/etc/commerce/shipping-methods<br /> </li> 
    </ul> <p>Für größere Kataloge wird empfohlen, die Commerce-Migrationsaufgabe einzeln auszuführen, indem die folgende Java-Systemeigenschaft an AEM übergeben wird:</p> <p><code>propertyname: com.adobe.upgrade.forcemigration</code></p> <p><code>property value: com.day.cq.compat.codeupgrade.impl.cq64.CQ64CommerceMigrationTask</code></p> <p>Nach der Migration muss AEM neu gestartet werden.</p> </td> 
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td> 
   <td>Nicht zutreffend<br /> </td> 
  </tr>
 </tbody>
</table>
