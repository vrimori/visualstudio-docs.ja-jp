---
title: Idiaenumdebugstreams::skip |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Skip method
ms.assetid: 6ec7753c-d7af-4879-b107-1b3442e0b025
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4314af1509cbeb22ad35b372b45e2429aa10476c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54972574"
---
# <a name="idiaenumdebugstreamsskip"></a>IDiaEnumDebugStreams::Skip
指定された数の列挙体シーケンス内の debug ストリームをスキップします。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celt`  
 [in]スキップする列挙体シーケンス内の debug ストリームの数。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`をスキップするレコードがある場合。  
  
## <a name="see-also"></a>「  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)