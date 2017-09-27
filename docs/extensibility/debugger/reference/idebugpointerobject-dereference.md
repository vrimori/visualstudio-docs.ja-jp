---
title: "IDebugPointerObject::Dereference |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
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
ms.openlocfilehash: d69fbe6a4f3c5453053f81cffd1753dca0470438
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
指されるオブジェクトを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwIndex`  
 [in]オブジェクトの先頭からの単純なバイト オフセットを参照できます。  
  
 `ppObject`  
 [out]返します、 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)指す、およびオフセット、オブジェクトを表すオブジェクトの存在する場合。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。 このオブジェクトが別のオブジェクトを指していない場合は、E_FAIL を返します。  
  
## <a name="remarks"></a>コメント  
 指されるオブジェクトには、プリミティブまたはクラスまたは構造体などのより複雑な型を指定できます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
