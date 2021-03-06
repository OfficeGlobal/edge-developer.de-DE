---
title: Überprüfen von Animationen
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 04/01/2020
ms.topic: article
ms.prod: microsoft-edge
keywords: Microsoft Edge, Web-Entwicklung, F12-Tools, devtools
ms.openlocfilehash: 6466c7f0e1f8680a2429b565e8022d152d05d733
ms.sourcegitcommit: 6860234c25a8be863b7f29a54838e78e120dbb62
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2020
ms.locfileid: "10568277"
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





# Überprüfen von Animationen   



Überprüfen und Ändern von Animationen mit dem Animations Inspektor für Microsoft Edge devtools  

> ##### Abbildung1  
> Animations Inspektor  
> ![Animations Inspektor][ImageAnimationInspector]  

### Zusammenfassung  

*   Zeichnen Sie Animationen auf, indem Sie den Animations Inspektor öffnen.  Der Animations Inspektor erkennt und sortiert Animationen automatisch in Gruppen.  
*   Überprüfen Sie Animationen, indem Sie Sie verlangsamen, jede einzelne wiedergeben oder den Quellcode anzeigen.  
*   Sie können Animationen ändern, indem Sie den Offset für Anzeigedauer, Verzögerung, Dauer oder Keyframe ändern.  

## Übersicht   

Der Microsoft Edge devtools-Animations Inspektor hat zwei Hauptaufgaben.  

*   Untersuchen von Animationen  Sie möchten den Quellcode für eine Animationsgruppe verlangsamen, wiedergeben oder überprüfen.  
*   Ändern von Animationen  Sie möchten die Zeitmessung, die Verzögerung, die Dauer oder den Keyframe-Offset einer Animationsgruppe ändern.  Bezier-und Keyframe-Bearbeitung werden zurzeit nicht unterstützt.  

Der Animations Inspektor unterstützt CSS-Animationen, CSS-Übergänge und Web-Animationen.  `requestAnimationFrame` Animationen werden zurzeit nicht unterstützt.  

### Was ist eine Animationsgruppe?  

Bei einer Animationsgruppe handelt es sich um eine Gruppe von Animationen, die möglicherweise miteinander in Beziehung stehen.  Derzeit hat das Web kein echtes Konzept einer Gruppen Animation, daher müssen Motion-Designer und-Entwickler einzelne Animationen zusammenstellen und verfassen, damit die Animationen als ein kohärenter visueller Effekt gerendert werden.  Der Animations Inspektor prognostiziert, welche Animationen auf der Grundlage der Startzeit \ (ohne Verzögerungen usw.) zusammenhängen.  Der Animations Inspektor gruppiert auch die Animationen nebeneinander.  
Mit anderen Worten: eine Gruppe von Animationen, die alle im gleichen Skriptblock ausgelöst werden, wird zusammen gruppiert.  Wenn eine Animation asynchron ist, wird Sie in eine separate Gruppe verschoben.  

## Erste Schritte  

Es gibt zwei Möglichkeiten, den Animations Inspektor zu öffnen:  

*   Öffnen des Menüs zum **anpassen und Steuern des devtools**  
    1.  Navigieren Sie zum unter Menü **Weitere Tools** .  
    1.  Wählen Sie **Animationen**aus:  
        
        > ##### Abbildung2  
        > Animationen über das Hauptmenü  
        > ![Animationen über das Hauptmenü][ImageAnimationsViaMainMenu]  
        
*   Öffnen des **Befehlsmenüs**  
    1.  Geben Sie `Drawer: Show Animations` ein.  

Der Animations Inspektor wird als Registerkarte neben dem Konsolen Einzug geöffnet.  Da es sich bei dem Animations Inspektor um eine Schublade handelt, können Sie den Animations Inspektor in einem beliebigen devtools-Fenster verwenden.  

> ##### Abbildung 3  
> Animations Inspektor leeren  
> ![Animations Inspektor leeren][ImageEmptyAnimationInspector]  

Der Animations Inspektor ist in vier Hauptabschnitte unterteilt \ (oder Bereiche \).  Dieser Leitfaden bezieht sich auf jeden Bereich wie folgt:  

| | Bereich | Beschreibung |  
| --- |:--- |:--- |  
| 1 | **Steuerelemente** | Hier können Sie alle aktuell aufgenommenen Animationsgruppen löschen oder die Geschwindigkeit der aktuell ausgewählten Animationsgruppe ändern. |  
| 2 | **Übersicht** | Wählen Sie hier eine Animationsgruppe aus, um Sie im **Detail** Bereich zu überprüfen und zu ändern. |  
| 3 | **Zeitachse** | Pausieren und starten Sie eine Animation von hier aus, oder springen Sie zu einer bestimmten Stelle in der Animation. |  
| 4 | **Details** | Überprüfen und Ändern der aktuell ausgewählten Animationsgruppe |  

