---
title: "IEEVisualizerDataProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerDataProvider"
helpviewer_keywords: 
  - "IEEVisualizerDataProvider インターフェイス"
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IEEVisualizerDataProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 このインターフェイスは、型のビジュアライザーを使用して、オブジェクトの値を変更する機能を提供します。  
  
## 構文  
  
```  
IEEVisualizerDataProvider : IUnknown  
```  
  
## 実装についてのメモ  
 式エバリュエーターでは、型のビジュアライザーをプロパティ オブジェクトでデータの変更をサポートするには、このインターフェイスを実装します。  
  
## 呼び出し元のノート  
 このインターフェイスは、作成に使用されます、 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) を呼び出すことによってオブジェクト [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)します。 詳細については、「[視覚化して、データを表示します。](../../../extensibility/debugger/visualizing-and-viewing-data.md)」を参照してください。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[CanSetObjectForVisualizer](../Topic/IEEVisualizerDataProvider::CanSetObjectForVisualizer.md)|オブジェクト \(とその後、その値\) を更新するかどうかをこのビジュアライザーを表すことです。|  
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|このビジュアライザーのオブジェクトの再評価を強制します。|  
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|このビジュアライザー \(評価は行われません\) の既存のオブジェクトを取得します。|  
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|このビジュアライザーは、それによって、ビジュアライザーを表示する値を変更のオブジェクトを更新します。|  
  
## 解説  
 ビジュアライザー サービス \(で表される、 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) インターフェイスおよびによって返される [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)\) を実装するオブジェクト参照を保持、 `IEEVisualizerDataProvider` インターフェイスです。 結果として、 `IEEVisualizerDataProvider` を実装する同一のオブジェクトに、インターフェイスを実装しないように、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) そのオブジェクトへの参照を保持する場合、 `IEEVisualizerService` オブジェクト: 循環参照が発生し、デッドロックは、オブジェクトが破棄されると発生します。 推奨されるアプローチは、実装する `IEEVisualizerDataProvider` する個別のオブジェクトに、 `IDebugProperty2` 呼び出さずにデリゲートをオブジェクト `IUnknown::AddRef` にします。  
  
## 必要条件  
 ヘッダー: ee.h  
  
 名前空間: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [式評価インターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [視覚化して、データを表示します。](../../../extensibility/debugger/visualizing-and-viewing-data.md)