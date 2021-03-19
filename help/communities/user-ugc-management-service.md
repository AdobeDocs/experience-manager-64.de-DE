---
title: Verwaltungsdienst für Benutzer und benutzergenerierte Inhalte in AEM Communities
seo-title: Verwaltungsdienst für Benutzer und benutzergenerierte Inhalte in AEM Communities
description: 'Verwenden Sie APIs zur Massenlöschung und zum Massenexport von benutzergenerierten Inhalten sowie zum Deaktivieren von Benutzerkonten. '
seo-description: 'Verwenden Sie APIs zur Massenlöschung und zum Massenexport von benutzergenerierten Inhalten sowie zum Deaktivieren von Benutzerkonten. '
uuid: f4663825-eac8-4ef5-8253-46875e0cd71d
contentOwner: mgulati
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
discoiquuid: f564759f-fb56-4f70-a7b1-286a223755c6
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 38%

---


# Verwaltungsdienst für Benutzer und benutzergenerierte Inhalte in AEM Communities {#user-and-ugc-management-service-in-aem-communities}

>[!IMPORTANT]
>
>GDPR wird als Beispiel in den folgenden Abschnitten verwendet, aber die betreffenden Details gelten für alle Datenschutz- und Datenschutzbestimmungen. wie GDPR, CCPA usw.

AEM Communities stellt bereits verfügbare APIs zur Verwaltung von Profilen und Massenverwaltung benutzergenerierter Inhalte (UGC) bereit. Nach der Aktivierung ermöglicht der Dienst **UserUgcManagement** den privilegierten Benutzern (Community-Administratoren und -Moderatoren), Benutzerkonten zu deaktivieren und benutzerspezifische Profil für Massenlöschen oder Massenexport-UGC für bestimmte Benutzer zu verwenden. Diese APIs ermöglichen es den für die Verarbeitung und Verarbeitung von Kundendaten Verantwortlichen und Verarbeitern auch, die allgemeinen Datenschutzbestimmungen der Europäischen Vereinigung (GDPR) und andere vom GDPR inspirierte Datenschutzauflagen einzuhalten.

Weitere Informationen finden Sie auf der [DSGVO-Seite im Datenschutzzentrum von Adobe](https://www.adobe.com/de/privacy/general-data-protection-regulation.html).

>[!NOTE]
>
>Wenn Sie die Site [Adobe Analytics in AEM Communities](analytics.md) konfiguriert haben, werden die erfassten Benutzerdaten an den Adobe Analytics-Server gesendet. Adobe Analytics stellt APIs bereit, mit denen Sie auf Benutzerdaten zugreifen, sie exportieren und löschen und GDPR einhalten können. Weitere Informationen finden Sie unter [Anforderungen senden und Löschen](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/gdpr-submit-access-delete.html).

Damit diese APIs verwendet werden können, müssen Sie den Endpunkt `/services/social/ugcmanagement` aktivieren, indem Sie den UserUgcManagement-Dienst aktivieren. Um diesen Dienst zu aktivieren, installieren Sie das [Beispiel-Servlet](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet), das unter [GitHub.com](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet) verfügbar ist. Dann drücken Sie den Endpunkt auf der Veröffentlichungsinstanz Ihrer Communities-Site mit den entsprechenden Parametern mithilfe einer HTTP-Anforderung, ähnlich wie im Folgenden:

`http://localhost:port/services/social/ugcmanagement?user=<authorizable ID>&operation<getUgc>`

Alternativ dazu können Sie auch eine grafische Benutzeroberfläche erstellen, über die Sie dann die im System vorhandenen Benutzerprofile und benutzergenerierten Inhalte verwalten können.

Mit diesen APIs können die folgenden Funktionen ausgeführt werden:

## Benutzergenerierte Inhalte abrufen {#retrieve-the-ugc-of-a-user}

`getUserUgc(ResourceResolver resourceResolver, String user, OutputStream outputStream)` unterstützt den Export des gesamten UGC eines Benutzers aus dem System.

* **Benutzer**: autorisierbare ID eines Benutzers.
* **outputStream**: Das Ergebnis wird als Ausgabestream in einer ZIP-Datei ausgegeben, die die benutzergenierten Inhalte (als JSON-Datei) sowie Anhänge (vom Benutzer hochgeladene Bilder oder Videos) enthält.

Beispiel: Um die Inhalte zu exportieren, die ein Benutzer mit dem Namen „Weston McCall“ generiert hat und der für die Anmeldung bei der Communities-Site über die ID „weston.mccall@dodgit.com“ autorisiert wird, können Sie eine HTTP-GET-Anfrage senden. Diese kann in etwa wie folgt aussehen:

`http://localhost:port/services/social/ugcmanagement?user=weston.mccall@dodgit.com&operation=getUgc`

## Benutzergenerierte Inhalte löschen {#delete-the-ugc-of-a-user}

**deleteUserUgc(ResourceResolver resourceResolver, String user)** hilft beim Löschen des gesamten UGC für einen Benutzer aus dem System.

* **user**: Die zur Autorisierung eines Benutzers verwendete ID.

Um beispielsweise die UGC eines Benutzers mit autorisierbarer ID weston.mccall@dodgit.com über eine HTTP-POST-Anforderung zu löschen, verwenden Sie die folgenden Parameter:

* user= weston.mccall@dodgit.com
* operation= deleteUgc

### UGC aus Adobe Analytics löschen {#delete-ugc-from-analytics}

Um Benutzerdaten aus dem Adobe Analytics zu löschen, befolgen Sie den Arbeitsablauf für GDPR-Analysen. da die API keine Benutzerdaten aus Adobe Analytics löscht.

Für Adobe Analytics-Variablenzuordnungen, die von AEM Communities verwendet werden, siehe folgende Abbildung:

![Variablenzuordnung AEM Communities für Adobe Analytics](assets/Analytics-Communities-Mapping.png)

## Benutzerkonto deaktivieren {#disable-a-user-account}

**deleteUserAccount(ResourceResolver resourceResolver, String user)** hilft beim Deaktivieren eines Benutzerkontos.

* **user**: Die zur Autorisierung eines Benutzers verwendete ID.

>[!NOTE]
>
>Durch das Deaktivieren eines Benutzers wird der gesamte von diesem generierte Inhalt gelöscht, der auf dem Server vorhanden ist.

Um beispielsweise das Profil eines Benutzers mit autorisierbarer ID weston.mccall@dodgit.com über eine HTTP-POST-Anforderung zu löschen, verwenden Sie die folgenden Parameter:

* user= weston.mccall@dodgit.com
* operation= deleteUser

>[!NOTE]
>
>Mit der API „deleteUserAccount()“ werden im System nur die benutzergenerierten Inhalte gelöscht, das diesen zugehörige Benutzerprofil wird damit lediglich deaktiviert. Um ein Profil zu löschen, navigieren Sie jedoch zu **CRXDE Lite**: [https://&lt;server>/crx/de](http://localhost:4502/crx/de), suchen Sie den Benutzerknoten und löschen Sie ihn.
