---
title: IEEVisualizerServiceProvider |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aa8428a770f3e3c5f06ea9484d7ff43535d449c2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807258"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [式の評価のインターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [データの視覚化と表示](../../../extensibility/debugger/visualizing-and-viewing-data.md)

