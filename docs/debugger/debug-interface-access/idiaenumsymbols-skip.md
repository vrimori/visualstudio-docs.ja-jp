---
title: "IDiaEnumSymbols::Skip | Microsoft Docs"
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
  - "IDiaEnumSymbols::Skip メソッド"
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSymbols::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

列挙体シーケンス内のシンボルの指定した数の要素をスキップします。  
  
## 構文  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### パラメーター  
 celt  
 \[入力\] スキップ列挙体シーケンス内のシンボルの数。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; これはスキップ以上のシンボルが存在しない場合戻り `S_FALSE`。  
  
## 参照  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)