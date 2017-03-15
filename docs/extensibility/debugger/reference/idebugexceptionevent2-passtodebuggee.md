---
title: "IDebugExceptionEvent2::PassToDebuggee | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExceptionEvent2::PassToDebuggee"
helpviewer_keywords: 
  - "IDebugExceptionEvent2::PassToDebuggee"
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugExceptionEvent2::PassToDebuggee
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

実行を再開したときまたは例外が破棄例外をデバッグ中のプログラムに渡す必要があるかどうかを指定します。  
  
## 構文  
  
```cpp#  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```c#  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### パラメーター  
 `fPass`  
 \[入力\] 例外が破棄実行を再開すると例外がデバッグ対象のプログラムに渡された場合 \(\)`TRUE` 場合はゼロ \(`FALSE`\)。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドを呼び出して実際にはコードをデバッグするプログラムの実行されません。  呼び出しは次のコードの実行の状態を設定します。  たとえば[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) メソッドの呼び出しが [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) を除く `S_OK` を返すことがあります。`EXCEPTION_STOP_SECOND_CHANCE` への `dwState` のフィールド セット。  
  
 IDE で [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) イベントを受け取り[続行](../../../extensibility/debugger/reference/idebugprogram2-continue.md) メソッドを呼び出すことがあります。  デバッグ エンジンは \(DE\)`PassToDebuggee` のメソッドが呼び出されなかった場合既定の動作が必要です。  
  
## 参照  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [続行](../../../extensibility/debugger/reference/idebugprogram2-continue.md)