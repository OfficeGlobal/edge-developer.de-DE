---
ms.assetid: 89ac711a-78ff-4219-8dc3-2bad2099cf49
description: Sehen Sie sich ein Beispiel für ein Microsoft Edge-JSON-Manifest an, um mögliche Feldwerte anzuzeigen.
title: Erweiterungen – Beispiel für ein JSON-Manifest
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 01/15/2020
ms.topic: article
ms.prod: microsoft-edge
keywords: Edge, Web-Entwicklung, HTML, CSS, JavaScript, Entwickler
ms.custom: seodec18
ms.openlocfilehash: b4055524201821e3051f704b3bc9894de370c76d
ms.sourcegitcommit: 6860234c25a8be863b7f29a54838e78e120dbb62
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2020
ms.locfileid: "10567466"
---
# Beispiel für eine JSON-Manifestdatei  

[!INCLUDE [deprecation-note](../../includes/deprecation-note.md)]  

Der folgende Codeausschnitt enthält ein Beispiel für eine Microsoft Edge JSON-Manifestdatei.

```json
{
    "name" : "Sample extension manifest",
    "version" : "1.0.0.0",
    "author" : "Microsoft Corporation",
    "browser_action" : 
    {
        "default_icon" : 
        {
            "20" : "icon_20.png",
            "40" : "icon_40.png"
        },
        "default_title" : "Sample extension",
        "default_popup" : "popup.html"
    },
    "content_scripts" : [{
            "js" : ["content_script.js"],
            "matches" : ["*://*/*"]
        }
    ],

    "content_security_policy" : "script-src 'self'; object-src 'self'",
    "default_locale" : "en",
    "description" : "This is a sample extension that illustrates the JSON manifest schema",

    "options_page" : "options.html",
    "permissions" : 
    [
        "*://*/*", "notifications", "cookies", "tabs", "storage", "contextMenus", "background"
    ],
    "background" : 
    {
        "page" : "background.html",
        "persistent" : false
    },
    "icons" : {
        "128" : "icon_128.png",
        "16" : "icon_16.png",
        "48" : "icon_48.png"
    },
    "minimum_edge_version" : "33.14281.1000.0",

    "web_accessible_resources" : ["icon_48.png"]

} 
```



