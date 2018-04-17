---
title: IDebugArrayObject::GetCount |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 81788423523837b6e8b29a8869abca7b393cf37a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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
  
## <a name="see-also"></a>関連項目  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)