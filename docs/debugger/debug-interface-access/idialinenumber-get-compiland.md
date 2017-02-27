---
title: "IDiaLineNumber::get_compiland | Microsoft Docs"
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
  - "IDiaLineNumber::get_compiland メソッド"
ms.assetid: c476d0b8-c473-47eb-96f5-c4e8f577b1c9
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaLineNumber::get_compiland
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

イメージのテキストのバイトを提供するコンパイル単位のシンボルへの参照を取得します。  
  
## 構文  
  
```cpp#  
HRESULT get_compiland (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### パラメーター  
 pRetVal  
 \[入力\] イメージのテキストのバイトを提供するコンパイル単位の [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) のオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` このプロパティをサポートする必要 `S_FALSE` を返します。  それ以外の場合はエラー コード。  
  
## 参照  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)