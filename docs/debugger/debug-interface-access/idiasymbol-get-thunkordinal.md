---
title: "IDiaSymbol::get_thunkOrdinal | Microsoft Docs"
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
  - "IDiaSymbol::get_thunkOrdinal メソッド"
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_thunkOrdinal
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

関数のサンクの種類を取得します。  
  
## 構文  
  
```cpp#  
HRESULT get_thunkOrdinal (   
   DWORD* pRetVal  
);  
```  
  
#### パラメーター  
 `pRetVal`  
 \[入力\] 関数のサンクの型を指定する [THUNK\_ORDINAL 列挙型](../../debugger/debug-interface-access/thunk-ordinal.md) の列挙型の値を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合戻り `S_FALSE` またはエラー コード。  
  
> [!NOTE]
>  `S_FALSE` の戻り値はプロパティのシンボルで使用できないことを意味します。  
  
## 解説  
 このプロパティは `SymTagThunk` の [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md) の値としている場合のみシンボルです。  
  
 サンク 「」では32 ビットのメモリ アドレス空間 \(またはフラット アドレス空間\) と 16 ビット アドレス空間の間で変換を行うコード \(ように分割されたアドレス空間\) がわかっている。  
  
## 参照  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [THUNK\_ORDINAL 列挙型](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)