---
title: "IDiaSymbol::get_offset | Microsoft Docs"
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
  - "IDiaSymbol::get_offset メソッド"
ms.assetid: 8292bb08-4dc8-4663-beb4-258f5d5a448d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_offset
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

シンボルの場所のオフセットを取得します。  [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md) が `LocIsRegRel` または `LocIsBitField` である場合はを使用します。  
  
## 構文  
  
```cpp#  
HRESULT get_offset (   
   LONG* pRetVal  
);  
```  
  
#### パラメーター  
 `pRetVal`  
 \[入力\] シンボルの場所のバイト オフセットを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合戻り `S_FALSE` またはエラー コード。  
  
> [!NOTE]
>  `S_FALSE` の戻り値はプロパティのシンボルで使用できないことを意味します。  
  
## 解説  
 オフセットはあらかじめ定義した既知の点からです。  たとえば`LocIsBitField` の場所の種類のオフセットはコンテナー クラス先頭からです。  
  
## 必要条件  
  
|必要条件|Description|  
|----------|-----------------|  
|ヘッダー:|dia2.h|  
|バージョン :|DIA SDK v7.0|  
  
## 参照  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)