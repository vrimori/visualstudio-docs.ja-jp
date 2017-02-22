---
title: "IDiaEnumFrameData::Next | Microsoft Docs"
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
  - "IDiaEnumFrameData::Next メソッド"
ms.assetid: 546e2e23-efb2-425a-96a1-808c67c519fb
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumFrameData::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

列挙体シーケンスのフレームのデータ指定された数の要素を取得します。  
  
## 構文  
  
```cpp#  
HRESULT Next (   
   ULONG           celt,   
   IDiaFrameData** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
#### パラメーター  
 celt  
 \[出力\] 取得された列挙子フレームのデータ要素数。  
  
 rgelt  
 \[入力\] [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) の配列は要求されたフレームのデータ要素を挿入する方法について説明します。  
  
 pceltFetched  
 \[入力\] 取得する列挙子フレームのデータ要素数を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` 次のレコードがある `S_FALSE` を返します。  それ以外の場合はエラー コード。  
  
## 参照  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)