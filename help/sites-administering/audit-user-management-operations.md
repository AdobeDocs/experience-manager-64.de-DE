---
title: Prüfen von Benutzerverwaltungsvorgängen in AEM
seo-title: How to Audit User Management Operations in AEM
description: Erfahren Sie, wie Sie User Management-Vorgänge in AEM überprüfen.
feature: Operations
seo-description: Learn how to audit User Management Operations in AEM.
uuid: 4ea704b4-9150-4b5f-b9cb-cdac95cfd70c
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 437fa139-2dde-41a0-9649-6bb110039618
exl-id: f987c4f5-64dd-491b-aafe-cb98acf0b1eb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 34%

---

# Prüfen von Benutzerverwaltungsvorgängen in AEM{#how-to-audit-user-management-operations-in-aem}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Einführung {#introduction}

AEM hat die Möglichkeit eingeführt, Berechtigungsänderungen zu protokollieren, damit sie zu einem späteren Zeitpunkt überprüft werden können.

Die Verbesserung ermöglicht die Prüfung von CRUD-Aktionen (Erstellen, Lesen, Aktualisieren, Löschen) für Berechtigungen und Gruppenzuweisungen von Benutzern. Konkret wird Folgendes protokolliert:

* Ein neuer Benutzer wird erstellt
* Einen Benutzer, der einer Gruppe hinzugefügt wird
* Berechtigungsänderungen eines vorhandenen Benutzers oder einer vorhandenen Gruppe

Standardmäßig werden die Einträge in die Datei `error.log` geschrieben. Um die Überwachung zu vereinfachen, empfiehlt es sich, diese Einträge in einer separaten Protokolldatei zu speichern. Weitere Informationen dazu finden Sie im folgenden Absatz.

## Weiterleiten der Ausgabe in eine separate Protokolldatei {#redirecting-the-output-to-a-separate-log-file}

Um die Protokollierungsausgabe in eine separate Protokolldatei umzuleiten, müssen Sie eine neue **Apache Sling Logging Logger** Konfiguration. Im folgenden Beispiel verwenden wir `useraudit.log` als Namen dieser separaten Datei.

1. Navigieren Sie zur Web-Konsole , indem Sie zu `https://<serveraddress>:<serverport>/system/console/configMgr`
1. Suchen Sie nach **Apache Sling Logging Logger-Konfiguration**. Klicken Sie dann auf das &quot;+&quot; rechts vom Eintrag, um eine neue Werkskonfiguration zu erstellen.
1. Erstellen Sie die folgende Konfiguration:

   * **Protokollebene:** Informationen
   * **Protokolldatei:** logs/useraudit.log
   * **Nachrichtenmuster:** Standardwert beibehalten
   * **Logger:** com.adobe.granite.security.user.internal.audit, com.adobe.granite.security.user.internal.servlets.AuthorizableServlet

   Um beide Logger in das Feld **Logger** einzugeben, müssen Sie den Namen des ersten Loggers eingeben und dann ein weiteres Feld erstellen. Klicken Sie dazu auf die Schaltfläche „+“. Nun können Sie den Namen des zweiten Loggers eingeben.

## Beispielausgabe {#example-output}

Bei richtiger Konfiguration sollte die Ausgabe wie folgt aussehen:

