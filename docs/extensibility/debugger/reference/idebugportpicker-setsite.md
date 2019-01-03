---
title: IDebugPortPicker::SetSite |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 664b036d22cad95f568f5b86eb17acf72429042a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889281"
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
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドが、他のメソッドが呼び出される前に呼び出されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)