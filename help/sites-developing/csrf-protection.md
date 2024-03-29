---
title: Das CSRF Protection Framework
seo-title: The CSRF Protection Framework
description: Das Framework verwendet Token, um sicherzustellen, dass die Client-Anfrage legitim ist
seo-description: The framework makes use of tokens to guarantee that the client request is legitimate
uuid: 7cb222ba-fc7a-46ee-8b49-a5f39a53580b
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: f453427d-c813-48b7-b2f9-adadea39c67d
exl-id: 533c348e-517f-4d70-a89c-bfc87f71a633
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 76%

---

# Das CSRF Protection Framework {#the-csrf-protection-framework}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Zusätzlich zum Apache Sling Referrer-Filter bietet Adobe auch ein neues CSRF Protection Framework zum Schutz vor Angriffen dieser Art.

Das Framework verwendet Tokens, um sicherzustellen, dass die Client-Anfrage legitim ist. Die Token werden generiert, wenn das Formular an den Client gesendet und validiert wird, wenn das Formular an den Server zurückgesendet wird.

>[!NOTE]
>
>Für anonyme Benutzer gibt es in den Veröffentlichungsinstanzen keine Token.

## Voraussetzungen {#requirements}

### Abhängigkeiten {#dependencies}

Jede Komponente, die sich auf die Abhängigkeit `granite.jquery` stützt, profitiert automatisch vom CSRF Protection Framework. Wenn dies für eine Ihrer Komponenten nicht der Fall ist, müssen Sie eine Abhängigkeit von `granite.csrf.standalone` deklarieren, bevor Sie das Framework verwenden können.

### Replizieren des Crypto-Schlüssels {#replicating-crypto-keys}

Um die Tokens zu verwenden, müssen Sie die Binärdatei `/etc/keys/hmac` auf allen Instanzen in Ihrer Bereitstellung replizieren. Eine bequeme Möglichkeit, den HMAC-Schlüssel in alle Instanzen zu kopieren, besteht darin, ein Paket zu erstellen, das den Schlüssel enthält, und ihn über Package Manager auf alle Instanzen zu installieren.

>[!NOTE]
>
>Achten Sie darauf, auch die notwendigen [Dispatcher-Konfigurationsänderungen](https://helpx.adobe.com/de/experience-manager/dispatcher/user-guide.html) vorzunehmen, um das CSRF Protection Framework zu verwenden.

>[!NOTE]
>
>Wenn Sie den Manifest-Cache mit Ihrer Web-Anwendung verwenden, stellen Sie sicher, dass Sie „**&amp;ast;**“ zum Manifest hinzufügen, damit das Token die CSRF-Token-Erzeugungsanforderung nicht offline nimmt. Weitere Informationen finden Sie unter diesem [Link](https://www.w3.org/TR/offline-webapps/).
>
>Weitere Informationen zu CSRF-Angriffen und Möglichkeiten, sie abzuschwächen, finden Sie auf der Seite [Cross-Site Request Forgery OWASP](https://owasp.org/www-community/attacks/csrf).
