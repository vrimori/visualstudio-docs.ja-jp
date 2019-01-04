---
title: IDebugAlias::Dispose |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugAlias::Dispose
helpviewer_keywords:
- IDebugAlias::Dispose method
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 871041c69fafef2154db2794e20212705eaea3c9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53943997"
---
# <a name="idebugaliasdispose"></a>IDebugAlias::Dispose
このエイリアスの削除をマークします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Dispose();  
```  
  
```csharp  
int Dispose();  
```  
  
#### <a name="parameters"></a>パラメーター  
 なし。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドが呼び出されると、エイリアスは使用できなくします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)