---
description: Der JsRT-Rückruf, der aufgerufen werden soll, wobei der Kontext an `JsProjectionEnqueueCallback` den richtigen Thread übergeben wird.
title: JsProjectionCallback typedef | Microsoft docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: microsoft-edge
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 32f22d37-e57e-4196-b6cd-a3fc75bd0632
caps.latest.revision: 3
author: MSEdgeTeam
ms.author: msedgedevrel
manager: ''
ms.openlocfilehash: b30f9a7dc4671896eeacecbf58ef88f0383e9e7e
ms.sourcegitcommit: 6860234c25a8be863b7f29a54838e78e120dbb62
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2020
ms.locfileid: "10567211"
---
# JsProjectionCallback typedef
Der JsRT-Rückruf, der aufgerufen werden soll, wobei der Kontext an `JsProjectionEnqueueCallback` den richtigen Thread übergeben wird.  
  
## Syntax  
  
```cpp  
typedef void (CALLBACK *JsProjectionCallback)(  
  _In_ JsProjectionCallbackContext jsContext  
);  
```  
  
#### Parameter  
 `jsContext`  
 Erfordert Anrufe `JsSetProjectionEnqueueCallback` , um Rückrufe zu empfangen.  
  
## Hinweise  
 Diese API wird nur im EdgeHTML-Modus unterstützt.  
  
## Anforderungen  
 jsrt. h  
  
## Weitere Informationen  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)