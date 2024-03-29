---
title: Fehlerbehebung
seo-title: Troubleshooting
description: Fehlerbehebung in der Community einschließlich bekannter Probleme
seo-description: Troubleshooting Community including Known Issues
uuid: 99225430-fa2a-4393-ae5a-18b19541c358
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: cdb2d80a-2fbf-4ee6-b89b-b5d74e6d3bfc
exl-id: 1a1de20d-53f6-4787-92e3-e12f30d925d3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 3%

---

# Fehlerbehebung {#troubleshooting}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Dieser Abschnitt enthält allgemeine Probleme und bekannte Probleme.

## Bekannte Probleme {#known-issues}

### Dispatcher-Neuabruf schlägt fehl {#dispatcher-refetch-fails}

Bei Verwendung von Dispatcher 4.1.5 mit einer neueren Version von Jetty kann eine Refektion dazu führen, dass &quot;Antwort vom Remote-Server kann nicht empfangen&quot;angezeigt wird, nachdem auf die Anfrage zum Timeout gewartet wurde.

Durch die Verwendung von Dispatcher 4.1.6 oder höher wird dieses Problem behoben.

### Nach der Aktualisierung von CQ 5.4 kann nicht auf Forumsbeiträge zugegriffen werden {#cannot-access-forum-post-after-upgrading-from-cq}

Wenn ein Forum in CQ 5.4 erstellt wurde und Themen veröffentlicht wurden und die Site dann auf AEM 5.6.1 oder höher aktualisiert wurde, kann der Versuch, die vorhandenen Beiträge anzuzeigen, zu einem Fehler auf der Seite führen:

unzulässiges Musterzeichen &#39;a&#39;\
Anfrage an /content/demoforums/forum-test.html auf diesem Server kann nicht bereitgestellt werden

Die Protokolle enthalten Folgendes:

```xml
20.03.2014 22:49:35.805 ERROR [10.177.45.32 [1395380975744] GET /content/demoforums/forum-test.html HTTP/1.1] com.day.cq.wcm.tags.IncludeTag Error while executing script content.jsp
org.apache.sling.api.scripting.ScriptEvaluationException: 
at org.apache.sling.scripting.core.impl.DefaultSlingScript.call(DefaultSlingScript.java:388)
at org.apache.sling.scripting.core.impl.DefaultSlingScript.eval(DefaultSlingScript.java:171)
```

Das Problem besteht darin, dass die Formatzeichenfolge für com.day.cq.commons.date.RelativeTimeFormat zwischen 5.4 und 5.5 geändert wurde, sodass das &quot;a&quot;für &quot;ago&quot;nicht mehr akzeptiert wird.

Daher muss jeder Code, der die RelativeTimeFormat()-API verwendet,

* Von: `final RelativeTimeFormat fmt = new RelativeTimeFormat("r a", resourceBundle);`
* An: `final RelativeTimeFormat fmt = new RelativeTimeFormat("r", resourceBundle);`

Der Fehler unterscheidet sich bei der Autoren- und Veröffentlichungsinstanz. Beim Autor schlägt es still fehl und zeigt die Forenthemen einfach nicht an. Beim Veröffentlichen wird der Fehler auf der Seite ausgegeben.

Siehe [com.day.cq.commons.date.RelativeTimeFormat](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/date/RelativeTimeFormat.html) API für weitere Informationen.

## Häufige Bedenken {#common-concerns}

### Warnung in Protokollen: Handlebars - veraltet {#warning-in-logs-handlebars-deprecated}

Während des Starts (nicht der 1., sondern alle darauf folgenden) kann die folgende Warnung in den Protokollen angezeigt werden:

* 11.04.2014 08:38:07 223 **WARN** [FelixStartLevel]com.github.jknack.handlebars.Handlebars Helper &#39;i18n&#39; wurde durch &#39;com.adobe.cq.social.handlebars.I18nHelper@15bac645&#39; ersetzt.

Diese Warnung kann sicher ignoriert werden als jknack.handlebars.Handlebars, verwendet von [SCF](scf.md#handlebarsjavascripttemplatinglanguage), ist mit einem eigenen i18n Helper-Dienstprogramm ausgestattet. Beim Start wird er durch eine AEM spezifische [i18n Helper](handlebars-helpers.md#i-n). Diese Warnung wird von der Bibliothek eines Drittanbieters generiert, um das Außerkraftsetzen eines vorhandenen Helfers zu bestätigen.

### Warnung in Protokollen: OakResourceListener processOsgiEventQueue {#warning-in-logs-oakresourcelistener-processosgieventqueue}

Das Posten einer Reihe von Forumsthemen in Social Communities kann zu einer großen Menge an Warn- und Infoprotokollen aus OakResourceListener processOsgiEventQueue führen.

Diese Warnungen können ignoriert werden.

```xml
23.04.2014 14:21:18.900 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/search-collections/ugc-sc/_m.frq/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.908 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/search-collections/ugc-sc/_m.prx/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.909 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/replication/data/1f799fb4-0aeb-4660-aadb-705657f16048/67/67699ab5-9d57-4c79-a755-2727ba9e6452/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.909 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/replication/data/1f799fb4-0aeb-4660-aadb-705657f16048/67/67699ab5-9d57-4c79-a755-2727ba9e6452/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.990 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/replication/data/1f799fb4-0aeb-4660-aadb-705657f16048/b9/b91f1690-87e8-41d8-a78e-cd2259f837c8/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.990 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/replication/data/1f799fb4-0aeb-4660-aadb-705657f16048/b9/b91f1690-87e8-41d8-a78e-cd2259f837c8/jcr:content not found, which is not expected for an added or modified node
```

### Fehler in Protokollen: NoClassDefFoundError für IndexElementFactory {#error-in-logs-noclassdeffounderror-for-indexelementfactory}

Die Aktualisierung von AEM 5.6.1 GA auf die neueste Version von cq-socialcommunities-pkg-1.4.x oder auf AEM 6.0 führt zu Fehlern in der Protokolldatei während des Starts für eine Bedingung, die sich löst, wie der Fehler zeigt, der beim Neustart nicht erkannt wird.

```xml
14.11.2013 20:52:39.453 ERROR [Apache Sling JCR Resource Event Queue Processor for path '/'] com.adobe.cq.social.storage.index.impl.IndexService Error occurred while processing event java.util.ConcurrentModificationException
14.11.2013 20:52:40.716 ERROR [OsgiInstallerImpl] com.adobe.cq.social.cq-social-commons [CommentListProvider] Error during instantiation of the implementation object (java.lang.NoClassDefFoundError: com/adobe/cq/social/storage/index/IndexElementFactory) java.lang.NoClassDefFoundError: com/adobe/cq/social/storage/index/IndexElementFactory
14.11.2013 20:52:40.717 ERROR [OsgiInstallerImpl] com.adobe.cq.social.cq-social-commons [CommentListProvider] Failed creating the component instance; see log for reason
```
