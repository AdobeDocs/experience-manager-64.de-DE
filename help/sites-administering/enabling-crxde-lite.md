---
title: Aktivieren von CRXDE Lite in AEM
seo-title: Aktivieren von CRXDE Lite in AEM
description: Erfahren Sie, wie Sie CRXDE Lite in AEM aktivieren können.
seo-description: Erfahren Sie, wie Sie CRXDE Lite in AEM aktivieren können.
uuid: d7a3db67-6384-463b-9aa9-f08ecc6c99c6
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 72df3ece-badf-466b-8f9a-0ec985d87741
exl-id: 3d8dc987-2ff9-4f71-bc07-48018caa3af4
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 87%

---

# Aktivieren von CRXDE Lite in AEM{#enabling-crxde-lite-in-aem}

Um dafür zu sorgen, dass AEM-Installationen so sicher wie möglich sind, wird gemäß Sicherheitsprüfliste empfohlen, in Produktionsumgebungen [WebDAV zu deaktivieren](/help/sites-administering/security-checklist.md#disable-webdav).

Allerdings hängt CRXDE Lite davon ab, dass das Bundle `org.apache.sling.jcr.davex` ordnungsgemäß funktioniert, weshalb durch die Deaktivierung von WebDAV effektiv auch CRXDE Lite deaktiviert wird.

Wenn dies geschieht, zeigt das Browsen zu `https://serveraddress:4502/crx/de/index.jsp` einen leeren Stammknoten an, und alle HTTP-Anforderungen an CRXDE Lite-Ressourcen schlagen fehl:

```xml
404 Resource at '/crx/server/crx.default/jcr:root/.1.json' not found: No resource found
```

Während diese Empfehlung dazu dient, Angriffsflächen so weit wie möglich zu minimieren, müssen Systemadministratoren manchmal vielleicht auf CRXDE Lite zugreifen, um Inhalte zu durchsuchen oder Probleme von Produktionsinstanzen zu debuggen.

Wenn CRXDE Lite deaktiviert ist, können Sie es wieder aktivieren, indem Sie wie folgt vorgehen:

1. Wechseln Sie zur OSGi-Komponentenkonsole unter `http://localhost:4502/system/console/components`
1. Suchen Sie nach der folgenden Komponente:

   * `org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet`

1. Klicken Sie auf das Schraubenschlüsselsymbol daneben, um die Konfigurationsoptionen anzuzeigen:

   ![chlimage_1-80](assets/chlimage_1-80.png)

1. Erstellen Sie die folgende Konfiguration:

   * **Stammverzeichnis:** `/crx/server`
   * Markieren Sie das Kästchen unter **Absolute URIs verwenden**.

1. Wenn Sie mit der Verwendung von CRXDE Lite fertig sind, stellen Sie sicher, dass Sie WebDAV erneut deaktivieren.

Sie können CRXDE Lite auch über cURL aktivieren, indem Sie diesen Befehl ausführen:

```shell
curl -u admin:admin -F "jcr:primaryType=sling:OsgiConfig" -F "alias=/crx/server" -F "dav.create-absolute-uri=true" -F "dav.create-absolute-uri@TypeHint=Boolean" http://localhost:4502/apps/system/config/org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet
```

## Sonstige Ressourcen  {#other-resources}

Weitere Informationen zu den Sicherheitsfunktionen von AEM 6 finden Sie auf den folgenden Seiten:

* [Die AEM-Sicherheitsprüfliste](/help/sites-administering/security-checklist.md)
* [Ausführung von AEM im produktionsbereiten Modus](/help/sites-administering/production-ready.md)
