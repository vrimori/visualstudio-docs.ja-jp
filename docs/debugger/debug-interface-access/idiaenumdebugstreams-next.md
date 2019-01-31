---
title: Idiaenumdebugstreams::next |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Next method
ms.assetid: eb8eae5a-be27-45f4-a7bd-6e4ef0652385
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37236435204bc5fc5d7f971b1ecbf14ca628dd13
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55010429"
---
# <a name="idiaenumdebugstreamsnext"></a>IDiaEnumDebugStreams::Next
指定された数の列挙体シーケンス内の debug ストリームを取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Next (   
   ULONG                     celt,   
   IDiaEnumDebugStreamData** rgelt,  
   ULONG*                    pceltFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 celt  
 [in]デバッグ ストリームを取得する列挙子の数。  
  
 rgelt  
 [out]配列を返します[IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)デバッグを表すオブジェクトをストリームを取得します。  
  
 pceltFetched  
 [out]返されるデバッグ ストリームの数を返します。  
  
## <a name="return-value"></a>戻り値  
 正常に終了した場合は、`S_OK` を返します。 返します`S_FALSE`以上のストリームがありませんがある場合。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>「  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)