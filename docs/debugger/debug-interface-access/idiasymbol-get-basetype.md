---
title: Idiasymbol::get_basetype |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_baseType method
ms.assetid: 5c69a241-a8d3-48ed-8b36-27463a196572
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c9e30e8b60457f03f7d30799f6f18581cc25fe43
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idiasymbolgetbasetype"></a>IDiaSymbol::get_baseType
このシンボルの基本データ型を取得*です。*  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_baseType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]値を返します、 [BasicType 列挙型](../../debugger/debug-interface-access/basictype.md)シンボルの基本型を指定する列挙です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値の`S_FALSE`プロパティが、シンボルを使用できないことを意味します。  
  
## <a name="remarks"></a>コメント  
 シンボル用の基本的な型は、まず、シンボルの種類を取得し、し、その基本型の型が返されますの問い合わせで決定できます。 いくつかの記号可能性がありますいない必要がある基本データ型: 構造体名ではたとえば、します。  
  
## <a name="example"></a>例  
  
```C++  
IDiaSymbol* pType;  
CComPtr<IDiaSymbol> pBaseType;  
if (pType->get_type( &pBaseType ) == S_OK)  
{  
    BasicType btBaseType;  
    if (pBaseType->get_baseType((DWORD *)&btBaseType) == S_OK)  
    {  
        // Do something with basic type.  
    }  
}  
```  
  
## <a name="requirements"></a>要件  
  
|必要条件|説明|  
|-----------------|-----------------|  
|ヘッダー:|dia2.h|  
|バージョン:|DIA SDK v7.0|  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [BasicType 列挙型](../../debugger/debug-interface-access/basictype.md)   
 [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)