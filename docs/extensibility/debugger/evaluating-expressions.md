---
title: "式を評価します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "評価する式を [デバッグの SDK]"
  - "[デバッグ SDK] の式の評価のデバッグ"
  - "式の評価"
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 式を評価します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

式は自動変数\]\[ウォッチ\]\[クイック ウォッチ\]または \[イミディエイト\] ウィンドウから渡された文字列で作成されます。  式を評価すると変数の名前と型引数と値を含む出力する文字列を生成します。  この文字列は対応する IDE ウィンドウに表示されます。  
  
## 実装  
 式はプログラムがブレークポイントで停止して評価されます。  式自体は指定した式の評価コンテキスト内のバインディングと評価の準備が整った解析された式を表す [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) のインターフェイスで表されます。  スタック フレームは [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) のインターフェイスを実装してデバッグ エンジン \(DE\) 指定式の評価のコンテキストを指定します。  
  
 ユーザーが文字列と [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) のインターフェイスはデバッグ エンジンは \(DE\)[IDebugExpressionContext2:: ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) のメソッドにユーザー文字列を渡すことによって [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) のインターフェイスを取得できます。  返されるインターフェイスは評価 IDebugExpression2 終了準備完了の解析された式を含みます。  
  
 `IDebugExpression2` のインターフェイスを使用するとde\-DE は [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) または [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) を使用すると同期または非同期式を評価して式の値を取得できます。  変数または引数の名前および型とともにこの値は表示のためにIDE に送信されます。  値型は名前と [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) のインターフェイスによって表されます。  
  
 式の評価を有効にするにはde\-DE [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) は[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) のインターフェイスを実装する必要があります。  同期および非同期の評価は [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) のメソッドの実装が必要です。  
  
## 参照  
 [スタック フレーム](../../extensibility/debugger/stack-frames.md)   
 [式の評価コンテキスト](../../extensibility/debugger/expression-evaluation-context.md)   
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)