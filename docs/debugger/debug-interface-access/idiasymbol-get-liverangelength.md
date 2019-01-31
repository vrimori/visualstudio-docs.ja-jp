---
title: IDiaSymbol::get_liveRangeLength |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeLength
ms.assetid: ffcce3cc-085c-44eb-8145-46e3819c54f9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 774ea527cb34b1be1a27bed2904788498390ec10
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54968883"
---
# <a name="idiasymbolgetliverangelength"></a>IDiaSymbol::get_liveRangeLength
ローカル シンボルの有効なアドレスの範囲の長さを返します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_liveRangeLength (   
   ULONGLONG* length  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `length`  
 [out]アドレスの範囲の長さを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
> [!NOTE]
>  返されたエラー コードは、シンボルにライブの範囲の情報がないことを意味します。  
  
## <a name="remarks"></a>コメント  
  
## <a name="requirements"></a>要件  
 ヘッダー:dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>「  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)