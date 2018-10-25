---
title: IDebugEnumField::GetValueFromString |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 86cf8b1421769ac9a4b302e0da3676d826b9bea6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942232"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
このメソッドは、列挙定数の名前に関連付けられている値を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetValueFromString(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```csharp  
int GetValueFromString(  
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
 このメソッドは大文字小文字を区別します。 (たとえば、名前は大文字小文字を区別しない、Visual Basic などの言語) で、大文字と小文字が必要に応じて、使用して[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)