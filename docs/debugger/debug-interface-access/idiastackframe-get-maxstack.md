---
title: "IDiaStackFrame::get_maxStack | Microsoft Docs"
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
  - "IDiaStackFrame::get_maxStack メソッド"
ms.assetid: 6352e972-7105-4d0e-aeba-b8fc16d62dec
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaStackFrame::get_maxStack
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

フレームのスタックにプッシュされる最大バイト数を取得します。  
  
## 構文  
  
```cpp#  
HRESULT get_maxStack (   
   DWORD* pRetVal  
);  
```  
  
#### パラメーター  
 `pRetVal`  
 \[入力\] スタックにプッシュされる最大バイト数を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` プロパティがサポートされていない場合 `S_FALSE` を返します。  それ以外の場合はエラー コード。  
  
## 参照  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)