---
title: Idiaenumframedata::get_count |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::get_Count method
ms.assetid: 94374d27-e335-4e90-a442-233181ab8e58
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c1f45287ade10ddff6dc10ddea44936890d6208
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005346"
---
# <a name="idiaenumframedatagetcount"></a>IDiaEnumFrameData::get_Count
フレーム データ要素の数を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_Count (   
   LONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pRetVal  
 [out]フレーム データ要素の数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>「  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)