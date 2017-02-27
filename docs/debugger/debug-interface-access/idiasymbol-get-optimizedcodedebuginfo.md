---
title: "IDiaSymbol::get_optimizedCodeDebugInfo | Microsoft Docs"
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
helpviewer_keywords: 
  - "IDiaSymbol::get_optimizedCodeDebugInfo メソッド"
ms.assetid: 57ef4170-37a9-46b0-8217-c1a674725113
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_optimizedCodeDebugInfo
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

関数は、最適化されたコードに対して指定されたデバッグ情報を含めるかどうかを示すフラグを取得します。  
  
## 構文  
  
```cpp  
HRESULT get_optimizedCodeDebugInfo(  
   BOOL *pFlag  
);  
```  
  
#### パラメーター  
 `pFlag`  
 \[出力\] 最適化された関数またはラベルにデバッグ情報が含まれている場合は `TRUE` を返します。それ以外の場合は `FALSE` を返します。  
  
## 戻り値  
 成功した場合は `S_OK` を返し、それ以外の場合は `S_FALSE` またはエラー コードを返します。  
  
> [!NOTE]
>  `S_FALSE` の戻り値は、プロパティがシンボルに対して使用できないことを意味します。  
  
## 必要条件  
  
|必要条件|説明|  
|----------|--------|  
|ヘッダー:|dia2.h|  
  
## 参照  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)