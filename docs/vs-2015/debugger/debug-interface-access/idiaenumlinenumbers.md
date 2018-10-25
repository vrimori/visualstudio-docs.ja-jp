---
title: IDiaEnumLineNumbers |Microsoft Docs
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
helpviewer_keywords:
- IDiaEnumLineNumbers interface
ms.assetid: cdf07b4f-19e4-4dcd-8af8-c2dbca586a7c
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aaf502093c45e3f615bc7dec582ef46ce8e9b47d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49266046"
---
# <a name="idiaenumlinenumbers"></a>IDiaEnumLineNumbers
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

データ ソースに含まれるさまざまな行番号を列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
IDiaEnumLineNumbers : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDiaEnumLineNumbers`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDiaEnumLineNumbers::get__NewEnum](../../debugger/debug-interface-access/idiaenumlinenumbers-get-newenum.md)|取得、 [IEnumVARIANT インターフェイス](http://msdn.microsoft.com/en-us/139e3c93-faef-4003-9079-e0e94494db3e)この列挙子のバージョン。|  
|[IDiaEnumLineNumbers::get_Count](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md)|行番号の数を取得します。|  
|[IDiaEnumLineNumbers::Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md)|インデックスを使用して、行番号を取得します。|  
|[IDiaEnumLineNumbers::Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md)|指定された数の列挙体シーケンス内の行番号を取得します。|  
|[IDiaEnumLineNumbers::Skip](../../debugger/debug-interface-access/idiaenumlinenumbers-skip.md)|指定された数の列挙体シーケンス内の行番号をスキップします。|  
|[IDiaEnumLineNumbers::Reset](../../debugger/debug-interface-access/idiaenumlinenumbers-reset.md)|先頭に、列挙体シーケンスをリセットします。|  
|[IDiaEnumLineNumbers::Clone](../../debugger/debug-interface-access/idiaenumlinenumbers-clone.md)|現在の列挙子と同じ列挙状態を格納する列挙子を作成します。|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスは、次のメソッドのいずれかを呼び出すことによって取得は、 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)インターフェイス。  
  
-   [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)  
  
-   [IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)  
  
-   [IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)  
  
-   [IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)  
  
-   [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)  
  
## <a name="example"></a>例  
 この例は、取得する方法を示します、`IDiaEnumLineNumbers`セッションからのインターフェイス。 関数行番号の列挙を取得する方法を示しますこの場合、(によって表される`pSymbol`)。 行番号を使用してのより完全な例を参照してください、 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)インターフェイス。  
  
```cpp#  
void dumpFunctionLines( IDiaSymbol* pSymbol, IDiaSession* pSession )  
{  
    ULONGLONG length = 0;  
    DWORD isect = 0;  
    DWORD offset = 0;  
    pSymbol->get_addressSection( &isect );  
    pSymbol->get_addressOffset( &offset );  
    pSymbol->get_length( &length );  
    if ( isect != 0 && length > 0 )  
    {  
        CComPtr< IDiaEnumLineNumbers > pLines;  
        if ( SUCCEEDED( pSession->findLinesByAddr(  
                                      isect,  
                                      offset,  
                                      static_cast<DWORD>( length ),  
                                      &pLines )  
                      )  
           )  
        {  
            // Do something with the enumeration  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>要件  
 ヘッダー: Dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>関連項目  
 [インターフェイス (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Idiasession::findlinesbylinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [Idiasession::findlinesbyrva](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)   
 [Idiasession::findlinesbyva](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)   
 [Idiasession::findlines](../../debugger/debug-interface-access/idiasession-findlines.md)   
 [IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)



