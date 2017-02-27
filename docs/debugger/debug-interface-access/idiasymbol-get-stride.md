---
title: "IDiaSymbol::get_stride | Microsoft Docs"
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
ms.assetid: 4264742a-3d91-44b9-9d14-87adbc77f0f0
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_stride
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

行列または strided 配列のストライドを取得します。  
  
## 構文  
  
```cpp  
HRESULT get_stride(   
   DWORD* pRetVal);  
```  
  
#### パラメーター  
 `pRetVal`  
 \[入力\] ストライドを保持する `DWORD` へのポインター。  
  
## 戻り値  
 成功した場合は `S_OK` を返し、それ以外の場合は `S_FALSE` またはエラー コードを返します。  
  
## 参照  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)