---
title: "IDiaSymbol::get_constType | Microsoft Docs"
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
  - "IDiaSymbol::get_constType メソッド"
ms.assetid: cb43605e-fa39-4f83-b047-f936a8019d03
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_constType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ユーザー定義データ型が設定されているかどうかを指定するフラグを取得します。  
  
## 構文  
  
```cpp#  
HRESULT get_constType (   
   BOOL* pRetVal  
);  
```  
  
#### パラメーター  
 `pRetVal`  
 \[入力\] ユーザー定義データ型が設定している場合はを返します `TRUE` ; それ以外の場合戻り `FALSE`。  
  
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