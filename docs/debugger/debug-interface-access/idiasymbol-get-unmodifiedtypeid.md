---
title: "IDiaSymbol::get_unmodifiedTypeId | Microsoft Docs"
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
ms.assetid: 4f7fc73c-f524-4d7a-b378-a9ab99a96104
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_unmodifiedTypeId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

元の \(非修飾\) 型 ID を取得します。  
  
## 構文  
  
```cpp  
HRESULT get_unmodifiedTypeId(   
   DWORD* pRetVal);  
```  
  
#### パラメーター  
 `pRetVal`  
 \[入力\] ID を保持する `DWORD` へのポインター。  
  
## 戻り値  
 成功した場合は `S_OK` を返し、それ以外の場合は `S_FALSE` またはエラー コードを返します。  
  
## 参照  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)