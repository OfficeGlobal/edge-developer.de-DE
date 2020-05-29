---
description: Erweiterungen erste Schritte Teil 1
title: Dynamisches Einfügen eines NASA-Bilds unter dem Body-Tag der Seite mithilfe von Inhalts Skripts
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 05/08/2020
ms.topic: article
ms.prod: microsoft-edge-chromium
keywords: Edge-Chromium, Web-Entwicklung, HTML, CSS, JavaScript, Entwickler, Erweiterungen
ms.openlocfilehash: b37184f0188b72ec868ab3de3f2341c0694ee42c
ms.sourcegitcommit: 0bc1312a1e6a0ac37cf385201db4361fc05184fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2020
ms.locfileid: "10683644"
---
# <span data-ttu-id="aecc8-104">Dynamisches Einfügen eines NASA-Bilds unter dem Body-Tag der Seite mithilfe von Inhalts Skripts</span><span class="sxs-lookup"><span data-stu-id="aecc8-104">Dynamically Insert NASA Picture Below The Page Body Tag Using Content Scripts</span></span>  
  
[<span data-ttu-id="aecc8-105">Abgeschlossene Erweiterungspaket Quelle für diesen Teil</span><span class="sxs-lookup"><span data-stu-id="aecc8-105">Completed Extension Package Source for This Part</span></span>][ArchiveExtensionGettingStartedPart2]  

## <span data-ttu-id="aecc8-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="aecc8-106">Overview</span></span>  

<span data-ttu-id="aecc8-107">In Teil 2 erfahren Sie, wie Sie das Popup-Menü aktualisieren können, damit das Bild, das Sie vorher hatten, nicht angezeigt wird, aber dieses Bild durch einen Titel und eine standardmäßige HTML-Schaltfläche ersetzt.</span><span class="sxs-lookup"><span data-stu-id="aecc8-107">In part 2, you learn to update your pop-up menu to not show the static stars image you had before, but to replace that image with a title and a standard HTML button.</span></span>  <span data-ttu-id="aecc8-108">Wenn diese Schaltfläche ausgewählt ist, wird das in der Erweiterung eingebettete Sternchen-Bild an die Inhaltsseite weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="aecc8-108">That button, when selected, passes that stars image, which is embedded in the Extension, to the content page.</span></span>  <span data-ttu-id="aecc8-109">Das Bild wird in die Registerkarte aktiver Browser eingefügt.</span><span class="sxs-lookup"><span data-stu-id="aecc8-109">That image, is inserted into the active browser tab.</span></span>  

*   <span data-ttu-id="aecc8-110">In diesem Leitfaden behandelte Erweiterungstechnologien</span><span class="sxs-lookup"><span data-stu-id="aecc8-110">Extension technologies covered in this guide</span></span>  
    *   <span data-ttu-id="aecc8-111">Einfügen von JavaScript-Bibliotheken in die Erweiterung</span><span class="sxs-lookup"><span data-stu-id="aecc8-111">Injecting JavaScript libraries into Extension</span></span>  
    *   <span data-ttu-id="aecc8-112">Verfügbar machen von Erweiterungs Ressourcen für browserregisterkarten</span><span class="sxs-lookup"><span data-stu-id="aecc8-112">Exposing Extension assets to browser tabs</span></span>  
    *   <span data-ttu-id="aecc8-113">Einschließen von Inhaltsseiten in vorhandene browserregisterkarten</span><span class="sxs-lookup"><span data-stu-id="aecc8-113">Including content pages in existing browser tabs</span></span>  
    *   <span data-ttu-id="aecc8-114">Wenn Inhaltsseiten auf Nachrichten von Popups abhören und Antworten</span><span class="sxs-lookup"><span data-stu-id="aecc8-114">Having content pages listen for messages from pop-ups and respond</span></span>  

## <span data-ttu-id="aecc8-115">Entfernen des Bilds aus dem Popup und ersetzen durch eine Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="aecc8-115">Remove the image from the pop-up and replace it with a button</span></span>  

