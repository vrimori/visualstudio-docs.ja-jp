---
title: Debug Interface Access SDK |Microsoft Docs
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
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7784cdbc265d487dd35f11a8bf50d38594e0cea6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49177061"
---
# <a name="debug-interface-access-sdk"></a>Debug Interface Access SDK
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Microsoft デバッグ インターフェイス アクセス ソフトウェア開発キット (DIA SDK) は、Microsoft ポスト コンパイラ ツールによって生成されたプログラム データベース (.pdb) ファイルに格納されている情報のデバッグへのアクセスを提供します。 ポスト コンパイラ ツールによって生成される .pdb ファイルの形式が定数のリビジョンを受けて、ために、形式を公開する実用的ではありません。 DIA API を使用すると、検索し、.pdb ファイルに格納されているデバッグ情報を参照するアプリケーションを開発できます。 このようなアプリケーションはスタック トレース バック情報を報告やパフォーマンス データを分析などのことができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [はじめに](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 機能 DIA SDK の概要が示され、および必須のヘッダーとライブラリ ファイル DIA SDK がインストールされているを指定します。  
  
 [.Pdb ファイルの照会](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 DIA API を使用して、.pdb ファイルを照会する方法について説明します。  
  
 [シンボルとシンボル タグ](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
 DIA API でシンボルとシンボル タグの使用方法について説明します。  
  
 [参照](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
 インターフェイス、メソッド、列挙型、および DIA API の構造が含まれています。  
  
 [Dia2dump サンプル](../../debugger/debug-interface-access/dia2dump-sample.md)  
 DIA API を使用して検索し、デバッグ情報を参照する方法を示しています。  
  
 [Dia2dump.cpp ソース ファイル](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 ソース コードで使用される[Dia2dump サンプル](../../debugger/debug-interface-access/dia2dump-sample.md)DIA API を示します。



