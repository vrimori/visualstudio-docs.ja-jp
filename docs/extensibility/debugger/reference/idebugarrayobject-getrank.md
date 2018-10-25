---
title: IDebugArrayObject::GetRank |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7660be0b391208fc52b81796c0a980b079e5aaa2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875425"
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
つまり、ディメンションの数、配列のランクを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```csharp  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pdwRank`  
 [out]順位を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 使用して、 [GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)配列オブジェクトの各次元のサイズを取得します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)