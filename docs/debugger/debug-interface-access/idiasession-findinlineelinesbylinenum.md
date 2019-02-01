---
title: IDiaSession::findInlineeLinesByLinenum |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cf32ae7c-a0c8-4800-bc8f-d64fdd15fb06
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 432c0859041740c74e6c3264c318d46352d262b3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54972694"
---
# <a name="idiasessionfindinlineelinesbylinenum"></a>IDiaSession::findInlineeLinesByLinenum
により、クライアントは、すべての関数がインライン展開されて、直接または間接的に、指定したソース ファイルと行番号での行番号情報を反復処理する列挙体を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT findInlineeLinesByVA (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 column,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `compiland`  
 [in][IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)行番号を検索するためのコンパイル単位を表すオブジェクト。 このパラメーターを `NULL` とすることはできません。  
  
 `file`  
 [in][IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)を検索するソース ファイルを表すオブジェクト。 このパラメーターを `NULL` とすることはできません。  
  
 `linenum`  
 [in]1 から始まる行番号を指定します。  
  
> [!NOTE]
>  0 を使用して、すべての行を指定することはできません (を使用して、 [idiasession::findlines](../../debugger/debug-interface-access/idiasession-findlines.md)すべての行を検索するメソッド)。  
  
 `column`  
 [in]列番号を指定します。 すべての列を指定するのにには、0 を使用します。 列は、行へのバイト オフセットです。  
  
 `ppResult`  
 [out]返します、 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)取得された行番号の一覧を含むオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>「  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)