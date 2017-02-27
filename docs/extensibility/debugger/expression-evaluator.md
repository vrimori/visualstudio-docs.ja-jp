---
title: "式エバリュエーター | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "式 [SDK のデバッグ]"
  - "[デバッグ SDK] の式の評価のデバッグ"
  - "式の評価"
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# 式エバリュエーター
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

式エバリュエーターは \(EE\)IDE が中断モードの実行時に変数と式を解析し評価する言語の構文を確認してユーザーに表示することができます。  
  
## 式エバリュエーターを使用する  
 式は [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) のメソッドを使用して次のように作成されます :  
  
1.  デバッグ エンジンは \(DE\)[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) のインターフェイスを実装します。  
  
2.  デバッグのパッケージは [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) のインターフェイスを `IDebugExpressionContext2` のオブジェクトを取得し[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) のオブジェクトを取得するための `IDebugStackFrame2::ParseText` のメソッドを呼び出します。  
  
3.  デバッグのパッケージは [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) のメソッドや式の値を取得するに [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) のメソッドを呼び出します。  `IDebugExpression2::EvaluateAsync` はコマンドまたは \[イミディエイト\] ウィンドウから呼び出されます。  他のすべての UI コンポーネントの呼び出し `IDebugExpression2::EvaluateSync`。  
  
4.  式の評価の結果は二つの式の評価の結果タイプ名と値を含む [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) のオブジェクトです。  
  
 式の評価中にEE はシンボルのプロバイダー コンポーネントの情報を必要とします。  シンボルのプロバイダーは解析された式を識別および理解するために使用するシンボル情報を提供します。  
  
 非同期式の評価が完了したら IDE に通知するために式の評価が完了すると非同期イベントはデバッグ セッションのマネージャー \(SDM\) を使用して de\-DE に送られます。  同期式の評価が完了すると評価の結果は `IDebugExpression2::EvaluateSync` の呼び出しからメソッドに戻ります。  
  
## 実装のメモ  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のデバッグ エンジンは共通言語ランタイムのインターフェイスを使用して式エバリュエーターと通信 \(CLR\) することを想定しています。  その結果[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のデバッグ エンジンを使用した式エバリュエーターはCLR をサポートする必要があります \(すべての CLR のデバッグ インターフェイスの完全なリストを [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] の一部である debugref.doc を参照してください。  
  
## 参照  
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)