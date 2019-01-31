---
title: Idiastackframe::get_lengthprolog |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_lengthProlog method
ms.assetid: 9894c5ca-835f-41e9-a35e-70e046dfb7f0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74232b3189d75b53ab9c7f8cc2da9160e75c3112
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54926016"
---
# <a name="idiastackframegetlengthprolog"></a>IDiaStackFrame::get_lengthProlog
プロローグ コード ブロック内のバイト数を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_lengthProlog (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]プロローグ コードのバイト数を返します。  
  
## <a name="return-value"></a>戻り値  
 正常に終了した場合は、`S_OK` を返します。 返します`S_FALSE`プロパティがサポートされていない場合。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>「  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)