---
title: "IJsDebugFrame::GetStackRange メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetStackRange
apilocation: jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::GetStackRange メソッド
Returns the absolute address range of the logical JavaScript stack frame.  
  
## 構文  
  
```  
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### パラメーター  
 `pStart`  
 \[出力\] フレームの末尾のスタック ポインター。  
  
 `pEnd`  
 \[出力\] フレームの先頭のスタック ポインター。  
  
## 戻り値  
  
## 解説  
 このメソッドは、複数のランタイムから収集されインタリーブ化されたスタック トレースを統合する場合に役立ちます。  先頭と末尾のスタック ポインター間に複数の物理マシンのスタック フレームを格納できます \(解釈済みの JavaScript ランタイム フレームの場合\)。先頭のスタック ポインター \> 末尾のスタック ポインターとなるのは、スタックが高位アドレスから低位アドレスへと伸びていくためです。  
  
## 必要条件  
 **Header:** jscript9diag.h  
  
## 参照  
 [IJsDebugFrame インターフェイス](../../winscript/reference/ijsdebugframe-interface.md)