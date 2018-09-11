---
title: クエリを実行します。Pdb ファイル |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a13f98e9d1507c0044057099d61b625e1142929e
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44282054"
---
# <a name="querying-the-pdb-file"></a>.Pdb ファイルの照会
プログラム データベース ファイル (拡張子 .pdb) とは、型とコンパイルとリンク、プロジェクトの過程で収集された、シンボリック デバッグ情報を含むバイナリ ファイルです。 C/C++ プログラムをコンパイルするときに、PDB ファイルが作成された **/ZI**または **/Zi**または[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]、 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]、または[!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)]を使ってプログラム、 **/debug**オプション。 オブジェクト ファイルには、デバッグ情報の .pdb ファイルへの参照が含まれます。 Pdb ファイルの詳細については、次を参照してください。 [PDB ファイル](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yd4f8bd1(v=vs.100))します。 DIA アプリケーションでは、次の一般的な手順を使用して、詳細については、さまざまなシンボル、オブジェクト、および実行可能イメージ内のデータ要素を取得します。  
  
### <a name="to-query-the-pdb-file"></a>.Pdb ファイルを照会するには  
  
1.  作成してデータ ソースを取得、 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)インターフェイス。  
  
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
  
3.  呼び出す[idiadatasource::opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)を開く、 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)デバッグ情報にアクセスします。  
  
    ```C++  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4.  メソッドを使用`IDiaSession`データ ソース内のシンボルを照会します。  
  
    ```C++  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5.  使用して、`IDiaEnum*`デバッグ情報を列挙し、記号やの他の要素をスキャンするインターフェイス。  
  
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