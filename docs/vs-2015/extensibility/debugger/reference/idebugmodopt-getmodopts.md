---
title: IDebugModOpt::GetModOpts |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c1c24888fc62d3a3f79e375b720a41c9364d6e37
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780400"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

オプションの修飾子の一覧を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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

