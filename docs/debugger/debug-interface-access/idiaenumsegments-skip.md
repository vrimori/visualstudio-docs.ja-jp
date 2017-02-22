---
title: "IDiaEnumSegments::Skip | Microsoft Docs"
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
  - "IDiaEnumSegments::Skip メソッド"
ms.assetid: ec67039f-da8c-4e70-8db7-957d7d5281e8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSegments::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

列挙体シーケンス内の指定した数のセグメントをスキップします。  
  
## 構文  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### パラメーター  
 celt  
 \[入力\] スキップ列挙体シーケンス内の線分の数。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; これはスキップ以上のセグメントが存在しない場合戻り `S_FALSE`。  
  
## 参照  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)