<span data-ttu-id="aecc8-116">Aktualisieren Sie zunächst die `popup.html` Datei mit einem geraden Markup, in dem ein Titel und eine Schaltfläche angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="aecc8-116">First, update your `popup.html` file with some straight forward markup that displays a title and a button.</span></span>  <span data-ttu-id="aecc8-117">Sie programmieren die Schaltfläche in Kürze, aber im Moment fügen Sie einfach einen Verweis auf eine leere JavaScript-Datei hinzu `popup.js` .</span><span class="sxs-lookup"><span data-stu-id="aecc8-117">You program that button shortly, but for now, just include a reference to an empty JavaScript file `popup.js`.</span></span>  <span data-ttu-id="aecc8-118">Hier ist Update HTML.</span><span class="sxs-lookup"><span data-stu-id="aecc8-118">Here is update HTML.</span></span>  

```html
<html>
    <head>
        <meta charset="utf-8" />
        <style>
            body {
                width: 500px;
            }
            button {
                background-color: #336dab;
                border: none;
                color: white;
                padding: 15px 32px;
                text-align: center;
                font-size: 16px;
            }
        </style>
    </head>
    <body>
        <h1>Show the NASA Picture of the Day</h1>
        <h2>(select the image to remove)</h2>
        <button id="sendmessageid">Display</button>
        <script src="popup.js"></script>
    </body>
</html>
```  

<span data-ttu-id="aecc8-119">Nachdem Sie Ihre Erweiterung aktualisiert und das Symbol für die Erweiterungs Einführung ausgewählt haben, enthält das Popupfenster die Schaltfläche Anzeige.</span><span class="sxs-lookup"><span data-stu-id="aecc8-119">After updating your Extension and selecting the Extension launch icon, the have the following pop-up includes a display button.</span></span>  

:::image type="complex" source="./media/part2-popupdialog.png" alt-text="Popup. HTML-Anzeige nach dem Drücken des Erweiterungssymbols":::
   <span data-ttu-id="aecc8-121">Popup. HTML-Anzeige nach dem Drücken des Erweiterungssymbols</span><span class="sxs-lookup"><span data-stu-id="aecc8-121">popup.html display after pressing the Extension icon</span></span>
:::image-end:::

<!--![popup.html display after pressing the Extension icon][ImagePart2Popupdialog]  -->  

## <span data-ttu-id="aecc8-122">Aktualisierte Strategie zum Anzeigen des Bilds oben auf der Registerkarte "Browser"</span><span class="sxs-lookup"><span data-stu-id="aecc8-122">Updated strategy to display image at the top of the browser tab</span></span>  

<span data-ttu-id="aecc8-123">Nachdem Sie die Schaltfläche hinzugefügt haben, besteht die nächste Aufgabe darin, die Bilddatei oben auf der `images/stars.jpeg` aktiven Registerkarte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="aecc8-123">After adding the button, the next task is to make it bring up the `images/stars.jpeg` image file at the top of the active tab page.</span></span>  

<span data-ttu-id="aecc8-124">Beachten Sie, dass jede Registerkarte einen eigenen Thread hat und die Erweiterung einen separaten Thread aufweist.</span><span class="sxs-lookup"><span data-stu-id="aecc8-124">Remember, each tab page has a unique own thread and the Extension has a separate thread.</span></span>  <span data-ttu-id="aecc8-125">Daher müssen Sie zuerst ein Inhalts Skript erstellen und dieses Inhalts Skript auf der Registerkartenseite einfügen.</span><span class="sxs-lookup"><span data-stu-id="aecc8-125">So, you must first create a content script and inject that content script into the tab page.</span></span>  <span data-ttu-id="aecc8-126">Wenn Sie dies tun, müssen Sie eine Nachricht von Ihrem Popup an das Inhalts Skript senden, das auf der Registerkartenseite ausgeführt wird und dem Inhalts Skript mitteilt, welches Bild angezeigt werden soll und wie es angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="aecc8-126">Once you do that, you must send a message from your pop-up to that content script running on the tab page telling that content script what image to show, and how to show it.</span></span>  

## <span data-ttu-id="aecc8-127">Erstellen des Popup-Javascripts zum Senden einer Nachricht</span><span class="sxs-lookup"><span data-stu-id="aecc8-127">Creating the pop-up JavaScript to send a message</span></span>  

