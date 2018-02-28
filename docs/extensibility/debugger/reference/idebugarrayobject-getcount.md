---
title: "IDebugArrayObject::GetCount |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 00f3f0daa09f41168224c0d0817707de26dc817a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
配列内の要素の数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
[C++]  
HRESULT GetCount(   
   DWORD* pdwElements  
);  
```  
  
```  
[C#]  
int GetCount(  
   out uint pdwElements  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pdwElements`  
 [out]カウントを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、1 次元の配列として、配列オブジェクトがマルチ ディメンションの場合でもすべての要素の配列オブジェクトのように表示されます。 たとえば、配列を指定`myarray[3][2][6]`、メソッドは 36 で、`pdwElements`パラメーター。 使用して、 [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)を一度に 1 つの個々 の要素を取得する方法です。  
  
## <a name="see-also"></a>参照  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)