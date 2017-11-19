---
title: "IDebugPort2::GetPortRequest |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPort2::GetPortRequest
helpviewer_keywords: IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: df00ec25a4f417e6a84a5c42f04f082df6e0b05c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
(該当する場合) のポートを作成する際に使用されたポートの説明を取得します。  
  
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
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  返します`E_PORT_NO_REQUEST`ポートが使用して作成されなかった場合、 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)ポート要求します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)