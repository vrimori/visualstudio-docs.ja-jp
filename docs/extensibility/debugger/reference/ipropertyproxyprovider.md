---
title: IPropertyProxyProvider |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f12925c362d3c87b6eb6724c28936333519e844f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53877099"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
このインターフェイスには、オブジェクトのデータの変更を表示したり、プロキシ インターフェイスが用意されています。  
  
## <a name="syntax"></a>構文  
  
```  
IPropertyProxyProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 式エバリュエーター (EE) を実装する同一のオブジェクトにこのインターフェイスを実装する、 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)型のビジュアライザーの EE のサポートの一環としてインターフェイス。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[QueryInterface](/cpp/atl/queryinterface)上、`IDebugProperty3`をこのインターフェイスを取得するインターフェイス。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序メソッド  
 `IPropertyProxyProvider`インターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|オブジェクトのデータを表示するプロパティのプロキシ インターフェイスを取得します。|  
  
## <a name="remarks"></a>Remarks  
 EE の実装は、このインターフェイスの実装が[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)によって処理が通常[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)します。 参照してください[視覚化してデータの表示](../../../extensibility/debugger/visualizing-and-viewing-data.md)IEEVisualizerService インターフェイスを取得する方法の詳細。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [型のビジュアライザーとカスタム ビューアー](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [データの視覚化と表示](../../../extensibility/debugger/visualizing-and-viewing-data.md)