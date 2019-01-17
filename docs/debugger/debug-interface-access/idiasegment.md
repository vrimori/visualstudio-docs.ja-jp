---
title: IDiaSegment |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment interface
ms.assetid: 384ae0e1-077e-4d4f-98de-ac43c32c882f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4f4cc24d64d3d1b1f8ab3e4182c21d451763b15e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53847192"
---
# <a name="idiasegment"></a>IDiaSegment
セクション数からアドレス空間のセグメントにデータをマップします。  
  
## <a name="syntax"></a>構文  
  
```  
IDiaSegment : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDiaSegment`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDiaSegment::get_frame](../../debugger/debug-interface-access/idiasegment-get-frame.md)|セグメントの数を取得します。|  
|[IDiaSegment::get_offset](../../debugger/debug-interface-access/idiasegment-get-offset.md)|セグメントのセクションの開始位置のオフセットを取得します。|  
|[IDiaSegment::get_length](../../debugger/debug-interface-access/idiasegment-get-length.md)|セグメント内のバイト数を取得します。|  
|[IDiaSegment::get_read](../../debugger/debug-interface-access/idiasegment-get-read.md)|セグメントを読み取れるかどうかを示すフラグを取得します。|  
|[IDiaSegment::get_write](../../debugger/debug-interface-access/idiasegment-get-write.md)|セグメントを変更できるかどうかを示すフラグを取得します。|  
|[IDiaSegment::get_execute](../../debugger/debug-interface-access/idiasegment-get-execute.md)|セグメントが実行可能かどうかを示すフラグを取得します。|  
|[IDiaSegment::get_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|このセグメントに対応するセクションを取得します。|  
|[IDiaSegment::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasegment-get-relativevirtualaddress.md)|セクションの先頭の相対仮想アドレス (RVA) を取得します。|  
|[IDiaSegment::get_virtualAddress](../../debugger/debug-interface-access/idiasegment-get-virtualaddress.md)|セクションの先頭の仮想アドレス (VA) を取得します。|  
  
## <a name="remarks"></a>コメント  
 ほとんどのアプリケーションのことはありません、DIA SDK は既に、相対仮想アドレスをセクションのオフセット位置から翻訳を実行するためのセグメント マップ内の情報を使用します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスを呼び出すことによって取得、 [idiaenumsegments::item](../../debugger/debug-interface-access/idiaenumsegments-item.md)または[idiaenumsegments::next](../../debugger/debug-interface-access/idiaenumsegments-next.md)メソッド。 詳細については、例を参照してください。  
  
## <a name="example"></a>例  
 この関数には、テーブルと最も近いシンボルのすべてのセグメントのアドレスが表示されます。  
  
```C++  
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pSegments;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                _uuidof( IDiaEnumSegments ),  
                               (void**)&pSegments )  
                  )  
       )  
    {  
        CComPtr<IDiaSegment> pSegment;  
        while ( SUCCEEDED( hr = pSegments->Next( 1, &pSegment, &celt ) ) &&  
                celt == 1 )  
        {  
            DWORD rva;  
            DWORD seg;  
  
            pSegment->get_addressSection( &seg );  
            if ( pSegment->get_relativeVirtualAddress( &rva ) == S_OK )  
            {  
                printf( "Segment %i addr: 0x%.8X\n", seg, rva );  
                pSegment = NULL;  
  
                CComPtr<IDiaSymbol> pSym;  
                if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )  
                {  
                    CDiaBSTR name;  
                    DWORD    tag;  
  
                    pSym->get_symTag( &tag );  
                    pSym->get_name( &name );  
                    printf( "\tClosest symbol: %ws (%ws)\n",  
                            name != NULL ? name : L"",  
                            szTags[ tag ] );  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>要件  
 ヘッダー:dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>「  
 [インターフェイス (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)   
 [IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)