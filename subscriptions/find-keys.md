---
title: Suchen und Beanspruchen von Product Keys in Visual Studio-Abonnements | Microsoft-Dokumentation
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/11/2019
ms.topic: conceptual
description: Hier erhalten Sie Informationen zum Suchen, Beanspruchen und Exportieren Ihrer Product Keys in Visual Studio-Abonnements.
ms.openlocfilehash: 4efdc118961b6e773e33eb16e40c6e0f09a13dc7
ms.sourcegitcommit: 485881e6ba872c7b28a7b17ceaede845e5bea4fe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2019
ms.locfileid: "68378010"
---
# <a name="finding-and-claiming-product-keys-in-visual-studio-subscriptions"></a>Suchen und Beanspruchen von Product Keys in Visual Studio-Abonnements
In diesem Artikel wird das Suchen, Beanspruchen und Exportieren von Product Keys über https://my.visualstudio.com/productkeys erläutert.  Weitere Informationen zum Aktivieren eines Produkts mit einem Product Key, den Einzelhandels- und Volumenlizenzversionen von Product Keys und den Anspruchseinschränkungen für Product Keys pro Tag finden Sie in der [Übersicht über Product Keys](product-keys.md).

## <a name="locating-and-claiming-product-keys"></a>Suchen nach und Inanspruchnahme von Product Keys
Sie müssen bei Ihrem Visual Studio-Abonnement angemeldet sein, um Ihre Product Keys anzeigen zu können. Einzelne Product Keys können gefunden werden, indem Sie wie im Folgenden dargestellt auf der Seite [Downloads](https://my.visualstudio.com/downloads) auf den blauen Link **Schlüssel abrufen** für ein bestimmtes Produkt klicken.  Sämtliche Schlüssel sind auch zusammengefasst auf der Seite [Product Keys](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) verfügbar. Wenn für ein einzelnes Produkt mehrere Schlüssel vorhanden sind, werden in der Spalte „Hinweise“ Hinweise zum Download angezeigt, die Sie beim Ermitteln des erforderlichen Schlüssels unterstützen sollen.
> [!div class="mx-imgBorder"]
> ![„Schlüssel abrufen“ auf der Seite „Downloads“](_img/product-keys/download-get-key.png)

Einige Produkte fassen mehrere Produkteditionen in einem einzigen Download zusammen. In diesen Fällen wird durch den eingegebenen Product Key festgelegt, welche Edition des Produkts installiert wird.
Einige Schlüssel werden automatisch bereitgestellt, wie z.B. „statische“ Product Keys, die Sie so häufig wie nötig verwenden können, da keine Aktivierung erforderlich ist. Andere Product Keys müssen durch Klicken auf den Link **Schlüssel abrufen** für das entsprechende Produkt in Anspruch genommen werden.

Abhängig vom Produkt ist eine Vielzahl von Schlüsseltypen verfügbar.

### <a name="product-key-types"></a>Product Key-Typen

|    Schlüsseltyp           |    BESCHREIBUNG                                                                                                                                                                                                           |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Nicht zutreffend                    |    Für die Installation dieses Produkts ist kein Schlüssel erforderlich.                                                       |
|    Einzelhandel                     |    Mit Verkaufsschlüsseln sind mehrere Aktivierungen möglich. Sie werden für die Verkaufsversionen des Produkts verwendet. In vielen Fällen sind pro Schlüssel 10 Aktivierungen zulässig. Häufig sind jedoch weitere Aktivierungen auf demselben Computer zulässig.                                                       |
|    Mehrfachaktivierung        |    Ein Mehrfachaktivierungsschlüssel ermöglicht Ihnen die Aktivierung mehrerer Installationen eines Produkts mittels des gleichen Product Keys. Im Allgemeinen werden Mehrfachaktivierungen für Volumenlizenzversionen von Produkten verwendet. In der Regel wird pro Abonnement nur ein Schlüssel für die Mehrfachaktivierung bereitgestellt.    |
|    Statischer Aktivierungsschlüssel    |    Statische Aktivierungsschlüssel werden für Produkte bereitgestellt, für die keine Aktivierung erforderlich ist. Sie können für eine beliebige Anzahl von Installationen verwendet werden.                                                                                                                  |
|    Benutzerdefinierter Product Key                 |    Benutzerdefinierte Product Keys stellen besondere Aktionen oder Informationen zur Aktivierung oder Installation des betreffenden Produkts bereit.                                                                                                                                                                |
|    VA 1.0                     |    Hierbei handelt es sich um Mehrfachaktivierungsschlüssel, ähnlich den MAK-Schlüsseln.                                                                                                                                                                                                 |
|    OEM-Schlüssel                    |    Hierbei handelt es sich um Product Keys für Originalgerätehersteller (Original Equipment Manufacturers, OEM), die Mehrfachaktivierungen zulassen.                                                                                                                                                                       |
|    DreamSpark-Verkaufsschlüssel    |    Diese Verkaufsschlüssel sind für DreamSpark bestimmt und lassen eine einzige Aktivierung zu. DreamSpark-Verkaufsschlüssel werden in Batches ausgegeben und sind primär für die Nutzung durch Schüler und Studierende vorgesehen.                                                                                     |
|    DreamSpark-Lab-Schlüssel         |    Diese Schlüssel für die Verwendung in Laboren sind für DreamSpark-Programme bestimmt und lassen Mehrfachaktivierungen zu. DreamSpark Lab-Schlüssel sind für die Verwendung in Computerlaboren von Universitäten und Hochschulen vorgesehen.                                                                                       |
|    DreamSpark-MAK-Schlüssel         |    Hierbei handelt es sich um MAK-Schlüssel für Kunden von DreamSpark-Programmen.                                                                                                                                                                                                  |
|

Sie können einen Schlüssel von der Downloadseite des Produkts anfordern. Alternativ können Sie auf der Seite [Product Keys](https://my.visualstudio.com/productkeys) nach dem erforderlichen Schlüssel suchen.

### <a name="claiming-product-keys"></a>Inanspruchnahme von Product Keys
Nur Abonnenten mit aktiven Abonnements können Produkte herunterladen und Product Keys in Anspruch nehmen.  Sie können Ihre in Anspruch genommenen Schlüssel von der Seite [Product Keys](https://my.visualstudio.com/productkeys) herunterladen, während Ihr Abonnement aktiv ist.

So nehmen Sie einen Product Key in Anspruch:
1. Melden Sie sich bei Ihrem Visual Studio-Abonnement an.  Sie müssen angemeldet sein, um Produkte herunterladen oder Product Keys in Anspruch nehmen zu können.
2. Klicken Sie auf die Registerkarte [Product Keys](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs).
3. Die Product Keys werden in alphabetischer Reihenfolge nach dem Namen des Produkts aufgelistet.  Sie können den Fensterinhalt bis zum gewünschten Produkt nach unten verschieben oder über die Suchleiste oben auf der Seite nach dem Namen suchen.
> [!div class="mx-imgBorder"]
> ![Nach Product Key suchen](_img/product-keys/search-keys.png)
   
In diesem Beispiel wird die Suchleiste verwendet, um einen Product Key für Visual Studio Enterprise 2019 zu suchen.
Wie Sie sehen können, werden mehrere Versionen aufgeführt.  Es wurde bereits ein Schlüssel für die Visual Studio Enterprise 2019-Versionen 16.0 und 16.1 beansprucht.  Für beide Versionen sind noch weitere Schlüssel unterschiedlicher Typen verfügbar. Beachten Sie, dass Sie in der Spalte **Hinweise** eine kurze Notiz zu den beanspruchten Schlüsseln hinterlassen können.  Diese können Sie zusammen mit dem Datum in der Spalte **Beansprucht** verwenden, um den Überblick über in Anspruch genommene Schlüssel zu behalten.  Sie könnten beispielsweise Notizen machen, wenn Sie die Installation eines Produkts mit dem Schlüssel aktivieren.

### <a name="exporting-your-claimed-keys"></a>Exportieren Ihrer in Anspruch genommenen Schlüssel
Sie können eine Liste mit allen in Anspruch genommenen Schlüsseln exportieren, zusammen mit einer großen Auswahl statischer und anderer Schlüssel, die automatisch mit „In Anspruch genommen“ markiert wurden.

> [!IMPORTANT]
> Wenn Ihr Abonnement abgelaufen ist, können Sie keine neuen Schlüssel mehr in Anspruch nehmen oder Ihre in Anspruch genommenen Schlüssel exportieren.

Klicken Sie zum Exportieren Ihrer Schlüssel einfach ganz rechts auf der Seite „Product Keys“ auf den Link **Alle Schlüssel exportieren**.  Es wird eine XML-Datei mit dem Namen „KeysExport.xml“ erstellt, die Sie öffnen oder speichern können.  Sie müssen die Datei mit einer Anwendung öffnen, die XML-Dateien verarbeiten kann.  Sie können die Datei beispielsweise als schreibgeschützte Arbeitsmappe in Excel öffnen.

## <a name="next-steps"></a>Nächste Schritte
Wenn Sie bereit sind, die Software herunterzuladen und Schlüssel zu verwenden, rufen Sie https://my.visualstudio.com/downloads auf.  Weitere Informationen zum Herunterladen von Software finden Sie in der [Übersicht über Downloads](download-software.md).