<span data-ttu-id="aecc8-128">Erstellen Sie zunächst `popup/popup.js` Code, um eine Nachricht an ihr noch nicht erstelltes Inhalts Skript zu senden, das Sie im Moment erstellen und in Ihre Browserregister Karte einfügen müssen.  Dazu fügt der folgende Code der `onclick` Popup Anzeige Schaltfläche ein Ereignis hinzu.</span><span class="sxs-lookup"><span data-stu-id="aecc8-128">First, create `popup/popup.js` and add code to send a message to your not-yet-created content script that you must momentarily create and inject into your browser tab.  To do that, the following code adds an `onclick` event to your pop-up display button.</span></span>  

```javascript
const sendMessageId = document.getElementById("sendmessageid");
if (sendMessageId) {
  sendMessageId.onclick = function() {
    // do something
  };
}
```  

<span data-ttu-id="aecc8-129">Im `onclick` Fall, was Sie tun müssen, ist die aktuelle Browser-Registerkarte zu finden \ (wenn nur eine geöffnet ist, ist das eine \).</span><span class="sxs-lookup"><span data-stu-id="aecc8-129">In the `onclick` event, what you must do is find the current browser tab \(if there is only one open it is that one\).</span></span>  <span data-ttu-id="aecc8-130">Nachdem Sie diese Registerkarte gefunden haben, verwenden Sie die `chrome.tabs.sendmessage` Erweiterungs-API, um eine Nachricht an diesen Reiter zu senden.</span><span class="sxs-lookup"><span data-stu-id="aecc8-130">Then, once you find that tab, use the `chrome.tabs.sendmessage` Extension API to send a message to that tab.</span></span>  

<span data-ttu-id="aecc8-131">In dieser Nachricht müssen Sie die URL zu dem Bild hinzufügen, das Sie anzeigen möchten, und Sie möchten eine eindeutige ID senden, die dem eingefügten Bild zugewiesen werden soll.</span><span class="sxs-lookup"><span data-stu-id="aecc8-131">In that message you must include the URL to the image you want to display, and you want to send a unique ID that should be assigned to that inserted image.</span></span>  <span data-ttu-id="aecc8-132">Sie können festlegen, dass die Inhalts Einfügung JavaScript generieren soll, aber aus Gründen, die später deutlich werden, generieren Sie diese eindeutige ID hier in `popup.js` und übergeben Sie an das noch nicht erstellte Inhalts Skript.</span><span class="sxs-lookup"><span data-stu-id="aecc8-132">You may choose to let the content insertion JavaScript generate that, but for reasons that become apparent later, generate that unique ID here in `popup.js` and pass it to the not-yet-created content script.</span></span>  

<span data-ttu-id="aecc8-133">Hier ist Ihre aktualisierte `popup/popup.js` Datei.</span><span class="sxs-lookup"><span data-stu-id="aecc8-133">Here is your updated `popup/popup.js` file.</span></span>  <span data-ttu-id="aecc8-134">Übergeben Sie auch die aktuelle Tab-ID, die Sie in einem späteren Abschnitt benötigen, aber für jetzt, wird nicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="aecc8-134">Also, pass in the current tab ID which you should need in a later section but for now, is not be used.</span></span>  

```javascript
const sendMessageId = document.getElementById("sendmessageid");
if (sendMessageId) {
    sendMessageId.onclick = function() {
        chrome.tabs.query({ active: true, currentWindow: true }, function(tabs) {
            chrome.tabs.sendMessage(
                tabs[0].id,
                {
                    url: chrome.extension.getURL("images/stars.jpeg"),
                    imageDivId: `${guidGenerator()}`,
                    tabId: tabs[0].id
                },
                function(response) {
                    window.close();
                }
            );
            function guidGenerator() {
                const S4 = function () {
                    return (((1 + Math.random()) * 0x10000) | 0).toString(16).substring(1);
                };
                return (S4() + S4() + "-" + S4() + "-" + S4() + "-" + S4() + "-" + S4() + S4() + S4());
            }
        });
    };
}
```  

## <span data-ttu-id="aecc8-135">So können Sie Ihre Stars. JPEG auf jeder Registerkarte des Browsers zur Verfügung stellen</span><span class="sxs-lookup"><span data-stu-id="aecc8-135">Making your stars.jpeg available from any browser tab</span></span>  

