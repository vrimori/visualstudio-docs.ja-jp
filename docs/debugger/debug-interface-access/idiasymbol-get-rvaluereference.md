---
title: "IDiaSymbol::get_RValueReference | Microsoft Docs"
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
  - "IDiaSymbol::get_RValueReference メソッド"
ms.assetid: c6c8c543-253e-4c23-a939-3e66f3db0ee2
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IDiaSymbol::get_RValueReference
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ポインター型はrvalue 参照であるかどうかを指定するフラグを取得します。  [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md) がポインター型に設定されている場合はを使用します。  
  
## 構文  
  
```cpp#  
HRESULT get_RValueReference (  
   BOOL* pRetVal  
);  
```  
  
#### パラメーター  
 `pRetVal`  
 \[出力\] ポインターが rvalue 参照の場合はを返します `TRUE` ; それ以外の場合戻り `FALSE`。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合戻り `S_FALSE` またはエラー コード。  
  
> [!NOTE]
>  `S_FALSE` の戻り値はプロパティのシンボルで使用できないことを意味します。  
  
## 解説  
  
## 必要条件  
 ヘッダー : Dia2.h  
  
 ライブラリ : diaguids.lib  
  
 DLL: msdia100.dll  
  
## 参照  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)