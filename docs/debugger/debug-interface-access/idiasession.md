---
title: "IDiaSession |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f3939ab86cd9f0948a2be44756b9ed94d143ecc8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idiasession"></a>IDiaSession
デバッグ シンボルをクエリのコンテキストを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
IDiaSession : IUnknown  
```  
  
## <a name="methods"></a>メソッド  
 次の表は、メソッドの`IDiaSession`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|このシンボル ストア内のシンボルに対応する実行可能ファイルの読み込みアドレスを取得します。 これに渡されたものと同じ値、`put_loadAddress`メソッドです。|  
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|このシンボル ストアで、シンボルに対応する実行可能ファイルの読み込みアドレスを設定します。 **注:**を取得する場合は、このメソッドを呼び出すことが重要な`IDiaSession`オブジェクトおよびオブジェクトの使用を開始する前にします。|  
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|グローバル スコープへの参照を取得します。|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|シンボル ストアに含まれているすべてのテーブルの列挙子を取得します。|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|静的な場所にあるすべての名前付きシンボルの列挙子を取得します。|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|指定した親の識別子の名と記号の種類に一致するすべての子を取得します。|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|が含まれているか、指定したアドレスに最も近いを指定した記号の型を取得します。|  
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|が含まれているか、指定された相対仮想アドレス (RVA) に最も近いを指定した記号の型を取得します。|  
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|が含まれているか、指定した仮想アドレス (VA) に最も近いを指定した記号の型を取得します。|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|指定したメタデータ トークンを含むシンボルを取得します。|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|2 つのシンボルが等しいかどうかを確認します。|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|一意の識別子、シンボルを取得します。|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|が含まれているか、指定の相対仮想アドレスとオフセットに最も近いを指定した記号の型を取得します。|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|が含まれているか、指定された仮想アドレスとオフセットに最も近いを指定した記号の型を取得します。|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|コンパイル単位と名前によってソース ファイルを取得します。|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|ソース ファイルをソース ファイル識別子を取得します。|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|指定したコンパイル単位とソース ファイル識別子内で行番号を取得します。|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|指定コンパイル単位で指定されたアドレスを含む行を取得します。|  
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|指定のコンパイル単位で指定された相対仮想アドレスを含む行を取得します。|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|指定されたアドレス範囲に含まれる行の行番号情報を検索します。|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|ソース ファイルと行番号で指定されたコンパイル単位内の行を取得します。|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|属性のプロバイダーがシンボル ストアまたはコンパイル処理の他のコンポーネントに配置されていますが、ソースを取得します。|  
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|デバッグのデータ ストリームの列挙のシーケンスを取得します。|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|すべての指定したアドレスのインライン フレームを反復処理するクライアントを許可する列挙体を取得します。|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|すべての指定された相対仮想アドレス (RVA) でのインライン フレームを反復処理するクライアントを許可する列挙体を取得します。|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|指定された仮想アドレス (VA) 上のインライン フレームのすべての反復処理にクライアントを許可する列挙体を取得します。|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|行番号の情報のすべての関数はインライン展開を直接または間接的に指定した親シンボルを反復処理するクライアントを許可する列挙体を取得します。|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|行番号の情報のすべての関数はインライン展開を直接または間接的に指定した親シンボルを反復処理するクライアントを許可し、指定したアドレスの範囲内に含まれる列挙型を取得します。|  
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|行番号の情報のすべての関数はインライン展開を直接または間接的に指定した親シンボルを反復処理するクライアントは、指定された相対仮想アドレス (RVA) 内に含まれている列挙を取得します。|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|行番号の情報のすべての関数はインライン展開を直接または間接的に指定した親シンボルを反復処理するクライアントは、指定された仮想アドレス (VA) 内に含まれている列挙を取得します。|  
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|すべての関数のインライン展開され、直接または間接的に含まれていない、指定されたソース ファイルと行番号の行番号情報を反復処理するクライアントを許可する列挙体を取得します。|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|指定した名前に一致するすべてのインライン関数の行番号情報を反復処理するクライアントを許可する列挙体を取得します。|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|アクセラレータのスタブ関数の親に指定したタグの値に対応する変数のシンボルの列挙を返します。|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|対応するタグの値を指定するには、このメソッドは、指定された相対仮想アドレスでは、指定した親アクセラレータ スタブ関数に含まれている記号の列挙を返します。|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|指定されたインライン関数名に対応するインライン フレームにシンボルの列挙を返します。|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|指定したソースの場所への対応するインライン フレームにシンボルの列挙を返します。|  
  
## <a name="remarks"></a>コメント  
 呼び出すことが重要、 [idiasession::put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)メソッドを作成した後に、`IDiaSession`オブジェクト: とに渡された値、`put_loadAddress`メソッドは 0 以外である必要があります: するシンボルの仮想アドレス (VA) プロパティのアクセスできます。 読み込みアドレスどのようなプログラムは、デバッグされている実行可能ファイルを読み込んだに由来します。 たとえば、Win32 関数を呼び出すことができます`GetModuleInformation`ハンドルを指定して実行可能ファイルを実行可能ファイルの読み込みアドレスを取得します。  
  
## <a name="example"></a>例  
 この例は、取得する方法を示します、 `IDiaSession` DIA SDK の一般的な初期化の一部としてインターフェイスです。  
  
```C++  
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
  
## <a name="requirements"></a>必要条件  
 ヘッダー: Dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>参照  
 [インターフェイス (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [概要](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [Exe](../../debugger/debug-interface-access/exe.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idiadatasource::opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [Idiasymbol::findchildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [.Pdb ファイルの照会](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)