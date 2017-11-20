---
title: "IDebugCustomAttributeQuery2::IsCustomAttributeDefined |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords: IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2f1311beccfb36364bb8039f75bbe2955cbc9fca
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
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
 S_OK でこのフィールドは、カスタム属性が定義されている場合は、それ以外の場合は S_FALSE を返しますを返します。  
  
## <a name="remarks"></a>コメント  
 カスタム属性に関連付けられている属性のバイト数を取得するを呼び出して、 [GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)