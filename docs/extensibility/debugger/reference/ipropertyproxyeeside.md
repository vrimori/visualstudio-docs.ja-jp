---
title: "IPropertyProxyEESide | Microsoft Docs"
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
  - "IPropertyProxyEESide"
helpviewer_keywords: 
  - "IPropertyProxyEESide インターフェイス"
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IPropertyProxyEESide
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスは関連するオブジェクトでデータのメソッドを提供します。  このインターフェイスは型のビジュアライザーのサポートの一部です。  
  
## 構文  
  
```  
IPropertyProxyEESide : IUnknown  
```  
  
## 実装についてのメモ  
 式エバリュエーターは型のビジュアライザーをサポートするにはこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 このインターフェイスを取得します [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)。  [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) のインターフェイスを取得 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) のインターフェイスでは [QueryInterface](/visual-cpp/atl/queryinterface)。  
  
## Vtable の順序でメソッド  
 次のメソッドはこのインターフェイスが実装されます :  
  
|メソッド|Description|  
|----------|-----------------|  
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|オブジェクトのデータにアクセスできるようにデータ ソース プロバイダーを初期化します。|  
|[GetManagedViewerCreationData](../Topic/IPropertyProxyEESide::GetManagedViewerCreationData.md)|オブジェクトのアセンブリについての情報を取得します。|  
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|オブジェクトの初期データを取得します。|  
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|既存のデータ ストレージのコピーを作成します。|  
|[InPlaceUpdateObject](../Topic/IPropertyProxyEESide::InPlaceUpdateObject.md)|既存のデータ ストレージへの参照を作成します。|  
|[ResolveAssemblyRef](../Topic/IPropertyProxyEESide::ResolveAssemblyRef.md)|含むアセンブリのコンテキストの特定のアセンブリについてこのオブジェクトを取得します。|  
  
## 解説  
 型のビジュアライザーはこのインターフェイスを含んでいるオブジェクトに関連付けられた値にアクセスするにはこのインターフェイスを使用します。  データはデータの読み取り専用のビューを提供する [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) のインターフェイスを介してアクセスされます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [型のビジュアライザーとカスタム ビューアー](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)