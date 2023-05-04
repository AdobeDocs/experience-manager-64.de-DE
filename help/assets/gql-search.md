---
title: GQL-Volltextsuche
description: Erkunden Sie die GQL-Volltextsuchfunktion in [!DNL Experience Manager] Assets. Verwenden Sie sie, um basierend auf bestimmten Metadaten, wie Titel, Beschreibung und Autorenname, nach Assets zu suchen.
contentOwner: AG
feature: Search,Metadata
role: User
exl-id: e819501c-4ac3-447f-944c-67adc42e8c61
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '909'
ht-degree: 37%

---

# GQL-Volltextsuche {#gql-full-text-search}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Erkunden Sie die GQL-Volltextsuchfunktion in [!DNL Experience Manager] Assets. Verwenden Sie sie, um basierend auf bestimmten Metadaten, wie Titel, Beschreibung und Autorenname, nach Assets zu suchen.

Mit der Funktion für die GQL-Volltextsuche können Sie basierend auf bestimmten Metadaten (z. B. Titel, Beschreibung, Autor usw.) nach Assets suchen.

Um basierend auf Metadaten (z. B. dem Titel) nach einem Asset zu suchen, geben Sie das Metadaten-Keyword gefolgt von dessen Wert im Suchbereich an. Die Volltextsuchfunktion GQL ruft nur die Assets ab, deren Metadaten genau mit dem eingegebenen Wert übereinstimmen.

Um beispielsweise nach Assets mit dem Titel &quot;Target&quot;zu suchen, führen Sie die folgenden Schritte aus:

## Suchen nach Assets {#searching-assets}

1. Klicken oder tippen Sie in der Symbolleiste der Assets-Benutzeroberfläche auf die **[!UICONTROL Suche]** zum Anzeigen des Omnisearch-Suchfelds.

   ![](assets/do-not-localize/chlimage_1.png)

1. Betätigen Sie bei in das OmniSearch-Feld gesetztem Cursor die Eingabetaste.
1. Klicken oder tippen Sie auf das GlobalNav-Symbol, um die **[!UICONTROL Filter]** Bereich.
1. Geben Sie im Omni-Suchfeld den Wert &quot;Target&quot;an. Um die Suche auf einen bestimmten Ordner zu beschränken, klicken oder tippen Sie im Bedienfeld Filter auf das Symbol Durchsuchen und wählen Sie den Ordner aus. In diesem Fall wird die Übereinstimmung nur innerhalb des Ordners und der Unterordner darunter gesucht.

   >[!NOTE]
   >
   >Sie können auch eine Volltextsuche nach Ordnern durchführen. In diesem Fall müssen Sie einen nicht leeren Volltextsuchbegriff angeben.

   ![gql_search](assets/gql_search.png)

1. Presse **[!UICONTROL Eingabe]**. Die [!DNL Assets] -Benutzeroberfläche zeigt nur die Assets an, deren Titel genau mit &quot;Target&quot;übereinstimmt.

Mit der Funktion für die GQL-Volltextsuche können Sie Assets anhand der folgenden Elemente durchsuchen:

* Komplexe Abfrage, die durch Kombinieren der Werte, die Sie für mehrere Metadatenfelder (Eigenschaften) angeben, über einen Und-Vorgang erstellt wurde
* Mehrere Werte für ein einzelnes Metadatenfeld
* Teilzeichenfolge stimmt überein mit

Mit der Volltextsuchfunktion GQL können Sie anhand der folgenden Metadateneigenschaften nach Assets suchen. Bei den Namen der Eigenschaften (z. B. Autor, Titel usw.) und Werten wird zwischen Groß- und Kleinschreibung unterschieden.

>[!NOTE]
>
>Die GQL-Volltextsuche funktioniert nur für Volltextprädikate.

| Eigenschaft | Suchformat (Facettenwert) |
|---|---|
| [!UICONTROL Titel] | title:John |
| [!UICONTROL Ersteller] | creator:John |
| [!UICONTROL Mitarbeiter] | contributor:John |
| [!UICONTROL Speicherort] | location:India |
| [!UICONTROL Beschreibung] | description:&quot;Sample Image&quot; |
| [!UICONTROL Erstellungswerkzeug] | creatortool:&quot;Adobe Photoshop 7.0&quot; |
| [!UICONTROL Urheberrechtsbesitzer] | copyrightowner:&quot;Adobe Systems&quot; |
| [!UICONTROL Mitarbeiter] | contributor:John |
| [!UICONTROL Nutzungsbedingungen] | usageterms:„CopyRights Reserved“ |
| [!UICONTROL Erstellt] | created:YYYY-MM-DDTHH:MM:SS.000+05:30..YYYY-MM-DDTHH:MM:SS.000+05:30 |
| [!UICONTROL Ablaufdatum] | expires:YYYY-MM-DDTHH:MM:SS.000+05:30..YYYY-MM-DDTHH:MM:SS.000+05:30 |
| [!UICONTROL Einschaltzeit] | ontime:YYYY-MM-DDTHH:MM:SS.000+05:30..YYYY-MM-DDTHH:MM:SS.000+05:30 |
| [!UICONTROL Ausschaltzeit] | Offtime:YYYY-MM-DDTHH:MM:SS.000+05:30..YYYY-MM-DDTHH:MM:SS.000+05:30 |
| [!UICONTROL Zeitraum] (expires dateontime,offtime) | facet field : lowerbound.upperbound |
| [!UICONTROL Pfad] | /content/dam/&lt;folder name> |
| [!UICONTROL PDF-Titel] | pdftitle:„Adobe Document“ |
| [!UICONTROL Betreff] | subject:„Training“ |
| [!UICONTROL Tags] | tags:„Location And Travel“ |
| [!UICONTROL Typ] | type:&quot;image\png&quot; |
| [!UICONTROL Bildbreite] | width:lowerbound.upperbound |
| [!UICONTROL Bildhöhe] | height:lowerbound.upperbound |
| [!UICONTROL Person] | person:John |

