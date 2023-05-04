---
title: Single Sign-On
seo-title: Single Sign On
description: Erfahren Sie, wie Sie Single Sign-On (SSO) für eine AEM-Instanz konfigurieren.
seo-description: Learn how to configure Single Sign On (SSO) for an AEM instance.
uuid: b8dcb28e-4604-4da5-b8dd-4e1e2cbdda18
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: Security, configuring
discoiquuid: 86e8dc12-608d-4aff-ba7a-5524f6b4eb0d
feature: Configuring
exl-id: ae7e8ce6-7bdd-462b-8939-361c122317b3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 45%

---

# Single Sign-On {#single-sign-on}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mithilfe von Single Sign-On (SSO) können Sie durch die einmalige Eingabe Ihrer Zugangsdaten (z. B. Ihres Benutzernamens und Passworts) auf mehrere Systeme zugreifen. Ein separates System (auch als vertrauenswürdiger Authentifizierer bezeichnet) führt die Authentifizierung durch und stellt den Experience Manager die Benutzeranmeldeinformationen zur Verfügung. Experience Manager überprüft und erzwingt die Zugriffsberechtigungen für den Benutzer (d. h. legt fest, auf welche Ressourcen der Benutzer zugreifen darf).

Der Handler-Dienst der SSO-Authentifizierung (`com.adobe.granite.auth.sso.impl.SsoAuthenticationHandler`) verarbeitet die von der vertrauenswürdigen Authentifizierung bereitgestellten Authentifizierungsergebnisse. Der SSO-Authentifizierungs-Handler sucht nach einer SSID (SSO-Kennung) als Wert eines speziellen Attributs an folgenden Speicherorten in dieser Reihenfolge:

1. Anforderungsheader
1. Cookies
1. Anfrageparameter

Wenn ein Wert gefunden wird, ist die Suche abgeschlossen und dieser Wert wird verwendet.

Konfigurieren Sie die folgenden beiden Dienste, um den Namen des Attributs zu erkennen, in dem die Sid gespeichert wird:

* Das Anmeldemodul.
* Der SSO-Authentifizierungsdienst.

Sie müssen denselben Attributnamen für beide Dienste angeben. Das Attribut ist in den `SimpleCredentials` enthalten, die beim `Repository.login` angegeben werden. Der Wert des Attributs ist irrelevant und wird ignoriert, das bloße Vorhandensein ist wichtig und verifiziert.

## Konfigurieren von SSO {#configuring-sso}

