---
title: Verwalten Sie [!DNL Adobe Stock] -Assets in [!DNL Adobe Experience Manager Assets].
description: Suchen, lizenzieren, verwalten und rufen Sie [!DNL Adobe Stock] -Assets in [!DNL Adobe Experience Manager] ab. Nutzen Sie die lizenzierten Assets wie jedes andere digitale Asset.
contentOwner: AG
feature: Search,Adobe Stock
role: User,Admin
exl-id: f360abaf-a812-46ed-a160-ff569b6bec1c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 88%

---

# Verwenden von [!DNL Adobe Stock]-Assets in [!DNL Adobe Experience Manager Assets] {#use-adobe-stock-assets-in-aem-assets}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Organisationen können ihr [!DNL Adobe Stock]-Unternehmensabo mit [!DNL Experience Manager Assets] integrieren, damit lizenzierte Assets für kreative und Marketing-Projekte umfassend verfügbar sind und mit den leistungsstarken Asset-Management-Funktionen von [!DNL Experience Manager] verwaltet werden können.

Der [!DNL Adobe Stock]-Service bietet Designern und Unternehmen Zugang zu Millionen von hochwertigen, kuratierten und gebührenfreien Fotos, Vektorgrafiken, Illustrationen, Videos, Vorlagen und 3D-Assets für sämtliche Kreativprojekte. [!DNL Experience Manager]-Benutzer können [!DNL Adobe Stock]-Assets, die in [!DNL Experience Manager] gespeichert sind, schnell finden, eine Vorschau anzeigen und die Lizenz abrufen, ohne ihre [!DNL Experience Manager]-Oberfläche zu verlassen.

## Voraussetzungen {#prerequisites}

