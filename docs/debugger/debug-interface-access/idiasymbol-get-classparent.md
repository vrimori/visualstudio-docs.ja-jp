---
title: Idiasymbol::get_classparent |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_classParent method
ms.assetid: 99db875a-caae-4d60-ae70-64bc8a9f6fba
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 38f91ff64337fd9a1d18fa9ae63743437fa1287b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53864817"
---
# <a name="idiasymbolgetclassparent"></a>IDiaSymbol::get_classParent
シンボルのクラスの親への参照を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_classParent (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]返します、 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)シンボルのクラスの親を表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティがシンボルを使用できないことを意味します。  
  
## <a name="requirements"></a>要件  
  
|必要条件|説明|  
|-----------------|-----------------|  
|ヘッダー:|dia2.h|  
|バージョン:|DIA SDK v7.0|  
  
## <a name="remarks"></a>コメント  
 クラスの親にするシンボルの種類が記載されて[シンボル型のクラス階層](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)します。  
  
## <a name="see-also"></a>「  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [シンボル型のクラス階層](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)