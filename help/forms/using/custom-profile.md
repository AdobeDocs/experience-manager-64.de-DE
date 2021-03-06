---
title: Erstellen eines benutzerdefinierten Profils für HTML5-Formulare
seo-title: Creating a custom profile for HTML5 forms
description: Ein HTML5-Formularprofil ist ein Ressourcenknoten in Apache Sling. Es enthält eine benutzerdefinierte Version von HTML5-Formularen-Render-Diensten.
seo-description: A HTML5 forms profile is a resource node in Apache Sling. It represents a customized version of HTML5 forms Render service.
uuid: b9938280-a92c-4dde-b465-04372db3ca8d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 9cd22244-9aa6-4b5f-96cf-c9cb3d6f9c8a
feature: Mobile Forms
exl-id: 4630c43f-5b47-435c-8ce5-b4e0d986ec02
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 63%

---

# Erstellen eines benutzerdefinierten Profils für HTML5-Formulare {#creating-a-custom-profile-for-html-forms}

Ein Profil ist ein Ressourcenknoten in [Apache Sling](https://sling.apache.org/). Es enthält eine benutzerdefinierte Version des HTML5-Formularen-Render-Dienstes. Sie können den HTML5 forms Rendition-Dienst verwenden, um Erscheinungsbild, Verhalten und Interaktionen der HTML5-Formulare anzupassen. Ein Profilknoten ist in der `/content` Ordner im JCR-Repository. Sie können den Knoten direkt unter dem `/content` Ordner oder Unterordner des `/content` Ordner.

Der Profilknoten hat die **sling:resourceSuperType**-Eigenschaft und der Standardwert ist **xfaforms/profile**. Das Render-Skript für den Knoten ist unter /libs/xfaforms/profile verfügbar.

Die Sling-Skripte sind JSP-Skripte. Diese JSP-Skripte dienen als Container für den HTML-Code für das angeforderte Formular und die erforderlichen JS-/CSS-Artefakte. Die Sling-Skripte werden auch als **Profil-Renderer-Skripte bezeichnet.** Der Profil-Renderer ruft den Forms OSGi-Dienst auf, um das angeforderte Formular wiederzugeben.

Das Profilskript befindet sich in html.jsp und html.POST.jsp für GET- und POST-Anfragen. Sie können eine oder mehrere Dateien kopieren und verändern, um Ihre Anpassungen zu überschreiben. Nehmen Sie keine ersetzenden Änderungen vor, die Patch-Aktualisierung überschreibt solche Änderungen.

Ein Profil enthält verschiedenen Module. Die Module sind formRuntime.jsp, config.jsp, toolbar.jsp, formBody.jsp, nav_footer.jsp und footer.jsp.

## formRuntime.jsp {#formruntime-jsp-br}

Die formRuntime.jsp-Module enthalten Verweise auf die Client-Bibliotheken. Sie stellen außerdem Methoden dar, um Gebietsschema-Informationen von einer Anforderung zu extrahieren und lokalisierte Nachrichten in die Anforderung einzufügen. Sie können eigene benutzerdefinierte JavaScript-Bibliotheken oder -Stile in die formRuntime.jsp aufnehmen.

## config.jsp {#config-jsp}

Das config.jsp-Modul enthält verschiedene Konfigurationen wie Protokollierung, Proxy-Dienste und Verhaltensversion. Sie können Ihre eigene benutzerdefinierte Konfiguration und das benutzerdefinierte Widget zum config.jsp-Modul hinzufügen. Sie können auch Konfigurationen wie die benutzerdefinierte Widget-Registrierung zum config.jsp-Modul hinzufügen.

## toolbar.jsp {#toolbar-jsp}

Die toolbar.jsp enthält Code zum Erstellen einer farbigen Symbolleiste. Um die Symbolleiste zu entfernen, müssen Sie toolbar.jsp aus der html.jsp entfernen.

## formBody.jsp {#formbody-jsp}

Das formBody.jsp-Modul dient zur HTML-Darstellung des XFA-Formulars.

## nav_footer.jsp {#nav-footer-jsp}

Zunächst rendert das HTML5-Formular nur die erste Seite des Formulars. Wenn ein Benutzer das Formular scrollt, wird der Rest des Formulars geladen. Dadurch wird der Ladevorgang verkürzt. Die Komponente „nav_footer.jsp“ enthält alle Stile und erforderlichen Elemente, um das schrittweise Laden der Seiten beim Scrollen zu erleichtern.

## footer.jsp {#footer-jsp}

Das Modul „footer.jsp“ ist leer. Damit können Sie Skripte hinzufügen, die nur für Benutzerinteraktionen verwendet werden.

## Erstellen von benutzerdefinierten Profilen {#creating-custom-profiles}

Um ein benutzerdefiniertes Profil zu erstellen, führen Sie die folgenden Schritte aus:

### Profilknoten erstellen {#create-profile-node}

1. Navigieren Sie zur CRX DE-Schnittstelle unter der URL: `https://[server]:[port]/crx/de` und melden Sie sich mit Administratorberechtigungen bei der Benutzeroberfläche an.

1. Im linken Fensterbereich navigieren Sie zum Speicherort: */content/xfaforms/profiles*.

1. Kopieren Sie „node default“ und fügen Sie den Knoten in einen anderen Ordner (*/content/profiles*) mit dem Namen *hrform* ein.

1. Wählen Sie den neuen Knoten *hrform* und fügen Sie eine String-Eigenschaft hinzu: *sling:resourceType* mit dem Wert: *hrform/demo*.

1. Klicken Sie im Symbolleistenmenü auf Alle speichern, um die Änderungen zu speichern.

### Das Profil-Renderer-Skript erstellen {#create-the-profile-renderer-script}

Nachdem Sie ein benutzerdefiniertes Profil erstellt haben, fügen Sie Render-Informationen zu diesem Profil hinzu. Nach Erhalt einer Anfrage für das neue Profil prüft CRX das Vorhandensein des Ordners „/apps“, damit die JSP-Seite wiedergegeben werden kann. Erstellen Sie die JSP-Seite im Ordner „/apps“.

1. Navigieren Sie im linken Bereich zum `/apps` Ordner.
1. Klicken Sie mit der rechten Maustaste auf die `/apps` Ordner erstellen und einen Ordner mit dem Namen erstellen **hrform**.
1. Im **hrform** Ordner erstellen Sie einen Ordner mit dem Namen **Demo**.
1. Klicken Sie auf die Schaltfläche **Alle speichern**.
1. Navigieren Sie zu `/libs/xfaforms/profile/html.jsp` und kopieren Sie den Knoten **html.jsp**.
1. Einfügen **html.jsp** Knoten in `/apps/hrform/demo` Ordner, der oben mit demselben Namen erstellt wurde **html.jsp** und klicken Sie auf **Speichern**.
1. Wenn Sie andere Profil-Skript-Komponenten haben, führen Sie die Schritte 1-6 aus, um die Komponenten in den Ordner „/apps/hrform/demo“ zu kopieren.

1. Um zu überprüfen, ob das Profil erstellt wurde, öffnen Sie die URL . `https://[server]:[port]/content/xfaforms/profiles/hrform.html`

Um Ihre Formulare zu überprüfen,[ Importieren Sie Ihre Formulare ](/help/forms/using/get-xdp-pdf-documents-aem.md)aus Ihrem lokalen Dateisystem in AEM Forms und[ zeigen Sie eine Vorschau des Formulars](/help/forms/using/previewing-forms.md) in der Autoreninstanz des AEM-Servers an.
