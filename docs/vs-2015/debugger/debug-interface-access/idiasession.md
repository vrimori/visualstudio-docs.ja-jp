---
title: IDiaSession |Microsoft Docs
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
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a2ff17cc95769a9cada09b31b800afeaa13a44a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252981"
---
# <a name="idiasession"></a>IDiaSession
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

デバッグ シンボルのクエリ コンテキストを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
IDiaSession : IUnknown  
```  
  
## <a name="methods"></a>メソッド  
 次の表は、メソッドの`IDiaSession`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|このシンボル ストア内のシンボルに対応する実行可能ファイルの読み込みアドレスを取得します。 これは、同じ値に渡された、`put_loadAddress`メソッド。|  
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|このシンボル ストアのシンボルに対応する実行可能ファイルの読み込みアドレスを設定します。 **注:** するを取得する場合は、このメソッドを呼び出すことが重要、`IDiaSession`オブジェクトし、オブジェクトの使用を開始する前にします。|  
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|グローバル スコープへの参照を取得します。|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|シンボル ストアに含まれているすべてのテーブルの列挙子を取得します。|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|静的な場所にあるすべての名前付きシンボルの列挙子を取得します。|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|指定した親の識別子の名前とシンボルの種類に一致するすべての子を取得します。|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|が含まれているか、指定したアドレスに最も近い指定の記号の型を取得します。|  
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|または、指定された相対仮想アドレス (RVA) に最も近いする指定の記号の型を取得します。|  
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|または、指定された仮想アドレス (VA) に最も近いする指定の記号の型を取得します。|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|指定したメタデータ トークンが含まれているシンボルを取得します。|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|2 つのシンボルが等しいかどうかを確認します。|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|一意の識別子をシンボルを取得します。|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|が含まれているか、指定の相対仮想アドレスとオフセットに最も近い指定の記号の型を取得します。|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|が含まれているか、指定された仮想アドレスとオフセットに最も近い指定の記号の型を取得します。|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|コンパイル単位と名前のソース ファイルを取得します。|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|ソース ファイルの識別子を使用してソース ファイルを取得します。|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|指定したコンパイル単位とソース ファイルの識別子内で行番号を取得します。|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|指定したコンパイル単位で指定されたアドレスが含まれている行を取得します。|  
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|指定したコンパイル単位で指定された相対仮想アドレスが含まれている行を取得します。|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|指定されたアドレス範囲に含まれる行の行番号情報を検索します。|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|ソース ファイルと行番号で指定したコンパイル単位内の行を取得します。|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|属性プロバイダーによってシンボル ストアに、コンパイル プロセスの他のコンポーネントに配置されたソースを取得します。|  
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|デバッグのデータ ストリームの列挙のシーケンスを取得します。|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|により、クライアントは、すべての指定したアドレスにインライン フレームを反復処理する列挙体を取得します。|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|により、クライアントは、すべての指定された相対仮想アドレス (RVA) でのインライン フレームを反復処理する列挙体を取得します。|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|により、クライアントは、すべての指定した仮想アドレス (VA) にインライン フレームを反復処理する列挙体を取得します。|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|により、クライアントは直接、インライン展開はすべての関数の直接的または間接的に指定した親シンボルの行番号情報を反復処理する列挙体を取得します。|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|により、クライアントは直接、インライン展開はすべての関数の直接的または間接的に指定した親シンボルの行番号情報を反復処理して、指定したアドレスの範囲内に含まれる列挙体を取得します。|  
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|により、クライアントは直接、インライン展開はすべての関数の直接的または間接的に指定した親シンボルの行番号情報を反復処理して、指定された相対仮想アドレス (RVA) 内に含まれる列挙体を取得します。|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|により、クライアントは直接、インライン展開はすべての関数の直接的または間接的に指定した親シンボルの行番号情報を反復処理して、指定された仮想アドレス (VA) 内に含まれる列挙体を取得します。|  
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|により、クライアントは、すべての関数がインライン展開されて、直接または間接的に、指定したソース ファイルと行番号での行番号情報を反復処理する列挙体を取得します。|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|により、クライアントは、指定した名前と一致するすべてのインライン関数の行番号情報を反復処理する列挙体を取得します。|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|親のアクセラレータのスタブ関数で指定したタグ値に対応する変数のシンボルの列挙を返します。|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|対応するタグの値を指定すると、このメソッドは、指定の相対仮想アドレスにある指定した親アクセラレータ スタブ関数に含まれているシンボルの列挙体を返します。|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|指定されたインライン関数の名前に対応するインライン フレームのシンボルの列挙を返します。|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|指定したソースの場所に対応するインライン フレームのシンボルの列挙を返します。|  
  
## <a name="remarks"></a>Remarks  
 呼び出しすることが重要、 [idiasession::put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)メソッドを作成した後、`IDiaSession`オブジェクト-に渡される値と、`put_loadAddress`メソッドは 0 以外である必要があります: するシンボルの仮想アドレス (VA) プロパティのアクセスできます。 どのようなプログラムにはデバッグ中の実行可能ファイルが読み込まれてからの読み込みアドレスが取得されます。 たとえば、Win32 関数を呼び出すことができます`GetModuleInformation`ハンドルを指定して実行可能ファイル、実行可能ファイルの読み込みアドレスを取得します。  
  
## <a name="example"></a>例  
 この例は、取得する方法を示します、 `IDiaSession` DIA SDK の一般的な初期化の一環としてインターフェイス。  
  
```cpp#  
CComPtr<IDiaDataSource> pSource;  
ComPtr<IDiaSession> psession;  
  
void InitializeDIA(const char *szFilename)  
{  
    HRESULT hr = CoCreateInstance( CLSID_DiaSource,  
                                   NULL,  
                                   CLSCTX_INPROC_SERVER,  
                                   __uuidof( IDiaDataSource ),  
                                  (void **) &pSource);  
    if (FAILED(hr))  
    {  
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );  
    }  
    wchar_t wszFilename[ _MAX_PATH ];  
    mbstowcs( wszFilename,  
              szFilename,  
              sizeof( wszFilename )/sizeof( wszFilename[0] ) );  
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )  
    {  
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )  
        {  
            Fatal( "loadDataFromPdb/Exe" );  
        }  
    }  
    if ( FAILED( pSource->openSession( &psession ) ) )  
    {  
        Fatal( "openSession" );  
    }  
}  
```  
  
## <a name="requirements"></a>要件  
 ヘッダー: Dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>関連項目  
 [インターフェイス (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [概要](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [実行可能ファイル](../../debugger/debug-interface-access/exe.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idiadatasource::opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [Idiasymbol::findchildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [.Pdb ファイルの照会](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)



