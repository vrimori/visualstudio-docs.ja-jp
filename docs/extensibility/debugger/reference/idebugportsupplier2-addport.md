---
title: "IDebugPortSupplier2::AddPort |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 6f77b0dd072c0e1acdbe642a0ded64a554f809f1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
ポートを追加します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT AddPort(   
   IDebugPortRequest2* pRequest,  
   IDebugPort2**       ppPort  
);  
```  
  
```csharp  
int AddPort(   
   IDebugPortRequest2 pRequest,  
   out IDebugPort2    ppPort  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRequest`  
 [in][IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)を追加するポートを記述するオブジェクト。  
  
 `ppPort`  
 [out]返します、 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)ポートを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、実際には、アクティブなポートのポート業者の内部リストに追加するとともに、要求されたポートを作成します。 [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)可能な時間がかかる遅延を回避するメソッドを最初に呼び出すことができます。  
  
## <a name="see-also"></a>参照  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)