---
title: Idiastackframe::get_localsbase |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_localsBase method
ms.assetid: eb0bd73e-d92d-468e-a0b1-fbc279919f54
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7138bae8ddf987082ede9b216b19396ad8bb02ea
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53883523"
---
# <a name="idiastackframegetlocalsbase"></a>IDiaStackFrame::get_localsBase
フレームのローカル変数のベース アドレスを取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_localsBase (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]ローカル変数のベース アドレスを返します。  
  
## <a name="return-value"></a>戻り値  
 正常に終了した場合は、`S_OK` を返します。 返します`S_FALSE`プロパティがサポートされていない場合。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>「  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)