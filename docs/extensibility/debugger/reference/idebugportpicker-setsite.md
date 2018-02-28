---
title: "IDebugPortPicker::SetSite |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a307c2b387905706d229d7811f490f109f14c78f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
サービス プロバイダーを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetSite(  
   IServiceProvider * pSP  
);  
```  
  
```csharp  
public int SetSite(  
   IServiceProvider pSP  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pSP`  
 [in]サービス プロバイダーのインターフェイスへの参照。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドが、他のメソッドが呼び出される前に呼び出されます。  
  
## <a name="see-also"></a>参照  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)