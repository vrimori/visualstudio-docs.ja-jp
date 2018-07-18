---
title: IEEVisualizerServiceProvider::CreateVisualizerService |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f59d86e94be5c0295786b747f6b57753aa087b07
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120677"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
このメソッドは、ビジュアライザー サービスを作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateVisualizerService(  
   IDebugBinder*              binder,  
   IDebugSymbolProvider*      pSymProv,  
   IDebugAddress*             pAddress,  
   IEEVisualizerDataProvider* dataProvider,  
   IEEVisualizerService**     ppService  
);  
```  
  
```csharp  
int CreateVisualizerService(  
   IDebugBinder binder,  
   IDebugSymbolProvider      pSymProv,  
   IDebugAddress             pAddress,  
   IEEVisualizerDataProvider dataProvider,  
   out IEEVisualizerService  ppService  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `binder`  
 [in][IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)オブジェクトに渡される[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)です。  
  
 `pSymProv`  
 [in][IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)オブジェクトに渡される`IDebugParsedExpression::EvaluateSync`です。  
  
 `pAddress`  
 [in][IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)オブジェクトに渡される`IDebugParsedExression::EvaluateSync`です。  
  
 `dataProvider`  
 [in]実装するオブジェクト、 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) (式エバリュエーターで提供されている) インターフェイス。  
  
 `ppService`  
 [out]作成したサービスです。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 `binder`、 `pSymProv`、および`pAddress`すべてに渡すパラメーター、`IDebugParsedExpression::EvaluateSync`メソッドです。 `CreateVisualizerService` のみ呼び出される`IDebugParsedExpression::EvaluateSync`ビジュアライザーの型の式エバリュエーターのサポートの一部として。  
  
## <a name="see-also"></a>関連項目  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)