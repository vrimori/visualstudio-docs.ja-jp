---
title: "IPropertyProxyProvider |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IPropertyProxyProvider
helpviewer_keywords: IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 671c80de705ffafc5a3e0040aee0de7f750e28af
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
このインターフェイスは、プロキシ インターフェイスを表示および変更、オブジェクトのデータを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
IPropertyProxyProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 式エバリュエーター (EE) を実装する同一のオブジェクトにこのインターフェイスを実装する、 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)型のビジュアライザーの EE のサポートの一部としてインターフェイスです。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[QueryInterface](/cpp/atl/queryinterface)上、`IDebugProperty3`インターフェイスをこのインターフェイスを取得します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 `IPropertyProxyProvider`インターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|データ オブジェクトを表示するプロパティ プロキシ インターフェイスを取得します。|  
  
## <a name="remarks"></a>コメント  
 EE は、このインターフェイスの実装[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)によって処理は通常[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)です。 参照してください[Visualizing とデータの表示](../../../extensibility/debugger/visualizing-and-viewing-data.md)IEEVisualizerService インターフェイスを取得する方法の詳細。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [型のビジュアライザーとカスタム ビューアー](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [データの視覚化と表示](../../../extensibility/debugger/visualizing-and-viewing-data.md)