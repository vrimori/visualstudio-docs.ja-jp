---
title: "IDiaSession::findInlineeLinesByAddr |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: bb70e408-eed1-4c9c-b5b1-44323125f48b
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f93d9d04f83b2f23a3ae4e84e60b2b397bbd0c42
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindinlineelinesbyaddr"></a>IDiaSession::findInlineeLinesByAddr
行番号の情報のすべての関数はインライン展開を直接または間接的に指定した親シンボルを反復処理するクライアントを許可し、指定したアドレスの範囲内に含まれる列挙型を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT findInlineeLinesByAddr (   
   IDiaSymbol*           parent,   DWORD                 isect,   DWORD                 offset,   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `parent`  
 [in]`IDiaSymbol`親を表すオブジェクト。  
  
 `isect`  
 [in]アドレスのセクションのコンポーネントを指定します。  
  
 `offset`  
 [in]アドレスのオフセットのコンポーネントを指定します。  
  
 `length`  
 [in]このクエリに対応する、バイト数で、アドレスの範囲を指定します。  
  
 `ppResult`  
 [out]保持する`IDiaEnumLineNumbers`取得される行番号の一覧を含むオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)