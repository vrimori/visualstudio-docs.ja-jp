---
title: Idiaenumframedata::next |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Next method
ms.assetid: 546e2e23-efb2-425a-96a1-808c67c519fb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b6a2c4c2a80ea5186b4a3036491bd64a6531d753
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53951564"
---
# <a name="idiaenumframedatanext"></a>IDiaEnumFrameData::Next
指定した列挙体シーケンス内のデータ要素のフレーム数を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Next (   
   ULONG           celt,   
   IDiaFrameData** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 celt  
 [in]フレームを取得する列挙子のデータ要素の数。  
  
 rgelt  
 [out]配列の[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)で要求されたフレームのデータ要素を格納するオブジェクト。  
  
 pceltFetched  
 [out]フェッチされた列挙子では、フレーム データ要素の数を返します。  
  
## <a name="return-value"></a>戻り値  
 正常に終了した場合は、`S_OK` を返します。 返します`S_FALSE`レコードがある場合。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>「  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)