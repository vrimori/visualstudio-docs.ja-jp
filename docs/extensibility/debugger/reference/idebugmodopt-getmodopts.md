---
title: IDebugModOpt::GetModOpts |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 4be7cf2239b77314646df8285d1a89953f9401fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31112383"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
省略可能な修飾子の一覧を取得します。  
  
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
 [入力、出力].返される要素の数、`rgelt`配列。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)