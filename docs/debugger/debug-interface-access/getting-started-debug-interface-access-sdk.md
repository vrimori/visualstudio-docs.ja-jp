---
title: "はじめに (Debug Interface Access SDK) | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
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
  - ".dbg ファイル"
  - "DBG ファイル"
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# はじめに (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Debug Interface Access SDK ドキュメントは \(DIA\) 説明と DIA API を使用する方法を示すサンプルが含まれています。  .pdb および .dbg ファイルを開きシンボル値属性アドレスなどのデバッグ情報がコンテンツを検索するカスタム アプリケーションの開発に DIA SDK のインターフェイスとメソッドを使用します。  この SDK はC\+\+ アプリケーションにあるシンボルに関連付けられたプロパティの参照一覧を示します。  
  
 最適な使用法に DIA SDK次を理解している必要があります :  
  
-   C\+\+ プログラミング言語  
  
-   COM プログラミング  
  
-   サンプルをコンパイル \(IDE\) するための Visual Studio 統合開発環境  
  
 DIA SDK にはVisual Studio に通常インストール既定では *ドライブ \[入力\]*\\ Program Files \\ Microsoft Visual Studio 9.0 SDK \\ DIA です。  インストールの一部としてDIA SDK を実行する msdia90.dll は自動的にはすべて使用するする必要がある登録されます `diaguids.lib` にプログラムおよびリンクに `dia2.h` を含めることです。  
  
 ヘッダー : INCLUDE \\ dia2.h  
  
 ライブラリ : Lib \\ diaguids.lib  
  
 DLL: bin \\ msdia80.dll  
  
 IDL: idl \\ dia2.idl  
  
## このセクションの内容  
 [概要](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 DIA. の基本アーキテクチャを確認します。  
  
 [.Pdb ファイルの照会](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 DIA API を .pdb ファイルを照会する方法を手順に沿って説明します。  
  
## 参照  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)