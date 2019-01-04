---
title: IDebugEnumField::GetStringFromValue |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eb3fc6a0e8aab20659abe7a2d8601f478f948a9b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53877407"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
このメソッドは、その値を指定された列挙定数の名前を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetStringFromValue(  
   ULONGLONG value,  
   BSTR*     pbstrValue  
);  
```  
  
```csharp  
int GetStringFromValue(  
   ulong      value,  
   out string pbstrValue  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `value`  
 [in]定数、列挙型の名前を取得する対象の値。  
  
 `pbstrValue`  
 [out]列挙定数の名前を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`場合は、値は、関連付けの名前がないか、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 同じ値に関連付けられている 1 つ以上の名前がある場合は、列挙で定義されている最初の名前が返されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)