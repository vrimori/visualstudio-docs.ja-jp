---
title: IDiaEnumSymbolsByAddr |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaEnumSymbolsbyAddr interface
ms.assetid: 37d3dcdf-e4fa-4354-b5e1-8843566b52ac
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0fad99c5e12151df4b01c0153327f359973b50d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539925"
---
# <a name="idiaenumsymbolsbyaddr"></a>IDiaEnumSymbolsByAddr
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDiaEnumSymbolsByAddr](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumsymbolsbyaddr)します。  
  
アドレスを指定して、データ ソースに含まれるさまざまなシンボルを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
IDiaEnumSymbolsByAddr : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDiaEnumSymbolsByAddr`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)|セクションとオフセットで検索を実行して、列挙子を配置します。|  
|[IDiaEnumSymbolsByAddr::symbolByRVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyrva.md)|相対仮想アドレス (RVA) で検索を実行して、列挙子を配置します。|  
|[IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)|仮想アドレス (VA) で検索を実行して、列挙子を配置します。|  
|[IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)|アドレスの順序で次のシンボルを取得します。 フェッチされる要素の数によっては、列挙子の位置を更新します。|  
|[IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)|アドレスの順序で前のシンボルを取得します。 フェッチされる要素の数によっては、列挙子の位置を更新します。|  
|[IDiaEnumSymbolsByAddr::Clone](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-clone.md)|オブジェクトのコピーを作成します。|  
  
## <a name="remarks"></a>Remarks  
 このインターフェイスは、アドレスでグループ化されたシンボルを提供します。 たとえばの種類でグループ化されたシンボルを使用する`SymTagUDT`(ユーザー定義型) または`SymTagBaseClass`を使用して、 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)インターフェイス。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスを呼び出すことによって取得、 [idiasession::getsymbolsbyaddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)メソッド。  
  
## <a name="example"></a>例  
 この関数は、すべてのシンボルを順に相対仮想アドレスのアドレスと名前が表示されます。  
  
```cpp#  
void ShowSymbolsByAddress(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSymbolsByAddr> pEnumByAddr;  
    if ( FAILED( psession->getSymbolsByAddr( &pEnumByAddr ) ) )  
    {  
        Fatal( "getSymbolsByAddr" );  
    }  
    CComPtr<IDiaSymbol> pSym;  
    if ( FAILED( pEnumByAddr->symbolByAddr( 1, 0, &pSym ) ) )  
    {  
        Fatal( "symbolByAddr" );  
    }  
    DWORD rvaLast = 0;  
    if ( pSym->get_relativeVirtualAddress( &rvaLast ) == S_OK )  
    {  
        pSym = 0;  
        if ( FAILED( pEnumByAddr->symbolByRVA( rvaLast, &pSym ) ) )  
        {  
            Fatal( "symbolByAddr" );  
        }  
        printf( "Symbols in order\n" );  
        do  
        {   
            CDiaBSTR name;  
            if ( pSym->get_name( &name ) != S_OK )  
            {  
                printf( "\t0x%08X (%ws) <no name>\n", rvaLast );  
            }  
            else  
            {  
               printf( "\t0x%08X %ws\n", rvaLast, name );  
            }  
            pSym = 0;  
            celt = 0;  
            if ( FAILED( hr = pEnumByAddr->Next( 1, &pSym, &celt ) ) )  
            {  
                break;  
            }  
        } while ( celt == 1 );  
    }  
}  
```  
  
## <a name="requirements"></a>要件  
 ヘッダー: Dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>関連項目  
 [インターフェイス (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiasession::getsymbolsbyaddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)



