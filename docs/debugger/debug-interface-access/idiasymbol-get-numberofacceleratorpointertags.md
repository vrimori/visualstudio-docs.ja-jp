---
title: IDiaSymbol::get_numberOfAcceleratorPointerTags |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1886e3ec-b227-4187-8d93-c5144b4b77ae
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 94e052865c94d747bcb36cd81e0b1c023262b0c1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875155"
---
# <a name="idiasymbolgetnumberofacceleratorpointertags"></a>IDiaSymbol::get_numberOfAcceleratorPointerTags
C++ AMP のスタブ関数では、アクセラレータのポインターのタグの数を返します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_numberOfAcceleratorPointerTags(   
   DWORD* count);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `count`  
 [out]ポインターを`DWORD`で C++ AMP のスタブ関数ポインターのタグのアクセラレータの数を保持します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
## <a name="remarks"></a>コメント  
 このメソッドが、 `IDiaSymbol` C++ AMP のアクセラレータのスタブ関数に対応するインターフェイス。  
  
## <a name="see-also"></a>「  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)