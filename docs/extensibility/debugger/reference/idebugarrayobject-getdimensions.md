---
title: IDebugArrayObject::GetDimensions |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0f58db8f1f9d847f7ca69c2c829b57f1e45b5d66
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53849351"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
配列の次元を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetDimensions(   
   DWORD dwCount,  
   DWORD dwDimensions[]  
);  
```  
  
```csharp  
int GetDimensions(  
   [In] uint    dwCount,   
   [Out] uint[] dwDimensions  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwCount`  
 [in]取得するディメンションの数。  
  
 `dwDimensions`  
 [入力、出力]各次元のサイズが入力する配列。 `dwCount` 最大サイズを指定します、`dwDimensions`配列。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 多次元配列の各次元のサイズが異なることができます。 たとえば、3 次元の配列を指定`myarray[3][2][6]`、3、2、および 6 でこのメソッドを返しますが、`dwDimensions`をこの順序でパラメーター。  
  
## <a name="see-also"></a>関連項目  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)