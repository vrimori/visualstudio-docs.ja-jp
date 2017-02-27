---
title: "IDiaSymbol::get_access | Microsoft Docs"
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
  - "IDiaSymbol::get_access メソッド"
ms.assetid: 908976ae-95c4-4020-89c9-de137f727f98
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_access
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

クラス メンバーのアクセス修飾子を取得します。  
  
## 構文  
  
```cpp#  
HRESULT get_access (   
   DWORD* pRetVal  
);  
```  
  
#### パラメーター  
 `pRetVal`  
 \[入力\] クラス メンバーのアクセス修飾子を指定する [CV\_access\_e 列挙型](../../debugger/debug-interface-access/cv-access-e.md) の列挙型の値を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合戻り `S_FALSE` またはエラー コード。  
  
> [!NOTE]
>  `S_FALSE` の戻り値はプロパティのシンボルで使用できないことを意味します。  
  
## 必要条件  
  
|必要条件|Description|  
|----------|-----------------|  
|ヘッダー:|dia2.h|  
|バージョン :|DIA SDK v7.0|  
  
## 参照  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CV\_access\_e 列挙型](../../debugger/debug-interface-access/cv-access-e.md)