Die Integration erfordert eine [Enterprise Adobe Stock-Abo](https://stockenterprise.adobe.com/de/home.html) und [!DNL Experience Manager] 6.4 mit mindestens Service Pack 2 bereitgestellt. Für [!DNL Experience Manager] 6.4 Service Pack-Details, siehe diese [Versionshinweise](/help/release-notes/sp-release-notes.md).

## Integrieren von [!DNL Experience Manager] und [!DNL Adobe Stock] {#integrate-aem-and-adobe-stock}

Um die Kommunikation zwischen [!DNL Experience Manager] und [!DNL Adobe Stock] zu ermöglichen, erstellen Sie eine IMS- sowie eine [!DNL Adobe Stock]-Konfiguration in [!DNL Experience Manager].

>[!NOTE]
>
>Nur [!DNL Experience Manager]- und [!DNL Admin Console]-Administratoren einer Organisation können die Integration durchführen, da hierfür Administratorrechte erforderlich sind.

### Erstellen einer IMS-Konfiguration {#create-an-ims-configuration}

1. Navigieren Sie in der [!DNL Experience Manager]-Benutzeroberfläche zu **[!UICONTROL Tools]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Adobe IMS-Konfigurationen]**. Klicken Sie auf **[!UICONTROL Erstellen]** und wählen Sie **[!UICONTROL Cloud-Lösung]** > **[!UICONTROL Adobe Stock]**.
1. Verwenden Sie entweder ein vorhandenes Zertifikat erneut oder wählen Sie **[!UICONTROL Neues Zertifikat erstellen]**.
1. Klicken Sie auf **[!UICONTROL Zertifikat erstellen]**. Laden Sie nach der Erstellung den öffentlichen Schlüssel herunter. Klicken Sie auf **[!UICONTROL Weiter]**. Lassen Sie den Bildschirm [!UICONTROL Konfiguration des technischen Adobe IMS-Kontos] geöffnet, um die erforderlichen Werte in Kürze anzugeben.
1. Greifen Sie auf die [Adobe Developer Console](https://console.adobe.io) zu. Stellen Sie sicher, dass Ihr Konto über Administratorrechte für die Organisation verfügt, für die die Integration benötigt wird.
1. Klicken Sie auf **[!UICONTROL Neues Projekt erstellen]** und dann auf **[!UICONTROL API hinzufügen]**. Wählen Sie **[!UICONTROL Adobe Stock]** aus der Liste der zur Verfügung stehenden APIs. Wählen Sie [!UICONTROL OAUTH 2.0 Web] aus.
1. Geben Sie die Werte für den **[!UICONTROL Standard-Umleitungs-URI]** und **[!UICONTROL Umleitungs-URI-Muster]** an. Klicken Sie auf **[!UICONTROL Konfigurierte API speichern]**. Kopieren Sie die generierte ID und den geheimen Schlüssel.
1. Geben Sie im Bildschirm [!UICONTROL Konfiguration des technischen Adobe IMS-Kontos] die Werte in die Felder **[!UICONTROL Titel]**, **[!UICONTROL Autorisierungsserver]**, **[!UICONTROL API-Schlüsel]**, **[!UICONTROL Client-Geheimnis]** und **[!UICONTROL Nutzlast]** ein. Ausführliche Informationen zu diesen Werten finden Sie unter [Schnellstart zur JWT-Authentifizierung](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/JWT/JWT.md).

<!-- TBD: Update the URL when the new URL is available. Logged issue github.com/AdobeDocs/adobeio-auth/issues/63.
-->

### Erstellen der [!DNL Adobe Stock]-Konfiguration in [!DNL Experience Manager] {#create-adobe-stock-configuration-in-aem}

1. Navigieren Sie in der [!DNL Experience Manager] Benutzeroberfläche zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Stock]**.
1. Klicken Sie auf **[!UICONTROL Erstellen]**, um eine Konfiguration zu erstellen und sie Ihrer bestehenden IMS-Konfiguration zuzuordnen. Wählen Sie `PROD` als Umgebungsparameter aus.
1. Lassen Sie den Speicherort im Feld **[!UICONTROL Pfad lizenzierter Assets]** unverändert. Ändern Sie den Speicherort nicht in den Pfad, in dem Sie die [!DNL Adobe Stock]-Assets speichern möchten.
1. Schließen Sie die Erstellung ab, indem Sie alle erforderlichen Eigenschaften hinzufügen. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.
1. Fügen Sie [!DNL Experience Manager]-Benutzer oder -Gruppen hinzu, die die Assets lizenzieren können.

>[!NOTE]
>
>Wenn mehrere [!DNL Adobe Stock] -Konfigurationen die gewünschte Konfiguration im Bedienfeld Benutzereinstellungen (**[!UICONTROL AEM]** > **[!UICONTROL Benutzersymbol]** > **[!UICONTROL Benutzereinstellungen]** > **[!UICONTROL Stock-Konfiguration]**).

## Verwenden und Verwalten von [!DNL Adobe Stock]-Assets in [!DNL Experience Manager] {#usemanage}

Mit dieser Funktion können Organisationen ihren Benutzern die Arbeit mit [!DNL Adobe Stock]-Assets in [!DNL Experience Manager Assets] ermöglichen. Benutzer können aus der [!DNL Experience Manager]-Benutzeroberfläche heraus nach [!DNL Adobe Stock]-Assets suchen und die erforderlichen Assets lizenzieren.

Sobald ein [!DNL Adobe Stock]-Asset in [!DNL Experience Manager] lizenziert ist, kann es wie ein typisches Asset verwendet und verwaltet werden. Benutzer können Assets in [!DNL Experience Manager] suchen und eine Vorschau zu diesen anzeigen, Assets kopieren und veröffentlichen, Assets in [!DNL Brand Portal] teilen, Assets per [!DNL Experience Manager]-Desktop-Programm aufrufen und verwenden und vieles mehr.

![Suchen nach Adobe Stock-Assets und Filtern von Ergebnissen aus Ihrem Adobe Experience Manager Workspace](assets/adobe-stock-search-results-workspace.png)

