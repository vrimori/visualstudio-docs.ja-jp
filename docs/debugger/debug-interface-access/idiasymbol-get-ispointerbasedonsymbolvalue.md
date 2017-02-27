---
title: "IDiaSymbol::get_isPointerBasedOnSymbolValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 577c8011-9269-4373-8577-b4822a983724
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_isPointerBasedOnSymbolValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

`this` のポインターがシンボル値に基づいているかどうかを指定します。  
  
## 構文  
  
```cpp  
HRESULT get_isPointerBasedOnSymbolValue(   
   BOOL* pRetVal);  
```  
  
#### パラメーター  
 `pRetVal`  
 \[入力\] `this` のポインターは、シンボル値に基づいているかどうかを指定する `BOOL` へのポインター。  
  
## 戻り値  
 成功した場合は `S_OK` を返し、それ以外の場合は `S_FALSE` またはエラー コードを返します。  
  
## 参照  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)