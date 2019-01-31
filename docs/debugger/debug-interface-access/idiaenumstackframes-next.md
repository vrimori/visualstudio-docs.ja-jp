---
title: Idiaenumstackframes::next |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00be37ffa1724cb6ced2423ea388b2a24dae42f3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54919969"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
列挙体シーケンスから、指定したスタック フレームの要素数を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Next(   
   ULONG             celt,  
   IDiaStackFrame**  rgelt,  
   ULONG*            pceltFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 celt  
 [in]スタック フレームを取得する列挙子の要素の数。  
  
 rgelt  
 [out]要求を格納する配列を[IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)オブジェクト。  
  
 pceltFetched  
 [out]フェッチされた列挙子内のスタックのフレーム要素を返します。  
  
## <a name="return-value"></a>戻り値  
 正常に終了した場合は、`S_OK` を返します。 返します`S_FALSE`スタック フレームがある場合。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>「  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)