*Abbildung: Suchen Sie nach [!DNL Adobe Stock] Assets und Filtern von Ergebnissen aus Ihrer [!DNL Experience Manager] -Schnittstelle.*

**A.** Suche nach Assets, die den Assets ähneln, deren [!DNL Adobe Stock]-ID angegeben ist. **B.** Suche nach Assets, die Ihrer Form- und Ausrichtungswahl entsprechen. **C.** Suche nach einem von mehreren unterstützten Asset-Typen **D.** Öffnen oder Reduzieren des Filterbereichs **E.** Lizenzieren und Speichern des ausgewählten Assets in [!DNL Experience Manager] **F.** Speichern des Assets in [!DNL Experience Manager] mit Wasserzeichen **G.** Erkunden von Assets auf der [!DNL Adobe Stock]-Website, die dem ausgewählten Asset ähnlich sind **H.** Anzeigen der ausgewählten Assets auf der [!DNL Adobe Stock]-Website **I.** Anzahl der ausgewählten Assets aus den Suchergebnissen **J.** Umschalten zwischen Kartenansicht und Listenansicht

### Suchen von Assets {#find-assets}

Ihre [!DNL Experience Manager]-Benutzer können in [!DNL Experience Manager] und [!DNL Adobe Stock] nach Assets suchen. Wenn die Suche nicht auf [!DNL Adobe Stock] beschränkt ist, werden Suchergebnisse aus [!DNL Experience Manager] und [!DNL Adobe Stock] angezeigt.

* Um nach [!DNL Adobe Stock]-Assets zu suchen, klicken Sie auf **[!UICONTROL Navigation]** > **[!UICONTROL Assets]** > **[!UICONTROL Adobe Stock durchsuchen]**.

* So suchen Sie Assets überall [!DNL Adobe Stock] und [!DNL Experience Manager Assets], klicken Sie auf Suchen ![search_icon](assets/search_icon.png).

Geben Sie alternativ `Location: Adobe Stock` in die Suchleiste ein, um [!DNL Adobe Stock]-Assets auszuwählen. [!DNL Experience Manager] bietet erweiterte Filterfunktionen, mit denen Benutzer schnell die gewünschten Assets finden können. Hierzu stehen Filter, wie z. B. unterstützte Asset-Typen, Bildausrichtung und Lizenzstatus, zur Verfügung.

