---
title: Idiasymbol::get_unmodifiedtype |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_unmodifiedType method
ms.assetid: bf914dc0-ff84-4f5d-9f75-1733b17f3be0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fe76a3155941c9f7a3c6cc02d02291e61c8e4e89
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53898558"
---
# <a name="idiasymbolgetunmodifiedtype"></a>IDiaSymbol::get_unmodifiedType
このシンボルには、元の型を取得します。 使用する場合、 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)型に設定されます。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_unmodifiedType(   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]返します、 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)このシンボルの元の型を表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティが、シンボルの使用可能なことを意味します。  
  
## <a name="remarks"></a>コメント  
 現在の型が、返された元の型を変更します。 シンボルの元の型は、まず、記号の種類を取得し、元の型の型を返すを問い合わせるで決定できます。 いくつかの記号は、元の型の変更後の型を持てませんに注意してください。  
  
## <a name="requirements"></a>要件  
 ヘッダー:dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>「  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)