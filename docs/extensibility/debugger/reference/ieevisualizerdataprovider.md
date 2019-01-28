---
title: IEEVisualizerDataProvider |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc5c16d71fac3b52187b3e0392ed21bdd56a079f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54978322"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 このインターフェイスは、型のビジュアライザーを使用して、オブジェクトの値を変更する機能を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
IEEVisualizerDataProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 式エバリュエーターでは、型のビジュアライザーをプロパティ オブジェクトのデータの変更をサポートするためにこのインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスは、作成に使用されます、 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)への呼び出しを使用してオブジェクト[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)します。 参照してください[視覚化してデータの表示](../../../extensibility/debugger/visualizing-and-viewing-data.md)の詳細。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|かどうかは、オブジェクト (とその後、その値) を更新することを決定します。 このビジュアライザーを表すです。|  
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|このビジュアライザーのオブジェクトの再評価を強制します。|  
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|このビジュアライザー (評価は行われません) の既存のオブジェクトを取得します。|  
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|このビジュアライザーは、それによってビジュアライザーを表示します。 値を変更するのには、オブジェクトを更新します。|  
  
## <a name="remarks"></a>Remarks  
 ビジュアライザー サービス (によって表される、 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)インターフェイスし、によって返される[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) 実装するオブジェクトへの参照を保持、`IEEVisualizerDataProvider`インターフェイス. 結果として、`IEEVisualizerDataProvider`を実装するオブジェクトと同じで、インターフェイスを実装しないように、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)そのオブジェクトへの参照を保持している場合、`IEEVisualizerService`オブジェクト: 循環参照の結果とオブジェクトが破棄されるときに、デッドロックが発生します。 推奨されるアプローチを実装するためには`IEEVisualizerDataProvider`を個別のオブジェクトで、`IDebugProperty2`呼び出さずにデリゲートをオブジェクト`IUnknown::AddRef`にします。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: ee.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [式の評価のインターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [データの視覚化と表示](../../../extensibility/debugger/visualizing-and-viewing-data.md)