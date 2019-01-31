---
title: Idiasymbol::get_packed |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_packed method
ms.assetid: e42ff368-56c4-49a2-8676-f80e349efa21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b52685c66daac5c1f5f3da9d632ff3a03aabd762
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55026427"
---
# <a name="idiasymbolgetpacked"></a>IDiaSymbol::get_packed
ユーザー定義データ型 (UDT) が搭載されたかどうかを指定するフラグを取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_packed (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]返します`TRUE`UDT がパッキング; 場合を返しますそれ以外の場合、`FALSE`します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティがシンボルを使用できないことを意味します。  
  
## <a name="remarks"></a>コメント  
 パック手段をメモリ境界に揃えるの介在する埋め込みなしで、UDT のすべてのメンバーが、できるだけ近くに配置されます。  
  
## <a name="see-also"></a>「  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)