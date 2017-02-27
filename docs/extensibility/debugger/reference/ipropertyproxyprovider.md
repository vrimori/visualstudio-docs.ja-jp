---
title: "IPropertyProxyProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyProvider"
helpviewer_keywords: 
  - "IPropertyProxyProvider インターフェイス"
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IPropertyProxyProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはオブジェクトのデータを表示および変更するためにプロキシのインターフェイスを提供します。  
  
## 構文  
  
```  
IPropertyProxyProvider : IUnknown  
```  
  
## 実装についてのメモ  
 式エバリュエーターは \(EE\) EE の型のビジュアライザーのサポートの一部として既に同じオブジェクトがこのインターフェイスを実装する [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) のインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 このインターフェイスを取得 `IDebugProperty3` のインターフェイスでは [QueryInterface](/visual-cpp/atl/queryinterface)。  
  
## Vtable の順序でメソッド  
 `IPropertyProxyProvider` のインターフェイスは以下のメソッドを実行します :  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|オブジェクトのデータにプロパティのプロキシのインターフェイスを取得します。|  
  
## 解説  
 EE がこのインターフェイスを実装しますが[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) の実装は通常 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md) に処理されます。  IEEVisualizerService のインターフェイスの詳細については [視覚化して、データを表示します。](../../../extensibility/debugger/visualizing-and-viewing-data.md) を参照してください。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [型のビジュアライザーとカスタム ビューアー](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [視覚化して、データを表示します。](../../../extensibility/debugger/visualizing-and-viewing-data.md)