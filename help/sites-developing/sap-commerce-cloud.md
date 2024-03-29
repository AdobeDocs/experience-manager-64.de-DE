---
title: Entwicklung mit SAP Commerce Cloud
seo-title: Developing with SAP Commerce Cloud
description: Das Integrations-Framework SAP Commerce Cloud enthält eine Integrationsebene mit einer API
seo-description: The SAP Commerce Cloud integration framework includes an integration layer with an API
uuid: a780dd17-027a-4a61-af8f-3e2f600524c7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: platform
discoiquuid: 96dc0c1a-b21d-480a-addf-c3d0348bd3ad
exl-id: fa5b9b61-7dba-42e0-8fbd-4a96617569d8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2346'
ht-degree: 46%

---

# Entwickeln mit SAP Commerce Cloud{#developing-with-sap-commerce-cloud}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!NOTE]
>
>Das eCommerce-Framework kann mit jeder eCommerce-Lösung verwendet werden. Bestimmte hier behandelte Aspekte und Beispiele beziehen sich auf die [Hybris](https://www.hybris.com/)-Lösung.

Das Integrations-Framework enthält eine Integrationsebene mit einer API. Dies ermöglicht Ihnen Folgendes:

* ein eCommerce-System einbinden und Produktdaten in AEM abrufen
* Erstellen AEM Komponenten für Commerce-Funktionen unabhängig von der jeweiligen eCommerce-Engine

![chlimage_1-11](assets/chlimage_1-11.png)

>[!NOTE]
>
>[API-Dokumentation](/help/sites-developing/ecommerce.md#api-documentation) ist ebenfalls verfügbar.

Eine Reihe vorkonfigurierter AEM-Komponenten wird zur Verwendung der Integrationsebene bereitgestellt. Derzeit sind dies:

* eine Produktanzeigekomponente
* Warenkorb
* Auschecken

Für die Suche wird ein Integrations-Hook bereitgestellt, mit dem Sie die AEM, die Suche nach dem E-Commerce-System, eine Suche nach Drittanbietern oder eine Kombination daraus verwenden können.

## Auswahl der eCommerce-Engine {#ecommerce-engine-selection}

Das eCommerce-Framework kann mit einer beliebigen eCommerce-Lösung verwendet werden, allerdings muss die verwendete Engine von AEM identifizierbar sein:

* eCommerce-Engines sind OSGi-Services, die die `CommerceService`-Schnittstelle unterstützen.

   * Engines können anhand einer `commerceProvider`-Service-Eigenschaft identifiziert werden.

* AEM unterstützt `Resource.adaptTo()` für `CommerceService` und `Product`.

   * Die `adaptTo`-Implementierung sucht nach einer `cq:commerceProvider`-Eigenschaft in der Hierarchie der Ressource:

      * Wenn der Wert gefunden wird, wird er zum Filtern der Commerce-Service-Suche verwendet.
      * Wenn nicht gefunden, wird der Commerce-Dienst mit dem höchsten Rang verwendet.
   * Ein `cq:Commerce`-Mixin wird verwendet, um `cq:commerceProvider` zu stark typisierten Ressourcen hinzuzufügen.


* Die `cq:commerceProvider`-Eigenschaft wird auch als Verweis auf die geeignete Commerce-Factory-Definition verwendet.

   * Eine `cq:commerceProvider`-Eigenschaft mit dem Wert `hybris` korreliert beispielsweise mit der OSGi-Konfiguration für **Day CQ Commerce Factory for Hybris** (com.adobe.cq.commerce.hybris.impl.HybrisServiceFactory), wenn der Parameter `commerceProvider` auch den Wert `hybris` aufweist.

   * In diesem Fall können weitere Eigenschaften wie **Catalog version** konfiguriert werden (falls zutreffend und verfügbar).

Siehe folgendes Beispiel:

| `cq:commerceProvider = geometrixx` | In einer AEM-Standardinstallation ist eine bestimmte Implementierung erforderlich; Beispiel: das geometrixx-Beispiel, das minimale Erweiterungen der generischen API enthält |
|---|---|
| `cq:commerceProvider = hybris` | Hybris-Implementierung |

### Beispiel {#example}

```shell
/content/store 
+ cq:commerceProvider = hybris 
  + mens 
    + polo-shirt-1 
    + polo-shirt-2 
    + employee 
+ cq:commerceProvider = jcr 
  + adobe-logo-shirt 
    + cq:commerceType = product 
    + price = 12.50 
  + adobe-logo-shirt_S 
    + cq:commerceType = variant 
    + size = S 
  + adobe-logo-shirt_XL 
    + cq:commerceType = variant 
    + size = XL 
    + price = 14.50
```

>[!NOTE]
>
>Mithilfe der CRXDE Lite können Sie sehen, wie dies in der Produktkomponente für die Hybris-Implementierung gehandhabt wird:
>
>`/apps/geometrixx-outdoors/components/hybris/product/product.jsp`

### Entwickeln für Hybris 4 {#developing-for-hybris}

Die Hybris-Erweiterung des eCommerce-Integrations-Frameworks wurde aktualisiert und unterstützt jetzt Hybris 5, wobei die Rückwärtskompatibilität mit Hybris 4 ebenfalls gewährleistet bleibt.

Die Standardeinstellungen im Code sind auf Hybris 5 abgestimmt.

Um für Hybris 4 zu entwickeln, ist Folgendes erforderlich:

* Fügen Sie beim Aufrufen von Maven das folgende Befehlszeilenargument zum Befehl hinzu:

   `-P hybris4`

   Sie lädt die vorkonfigurierte Hybris 4-Distribution herunter und bettet sie in das Bundle ein:

   ```
   cq-commerce-hybris-server
   ```

* Nehmen Sie im OSGi-Konfigurations-Manager folgende Einstellungen vor:

   * Deaktivieren Sie die Hybris 5-Unterstützung für den Default Response Parser-Service.
   * Stellen Sie sicher, dass der Hybris Basic Authentication Handler-Dienst einen niedrigeren Dienstrang als der Hybris OAuth Handler-Dienst aufweist.

### Session-Handling {#session-handling}

Hybris verwendet eine Benutzersitzung, um Informationen wie den Warenkorb des Kunden zu speichern. Die Sitzungs-ID wird von Hybris in einem `JSESSIONID`-Cookie zurückgegeben, das bei nachfolgenden Anfragen an Hybris gesendet werden muss. Um zu vermeiden, die Sitzungs-ID im Repository zu speichern, ist sie in einem anderen Cookie kodiert, das im Browser des Käufers gespeichert ist. Die folgenden Schritte werden ausgeführt:

* Bei der ersten Anfrage wird kein Cookie für die Anfrage des Käufers gesetzt. , sodass eine Anfrage an die Hybris-Instanz gesendet wird, um eine Sitzung zu erstellen.
* Die Sitzungs-Cookies werden aus der Antwort extrahiert, als Code in ein neues Cookie (z. B. `hybris-session-rest`) eingebettet und in der Antwort an den Erstkäufer festgelegt. Die Kodierung in einem neuen Cookie ist erforderlich, da das ursprüngliche Cookie nur für einen bestimmten Pfad gültig ist und ansonsten in nachfolgenden Anfragen nicht vom Browser zurückgesendet wird. Die Pfadinformationen müssen auch dem -Wert des Cookies hinzugefügt werden.
* Bei nachfolgenden Anfragen wird das Cookie aus den `hybris-session-<*xxx*>`-Cookies dekodiert und auf den HTTP-Client festgelegt, der zum Anfordern der Daten von Hybris verwendet wird.

>[!NOTE]
>
>Eine neue anonyme Sitzung wird erstellt, wenn die ursprüngliche Sitzung nicht mehr gültig ist.

#### CommerceSession {#commercesession}

* Diese Sitzung „besitzt“ den **Warenkorb**.

   * Sie führt Hinzufügen/Entfernen-Aktionen aus.
   * Führt die verschiedenen Berechnungen für den Warenkorb durch;

      `commerceSession.getProductPrice(Product product)`

* Sie steuert den *Speicherort* für die **Auftragsdaten**.

   `CommerceSession.getUserContext()`

* Eigentümer des **payment** Verarbeitungsverbindung
* Sie steuert ebenfalls die Verbindung für die **Auftragserfüllung**.

### Produktsynchronisierung und -veröffentlichung {#product-synchronization-and-publishing}

Produktdaten, die in Hybris gepflegt werden, müssen in AEM verfügbar sein. Der folgende Mechanismus wurde eingeführt:

* Ein anfängliches Laden von IDs wird von hybris als Feed bereitgestellt. Dieser Feed kann aktualisiert werden.
* hybris liefert Aktualisierungsinformationen über einen Feed (AEM Umfragen).
* Wenn AEM Produktdaten verwendet, sendet es Anfragen für die aktuellen Daten an Hybris (bedingte GET-Anfrage mit dem Datum der letzten Änderung).
* Auf hybris ist es möglich, Feed-Inhalte deklarativ anzugeben.
* Die Zuordnung der Feed-Struktur zum AEM Inhaltsmodell erfolgt im Feed-Adapter auf der AEM Seite.

![chlimage_1-12](assets/chlimage_1-12.png)

* Das Importtool (b) wird für die Ersteinrichtung der Seitenstruktur in AEM für Kataloge verwendet.
* Katalogänderungen in Hybris werden über einen Feed AEM, die dann nach AEM (b) propagiert werden

   * Produkt in Bezug auf die Katalogversion hinzugefügt/gelöscht/geändert.
   * Produkt genehmigt.

* Die hybris-Erweiterung bietet ein Abruf-Importtool (&quot;hybris&quot;-Schema), das so konfiguriert werden kann, dass Änderungen in AEM in einem bestimmten Intervall importiert werden (z. B. alle 24 Stunden, in denen das Intervall in Sekunden angegeben ist):

   ```
     http://localhost:4502/content/geometrixx-outdoors/en_US/jcr:content.json
      {
      * "jcr:mixinTypes": ["cq:PollConfig"],
      * "enabled": true,
      * "source": "hybris:outdoors",
      * "jcr:primaryType": "cq:PageContent",
      * "interval": 86400
      }
   ```

* Die Katalogkonfiguration in AEM erkennt Kataloge der Versionen **Gestaffelt** und **Online**.

* Die Synchronisierung von Produkten zwischen Katalogversionen erfordert eine (De-)Aktivierung der entsprechenden AEM (a, c).

   * Hinzufügen eines Produkts zu einem **Online** -Katalogversion erfordert die Aktivierung der Produktseite.
   * Das Entfernen eines Produkts erfordert eine Deaktivierung.

* Die Aktivierung einer Seite in AEM c erfordert eine Prüfung (b) und ist nur möglich, wenn

   * sich das Produkt in der **Online**-Version eines Katalogs für Produktseiten befindet.
   * die Produkte, auf die verwiesen wird, in der **Online**-Version eines Katalogs für andere Seiten (z. B. Kampagnenseiten) verfügbar sind.

* Aktivierte Produktseiten müssen auf die **Online**-Version der Produktdaten zugreifen (d).

* Die AEM Veröffentlichungsinstanz benötigt Zugriff auf hybris , um Produkt- und personalisierte Daten abzurufen (d).

### Architektur {#architecture}

#### Architektur von Produkt und Varianten {#architecture-of-product-and-variants}

Ein einzelnes Produkt kann mehrere Varianten aufweisen. Beispielsweise kann es je nach Farbe und/oder Größe variieren. Ein Produkt muss definieren, welche Eigenschaften die Variante beeinflussen. wir diese *Variantenachsen*.

Es sind jedoch nicht alle Eigenschaften Variantenachsen. Varianten können sich auch auf andere Eigenschaften auswirken. Beispielsweise kann der Preis von der Größe abhängen. Diese Eigenschaften können nicht vom Käufer ausgewählt werden und werden daher nicht als Variantenachsen betrachtet.

Jedes Produkt bzw. jede Variante steht für eine Ressource und ist daher im Verhältnis 1:1 einem Repository-Knoten zugeordnet. Eine Folge ist, dass ein bestimmtes Produkt und/oder eine bestimmte Variante durch ihren Pfad eindeutig identifiziert werden kann.

Die Produkt-/Variantenressource enthält nicht immer die tatsächlichen Produktdaten. Es kann sich um eine Darstellung der Daten handeln, die tatsächlich in einem anderen System (z. B. hybris) gespeichert sind. Beispielsweise werden Produktbeschreibungen, Preise und dergleichen nicht in AEM gespeichert, sondern in Echtzeit aus der eCommerce-Engine abgerufen.

Jede Produktressource kann als `Product API` dargestellt werden. Die meisten Aufrufe in einer Produkt-API beziehen sich auf spezifische Varianten (obwohl Varianten gemeinsame Werte von einem Vorgänger erben können). Bei manchen Aufrufen wird jedoch ein Variantensatz (`getVariantAxes()`, `getVariants()` usw.) aufgelistet.

>[!NOTE]
>
>Eine Variantenachse wird letztendlich durch das bestimmt, was von `Product.getVariantAxes()` zurückgegeben wird:
>
>* hybris definiert es für die Hybris-Implementierung
>
>Zwar können Produkte (im Allgemeinen) viele Variantenachsen haben, vorkonfigurierte Produktkomponenten jedoch nur zwei:
>
>1. `size`
>
>1. und eine zusätzliche Variante

>
>   Diese zusätzliche Variante wird von der `variationAxis`-Eigenschaft des Produktverweises (in der Regel `color` für Geometrixx Outdoors) ausgewählt.

#### Produktverweise und Produktdaten {#product-references-and-product-data}

Allgemein:

* befinden sich Produktdaten unter `/etc`

* und Produktverweise unter `/content`.

Die Knoten für die Produktvarianten und Produktdaten müssen 1:1 zugeordnet sein.

Produktverweise müssen außerdem einen Knoten für jede präsentierte Variante haben, es müssen jedoch nicht alle Varianten präsentiert werden. Wenn ein Produkt beispielsweise die Varianten S, M und L hat, können die Produktdaten wie folgt aussehen:

```shell
etc
  commerce
    products
      shirt
        shirt-s
        shirt-m
        shirt-l
```

Im Katalog „big-and-tall“ sind möglicherweise nur diese Daten enthalten:

```shell
content
  big-and-tall
    shirt
      shirt-l
```

Es ist nicht zwingend erforderlich, Produktdaten zu verwenden. Sie können alle Produktdaten unter den Verweisen im Katalog speichern. Allerdings müssen Sie dann alle Produktdaten duplizieren, wenn Sie mehrere Kataloge verwenden möchten.

**API**

#### com.adobe.cq.commerce.api.Product interface {#com-adobe-cq-commerce-api-product-interface}

```java
public interface Product extends Adaptable {

    public String getPath();            // path to specific variation
    public String getPagePath();        // path to presentation page for all variations
    public String getSKU();             // unique ID of specific variation

    public String getTitle();           // shortcut to getProperty(TITLE)
    public String getDescription();     // shortcut to getProperty(DESCRIPTION)
    public String getImageUrl();        // shortcut to getProperty(IMAGE_URL)
    public String getThumbnailUrl();    // shortcut to getProperty(THUMBNAIL_URL)

    public <T> T getProperty(String name, Class<T> type);

    public Iterator<String> getVariantAxes();
    public boolean axisIsVariant(String axis);
    public Iterator<Product> getVariants(VariantFilter filter) throws CommerceException;
}
```

#### com.adobe.cq.commerce.api.VariantFilter  {#com-adobe-cq-commerce-api-variantfilter}

```java
/**
 * Interface for filtering variants and AxisFilter provided as common implementation
 *
 * The <code>VariantFilter</code> is used to filter variants,
 * e.g. when using {@link Product#getVariants(VariantFilter filter)}.
 */
public interface VariantFilter {
    public boolean includes(Product product);
}

/**
 * A {@link VariantFilter} for filtering variants by the given
 * axis and value. The following example returns a list of
 * variant products that have a value of <i>blue</i> on the
 * <i>color</i> axis.
 * 
 * <p>
 * <code>product.getVariants(new AxisFilter("color", "blue"));</code>
 */
public class AxisFilter implements VariantFilter {

    private String axis;
    private String value;

    public AxisFilter(String axis, String value) {
        this.axis = axis;
        this.value = value;
    }

    /**
     * {@inheritDoc}
     */
    public boolean includes(Product product) {
        ValueMap values = product.adaptTo(ValueMap.class);

        if(values != null) {
            String v = values.get(axis, String.class);

            return v != null && v == value;
        }

        return false;
    }
}
```

* **Allgemeiner Speichermechanismus**

   * Produktknoten sind nt:unstructured.
   * Ein Produktknoten kann entweder:

      * Referenz mit den an anderer Stelle gespeicherten Produktdaten:

         * Produktverweise enthalten eine `productData`-Eigenschaft, die auf die Produktdaten verweist (in der Regel unter `/etc/commerce/products`).
         * Die Produktdaten sind hierarchisch; Produktattribute werden von den Vorgängern eines Produktdatenknotens vererbt.
         * Produktverweise können auch lokale Eigenschaften enthalten, die die in ihren Produktdaten angegebenen überschreiben.
      * Ein Produkt selbst:

         * Ohne eine `productData`-Eigenschaft.
         * Ein Produktknoten, der alle Eigenschaften lokal enthält (und keine productData -Eigenschaft enthält), erbt Produktattribute direkt von seinen eigenen Vorgängern.


* **AEM-generische Produktstruktur**

   * Jede Variante muss über einen eigenen Blattknoten verfügen.
   * Die Produktoberfläche stellt sowohl Produkte als auch Varianten dar, aber der zugehörige Repository-Knoten ist spezifisch für den es ist.
   * Der Produktknoten beschreibt die Produktattribute und Variantenachsen.

#### Beispiel {#example-1}

```shell
+ banyan_shirt
    - cq:commerceType = product
    - cq:productAttributes = [jcr:title, jcr:description, size, price, color]
    - cq:productVariantAxes = [color, size]
    - jcr:title = Banyan Shirt
    - jcr:description = Flowery, all-cotton shirt.
    - price = 14.00
    + banyan_shirt_s
        - cq:commerceType = variant
        - size = S
        + banyan_shirt_s_red
            - cq:commerceType = variant
            - color = red
        + banyan_shirt_s_blue
            - cq:commerceType = variant
            - color = blue
    + banyan_shirt_m
        - cq:commerceType = variant
        - size = M
        + banyan_shirt_m_red
            - cq:commerceType = variant
            - color = red
        + banyan_shirt_m_blue
            - cq:commerceType = variant
            - color = blue
    + banyan_shirt_l
        - cq:commerceType = variant
        - size = L
        + banyan_shirt_l_red
            - cq:commerceType = variant
            - color = red
        + banyan_shirt_l_blue
            - cq:commerceType = variant
            - color = blue
    + banyan_shirt_xl
        - cq:commerceType = variant
        - size = XL
        - price = 18.00
```

#### Architektur des Warenkorbs {#architecture-of-the-shopping-cart}

**Komponenten**

* Der Warenkorb wird von `CommerceSession:` gesteuert:

   * `CommerceSession` führt Hinzufügen/Entfernen-Aktionen usw. durch.
   * `CommerceSession` nimmt auch die diversen Berechnungen des Warenkorbs vor. ``

* Obwohl dies nicht direkt mit dem Warenkorb zusammenhängt, muss `CommerceSession` auch Katalogpreisinformationen angeben (da sie die Preise steuert).

   * Preise können mehrere Modifikatoren aufweisen:

      * Mengenrabatte.
      * Verschiedene Währungen.
      * Mehrwertsteuerpflichtig und mehrwertsteuerfrei.
   * Die Modifikatoren sind vollständig offen mit der folgenden Benutzeroberfläche:

      * `int CommerceSession.getQuantityBreakpoints(Product product)`
      * `String CommerceSession.getProductPrice(Product product)`


**Speicher**

* Speicher

   * Im hybris-Fall ist der hybris-Server Eigentümer des Warenkorbs.
   * Im AEM generischen Fall werden Warenkörbe im [ClientContext](/help/sites-administering/client-context.md).

**Personalisierung**

* Die Personalisierung sollte immer durch das [ClientContext](/help/sites-administering/client-context.md).
* In allen Fällen wird eine ClientContext-Version (`/version/`) des Warenkorbs erstellt:

   * Produkte sollten mithilfe der `CommerceSession.addCartEntry()`-Methode hinzugefügt werden.

* Nachstehend sehen Sie ein Beispiel für Warenkorbinformationen in einem ClientContext-Warenkorb:

![chlimage_1-13](assets/chlimage_1-13.png)

#### Architektur des Auscheckens {#architecture-of-checkout}

**Warenkorb- und Bestelldaten**

`CommerceSession` steuert die drei folgenden Elemente:

1. Inhalt des Warenkorbs
1. Preise
1. Die Bestelldetails

1. **Inhalt des Warenkorbs**

   Das Inhaltsschema des Warenkorbs wird durch die API festgelegt:

   ```java
       public void addCartEntry(Product product, int quantity);
       public void modifyCartEntry(int entryNumber, int quantity);
       public void deleteCartEntry(int entryNumber);
   ```

1. **Preise**

   Das Preisschema wird ebenfalls von der API festgelegt:

   ```java
       public String getCartPreTaxPrice();
       public String getCartTax();
       public String getCartTotalPrice();
       public String getOrderShipping();
       public String getOrderTotalTax();
       public String getOrderTotalPrice();
   ```

1. **Auftragsdetails**

   Die Auftragsdetails werden jedoch *nicht* von der API festgelegt:

   ```java
       public void updateOrderDetails(Map<String, String> orderDetails);
       public Map<String, String> getOrderDetails();
       public void submitOrder();
   ```

**Versandberechnungen**

* Bestellformulare müssen häufig mehrere Versandoptionen (und Preise) enthalten.
* Die Preise können auf Artikeln und Details der Bestellung basieren, wie Gewicht und/oder Lieferadresse.
* `CommerceSession` hat Zugriff auf alle Abhängigkeiten und kann daher ähnlich wie Produktpreise behandelt werden:

   * `CommerceSession` steuert die Versandkosten.
   * Kann Versanddetails über `updateOrder(Map<String, Object> delta)` abrufen oder aktualisieren.

>[!NOTE]
>
>Sie können eine Versandauswahl implementieren, z. B.:
>
>`yourProject/commerce/components/shippingpicker`:
>
>* Dabei kann es sich im Wesentlichen um eine Kopie von `foundation/components/form/radio` handeln, jedoch mit Rückrufen an `CommerceSession` für folgende Zwecke:
>
>* Überprüfen, ob die Methode verfügbar ist
>* Preisinformationen hinzufügen
>* Möglichkeit für Erstkäufer, die Auftragsseite in AEM (einschließlich Obermenge der Versandmethoden und Beschreibungstexten) zu aktualisieren und weiterhin die Anzeige relevanter `CommerceSession`-Informationen zu steuern.


**Zahlungsverarbeitung**

* `CommerceSession` steuert auch die Verbindung für die Zahlungsverarbeitung.
* Implementierungsprogramme müssen spezifische Aufrufe (an den ausgewählten Zahlungsverarbeitungs-Service) zur `CommerceSession`-Implementierung hinzufügen.

**Auftragserfüllung**

* `CommerceSession` steuert auch die Verbindung für die Auftragserfüllung.
* Implementierungprogramme müssen spezifische Aufrufe (an den ausgewählten Zahlungsverabeitungs-Service) zur `CommerceSession`-Implementierung hinzufügen.

### Suchdefinition {#search-definition}

Gemäß dem Standard-Service-API-Modell stellt das eCommerce-Projekt eine Reihe suchbezogener APIs bereit, die von einzelnen Commerce-Engines implementiert werden können.

>[!NOTE]
>
>Derzeit implementiert nur die hybris-Engine die Such-API standardmäßig.
>
>Die Such-API ist jedoch generisch und kann von jedem CommerceService einzeln implementiert werden.

Das eCommerce-Projekt enthält eine standardmäßige Suchkomponente, die sich unter:

`/libs/commerce/components/search`

![chlimage_1-14](assets/chlimage_1-14.png)

Dadurch wird die Such-API zur Abfrage der ausgewählten Commerce-Engine verwendet (siehe [Auswahl der eCommerce-Engine](#ecommerce-engine-selection)):

#### Such-API {#search-api}

Es gibt mehrere generische / Helper-Klassen, die vom Kernprojekt bereitgestellt werden:

1. `CommerceQuery`

   Wird zum Beschreiben einer Suchabfrage verwendet (enthält Informationen zu Abfragetext, aktueller Seite, Seitengröße, Sortierung und ausgewählten Facetten). Alle eCommerce-Services, die die Such-API implementieren, erhalten Instanzen dieser Klasse, um die Suche durchführen zu können. Es kann eine `CommerceQuery`-Instanz anhand eines Anfrageobjekts (`HttpServletRequest`) erstellt werden.

1. `FacetParamHelper`

   Eine Hilfsprogramm-Klasse, die eine statische Methode (`toParams`) zum Erzeugen von `GET`-Parameterzeichenfolgen aus einer Facettenliste und einen umgeschalteten Wert bereitstellt. Dies ist auf der UI-Seite nützlich, auf der Sie für jeden Wert einer Facette einen Hyperlink anzeigen müssen. Wenn der Benutzer auf den Hyperlink klickt, wird der entsprechende Wert umgeschaltet (d. h. wenn er ausgewählt wurde, wird er aus der Abfrage entfernt und andernfalls hinzugefügt). Dadurch wird die gesamte Logik des Umgangs mit Facetten mit mehreren/einzelnen Werten, des Überschreibens von Werten usw. berücksichtigt.

Einstiegspunkt für die Such-API ist die `CommerceService#search`-Methode, die ein `CommerceResult`-Objekt zurückgibt. Siehe [API-Dokumentation](/help/sites-developing/ecommerce.md#api-documentation) für weitere Informationen zu diesem Thema.

### Benutzerintegration {#user-integration}

Die Integration zwischen AEM und verschiedenen E-Commerce-Systemen erfolgt. Dies erfordert eine Strategie zur Synchronisierung der Käufer zwischen den verschiedenen Systemen, sodass AEM-spezifischer Code nur über AEM und umgekehrt wissen muss:

* Authentifizierung

   Es wird davon ausgegangen, dass AEM das *einzige* Web-Front-End ist und daher *alle* Authentifizierungen verarbeitet.

* Konten in Hybris

   AEM erstellt für jeden Erstkäufer ein entsprechendes (sekundäres) Konto in Hybris. Der Benutzername dieses Kontos ist mit dem AEM-Benutzernamen identisch. Ein kryptografisches Zufallskennwort wird automatisch in AEM erstellt und gespeichert (verschlüsselt).

#### Vorhandene Benutzer {#pre-existing-users}

Ein AEM Frontend kann vor einer vorhandenen Hybris-Implementierung positioniert werden. Auch eine Hybris-Engine kann zu einer bestehenden AEM-Installation hinzugefügt werden. Dazu müssen die Systeme in der Lage sein, bestehende Benutzer in beiden Systemen ordnungsgemäß zu handhaben:

* AEM -> hybris

   * Beim Anmelden bei Hybris (falls noch kein AEM-Benutzer vorhanden ist):

      * Erstellen Sie einen neuen Hybris-Benutzer mit einem kryptografischen Zufallskennwort.
      * Speichern Sie den Hybris-Benutzernamen im Benutzerverzeichnis des AEM-Benutzers.
   * Siehe: `com.adobe.cq.commerce.hybris.impl.HybrisSessionImpl#login()`


* Hybris -> AEM

   * Beim Anmelden bei AEM (falls das System einen Benutzer erkennt):

      * Versuch, sich bei hybris mit dem angegebenen Benutzernamen/PWD anzumelden
      * Wenn dies erfolgreich war, erstellen Sie den neuen Benutzer in AEM mit demselben Kennwort (AEM-spezifisches Salz führt zu AEM Hash).
   * Der obige Algorithmus wird in einem `AuthenticationInfoPostProcessor` von Sling implementiert.

      * Siehe: `com.adobe.cq.commerce.hybris.impl.user.LazyUserImporter.java`


### Anpassen des Importvorgangs {#customizing-the-import-process}

Um auf vorhandenen Funktionen aufzubauen, verwenden Sie Ihren benutzerdefinierten Import-Handler:

* Er muss die `ImportHandler`-Schnittstelle implementieren.

* kann die `DefaultImportHandler`

```java
/**
 * Services implementing the <code>ImportHandler</code> interface are
 * called by the {@link HybrisImporter} to create actual commerce entities
 * such as products.
 */
public interface ImportHandler {

    /**
     * Not used.
     */
    public void createTaxonomie(ImporterContext ctx);

    /**
     * Creates a catalog with the given name.
     * @param ctx   The importer context
     * @param name  The catalog's name
     * @return Path of created catalog
     */
    public String createCatalog(ImporterContext ctx, String name) throws Exception;

    /**
     * Creates a product from the given values.
     * @param ctx                The importer context
     * @param values             The product's properties
     * @param parentCategoryPath The containing category's path
     * @return Path of created product
     */
    public String createProduct(ImporterContext ctx, ValueMap values, String parentCategoryPath) throws Exception;

    /**
     * Creates a variant product from the given values.
     * @param ctx             The importer context
     * @param values          The product's properties
     * @param baseProductPath The base product's path
     * @return Path of created product
     */
    public String createVariantProduct(ImporterContext ctx, ValueMap values, String baseProductPath) throws Exception;

    /**
     * Creates an asset for a product. This is usually a product
     * image.
     * @param ctx             The importer context
     * @param values          The product's properties
     * @param baseProductPath The product's path
     * @return Path of created asset
     */
    public String createAsset(ImporterContext ctx, ValueMap values, String productPath) throws Exception;

    /**
     * Creates a category from the given values.
     * @param ctx           The importer context
     * @param values        The category's properties
     * @param parentPath    Path of parent category or base path of import in case of root category
     * @return Path of created category
     */
    public String createCategory(ImporterContext ctx, ValueMap values, String parentCategoryPath) throws Exception;
}
```

Damit Ihr benutzerdefinierter Handler vom Importer erkannt wird, muss er die `service.ranking`Eigenschaft mit einem Wert größer als 0; Beispiel:

```java
@Component
@Service
@Property(name = "service.ranking", value = 100)
public class MyImportHandler extends DefaultImportHandler {
    ...
}
```
