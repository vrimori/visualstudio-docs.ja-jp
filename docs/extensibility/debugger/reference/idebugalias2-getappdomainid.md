---
title: IDebugAlias2::GetAppDomainId |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b70b26cbf9248f654836a2d138ad0f79b80a3b54
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55011749"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
アプリケーション ドメインの識別子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetAppDomainId (  
   ULONG32* pappDomainId  
);  
```  
  
```csharp  
int GetAppDomainId (  
   out uint pappDomainId  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pappDomainId`  
 [out]アプリケーション ドメインの識別子を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 アプリケーション ドメインの識別子変更、アプリケーションが再起動されるたびに、新しいアプリケーション ドメインが作成されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)