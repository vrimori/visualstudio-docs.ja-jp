---
title: "IEEDataStorage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEDataStorage"
helpviewer_keywords: 
  - "IEEDataStorage インターフェイス"
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEEDataStorage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはバイト配列を表します。  
  
## 構文  
  
```  
IEEDataStorage : IUnknown  
```  
  
## 実装についてのメモ  
 式エバリュエーターは \(EE\)バイト配列を実装します。[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) のインターフェイスを通じてデータを取得および変更する型のビジュアライザーによって使用される\) を表すためこのインターフェイス。  EE は外部型のビジュアライザーをサポートするにはこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 `IPropertyProxyEESide` のメソッドはすべてを返します。このインターフェイスによって。  [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) のインターフェイスを取得します [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)。  [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) のインターフェイスを取得するに [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) のインターフェイス [QueryInterface](/visual-cpp/atl/queryinterface) を呼び出します。  
  
## Vtable の順序でメソッド  
 `IEEDataStorage` のインターフェイスは以下のメソッドを実行します :  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetData](../Topic/IEEDataStorage::GetData.md)|指定されたバッファーにデータ型の指定した数を取得します。|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|使用できるデータ バイト数を取得します。|  
  
## 解説  
 このインターフェイスは特定のオブジェクトによって保持されているデータにアクセスする型のビジュアライザーによって使用されます。  データはバイト配列としてユーザーに提示する方法が必要な処理されそのファイルを処理する型のビジュアライザーができます。  
  
 カスタム ビューアーは通常よりカスタム ビューアーがカスタム インターフェイス[GetMemoryBytes](../Topic/IDebugProperty2::GetMemoryBytes.md) または [GetStringChars](../Topic/IDebugProperty3::GetStringChars.md) を使用しますがこのインターフェイスを使用して必要に応じて指向 \(文字列データの場合\)。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [型のビジュアライザーとカスタム ビューアー](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)