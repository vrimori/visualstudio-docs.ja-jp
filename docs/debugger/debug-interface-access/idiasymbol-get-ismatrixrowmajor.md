---
title: "IDiaSymbol::get_isMatrixRowMajor | Microsoft Docs"
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
ms.assetid: 36b1e881-ea76-48b0-b67f-e9eb0d19bec7
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_isMatrixRowMajor
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

行列が行のメジャーかどうかを指定します。  
  
## 構文  
  
```cpp  
HRESULT get_isMatrixRowMajor(   
   BOOL* pRetVal);  
```  
  
#### パラメーター  
 `pRetVal`  
 \[入力\] 行列は行のメジャーかどうかを指定する `BOOL` へのポインター。  
  
## 戻り値  
 成功した場合は `S_OK` を返し、それ以外の場合は `S_FALSE` またはエラー コードを返します。  
  
## 参照  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)