---
title: "IDiaSymbol::get_samplerSlot | Microsoft Docs"
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
ms.assetid: 41c751ba-81be-4bd3-838f-8373fc146157
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_samplerSlot
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

サンプラー スロットを取得します。  
  
## 構文  
  
```cpp  
HRESULT get_samplerSlot(   
   DWORD* pRetVal);  
```  
  
#### パラメーター  
 `pRetVal`  
 \[入力\] サンプラー スロットを保持 `DWORD` へのポインター。  
  
## 戻り値  
 成功した場合は `S_OK` を返し、それ以外の場合は `S_FALSE` またはエラー コードを返します。  
  
## 参照  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)