---
title: IDebugBinder3::GetEEService |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdc3470d07ebe8061a1e8b0c452cd55480af94c6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54926191"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
このメソッドは、要求されたサービスを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetEEService(  
   [in] GUID        vendor,  
   [in] GUID        language,  
   [in] GUID        iid,  
   [out] IUnknown** ppService  
);  
```  
  
```csharp  
Int GetEEService(  
   Guid       vendor,  
   Guid       language,  
   Guid       iid,  
   out object ppService  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `vendor`  
 [in]`GUID` (null 値が許容される) のベンダー。  
  
 `language`  
 [in]`GUID` (null 値が許容可能な) 言語の。  
  
 `iid`  
 [in]`IID`のサービスを取得します。  
  
 `ppService`  
 [out]要求されたサービスへのインターフェイス。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 渡す、`IID`の[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)インターフェイス (`IID_IEEVisualizerServiceProvider`) 型のビジュアライザー サービスが使用できるかどうかをします。 そのため、式エバリュエーターを取得できます場合、 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)型のビジュアライザーをサポートするインターフェイス。 参照してください[視覚化してデータの表示](../../../extensibility/debugger/visualizing-and-viewing-data.md)詳細についてはします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [データの視覚化と表示](../../../extensibility/debugger/visualizing-and-viewing-data.md)