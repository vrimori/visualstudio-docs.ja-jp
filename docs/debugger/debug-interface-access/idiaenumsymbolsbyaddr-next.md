---
title: Idiaenumsymbolsbyaddr::next |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Next method
ms.assetid: a1320587-7ce7-401f-9548-2f8bcece5cc3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 473fcb49839635090e39bf245ad56ce2554c77dd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879923"
---
# <a name="idiaenumsymbolsbyaddrnext"></a>IDiaEnumSymbolsByAddr::Next
アドレスの順序で次のシンボルを取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Next (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 celt  
 [in]シンボルを取得する列挙子の数。  
  
 rgelt  
 [out]格納する配列、 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)必要なシンボルを表すオブジェクト。  
  
 pceltFetched  
 [out]フェッチされた列挙子の記号の数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`します。 返します`S_FALSE`シンボルがある場合。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、フェッチされる要素の数によって、列挙子の位置を更新します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)