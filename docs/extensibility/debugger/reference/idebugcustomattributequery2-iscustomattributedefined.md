---
title: IDebugCustomAttributeQuery2::IsCustomAttributeDefined |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 619c96a2e38302ff4f40a8376116a67c5664743c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49834301"
---
# <a name="idebugcustomattributequery2iscustomattributedefined"></a>IDebugCustomAttributeQuery2::IsCustomAttributeDefined
名前でカスタム属性が存在するかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsCustomAttributeDefined(   
   LPCOLESTR pszCustomAttributeName  
);  
```  
  
```csharp  
int IsCustomAttributeDefined(  
   [In] string pszCustomAttributeName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszCustomAttributeName`  
 [in]検索するカスタム属性の名前を含む文字列。  
  
## <a name="return-value"></a>戻り値  
 S_OK をこのフィールドでカスタム属性が定義されている場合は、それ以外の場合は S_FALSE を返しますを返します。  
  
## <a name="remarks"></a>Remarks  
 カスタム属性に関連付けられた属性のバイト数を取得する呼び出し、 [GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)メソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)