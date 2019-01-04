---
title: IDebugPort2::GetPortRequest |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7bc68272523100c07879b00b261b86f27023a13b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53844617"
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
(該当する場合) のポートの作成に使用されていたポートの説明を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetPortRequest(   
   IDebugPortRequest2** ppRequest  
);  
```  
  
```csharp  
int GetPortRequest(   
   out IDebugPortRequest2 ppRequest  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppRequest`  
 [out]返します、 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)ポートの作成に使用された要求を表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  返します`E_PORT_NO_REQUEST`ポートが使用して作成されなかった場合、 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)ポート要求。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)