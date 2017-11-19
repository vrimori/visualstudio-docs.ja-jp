---
title: "列挙子 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0b9f71c83d70dc6daca7a3906b784d6babf8dea7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="enumerators"></a>列挙子
このセクションでは、ソース管理プラグインはについて知る必要がありますソース管理プラグイン API で列挙子のデータ型を示します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [コマンドのコード](../extensibility/command-code-enumerator.md)  
 オプションを列挙、 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)と[SccPopulateList](../extensibility/sccpopulatelist-function.md)関数。  
  
 [メッセージ](../extensibility/message-enumerator.md)  
 印刷のコールバックの使用フラグを列挙[LPTEXTOUTPROC](../extensibility/lptextoutproc.md)です。  
  
 [ファイルの状態コード](../extensibility/file-status-code-enumerator.md)  
 ソース管理下にあるファイルの状態を指定する名前付き定数値が含まれています。  
  
 [ディレクトリの状態コード](../extensibility/directory-status-code-enumerator.md)  
 ソース管理下にあるディレクトリの状態を指定する名前付き定数値が含まれています。  
  
## <a name="related-sections"></a>関連項目  
 [ソース管理プラグインの作成](../extensibility/internals/creating-a-source-control-plug-in.md)  
 ソース管理プラグイン SDK を定義して、含まれているリソースを記述します。  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 指定したコマンドの詳細設定オプションのユーザーに求めます。  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 現在の状態のファイルの一覧を調べます。 さらに、使用、`pfnPopulate`ファイルに使用される条件に一致しない場合、呼び出し元に通知する関数、`nCommand`です。  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 によって使用されているコールバック関数の説明[SccOpenProject](../extensibility/sccopenproject-function.md) IDE を介してプラグイン ソース管理からメッセージを表示します。  
  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)  
 ソース管理プラグイン API 内のすべての要素の完全な一覧を提供します。