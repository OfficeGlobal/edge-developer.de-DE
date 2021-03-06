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
ms.openlocfilehash: 3ac37f7d90fc03214381b991c8becae602bac738
ms.sourcegitcommit: 07cda56425e5fdf90eeb3972e17041261bf720cd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2020
ms.locfileid: "10653949"
---
# Schnittstellen ICoreWebView2NewBrowserVersionAvailableEventArgs 

> [!NOTE]
> Diese Schnittstelle kann nach der SDK-Version 0.9.430 geändert oder für Versionen nicht verfügbar sein. Die neueste API-Referenz finden Sie unter [Referenz](../../../webview2-api-reference.md) .

```
interface ICoreWebView2NewBrowserVersionAvailableEventArgs
  : public IUnknown
```

Ereignis-args für das NewBrowserVersionAvailable-Ereignis.

## Zusammenfassung

 Member                        | Beschreibungen
--------------------------------|---------------------------------------------
[get_NewVersion](#get_newversion) | Die Browser Versionsinformationen des aktuellen [ICoreWebView2Environment](ICoreWebView2Environment.md).

## Member

#### get_NewVersion 

Die Browser Versionsinformationen des aktuellen [ICoreWebView2Environment](ICoreWebView2Environment.md).

> Public HRESULT [get_NewVersion](#get_newversion)(LPWSTR *-Version)

