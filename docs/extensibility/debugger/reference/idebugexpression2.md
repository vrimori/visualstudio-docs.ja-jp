---
title: "IDebugExpression2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpression2"
helpviewer_keywords: 
  - "IDebugExpression2 インターフェイス"
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpression2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはバインド評価し終了準備完了の解析された式を表します。  
  
## 構文  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジンは評価 \(DE\) できる状態となります。解析された式を表すためこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) の呼び出しはこのインターフェイスを返します。  [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) は [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) のインターフェイスを返します。  これらのインターフェイスはプログラムのデバッグを停止スタック フレームが使用できる場合にのみアクセスできます。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugExpression2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|この式を非同期的に評価されます。|  
|[\[中止\]](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|非同期式の評価を終了します。|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|この式を同期的に評価されます。|  
  
## 解説  
 プログラムが終了するとデバッグ セッション マネージャーは \(SDM\) を呼び出してからします [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) にスタック フレームを取得します。  SDM は[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) のインターフェイスを取得するに [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) を呼び出します。  これは [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) の呼び出しに評価できる状態となります。解析された式を表す `IDebugExpression2` のインターフェイスを作成するように指定します。  
  
 SDM は式を評価し値を生成するために [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) または [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) を呼び出します。  
  
 `IDebugExpressionContext2::ParseText` の実装では式エバリュエーターをインスタンス化しインターフェイスを取得します [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) で使用する COM `CoCreateInstance` の関数 \(`IDebugExpressionEvaluator` のインターフェイスの例を参照\)。  DE は[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) のインターフェイスを取得するに [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) を呼び出します。  `IDebugExpression2::EvaluateSync` と `IDebugExpression2::EvaluateAsync` の実装でこのインターフェイスの評価を実行するために使用されます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)