>[!NOTE]
>
>In [!DNL Adobe Stock] durchsuchte Assets werden nur in [!DNL Experience Manager] angezeigt. [!DNL Adobe Stock]-Assets werden nur dann abgerufen und im [!DNL Experience Manager]-Repository gespeichert, wenn Benutzer [Assets speichern](/help/assets/aem-assets-adobe-stock.md#saveassets) oder [Assets lizenzieren und speichern](/help/assets/aem-assets-adobe-stock.md#licenseassets). Assets, die bereits in [!DNL Experience Manager] gespeichert sind, werden angezeigt und hervorgehoben, um einfachen Zugriff und eine schnelle Referenzierung zu ermöglichen. Außerdem werden die [!DNL Stock]-Assets mit einigen zusätzlichen Metadaten gespeichert, um die Quelle als [!DNL Stock] anzugeben.

![Suchfilter in Experience Manager und in Suchergebnissen hervorgehobene Adobe Stock-Assets](assets/aem-search-filters2.jpg)

*Abbildung: Suchfilter in [!DNL Experience Manager] und hervorgehobene [!DNL Adobe Stock]-Assets in Suchergebnissen.*

### Speichern und Anzeigen erforderlicher Assets {#saveassets}

Wählen Sie ein Asset aus, das Sie in [!DNL Experience Manager] speichern möchten. Klicken Sie in der oberen Symbolleiste auf [!UICONTROL Speichern] und geben Sie den Namen und Speicherort des Assets an. Unlizenzierte Assets werden lokal mit Wasserzeichen gespeichert.

Wenn Sie erneut nach Assets suchen, werden die gespeicherten Assets durch ein Symbol hervorgehoben, um anzuzeigen, dass diese Assets in [!DNL Experience Manager Assets] verfügbar sind.

>[!NOTE]
>
>Bei den kürzlich hinzugefügten Assets wird das Symbol „Neu“ anstelle des Symbols „Lizenziert“ angezeigt.

### Lizenzieren von Assets {#licenseassets}

Benutzer können [!DNL Adobe Stock]-Assets über das Kontingent ihres [!DNL Adobe Stock]-Unternehmensplans lizenzieren. Wenn Sie ein Asset lizenzieren, wird es ohne Wasserzeichen gespeichert und ist in der Suche sowie für die Verwendung in [!DNL Experience Manager Assets] verfügbar.

![Dialogfeld zum Lizenzieren und Speichern von Adobe Stock-Assets in Experience Manager Assets](assets/aem-stock_licenseandsave.jpg)

*Abbildung: Dialogfeld zum Lizenzieren und Speichern von [!DNL Adobe Stock]-Assets in [!DNL Experience Manager Assets].*

### Anzeigen von Metadaten und Asset-Eigenschaften {#access-metadata-and-asset-properties}

Benutzer können Metadaten, einschließlich der [!DNL Adobe Stock]-Metadateneigenschaften für Assets, die in [!DNL Experience Manager] gespeichert wurden, öffnen bzw. eine Vorschau dieser Daten anzeigen und **[!UICONTROL Lizenzreferenzen]** für Assets hinzufügen. Die Änderungen an der Lizenzreferenz werden zwischen [!DNL Experience Manager] und der [!DNL Adobe Stock]-Website jedoch nicht synchronisiert.

Benutzer können die Eigenschaften für lizenzierte und unlizenzierte Assets anzeigen.

![Metadaten und Lizenzreferenzen gespeicherter Assets anzeigen](assets/metadata_properties.jpg)

*Abbildung: Metadaten und Lizenzreferenzen gespeicherter Assets anzeigen und aufrufen.*

## Bekannte Einschränkungen {#known-limitations}

* **Redaktionelle Bildwarnung wird nicht angezeigt**: Bei der Lizenzierung eines Bilds können Benutzer nicht prüfen, ob ein Bild ausschließlich der redaktionellen Verwendung dient. Um zu verhindern, dass Bilder falsch verwendet werden, können Administratoren den Zugriff auf redaktionelle Assets über die Admin Console deaktivieren.

* **Falscher Lizenztyp wird angezeigt**: Es ist möglich, dass in [!DNL Experience Manager] ein falscher Lizenztyp für ein Asset angezeigt wird. Benutzer können sich bei der [!DNL Adobe Stock]-Website anmelden, um den richtigen Lizenztyp zu ermitteln.

* **Referenzfelder und Metadaten werden nicht synchronisiert**: Wenn ein Benutzer ein Lizenzreferenzfeld aktualisiert, werden die Lizenzreferenzdaten in [!DNL Experience Manager] aktualisiert, jedoch nicht auf der [!DNL Adobe Stock]-Website. Ebenso werden Änderungen, die Benutzer an den Referenzfeldern auf der [!DNL Adobe Stock]-Website vornehmen, nicht mit [!DNL Experience Manager] synchronisiert.

>[!MORELIKETHIS]
>
>* [Video-Tutorial zur Verwendung von [!DNL Adobe Stock] Assets mit  [!DNL Experience Manager Assets]](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/creative-workflows/adobe-stock.html?lang=de)
>* [[!DNL Adobe Stock] Hilfe zum Unternehmensplan](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/adobe-stock-enterprise.ug.html)
>* [[!DNL Adobe Stock] Häufig gestellte Fragen (FAQ)](https://helpx.adobe.com/de/stock/faq.html)

