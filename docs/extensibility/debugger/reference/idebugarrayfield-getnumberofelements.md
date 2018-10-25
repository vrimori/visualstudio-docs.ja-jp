---
title: IDebugArrayField::GetNumberOfElements |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayField::GetNumberOfElements
helpviewer_keywords:
- IDebugArrayField::GetNumberOfElements method
ms.assetid: a1961ef3-d69d-4022-b8c9-b9cfb9811345
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1fbb550c438799a02821c255405d94bc9737b3c6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934757"
---
# <a name="idebugarrayfieldgetnumberofelements"></a>IDebugArrayField::GetNumberOfElements
配列内の要素の数を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetNumberOfElements(   
   DWORD* pdwNumElements  
);  
```  
  
```csharp  
int GetNumberOfElements(  
   out uint pdwNumElements  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pdwNumElements`  
 [out]配列内の要素の数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 返される値は、ディメンションの数に関係なく、配列内の要素の合計数です。  
  
## <a name="see-also"></a>関連項目  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)