Um SSO für eine AEM-Instanz zu konfigurieren, müssen Sie die [SSO-Authentifizierungs-Handler](/help/sites-deploying/osgi-configuration-settings.md#adobegranitessoauthenticationhandler):

1. Bei der Verwendung von AEM gibt es mehrere Methoden zur Verwaltung der Konfigurationseinstellungen für solche Services. Weitere Informationen und empfohlene Praktiken finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

   Beispiel: für NTLM-Satz:

   * **Pfad:** nach Bedarf, z. B. `/`
   * **Kopfzeilennamen**: `LOGON_USER`
   * **ID-Format**: `^<DOMAIN>\\(.+)$`

      Hierbei wird `<*DOMAIN*>` durch Ihren Domain-Namen ersetzt.
   Für CoSign:

   * **Pfad:** nach Bedarf, z. B. `/`
   * **Kopfzeilennamen**: remote_user
   * **ID-Format:** AsIs

   Für SiteMinder:

   * **Pfad:** nach Bedarf, z. B. `/`
   * **Kopfzeilennamen:** SM_USER
   * **ID-Format:** AsIs



1. Bestätigen Sie, dass Single Sign-on wie erforderlich funktioniert, einschließlich Autorisierung. 

>[!CAUTION]
>
>Stellen Sie sicher, dass Benutzer nicht direkt auf AEM zugreifen können, wenn SSO konfiguriert ist.
>
>Durch die Anforderung, dass Benutzer einen Webserver durchlaufen müssen, auf dem der Agent Ihres SSO-Systems ausgeführt wird, wird sichergestellt, dass kein Benutzer direkt einen Header, ein Cookie oder einen Parameter sendet, der dazu führt, dass der Benutzer von AEM als vertrauenswürdig eingestuft wird, da der Agent diese Informationen filtert, wenn sie von außen gesendet werden.
>
>Jeder Benutzer, der direkt auf Ihre AEM-Instanz zugreifen kann, ohne den Webserver zu durchlaufen, kann wie jeder Benutzer agieren, indem er die Kopfzeile, das Cookie oder den Parameter sendet, sofern die Namen bekannt sind.
>
>Stellen Sie außerdem sicher, dass Sie bei Headern, Cookies und Anforderungsparametern nur den konfigurieren, der für Ihre SSO-Einrichtung erforderlich ist.

>[!NOTE]
>
>Single Sign-On wird oft zusammen mit [LDAP](/help/sites-administering/ldap-config.md).

>[!NOTE]
>
>Wenn Sie auch die [Dispatcher](https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher.html) Mit dem Microsoft Internet Information Server (IIS) ist eine zusätzliche Konfiguration erforderlich in:
>
>* `disp_iis.ini`
>* IIS
>
>Legen Sie in `disp_iis.ini` Folgendes fest:\
>(Einzelheiten finden Sie unter [Installieren des Dispatchers mit dem Microsoft Internet Information Server](https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher-install.html#microsoft-internet-information-server).)
>
>* `servervariables=1` (leitet IIS-Server-Variablen als Anforderungskopfzeilen an die Remote-Instanz weiter)
>* `replaceauthorization=1` (ersetzt alle Kopfzeilen mit dem Namen „Authorization“ mit Ausnahme von „Basic“ durch die Entsprechung von „Basic“)
>
>In IIS:
>
>* Deaktivieren Sie die Option **Anonymer Zugriff**.
>
>* enable **Integrierte Windows-Authentifizierung**
>


Mithilfe der **Authenticator** Option der Felix-Konsole; Beispiel:

`http://localhost:4502/system/console/slingauth`

Der Handler, der zum größten Teil mit dem Pfad übereinstimmt, wird zuerst abgefragt. Falls Sie z. B. Handler-A für den Pfad `/` und Handler-B für den Pfad `/content` konfigurieren, wird bei einer Anforderung an `/content/mypage.html` zuerst Handler-B abgefragt.

![screen_shot_2012-02-15at21006pm](assets/screen_shot_2012-02-15at21006pm.png)

### Beispiel {#example}

Bei einer Cookie-Anforderung (mit der URL `http://localhost:4502/libs/wcm/content/siteadmin.html`):

```xml
GET /libs/cq/core/content/welcome.html HTTP/1.1
Host: localhost:4502
Cookie: TestCookie=admin
```

mit folgender Konfiguration:

* **Pfad**: `/`

* **Kopfzeilennamen**: `TestHeader`

* **Cookie-Namen**: `TestCookie`

* **Parameternamen**: `TestParameter`

* **ID-Format**: `AsIs`

sieht die Antwort wie folgt aus: 

```xml
HTTP/1.1 200 OK
Connection: Keep-Alive
Server: Day-Servlet-Engine/4.1.24 
Content-Type: text/html;charset=utf-8
Date: Thu, 23 Aug 2012 09:58:39 GMT
Transfer-Encoding: chunked

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "https://www.w3.org/TR/html4/strict.dtd">
<html>
<head>
    <meta http-equiv="content-type" content="text/html; charset=UTF-8">
    <title>Welcome to Adobe&reg; CQ5</title>
....
```

Dies funktioniert auch, wenn Sie Folgendes anfordern:\
`http://localhost:4502/libs/cq/core/content/welcome.html?TestParameter=admin`

Sie können auch den folgenden curl-Befehl verwenden, um die `TestHeader`-Kopfzeile an `admin:` zu senden:
\
`curl -D - -H "TestHeader: admin" http://localhost:4502/libs/cq/core/content/welcome.html`

>[!NOTE]
>
>Wenn Sie den Anforderungsparameter in einem Browser verwenden, sehen Sie nur einige der HTML - ohne CSS. Dies liegt daran, dass alle Anfragen von der HTML ohne den Anforderungsparameter durchgeführt werden.

## Entfernen AEM Abmelde-Links {#removing-aem-sign-out-links}

Bei Verwendung von SSO werden Anmelden und Abmelden extern verarbeitet, sodass AEM eigenen Abmelde-Links nicht mehr anwendbar sind und entfernt werden sollten.

Der Abmelde-Link auf dem Willkommensbildschirm kann mithilfe der folgenden Schritte entfernt werden.

1. Überlagern Sie `/libs/cq/core/components/welcome/welcome.jsp` über `/apps/cq/core/components/welcome/welcome.jsp`.
1. Entfernen Sie folgenden Teil aus der JSP-Datei:

   `<a href="#" onclick="signout('<%= request.getContextPath() %>');" class="signout"><%= i18n.get("sign out", "welcome screen") %>`

Um den Abmelde-Link oben rechts aus dem persönlichen Menü des Benutzers zu entfernen, folgen Sie diesen Schritten:

1. Überlagern Sie `/libs/cq/ui/widgets/source/widgets/UserInfo.js` über `/apps/cq/ui/widgets/source/widgets/UserInfo.js`.

1. Entfernen Sie den folgenden Teil aus der Datei:

   ```
   menu.addMenuItem({
       "text":CQ.I18n.getMessage("Sign out"),
       "cls": "cq-userinfo-logout",
       "handler": this.logout
   });
   menu.addSeparator();
   ```
