---
title: Idiaenumsymbolsbyaddr::prev |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Prev method
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e165268c1d31c61ba671f6087cc9922bf37e4103
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49870277"
---
# <a name="idiaenumsymbolsbyaddrprev"></a>IDiaEnumSymbolsByAddr::Prev
アドレスの順序で前のシンボルを取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Prev (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 celt  
 [in]シンボルを取得する列挙子の数。  
  
 rgelt  
 [out]格納する配列[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)必要なシンボルを表すオブジェクト。  
  
 pceltFetched  
 [out]フェッチされた列挙子の記号の数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`します。 返します`S_FALSE`前のシンボルがない場合。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、フェッチされる要素の数によって、列挙子の位置を更新します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)