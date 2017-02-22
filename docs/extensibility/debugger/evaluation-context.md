---
title: "評価コンテキスト | Microsoft Docs"
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
  - "[デバッグ SDK] の式の評価のデバッグ"
  - "式の評価、コンテキスト"
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 評価コンテキスト
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 3 つの引数が渡されるデバッグ エンジン \(DE\) を呼び出すと、式エバリュエーター \(EE\)、 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 次の表に示すように検出して、シンボルを評価するためのコンテキストを決定します。  
  
## 引数  
  
|引数|説明|  
|--------|--------|  
|`pSymbolProvider`|[IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) シンボルを識別するために使用するシンボル ハンドラー \(SH\) を指定するインターフェイスです。|  
|`pAddress`|[IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) 実行の現在位置を指定するインターフェイスです。 実行対象のコードを含むメソッドを検索するために使用できます。|  
|`pBinder`|[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) 値と指定した名前のシンボルの型を検索するために使用するインターフェイスです。|  
  
 `IDebugParsedExpression::EvaluateSync` 返します、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 結果の値とその型を表すインターフェイスです。  
  
## 参照  
 [キー式エバリュエーター インターフェイス](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [\[ローカル\] を表示します。](../Topic/Displaying%20Locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)