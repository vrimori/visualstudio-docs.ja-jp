---
title: DslTextTransform コマンド |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 8a565fa6226348a1fe1b6dcfcbb67f704e74abc8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540339"
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform コマンド
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[、DslTextTransform コマンド](https://docs.microsoft.com/visualstudio/modeling/the-dsltexttransform-command)します。  
  
DslTextTransform.cmd、TextTransform.exe を呼び出すし、一般的なオプションを使用して実行するスクリプトです。 DslTextTransformation.cmd を使用して、夜間のビルドを自動化することができます、[!INCLUDE[dsl](../includes/dsl-md.md)]プロジェクト。 詳細については、次を参照してください。 [TextTransform ユーティリティを使ってファイルを生成する](../modeling/generating-files-with-the-texttransform-utility.md)します。  
  
 DslTextTransform.cmd については、次のディレクトリにあります。  
  
 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**  
  
 DslTextTransform.cmd への入力として、次の引数を指定できます。  
  
-   ドメイン モデル プロジェクトの出力ディレクトリ。  
  
-   デザイナー定義プロジェクトの出力ディレクトリ。  
  
-   テキスト テンプレート ファイルの場所。  
  
 DslTextTransform.cmd では、既定のディレクティブ プロセッサとアセンブリを使用して、指定したテキスト テンプレート ファイルを処理します。 カスタム ディレクティブ プロセッサを作成する場合は、独自 TextTransform.exe を呼び出すバッチ ファイルを作成できます。 このバッチ ファイルでは、アセンブリと関連付けられているカスタム ディレクティブ プロセッサを指定できます。



