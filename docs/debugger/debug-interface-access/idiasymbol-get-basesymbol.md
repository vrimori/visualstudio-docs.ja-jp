---
title: IDiaSymbol::get_baseSymbol |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cabb5a18-bda7-47e8-9e46-5f4718579fc9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 056e479a6d63665fe6121921fb941f04b3f20048
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54987415"
---
# <a name="idiasymbolgetbasesymbol"></a>IDiaSymbol::get_baseSymbol
ポインターを基づいてシンボルを取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_baseSymbol(   
   IDiaSymbol** pRetVal);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]ポインターを基づいてシンボルへのポインター。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
## <a name="see-also"></a>「  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_baseSymbolId](../../debugger/debug-interface-access/idiasymbol-get-basesymbolid.md)