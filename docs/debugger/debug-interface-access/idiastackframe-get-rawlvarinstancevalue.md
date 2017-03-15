---
title: "IDiaStackFrame::get_rawLVarInstanceValue | Microsoft Docs"
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
  - "IDiaStackFrame::get_rawLVarInstanceValue メソッド"
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaStackFrame::get_rawLVarInstanceValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

このメソッドは生バイトとして指定したローカル変数の値を取得します。  
  
## 構文  
  
```cpp#  
HRESULT get_rawLVarInstanceValue(  
   IDiaLVarInstance* pInstance,  
   DWORD             cbDataMax,  
   DWORD*            pcbData,  
   BYTE*             pbData  
);  
```  
  
#### パラメーター  
 `pInstance`  
 \[入力\] `IDiaLVarInstance` 表すオブジェクトの値を取得するローカル変数のインスタンス。  
  
 `cbDataMax`  
 \[入力\] バッファーの最大バイト数は `pbData` によってします。  これは最大 8 バイト \(`sizeof(ULONGLONG)`\) です。  
  
 `pcbData`  
 \[入力\] バッファーに格納される実際のバイト数を返します。  
  
 `pbData`  
 \[入力\] データが格納されるバッファー。  これには、`NULL` を指定することはできません。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)