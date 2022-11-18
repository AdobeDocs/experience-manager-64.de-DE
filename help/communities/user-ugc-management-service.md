---
title: Verwaltungsdienst für Benutzer und benutzergenerierte Inhalte in AEM Communities
seo-title: User and UGC Management Service in AEM Communities
description: Verwenden Sie APIs zur Massenlöschung und zum Massenexport von benutzergenerierten Inhalten sowie zum Deaktivieren von Benutzerkonten.
seo-description: Use APIs to bulk delete and bulk export user generated content, and disable user account.
uuid: f4663825-eac8-4ef5-8253-46875e0cd71d
contentOwner: mgulati
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
discoiquuid: f564759f-fb56-4f70-a7b1-286a223755c6
role: Admin
exl-id: f4adc53d-6809-4d89-a3dd-5d783e938a63
source-git-commit: 0f4f8c2640629f751337e8611a2c8f32f21bcb6d
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 40%

---

# Verwaltungsdienst für Benutzer und benutzergenerierte Inhalte in AEM Communities {#user-and-ugc-management-service-in-aem-communities}

>[!IMPORTANT]
>
>Die DSGVO wird in den folgenden Abschnitten als Beispiel verwendet, aber die behandelten Details gelten für alle Datenschutzbestimmungen wie die DSGVO, CCPA usw.

AEM Communities stellt native APIs zur Verwaltung von Benutzerprofilen und zur Massenverwaltung benutzergenerierter Inhalte bereit. Nach der Aktivierung wird die **UserUgcManagement** Der -Dienst ermöglicht es berechtigten Benutzern (Community-Administratoren und -Moderatoren), Benutzerprofile zu deaktivieren und UGC-Dateien für bestimmte Benutzer per Massenlöschung oder Massenexport zu löschen. Diese APIs ermöglichen es auch den Datenverantwortlichen und Verarbeitern von Kundendaten, die Datenschutz-Grundverordnung (DSGVO) der Europäischen Union und andere DSGVO-inspirierte Datenschutzmandate einzuhalten.

Weitere Informationen finden Sie auf der [DSGVO-Seite im Datenschutzzentrum von Adobe](https://www.adobe.com/de/privacy/general-data-protection-regulation.html).

>[!NOTE]
>
>Wenn Sie [Adobe Analytics in AEM Communities](analytics.md) Site werden die erfassten Benutzerdaten an den Adobe Analytics-Server gesendet. Adobe Analytics bietet APIs, mit denen Sie auf Benutzerdaten zugreifen, diese exportieren und löschen und die DSGVO einhalten können. Weitere Informationen finden Sie unter [Zugriffs- und Löschanfragen einreichen](https://experienceleague.adobe.com/docs/analytics/admin/data-governance/gdpr-submit-access-delete.html).

Damit diese APIs verwendet werden können, müssen Sie die `/services/social/ugcmanagement` -Endpunkt durch Aktivierung des UserUgcManagement-Dienstes. Um diesen Dienst zu aktivieren, installieren Sie die [Beispiel-Servlet](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet) verfügbar unter [GitHub.com](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet). Drücken Sie dann den Endpunkt auf der Veröffentlichungsinstanz Ihrer Communities-Site mit den entsprechenden Parametern mithilfe einer HTTP-Anfrage, ähnlich der folgenden:

`http://localhost:port/services/social/ugcmanagement?user=<authorizable ID>&operation<getUgc>`

Alternativ dazu können Sie auch eine grafische Benutzeroberfläche erstellen, über die Sie dann die im System vorhandenen Benutzerprofile und benutzergenerierten Inhalte verwalten können.

Mit diesen APIs können die folgenden Funktionen ausgeführt werden:

## Benutzergenerierte Inhalte abrufen {#retrieve-the-ugc-of-a-user}

`getUserUgc(ResourceResolver resourceResolver, String user, OutputStream outputStream)` unterstützt den Export aller benutzergenerierten Inhalte eines Benutzers aus dem System.

* **Benutzer**: autorisierbare ID eines Benutzers.
* **outputStream**: Das Ergebnis wird als Ausgabestream in einer ZIP-Datei ausgegeben, die die benutzergenierten Inhalte (als JSON-Datei) sowie Anhänge (vom Benutzer hochgeladene Bilder oder Videos) enthält.

Beispiel: Um die Inhalte zu exportieren, die ein Benutzer mit dem Namen „Weston McCall“ generiert hat und der für die Anmeldung bei der Communities-Site über die ID „weston.mccall@dodgit.com“ autorisiert wird, können Sie eine HTTP-GET-Anfrage senden. Diese kann in etwa wie folgt aussehen:

`http://localhost:port/services/social/ugcmanagement?user=weston.mccall@dodgit.com&operation=getUgc`

## Benutzergenerierte Inhalte löschen {#delete-the-ugc-of-a-user}

**deleteUserUgc(ResourceResolver resourceResolver, String user)** hilft, alle benutzergenerierten Inhalte für einen Benutzer aus dem System zu löschen.

* **user**: Die zur Autorisierung eines Benutzers verwendete ID.

Um beispielsweise die benutzergenerierte Inhalte eines Benutzers mit autorisierbarer ID weston.mccall@dodgit.com über eine HTTP-POST-Anfrage zu löschen, verwenden Sie die folgenden Parameter:

* user= weston.mccall@dodgit.com
* operation= deleteUgc

### UGC aus Adobe Analytics löschen {#delete-ugc-from-analytics}

Um Benutzerdaten aus der Adobe Analytics zu löschen, folgen Sie dem DSGVO-Analytics-Workflow. da die API keine Benutzerdaten aus Adobe Analytics löscht.

Informationen zu von AEM Communities verwendeten Adobe Analytics-Variablenzuordnungen finden Sie in der folgenden Abbildung:

![Variablenzuordnung für AEM Communities in Adobe Analytics](assets/Analytics-Communities-Mapping.png)

## Benutzerkonto deaktivieren {#disable-a-user-account}

**deleteUserAccount(ResourceResolver resourceResolver, String user)** hilft, ein Benutzerkonto zu deaktivieren.

* **user**: Die zur Autorisierung eines Benutzers verwendete ID.

>[!NOTE]
>
>Durch das Deaktivieren eines Benutzers wird der gesamte von diesem generierte Inhalt gelöscht, der auf dem Server vorhanden ist.

Um beispielsweise das Profil eines Benutzers mit autorisierbarer ID weston.mccall@dodgit.com über eine HTTP-POST-Anfrage zu löschen, verwenden Sie die folgenden Parameter:

* user= weston.mccall@dodgit.com
* operation= deleteUser

>[!NOTE]
>
>Mit der API „deleteUserAccount()“ werden im System nur die benutzergenerierten Inhalte gelöscht, das diesen zugehörige Benutzerprofil wird damit lediglich deaktiviert. Um jedoch ein Benutzerprofil aus dem System zu löschen, navigieren Sie zu **CRXDE Lite**: [https://&lt;server>/crx/de](http://localhost:4502/crx/de), suchen Sie den Benutzerknoten und löschen Sie ihn.
