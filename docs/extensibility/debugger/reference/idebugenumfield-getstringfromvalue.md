---
title: "IDebugEnumField::GetStringFromValue |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEnumField::GetStringFromValue
helpviewer_keywords: IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 695c35e6d849806911aaf9cb293b53e66dbbca0e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>参照  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)