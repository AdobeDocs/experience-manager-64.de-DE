---
title: Konfigurieren einer zertifikatbasierten Authentifizierung
seo-title: Configuring certificate-based authentication
description: Importieren Sie ein Zertifikat der Zertifizierungsstelle (Certificate Authority, CA) in den Trust Store und erstellen Sie eine Zertifikatzuordnung für die zertifikatbasierte Authentifizierung.
seo-description: Import a Certificate Authority (CA) certificate into the Trust Store and create a certificate mapping for certificate-based authentication.
uuid: 9802a969-6d29-4b80-a4ed-06eb6e66e046
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d958ae65-3008-4d68-9e11-4346e149827f
exl-id: 88932b5b-2acc-4f21-8ce3-b819a990ad30
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 12%

---

# Konfigurieren einer zertifikatbasierten Authentifizierung {#configuring-certificate-based-authentication}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die Benutzerverwaltung führt die Authentifizierung in der Regel mithilfe eines Benutzernamens und Kennworts durch. User Management unterstützt auch die zertifikatbasierte Authentifizierung, mit der Sie Benutzer über Acrobat authentifizieren oder Benutzer programmgesteuert authentifizieren können. Weitere Informationen zum programmgesteuerten Authentifizieren von Benutzern finden Sie unter [Programmieren mit AEM Formularen](https://www.adobe.com/go/learn_aemforms_programming_63_de).

Um die zertifikatbasierte Authentifizierung zu verwenden, importieren Sie ein Zertifikat der Zertifizierungsstelle (Certificate Authority, CA), dem Sie vertrauen, in den Trust Store und erstellen Sie dann eine Zertifikatzuordnung.

## CA-Zertifikat importieren {#import-the-ca-certificate}

