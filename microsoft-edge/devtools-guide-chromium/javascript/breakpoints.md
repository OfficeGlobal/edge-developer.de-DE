---
title: Anhalten des Codes mit Haltepunkten in Microsoft Edge devtools
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 03/18/2020
ms.topic: article
ms.prod: microsoft-edge
keywords: Microsoft Edge, Web-Entwicklung, F12-Tools, devtools
ms.openlocfilehash: 2afa4b7dbe96b65747ec17b147f0a82c16efa288
ms.sourcegitcommit: ecdc4287fa25a18cb4ddcaf43fcce3b396c3314c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2020
ms.locfileid: "10581803"
---
<!-- Copyright Kayce Basques 
   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at
       https://www.apache.org/licenses/LICENSE-2.0
   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->  







# Anhalten des Codes mit Haltepunkten in Microsoft Edge devtools   



Verwenden Sie Haltepunkte, um Ihren JavaScript-Code anzuhalten.  In diesem Leitfaden werden die einzelnen Typen von Haltepunkten erläutert, die in devtools zur Verfügung stehen, sowie Informationen dazu, wann und wie die einzelnen Typen festzulegen sind.  Eine praktische Einführung in den Debuggingprozess finden Sie unter [Erste Schritte mit dem Debuggen von JavaScript in Microsoft Edge devtools][DevtoolsJavascriptIndex].  

## Übersicht über die Verwendung der einzelnen Haltepunkttypen   

Der bekannteste Breakpoint-Typ ist "Codezeile".  Es ist jedoch möglich, dass die festgelegten Code Haltepunkte nicht besonders effizient sind, wenn Sie nicht genau wissen, wo Sie suchen müssen, oder wenn Sie mit einer umfangreichen CodeBase arbeiten.  Sie können beim Debuggen Zeit sparen, indem Sie wissen, wie und wann die anderen Arten von Haltepunkten verwendet werden.  

