---
title: "IDiaEnumLineNumbers::Skip | Microsoft Docs"
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
  - "IDiaEnumLineNumbers::Skip メソッド"
ms.assetid: d182c269-8c76-4d8b-8275-c6807c5ae4e1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumLineNumbers::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

列挙体シーケンス内の行番号を指定した数の要素をスキップします。  
  
## 構文  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### パラメーター  
 celt  
 \[入力\] スキップ列挙体シーケンス内の行数。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; はスキップそれ以上行番号がない場合戻り `S_FALSE`。  
  
## 参照  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)