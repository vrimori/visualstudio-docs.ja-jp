---
title: IDebugSymbolProvider::GetLanguage |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugSymbolProvider::GetLanguage
helpviewer_keywords:
- IDebugSymbolProvider::GetLanguage method
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a9fa14555dee5ee4e39ccd34de51ecdae567e038
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817603"
---
# <a name="idebugsymbolprovidergetlanguage"></a>IDebugSymbolProvider::GetLanguage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このメソッドは、デバッグ アドレスにコードをコンパイルするために使用された言語を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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

