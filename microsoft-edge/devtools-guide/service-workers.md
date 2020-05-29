---
description: Verwenden des Service Worker-Panels zum Verwalten und Debuggen Ihrer Dienstmitarbeiter
title: DevTools-Debugger – Dienstmitarbeiter
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 03/05/2020
ms.topic: article
ms.prod: microsoft-edge
keywords: Microsoft Edge, Web-Entwicklung, F12-Tools, devtools, Debugger, Debuggen, PWA, Service Worker, Cache-API
ms.custom: seodec18
ms.openlocfilehash: 8e1fa62358657a47ce40d0742f95a76f2586d0c8
ms.sourcegitcommit: 6860234c25a8be863b7f29a54838e78e120dbb62
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2020
ms.locfileid: "10567592"
---
# <span data-ttu-id="0a998-104">Dienstmitarbeiter</span><span class="sxs-lookup"><span data-stu-id="0a998-104">Service Workers</span></span>

<span data-ttu-id="0a998-105">Das **Dienstpersonal** -Panel enthält Tools zum Verwalten und Debuggen der Dienstmitarbeiter für Ihre Website, um Ihnen zu helfen:</span><span class="sxs-lookup"><span data-stu-id="0a998-105">The **Service Workers** panel has tools for managing and debugging the service workers for your site, to help you:</span></span>

 - <span data-ttu-id="0a998-106">Verschaffen Sie sich einen Überblick über alle Servicemitarbeiter, die Ihrer Website zugeordnet sind, sowie Einzelheiten zu deren Umfang und Status.</span><span class="sxs-lookup"><span data-stu-id="0a998-106">Get an overview of all the service workers associated with your site and details of their scope and status</span></span>
 - <span data-ttu-id="0a998-107">**Aktualisieren** und verwalten (**aufheben**der Registrierung) der Service Worker-Registrierung für den angegebenen Bereich</span><span class="sxs-lookup"><span data-stu-id="0a998-107">**Update** and manage (**Unregister**) the service worker registration for the given scope</span></span>
 - <span data-ttu-id="0a998-108">**Pushen** einer testbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="0a998-108">**Push** a test notification</span></span>
 - <span data-ttu-id="0a998-109">**Stopp** / **Starten** einzelner Servicemitarbeiter und</span><span class="sxs-lookup"><span data-stu-id="0a998-109">**Stop**/**Start** individual service workers, and</span></span>
 - <span data-ttu-id="0a998-110">Über **prüfen** der ausgewählten Dienstmitarbeiter in einem separaten Debuggerfenster</span><span class="sxs-lookup"><span data-stu-id="0a998-110">**Inspect** the selected service worker in a separate debugger window</span></span>

![Bereich ' Dienstmitarbeiter Übersicht '](./media/service_worker.png)

<span data-ttu-id="0a998-112">Beachten Sie die folgenden Informationen zum Service Worker-Debuggen in Edge devtools:</span><span class="sxs-lookup"><span data-stu-id="0a998-112">Please note the following about service worker debugging in Edge DevTools:</span></span>

 - <span data-ttu-id="0a998-113">Beim Debuggen eines Dienst Arbeitsthreads wird eine neue Instanz des devtools, die sich von den Tools der Seite trennt, gestartet, da Dienstmitarbeiter auf mehreren Registerkarten freigegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="0a998-113">Debugging a service worker will launch a new instance of the  DevTools separate from the page's tools because service workers can be shared across multiple tabs.</span></span>
 - <span data-ttu-id="0a998-114">Die [**Elemente**](./elements.md) und [**Emulations**](./emulation.md) Panels fehlen im Service Worker-Debugger, da Dienstmitarbeiter im Hintergrund ausgeführt werden und das Front-End Ihrer APP nicht direkt steuern.</span><span class="sxs-lookup"><span data-stu-id="0a998-114">The [**Elements**](./elements.md) and [**Emulation**](./emulation.md) panels are absent from the service worker debugger, given that service workers run in the background and do not directly control the front-end of your app.</span></span>
 - <span data-ttu-id="0a998-115">Zurzeit wird der Netzwerkdatenverkehr für einen Dienstmitarbeiter nur von der devtools-Debugsitzung für diesen Worker und nicht von der Debugger-Instanz für die Seite selbst gemeldet.</span><span class="sxs-lookup"><span data-stu-id="0a998-115">Currently network traffic for a service worker is only reported from the  DevTools debugging instance for that worker, and not from the debugger instance for the page itself.</span></span>
 - <span data-ttu-id="0a998-116">Wenn Sie einen **Push** aus dem devtools simulieren möchten, müssen Sie einen *Push* -Ereignis-Listener zu Ihrem Dienstmitarbeiter hinzufügen, um dessen Wirkung zu beobachten.</span><span class="sxs-lookup"><span data-stu-id="0a998-116">To simulate a **Push** from the DevTools, you'll need to add a *push* event listener to your service worker in order to observe its effect.</span></span> <span data-ttu-id="0a998-117">Im folgenden Beispiel wird "Test Push Message from devtools" in Ihrer Service Worker- **Konsole**gedruckt.</span><span class="sxs-lookup"><span data-stu-id="0a998-117">The following example will print "Test push message from DevTools" in your service worker **Console**.</span></span>

   ```JavaScript
   self.addEventListener('push', function(event){
       console.log(event.data.text());
   });
   ```

<span data-ttu-id="0a998-118">Im folgenden finden Sie einige allgemeine Punkte, die Sie bei der Verwendung von Servicemitarbeitern beachten sollten:</span><span class="sxs-lookup"><span data-stu-id="0a998-118">Here are some general things to keep in mind when using service workers:</span></span>

- **<span data-ttu-id="0a998-119">Nur HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0a998-119">HTTPS-only.</span></span>** <span data-ttu-id="0a998-120">Dienstmitarbeiter funktionieren nicht in http; Sie müssen HTTPS verwenden.</span><span class="sxs-lookup"><span data-stu-id="0a998-120">Service workers will not work in HTTP; you will need to use HTTPS.</span></span> <span data-ttu-id="0a998-121">Sie können Dienstmitarbeiter jedoch zu `localhost` Testzwecken registrieren.</span><span class="sxs-lookup"><span data-stu-id="0a998-121">However, you can register service workers on `localhost` for testing purposes.</span></span>

- **<span data-ttu-id="0a998-122">Kein DOM-Zugriff zulässig.</span><span class="sxs-lookup"><span data-stu-id="0a998-122">No DOM access allowed.</span></span>** <span data-ttu-id="0a998-123">Wie bei Web Workern erhalten Sie keinen Zugriff auf das Objektmodell der Seite.</span><span class="sxs-lookup"><span data-stu-id="0a998-123">As with web workers, you don't get access to the page's object model.</span></span> <span data-ttu-id="0a998-124">Das bedeutet, dass Sie, wenn Sie etwas über die Seite ändern müssen, [`postMessage`](https://developer.mozilla.org/docs/Web/API/Worker/postMessage) von der Dienstmitarbeiter auf die Seite verwenden müssen, damit Sie DOM-Änderungen auf der Seite behandeln können.</span><span class="sxs-lookup"><span data-stu-id="0a998-124">This means that if you need to change something about the page, you'll need to use [`postMessage`](https://developer.mozilla.org/docs/Web/API/Worker/postMessage) from the service worker to the page so that you can handle it DOM changes from the page.</span></span>

- **<span data-ttu-id="0a998-125">Führt eine separate Seite aus.</span><span class="sxs-lookup"><span data-stu-id="0a998-125">Executes separate from page.</span></span>** <span data-ttu-id="0a998-126">Da diese Skripts nicht an die Lebensdauer einer Seite gebunden sind, ist es wichtig zu verstehen, dass Sie nicht den gleichen Kontext wie die Seite aufweisen.</span><span class="sxs-lookup"><span data-stu-id="0a998-126">Because these scripts are not tied to the lifetime of a page, it's important to understand that they do not share the same context as the page.</span></span> <span data-ttu-id="0a998-127">Abgesehen davon, dass Sie keinen Zugriff auf das DOM haben (wie bereits erwähnt), haben Sie keinen Zugriff auf die gleichen Variablen, die auf der Seite verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="0a998-127">Aside from not having access to the DOM (as stated earlier), they won't have access to the same variables available on the page.</span></span>

- **<span data-ttu-id="0a998-128">Überschreibt den *App-Cache*.</span><span class="sxs-lookup"><span data-stu-id="0a998-128">Overrides *App Cache*.</span></span>** <span data-ttu-id="0a998-129">Der APP-Cache wird ignoriert, wenn Dienstmitarbeiter verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0a998-129">App Cache will be ignored when service workers are in use.</span></span> <span data-ttu-id="0a998-130">Die Service Worker-API soll den App-Cache vollständig verdrängen, indem Sie dem Web-Entwickler eine genauere Steuerung bietet.</span><span class="sxs-lookup"><span data-stu-id="0a998-130">The Service Worker API is intended to entirely supplant App Cache  by giving more granular control to the web developer.</span></span>

  - **<span data-ttu-id="0a998-131">Das Skript kann nicht auf CDN lauten.</span><span class="sxs-lookup"><span data-stu-id="0a998-131">Script can't be on CDN.</span></span>** <span data-ttu-id="0a998-132">Die JavaScript-Datei für den Dienstmitarbeiter kann nicht in einem Inhalts Verteilungsnetzwerk (CDN) gehostet werden, sondern muss sich in der gleichen Domäne wie die Seite befinden.</span><span class="sxs-lookup"><span data-stu-id="0a998-132">The JavaScript file for the service worker can't be hosted on a Content Distribution Network (CDN), it must be on the same domain as the page.</span></span> <span data-ttu-id="0a998-133">Wenn Sie möchten, können Sie jedoch Skripts aus Ihrem CDN importieren.</span><span class="sxs-lookup"><span data-stu-id="0a998-133">However, if you like, you can import scripts from your CDN.</span></span>

- **<span data-ttu-id="0a998-134">Kann jederzeit gekündigt werden.</span><span class="sxs-lookup"><span data-stu-id="0a998-134">Can be terminated any time.</span></span>** <span data-ttu-id="0a998-135">Dienstmitarbeiter sollen kurzlebig sein und ihre Lebenszeit ist an Ereignisse gebunden.</span><span class="sxs-lookup"><span data-stu-id="0a998-135">Service workers are meant to be short-lived and their lifetime is tied to events.</span></span> <span data-ttu-id="0a998-136">Insbesondere können Servicemitarbeiter ein Zeitlimit angeben, in dem Sie die Ausführung ihrer Ereignishandler beenden müssen.</span><span class="sxs-lookup"><span data-stu-id="0a998-136">In particular, service workers have a time limit in which they must finish executing their event handlers.</span></span> <span data-ttu-id="0a998-137">In anderen Fällen kann es vorkommen, dass der Browser oder das Betriebssystem einen Dienstmitarbeiter beendet, der sich auf die Akku-, CPU-oder Speicherauslastung auswirkt.</span><span class="sxs-lookup"><span data-stu-id="0a998-137">In other cases, the browser or the operating system may choose to terminate a service worker that impacts the battery, CPU, or memory consumption.</span></span> <span data-ttu-id="0a998-138">Vermeiden Sie in beiden Fällen die Verwendung globaler Variablen im Service Worker-Skript, wenn für ein nachfolgendes Ereignis, das verarbeitet wird, eine andere Dienst Arbeitskraft-Instanz verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="0a998-138">In either case, avoid relying on global variables in the service worker script in case a different service worker instance is used on a subsequent event that's being handled.</span></span>

- **<span data-ttu-id="0a998-139">Nur asynchrone Anforderungen zulässig.</span><span class="sxs-lookup"><span data-stu-id="0a998-139">Only asynchronous requests allowed.</span></span>** <span data-ttu-id="0a998-140">Synchrone XMLHttpRequest ist hier nicht zulässig!</span><span class="sxs-lookup"><span data-stu-id="0a998-140">Synchronous XHR is not allowed here!</span></span> <span data-ttu-id="0a998-141">Weder ist localStorage, daher empfiehlt es sich, IndexedDB und die zuvor beschriebene neue Caches-API zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="0a998-141">Neither is localStorage, so it's best to make use of IndexedDB and the new Caches API described earlier.</span></span>

- **<span data-ttu-id="0a998-142">Der Dienstmitarbeiter für den Bereich ist 1:1.</span><span class="sxs-lookup"><span data-stu-id="0a998-142">Service worker to scope is 1:1.</span></span>** <span data-ttu-id="0a998-143">Sie können nur einen Dienstmitarbeiter pro Bereich haben.</span><span class="sxs-lookup"><span data-stu-id="0a998-143">You'll only be able to have one service worker per scope.</span></span> <span data-ttu-id="0a998-144">Das bedeutet, wenn Sie versuchen, einen anderen Dienstmitarbeiter für einen Bereich zu registrieren, der bereits über einen Dienstmitarbeiter verfügt, wird dieser Dienstmitarbeiter aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="0a998-144">That means if you try to register a different service worker for a scope that already has a service worker, that service worker will be updated.</span></span>