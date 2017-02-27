---
title: "IDiaSectionContrib | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSectionContrib インターフェイス"
ms.assetid: 371d40f6-ca0e-4d7e-9210-64d3768996c6
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# IDiaSectionContrib
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

セクションの情報コンパイル単位にイメージに使用されるメモリのつまり連続したブロックを記述したデータを取得します。  
  
## 構文  
  
```  
IDiaSectionContrib : IUnknown  
```  
  
## Vtable の順序でメソッド  
 次の表は `IDiaSectionContrib` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[IDiaSectionContrib::get\_compiland](../../debugger/debug-interface-access/idiasectioncontrib-get-compiland.md)|このセクションを提供するコンパイル単位のシンボルへの参照を取得します。|  
|[IDiaSectionContrib::get\_addressSection](../../debugger/debug-interface-access/idiasectioncontrib-get-addresssection.md)|指定のアドレスでの部分を取得します。|  
|[IDiaSectionContrib::get\_addressOffset](../../debugger/debug-interface-access/idiasectioncontrib-get-addressoffset.md)|指定のアドレスのオフセットの部分を取得します。|  
|[IDiaSectionContrib::get\_relativeVirtualAddress](../Topic/IDiaSectionContrib::get_relativeVirtualAddress.md)|要素の \(RVA\) イメージの相対仮想アドレスを取得します。|  
|[IDiaSectionContrib::get\_virtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-virtualaddress.md)|処理の \(VA\) 仮想アドレスを取得します。|  
|[IDiaSectionContrib::get\_length](../../debugger/debug-interface-access/idiasectioncontrib-get-length.md)|セクションのバイト数を取得します。|  
|[IDiaSectionContrib::get\_notPaged](../../debugger/debug-interface-access/idiasectioncontrib-get-notpaged.md)|セクションはメモリからページングできるかどうかを示すフラグを取得します。|  
|[IDiaSectionContrib::get\_nopad](../../debugger/debug-interface-access/idiasectioncontrib-get-nopad.md)|セクションに次メモリの境界に埋められた必要であるかどうかを示すフラグを取得します。|  
|[IDiaSectionContrib::get\_code](../Topic/IDiaSectionContrib::get_code.md)|セクションには実行可能コードが含まれているかどうかを示すフラグを取得します。|  
|[IDiaSectionContrib::get\_code16bit](../../debugger/debug-interface-access/idiasectioncontrib-get-code16bit.md)|では 16 ビット コードが含まれているかどうかを示すフラグを取得します。|  
|[IDiaSectionContrib::get\_initializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-initializeddata.md)|セクションは初期化済みデータが含まれているかどうかを示すフラグを取得します。|  
|[IDiaSectionContrib::get\_uninitializedData](../Topic/IDiaSectionContrib::get_uninitializedData.md)|セクションでは初期化されていないデータが含まれているかどうかを示すフラグを取得します。|  
|[IDiaSectionContrib::get\_informational](../../debugger/debug-interface-access/idiasectioncontrib-get-informational.md)|セクションがコメントまたは類似した情報が含まれているかどうかを示すフラグを取得します。|  
|[IDiaSectionContrib::get\_remove](../../debugger/debug-interface-access/idiasectioncontrib-get-remove.md)|これはインメモリ イメージの一部に実行する前にセクションが削除されているかどうかを示すフラグを取得します。|  
|[IDiaSectionContrib::get\_comdat](../../debugger/debug-interface-access/idiasectioncontrib-get-comdat.md)|セクションは COMDAT の記録中であるかどうかを示すフラグを取得します。|  
|[IDiaSectionContrib::get\_discardable](../../debugger/debug-interface-access/idiasectioncontrib-get-discardable.md)|セクションでは破棄できるかどうかを示すフラグを取得します。|  
|[IDiaSectionContrib::get\_notCached](../../debugger/debug-interface-access/idiasectioncontrib-get-notcached.md)|セクションをキャッシュできるかどうかを示すフラグを取得します。|  
|[IDiaSectionContrib::get\_share](../../debugger/debug-interface-access/idiasectioncontrib-get-share.md)|セクションはメモリで共有できるかどうかを示すフラグを取得します。|  
|[IDiaSectionContrib::get\_execute](../../debugger/debug-interface-access/idiasectioncontrib-get-execute.md)|セクションではコードとして実行できるかどうかを示すフラグを取得します。|  
|[IDiaSectionContrib::get\_read](../../debugger/debug-interface-access/idiasectioncontrib-get-read.md)|セクションを読み取ることができるかどうかを示すフラグを取得します。|  
|[IDiaSectionContrib::get\_write](../../debugger/debug-interface-access/idiasectioncontrib-get-write.md)|セクションを書き込むことができるかどうかを示すフラグを取得します。|  
|[IDiaSectionContrib::get\_dataCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-datacrc.md)|セクションのデータ \(CRC\) を巡回詳細チェックを取得します。|  
|[IDiaSectionContrib::get\_relocationsCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-relocationscrc.md)|セクションの再配置の詳細に CRC を取得します。|  
|[IDiaLineNumber::get\_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|セクションのコンパイル単位の識別子を取得します。|  
  
## 解説  
  
## 呼び出し元のメモ  
 このインターフェイスは [IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md) と [IDiaEnumSectionContribs::Next](../Topic/IDiaEnumSectionContribs::Next.md) のメソッドを呼び出すことになります。  `IDiaSectionContrib` インターフェイスを取得する例については[IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) のインターフェイスを参照してください。  
  
## 使用例  
 この関数は関連するシンボルとともに各セクションのアドレスを示します。  `IDiaSectionContrib` のインターフェイスがどのように取得されたかについて [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) のインターフェイスを参照してください。  
  
```cpp#  
void PrintSectionContrib(IDiaSectionContrib* pSecContrib, IDiaSession* pSession)  
{  
    if (pSecContrib != NULL && pSession != NULL)  
    {  
        DWORD rva;  
        if ( pSecContrib->get_relativeVirtualAddress( &rva ) == S_OK )  
        {  
            printf( "\taddr: 0x%.8X", rva );  
            pSecContrib = NULL;  
            CComPtr<IDiaSymbol> pSym;  
            if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )  
            {  
                CDiaBSTR name;  
                DWORD    tag;  
                pSym->get_symTag( &tag );  
                pSym->get_name( &name );  
                printf( "     symbol: %ws (%ws)\n",  
                        name != NULL ? name : L"",  
                        szTags[ tag ] );  
            }  
            else  
            {  
                printf( "<no symbol found?>\n" );  
            }  
        }  
        else  
        {  
            DWORD isect;  
            DWORD offset;  
            pSecContrib->get_addressSection( &isect );  
            pSecContrib->get_addressOffset( &offset );  
            printf( "\taddr: 0x%.4X:0x%.8X", isect, offset );  
            pSecContrib = NULL;  
            CComPtr<IDiaSymbol> pSym;  
            if ( SUCCEEDED( psession->findSymbolByAddr(  
                                              isect,  
                                              offset,  
                                              SymTagNull,  
                                              &pSym )  
                          )  
               )  
            {  
                CDiaBSTR name;  
                DWORD    tag;  
                pSym->get_symTag( &tag );  
                pSym->get_name( &name );  
                printf( "     symbol: %ws (%ws)\n",  
                    name != NULL ? name : L"",  
                    szTags[ tag ] );  
            }  
            else  
            {  
                printf( "<no symbol found?>\n" );  
            }  
        }  
    }  
}  
```  
  
## 必要条件  
 ヘッダー : Dia2.h  
  
 ライブラリ : diaguids.lib  
  
 DLL: msdia80.dll  
  
## 参照  
 [インターフェイス \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)   
 [IDiaEnumSectionContribs::Next](../Topic/IDiaEnumSectionContribs::Next.md)