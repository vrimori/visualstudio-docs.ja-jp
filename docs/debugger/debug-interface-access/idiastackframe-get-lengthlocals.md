---
title: "IDiaStackFrame::get_lengthLocals | Microsoft Docs"
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
  - "IDiaStackFrame::get_lengthLocals メソッド"
ms.assetid: dbc3e544-578a-4f0b-8d20-f21ad4cbb604
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaStackFrame::get_lengthLocals
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

スタックにプッシュされるローカル変数の数を取得します。  
  
## 構文  
  
```cpp#  
HRESULT get_lengthLocals (   
   DWORD* pRetVal  
);  
```  
  
#### パラメーター  
 `pRetVal`  
 \[入力\] ローカル変数のバイト数を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` プロパティがサポートされていない場合 `S_FALSE` を返します。  それ以外の場合はエラー コード。  
  
## 参照  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)