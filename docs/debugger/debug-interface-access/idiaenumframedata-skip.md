---
title: "IDiaEnumFrameData::Skip | Microsoft Docs"
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
  - "IDiaEnumFrameData::Skip メソッド"
ms.assetid: 67140b4c-7125-4895-932d-42412326da29
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumFrameData::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

列挙体シーケンスのフレームのデータ指定した数の要素をスキップします。  
  
## 構文  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### パラメーター  
 celt  
 \[入力\] スキップ列挙体シーケンス内のフレームのデータ要素数。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; これはスキップ以上のレコードがない場合戻り `S_FALSE`。  
  
## 参照  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)