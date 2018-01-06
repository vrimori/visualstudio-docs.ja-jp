---
title: "IEEVisualizerServiceProvider |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEVisualizerServiceProvider
helpviewer_keywords: IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0d778ba9038a9d14c7bb107f239adbc0d9bab2b2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 このインターフェイスは、IDE の型のビジュアライザーのタスクを処理するために使用するビジュアライザー サービスを作成可能なメソッドへのアクセスを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
IEEVisualizerServiceProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 Visual Studio はさらに、クラス Id を指定するために使用されて、ビジュアライザーのサービス オブジェクトを作成するには、このインターフェイスを実装 (`CLSID`s)、Visual Studio IDE に種類のビジュアライザーのです。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 式エバリュエーター (EE) を呼び出す[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)このインターフェイスを取得します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|ビジュアライザー サービスを作成します。|  
  
## <a name="remarks"></a>コメント  
 `IEEVisualizerServiceProvider`インターフェイスが実装の中に取得した[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)です。 このインターフェイスを作成するビジュアライザー サービスを使用する機能を提供する、 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) EE を実装するためのインターフェイスです。 EE は実装を担当するも、 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)種類のビジュアライザーを表示およびプロパティの値を変更できるようにするインターフェイスです。  
  
 参照してください[Visualizing とデータの表示](../../../extensibility/debugger/visualizing-and-viewing-data.md)これらのインターフェイスがやり取りする方法の詳細。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [式の評価インターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [データの視覚化と表示](../../../extensibility/debugger/visualizing-and-viewing-data.md)