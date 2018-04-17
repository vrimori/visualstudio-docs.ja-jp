---
title: インターフェイス (Debug Interface Access SDK) |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interfaces [DIA SDK]
- DIA SDK, interfaces
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09f1d0496595f3026c7066f4ccfdeb7bc3add6d0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="interfaces-debug-interface-access-sdk"></a>インターフェイス (Debug Interface Access SDK)
Vtable 順序のインターフェイスのページの内容のテーブル内の各インターフェイスでメソッドをアルファベット順に一覧表示されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)  
 DIA SDK が仮想のアドレスと相対仮想アドレス デバッグ オブジェクトを計算する方法の制御を提供します。  
  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)  
 デバッグ シンボルのソースへのアクセスを開始します。  
  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)  
 デバッグ データ ストリーム内のレコードへのアクセスを提供します。  
  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)  
 データ ソースに含まれるさまざまなデバッグ ストリームを列挙します。  
  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
 データ ソースに含まれるさまざまなフレーム データ要素を列挙します。  
  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
 データ ソースに含まれるさまざまな挿入されたソースを列挙します。  
  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
 データ ソースに含まれるさまざまな行番号を列挙します。  
  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
 データ ソースに含まれるさまざまなセクション貢献度を列挙します。  
  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
 データ ソースに含まれるさまざまなセグメントを列挙します。  
  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
 データ ソースに含まれるさまざまなソース ファイルを列挙します。  
  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)  
 使用可能なさまざまなスタック フレームを列挙します。  
  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
 データ ソースに含まれるさまざまなシンボルを列挙します。  
  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)  
 アドレスを指定して、データ ソースに含まれるさまざまなシンボルを列挙します。  
  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)  
 データ ソースに含まれるさまざまなテーブルを列挙します。  
  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
 スタック フレームの詳細を公開します。  
  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)  
 モジュールまたはイメージの基本場所とメモリのオフセットの詳細情報を公開します。  
  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
 アクセス プログラムのソース コードは、DIA データ ソースに格納されます。  
  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
 イメージのテキストのバイトのブロックからソース ファイルの行番号へのマッピングのプロセスを説明する情報にアクセスします。  
  
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)  
 プロシージャを検索する、つまり、ユーザー インターフェイスの場所の試行の進行状況の報告を有効にする DIA シンボルからのコールバックを受信します。  
  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)  
 プロシージャを検索する検索のプロセスに適用される制限をできるように、DIA シンボルからのコールバックを受信します。  
  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)  
 DIA プロパティ セットの永続的なプロパティを読み取ることができます。  
  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)  
 ファイルの位置によって指定された実行可能ファイルのバイト数を指定するクライアント アプリケーションを有効にします。  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)  
 相対仮想アドレスで指定された実行可能ファイルのバイト数を指定するクライアント アプリケーションを有効にします。  
  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
 セクション貢献度を記述するデータを取得、つまり、連続するメモリ ブロックから提供されたイメージに、コンパイル単位です。  
  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
 アドレス空間のセグメント セクション番号からデータをマップします。  
  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)  
 デバッグ シンボルをクエリのコンテキストを提供します。  
  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
 ソース ファイルを表します。  
  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)  
 スタック フレームのプロパティを公開します。  
  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)  
 PDB ファイルを使用して、スタックを行う方法の説明を提供します。  
  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)  
 呼び出しの間でのスタック コンテキストを維持、 [idiaframedata::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)メソッドです。  
  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)  
 プログラム デバッグ データベース (PDB) ファイルを使用して、スタック ウォークが容易になります。  
  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
 シンボルのインスタンスのプロパティについて説明します。  
  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)  
 DIA データ ソースのテーブルを列挙します。  
  
## <a name="related-sections"></a>関連項目  
 [列挙型と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)  
 DIA SDK のさまざまなインターフェイスで使用する構造体、列挙体について説明します。  
  
 [定数 (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)  
 DIA SDK で使用できる定数をについて説明します。  
  
## <a name="see-also"></a>関連項目  
 [参照](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)