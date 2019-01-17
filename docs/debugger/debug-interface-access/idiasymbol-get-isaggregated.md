---
title: Idiasymbol::get_isaggregated |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isAggregated method
ms.assetid: 24d280ef-6ea3-4958-9418-4ad3ca7c67c1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e288c0bf36b3899ec6398187f87af3a366083da6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53957421"
---
# <a name="idiasymbolgetisaggregated"></a>IDiaSymbol::get_isAggregated
データ シンボルが集計またはシンボルのコレクションの一部であるかどうかを指定するフラグを取得します。コンパイラでは、集計されたシンボルは個別のエンティティとして扱いますが、これらは実際に 1 つの大規模なシンボルの一部です。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_isAggregated(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pFlag`  
 [out]返します`TRUE`データが分割親シンボルからシンボルの集計の一部である場合を返しますそれ以外の場合、`FALSE`します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティが、シンボルの使用可能なことを意味します。  
  
## <a name="remarks"></a>コメント  
 [Idiasymbol::get_issplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)メソッドは`TRUE`の集計されたシンボルの親であるシンボル。  
  
## <a name="requirements"></a>要件  
  
|必要条件|説明|  
|-----------------|-----------------|  
|ヘッダー:|dia2.h|  
|バージョン:|DIA SDK バージョン 8.0|  
  
## <a name="see-also"></a>「  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)