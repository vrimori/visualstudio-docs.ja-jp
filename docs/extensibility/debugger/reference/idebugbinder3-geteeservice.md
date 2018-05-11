---
title: IDebugBinder3::GetEEService |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56c97e9fc7e5505578533c9e7b958a73dc8d2380
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
このメソッドは、要求されたサービスを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetEEService(  
   [in] GUID        vendor,  
   [in] GUID        language,  
   [in] GUID        iid,  
   [out] IUnknown** ppService  
);  
```  
  
```csharp  
Int GetEEService(  
   Guid       vendor,  
   Guid       language,  
   Guid       iid,  
   out object ppService  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `vendor`  
 [in]`GUID` (null 値が許容される) のベンダー。  
  
 `language`  
 [in]`GUID` (null 値を許容) 言語のです。  
  
 `iid`  
 [in]`IID`のサービスから取得します。  
  
 `ppService`  
 [out]要求されたサービスへのインターフェイス。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 渡す、`IID`の[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)インターフェイス (`IID_IEEVisualizerServiceProvider`) 型のビジュアライザー サービスが利用可能な。 式エバリュエーターを取得できるため場合、 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)種類のビジュアライザーをサポートするインターフェイスです。 参照してください[Visualizing とデータの表示](../../../extensibility/debugger/visualizing-and-viewing-data.md)詳細についてはします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [データの視覚化と表示](../../../extensibility/debugger/visualizing-and-viewing-data.md)