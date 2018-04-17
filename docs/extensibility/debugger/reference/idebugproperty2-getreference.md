---
title: IDebugProperty2::GetReference |Microsoft ドキュメント
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
ms.openlocfilehash: 949792723135c21f6554a98403cfa58554b60185
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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
 成功した場合を返します`S_OK`以外の場合、通常、エラー コードを返します`E_NOTIMPL`または`E_GETREFERENCE_NO_REFERENCE`です。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)