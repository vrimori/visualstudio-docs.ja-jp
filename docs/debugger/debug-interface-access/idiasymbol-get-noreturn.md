---
title: Idiasymbol::get_noreturn |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_noReturn method
ms.assetid: 704c1cc0-5b84-4334-a02a-70f43aff39d5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 122a71289fc11e4301476c90e7ed9267cce18681
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55014823"
---
# <a name="idiasymbolgetnoreturn"></a>IDiaSymbol::get_noReturn
関数がで返すことはありませんとしてマークされているかどうかを指定するフラグを取得、 [noreturn](/cpp/cpp/noreturn)属性。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_noReturn(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pFlag  
 [out]返します`TRUE`で返すことはありませんとして関数を宣言されているかどうか、 `noreturn` 、それ以外の属性`FALSE`します。  
  
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
 [noreturn](/cpp/cpp/noreturn)