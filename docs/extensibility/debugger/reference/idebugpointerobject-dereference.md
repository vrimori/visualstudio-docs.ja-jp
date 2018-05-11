---
title: IDebugPointerObject::Dereference |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4cc287887baf2530786b03b591d6c03592055e55
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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