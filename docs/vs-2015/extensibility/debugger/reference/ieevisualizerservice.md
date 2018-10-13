---
title: IEEVisualizerService |Microsoft Docs
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
- IEEVisualizerService
helpviewer_keywords:
- IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 27b7d36820cc127e4fb6367336926fb9c4236193
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49228749"
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 このインターフェイスは実装する機能を提供する主要なメソッド、 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)と[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)インターフェイス。  
  
## <a name="syntax"></a>構文  
  
```  
IEEVisualizerService : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 Visual Studio では、式エバリュエーターの種類のビジュアライザーをサポートするために (EE) を許可するには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 EE 呼び出し[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)型のビジュアライザーのサポートの一部としてこのインターフェイスを取得します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|このサービスを認識するカスタム ビューアーの数を取得します。|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|カスタム ビューアーの一覧を取得します。|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|プロパティのプロキシ オブジェクトを返します。|  
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|指定したプロパティまたはフィールドを表示する値の文字列の数を取得します。|  
  
## <a name="remarks"></a>Remarks  
 IDE を使用、 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)インターフェイスを任意のカスタム ビューアーがあるかを確認するか、プロパティのビジュアライザーを入力します。 ビジュアライザーのサービスを作成して (で[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md))、EE にするための機能を指定できます、`IDebugProperty3`と[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) (の表示と変更をサポートする、プロパティの値) では、インターフェイスし、それによって型のビジュアライザーをサポートします。  
  
 その自体を実装して、EE にカスタム ビューアーがある場合は、EE を追加できる、`CLSID`によって返される一覧の末尾にこれらのカスタム ビューアーの[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)します。 これにより、型のビジュアライザーおよび独自のカスタム ビューアーの両方をサポートするために、EE できます。 同じことを確認します[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)任意のカスタム ビューアーの加算を反映します。  
  
 参照してください[型のビジュアライザーとカスタム ビューアー](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)ビジュアライザーとビューアーの違いの詳細についてはします。  
  
## <a name="requirements"></a>要件  
 ヘッダー: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [式の評価のインターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)   
 [型のビジュアライザーとカスタム ビューアー](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

