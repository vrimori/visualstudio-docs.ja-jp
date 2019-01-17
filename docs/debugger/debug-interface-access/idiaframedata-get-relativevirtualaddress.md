---
title: Idiaframedata::get_relativevirtualaddress |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_relativeVirtualAddress method
ms.assetid: de070ef4-6c9d-43ca-911c-5245cbcb8dbe
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f99c7fec3afa2f086f835d0d6295bafdcbdfdf29
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910573"
---
# <a name="idiaframedatagetrelativevirtualaddress"></a>IDiaFrameData::get_relativeVirtualAddress
フレームのコードの相対仮想アドレス (RVA) を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_relativeVirtualAddress (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]フレームのコードの相対仮想アドレスを返します。  
  
## <a name="return-value"></a>戻り値  
 正常に終了した場合は、`S_OK` を返します。 返します`S_FALSE`場合、このプロパティはサポートされていません。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>「  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)