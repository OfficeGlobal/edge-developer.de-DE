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
ms.openlocfilehash: 8cdedd8051f52b7f6ad187ec948eabef96c6670b
ms.sourcegitcommit: 07cda56425e5fdf90eeb3972e17041261bf720cd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2020
ms.locfileid: "10653761"
---
# Schnittstellen ICoreWebView2WebResourceRequestedEventArgs 

```
interface ICoreWebView2WebResourceRequestedEventArgs
  : public IUnknown
```

Ereignis-args für das WebResourceRequested-Ereignis.

## Zusammenfassung

 Member                        | Beschreibungen
--------------------------------|---------------------------------------------
[get_Request](#get_request) | Die HTTP-Anforderung.
[get_ResourceContext](#get_resourcecontext) | Der Webressource-Anforderungskontext.
[get_Response](#get_response) | Die HTTP-Antwort.
[GetDeferral](#getdeferral) | Rufen Sie ein [ICoreWebView2Deferral](icorewebview2deferral.md) -Objekt ab, und setzen Sie das Ereignis in einen verzögerten Zustand.
[put_Response](#put_response) | Festlegen der Response-Eigenschaft

## Member

#### get_Request 

Die HTTP-Anforderung.

> öffentliche HRESULT- [get_Request](#get_request)([ICoreWebView2WebResourceRequest](icorewebview2webresourcerequest.md) * * Request)

#### get_ResourceContext 

Der Webressource-Anforderungskontext.

> öffentliche HRESULT- [get_ResourceContext](#get_resourcecontext)(COREWEBVIEW2_WEB_RESOURCE_CONTEXT *-Kontext)

#### get_Response 

Die HTTP-Antwort.

> öffentliche HRESULT- [get_Response](#get_response)([ICoreWebView2WebResourceResponse](icorewebview2webresourceresponse.md) * * Response)

#### GetDeferral 

Rufen Sie ein [ICoreWebView2Deferral](icorewebview2deferral.md) -Objekt ab, und setzen Sie das Ereignis in einen verzögerten Zustand.

> öffentliche HRESULT [getstundung](#getdeferral)([ICoreWebView2Deferral](icorewebview2deferral.md) * * Stundung)

Sie können das [ICoreWebView2Deferral](icorewebview2deferral.md) -Objekt verwenden, um die Netzwerkanforderung zu einem späteren Zeitpunkt abzuschließen.

#### put_Response 

Festlegen der Response-Eigenschaft

> öffentliche HRESULT- [put_Response](#put_response)([ICoreWebView2WebResourceResponse](icorewebview2webresourceresponse.md) * Response)

