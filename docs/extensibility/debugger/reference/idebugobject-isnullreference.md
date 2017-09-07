---
title: "IDebugObject::IsNullReference |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: dee4f1909ec5f6e66c7f828b5552ff424b4d9edc
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
このオブジェクトが null 参照であるかどうかをテストします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsNullReference(   
   BOOL* pfIsNull  
);  
```  
  
```csharp  
int IsNullReference(  
   out int pfIsNull  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pfIsNull`  
 [out]0 以外を返します (`TRUE`) このオブジェクトは null 参照である場合は、0 を返しますそれ以外の場合 (`FALSE`)。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 Null 参照では、空のオブジェクトまたはいないに割り当てられているオブジェクトを意味します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
