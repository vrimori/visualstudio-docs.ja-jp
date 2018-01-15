---
title: "DslTextTransform コマンド |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, commands
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 47b64bf5049baf981cbf85ec5bfeba4f5f796636
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform コマンド
DslTextTransform.cmd は、TextTransform.exe を呼び出すし、一般的なオプションで実行されるスクリプトに示します。 DslTextTransformation.cmd を使用して、夜間のビルドを自動化することができます、[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]プロジェクト。 詳細については、次を参照してください。 [TextTransform ユーティリティを使ってファイルを生成する](../modeling/generating-files-with-the-texttransform-utility.md)です。  
  
 DslTextTransform.cmd は、次のディレクトリにあります。  
  
 **\<Visual Studio SDK インストール パス > \VisualStudioIntegration\Tools\Bin**  
  
 DslTextTransform.cmd への入力として、次の引数を指定できます。  
  
-   ドメイン モデル プロジェクトの出力ディレクトリです。  
  
-   デザイナー定義がプロジェクトの出力ディレクトリです。  
  
-   テキスト テンプレート ファイルの場所です。  
  
 DslTextTransform.cmd は、既定のディレクティブ プロセッサとアセンブリを使用して指定されたテキスト テンプレート ファイルを処理します。 カスタム ディレクティブ プロセッサを作成する場合は、TextTransform.exe を呼び出す独自のバッチ ファイルを作成できます。 このバッチ ファイルで、アセンブリと関連付けられているカスタム ディレクティブ プロセッサを指定することができます。