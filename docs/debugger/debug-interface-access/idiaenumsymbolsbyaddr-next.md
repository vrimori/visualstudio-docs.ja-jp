---
title: "IDiaEnumSymbolsByAddr::Next | Microsoft Docs"
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
  - "IDiaEnumSymbolsByAddr::Next メソッド"
ms.assetid: a1320587-7ce7-401f-9548-2f8bcece5cc3
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSymbolsByAddr::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

アドレスで次の順序でシンボルを取得します。  
  
## 構文  
  
```cpp#  
HRESULT Next (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### パラメーター  
 celt  
 \[出力\] 取得された列挙子のシンボルの数。  
  
 rgelt  
 \[入力\] [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) のオブジェクトが格納される配列必要なシンボルを表します。  
  
 pceltFetched  
 \[入力\] 列挙子のフェッチ シンボルの数を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` これ以上のシンボルがある `S_FALSE` を返します。  それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドはフェッチ要素数列挙子の位置を更新します。  
  
## 参照  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)