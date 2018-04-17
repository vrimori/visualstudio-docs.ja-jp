---
title: IDebugEnumField::GetStringFromValue |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: a0b7ac4f7cde93d4637906202f7b4c643750d8e0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
このメソッドは、その値を指定する列挙定数の名前を取得します。  
  
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
 [in]定数、列挙型の名前を取得する対象の値です。  
  
 `pbstrValue`  
 [out]列挙定数の名前を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外を返します`S_FALSE`場合は、値が関連付けられている名前がないか、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 複数の名前が同じ値に関連付けられている場合は、列挙体の定義名が返されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)