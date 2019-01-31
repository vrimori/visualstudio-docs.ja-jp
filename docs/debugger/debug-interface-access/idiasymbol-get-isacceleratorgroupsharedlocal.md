---
title: IDiaSymbol::get_isAcceleratorGroupSharedLocal |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 17a20542-5b45-478f-bb80-0d56031aadb5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10219746f46dfcd9b628d84fdd7c75c1ff93bfb3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54950732"
---
# <a name="idiasymbolgetisacceleratorgroupsharedlocal"></a>IDiaSymbol::get_isAcceleratorGroupSharedLocal
C++ AMP のアクセラレータのコンパイルされたコードでグループの共有ローカル変数に、シンボルが対応かどうかを示すフラグを取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_isAcceleratorGroupSharedLocal(   
   BOOL* pFlag);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pFlag`  
 [out]ポインターを`BOOL`シンボルが C++ AMP のアクセラレータのコンパイルされたコードでグループの共有ローカル変数に対応するかどうかを示します。 場合`TRUE`、`get_baseDataSlot`と`get_baseDataOffset`メソッドは、変数の記憶域の場所情報を取得するために使用できます。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
## <a name="see-also"></a>「  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)   
 [IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)