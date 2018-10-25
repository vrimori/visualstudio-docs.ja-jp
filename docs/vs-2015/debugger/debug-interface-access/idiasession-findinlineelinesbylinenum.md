---
title: IDiaSession::findInlineeLinesByLinenum |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: cf32ae7c-a0c8-4800-bc8f-d64fdd15fb06
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c5c657ac37c950dc9dde923a1a28dab76beb33fa
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49929830"
---
# <a name="idiasessionfindinlineelinesbylinenum"></a>IDiaSession::findInlineeLinesByLinenum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

により、クライアントは、すべての関数がインライン展開されて、直接または間接的に、指定したソース ファイルと行番号での行番号情報を反復処理する列挙体を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [in][IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)行番号を検索するためのコンパイル単位を表すオブジェクト。 このパラメーターにすることはできません`NULL`します。  
  
 `file`  
 [in][IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)を検索するソース ファイルを表すオブジェクト。 このパラメーターにすることはできません`NULL`します。  
  
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
  
## <a name="see-also"></a>関連項目  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)



