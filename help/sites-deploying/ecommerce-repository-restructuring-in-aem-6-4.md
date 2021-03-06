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
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 84%

---

# E-Commerce-Repository-Neustrukturierung in AEM 6.4{#e-commerce-repository-restructuring-in-aem}

Wie im übergeordneten Element beschrieben [Repository-Neustrukturierung in AEM 6.4](/help/sites-deploying/repository-restructuring.md) -Seite sollten Kunden, die auf AEM 6.4 aktualisieren, diese Seite verwenden, um den Arbeitsaufwand im Zusammenhang mit Repository-Änderungen zu bewerten, die sich auf die E-Commerce-AEM auswirken. Einige Änderungen erfordern einen Arbeitsaufwand während des Aktualisierungsprozesses auf AEM 6.4, während andere bis zu einer Aktualisierung auf 6.5 verschoben werden können.

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
   <td><p>Sie können die Aufgabe <a href="/help/sites-deploying/lazy-content-migration.md" target="_blank">Lazy Migration</a> verwenden, um E-Commerce-Daten zu migrieren.</p> <p>Folgende Schritte werden ausgeführt:</p> 
    <ul> 
     <li>passt Referenzen auf den alten Speicherort so an, dass nur auf den neuen Speicherort verwiesen wird.</li> 
     <li>verschiebt Inhalte vom alten Speicherort an den neuen Speicherort</li> 
     <li>entfernt den alten Speicherort, um letztlich die Verwendung des neuen Speicherorts im gesamten System zu aktivieren</li> 
    </ul> <p>Die von der Aufgabe betroffenen Speicherorte:</p> 
    <ul> 
     <li>/etc/commerce/products</li> 
     <li>/etc/commerce/collections<br /> </li> 
     <li>/etc/commerce/orders<br /> </li> 
     <li>/etc/commerce/payment-methods<br /> </li> 
     <li>/etc/commerce/shipping-methods<br /> </li> 
    </ul> <p>Für größere Kataloge wird empfohlen, die Commerce-Migration einzeln auszuführen, indem die folgende Java-Systemeigenschaft an AEM übergeben wird:</p> <p><code>propertyname: com.adobe.upgrade.forcemigration</code></p> <p><code>property value: com.day.cq.compat.codeupgrade.impl.cq64.CQ64CommerceMigrationTask</code></p> <p>Nach der Migration muss AEM neu gestartet werden.</p> </td> 
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td> 
   <td>Nicht zutreffend<br /> </td> 
  </tr>
 </tbody>
</table>
