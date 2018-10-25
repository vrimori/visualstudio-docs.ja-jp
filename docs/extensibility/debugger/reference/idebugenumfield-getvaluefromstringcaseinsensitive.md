---
title: IDebugEnumField::GetValueFromStringCaseInsensitive |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 96e1e98a8d095a2fd7fc9c63b42267fc70cab065
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933327"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
このメソッドでは、検索を使用して、列挙定数の名前に関連付けられた値を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetValueFromStringCaseInsensitive(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```csharp  
int GetValueFromStringCaseInsensitive(  
   string    pszValue,   
   out ulong pValue  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszValue`  
 [in]値を取得する対象の名前を指定する文字列。 C++、ワイド文字の文字列は、このことに注意してください。  
  
 `pValue`  
 [out]関連付けられている数値を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`名前列挙型、またはエラー コードの一部でない場合は、します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは大文字です。 (たとえば、C++ の名前が大文字小文字を区別などの言語) で大文字と小文字が必要に応じて、使用して[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)