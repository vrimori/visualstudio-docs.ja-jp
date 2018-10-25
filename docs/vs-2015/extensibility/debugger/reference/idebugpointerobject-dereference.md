---
title: IDebugPointerObject::Dereference |Microsoft Docs
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
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e82f2d1635b46dccd9f5f93b5773ba757342f04d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49838999"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

指すオブジェクトを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [in]オブジェクトの先頭からの単純なバイト オフセットが指すになりました。  
  
 `ppObject`  
 [out]返します、 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)存在する場合、オブジェクトを表す、指すし、オフセットのオブジェクトします。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。 このオブジェクトが別のオブジェクトを指していない場合は、E_FAIL を返します。  
  
## <a name="remarks"></a>Remarks  
 指すオブジェクトには、プリミティブ型またはクラスまたは構造体などのより複雑な型を使用できます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)

