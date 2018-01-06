---
title: "IEEVisualizerDataProvider |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEVisualizerDataProvider
helpviewer_keywords: IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: edf2cfe689caa58e1c0402a91fa31237cb2c7215
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 このインターフェイスは、型のビジュアライザーを使用して、オブジェクトの値を変更する機能を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
IEEVisualizerDataProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 式エバリュエーターでは、型のビジュアライザーをプロパティ オブジェクトでデータの変更をサポートするには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスは、作成に使用されます、 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)を呼び出すことによってオブジェクト[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)です。 参照してください[Visualizing とデータの表示](../../../extensibility/debugger/visualizing-and-viewing-data.md)詳細についてはします。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|かどうかは、オブジェクト (およびその後、その値) を更新することを決定するこのビジュアライザーを表すです。|  
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|このビジュアライザーのオブジェクトの再評価を強制します。|  
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|このビジュアライザー (評価は行われません) の既存のオブジェクトを取得します。|  
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|ビジュアライザーを表示する値が変更され、このビジュアライザーのオブジェクトを更新します。|  
  
## <a name="remarks"></a>コメント  
 ビジュアライザー サービス (で表される、 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)インターフェイスし、によって返される[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) を実装するオブジェクト参照を保持、`IEEVisualizerDataProvider`インターフェイス. その結果、`IEEVisualizerDataProvider`を実装する、同じオブジェクトに対して、インターフェイスを実装しないように、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)そのオブジェクトへの参照を保持する場合、`IEEVisualizerService`オブジェクト: 循環参照の結果とオブジェクトが破棄されるときに、デッドロックが発生します。 実装するのには、推奨されるアプローチ`IEEVisualizerDataProvider`する個別のオブジェクトで、`IDebugProperty2`呼び出さずにデリゲートをオブジェクト`IUnknown::AddRef`にします。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [式の評価インターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [データの視覚化と表示](../../../extensibility/debugger/visualizing-and-viewing-data.md)