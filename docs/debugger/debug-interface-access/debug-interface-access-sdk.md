---
title: Debug Interface Access SDK |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ae5afe3b5eacaad31ae7b4fcd6aeb092aa37300c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="debug-interface-access-sdk"></a>Debug Interface Access SDK
Microsoft デバッグ インターフェイス アクセス ソフトウェア開発キット (DIA SDK) は、Microsoft ポスト コンパイラ ツールで生成されたプログラム データベース (.pdb) ファイルに格納されている情報のデバッグへのアクセスを提供します。 ポスト コンパイラ ツールによって生成される .pdb ファイルの形式では、定数のリビジョンが加えられた、ために、形式を公開する実用的ではありません。 DIA API を使用すると、.pdb ファイルに格納されているデバッグ情報の参照を検索しているアプリケーションを開発できます。 このようなアプリケーション、たとえば、スタック トレース バック情報を報告パフォーマンス データと分析します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [はじめに](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 DIA SDK の概要については、機能提供し、必要なヘッダーとライブラリ ファイルだけでなく、DIA SDK がインストールされているを指定します。  
  
 [.Pdb ファイルの照会](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 DIA API を使用して、.pdb ファイルを照会する方法について説明します。  
  
 [シンボルとシンボル タグ](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
 DIA API でのシンボルとシンボル タグの使用方法について説明します。  
  
 [参照](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
 インターフェイス、メソッド、列挙型、および DIA API の構造が含まれています。  
  
 [Dia2dump サンプル](../../debugger/debug-interface-access/dia2dump-sample.md)  
 DIA API を使用して検索し、デバッグ情報を参照する方法を示しています。  
  
 [Dia2dump.cpp ソース ファイル](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 ソース コードで使用される[Dia2dump サンプル](../../debugger/debug-interface-access/dia2dump-sample.md)DIA API を示します。