<span data-ttu-id="aecc8-136">Sie Fragen sich wahrscheinlich, warum Sie die `images/stars.jpeg` `chrome.extension.getURL` Chrome-Erweiterungs-API verwenden müssen, anstatt einfach nur die relative URL ohne das zusätzliche Präfix zu übergeben, wie im vorherigen Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="aecc8-136">You are probably wondering why, when you pass the `images/stars.jpeg` must you use the `chrome.extension.getURL` chrome Extension API instead of just passing in the relative URL without the extra prefix like in the previous section.</span></span>  <span data-ttu-id="aecc8-137">Übrigens sieht das zusätzliche Präfix, das `getUrl` mit dem angefügten Bild zurückgegeben wird, ungefähr wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="aecc8-137">By the way, that extra prefix, returned by `getUrl` with the image attached looks something like the following.</span></span>  

```http
extension://inigobacliaghocjiapeaaoemkjifjhp/images/stars.jpeg
```  

<span data-ttu-id="aecc8-138">Der Grund dafür ist, dass Sie das Bild mit dem `src` Attribut des `img` Elements in die Inhaltsseite einfügen.</span><span class="sxs-lookup"><span data-stu-id="aecc8-138">The reason is that you are injecting the image using the `src` attribute of the `img` element into the content page.</span></span>  <span data-ttu-id="aecc8-139">Die Inhaltsseite wird in einem eindeutigen Thread ausgeführt, der nicht mit dem Thread identisch ist, auf dem die Erweiterung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="aecc8-139">The content page is running on a unique thread that is not the same as the thread running the Extension.</span></span>  <span data-ttu-id="aecc8-140">Sie müssen die statische Bilddatei als Web-Ressource verfügbar machen, damit Sie ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="aecc8-140">You must expose the static image file as a web asset for it to work correctly.</span></span>  

<span data-ttu-id="aecc8-141">Dazu müssen Sie einen weiteren Eintrag in der Datei hinzufügen `manifest.json` .</span><span class="sxs-lookup"><span data-stu-id="aecc8-141">To do that, you must add another entry in the `manifest.json` file.</span></span>  <span data-ttu-id="aecc8-142">Sie müssen das Bild deklarieren, damit es über jede Registerkarte des Browsers zugänglich ist.  Dieser Eintrag sieht folgendermaßen aus: \ (Sie sollten ihn in der vollständigen `manifest.json` Datei unten sehen, wenn Sie die Inhalts Skript Deklaration hinzufügen).</span><span class="sxs-lookup"><span data-stu-id="aecc8-142">You must declare the image to be accessible from any browser tab.  That entry is as follows \(you should see it in the full `manifest.json` file below when you add the content script declaration coming up\).</span></span>  

```json
"web_accessible_resources": [
    "images/*.jpeg"
]
```  

<span data-ttu-id="aecc8-143">Sie haben nun den Code in Ihre Datei geschrieben, `popup.js` um eine Nachricht an die Inhaltsseite zu senden, die auf der aktuellen aktiven Registerkarte eingebettet ist, aber Sie haben diese Inhaltsseite nicht erstellt und eingefügt.</span><span class="sxs-lookup"><span data-stu-id="aecc8-143">You have now written the code in your `popup.js` file to send a message to the content page that is embedded on the current active tab page, but you have not created and injected that content page.</span></span>  <span data-ttu-id="aecc8-144">Tun Sie das jetzt.</span><span class="sxs-lookup"><span data-stu-id="aecc8-144">Do that now.</span></span>  

## <span data-ttu-id="aecc8-145">Aktualisieren ihres Manifests. JSON für Content und Web Access</span><span class="sxs-lookup"><span data-stu-id="aecc8-145">Updating your manifest.json for content and web access</span></span>  

<span data-ttu-id="aecc8-146">Das aktualisierte `manifest.json` , das das `content-scripts` und enthält, `web_accessible_resources` ist wie folgt.</span><span class="sxs-lookup"><span data-stu-id="aecc8-146">The updated `manifest.json` that includes the `content-scripts` and `web_accessible_resources` is as follows.</span></span>  

