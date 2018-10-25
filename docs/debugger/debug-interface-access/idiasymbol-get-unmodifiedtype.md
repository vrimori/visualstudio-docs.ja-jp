---
title: Idiasymbol::get_unmodifiedtype |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 32e636a35d1cfed085ddf1bc44d60249a71d0b69
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49935754"
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
  
## <a name="remarks"></a>Remarks  
 現在の型が、返された元の型を変更します。 シンボルの元の型は、まず、記号の種類を取得し、元の型の型を返すを問い合わせるで決定できます。 いくつかの記号は、元の型の変更後の型を持てませんに注意してください。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: Dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)