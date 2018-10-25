---
title: IDebugObject::GetMemoryContext |Microsoft Docs
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
- IDebugObject::GetMemoryContext
helpviewer_keywords:
- IDebugObject::GetMemoryContext method
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 92fc7e511230bfd0344e0e108fc0fdc599649c68
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881652"
---
# <a name="idebugobjectgetmemorycontext"></a>IDebugObject::GetMemoryContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

オブジェクトの値のアドレスを表すメモリ コンテキストを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetMemoryContext(   
   IDebugMemoryContext2** pContext  
);  
```  
  
```csharp  
int GetMemoryContext(  
   ref IDebugMemoryContext2 pContext  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pContext`  
 [out]返します、 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)オブジェクトの値のアドレスを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 これによって表される、返されたメモリ コンテキストは、値のアドレスを指定します[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)オブジェクト。  
  
## <a name="see-also"></a>関連項目  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

