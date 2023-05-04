---
title: Trainings-Richtlinien für Smart Content Service
description: Trainieren des AI-Dienstes zum Anwenden von Smart-Tags auf Assets
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: 1c011496-be6e-470b-9da8-48db8c6d1108
contentOwner: AG
discoiquuid: a5aab094-8b2d-4a23-890f-be6f9e5137bd
feature: Tagging,Metadata,Smart Tags
role: User
exl-id: 14241f8d-fd0b-4bcf-b2bb-1d0e52bf7748
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 65%

---

# Trainings-Richtlinien für Smart Content Service {#smart-content-service-training-guidelines}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Um Ihre Markenbilder effektiv mit Tags versehen zu können, erfordert der Smart Content Service, dass die Schulungsbilder bestimmten Richtlinien entsprechen.

## Richtlinien für das Training {#guidelines-for-training}

Um optimale Ergebnisse zu erzielen, sollten Bilder in Ihrem Trainings-Satz den folgenden Richtlinien entsprechen:

**Menge und Größe:****Mindestens 30 Bilder pro Tag**. Mindestens 500 Pixel auf der längeren Seite.

**Kohärenz**: Bilder für ein Tag sollten visuell ähnlich sein.

Es ist beispielsweise nicht empfehlenswert, alle diese Bilder mit einem Tag zu versehen als *my-party* (für das Training), da sie visuell nicht ähnlich sind.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](assets/do-not-localize/coherence.png)

**Abdeckung:** Bei den Trainings-Bildern muss eine ausreichende Vielfalt vorhanden sein. Der Grundgedanke ist, einige Beispiele bereitzustellen, die jedoch verhältnismäßig vielfältig sind, sodass [!DNL Experience Manager] lernt, sich auf die richtigen Dinge zu konzentrieren. Wenn Sie dasselbe Tag auf visuell unähnliche Bilder anwenden, schließen Sie mindestens fünf Beispiele für jeden Typ ein.

Beispiel: Schließen Sie für das Tag *model-down-pose* mehr Trainings-Bilder ein, die dem hervorgehobenen Bild unten ähnlich sind, sodass der Service ähnliche Bilder beim Hinzufügen von Tags genauer identifizieren kann.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](assets/do-not-localize/coverage_1.png)

**Ablenkung/Verdeckung**: Der Service kann besser mit Bildern trainieren, die weniger Ablenkungen enthalten (hervorgehobenen Hintergründe oder Elemente ohne Bezug wie Objekte/Personen neben dem Hauptsubjekt).

Beispiel: Für das Tag *casual-shoe* ist das zweite Bild kein guter Kandidat für das Training.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](assets/do-not-localize/distraction.png)

**Vollständigkeit:** Wenn ein Bild für mehr als ein Tag qualifiziert ist, fügen Sie alle entsprechenden Tags hinzu, bevor Sie das Bild für eine Schulung hinzufügen. Fügen Sie beispielsweise für Tags wie *Regenmantel* und *Modell-Seitenansicht* beide Tags für das entsprechende Asset hinzu, bevor Sie es für die Schulung hinzufügen.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](assets/do-not-localize/completeness.png)

## Einschränkungen {#limitations}

Verbesserte Smart-Tags basieren auf Lernmodellen von Markenbildern und deren Tags. Diese Modelle können Tags nicht immer perfekt identifizieren. Die aktuelle Version des Smart Content Service weist die folgenden Einschränkungen auf:

* Subtile Unterschiede in Bildern können nicht erkannt werden. Beispiel: T-Shirts mit schmalem oder normalem Schnitt.
* Es ist nicht möglich, Tags basierend auf winzigen Mustern/Teilen eines Bildes zu identifizieren. Zum Beispiel Logos auf T-Shirts.
* Tagging wird in den Gebietsschemata unterstützt, in denen [!DNL Experience Manager] unterstützt wird. Eine Liste der Sprachen finden Sie in den [Versionshinweisen für Smart Content Services](/help/release-notes/smart-content-service-release-notes.md).

Um nach Assets mit Smart-Tags (normal oder erweitert) zu suchen, verwenden Sie die Asset-Omni-Suche (Volltextsuche). Es gibt kein separates Suchprädikat für Smart-Tags.

>[!NOTE]
>
>Die Fähigkeit des Smart Content Service, aus Ihren Tags zu lernen und diese Tags auf andere Bilder anzuwenden, hängt von der Qualität der für das Training verwendeten Bilder ab.
>
>Um die bestmöglichen Ergebnisse zu erzielen, empfiehlt Adobe die Verwendung visuell ähnlicher Bilder, um den Service für die einzelnen Tags zu trainieren.
