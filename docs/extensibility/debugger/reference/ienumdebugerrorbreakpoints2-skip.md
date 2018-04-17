---
title: IEnumDebugErrorBreakpoints2::Skip |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugErrorBreakpoints2::Skip
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2::Skip
ms.assetid: a5a02b38-4e3a-4f0e-b529-f770c3485c8b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3aea378f589346df2b96a1d667bc16930c5a0744
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugerrorbreakpoints2skip"></a>IEnumDebugErrorBreakpoints2::Skip
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
 成功した場合を返します`S_OK`です。 返します`S_FALSE`場合`celt`残りの要素の数よりも大きいです。 それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 場合`celt`数より大きい値を指定して残りの要素の列挙体が最後に設定し、`S_FALSE`が返されます。  
  
## <a name="see-also"></a>関連項目  
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)