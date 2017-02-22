---
title: "IDebugParsedExpression | Microsoft Docs"
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
  - "IDebugParsedExpression"
helpviewer_keywords: 
  - "IDebugParsedExpression インターフェイス"
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugParsedExpression
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 このインターフェイスは、評価する準備が解析された式を表します。  
  
## 構文  
  
```  
IDebugParsedExpression : IUnknown  
```  
  
## 実装についてのメモ  
 式エバリュエーターでは、評価の準備が整った解析された式を表すためには、このインターフェイスを実装します。  
  
## 呼び出し元のノート  
 呼び出し [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) このインターフェイスを返します。  
  
## Vtable 順序のメソッド  
 次の表は、メソッドの `IDebugParsedExpression`です。  
  
|メソッド|説明|  
|----------|--------|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|解析された式を評価します。|  
  
## 解説  
 それを呼び出す呼び出し元の式を評価する準備ができたら [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) を返す、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 評価の結果を格納しています。 この 2 部構成方法により、複数回に評価されるように解析された式を評価する、次の解析、式を解析の時間のかかるプロセスをバイパスして、評価をするには。  
  
## 必要条件  
 ヘッダー: ee.h  
  
 名前空間: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)