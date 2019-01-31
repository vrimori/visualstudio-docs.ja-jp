---
title: Idiasymbol::get_noinline |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_noInline method
ms.assetid: 5c610b78-f1a3-494a-acf8-c42b97935be1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c40ec5aa549239053848d6eb2a69bd07420df705
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54944606"
---
# <a name="idiasymbolgetnoinline"></a>IDiaSymbol::get_noInline
関数がインラインのものとしてマークされているかどうかを指定するフラグを取得します (を使用して、 [noinline](/cpp/cpp/noinline)属性)。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_noInline(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pFlag`  
 [out]返します`TRUE`関数の場合、 `noinline` 、それ以外の属性`FALSE`します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティが、シンボルの使用可能なことを意味します。  
  
## <a name="requirements"></a>要件  
  
|必要条件|説明|  
|-----------------|-----------------|  
|ヘッダー:|dia2.h|  
|バージョン:|DIA SDK バージョン 8.0|  
  
## <a name="see-also"></a>「  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [noinline](/cpp/cpp/noinline)