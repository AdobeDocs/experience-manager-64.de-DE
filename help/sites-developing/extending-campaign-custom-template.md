---
title: Erstellen benutzerdefinierter AEM-Seitenvorlagen mit Adobe Campaign-Formularkomponenten
seo-title: Creating Custom AEM Page Template with Adobe Campaign Form Components
description: Erstellen Sie eine benutzerdefinierte Seitenvorlage auf der Basis von Adobe Campaign-Formularkomponenten.
seo-description: Build a custom page template that uses Adobe Campaign Form components
uuid: 8162ace2-b661-4c39-b0fb-288e1c035b9c
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: c3f6eed4-bbda-454a-88ce-c7f2041d4217
exl-id: e70c9d23-5a4d-4137-82ad-3f3237f468c0
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 55%

---

# Erstellen benutzerdefinierter AEM-Seitenvorlagen mit Adobe Campaign-Formularkomponenten{#creating-custom-aem-page-template-with-adobe-campaign-form-components}

Auf dieser Seite wird beschrieben, wie Sie eine benutzerdefinierte Seitenvorlage erstellen, die [Adobe Campaign-Formular](/help/sites-authoring/adobe-campaign-components.md) Komponenten durch Prüfung der Vorlage &quot;Geometrixx Outdoors&quot;( `/apps/geometrixx-outdoors/components/page_campaign_profile`) implementiert ist und Sie auf wichtige Informationen verweist, die Sie beim Erstellen Ihrer eigenen benutzerdefinierten Vorlage benötigen.

>[!NOTE]
>
>[E-Mail- und Formularbeispiele sind nur in Geometrixx verfügbar](/help/sites-developing/we-retail.md). Laden Sie Geometrixx-Beispielinhalt von Package Share herunter.

Um eine benutzerdefinierte AEM-Seitenvorlage mit Adobe Campaign-Formularkomponenten zu erstellen, müssen Sie sicherstellen, dass Sie über Folgendes verfügen:

1. **Die richtige resourceSuperType-Klasse**

   Stellen Sie sicher, dass die Seitenkomponente von erbt. `mcm/campaign/components/profile`.

   Dies ist erforderlich, damit die Servlets Informationen abrufen und speichern können

   * `com.day.cq.mcm.campaign.servlets.TemplateListServlet`
   * `com.day.cq.mcm.campaign.servlets.SaveProfileServlet`

   ![chlimage_1-201](assets/chlimage_1-201.png)

1. **ClientContext-Einstellungen**

   Wenn Sie sich die ClientContext-Einstellungen ansehen ( `/etc/designs/geometrixx-outdoors/jcr:content/page_campaign_profile`) sehen Sie die folgenden Einstellungen:

   * ClientContext verweist auf `/etc/clientcontext/campaign`
   * Es ist außerdem ein zusätzlicher Knoten *config* vorhanden.

   ![chlimage_1-202](assets/chlimage_1-202.png)

1. **head.jsp (/apps/geometrixx-outdoors/components/page_campaign_profile/head.jsp)**

   **head.jsp** enthält die folgenden Zeilen, die **clientcontext-config** und **cloudservice-hook** verwenden:

   ```
   <cq:include path="config" resourceType="cq/personalization/components/clientcontext_optimized/config"/>
   <sling:include path="contexthub" resourceType="granite/contexthub/components/contexthub"/>
   <cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>
   ```

1. **body.jsp (/apps/geometrixx-outdoors/components/page_campaign_profile/body.jsp)**

   In **body.jsp**, werden die Cloud-Dienste unten auf der Seite geladen:

   ```
   <cq:include path="cloudservices" resourceType="cq/cloudserviceconfigs/components/servicecomponents"/>
   ```

1. **Kampagnenseiteneigenschaften**

   Um eine Adobe Campaign-Vorlage auswählen zu können, müssen die Seiteneigenschaften um die Registerkarte **Kampagne** erweitert werden:

   `/apps/geometrixx-outdoors/components/page_campaign_profile/dialog/items/tabs/items/campaign`

   ![chlimage_1-203](assets/chlimage_1-203.png)

1. **Vorlageneinstellungen**.

   In der Vorlage ( `/apps/geometrixx-outdoors/templates/campaign_profile/jcr:content`) sehen Sie die folgenden Standardwerte:

   | **acMapping** | mapRecipient (für Adobe Campaign 6.1), profile (für Adobe Campaign Standard) |
   |---|---|
   | **acTemplateId** | mail |

   ![chlimage_1-204](assets/chlimage_1-204.png)
