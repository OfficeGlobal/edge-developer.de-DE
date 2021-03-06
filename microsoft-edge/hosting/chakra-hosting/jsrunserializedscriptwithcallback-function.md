---
description: Führt ein serialisiertes Skript aus. Bietet die Möglichkeit, die Skript Quelle nur verzögert zu laden, wenn/wann dies erforderlich ist.
title: JsRunSerializedScriptWithCallback-Funktion | Microsoft docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: microsoft-edge
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0608d778-f65b-4dc5-a745-364aac57ef59
caps.latest.revision: 4
author: MSEdgeTeam
ms.author: msedgedevrel
manager: ''
ms.openlocfilehash: 31669615d5e00cb2dbe3730ed20e24d904161f8b
ms.sourcegitcommit: 6860234c25a8be863b7f29a54838e78e120dbb62
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2020
ms.locfileid: "10568331"
---
# JsRunSerializedScriptWithCallback-Funktion
Führt ein serialisiertes Skript aus. Bietet die Möglichkeit, die Skript Quelle nur verzögert zu laden, wenn/wann dies erforderlich ist.  
  
## Syntax  
  
```cpp  
STDAPI_(JsErrorCode) JsRunSerializedScriptWithCallback(  
  _In_ JsSerializedScriptLoadSourceCallback scriptLoadCallback,  
  _In_ JsSerializedScriptUnloadCallback scriptUnloadCallback,  
  _In_ BYTE *buffer,  
  _In_ JsSourceContext sourceContext,  
  _In_z_ const wchar_t *sourceUrl,  
  _Out_opt_ JsValueRef *result  
);  
  
```  
  
#### Parameter  
 `scriptLoadCallback`  
 Der Rückruf wird aufgerufen, wenn der Quellcode des Skripts geladen werden muss.  
  
 `scriptUnloadCallback`  
 Rückruf, der aufgerufen wird, wenn das serialisierte Skript und der Quellcode nicht mehr benötigt werden.  
  
 `buffer`  
 Das serialisierte Skript.  
  
 `sourceContext`  
 Ein Cookie, das das Skript identifiziert, das von debugfähigen-Skript Kontexten verwendet werden kann.     Dieser Kontext wird an scriptLoadCallback und scriptUnloadCallback übergeben.  
  
 `sourceUrl`  
 Der Speicherort, aus dem das Skript kam.  
  
 `result`  
 Das Ergebnis der Ausführung des Skripts (sofern vorhanden). Dieser Parameter kann NULL sein.  
  
## Rückgabewert  
 Der Code `JsNoError` , wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
  
> [!NOTE]
>  Diese API steht noch nicht für Store-Apps zur Verfügung.  
  
 Erfordert einen aktiven Skriptkontext.  
  
 Die Laufzeit bleibt auf dem Puffer, bis alle Instanzen von Funktionen, die aus dem Puffer erstellt wurden, als Garbage Collection erfasst werden.  Anschließend wird scriptUnloadCallback aufgerufen, um den Anrufer darüber zu informieren, dass es sicher freigegeben werden kann.  
  
## Anforderungen  
 **Kopfzeile:** jsrt. h  
  
## Weitere Informationen  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)