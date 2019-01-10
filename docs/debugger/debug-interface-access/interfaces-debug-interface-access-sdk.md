---
title: インターフェイス (Debug Interface Access SDK) |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 102d3456e1daf3c72f5f6c95c629ca2a42e7542f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53907710"
---
# <a name="interfaces-debug-interface-access-sdk"></a>インターフェイス (Debug Interface Access SDK)
メソッドは、下の目次や Vtable 順序でインターフェイスのページ テーブル内の各インターフェイスでアルファベット順に一覧表示されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)  
 DIA SDK がデバッグ オブジェクトの仮想および相対の仮想アドレスを計算する方法を制御できます。  
  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)  
 デバッグ シンボルのソースへのアクセスを開始します。  
  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)  
 デバッグのデータ ストリーム内のレコードへのアクセスを提供します。  
  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)  
 データ ソースに含まれるさまざまなデバッグ ストリームを列挙します。  
  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
 データ ソースに含まれるさまざまなフレーム データ要素を列挙します。  
  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
 データ ソースに含まれるさまざまな挿入されたソースを列挙します。  
  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
 データ ソースに含まれるさまざまな行番号を列挙します。  
  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
 データ ソースに含まれるさまざまなセクションの投稿を列挙します。  
  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
 データ ソースに格納されているさまざまなセグメントを列挙します。  
  
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
 スタック フレームの詳細が公開されます。  
  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)  
 モジュールまたはイメージのベースの位置とメモリのオフセットの詳細が公開されます。  
  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
 DIA のデータ ソースに格納されているプログラムのソース コードへのアクセス。  
  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
 イメージのテキストのバイトのブロックからソース ファイルの行番号へのマッピングのプロセスを説明する情報にアクセスします。  
  
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)  
 プロシージャの検索、したがって、ユーザー インターフェイスの場所の試行の進行状況の報告を有効にする DIA シンボルからのコールバックを受け取ります。  
  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)  
 DIA シンボル プロシージャを検索する特定のプロセスに適用される制限のことからには、コールバックを受信します。  
  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)  
 DIA プロパティ セットの永続的なプロパティを読み取ることができます。  
  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)  
 ファイルの位置によって指定された実行可能ファイルのバイト数を指定するクライアント アプリケーションを有効にします。  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)  
 相対仮想アドレスで指定された実行可能ファイルのバイト数を指定するクライアント アプリケーションを有効にします。  
  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
 セクションの投稿を記述するデータを取得、つまり、連続メモリ ブロックに起因イメージに、コンパイル単位。  
  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
 セクション数からアドレス空間のセグメントにデータをマップします。  
  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)  
 デバッグ シンボルのクエリ コンテキストを提供します。  
  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
 ソース ファイルを表します。  
  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)  
 スタック フレームのプロパティを公開します。  
  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)  
 スタックの操作を行う方法は、PDB ファイルを使用する方法について説明します。 を提供します。  
  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)  
 呼び出しの間のスタック コンテキストを維持、 [idiaframedata::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)メソッド。  
  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)  
 プログラム デバッグ データベース (PDB) ファイルを使用して、スタック ウォークが容易になります。  
  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
 シンボルのインスタンスのプロパティについて説明します。  
  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)  
 DIA データ ソースのテーブルを列挙します。  
  
## <a name="related-sections"></a>関連項目  
 [列挙型と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)  
 DIA SDK のさまざまなインターフェイスで使用される構造体、列挙体について説明します。  
  
 [定数 (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)  
 DIA SDK で使用できる定数をについて説明します。  
  
## <a name="see-also"></a>「  
 [参照](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)