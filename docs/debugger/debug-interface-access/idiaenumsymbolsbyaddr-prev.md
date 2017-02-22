---
title: "IDiaEnumSymbolsByAddr::Prev | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumSymbolsByAddr::Prev メソッド"
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSymbolsByAddr::Prev
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

アドレスで順序で前のシンボルを取得します。  
  
## 構文  
  
```cpp#  
HRESULT Prev (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### パラメーター  
 celt  
 \[出力\] 取得された列挙子のシンボルの数。  
  
 rgelt  
 \[入力\] 目的のシンボルを表します [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) のオブジェクトが格納された配列。  
  
 pceltFetched  
 \[入力\] 列挙子のフェッチ シンボルの数を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` 前のシンボルがある `S_FALSE` を返します。  それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドはフェッチ要素数列挙子の位置を更新します。  
  
## 参照  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)