```json
{
    "name": "NASA Picture of the day viewer",
    "version": "0.0.0.1",
    "manifest_version": 2,
    "description": "A Chromium Extension to show the NASA Picture of the Day.",
    "icons": {
        "16": "icons/nasapod16x16.png",
        "32": "icons/nasapod32x32.png",
        "48": "icons/nasapod48x48.png",
        "128": "icons/nasapod128x128.png"
    },
    "browser_action": {
        "default_popup": "popup/popup.html"
    },
    "content_scripts": [
        {
            "matches": [
              "<all_urls>"
            ],
            "js": ["lib/jquery.min.js","content-scripts/content.js"]
        }
    ],
    "web_accessible_resources": [
        "images/*.jpeg"
    ]
}
```  

<span data-ttu-id="aecc8-147">Der von Ihnen hinzugefügte Abschnitt ist `content_scripts` .</span><span class="sxs-lookup"><span data-stu-id="aecc8-147">The section you added is `content_scripts`.</span></span>  <span data-ttu-id="aecc8-148">Das Attribut `matches` auf `<all_urls>` bedeutet, dass alle Dateien, die im Abschnitt " **content_scripts** " erwähnt werden, bei jedem Laden in alle Registerkarten des Browsers eingefügt werden.</span><span class="sxs-lookup"><span data-stu-id="aecc8-148">The attribute `matches` set to `<all_urls>` means that all the files mention in the **content_scripts** section is injected into all browser tab pages when each are loaded.</span></span>  <span data-ttu-id="aecc8-149">Die zulässigen Dateitypen, die hier injiziert werden können, sind JavaScript und CSS.</span><span class="sxs-lookup"><span data-stu-id="aecc8-149">The allowable types of files that are able to be injected here are javascript and css.</span></span>  <span data-ttu-id="aecc8-150">Sie haben auch hinzugefügt `libjquery.min.js` .</span><span class="sxs-lookup"><span data-stu-id="aecc8-150">You also added `libjquery.min.js`.</span></span>  <span data-ttu-id="aecc8-151">Sie können diese aus dem oben im Abschnitt angegebenen Download aufnehmen.</span><span class="sxs-lookup"><span data-stu-id="aecc8-151">You are able to include that from the download mentioned at the top of the section.</span></span>  

## <span data-ttu-id="aecc8-152">Hinzufügen von jQuery und Grundlegendes zum zugehörigen Thread</span><span class="sxs-lookup"><span data-stu-id="aecc8-152">Adding jQuery and understanding the associated thread</span></span>  

<span data-ttu-id="aecc8-153">Planen Sie in den Inhalts Skripts, die Sie injizieren, die Verwendung von jQuery \ ( `$` \).</span><span class="sxs-lookup"><span data-stu-id="aecc8-153">In the content scripts you are injecting, plan on using jQuery \(`$`\).</span></span>  <span data-ttu-id="aecc8-154">Sie haben eine minimierte-Version von jQuery hinzugefügt und in Ihr Erweiterungspaket als eingefügt `lib\jquery.min.js` .</span><span class="sxs-lookup"><span data-stu-id="aecc8-154">You added a minified version of jQuery and put it in your Extension package as `lib\jquery.min.js`.</span></span>  <span data-ttu-id="aecc8-155">Diese Inhalts Skripts werden in einer einzelnen Sandbox von Sortierungen ausgeführt, was bedeutet, dass die in die Seite eingefügte jQuery-Datei `popup.js` nicht für den Inhalt freigegeben wird.</span><span class="sxs-lookup"><span data-stu-id="aecc8-155">These content scripts run in an individual sandbox of sorts, which means that the jQuery injected into the `popup.js` page does not share with the content.</span></span>  

<span data-ttu-id="aecc8-156">Beachten Sie, dass, selbst wenn auf der Registerkarte Browser auf der geladenen Webseite JavaScript ausgeführt wird, jeder eingefügte Inhalt keinen Zugriff darauf hat.</span><span class="sxs-lookup"><span data-stu-id="aecc8-156">Keep in mind that even if the browser tab has JavaScript running on it on the loaded web page, any content injected does not have access to that.</span></span>  <span data-ttu-id="aecc8-157">Das eingefügte JavaScript hat nur Zugriff auf das eigentliche Dom, das auf dieser Registerkarte des Browsers geladen wurde.</span><span class="sxs-lookup"><span data-stu-id="aecc8-157">That injected JavaScript just has access to the actual DOM loaded in that browser tab.</span></span>  

