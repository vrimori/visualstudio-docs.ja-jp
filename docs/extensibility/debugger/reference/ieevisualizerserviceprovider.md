---
title: "IEEVisualizerServiceProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerServiceProvider"
helpviewer_keywords: 
  - "IEEVisualizerServiceProvider インターフェイス"
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# IEEVisualizerServiceProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 このインターフェイスは、IDE の型のビジュアライザーのタスクを処理するために使用するビジュアライザー サービスを作成可能なメソッドにアクセスできます。  
  
## 構文  
  
```  
IEEVisualizerServiceProvider : IUnknown  
```  
  
## 実装についてのメモ  
 Visual Studio がさらに、クラス Id を指定するために使用は、ビジュアライザー サービス オブジェクトを作成するには、このインターフェイスを実装する \(`CLSID`s\)、Visual Studio IDE に型のビジュアライザーのです。  
  
## 呼び出し元のノート  
 式エバリュエーター \(EE\) を呼び出す [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) このインターフェイスを取得します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|ビジュアライザーのサービスを作成します|  
  
## 解説  
 `IEEVisualizerServiceProvider` インターフェイスがの実装時に取得した [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)します。 このインターフェイスを作成するビジュアライザー サービスを使用する機能を提供する、 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) EE を実装するためのインターフェイスです。 EE は、実装する責任も、 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) 型のビジュアライザーを表示およびプロパティの値を変更できるようにするインターフェイスです。  
  
 参照してください [視覚化して、データを表示します。](../../../extensibility/debugger/visualizing-and-viewing-data.md) これらのインターフェイスがやり取りする方法の詳細。  
  
## 必要条件  
 ヘッダー: ee.h  
  
 名前空間: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [式評価インターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [視覚化して、データを表示します。](../../../extensibility/debugger/visualizing-and-viewing-data.md)