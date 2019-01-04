---
title: IDebugCustomAttribute::GetParentField |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f0165c5a60b79ba5a23cb9e14a1d917058ad200
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916693"
---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
カスタム属性がアタッチされているフィールドを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetParentField(   
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetParentField(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppField`  
 [out]返します、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)カスタム属性がアタッチされているフィールドを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 呼び出す、 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)メソッドで返された[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)親フィールドの種類を決定するオブジェクトします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)