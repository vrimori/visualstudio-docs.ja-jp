---
title: IDebugModOpt::GetModOpts |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3ef054e35fe136b0b3280494b3dfd43cd58a53d5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53908242"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
オプションの修飾子の一覧を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetModOpts(  
   ULONG  celt,  
   BSTR*  rgelt,  
   ULONG* pceltFetched  
);  
```  
  
```csharp  
int GetModOpts(  
   uint         celt,  
   out string[] rgelt,  
   ref uint     pceltFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celt`  
 [in]返される要素の数。  
  
 `rgelt`  
 [out]オプションを含む配列を返します。  
  
 `pceltFetched`  
 [入力、出力]返される要素の数、`rgelt`配列。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)