```xml
19.05.2017 15:15:08.933 *INFO* [0:0:0:0:0:0:0:1 [1495196108932] POST /libs/granite/security/post/authorizables.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Create Group 'group1' operation initiated by User 'admin' (administrator)
19.05.2017 15:15:08.934 *INFO* [0:0:0:0:0:0:0:1 [1495196108932] POST /libs/granite/security/post/authorizables.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditAuthorizableAction Group 'group1' was created

19.05.2017 15:16:25.698 *INFO* [0:0:0:0:0:0:0:1 [1495196185696] POST /libs/granite/security/post/authorizables.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Create User 'user1' operation initiated by User 'admin' (administrator)
19.05.2017 15:16:25.700 *INFO* [0:0:0:0:0:0:0:1 [1495196185696] POST /libs/granite/security/post/authorizables.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditAuthorizableAction User 'user1' was created

19.05.2017 15:16:25.728 *INFO* [0:0:0:0:0:0:0:1 [1495196185726] POST /home/groups/d/dGf7f7vGrZRLs6HS3AK-.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Edit Membership for Group 'group1' operation initiated by User 'admin' (administrator)
19.05.2017 15:16:25.729 *INFO* [0:0:0:0:0:0:0:1 [1495196185726] POST /home/groups/d/dGf7f7vGrZRLs6HS3AK-.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditGroupAction User 'user1' was added to the group 'group1'

19.05.2017 15:17:29.830 *INFO* [0:0:0:0:0:0:0:1 [1495196249828] POST /home/users/5/5dI6iK4HkZmrfTjcLBoI.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Password Change for User 'user2' operation initiated by User 'admin' (administrator)
19.05.2017 15:17:29.832 *INFO* [0:0:0:0:0:0:0:1 [1495196249828] POST /home/users/5/5dI6iK4HkZmrfTjcLBoI.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditAuthorizableAction Password for User 'user2' was changed

19.05.2017 15:17:54.906 *INFO* [0:0:0:0:0:0:0:1 [1495196274904] POST /home/users/5/5dI6iK4HkZmrfTjcLBoI.rw.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Delete User 'user2' operation initiated by User 'admin' (administrator)
19.05.2017 15:17:54.906 *INFO* [0:0:0:0:0:0:0:1 [1495196274904] POST /home/users/5/5dI6iK4HkZmrfTjcLBoI.rw.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditAuthorizableAction User 'user2' was removed

19.05.2017 15:19:11.050 *INFO* [0:0:0:0:0:0:0:1 [1495196351049] POST /libs/granite/security/post/authorizables.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Create User 'user3' operation initiated by User 'admin' (administrator)
19.05.2017 15:19:11.052 *INFO* [0:0:0:0:0:0:0:1 [1495196351049] POST /libs/granite/security/post/authorizables.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditAuthorizableAction User 'user3' was created
19.05.2017 15:19:36.899 *INFO* [0:0:0:0:0:0:0:1 [1495196376898] POST /home/groups/d/dGf7f7vGrZRLs6HS3AK-.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Edit Membership for Group 'group1' operation initiated by User 'admin' (administrator)

19.05.2017 15:19:36.916 *INFO* [0:0:0:0:0:0:0:1 [1495196376915] POST /home/groups/d/dGf7f7vGrZRLs6HS3AK-.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Edit Membership for Group 'group1' operation initiated by User 'admin' (administrator)
19.05.2017 15:19:36.917 *INFO* [0:0:0:0:0:0:0:1 [1495196376915] POST /home/groups/d/dGf7f7vGrZRLs6HS3AK-.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditGroupAction User 'user1' was removed from the group 'group1'

19.05.2017 15:21:34.419 *INFO* [0:0:0:0:0:0:0:1 [1495196494417] POST /home/groups/d/dGf7f7vGrZRLs6HS3AK-.rw.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Delete Group 'group1' operation initiated by User 'admin' (administrator)
19.05.2017 15:21:34.419 *INFO* [0:0:0:0:0:0:0:1 [1495196494417] POST /home/groups/d/dGf7f7vGrZRLs6HS3AK-.rw.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditAuthorizableAction Group 'group1' was removed

19.05.2017 15:44:10.404 *INFO* [0:0:0:0:0:0:0:1 [1495197850401] POST /home/users/3/35XVpVtLRx4a5J9gKrVG.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Password Change for User 'john' operation initiated by User 'john' (not administrator)
19.05.2017 15:44:10.405 *INFO* [0:0:0:0:0:0:0:1 [1495197850401] POST /home/users/3/35XVpVtLRx4a5J9gKrVG.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditAuthorizableAction Password for User 'john' was changed
```

## Klassische Benutzeroberfläche

In der klassischen Benutzeroberfläche sind Informationen zu CRUD-Vorgängen, die im Auditprotokoll zum Hinzufügen und Löschen von Benutzern aufgezeichnet werden, auf die ID des betroffenen Benutzers und den Zeitpunkt der Änderung beschränkt.

Beispiel:

```
10.05.2019 18:01:09.123 INFO [0:0:0:0:0:0:0:1 [1557491469096] POST /libs/cq/security/authorizables/POST HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditAuthorizableAction User 'test' was created
```