## <span data-ttu-id="aecc8-158">Hinzufügen des Inhalts Skript-Nachrichten Listeners</span><span class="sxs-lookup"><span data-stu-id="aecc8-158">Adding the content script message listener</span></span>  

<span data-ttu-id="aecc8-159">Hier sehen `content-scripts\content.js` Sie die Datei, die auf jeder Registerkarte des Browsers basierend auf Ihrem Abschnitt eingefügt wird `manifest.json` `content-scripts` .</span><span class="sxs-lookup"><span data-stu-id="aecc8-159">Here is that `content-scripts\content.js` file that gets injected into every browser tab page based on your `manifest.json` `content-scripts` section.</span></span>  

```javascript
chrome.runtime.onMessage.addListener(function(request, sender, sendResponse) {
    $("body").prepend(
        `<img  src="${request.url}" id="${request.imageDivId}"
               class="slide-image" /> `
    );
    $("head").prepend(
        `<style>
          .slide-image {
              height: auto;
              width: 100vw;
          }
        </style>`
    );
    $(`#${request.imageDivId}`).click(function() {
        $(`#${request.imageDivId}`).remove(`#${request.imageDivId}`);
    });
    sendResponse({ fromcontent: "This message is from content.js" });
});
```  

<span data-ttu-id="aecc8-160">Beachten Sie, dass das obige JavaScript die `listener` Verwendung der `chrome.runtime.onMessage.addListener` Erweiterungs-API-Methode registriert.</span><span class="sxs-lookup"><span data-stu-id="aecc8-160">Notice that all the above JavaScript does is to register a `listener` using the `chrome.runtime.onMessage.addListener` Extension API method.</span></span>  <span data-ttu-id="aecc8-161">Dieser Listener wartet auf Nachrichten wie diejenige, die Sie von der `popup.js` zuvor beschriebenen mit der `chrome.tabs.sendMessage` Erweiterungs-API-Methode gesendet haben.</span><span class="sxs-lookup"><span data-stu-id="aecc8-161">This listener waits for messages like the one you sent from the `popup.js` described earlier with the `chrome.tabs.sendMessage` Extension API method.</span></span>  

<span data-ttu-id="aecc8-162">Der erste Parameter der `addListener` Methode ist eine Funktion, deren erster Parameter Request die Details der übergebenen Nachricht ist.</span><span class="sxs-lookup"><span data-stu-id="aecc8-162">The first parameter of the `addListener` method is a function whose first parameter, request, is the details of the message being passed in.</span></span>  <span data-ttu-id="aecc8-163">Beachten Sie, `popup.js` dass die `sendMessage` Attribute des ersten Parameters, wenn Sie die Methode verwendet haben, `url` und sind `imageDivId` .</span><span class="sxs-lookup"><span data-stu-id="aecc8-163">Remember, from `popup.js`, when you used the `sendMessage` method, those attributes of the first parameter are `url` and `imageDivId`.</span></span>  

<span data-ttu-id="aecc8-164">Wenn ein Ereignis vom Listener verarbeitet wird, wird die Funktion, die der erste Parameter ist, ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="aecc8-164">When an event is processed by the listener, the function that is the first parameter is run.</span></span>  <span data-ttu-id="aecc8-165">Der erste Parameter dieser Funktion ist ein Objekt, das Attribute wie zugewiesen von besitzt `sendMessage` .</span><span class="sxs-lookup"><span data-stu-id="aecc8-165">The first parameter of that function is an object that has attributes as assigned by `sendMessage`.</span></span>  <span data-ttu-id="aecc8-166">Diese Funktion verarbeitet einfach die drei jQuery-Skriptzeilen.</span><span class="sxs-lookup"><span data-stu-id="aecc8-166">That function simply processes the three jQuery script lines.</span></span>  

*   <span data-ttu-id="aecc8-167">Der erste fügt dynamisch in die DOM-Kopfzeile einen **\<style\>** Abschnitt ein, den Sie `slide-image` dem Element als Klasse zuweisen müssen `img` .</span><span class="sxs-lookup"><span data-stu-id="aecc8-167">The first dynamically inserts into the DOM header a **\<style\>** section that you must assign as a `slide-image` class to your `img` element.</span></span>  
*   <span data-ttu-id="aecc8-168">Mit der zweiten wird ein `img` Element direkt unter der `body` Registerkarte Ihres Browsers angefügt, auf der die `slide-image` Klasse sowie die `imageDivId` ID des Bildelements zugewiesen ist.</span><span class="sxs-lookup"><span data-stu-id="aecc8-168">The second, appends an `img` element right below the `body` of your browser tab that has the `slide-image` class assigned as well as the `imageDivId` as the ID of that image element.</span></span>  
*   <span data-ttu-id="aecc8-169">Das dritte fügt ein `click` Ereignis ein, das das gesamte Bild abdeckt, sodass der Benutzer eine beliebige Stelle im Bild auswählen kann, und dieses Bild wird von der Seite entfernt \ (zusammen mit dem Ereignis-Listener \).</span><span class="sxs-lookup"><span data-stu-id="aecc8-169">The third adds a `click` event that covers the entire image allowing the user to select any place on the image and that image is be removed from the page \(along with it is event listener\).</span></span>  

## <span data-ttu-id="aecc8-170">Hinzufügen von Funktionen zum Entfernen des angezeigten Bilds bei Auswahl</span><span class="sxs-lookup"><span data-stu-id="aecc8-170">Adding functionality to remove the displayed image when selected</span></span>  

<span data-ttu-id="aecc8-171">Wenn Sie nun zu einer beliebigen Seite navigieren und das Symbol für die **Erweiterung** auswählen, wird das Popupmenü wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="aecc8-171">Now, when you browse to any page and select your **Extension** icon, the pop-up menu is displayed as follows.</span></span>  

:::image type="complex" source="./media/part2-popupdialog.png" alt-text="Popup. HTML-Anzeige nach dem Drücken des Erweiterungssymbols":::
   <span data-ttu-id="aecc8-173">Popup. HTML-Anzeige nach dem Drücken des Erweiterungssymbols</span><span class="sxs-lookup"><span data-stu-id="aecc8-173">popup.html display after pressing the Extension icon</span></span>
:::image-end:::

<!--![popup.html display after pressing the Extension icon][ImagePart2Popupdialog]  -->  

<span data-ttu-id="aecc8-174">Wenn Sie die `Display` Schaltfläche auswählen, erhalten Sie die folgenden Elemente.</span><span class="sxs-lookup"><span data-stu-id="aecc8-174">When you select the `Display` button, you get what is below.</span></span>  <span data-ttu-id="aecc8-175">Wenn Sie eine beliebige Stelle im `stars.jpeg` Bild auswählen, wird das Bildelement entfernt, und die Registerkarten werden wieder auf die ursprüngliche Anzeige reduziert.</span><span class="sxs-lookup"><span data-stu-id="aecc8-175">If you select anywhere on the `stars.jpeg` image, that image element is removed and tab pages collapses back to what was originally displayed.</span></span>  

:::image type="complex" source="./media/part2-showingimage.png" alt-text="Das im Browser angezeigte Bild":::
   <span data-ttu-id="aecc8-177">Das im Browser angezeigte Bild</span><span class="sxs-lookup"><span data-stu-id="aecc8-177">The image showing in browser</span></span>
:::image-end:::

<!--![The image showing in browser][ImagePart2Showingimage]  -->  

<span data-ttu-id="aecc8-178">Sie haben jetzt eine Erweiterung erstellt, mit der eine Nachricht vom Popup Symbol für das Erweiterungssymbol erfolgreich an das dynamisch eingefügte JavaScript gesendet wird, das als Inhalt auf der Registerkarte Browser ausgeführt wird.  Durch diesen eingefügten Inhalt wird das Image-Element so festgesetzt, dass die statischen Sterne JPEG angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="aecc8-178">You have now created an Extension that successfully sends a message from the Extension icon pop-up, to the dynamically inserted JavaScript running as content on the browser tab.  That injected content set the image element to display your static stars jpeg.</span></span>  

<!-- image links -->  

<!--[ImagePart2Popupdialog]: ./media/part2-popupdialog.png "popup.html display after pressing the Extension icon"  -->  
<!--[ImagePart2Showingimage]: ./media/part2-showingimage.png "The image showing in browser"  -->

<!-- links -->  

[ArchiveExtensionGettingStartedPart2]: ./extension-source/extension-getting-started-part2.zip "Abgeschlossene Erweiterungspaket Quelle für diesen Teil | Microsoft docs"  