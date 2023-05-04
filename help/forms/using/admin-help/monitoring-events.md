---
title: Überwachen von Ereignissen
seo-title: Monitoring events
description: Wenn die Prüffunktion aktiviert ist, können Sie mit Document Security bestimmte Ereignistypen überwachen. Sie können die Ereignisliste mithilfe von Document Security einfach durchsuchen und sortieren.
seo-description: When the auditing capability is enabled, document security enables you to monitor certain types of events. You can easily search and sort the events list using the document security.
uuid: 22add6ff-536d-4cb9-8eac-b72cad5c3ecf
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 379957bf-0634-4182-b269-1b010da4c90f
feature: Document Security
exl-id: 0c4a846f-4e31-435b-a6f6-d0b7c4cd1259
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '994'
ht-degree: 34%

---

# Überwachen von Ereignissen {#monitoring-events}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Wenn die Prüffunktion aktiviert ist, können Sie mit Document Security bestimmte Ereignistypen überwachen. Die Ereignisse, die Sie sehen können, hängen von Ihrer Rolle ab:

**Benutzer:** Sind in der Lage, geprüfte Ereignisse für ihre richtliniengeschützten Dokumente sowie andere geschützte Dokumente, die sie erhalten und verwenden, anzuzeigen.

**Richtliniensatzkoordinatoren:** Sind in der Lage, geprüfte Ereignisse, einschließlich Dokument- und Richtlinienereignissen, für Dokumente anzuzeigen, die von Richtlinien in ihren Richtliniensätzen geschützt werden.

**Administratoren:** Sind in der Lage, geprüfte Ereignisse im Zusammenhang mit allen richtliniengeschützten Dokumenten und Benutzern anzuzeigen. Administratoren können auch andere Ereignistypen verfolgen, einschließlich Benutzer-, Dokument-, Richtlinien- und Systemereignissen.

>[!NOTE]
>
>Ereignisse, die für eine Kopie eines richtliniengeschützten Dokuments ausgeführt werden, werden auch als Ereignisse im ursprünglich geschützten Dokument verfolgt.

