---
title: IDebugProperty2::GetReference |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty2::GetReference
helpviewer_keywords:
- IDebugProperty2::GetReference method
ms.assetid: 2fa97d9b-c3d7-478e-ba5a-a933f40a0103
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7341c88bdf4039f16d87cdd137081c0c7bac5ba2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937539"
---
# <a name="idebugproperty2getreference"></a>IDebugProperty2::GetReference
プロパティの値への参照を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetReference(  
   IDebugReference2** ppReference  
);  
```  
  
```csharp  
int GetReference(  
   out IDebugReference2 ppReference  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppRererence`  
 [out]返します、 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)プロパティの値への参照を表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`。 そうしないと、通常、エラー コードを返します`E_NOTIMPL`または`E_GETREFERENCE_NO_REFERENCE`します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)