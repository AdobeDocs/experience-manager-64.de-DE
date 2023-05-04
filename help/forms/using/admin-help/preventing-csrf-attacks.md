---
title: Verhindern von CSRF-Angriffen
seo-title: Preventing CSRF attacks
description: Erfahren Sie, wie Sie CSRF-Angriffe (Cross-Site Request Forgery) verhindern und Benutzerdaten vor Beschädigung schützen können.
seo-description: Learn how to prevent Cross-site request forgery (CSRF) attacks and safeguard user data from being compromised.
uuid: f3553826-f5eb-40ea-aeb7-90e4ad30598c
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: a3cbffb7-c1d1-47c2-bcfd-70f1e2d81ac9
exl-id: 89286798-e02a-45d8-a91d-c50ef4dc7f25
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 28%

---

# Verhindern von CSRF-Angriffen {#preventing-csrf-attacks}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Funktionsweise von CSRF-Angriffen {#how-csrf-attacks-work}

Cross-Site Request Forgery (CSRF) ist eine Website-Schwachstelle, bei der der Browser eines gültigen Benutzers verwendet wird, um eine böswillige Anfrage zu senden, möglicherweise über einen iFrame. Da der Browser Cookies auf Domain-Basis sendet, wenn der Benutzer derzeit bei einer Anwendung angemeldet ist, sind die Daten des Benutzers möglicherweise gefährdet.

Angenommen, Sie sind in einem Browser bei Administration Console angemeldet. Sie erhalten eine E-Mail-Nachricht mit einem Link. Klicken Sie auf den Link, um eine neue Registerkarte in Ihrem Browser zu öffnen. Die Seite, die Sie geöffnet haben, enthält einen ausgeblendeten iFrame, der mithilfe des Cookies aus Ihrer authentifizierten AEM Forms-Sitzung eine böswillige Anforderung an den Formularserver sendet. Da User Management ein gültiges Cookie erhält, wird die Anfrage übergeben.

## CSRF-bezogene Begriffe {#csrf-related-terms}

**Referer:** Die Adresse der Quellseite, von der eine Anfrage kommt. Beispielsweise enthält eine Webseite auf site1.com einen Link zu site2.com. Durch Klicken auf den Link wird eine Anfrage an site2.com gesendet. Der Verweis auf diese Anfrage ist site1.com , da die Anfrage von einer Seite stammt, deren Quelle Site1.com ist.

**Whitelist-URIs:** URIs identifizieren Ressourcen auf dem Formularserver, die angefordert werden, z. B. /adminui oder /contentspace. Einige Ressourcen ermöglichen einer Anforderung möglicherweise, von einer externen Site aus auf die Anwendung zuzugreifen. Diese Ressourcen gelten als auf die Zulassungsliste gesetzte URIs. Der Formular-Server führt keine Referenzüberprüfungen für auf die Zulassungsliste gesetzten URIs durch.

**Null-Referer:** Wenn Sie ein neues Browserfenster oder eine neue Registerkarte öffnen, dann eine Adresse eingeben und die Eingabetaste drücken, ist die Referenz null. Die Anfrage ist völlig neu und stammt nicht von einer übergeordneten Webseite. Daher gibt es keine Referenz für die Anfrage. Der Formularserver kann eine Null-Referenz von erhalten:

* Anforderungen an SOAP- oder REST-Endpunkte von Acrobat
* alle Desktop-Clients, die HTTP-Anforderungen an einen SOAP- oder REST-Endpunkt AEM Formulars senden
* wenn ein neues Browser-Fenster geöffnet und die URL für die Anmeldeseite AEM Forms-Webanwendung eingegeben wird

