---
title: "列挙子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ソース管理プラグインを列挙子"
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# 列挙子
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このセクションでは、ソース管理プラグインがについて知る必要があるソース コントロールのプラグイン API で列挙子のデータ型を示します。  
  
## このセクションの内容  
 [コマンドのコード](../extensibility/command-code-enumerator.md)  
 オプションを列挙、 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) と [SccPopulateList](../extensibility/sccpopulatelist-function.md) 関数です。  
  
 [メッセージ](../extensibility/message-enumerator.md)  
 印刷のコールバックを使用するフラグを列挙 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)します。  
  
 [ファイルの状態コード](../extensibility/file-status-code-enumerator.md)  
 ソース管理下にあるファイルの状態を指定する名前付き定数の値が含まれています。  
  
 [ディレクトリの状態コード](../extensibility/directory-status-code-enumerator.md)  
 ソース管理下にディレクトリの状態を指定する名前付き定数の値が含まれています。  
  
## 関連項目  
 [ソース管理プラグインの作成](../extensibility/internals/creating-a-source-control-plug-in.md)  
 ソース管理プラグインの SDK を定義して、含まれているリソースを記述します。  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 指定されたコマンドの詳細設定オプションのユーザーに求めます。  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 現在の状態のファイルの一覧を調べます。 さらに、使用、 `pfnPopulate` ファイルに使用される条件に一致しない場合、呼び出し元に通知するため、 `nCommand`です。  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 によって使用されているコールバック関数を記述 [SccOpenProject](../extensibility/sccopenproject-function.md) IDE によってプラグインのソース管理からのメッセージを表示します。  
  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)  
 ソース コントロールのプラグイン API 内のすべての要素の完全な一覧を提供します。