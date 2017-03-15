---
title: "IDiaSession | Microsoft Docs"
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
  - "IDiaSession インターフェイス"
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# IDiaSession
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

デバッグ シンボルのクエリ コンテキストを提供します。  
  
## 構文  
  
```  
IDiaSession : IUnknown  
```  
  
## メソッド  
 `IDiaSession` のメソッドを次の表に示します。  
  
|メソッド|説明|  
|----------|--------|  
|[IDiaSession::get\_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|このシンボル ストア内のシンボルに対応する実行可能ファイルの読み込みアドレスを取得します。  これは、`put_loadAddress` メソッドに渡された値と同じ値です。|  
|[IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|このシンボル ストア内のシンボルに対応する実行可能ファイルの読み込みアドレスを設定します。 **Note:**  `IDiaSession` オブジェクトを取得して、オブジェクトを使い始める前に、このメソッドを呼び出すことが重要です。|  
|[IDiaSession::get\_globalScope](../Topic/IDiaSession::get_globalScope.md)|グローバル スコープへの参照を取得します。|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|シンボル ストアに格納されているすべてのテーブルの列挙子を取得します。|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|静的な場所にあるすべての名前付きシンボルの列挙子を取得します。|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|名前およびシンボル型と一致する、指定された親識別子のすべての子を取得します。|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|指定されたアドレスを含むか、または最も近くにある、指定されたシンボル型を取得します。|  
|[IDiaSession::findSymbolByRVA](../Topic/IDiaSession::findSymbolByRVA.md)|指定された相対仮想アドレス \(RVA\) を含むか、または最も近くにある、指定されたシンボル型を取得します。|  
|[IDiaSession::findSymbolByVA](../Topic/IDiaSession::findSymbolByVA.md)|指定された仮想アドレス \(VA\) を含むか、または最も近くにある、指定されたシンボル型を取得します。|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|指定されたメタデータ トークンを含むシンボルを取得します。|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|2 個のシンボルが同等かどうかをチェックします。|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|一意の識別子によってシンボルを取得します。|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|指定された相対仮想アドレスおよびオフセットを含むか、または最も近くにある、指定されたシンボル型を取得します。|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|指定された仮想アドレスおよびオフセットを含むか、または最も近くにある、指定されたシンボル型を取得します。|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|コンパイル単位と名前でソース ファイルを取得します。|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|ソース ファイル識別子でソース ファイルを取得します。|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|指定されたコンパイル単位およびソース ファイル識別子内にある行番号を取得します。|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|指定されたアドレスを含む、指定されたコンパイル単位内にある行を取得します。|  
|[IDiaSession::findLinesByRVA](../Topic/IDiaSession::findLinesByRVA.md)|指定された相対仮想アドレスを含む、指定されたコンパイル単位内にある行を取得します。|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|指定されたアドレス範囲に含まれる行の行番号情報を検索します。|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|ソース ファイルおよび行番号で指定されたコンパイル単位内にある行を取得します。|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|コンパイル プロセスの属性プロバイダーまたはその他のコンポーネントによってシンボル ストアに配置されたソースを取得します。|  
|[IDiaSession::getEnumDebugStreams](../Topic/IDiaSession::getEnumDebugStreams.md)|デバッグ データ ストリームの列挙シーケンスを取得します。|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|クライアントが特定のアドレスのインライン フレームすべての反復処理できる列挙型を取得します。|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|クライアントが指定した相対仮想アドレス \(RVA\) のインライン フレームすべての反復処理できる列挙型を取得します。|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|クライアントが指定された仮想アドレス \(VA\) のインライン フレームすべての反復処理できる列挙型を取得します。|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|クライアントが、指定した親シンボルによって、直接または間接的にインライン関数のすべての行番号情報によって、反復処理できる列挙型を取得します。|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|クライアントが、指定した親シンボルによって、直接または間接的に、インライン展開され、指定したアドレスの範囲に含まれるすべての関数の行番号情報を反復処理できる列挙型を取得します。|  
|[IDiaSession::findInlineeLinesByRVA](../Topic/IDiaSession::findInlineeLinesByRVA.md)|クライアントが、指定した親シンボルによって、直接または間接的に、インライン展開され、指定した相対仮想アドレス \(RVA\) に含まれるすべての関数の行番号情報を反復処理できる列挙型を取得します。|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|クライアントが、指定した親シンボルによって、直接または間接的に、インライン展開され、指定された仮想アドレス \(VA\) に含まれるすべての関数の行番号情報を反復処理できる列挙型を取得します。|  
|[IDiaSession::findInlineeLinesByLinenum](../Topic/IDiaSession::findInlineeLinesByLinenum.md)|クライアントが指定したソース ファイルと行番号で、直接または間接的に、インライン関数のすべての行番号情報を反復処理できる列挙型を取得します。|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|クライアントが、指定した名前に一致するすべてのインライン関数の行番号情報を反復処理できる列挙型を取得します。|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|親アクセラレータのスタブ関数でに指定したタグの値は対応する変数のシンボルの列挙体を返します。|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|対応するタグの値の場合、このメソッドは、指定した相対仮想アドレスの指定した親のアクセラレータのスタブの関数に含まれるシンボルの列挙体を返します。|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|指定したインライン関数の名前に対応するインライン フレームのシンボルの列挙体を返します。|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|指定されたソースの場所に対応するインライン フレームのシンボルの列挙体を返します。|  
  
## 解説  
 `IDiaSession` オブジェクトを作成した後に `put_loadAddress` メソッドを呼び出すことが重要です。そして、シンボルの仮想アドレス \(VA\) プロパティにアクセスできるように、[IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) メソッドに渡した値はゼロ以外である必要があります。  読み込みアドレスは、デバッグ対象の実行可能ファイルを読み込みんだプログラムから取得されます。  たとえば、実行可能ファイルへのハンドルを指定して、実行可能ファイルの読み込みアドレスを取得するには、Win32 関数 `GetModuleInformation` を呼び出します。  
  
## 使用例  
 この例は、DIA SDK の一般的な初期化の一部として `IDiaSession` インターフェイスを取得する方法を示しています。  
  
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
  
## 必要条件  
 ヘッダー: Dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia80.dll  
  
## 参照  
 [インターフェイス \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [概要](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [Exe](../../debugger/debug-interface-access/exe.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [.Pdb ファイルの照会](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)