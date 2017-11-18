---
title: "クエリを実行します。Pdb ファイル |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f329d285ec0f9014335b883e0206a426a9aab8e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="querying-the-pdb-file"></a>.Pdb ファイルの照会
プログラム データベース ファイル (拡張子 .pdb) とは、型とコンパイルとリンク、プロジェクトの過程で収集されたシンボリック デバッグ情報を含むバイナリ ファイルです。 C と C++ プログラムをコンパイルするときに PDB ファイルが作成された**/ZI**または**/Zi**または[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]、 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]、または[!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)]使用したプログラミング、 **/debug**オプション。 オブジェクト ファイルには、デバッグ情報の .pdb ファイルへの参照が含まれます。 Pdb ファイルの詳細については、次を参照してください。 [PDB ファイル](http://msdn.microsoft.com/en-us/1761c84e-8c2c-4632-9649-b5f99964ed3f)です。 DIA アプリケーションは、さまざまなシンボル、オブジェクト、および実行可能イメージ内のデータ要素の詳細を取得するのに、次の手順を使用できます。  
  
### <a name="to-query-the-pdb-file"></a>.Pdb ファイルを照会するには  
  
1.  作成することでデータ ソースを取得、 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)インターフェイスです。  
  
    ```C++  
    CComPtr<IDiaDataSource> pSource;  
    hr = CoCreateInstance( CLSID_DiaSource,  
                           NULL,  
                           CLSCTX_INPROC_SERVER,  
                           __uuidof( IDiaDataSource ),  
                          (void **) &pSource);  
  
    if (FAILED(hr))  
    {  
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );  
    }  
    ```  
  
2.  呼び出す[idiadatasource::loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)または[idiadatasource::loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)デバッグ情報を読み込めません。  
  
    ```C++  
    wchar_t wszFilename[ _MAX_PATH ];  
    mbstowcs( wszFilename, szFilename, sizeof( wszFilename )/sizeof( wszFilename[0] ) );  
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )  
    {  
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )  
        {  
            Fatal( "loadDataFromPdb/Exe" );  
        }  
    }  
    ```  
  
3.  呼び出す[idiadatasource::opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)を開くには、 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)デバッグ情報にアクセスするためにします。  
  
    ```C++  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4.  内のメソッドを使用して`IDiaSession`データ ソース内のシンボルを照会します。  
  
    ```C++  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5.  使用して、`IDiaEnum*`デバッグ情報を列挙し、シンボル、またはその他の要素をスキャンするインターフェイスです。  
  
    ```C++  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    CComPtr< IDiaTable > pTable;  
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) ) && celt == 1 )  
    {  
         // Do something with each IDiaTable.  
    }  
    ```  
  
## <a name="see-also"></a>関連項目  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)