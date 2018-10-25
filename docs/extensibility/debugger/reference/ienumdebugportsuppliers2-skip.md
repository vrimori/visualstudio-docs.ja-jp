---
title: IEnumDebugPortSuppliers2::Skip |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugPortSuppliers2::Skip
helpviewer_keywords:
- IEnumDebugPortSuppliers2::Skip
ms.assetid: bd95d7e9-274f-485d-8bf6-865306ae1b81
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f1aa661db20a0d12c65f053147062cd43a0363d3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819824"
---
# <a name="ienumdebugportsuppliers2skip"></a>IEnumDebugPortSuppliers2::Skip
指定した要素数をスキップします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celt`  
 [in]スキップする要素の数。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`します。 返します`S_FALSE`場合`celt`が残りの要素の数より大きい。 それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 場合`celt`数より大きい値を指定します。 残りの要素の列挙体が最後に設定し、`S_FALSE`が返されます。  
  
## <a name="see-also"></a>関連項目  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)