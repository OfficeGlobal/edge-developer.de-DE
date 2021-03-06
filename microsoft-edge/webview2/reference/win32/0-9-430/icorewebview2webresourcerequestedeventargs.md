---
description: Hosten von Webinhalten in ihrer Win32-App mit dem Microsoft Edge WebView2-Steuerelement
title: Microsoft Edge-WebView2 für Win32-apps
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 02/26/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, WebView, Win32-apps, Win32, Edge, ICoreWebView2, ICoreWebView2Host, Browser-Steuerelement, Edge-HTML
ms.openlocfilehash: 59557ca86e8b044fb937fe93b3060c0879abb6f1
ms.sourcegitcommit: 07cda56425e5fdf90eeb3972e17041261bf720cd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2020
ms.locfileid: "10654041"
---
# Schnittstellen ICoreWebView2WebResourceRequestedEventArgs 

> [!NOTE]
> Diese Schnittstelle kann nach der SDK-Version 0.9.430 geändert oder für Versionen nicht verfügbar sein. Die neueste API-Referenz finden Sie unter [Referenz](../../../webview2-api-reference.md) .

```
interface ICoreWebView2WebResourceRequestedEventArgs
  : public IUnknown
```

Ereignis-args für das WebResourceRequested-Ereignis.

## Zusammenfassung

 Member                        | Beschreibungen
--------------------------------|---------------------------------------------
[get_Request](#get_request) | Die HTTP-Anforderung.
[get_Response](#get_response) | Die HTTP-Antwort.
[put_Response](#put_response) | Festlegen der Response-Eigenschaft
[GetDeferral](#getdeferral) | Rufen Sie ein [ICoreWebView2Deferral](ICoreWebView2Deferral.md) -Objekt ab, und setzen Sie das Ereignis in einen verzögerten Zustand.
[get_ResourceContext](#get_resourcecontext) | Der Webressource-Anforderungskontext.

## Member

#### get_Request 

Die HTTP-Anforderung.

> öffentliche HRESULT- [get_Request](#get_request)([ICoreWebView2WebResourceRequest](ICoreWebView2WebResourceRequest.md) * * Request)

#### get_Response 

Die HTTP-Antwort.

> öffentliche HRESULT- [get_Response](#get_response)([ICoreWebView2WebResourceResponse](ICoreWebView2WebResourceResponse.md) * * Response)

#### put_Response 

Festlegen der Response-Eigenschaft

> öffentliche HRESULT- [put_Response](#put_response)([ICoreWebView2WebResourceResponse](ICoreWebView2WebResourceResponse.md) * Response)

#### GetDeferral 

Rufen Sie ein [ICoreWebView2Deferral](ICoreWebView2Deferral.md) -Objekt ab, und setzen Sie das Ereignis in einen verzögerten Zustand.

> öffentliche HRESULT [getstundung](#getdeferral)([ICoreWebView2Deferral](ICoreWebView2Deferral.md) * * Stundung)

Sie können das [ICoreWebView2Deferral](ICoreWebView2Deferral.md) -Objekt verwenden, um die Netzwerkanforderung zu einem späteren Zeitpunkt abzuschließen.

#### get_ResourceContext 

Der Webressource-Anforderungskontext.

> öffentliche HRESULT- [get_ResourceContext](#get_resourcecontext)(CORE_WEBVIEW2_WEB_RESOURCE_CONTEXT *-Kontext)

