---
title: IEEVisualizerServiceProvider::CreateVisualizerService |Microsoft Docs
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
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6f6bbb0077fcc8dd8d151b995a9c416113e1b5ef
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49243439"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
 [in][IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)オブジェクトに渡される[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)します。  
  
 `pSymProv`  
 [in][IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)オブジェクトに渡される`IDebugParsedExpression::EvaluateSync`します。  
  
 `pAddress`  
 [in][IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)オブジェクトに渡される`IDebugParsedExression::EvaluateSync`します。  
  
 `dataProvider`  
 [in]実装するオブジェクト、 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) (式エバリュエーターで提供されている) インターフェイス。  
  
 `ppService`  
 [out]作成したサービス。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 `binder`、 `pSymProv`、および`pAddress`にパラメーターすべて渡された、`IDebugParsedExpression::EvaluateSync`メソッド。 `CreateVisualizerService` のみ呼び出される`IDebugParsedExpression::EvaluateSync`ビジュアライザーの型の式エバリュエーターのサポートの一部として。  
  
## <a name="see-also"></a>関連項目  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

