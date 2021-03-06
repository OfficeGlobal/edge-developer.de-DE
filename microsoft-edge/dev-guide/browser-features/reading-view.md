---
ms.assetid: 2bc29371-4f2e-4b59-a588-30b107d751f6
description: Schauen Sie sich an, wie Microsoft Edge eine Leseansicht für Webseiten bietet, um Add-Free-Lesefunktionen zu ermöglichen.
title: Dev-Leitfaden – Leseansicht
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 01/15/2020
ms.topic: article
ms.prod: microsoft-edge
keywords: Edge, Web-Entwicklung, HTML, CSS, JavaScript, Entwickler
ms.openlocfilehash: e84edb5cc29b644939895f2996c50f3b4ec23379
ms.sourcegitcommit: 6860234c25a8be863b7f29a54838e78e120dbb62
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2020
ms.locfileid: "10566766"
---
# Leseansicht

Microsoft Edge bietet eine *Leseansicht* für eine optimierte, Buch ähnliche Leseerfahrung von Webseiten ohne Ablenkung von nicht miteinander verknüpften oder anderen sekundären Inhalten auf der Seite. Die Leseansicht kann über die Schaltfläche **Leseansicht** (Buchsymbol) auf der **Adressleiste** (oder mit **STRG**+  +  **UMSCHALT**  +  **R**) ein-oder ausgeblendet werden. In der Leseansicht werden die folgenden Metadaten von einer Seite extrahiert:

* Title
* Autor
* Date
* Herausgeber
* Dominantes Bild (e)
* Beschriftungen der dominanten Bilder
* Sekundäre Bilder
* Haupt Textinhalt der Seite
* Copyright

Benutzer können dann den Seiten Kontrast und den Schriftgrad im Microsoft Edge **Settings** -Panel anpassen.

## Extraktion von Metadaten


Hier finden Sie Details zu den Seiten Metadaten, die von der Leseansicht gerendert werden.

### Title

So stellen Sie sicher, dass die Leseansicht den Titel Ihres Artikels rendert:

* Einfügen eines **Titel** Elements in die Kopfzeile
* Einfügen eines Meta-Tags `name="title"`
* Vergleichen Sie den Titeltext in Ihrem Artikel Text mit der Inhaltszeichenfolge Ihres Meta-Tags. Pipes `|` in der Inhaltszeichenfolge verhindern, dass die Leseransicht aktiv wird, versuchen Sie stattdessen, hypens zu verwenden `-` .

### Autor

In der Leseansicht wird nach einem Element gesucht `class = "byline-name"` . Bewährte Methode besteht darin, den Autorennamen hinter dem Titel und vor dem Artikel Text zu platzieren.

```html
<div class="byline-name">Author name</div>
```

### Date

In der Leseansicht werden der Herausgeber und die Datumsinformationen in derselben Zeile zusammen mit zusätzlicher Formatierung gerendert, um diese Informationen hervorzuheben. Das Veröffentlichungsdatum des Artikels wird exakt so gerendert, wie es in der Zeichenfolge angezeigt wird. Die Leseansicht wird nicht in ein bestimmtes Datumsformat konvertiert.

Wenn Sie über ein Datum in Ihrem Artikel Text verfügen und es in der Leseansicht rendern möchten, weisen Sie das Element mit dem Datum der Klasse zu `'dateline'` :

```html
<div class="dateline"> Wednesday, September 18, 2013 7:38 AM </div>
```

Verwenden Sie das Meta-Tag, wenn Sie nicht über ein Datum im Artikel Text verfügen, aber die Leseansicht zum Rendern des Datums verwenden möchten `name='displaydate'` :

```html
<meta name="displaydate" content=" Wednesday, September 18, 2013 7:38 AM ">
```

### Herausgeber

In der Leseansicht wird nach dem *Open Graph* -Protokoll gesucht `"og:site_name"` , um die Herausgeberinformationen zu rendern. Darüber hinaus sucht Sie nach `source_organization` und `publisher` Attribute in einem beliebigen HTML-Tag als sekundärer Indikator für Herausgeberinformationen auf der Seite. Der Text des Herausgebers wird mit der URL der Seite über den Hyperlink-Stil "Leseansicht" verknüpft.

```html
<meta content="Name of organization source" property="og:site_name">
```

### Images

In der Leseansicht werden die meisten RAW-Bilder mit Breite >= 400px und Seitenverhältnis >= 1/3 und =< 3,0 erfasst. Bilder, die diese Dimensionen nicht erfüllen, werden möglicherweise weiterhin extrahiert, wie Bilder, die kleiner als 400px sind, aber über Beschriftungen verfügen. Das erste geeignete Bild wird zum dominanten Bild des Artikels. Das dominante Bild wird als erster Teil des Inhalts gerendert und erhält die volle Spaltenbreite. Alle folgenden Bilder werden als Inline Bilder innerhalb des Artikels gerendert.

### Beschriftungen

Bewährte Methode ist das Platzieren von Bildern in [Abbildungs](https://msdn.microsoft.com/library/gg593038(v=vs.85).aspx) Tags mit nicht mehr als zwei geschachtelten [figcaption](https://msdn.microsoft.com/library/gg593037(v=vs.85).aspx) -Tags.

### Textkörper

Um sicherzustellen, dass der gesamte Textkörper Ihrer Seite in der Leseansicht erfasst wird, hilft es, den größten Teil des Artikel Texts auf den gleichen Schriftgrad und die gleiche Dom-Tiefe zu beschränken. Der Leseansicht-Algorithmus ermöglicht eine gewisse Abweichung von dieser Regel, damit Publisher die Freiheit haben, Zeilen oder Wörter hervorheben zu können.

### Copyright

Leseansicht extrahiert und zeigt Copyright Informationen an, die durch Metatags gekennzeichnet `name = "copyright"` sind, oder wenn keine Meta-Tag-Informationen vorhanden sind, ein Textknoten, der das Copyright (**©**)-Symbol enthält. In der Leseansicht werden die Copyright Informationen am Ende des Haupttexts des Artikels angezeigt, wobei ein kleinerer Schriftgrad als der Hauptteil des Texts formatiert ist.

```html
<meta name="copyright" content="Your copyright information">
```

## Deaktivieren der Leseansicht


Wenn Sie der Meinung sind, dass Ihre Inhalte für die Leseansicht nicht geeignet sind, können Sie das folgende Meta-Tag verwenden, um dieses Feature zu deaktivieren:

```html
<meta name="IE_RM_OFF" content="true">
```

Mit dieser Kategorie wird die Schaltfläche " **Leseansicht** " in der Adressleiste nicht angezeigt, wenn die Benutzer Ihre Seite anzeigen.
