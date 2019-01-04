---
title: IDebugModule3::IsUserCode |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a8756e926f602c1be62670aa36f9367e064910a4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990059"
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
については、モジュールがかどうかにユーザー コードをどのように表すかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsUserCode(  
   BOOL* pfUser  
);  
```  
  
```csharp  
int IsUserCode(  
   out int pfUser  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pfUser`  
 [out]0 以外の場合 (`TRUE`) モジュールでは、ユーザー コードを表している場合は 0 (`FALSE`) そうでない場合。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)