Lassen Sie eine Null-Referenz auf SOAP- und REST-Endpunkten zu. Lassen Sie außerdem eine Null-Referenz auf allen URI-Anmeldeseiten wie /adminui und /contentspace und den entsprechenden zugeordneten Ressourcen zu. Beispielsweise ist das zugeordnete Servlet für /contentspace /contentspace/faces/jsp/login.jsp, was eine Null-Referrer-Ausnahme sein sollte. Diese Ausnahme ist nur erforderlich, wenn Sie die Filterung von GET für Ihre Webanwendung aktivieren. Ihre Anwendungen können angeben, ob Null-Referenzen zulässig sind. Siehe „Schutz vor Cross-Site Request Forgery-Angriffen“ in [Härtung und Sicherheit für AEM Forms](https://help.adobe.com/de_DE/livecycle/11.0/HardeningSecurity/index.html).

**Erlaubte Referer-Ausnahme:** Erlaubte Referer-Ausnahme ist eine Unterliste der Liste der erlaubten Referer, von denen Anfragen blockiert werden. Zulässige Referenzauausnahmen beziehen sich insbesondere auf eine Webanwendung. Wenn eine Teilmenge der erlaubten Referer eine bestimmte Webanwendung nicht aufrufen darf, können Sie die Referer über Erlaubte Referer-Ausnahmen auf eine Blockierungsliste setzen. Zulässige Referenzausnahmen werden in der Datei „web.xml“ für Ihre Anwendung angegeben. (Siehe den Abschnitt zum Schutz vor Cross-Site Request Forgery-Angriffen in Härtung und Sicherheit für AEM Forms on Hilfe und Tutorials.)

## Funktionsweise von zulässigen Referenzen {#how-allowed-referers-work}

AEM Formulare bietet Referrer-Filter, die CSRF-Angriffe verhindern können. So funktioniert die Filterung von Referenzen:

1. Der Formular-Server prüft die für den Aufruf verwendete HTTP-Methode:

   * Wenn es sich um eine POST handelt, führt der Formularserver die Überprüfung des Referrer-Headers durch.
   * Wenn es sich um eine GET handelt, umgeht der Formularserver die Referrer-Prüfung, es sei denn, CSRF_CHECK_GETS ist auf &quot;true&quot;festgelegt. In diesem Fall wird der Referrer-Header überprüft. CSRF_CHECK_GETS ist in der Datei web.xml für Ihre Anwendung festgelegt. (Siehe &quot;Schutz vor Cross-Site Request Forgery-Angriffen&quot; in [Handbuch zur Härtung und Sicherheit](https://help.adobe.com/de_DE/livecycle/11.0/HardeningSecurity/index.html).

1. Der Formular-Server prüft, ob die angeforderten URI auf die Zulassungsliste gesetzt ist:

   * Wenn der URI auf die Zulassungsliste gesetzt ist, übergibt der Server die Anforderung.
   * Wenn die angeforderte URI nicht auf die Zulassungsliste gesetzt ist, ruft der Server die Referenz der Anforderung ab.

1. Wenn die Anforderung einen Verweis enthält, prüft der Server, ob es sich um einen zulässigen Referrer handelt. Wenn dies zulässig ist, sucht der Server nach einer Referrer-Ausnahme:

   * Wenn es sich um eine Ausnahme handelt, wird die Anfrage blockiert.
   * Wenn es sich nicht um eine Ausnahme handelt, wird die Anforderung übergeben.

1. Wenn in der Anfrage kein Verweis enthalten ist, prüft der Server, ob eine Null-Referenz zulässig ist.

   * Wenn eine Null-Referenz zulässig ist, wird die Anforderung übergeben.
   * Wenn eine Null-Referenz nicht zulässig ist, prüft der Server, ob der angeforderte URI eine Ausnahme für Null-Referrer ist, und verarbeitet die Anfrage entsprechend.

## Zulässige Referenzen konfigurieren {#configure-allowed-referers}

Wenn Sie Configuration Manager ausführen, werden der Standardhost und die IP-Adresse oder der Formularserver der Liste &quot;Zulässige Referrer&quot;hinzugefügt. Sie können diese Liste in Administration Console bearbeiten.

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Konfiguration&quot;> &quot;URLs für zulässige Referenzen konfigurieren&quot;. Die Liste &quot;Zulässige Referrer&quot;wird unten auf der Seite angezeigt.
1. Hinzufügen einer zulässigen Referenz:

   * Geben Sie einen Hostnamen oder eine IP-Adresse in das Feld &quot;Zulässige Referenzen&quot;ein. Um mehr als einen zulässigen Referrer gleichzeitig hinzuzufügen, geben Sie jeden Hostnamen oder jede IP-Adresse in eine neue Zeile ein.
   * Geben Sie in den Feldern HTTP-Anschluss und HTTPS-Anschluss an, welche Ports für HTTP, HTTPS oder beide zulässig sein sollen. Wenn Sie diese Felder leer lassen, werden die Standardanschlüsse (Port 80 für HTTP und Port 443 für HTTPS) verwendet. Wenn Sie den Wert `0` (null) in die Felder eingeben, werden alle Anschlüsse auf diesem Server aktiviert. Sie können auch eine bestimmte Portnummer eingeben, um nur diesen Port zu aktivieren.
   * Klicken Sie auf Hinzufügen.

1. Um den Eintrag aus der Liste &quot;Zulässige Referrer&quot;zu entfernen, wählen Sie das Element aus der Liste aus und klicken Sie auf &quot;Löschen&quot;.

   Wenn die Liste für zulässige Referenzen leer ist, funktioniert die CSRF-Funktion nicht mehr und das System wird unsicher.

1. Nachdem Sie die Liste für zulässige Referenzen geändert haben, starten Sie den AEM forms-Server neu.
