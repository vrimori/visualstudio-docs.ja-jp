---
title: "IDebugBinder | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder"
helpviewer_keywords: 
  - "IDebugBinder インターフェイス"
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# IDebugBinder
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 このインターフェイスは、通常メモリ コンテキストまたはシンボルの現在の値を格納しているオブジェクトのシンボル プロバイダーによって返され、シンボルのフィールドをバインドします。  
  
## 構文  
  
```  
IDebugBinder : IUnknown  
```  
  
## 実装についてのメモ  
 このインターフェイスは、式の評価をサポートし、デバッグ エンジン \(DE\) によって実装する必要があります。  
  
## 呼び出し元のノート  
 このインターフェイスは式の評価プロセスに使用しは、通常の実装で使用 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) と [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)です。  
  
## Vtable 順序のメソッド  
 次の表は、のメソッドを示しています。 `IDebugBinder`します。  
  
|メソッド|説明|  
|----------|--------|  
|[バインド](../../../extensibility/debugger/reference/idebugbinder-bind.md)|メモリ コンテキストまたはシンボルの現在の値を含むオブジェクトを取得します。|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|オブジェクトの実行時の型を決定します。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|メモリ コンテキスト オブジェクトの場所またはメモリ アドレスに変換します。|  
|[GetFunctionObject](../Topic/IDebugBinder::GetFunctionObject.md)|取得、 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 関数のパラメーターを作成するために使用します。|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|変数の正確な型を取得します。|  
  
## 解説  
 このインターフェイスは、ツリーの解析での式エバリュエーターで使用されるオブジェクトを返します。 式エバリュエーターが式内のシンボルのインスタンスに変換するシンボル プロバイダーを使用して式を解析して [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), 、その型とソース コードの場所では、各シンボルを記述します。[バインド](../../../extensibility/debugger/reference/idebugbinder-bind.md) メソッドに変換 `IDebugField` オブジェクトを [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 接続またはシンボルをバインドするオブジェクトをメモリ内の実際の値を入力します。 これら `IDebugObject` オブジェクトは、後で評価の解析ツリーに保存されます。  
  
## 必要条件  
 ヘッダー: ee.h  
  
 名前空間: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [式評価インターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)