Im Folgenden finden Sie einige Beispiele für Suchformate für komplexe Abfragen:

* So zeigen Sie alle Assets mit mehreren Facettenfeldern an (wie: title=John Doe und creator tool = Adobe Photoshop):  

tiltle:&quot;John Doe&quot; creatortool : Adobe&amp;ast;

* So zeigen Sie alle Assets an, wenn der Facettenwert nicht ein einzelnes Wort, sondern ein Satz ist (wie: title=Scott Reynolds)

title:&quot;Scott Reynolds&quot;

* So zeigen Sie alle Assets mit mehreren Werten für eine einzelne Eigenschaft an (wie: title=Scott Reynolds oder John Doe)

title:&quot;Scott Reynolds&quot; ODER &quot;John Doe&quot;

* So zeigen Sie Assets an, deren Eigenschaftswerte mit einer bestimmten Zeichenfolge beginnen (wie: title ist Scott Reynolds)

title:&quot;Scott&quot;

* So zeigen Sie Assets an, deren Eigenschaftswerte mit einer bestimmten Zeichenfolge enden (wie: title ist Scott Reynolds)

title:&quot;Reynolds&quot;

* So zeigen Sie Assets mit einem Eigenschaftswert an, der eine bestimmte Zeichenfolge enthält (wie: title=Basel Meeting Room)

title:&quot;Meeting&quot;;

* So zeigen Sie Assets an, die eine bestimmte Zeichenfolge enthalten und einen bestimmten Eigenschaftswert aufweisen (wie die Suche nach der Zeichenfolge „Adobe“ in Assets mit title=John Doe)

&amp;ast;Adobe&amp;ast; title:&quot;John Doe &quot;OR title:&quot;John Doe&quot; &amp;ast;Adobe&amp;ast;

>[!NOTE]
>
>Die Eigenschaften path, limit, size und orderby können nicht mit einer anderen Eigenschaft ORed werden.
>
>Das Keyword für eine von einem Benutzer erstellte Eigenschaft ist ihre Feldbeschriftung im Eigenschafteneditor in Kleinbuchstaben und ohne Leerzeichen.

>[!NOTE]
>
>Wenn Sie eine JCR-Abfrage schreiben, um nur nach Unter-Assets zu suchen, werden auch die übereinstimmenden referenzierten Assets zusammen mit den übereinstimmenden Unter-Assets angezeigt.

Die Volltextsuche unterstützt auch Operatoren wie -, ^ usw. Um diese Buchstaben als alphabetische Zeichenfolgen zu suchen, setzen Sie den Suchausdruck in doppelte Anführungszeichen. Verwenden Sie z. B. „Notebook - Schönheit“ statt Notebook - Schönheit.

## Verstärken der Suche {#boosting-search}

Sie können die Relevanz von Keywords für bestimmte Assets verbessern, um die auf Keywords basierenden Suchen zu optimieren. D. h. die Bilder, für die Sie bestimmte Keywords festlegen, erscheinen bei der Suche nach diesen Keywords oben in den Suchergebnissen.

1. Öffnen Sie in der Assets-Benutzeroberfläche die Eigenschaftenseite für das Asset, für das Sie einen Suchbegriff bewerben möchten.
1. Wechseln Sie zu **[!UICONTROL Erweitert]** Registerkarte und klicken/tippen **[!UICONTROL Hinzufügen]** under **[!UICONTROL Für Suchbegriffe erhöhen]**.

   ![lift_for_search](assets/elevate_for_search.png)

1. Geben Sie im Feld **[!UICONTROL Suche priorisieren]** ein Keyword ein, für den Sie die Bildsuche optimieren möchten, und klicken oder tippen Sie anschließend auf **[!UICONTROL Hinzufügen]**. Geben Sie bei Bedarf mehrere Suchbegriffe auf die gleiche Weise an.

   ![add_search_word](assets/add_search_word.png)

1. Klicken/tippen Sie auf **[!UICONTROL Speichern und schließen]**.
1. Suchen Sie mithilfe des OmniSearch-Felds nach dem Suchbegriff. Das Asset, für das Sie diesen Suchbegriff beworben haben, wird unter den Top-Suchergebnissen angezeigt.
