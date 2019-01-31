---
title: IDiaSymbol::get_isPointerToDataMember |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ef17c737-242e-43e8-b7e1-2c3bc58cfcef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 13a4f117ca9e19c932a56ab3a68caf457dfa0fe6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009259"
---
# <a name="idiasymbolgetispointertodatamember"></a>IDiaSymbol::get_isPointerToDataMember
このシンボルがデータ メンバーへのポインターであるかどうかを指定します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_isPointerToDataMember(   
   BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]ポインターを`BOOL`シンボルは、データ メンバーへのポインターであるかどうかを指定します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
## <a name="see-also"></a>「  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)