> ##### Abbildung4  
> Animations Inspektor mit Anmerkungen  
> ![Animations Inspektor mit Anmerkungen][ImageAnnotatedAnimationInspector]  

Wenn Sie eine Animation aufzeichnen möchten, führen Sie einfach die Interaktion aus, mit der die Animation ausgelöst wird, während der Animations Inspektor geöffnet ist.  Wenn beim Laden einer Seite eine Animation ausgelöst wird, laden Sie die Seite neu, wobei der Animations Inspektor geöffnet wird, um die Animation zu erkennen.  

<!--  old link: <video src="animations/capture-animations.mp4" autoplay loop muted controls></video>  -->  

<!--  import the video to ACOM using https://review.docs.microsoft.com/en-us/help/contribute/contribute-video-publish?branch=master  -->  

<!--  > [!VIDEO animations/capture-animations.mp4]  -->  

## Überprüfen von Animationen   

Nachdem Sie eine Animation aufgenommen haben, gibt es verschiedene Möglichkeiten, Sie wiederzugeben:  

*   Zeigen Sie **mit der Maus** auf die Miniaturansicht im Übersichtsbereich, um eine Vorschau davon anzuzeigen.  
*   Wählen Sie im Bereich " **Übersicht** " die Gruppe "Animation" aus, damit Sie im **Detail** Bereich angezeigt wird, und drücken Sie dann das Symbol Symbol **Wiedergabe wieder** geben ![ ][ImageReplayButtonIcon] .  Die Animation wird im Viewport wiedergegeben.  Klicken Sie auf **die Symbole für Animations** Geschwindigkeits ![ Geschwindigkeits Symbole ][ImageAnimationSpeedButtonsIcon] , um die Vorschau Geschwindigkeit der aktuell ausgewählten Animationsgruppe zu ändern.  Sie können die rote vertikale Leiste verwenden, um Ihre aktuelle Position zu ändern.  
*   Klicken Sie, und ziehen Sie den roten vertikalen Balken, um die Animation des Viewports zu schrubben.  

### Anzeigen von Animations Details  

Nachdem Sie eine Animationsgruppe erfasst haben, klicken **Sie im Übersichtsbereich darauf** , um die Details anzuzeigen.  Im **Detail** Bereich wird jeder einzelnen Animation die Zeile a zugewiesen.  

> ##### Abbildung5  
> Animationsgruppen Details  
> ![Animationsgruppen Details][ImageAnimationGroupDetails]  

Zeigen Sie mit der Maus auf eine Animation, um Sie im Viewport zu markieren.  Klicken Sie auf die Animation, um Sie im **Element** Panel zu markieren.  

> ##### Abbildung6  
> Zeigen Sie mit der Maus auf die Animation, um Sie im Viewport hervorzuheben  
> ![Zeigen Sie mit der Maus auf die Animation, um Sie im Viewport hervorzuheben][ImageHoverOverAnimationHighlightViewport]  

