---
title: Idiaenumframedata::framebyva |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByVA method
ms.assetid: 0b1e441b-710a-46d8-8060-bed39071c834
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5c6f6252c23069ffce01b9b790a44b24efbd80a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949377"
---
# <a name="idiaenumframedataframebyva"></a>IDiaEnumFrameData::frameByVA
仮想アドレス (VA) でフレームを返します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT frameByVA(   
   ULONGLONG       virtualAddress,  
   IDiaFrameData** frame  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 virtualAddress  
 [in]目的のフレームの VA します。  
  
 フレーム  
 [out]返します、 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)を指定したアドレスを含むフレームを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 正常に終了した場合は、`S_OK` を返します。 返します`S_FALSE`フレーム データに指定されたアドレスが一致しない場合。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>「  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)