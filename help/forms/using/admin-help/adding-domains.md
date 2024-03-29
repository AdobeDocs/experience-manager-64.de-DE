---
title: Hinzufügen von Domains
seo-title: Adding domains
description: Erfahren Sie, wie Sie ein Unternehmen, eine lokale oder Hybrid-Domain mithilfe der Einstellungen in Domain Management hinzufügen und allgmeine Gedanken zu Domain-Namen und Ids.
seo-description: Learn how to add an enterprise, local, or hybrid domain using Domain Management settings and general considerations for domain names and IDs.
uuid: 3ae1e5d4-ea5b-4e0b-be97-3957c3702d5f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d4004ffe-c981-487d-b803-dc4492ae5998
exl-id: f2bafa0c-072c-4599-92bc-4eaafece5b4f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '958'
ht-degree: 62%

---

# Hinzufügen von Domains {#adding-domains}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Hinzufügen einer Unternehmens-Domain {#add-an-enterprise-domain}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.
1. Klicken Sie auf „Neue Unternehmens-Domain“.
1. Geben Sie in das Feld „ID“ einen eindeutigen Bezeichner für die Domain und in das Feld „Name“ einen beschreibenden Namen für die Domain ein. (Siehe [Wichtige Einstellungen für Domain-Namen und IDs](adding-domains.md#important-considerations-for-domain-names-and-ids).)
1. Geben Sie an, ob die Kontosperrung aktiviert werden soll. (Siehe [Einstellungen für die Kontosperrung konfigurieren](/help/forms/using/admin-help/configure-account-locking-settings.md#configure-account-locking-settings). Standardmäßig ist die Option Kontosperrung aktivieren ausgewählt.
1. Klicken Sie auf Authentifizierung hinzufügen und wählen Sie in der Liste Authentifizierungsanbieter je nach Authentifizierungsmechanismus, den Ihr Unternehmen verwendet, einen Anbieter aus. Mögliche Werte sind LDAP, Kerberos, SAML oder ein benutzerdefinierter Authentifizierungsanbieter.

   Wenn Sie LDAP auswählen, können Sie den in Ihrer Ordnerkonfiguration angegebenen LDAP-Server verwenden oder einen anderen LDAP-Server auswählen, der für die Authentifizierung verwendet werden soll. Wenn Sie einen anderen Server auswählen, müssen Ihre Benutzer auf beiden LDAP-Servern vorhanden sein.

1. Geben Sie zusätzliche Informationen an, die auf der Seite erforderlich sind. (Siehe [Authentifizierungseinstellungen](/help/forms/using/admin-help/configuring-authentication-providers.md#authentication-settings).
1. Fügen Sie ein Verzeichnis oder eine benutzerdefinierte Service Provider Interface (SPI) hinzu. (Siehe [Ordner oder benutzerdefinierte SPIs hinzufügen](/help/forms/using/admin-help/configuring-directories.md#adding-directories-or-custom-spis).
1. Klicken Sie auf Fertigstellen und dann auf OK.

Nach dem Erstellen einer Unternehmens-Domain müssen Sie den Ordner manuell synchronisieren oder einen Trigger für die Synchronisierung erstellen, bevor User Management den Ordner verwenden kann. Anschließend können Sie einen Zeitplan für die Ordnersynchronisierung einrichten und bei Bedarf eine manuelle Synchronisierung durchführen. (Siehe [Ordner synchronisieren](/help/forms/using/admin-help/synchronizing-directories.md#synchronizing-directories).

## Hinzufügen einer lokalen Domain {#add-a-local-domain}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.
1. Klicken Sie auf „Neue lokale Domain“.
1. Geben Sie in das Feld ID einen eindeutigen Bezeichner für die Domain ein und in das Feld Name einen beschreibenden Namen für die Domän. (Siehe [Wichtige Einstellungen für Domain-Namen und IDs](adding-domains.md#important-considerations-for-domain-names-and-ids).)
1. Geben Sie an, ob die Kontosperrung aktiviert werden soll, und klicken Sie auf &quot;OK&quot;. (Siehe [Einstellungen für die Kontosperrung konfigurieren](/help/forms/using/admin-help/configure-account-locking-settings.md#configure-account-locking-settings). Standardmäßig ist die Option Kontosperrung aktivieren ausgewählt.

## Hybrid-Domain hinzufügen {#add-a-hybrid-domain}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.
1. Klicken Sie auf „Neue Hybrid-Domain“.
1. Geben Sie in das Feld ID einen eindeutigen Bezeichner für die Domain ein und in das Feld Name einen beschreibenden Namen für die Domain. (Siehe [Wichtige Einstellungen für Domain-Namen und IDs](adding-domains.md#important-considerations-for-domain-names-and-ids).)
1. Klicken Sie auf Authentifizierung hinzufügen und wählen Sie in der Liste Authentifizierungsanbieter je nach Authentifizierungsmechanismus, den Ihr Unternehmen verwendet, einen Anbieter aus. Mögliche Werte sind LDAP, Kerberos, SAML oder ein benutzerdefinierter Authentifizierungsanbieter.
1. Geben Sie zusätzliche Informationen an, die auf der Seite erforderlich sind. (Siehe [Authentifizierungseinstellungen](/help/forms/using/admin-help/configuring-authentication-providers.md#authentication-settings).
1. Klicken Sie auf OK und dann erneut auf OK .

## Wichtige Einstellungen für Domain-Namen und IDs {#important-considerations-for-domain-names-and-ids}

Beachten Sie beim Auswählen eines Domain-Namens und einer ID die folgenden Einstellungen:

### Allgemeine Überlegungen {#general-considerations}

* Bei Nutzung anderer Datenbankanbieter als DB2 darf die Domain-ID maximal 50 Byte umfassen. Wenn Sie Einzelbyte-ASCII-Zeichen verwenden, beträgt die Beschränkung 50 Zeichen. Enthält die Domain-ID Multibyte-Zeichen, verringert sich dieser Grenzwert. Wenn Sie beispielsweise eine Domain erstellen, deren Bezeichner 3-Byte-Zeichen enthält, beträgt der Grenzwert 16 Zeichen. Das Erstellen von Domains, deren Bezeichner 4-Byte-Zeichen enthalten, ist nicht möglich. Wenn Sie eine Domain-ID erstellen, die diese Grenze überschreitet, versetzt dies AEM Forms in einen instabilen Zustand. Weitere Informationen zum Wiederherstellen des Systems aus diesem instabilen Zustand finden Sie unter [Entfernen einer Domain, die erweiterte Zeichen oder Multibyte-Zeichen enthält](adding-domains.md#remove-a-domain-that-contains-extended-or-multi-byte-characters) auf dieser Seite.
* Die Anzahl sowohl von Unternehmens- als auch von lokalen Domains, die in AEM Forms erstellt werden können, ist von der Länge jeder einzelnen Domain-ID abhängig. Wenn Sie eine Unternehmens- oder Hybrid-Domain hinzufügen, aktualisiert User Management die Zeichenfolge „configInstance“ im „AuthProviders“-Knoten der AEM Forms-Konfigurationsdatei (config.xml). Die Zeichenfolge „configInstance“ enthält eine durch Doppelpunkt getrennte Liste der absoluten Pfade aller Domains, die dem Autorisierungsanbieter zugeordnet sind. Diese Zeichenfolge ist auf 8192 Zeichen begrenzt. Wenn diese Grenze erreicht ist, können Sie keine zusätzlichen Domains erstellen.

### Überlegungen zur Verwendung von DB2 {#considerations-when-using-db2}

Bei Verwendung von DB2 als AEM Forms-Datenbank hängt die maximal zulässige Länge der Domain-ID von dem verwendeten Zeichentyp ab:

* 100 Einzelbyte-Zeichen (ASCII) (z. B. Zeichen, die in englischer, französischer oder deutscher Sprache verwendet werden)
* 50 Doppelbyte-Zeichen (z. B. Zeichen, die in chinesischer, japanischer oder koreanischer Sprache verwendet werden)
* 25 Vierbyte-Zeichen (z. B. in traditionellem Chinesisch verwendete Zeichen)

### Überlegungen zur Verwendung von MySQL {#considerations-when-using-mysql}

Bei der Verwendung von MySQL als AEM Forms-Datenbank gelten die folgenden Einschränkungen:

* Für die Domain-ID und den Domain-Namen dürfen nur Einzelbyte-Zeichen (ASCII) verwendet werden. Wenn Sie erweiterte ASCII-Zeichen verwenden, befindet sich AEM Forms in einem instabilen Zustand und erzeugt möglicherweise eine Ausnahme, wenn Sie versuchen, die Domain zu löschen. Weitere Informationen zum Wiederherstellen des Systems aus diesem instabilen Zustand finden Sie unter [Entfernen einer Domain, die erweiterte Zeichen oder Multibyte-Zeichen enthält](adding-domains.md#remove-a-domain-that-contains-extended-or-multi-byte-characters) auf dieser Seite.
* Sie können nicht zwei Domains mit demselben Namen, aber unterschiedlicher Groß-/Kleinschreibung erstellen. Der Versuch, die Domain *Adobe* zu erstellen, wenn die Domain *adobe* bereits vorhanden ist, führt zu einer Fehlermeldung.
* User Management kann nicht zwischen zwei Domain-Namen unterscheiden, die sich nur in der Verwendung erweiterter Zeichen unterscheiden. Wenn Sie beispielsweise eine Domäne mit dem Namen *abcde* und einer Domäne mit dem Namen *âbcdè *, werden sie als identisch betrachtet.

### Eine Domain, die erweiterte Zeichen oder Multibyte-Zeichen enthält, entfernen {#remove-a-domain-that-contains-extended-or-multi-byte-characters}

1. Exportieren Sie die Konfigurationsdatei, wie unter [Konfigurationsdatei importieren und exportieren](/help/forms/using/admin-help/importing-exporting-configuration-file.md#importing-and-exporting-the-configuration-file).
1. Öffnen Sie die Konfigurationsdatei und suchen Sie unter dem Knoten „Domains“ den Knoten, dessen Namensattribut mit dem Namen der Domain, die mit erweiterten Zeichen oder Multibyte-Zeichen erstellt wurde, übereinstimmt. Löschen Sie den gesamten Knoten für diese Domain.
1. Suchen Sie in Ihrer Datenbank die Domain in der Tabelle „edcprincipaldomainentity“:

   * Wählen Sie `*` von edcprincipaldomainentity.
   * Suchen Sie den Domain-Namen, der erweiterte Zeichen oder Multibyte-Zeichen enthält, und legen Sie den Status auf „OBSOLETE“ fest.

1. Importieren Sie die aktualisierte Konfigurationsdatei, wie unter [Konfigurationsdatei importieren und exportieren](/help/forms/using/admin-help/importing-exporting-configuration-file.md#importing-and-exporting-the-configuration-file).
