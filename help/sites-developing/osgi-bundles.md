---
title: OSGi-Bundles
seo-title: OSGI Bundles
description: Tipps zum Verwalten von OSGi-Bundles
seo-description: Tips for managing your OSGi bundles
uuid: 07af7089-a233-4e5b-928c-76ddc0af8839
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 8d3374ac-51dd-4ff5-84c9-495c937ade12
exl-id: 19df20a9-7c89-4dfa-8eca-81c4a14c21ff
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 57%

---

# OSGi-Bundles{#osgi-bundles}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Verwenden der semantischen Versionierung {#use-semantic-versioning}

Die vereinbarten Best Practices für die semantische Versionsnummeriierung finden Sie unter [https://semver.org/](https://semver.org/).

## Betten Sie nicht mehr Klassen und JARs ein, als in OSGi-Bundles unbedingt erforderlich sind {#do-not-embed-more-classes-and-jars-than-strictly-needed-in-osgi-bundles}

Gemeinsame Bibliotheken sollten in separate Bundles zusammengefasst werden. Dadurch können sie in allen Bundles wiederverwendet werden. Beim Umbrechen einer *JAR* in einem OSGi-Bundle überprüfen Sie die Online-Quellen, um festzustellen, ob dies bereits geschehen ist. Einige gängige Stellen, an denen vorhandene Bundle-Wrapper gefunden werden, sind: Apache Felix, Apache Sling, Apache Geronimo, Apache ServiceMix, Eclipse Bundle Recipes und das SpringSource Enterprise Bundle Repository.

## Abhängig von den am wenigsten benötigten Bundle-Versionen {#depend-on-the-lowest-needed-bundle-versions}

Verwenden Sie für Kompilierungszeit-Abhängigkeiten in POM-Dateien immer die niedrigste erforderliche Version, die die API verfügbar macht. Dies ermöglicht eine höhere Abwärtskompatibilität und erleichtert die Backport-Fehlerbehebung bei älteren Versionen.

## Exportieren der Mindestanzahl erforderlicher Pakete aus OSGi-Bundles {#export-a-minimal-set-of-packages-from-osgi-bundles}

Unmittelbar nach dem Exportieren eines Pakets wird eine API erstellt, von der andere Komponenten abhängen. Exportieren Sie so wenig wie möglich und stellen Sie sicher, dass Sie tatsächlich APIs exportieren. Es ist einfacher, eine private Methode oder Klasse öffentlich zu machen, als eine zuvor exportierte Komponente privat zu machen.

Implementierungen sollten immer in einem separaten *impl* Paket. Standardmäßig wird die *maven-bundle-plugin* exportiert alles im Projekt, das keine *impl* im Namen.

## Definieren Sie immer explizit eine semantische Version für jedes exportierte Paket {#always-explicitly-define-a-semantic-version-for-each-package-exported}

Dadurch können sich Nutzer der API an Ihr Entwicklungstempo anpassen. Folgen Sie dabei immer den Best Practices für die semantische Versionierung. Verbraucher der API sind dann immer darüber informiert, mit welchen Änderungen in einer neuen Version zu rechnen ist.

## Angeben von angezeigten Metatyp-Informationen {#include-metatype-information-where-exposed}

Durch Angabe aussagekräftiger Metatyp-Informationen sind Ihre Services und Komponenten in der Felix-Konsole verständlicher. Eine Liste der SCR-Anmerkungen und Attribute finden Sie unter: [https://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html](https://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html).
