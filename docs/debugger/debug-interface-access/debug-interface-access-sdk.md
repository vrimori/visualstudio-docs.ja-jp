---
title: "Debug Interface Access SDK | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "デバッグ [DIA SDK]"
  - "デバッガー [DIA SDK]"
  - "DIA SDK"
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Debug Interface Access SDK
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Microsoft のデバッグ インターフェイスのアクセスのソフトウェア開発キット \(SDK\) DIA はMicrosoft postcompiler ツールで生成されたプログラム データベース \(.pdb\) ファイルに格納されている情報をデバッグするためのアクセスを提供します。  postcompiler のツールによって生成された .pdb ファイルの形式が設定されたリビジョンを行うため形式を公開することは現実的ではありません。  DIA API を使用して検索し.pdb ファイルに保存されているデバッグ情報を参照するアプリケーションを開発できます。  このようなアプリケーションはなどのバック スタック トレース情報を報告しパフォーマンス データを分析できます。  
  
## このセクションの内容  
 [作業の開始](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 DIA SDK がインストールされますが必須ヘッダーとライブラリ ファイルまたは DIA SDK の機能の概要を指定してください。  
  
 [.Pdb ファイルの照会](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 DIA API を .pdb ファイルを照会する方法について説明します。  
  
 [シンボルとシンボル タグ](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
 シンボルとシンボルのタグが DIA API でどのように使用されるかについて説明します。  
  
 [参照](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
 DIA API のインターフェイスメソッド列挙体および構造体が含まれています。  
  
 [Dia2dump サンプル](../../debugger/debug-interface-access/dia2dump-sample.md)  
 DIA API を検索しデバッグ情報を参照する方法について説明します。  
  
 [Dia2dump.cpp ソース ファイル](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 DIA API を示すために [Dia2dump サンプル](../../debugger/debug-interface-access/dia2dump-sample.md) で使用されるソース・コード。