Der linke, dunklere Abschnitt einer Animation ist die Definition.  Der Rechte, verblasstere Abschnitt stellt Iterationen dar.  In [Abbildung 7](#figure-7)stellen beispielsweise Abschnitte zwei und drei Iterationen von Abschnitt eins dar.  

> ##### Abbildung7  
> Diagramm der Animations Iterationen  
> ![Diagramm der Animations Iterationen][ImageDiagramAnimationIterations]  

Wenn für zwei Elemente dieselbe Animation angewendet wurde, weist der Animations Inspektor den Elementen dieselbe Farbe zu.  Die Farbe ist zufällig und hat keine Bedeutung.  In [Abbildung 8](#figure-8) sind beispielsweise die beiden Elemente `div.cwccw.earlier` `div.cwccw.later` enthalten, und es wird dieselbe Animation `spinrightleft` wie für die `div.ccwcw.earlier` Elemente und verwendet `div.ccwcw.later` .  

> ##### Abbildung8  
> Farbcodierte Animationen  
> ![Farbcodierte Animationen][ImageColorCodedAnimations]  

## Ändern von Animationen   

Es gibt drei Möglichkeiten, wie Sie eine Animation mit dem Animations Inspektor ändern können:  

*   Animationsdauer.  
*   Keyframe-Anzeigedauern.  
*   Anfangszeit Verzögerung.  

In diesem Abschnitt wird angenommen, dass [Abbildung 9](#figure-9) die ursprüngliche Animation darstellt:  

> ##### Abbildung 9  
> Ursprüngliche Animation vor der Änderung  
> ![Ursprüngliche Animation vor der Änderung][ImageOriginalAnimationBeforeModification]  

Wenn Sie die Dauer einer Animation ändern möchten, klicken Sie auf den ersten oder letzten Kreis, und ziehen Sie ihn.  

> ##### Abbildung 10  
> Geänderte Dauer  
> ![Geänderte Dauer][ImageModifiedDuration]  

Wenn die Animation Keyframe-Regeln definiert, werden diese als weiße innere Kreise dargestellt.  Klicken Sie, und ziehen Sie eine der folgenden Schritte, um die Anzeigedauer des Keyframes zu ändern.  

> ##### Abbildung 11  
> Geänderter Keyframe  
> ![Geänderter Keyframe][ImageModifiedKeyframe]  

Wenn Sie einer Animation eine Verzögerung hinzufügen möchten, klicken Sie darauf, und ziehen Sie Sie mit Ausnahme der Kreise an eine beliebige Stelle.  

> ##### Abbildung 12  
> Geänderte Verzögerung  
> ![Geänderte Verzögerung][ImageModifiedDelay]  

<!--   -->  



<!-- image links -->  

[ImageAnimationSpeedButtonsIcon]: /microsoft-edge/devtools-guide-chromium/media/animation-speed-buttons-icon.msft.png  
[ImageReplayButtonIcon]: /microsoft-edge/devtools-guide-chromium/media/replay-button-icon.msft.png  

[ImageAnimationInspector]: /microsoft-edge/devtools-guide-chromium/media/inspect-styles-elements-styles-drawer-animations-completed.msft.png "Abbildung 1: Animations Inspektor"  
[ImageAnimationsViaMainMenu]: /microsoft-edge/devtools-guide-chromium/media/inspect-styles-elements-styles-more-tools-animations.msft.png "Abbildung 2: Animationen über das Hauptmenü"  
[ImageEmptyAnimationInspector]: /microsoft-edge/devtools-guide-chromium/media/inspect-styles-elements-styles-drawer-animations.msft.png "Abbildung 3: leeres Animations Inspektor"  
[ImageAnnotatedAnimationInspector]: /microsoft-edge/devtools-guide-chromium/media/inspect-styles-elements-styles-drawer-animations-selected-paused.msft.png "Abbildung 4: Inspektor für kommentierte Animationen"  
[ImageAnimationGroupDetails]: /microsoft-edge/devtools-guide-chromium/media/inspect-styles-elements-styles-drawer-animations-selected-completed.msft.png "Abbildung 5: Details zur Animationsgruppe"  
[ImageHoverOverAnimationHighlightViewport]: /microsoft-edge/devtools-guide-chromium/media/inspect-styles-split-elements-styles-drawer-animations-selected-completed.msft.png "Abbildung 6: zeigen Sie mit der Maus auf die Animation, um Sie im Viewport zu markieren."  
[ImageDiagramAnimationIterations]: /microsoft-edge/devtools-guide-chromium/media/inspect-styles-glitch-display-animations-highlight.msft.png "Abbildung 7: Diagramm der Animations Iterationen"  
[ImageColorCodedAnimations]: /microsoft-edge/devtools-guide-chromium/media/inspect-styles-glitch-display-animations.msft.png "Abbildung 8: farbcodierte Animationen"  
[ImageOriginalAnimationBeforeModification]: /microsoft-edge/devtools-guide-chromium/media/inspect-styles-glitch-spin-animations-console-animations.msft.png "Abbildung 9: ursprüngliche Animation vor der Änderung"  
[ImageModifiedDuration]: /microsoft-edge/devtools-guide-chromium/media/inspect-styles-glitch-spin-animations-console-animations-shorter.msft.png "Abbildung 10: geänderte Dauer"  
[ImageModifiedKeyframe]: /microsoft-edge/devtools-guide-chromium/media/inspect-styles-glitch-spin-animations-console-animations-keyframe-modification.msft.png "Abbildung 11: Geänderter Keyframe"  
[ImageModifiedDelay]: /microsoft-edge/devtools-guide-chromium/media/inspect-styles-glitch-spin-animations-console-animations-delay.msft.png "Abbildung 12: geänderte Verzögerung"  

<!-- links -->  

> [!NOTE]
> Teile dieser Seite sind Änderungen, die auf der [von Google erstellten und freigegebenen][GoogleSitePolicies] Arbeit basieren und gemäß den in der [Creative Commons Attribution 4,0 International-Lizenz][CCA4IL]beschriebenen Begriffen verwendet werden.  
> Die ursprüngliche Seite befindet sich [hier](https://developers.google.com/web/tools/chrome-devtools/inspect-styles/animations) und wird von [Kayce Basken][KayceBasques] (Technical Writer, Chrome devtools \ & Lighthouse \) erstellt.  

[![Creative Commons-Lizenz][CCby4Image]][CCA4IL]  
Diese Arbeit unterliegt einer [Creative Commons Attribution 4.0 International License][CCA4IL].  

[CCA4IL]: https://creativecommons.org/licenses/by/4.0  
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png  
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies  
[KayceBasques]: https://developers.google.com/web/resources/contributors/kaycebasques  
