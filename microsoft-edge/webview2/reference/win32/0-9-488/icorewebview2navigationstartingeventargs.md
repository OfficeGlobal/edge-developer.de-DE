---
description: Hosten von Webinhalten in ihrer Win32-App mit dem Microsoft Edge WebView2-Steuerelement
title: Microsoft Edge-WebView2 für Win32-apps
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 05/07/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, WebView, Win32-apps, Win32, Edge, ICoreWebView2, ICoreWebView2Controller, Browser-Steuerelement, Edge-HTML
ms.openlocfilehash: 3b348d64bb09fcdc693ffbdfa5481fe6d7520cae
ms.sourcegitcommit: 07cda56425e5fdf90eeb3972e17041261bf720cd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2020
ms.locfileid: "10653781"
---
# Schnittstellen ICoreWebView2NavigationStartingEventArgs 

```
interface ICoreWebView2NavigationStartingEventArgs
  : public IUnknown
```

Ereignis-args für das NavigationStarting-Ereignis.

## Zusammenfassung

 Member                        | Beschreibungen
--------------------------------|---------------------------------------------
[get_Cancel](#get_cancel) | Der Host kann dieses Flag so einstellen, dass die Navigation abgebrochen wird.
[get_IsRedirected](#get_isredirected) | "True", wenn die Navigation umgeleitet wird.
[get_IsUserInitiated](#get_isuserinitiated) | "True", wenn die Navigation im Gegensatz zur programmgesteuerten Navigation durch eine Benutzergeste initiiert wurde.
[get_NavigationId](#get_navigationid) | Die ID der Navigation.
[get_RequestHeaders](#get_requestheaders) | Die HTTP-Anforderungsheader für die Navigation.
[get_Uri](#get_uri) | Der URI der angeforderten Navigation.
[put_Cancel](#put_cancel) | Festlegen der Cancel-Eigenschaft

## Member

#### get_Cancel 

Der Host kann dieses Flag so einstellen, dass die Navigation abgebrochen wird.

> öffentliche HRESULT- [get_Cancel](#get_cancel)(bool * Cancel)

Wenn dies der Fall ist, ist es so, als ob die Navigation nie stattgefunden hat und der Inhalt der aktuellen Seite intakt bleibt. Aus Leistungsgründen können HTTP-Anforderungen auftreten, während der Host reagiert. Das bedeutet, dass Cookies für einen Teil einer Anforderung für die Navigation eingestellt und verwendet werden können.

#### get_IsRedirected 

"True", wenn die Navigation umgeleitet wird.

> öffentliche HRESULT- [get_IsRedirected](#get_isredirected)(bool * isumgeleitet)

#### get_IsUserInitiated 

"True", wenn die Navigation im Gegensatz zur programmgesteuerten Navigation durch eine Benutzergeste initiiert wurde.

> Public HRESULT [get_IsUserInitiated](#get_isuserinitiated)(bool * IsUserInitiated)

#### get_NavigationId 

Die ID der Navigation.

> Public HRESULT [get_NavigationId](#get_navigationid)(UINT64 * navigation_id)

#### get_RequestHeaders 

Die HTTP-Anforderungsheader für die Navigation.

> Public HRESULT [get_RequestHeaders](#get_requestheaders)([ICoreWebView2HttpRequestHeaders](icorewebview2httprequestheaders.md) * * RequestHeaders)

Beachten Sie, dass die HTTP-Anforderungs Kopfzeilen in einem NavigationStarting-Ereignis nicht geändert werden können.

#### get_Uri 

Der URI der angeforderten Navigation.

> Public HRESULT [get_Uri](#get_uri)(LPWSTR * URI)

#### put_Cancel 

Festlegen der Cancel-Eigenschaft

> öffentliche HRESULT- [put_Cancel](#put_cancel)(bool Cancel)