Wählen Sie beim Importieren des Zertifikats die Optionen &quot;Trust für Zertifikatauthentifizierung&quot;und &quot;Trust für Identität&quot;sowie alle anderen erforderlichen Optionen aus. Weitere Informationen zum Importieren von Zertifikaten finden Sie unter [Zertifikate verwalten](/help/forms/using/admin-help/certificates.md#managing-certificates).

## Zertifikatzuordnung konfigurieren {#configuring-certificate-mapping}

Um die zertifikatbasierte Authentifizierung für Benutzer zu aktivieren, erstellen Sie eine Zertifikatzuordnung. Eine *Zertifikatzuordnung* definiert eine Zuordnung zwischen den Attributen eines Zertifikats und den Attributen von Benutzern in einer Domain. Sie können derselben Domain mehr als ein Zertifikat zuordnen.

Beim Testen eines Zertifikats lädt User Management die Zertifikatprüfungen hoch, um sicherzustellen, dass es die folgenden Anforderungen erfüllt:

* Das Zertifikat ist gültig.
* Der von Ihnen angegebene Aussteller kann das Zertifikat überprüfen.
* Das Zertifikat enthält das für die Zuordnung erforderliche Attribut.
* Die von Ihnen angegebene Zuordnung ordnet das Zertifikat nur einem Benutzer in der AEM Formulardatenbank zu. Sowohl aktuelle als auch veraltete (gelöschte) Benutzer werden überprüft, um festzustellen, ob sie den Zuordnungskriterien entsprechen. Daher schlägt der Zertifikattest fehl, wenn mehr als ein Benutzer, einschließlich veralteter Benutzer, den Attributwert berücksichtigt.

>[!NOTE]
>
>Sie können eine vorhandene Zertifikatzuordnung nicht bearbeiten.

**Zertifikatzuordnung hinzufügen**

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Konfiguration&quot;> &quot;Zertifikatzuordnung&quot;.
1. Klicken Sie auf &quot;Neue Zertifikatzuordnung&quot;und wählen Sie in der Liste &quot;Für Aussteller&quot;den Zertifikatalias aus, der in der Trust Store-Verwaltung konfiguriert wurde.
1. Ordnen Sie eines der Attribute des Zertifikats dem -Attribut eines Benutzers zu. Sie können beispielsweise den allgemeinen Namen des Zertifikats der Anmelde-ID des Benutzers zuordnen.

   Wenn der Inhalt des Attributs im Zertifikat sich vom Inhalt des Benutzerattributs in der User Management-Datenbank unterscheidet, können Sie einen regulären Java-Ausdruck (Regex) verwenden, der mit den beiden Attributen übereinstimmt. Wenn die allgemeinen Namen der Zertifikate beispielsweise Namen wie *Alex Pink (Authentifizierung)* und *Alex Pink (Signing)* und der allgemeine Name in der User Management-Datenbank lautet *Alex Pink* verwenden, verwenden Sie einen Regex, um den erforderlichen Teil des Zertifikatattributs zu extrahieren (in diesem Beispiel: *Alex Pink*. Der von Ihnen angegebene reguläre Ausdruck muss der Java-Regex-Spezifikation entsprechen.

   Sie können den Ausdruck transformieren, indem Sie die Reihenfolge der Gruppen im Feld &quot;Benutzerdefinierte Reihenfolge&quot;angeben. Die benutzerdefinierte Reihenfolge wird mit der Methode `java.util.regex.Matcher.replaceAll()` verwendet. Das angezeigte Verhalten entspricht dem Verhalten dieser Methode, und die Eingabezeichenfolge (die benutzerdefinierte Reihenfolge) muss entsprechend angegeben werden.

   Geben Sie zum Testen des Regex einen Wert in das Feld &quot;Testparameter&quot;ein und klicken Sie auf &quot;Testen&quot;.

   Sie können die folgenden Zeichen im Regex verwenden:

   * . (beliebiges Zeichen)
   * &amp;ast; (0 oder mehr Vorkommen)
   * () (geben Sie die Gruppe in Klammern an)
   * \ (wird verwendet, um ein Regex-Zeichen in ein reguläres Zeichen zu Escape durchzuführen)
   * $n (wird verwendet, um auf die n-te Gruppe zu verweisen)

   Beispiele für reguläre Ausdrücke:

   * So extrahieren Sie &quot;Alex Pink&quot;aus &quot;Alex Pink (Authentifizierung)&quot;

      **Regex:** (.&amp;ast;) \(Authentifizierung\)

   * So extrahieren Sie &quot;Alex Pink&quot;aus &quot;Alex (Authentifizierung) Pink&quot;

      **Regex:** (.&amp;ast;)\(Authentifizierung\) (.&amp;ast;)

   * So extrahieren Sie &quot;Pink Alex&quot;aus &quot;Alex (Authentication) Pink&quot;

      **Regex:** (.&amp;ast;)\(Authentifizierung\) (.&amp;ast;)

      Benutzerdefinierte Reihenfolge: $2 $1 (return second group, verkettet mit der ersten Gruppe, erfasst durch Leerzeichen)

   * So extrahieren Sie &quot;apink@sampleorg.com&quot;aus &quot;smtp:apink@sampleorg.com&quot;

      **Regex:** smtp:(.&amp;ast;)
   Weitere Informationen zur Verwendung regulärer Ausdrücke finden Sie unter [Java-Tutorial zu regulären Ausdrücken](https://java.sun.com/docs/books/tutorial/essential/regex/).

1. Wählen Sie im Feld „Für Domain“ die Domain des Benutzers aus.
1. Um diese Konfiguration zu testen, klicken Sie auf Durchsuchen , um ein Beispielbenutzerzertifikat hochzuladen, auf Zertifikat testen und, falls die Konfiguration korrekt ist, auf OK.

**Vorhandene Zertifikatzuordnung bearbeiten**

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Konfiguration&quot;.
1. Klicken Sie auf Zertifikatzuordnung.
1. Wählen Sie die Zertifikatzuordnung aus, um die Konfiguration zu bearbeiten und zu bearbeiten. Sie können den regulären Ausdruck und die benutzerdefinierte Reihenfolge aktualisieren.
1. Um Ihre Änderungen zu testen, klicken Sie auf &quot;Durchsuchen&quot;, um ein Beispielzertifikat hochzuladen, klicken auf &quot;Zertifikat testen&quot;und anschließend auf &quot;OK&quot;.

**Zertifikatzuordnung löschen**

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Konfiguration&quot;> &quot;Zertifikatzuordnung&quot;.
1. Aktivieren Sie das Kontrollkästchen für die zu löschende Zertifikatzuordnung und klicken Sie auf &quot;Löschen&quot;und anschließend auf &quot;OK&quot;.