| Breakpoint-Typ | Verwenden Sie diese Taste, wenn Sie anhalten möchten...  |  
|:--- |:--- |  
| [Codezeile](#line-of-code-breakpoints) | In einem exakten Codebereich.  |  
| [Bedingte Codezeile](#conditional-line-of-code-breakpoints) | In einem exakten Codebereich, aber nur, wenn eine andere Bedingung wahr ist.  |  
| [DOM](#dom-change-breakpoints) | Auf dem Code, der einen bestimmten DOM-Knoten ändert oder entfernt, oder die untergeordneten Elemente.  |  
| [XMLHttpRequest](#xhrfetch-breakpoints) | Wenn eine XMLHttpRequest-URL ein Zeichenfolgenmuster enthält.  |  
| [Ereignis-Listener](#event-listener-breakpoints) | Auf dem Code, der nach einem Ereignis ausgeführt wird, beispielsweise `click` , wird ausgeführt.  |  
| [Ausnahme](#exception-breakpoints) | In der Codezeile, die eine abgefangene oder nicht abgefangene Ausnahme auslöst.  |  
| [Funktion](#function-breakpoints) | Jedes Mal, wenn ein bestimmter Befehl, eine bestimmte Funktion oder Methode ausgeführt wird.  |  

## Haltepunkte für die Code Zeile   

Verwenden Sie einen Haltepunkt für die Codezeile, wenn Sie den genauen Codebereich kennen, den Sie untersuchen müssen.  DevTools wird **immer** angehalten, bevor diese Codezeile ausgeführt wird.  

So setzen Sie einen Code Haltepunkt in devtools:  

1.  Klicken Sie auf die Registerkarte **Quellen** .  
1.  Öffnen Sie die Datei, die die Codezeile enthält, für die Sie eine Unterbrechung durchführen möchten.  
1.  Wechseln Sie zur Codezeile.  
1.  Links neben der Codezeile befindet sich die Spalte "Zeile".  Klicken Sie darauf.  Neben der Spalte "Zeile Nummer" wird ein rotes Symbol angezeigt.  

> ##### Abbildung1  
> Ein in Zeile 30 eingestellter Haltepunkt für den Code  
> ![Ein Haltepunkt für eine Codezeile][ImageLocBreakpoint]  

### Haltepunkte für die Code Zeile im Code   

Führen `debugger` Sie die Methode aus dem Code aus, um in dieser Zeile anzuhalten.  Dies entspricht einem [Zeile-zu-Code-Haltepunkt](#line-of-code-breakpoints), mit der Ausnahme, dass der Haltepunkt im Code festgesetzt wird, nicht auf der devtools-Benutzeroberfläche.  

```javascript
console.log('a');
console.log('b');
debugger;
console.log('c');
```  

### Bedingte Zeile-für-Code-Haltepunkte   

Verwenden Sie einen bedingten Code Haltepunkt, wenn Sie den genauen Codebereich kennen, den Sie untersuchen müssen, aber nur anhalten möchten, wenn eine andere Bedingung wahr ist.  

So setzen Sie einen bedingten Haltepunkt für eine bedingte Codezeile:  

1.  Klicken Sie auf die Registerkarte **Quellen** .  
1.  Öffnen Sie die Datei, die die Codezeile enthält, für die Sie eine Unterbrechung durchführen möchten.  
1.  Wechseln Sie zur Codezeile.  
1.  Links neben der Codezeile befindet sich die Spalte "Zeile".  Klicken Sie mit der rechten Maustaste auf die Leitungsnummer.  
1.  Wählen Sie **bedingter Haltepunkt hinzufügen**aus.  Unterhalb der Codezeile wird ein Dialogfeld angezeigt.  
1.  Geben Sie Ihre Bedingung in das Dialogfeld ein.  
1.  Drücken Sie `Enter` , um den Haltepunkt zu aktivieren.  Ein Symbol neben der Spalte "Zeile"  

> ##### Abbildung2  
> Ein bedingter Zeile-Code-Haltepunkt, der auf Zeile 34 gesetzt ist  
> ![Ein bedingter Zeile-Code-Haltepunkt][ImageConditionalLocBreakpoint]  

### Verwalten von Code Haltepunkten   

Verwenden Sie den Bereich **Haltepunkte** , um Code Haltepunkte an einer einzelnen Position zu deaktivieren oder zu entfernen.  

> ##### Abbildung 3  
> Der **Haltepunkt** -Panel mit zwei Zeile-zu-Code-Haltepunkten: eine Zeile mit einem `16` `get-started.js` anderen Online `33`  
> ![Der Haltepunkt-Panel][ImageBreakpointsPanel]  

*   Aktivieren Sie das Kontrollkästchen neben einem Eintrag, um diesen Haltepunkt zu deaktivieren.  
*   Klicken Sie mit der rechten Maustaste auf einen Eintrag, um diesen Haltepunkt zu entfernen.  
*   Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle im Bereich **Haltepunkte** , um alle Haltepunkte zu deaktivieren, alle Haltepunkte zu deaktivieren oder alle Haltepunkte zu entfernen.  Das Deaktivieren aller Haltepunkte entspricht der Deaktivierung der einzelnen Haltepunkte.  Durch die Deaktivierung aller Haltepunkte wird devtools angewiesen, alle Zeile-zu-Code-Haltepunkte zu ignorieren, aber auch den aktivierten Zustand beizubehalten, damit sich jeder in demselben Zustand wie zuvor befindet, wenn Sie ihn wieder aktivieren.  

> ##### Abbildung4  
> Deaktivierte Haltepunkte im Bereich " **Haltepunkte** " sind deaktiviert und transparent.  
> ![Deaktivierte Haltepunkte im Bereich "Haltepunkte"][ImageDeactivatedBreakpoints]  

## Dom-Änderungs Haltepunkte   

Verwenden Sie einen Dom-Änderungs Haltepunkt, wenn Sie den Code anhalten möchten, durch den ein DOM-Knoten oder die untergeordneten Elemente geändert werden.  

So setzen Sie einen Dom-Änderungs Haltepunkt:  

1.  Klicken Sie auf die Registerkarte **Elemente** .  
1.  Wechseln Sie zu dem Element, für das Sie den Haltepunkt festlegen möchten.  
1.  Klicken Sie mit der rechten Maustaste auf das Element.  
1.  Zeigen Sie **mit der Maus auf Umbruch**, und wählen Sie dann **Strukturänderungen**, **Attributänderungen**oder **Knoten Entfernung**aus.  

> ##### Abbildung5  
> Das Kontextmenü zum Erstellen eines DOM-Änderungs Haltepunkts  
> ![Das Kontextmenü zum Erstellen eines DOM-Änderungs Haltepunkts][ImageDomChangeBreakpoint]  

### Typen von Dom-Änderungs Haltepunkten   

*   Teil **Strukturänderungen**.  Wird ausgelöst, wenn ein untergeordnetes Element des aktuell ausgewählten Knotens entfernt oder hinzugefügt oder der Inhalt eines untergeordneten Elements geändert wird.  Wird nicht für Änderungen an einem Attribut des untergeordneten Knotens oder für Änderungen am aktuell ausgewählten Knoten ausgelöst.  

*   Attribut **Änderungen**: wird ausgelöst, wenn ein Attribut auf dem aktuell ausgewählten Knoten hinzugefügt oder entfernt wird oder wenn sich ein Attributwert ändert.  

*   **Knoten Entfernung**: wird ausgelöst, wenn der aktuell ausgewählte Knoten entfernt wird.  

## XMLHttpRequest/FETCH-Haltepunkte   

Verwenden Sie einen XMLHttpRequest-Haltepunkt, wenn Sie unterbrechen möchten, wenn die Anforderungs-URL eines XMLHttpRequest eine angegebene Zeichenfolge enthält.  DevTools wird in der Codezeile angehalten, in der die XMLHttpRequest die `send()` Methode ausführt.  

> [!NOTE]
> Dieses Feature funktioniert auch mit [Fetch-API-][MDNFetchApi] Anforderungen.  

Wenn dies hilfreich ist, können Sie beispielsweise feststellen, dass die Seite eine falsche URL anfordert, und Sie möchten schnell den AJAX-oder Fetch-Quellcode finden, der die falsche Anforderung verursacht.  

So setzen Sie einen XMLHttpRequest-Haltepunkt:  

1.  Klicken Sie auf die Registerkarte **Quellen** .  
1.  Erweitern Sie den Bereich **XMLHttpRequest-Haltepunkte** .  
1.  Klicken Sie auf **Haltepunkt hinzufügen**.  
1.  Geben Sie die Zeichenfolge ein, die Sie aufheben möchten.  DevTools wird angehalten, wenn diese Zeichenfolge an einer beliebigen Stelle in einer XMLHttpRequest-Anforderungs-URL vorhanden ist.  
1.  Drücken Sie `Enter` , um zu bestätigen.  

> ##### Abbildung6  
> Erstellen eines XMLHttpRequest-Haltepunkts in den **XMLHttpRequest-Haltepunkten** für jede Anforderung, die `org` in der URL enthalten ist  
> ![Erstellen eines XMLHttpRequest-Haltepunkts][ImageXhrBreakpoint]  

## Ereignis-Listener-Haltepunkte 

Verwenden Sie Ereignis-Listener-Haltepunkte, wenn Sie den Ereignislistener-Code anhalten möchten, der nach dem Auslösen eines Ereignisses ausgeführt wird.  Sie können bestimmte Ereignisse, beispielsweise `click` oder Kategorien von Ereignissen, wie alle Mausereignisse auswählen.  

1.  Klicken Sie auf die Registerkarte **Quellen** .  
1.  Erweitern Sie den Bereich **Ereignislistener-Haltepunkte** .  DevTools zeigt eine Liste der Ereigniskategorien, wie etwa **Animationen**, an.  
1.  Überprüfen Sie eine dieser Kategorien, um zu pausieren, wenn ein Ereignis aus dieser Kategorie ausgelöst wird, oder erweitern Sie die Kategorie, und überprüfen Sie ein bestimmtes Ereignis.  

> ##### Abbildung7  
> Erstellen eines Ereignis-Listener-Haltepunkts für `deviceorientation`  
> ![Erstellen eines Ereignis-Listener-Haltepunkts][ImageEventListenerBreakpoint]  

## Ausnahme Haltepunkte   

Verwenden Sie Ausnahme Haltepunkte, wenn Sie in der Codezeile anhalten möchten, die eine abgefangene oder nicht abgefangene Ausnahme auslöst.  

1.  Klicken Sie auf die Registerkarte **Quellen** .  
1.  Klicken Sie auf **bei** Ausnahmen anhalten ![ für Ausnahmen anhalten ][ImagePauseOnExceptionsIcon] .  Das Symbol wird blau, wenn es aktiviert ist.  
    
    > ##### Abbildung8  
    > Schaltfläche " **auf Ausnahmen pausieren** "  
    > ![Schaltfläche "auf Ausnahmen pausieren"][ImagePauseExceptionsHighlight]  

1.  **Optional**. Aktivieren Sie das Kontrollkästchen **auf abgefangene Ausnahmen anhalten** , wenn Sie zusätzlich zu den nicht abgefangenen Ausnahmen auch auf abgefangene Ausnahmen anhalten möchten.  

> ##### Abbildung 9  
> Bei einer nicht abgefangenen Ausnahme angehalten  
> ![Bei einer nicht abgefangenen Ausnahme angehalten][ImageUncaughtException]  

## Funktionshaltepunkte   

Führen Sie die Methode aus, `debug(method)` wobei `method` der Befehl, die Funktion oder die Methode, die Sie debuggen möchten, ist, wenn Sie anhalten möchten, wenn eine bestimmte Funktion ausgeführt wird.  Sie können `debug()` in Ihren Code einfügen (wie eine `console.log()` Anweisung) oder die Methode über die devtools-Konsole ausführen.  `debug()` entspricht dem Festlegen eines [Haltepunkts für die Code Zeile](#line-of-code-breakpoints) in der ersten Zeile der Funktion.  

```javascript
function sum(a, b) {
    let result = a + b; // DevTools pauses on this line.
    return result;
}
debug(sum); // Pass the function object, not a string.
sum();
```  

### Sicherstellen, dass sich die Zielfunktion im Bereich befindet   

DevTools löst a `ReferenceError` aus, wenn sich die zu debuggende Funktion nicht im Bereich befindet.  

```javascript
(function () {
    function hey() {
        console.log('hey');
    }
    function yo() {
        console.log('yo');
    }
    debug(yo); // This works.
    yo();
})();
debug(hey); // This does not work.  hey() is out of scope.
```  

Die Sicherstellung, dass die Zielfunktion im Bereich liegt, ist schwierig, wenn Sie die `debug()` Methode über die devtools-Konsole ausführen.  Hier ist eine Strategie:  

1.  Setzen Sie einen [Haltepunkt für die Codezeile](#line-of-code-breakpoints) an einer beliebigen Stelle, an der sich die Funktion im Bereich befindet.
1.  Auslösen des Haltepunkts  
1.  Führen `debug()` Sie die Methode in der devtools-Konsole aus, während der Code weiterhin auf dem Haltepunkt für die Code Zeile angehalten wird.  

 



<!-- image links -->  

[ImagePauseOnExceptionsIcon]: /microsoft-edge/devtools-guide-chromium/media/pause-on-exceptions-icon.msft.png  

[ImageLocBreakpoint]: /microsoft-edge/devtools-guide-chromium/media/javascript-sources-page-js-breakpoint-30.msft.png "Abbildung 1: ein Haltepunkt für eine Codezeile"  
[ImageConditionalLocBreakpoint]: /microsoft-edge/devtools-guide-chromium/media/javascript-sources-page-js-conditional-breakpoint.msft.png "Abbildung 2: ein bedingter Zeile-Code-Haltepunkt"  
[ImageBreakpointsPanel]: /microsoft-edge/devtools-guide-chromium/media/javascript-sources-page-js-breakpoints-16-33.msft.png "Abbildung 3: der Abschnitt "Haltepunkte""  
[ImageDeactivatedBreakpoints]: /microsoft-edge/devtools-guide-chromium/media/javascript-sources-page-js-breakpoints-deactivate-breakpoints.msft.png "Abbildung 4: deaktivierte Haltepunkte im Bereich "Haltepunkte""  
[ImageDomChangeBreakpoint]: /microsoft-edge/devtools-guide-chromium/media/javascript-elements-break-on-subtree-modifications.msft.png "Abbildung 5: Kontextmenü zum Erstellen eines DOM-Änderungs Haltepunkts"  
[ImageXhrBreakpoint]: /microsoft-edge/devtools-guide-chromium/media/javascript-sources-page-js-xhr-fetch-breakpoints-org.msft.png "Abbildung 6: Erstellen eines XMLHttpRequest-Haltepunkts"  
[ImageEventListenerBreakpoint]: /microsoft-edge/devtools-guide-chromium/media/javascript-sources-page-js-event-listener-breakpoints-device-deviceorientation.msft.png "Abbildung 7: Erstellen eines Ereignis-Listener-Haltepunkts"  
[ImagePauseExceptionsHighlight]: /microsoft-edge/devtools-guide-chromium/media/javascript-sources-page-js-pause-on-exceptions.msft.png "Abbildung 8: Schaltfläche "auf Ausnahmen pausieren""  
[ImageUncaughtException]: /microsoft-edge/devtools-guide-chromium/media/javascript-sources-page-js-paused-on-exception.msft.png "Abbildung 9: angehalten für eine nicht abgefangene Ausnahme"  

<!-- links -->  

[DevtoolsJavascriptIndex]: index.md "Erste Schritte mit dem Debuggen von JavaScript in Microsoft Edge devtools"  

[MDNFetchApi]: https://developer.mozilla.org/docs/Web/API/Fetch_API "FETCH-API | MDN"  

> [!NOTE]
> Teile dieser Seite sind Änderungen, die auf der [von Google erstellten und freigegebenen][GoogleSitePolicies] Arbeit basieren und gemäß den in der [Creative Commons Attribution 4,0 International-Lizenz][CCA4IL]beschriebenen Begriffen verwendet werden.  
> Die ursprüngliche Seite befindet sich [hier](https://developers.google.com/web/tools/chrome-devtools/javascript/breakpoints) und wird von [Kayce Basken][KayceBasques] (Technical Writer, Chrome devtools & Lighthouse) erstellt.  
[![Creative Commons-Lizenz][CCby4Image]][CCA4IL]  
Diese Arbeit unterliegt einer [Creative Commons Attribution 4.0 International License][CCA4IL].  

[CCA4IL]: https://creativecommons.org/licenses/by/4.0  
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png  
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies  
[KayceBasques]: https://developers.google.com/web/resources/contributors/kaycebasques  