(Siehe [Ereignisprüfungsoptionen](/help/forms/using/admin-help/configuring-client-server-options.md#event-auditing-options).

Ein fehlgeschlagenes Ereignis wird aufgezeichnet, wenn ein nicht autorisierter Benutzer versucht, ein Dokument anzuzeigen oder versucht, sich mit einem falschen Benutzernamen oder Kennwort anzumelden.

>[!NOTE]
>
>Fehlgeschlagene anonyme Zugriffsereignisse für Dokumente können protokolliert werden, wenn eine Richtlinie so bearbeitet wird, dass der anonyme Zugriff entfernt wird. Wenn ein autorisierter Empfänger versucht, auf ein Dokument zuzugreifen, das von der bearbeiteten Richtlinie geschützt wird, wird der anonyme Zugriff zwar weiterhin versucht, schlägt jedoch fehl.

Wenn eine Richtlinie den anonymen Benutzerzugriff zulässt, der Administrator jedoch später den anonymen Zugriff für Document Security deaktiviert, schlägt der anonyme Zugriff für mit der Richtlinie geschützte Dokumente fehl und das Ereignis wird nicht protokolliert.

## Ereignisprüfung aktivieren {#enable-event-auditing}

Diese Einrichtungsanforderungen müssen erfüllt sein, damit die Ereignisprüfung stattfindet:

* Das System oder der Administrator muss die Prüffunktion für den Server aktivieren.

   (Siehe [Ereignisprüfungs- und Datenschutzeinstellungen konfigurieren](/help/forms/using/admin-help/configuring-client-server-options.md#configuring-event-auditing-and-privacy-settings).

* Für die Richtlinie, die Sie zum Schutz des Dokuments verwenden, muss die Prüfung aktiviert sein. (Siehe [Richtlinien erstellen und bearbeiten](/help/forms/using/admin-help/creating-policies.md#creating-and-editing-policies).

## Suchen nach einem Ereignis {#search-for-an-event}

Sie können die Ereignisliste durchsuchen und detailliertere Beschreibungen zu Ereignissen anzeigen. Zu den detaillierten Beschreibungen gehören Informationen wie die Ereignis-ID, Beschreibung, IP-Adresse, Organisation, betroffene Benutzer, Datum und Uhrzeit des Ereignisses, verweigerte Aktivitäten und Offline-Ereignisse (wenn Benutzer versuchen, ein Dokument zu verwenden, wenn sie nicht mit Document Security verbunden sind).

Sie können auf der Seite &quot;Ereignisse&quot;nach Ereignissen suchen, indem Sie eine Kombination aus Ereignissuchkriterien und den Datumsangaben der Ereignisse verwenden. Die Ereignisse, nach denen Sie suchen können, hängen von Ihrer Rolle ab:

**Benutzer:** Sind in der Lage, geprüfte Ereignisse für ihre richtliniengeschützten Dokumente sowie andere geschützte Dokumente, die sie erhalten und verwenden, anzuzeigen. Die folgenden Suchoptionen sind verfügbar:

**Ereignisse, die mich 
betreffen:** Benutzer können nach Ereignissen für die richtliniengeschützten Dokumente suchen, die sie erstellt oder empfangen haben. Wenn ein Benutzer beispielsweise ein Dokument öffnet, anzeigt oder druckt, das von einer anderen Person geschützt wurde, werden dem Benutzer diese Ereignisse nur für dieses Dokument angezeigt.

**Ereignisse, die meine Dokumente betreffen:** Benutzer können alle Ereignisse finden, die im Zusammenhang mit ihren eigenen richtliniengeschützten Dokumenten stehen. Der Benutzer sieht die Ereignisse, die von allen Personen generiert wurden, die Umgang mit seinen Dokumenten hatten.

**Richtliniensatzkoordinatoren:** Sind in der Lage, geprüfte Ereignisse, einschließlich Dokument- und Richtlinienereignissen, für Dokumente anzuzeigen, die von Richtlinien in ihren Richtliniensätzen geschützt werden. Die folgenden Optionen stehen zur Auswahl:  

**Dokumentereignisse,
wenn ich Richtliniensatzkoordinator bin:** Richtliniensatzkoordinatoren mit der Berechtigung zum Anzeigen von Ereignissen können Ereignisse finden, die Dokumente betreffen, die von Richtlinien in ihren Richtliniensätzen geschützt werden.

**Richtlinienereignisse, wenn ich Richtliniensatzkoordinator bin:** Richtliniensatzkoordinatoren mit der Berechtigung zum Anzeigen von Ereignissen können Ereignisse finden, die mit Richtlinien in ihren Richtliniensätzen in Zusammenhang stehen.

**Administratoren:** Sind in der Lage, geprüfte Ereignisse im Zusammenhang mit allen richtliniengeschützten Dokumenten und Benutzern anzuzeigen. Administratoren können auch andere Typen verfolgen. Außerdem können Administratoren die Ereignissuche je nach Benutzertyp weiter unterteilen:

**Bekannte Benutzer:** Benutzer, die in den Quellordnern gefunden werden können oder als externe Benutzer registriert sind.

**Anonyme Benutzer:** Benutzer, die auf ein Dokument zugreifen, das durch eine Richtlinie geschützt ist, die den anonymen Zugriff erlaubt.

**Systembenutzer:** Vom Server ausgelöste Ereignisse, z. B. eine Ordnersynchronisierung.

1. Klicken Sie auf der Document Security-Seite auf Ereignisse.
1. Wählen Sie in der Liste &quot;Suchen&quot;die Suchkriterien aus, die Sie verwenden möchten. Je nach Auswahl in der Liste &quot;Suchen&quot;wird eine zweite Liste mit zusätzlichen Suchkriterien angezeigt. Falls zutreffend, geben Sie die Suchkriterien in das Textfeld ein.

   Weitere Informationen zu bestimmten Ereignistypen finden Sie unter [Ereignisprüfungsoptionen](/help/forms/using/admin-help/configuring-client-server-options.md#event-auditing-options).

1. Wählen Sie in der Liste Benutzer den Benutzertyp aus, der das Ereignis ausgeführt hat:

   * Wenn Sie &quot;Bekannter Benutzer&quot;auswählen, wird ein zweites Suchfeld angezeigt, in das Sie den Benutzernamen oder die E-Mail-Adresse des Benutzers eingeben müssen.
   * Wenn Sie diese Angaben nicht kennen, klicken Sie auf das Adressbuchsymbol, um den Benutzer anhand des Benutzernamens oder der E-Mail-Adresse zu suchen.

1. Wählen Sie in der Liste &quot;Datum&quot;eine Datumsbereichsoption aus. Wenn Sie &quot;Benutzerdefinierte Datumswerte&quot;auswählen, werden Felder angezeigt, in die Sie das Datum im Format JJJ/MM/TT eingeben. Alternativ können Sie die Datumsauswahl verwenden, um den Datumsbereich anzugeben:

   * Klicken Sie auf den Kalender , um die Datumsauswahl zu öffnen.
   * Verwenden Sie die Pfeile, um ein Jahr und einen Monat zu finden.
   * Klicken Sie auf einen Tag des Monats im Kalender.
   * Klicken Sie auf OK , um die Datumsauswahl zu schließen.

1. Wählen Sie in der Liste &quot;Anzeigen&quot;die Anzahl der Suchergebnisse aus, die pro Seite angezeigt werden sollen.
1. Klicken Sie auf „Suchen“.

   Fehlgeschlagene Ereignisse werden in der Liste mit dem Symbol &quot;Verweigert&quot;markiert.

1. Um Details zu einem Ereignis anzuzeigen, klicken Sie auf die Beschreibung des Ereignisses in der Liste.

## Sortieren der Ereignisliste {#sort-the-event-list}

Sie können die Ereignisliste nach Spaltenüberschrift sortieren, um Ereignisse leichter zu finden. Dreieckssymbole neben der Spaltenüberschrift geben an, welche Spalte derzeit zum Sortieren verwendet wird. Ein nach oben zeigendes Dreieck gibt eine aufsteigende Reihenfolge an, während ein nach unten zeigendes Dreieck eine absteigende Reihenfolge angibt.

1. Klicken Sie auf die entsprechende Spaltenüberschrift.
1. Um die Sortierreihenfolge zu ändern, klicken Sie erneut auf die Spaltenüberschrift.
