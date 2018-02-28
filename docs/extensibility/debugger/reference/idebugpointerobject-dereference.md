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
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 3e743f5a312e437ca48a5e36fb202783f41b934d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>参照  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)