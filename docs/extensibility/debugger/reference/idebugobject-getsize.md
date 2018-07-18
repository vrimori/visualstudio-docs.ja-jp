---
title: IDebugObject::GetSize |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject::GetSize
helpviewer_keywords:
- IDebugObject::GetSize method
ms.assetid: 89af423b-36eb-479d-b2de-2693455eca15
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a3a6880b7b3a09b92ca4dd9c31d01cb1c05d1620
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31112494"
---
# <a name="idebugobjectgetsize"></a>IDebugObject::GetSize
オブジェクトのサイズをバイト単位で取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetSize(   
   UINT* pnSize  
);  
```  
  
```csharp  
int GetSize(  
   out uint pnSize  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pnSize`  
 [out]サイズをバイト単位で返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 使用して、 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)バイトのシーケンスとして値を取得します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)