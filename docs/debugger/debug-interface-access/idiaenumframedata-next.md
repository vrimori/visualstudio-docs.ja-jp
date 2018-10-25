---
title: Idiaenumframedata::next |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 55320b4f07eb2acda1d46875fa6f3bd5eefe2813
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949982"
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
 成功した場合、返します`S_OK`します。 返します`S_FALSE`レコードがある場合。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)