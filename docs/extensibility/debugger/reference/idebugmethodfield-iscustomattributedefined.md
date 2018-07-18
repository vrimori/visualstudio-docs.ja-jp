---
title: IDebugMethodField::IsCustomAttributeDefined |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugMethodField::IsCustomAttributeDefined method
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f8515fd9fc9914daa7f28f876777dd5eb26ac14c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31111161"
---
# <a name="idebugmethodfieldiscustomattributedefined"></a>IDebugMethodField::IsCustomAttributeDefined
特定のカスタム属性が定義されているかどうかを判断します。  
  
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
 S_OK カスタム属性が、このメソッドで定義されている場合は、それ以外の場合は S_FALSE を返しますを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)