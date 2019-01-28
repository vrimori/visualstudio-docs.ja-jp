---
title: IEEVisualizerServiceProvider |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a21f14cbe6396a754d01892394584f319eaf8166
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54951739"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 このインターフェイスは、IDE の型のビジュアライザーのタスクを処理するために使用するビジュアライザー サービスを作成可能なメソッドにアクセスできます。  
  
## <a name="syntax"></a>構文  
  
```  
IEEVisualizerServiceProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 Visual Studio がさらに、クラス Id を指定するために使用がビジュアライザー サービス オブジェクトを作成するには、このインターフェイスを実装 (`CLSID`秒) の型のビジュアライザーを Visual Studio IDE にします。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 式エバリュエーター (EE) を呼び出す[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)このインターフェイスを取得します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|ビジュアライザーのサービスを作成します。|  
  
## <a name="remarks"></a>Remarks  
 `IEEVisualizerServiceProvider`インターフェイスの実装時に取得[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)します。 このインターフェイスを作成するビジュアライザー サービスを使用する機能を提供する、 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)インターフェイス、EE を実装する責任を負います。 EE は実装を担当することも、 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)型のビジュアライザーを表示およびプロパティの値を変更できるようにするインターフェイス。  
  
 参照してください[視覚化してデータの表示](../../../extensibility/debugger/visualizing-and-viewing-data.md)これらのインターフェイスがやり取りする方法の詳細について。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: ee.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [式の評価のインターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [データの視覚化と表示](../../../extensibility/debugger/visualizing-and-viewing-data.md)