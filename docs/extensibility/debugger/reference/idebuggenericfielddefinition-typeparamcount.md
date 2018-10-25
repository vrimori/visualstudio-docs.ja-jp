---
title: IDebugGenericFieldDefinition::TypeParamCount |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- TypeParamCount
- IDebugGenericFieldDefinition::TypeParamCount
ms.assetid: d41dd5ea-aa25-4bf3-bcfd-e0bf451ead49
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: baf6f6b7643c3d24a0f691a95477ad805823e541
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922381"
---
# <a name="idebuggenericfielddefinitiontypeparamcount"></a>IDebugGenericFieldDefinition::TypeParamCount
[標準] フィールドに関連付けられている型パラメーターの数を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT TypeParamCount(  
   ULONG32* pcParams  
);  
```  
  
```csharp  
int TypeParamCount(  
   ref uint pcParams  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pcParams`  
 [入力、出力]型パラメーターの数。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 場合一覧\<T >、このメソッドは、1 を返しますと、一覧\<T1, T2 >、このメソッドは、2 を返します。 このメソッドは、型パラメーターがない場合に 0 を返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)