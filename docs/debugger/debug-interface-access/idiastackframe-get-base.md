---
title: "IDiaStackFrame::get_base | Microsoft Docs"
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
  - "IDiaStackFrame::get_base メソッド"
ms.assetid: f27477d7-26fe-4c1c-a08a-c52cb20c8293
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackFrame::get_base
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

フレームのベース アドレスを取得します。  
  
## 構文  
  
```cpp#  
HRESULT get_base (   
   ULONGLONG* pRetVal  
);  
```  
  
#### パラメーター  
 `pRetVal`  
 \[入力\] ベース アドレスを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` プロパティがサポートされていない場合 `S_FALSE` を返します。  それ以外の場合はエラー コード。  
  
## 参照  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)