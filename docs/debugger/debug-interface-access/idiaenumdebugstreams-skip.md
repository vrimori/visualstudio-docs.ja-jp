---
title: "IDiaEnumDebugStreams::Skip | Microsoft Docs"
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
  - "IDiaEnumDebugStreams::Skip メソッド"
ms.assetid: 6ec7753c-d7af-4879-b107-1b3442e0b025
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumDebugStreams::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

列挙体シーケンスのデバッグのストリームから指定した数の要素をスキップします。  
  
## 構文  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### パラメーター  
 `celt`  
 \[入力\] デバッグの数は列挙体シーケンスでスキップするに渡されます。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; これはスキップ以上のレコードがない場合戻り `S_FALSE`。  
  
## 参照  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)