---
title: IDiaSymbol::findInlineeLinesByAddr |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f1ab47ca-c851-48ea-9c12-47fb80b31102
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56b2a70ecd0f8d4b7f9e3d49df0e764923f21fac
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54939609"
---
# <a name="idiasymbolfindinlineelinesbyaddr"></a>IDiaSymbol::findInlineeLinesByAddr
により、クライアントは、行番号の情報がインライン展開されて、直接または間接的に、この記号を指定したアドレスの範囲内のすべての関数を反復処理する列挙体を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT findInlineeLinesByAddr (   
   DWORD                 isect,  
   DWORD                 offset,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `isect`  
 [in]アドレスのセクションのコンポーネントを指定します。  
  
 `offset`  
 [in]アドレスのオフセットのコンポーネントを指定します。  
  
 `length`  
 [in]このクエリをカバーする、バイト数では、アドレスの範囲を指定します。  
  
 `ppResult`  
 [out]保持する`IDiaEnumLineNumbers`取得される行番号の一覧を含むオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>「  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)