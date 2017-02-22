---
title: "IEEVisualizerService | Microsoft Docs"
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
  - "IEEVisualizerService"
helpviewer_keywords: 
  - "IEEVisualizerService インターフェイス"
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# IEEVisualizerService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 このインターフェイスを実装する機能を提供する主要なメソッド、 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) と [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) インターフェイスです。  
  
## 構文  
  
```  
IEEVisualizerService : IUnknown  
```  
  
## 実装についてのメモ  
 Visual Studio では、式エバリュエーターの種類のビジュアライザーをサポートするために \(EE\) を許可するには、このインターフェイスを実装します。  
  
## 呼び出し元のノート  
 EE 呼び出し [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) 型のビジュアライザーのサポートの一部としてこのインターフェイスを取得します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|については、このサービスを知っているカスタム ビューアーの数を取得します。|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|カスタム ビューアーの一覧を取得します。|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|プロパティのプロキシ オブジェクトを返します。|  
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|指定したプロパティまたはフィールドを表示する値の文字列の数を取得します。|  
  
## 解説  
 IDE を使用して、 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) インターフェイス、カスタム ビューアーがあるかを確認するか、プロパティのビジュアライザーを入力します。 ビジュアライザーのサービスを作成することで \(と [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)\)、EE にするための機能を指定できます、 `IDebugProperty3` と [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) \(するサポートを表示して、このプロパティの値を変更する\) インターフェイスをし、それによってサポート型のビジュアライザー。  
  
 その自体を実装して、EE にカスタム ビューアーがある場合は、EE を追加できる、 `CLSID`で返される一覧の末尾にこれらのカスタム ビューアーの [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)です。 これにより、型のビジュアライザーと独自のカスタム ビューアーの両方をサポートするために、EE できます。 同じことを確認 [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) 任意のカスタム ビューアーの加算が反映されます。  
  
 参照してください [型のビジュアライザーとカスタム ビューアー](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) ビジュアライザーとビューアーの違いの詳細について。  
  
## 必要条件  
 ヘッダー: ee.h  
  
 名前空間: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [式評価インターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)   
 [型のビジュアライザーとカスタム ビューアー](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)