---
title: IDebugSymbolProvider::GetLanguage |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugSymbolProvider::GetLanguage
helpviewer_keywords:
- IDebugSymbolProvider::GetLanguage method
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9b9ca0df0652e2b2e1d1c9d08ef59ce32891f89f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53956167"
---
# <a name="idebugsymbolprovidergetlanguage"></a>IDebugSymbolProvider::GetLanguage
このメソッドは、デバッグ アドレスにコードをコンパイルするために使用された言語を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetLanguage(   
   IDebugAddress* pAddress,  
   GUID*          pguidLanguage,  
   GUID*          pguidLanguageVendor  
);  
```  
  
```csharp  
int GetLanguage(  
   IDebugAddress pAddress,   
   out Guid      pguidLanguage,   
   out Guid      pguidLanguageVendor  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pAddress`  
 [in]によって表されるアドレス オブジェクトを[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)インターフェイス。  
  
 `pguidLanguage`  
 [out]返します、`GUID`言語を指定します。  
  
 `pguidLanguageVendor`  
 [out]返します、`GUID`言語販売元を指定します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 デバッグ エンジンでは、正しい式エバリュエーターを選択する必要がある情報を取得するには、このメソッドを呼び出します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)