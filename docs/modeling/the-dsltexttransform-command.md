---
title: DslTextTransform コマンド |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 11fb12f3716fe9f8b5fee13a7eecd88ee107ff45
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform コマンド
DslTextTransform.cmd は、TextTransform.exe を呼び出すし、一般的なオプションで実行されるスクリプトに示します。 DslTextTransformation.cmd を使用して、夜間のビルドを自動化することができます、[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]プロジェクト。 詳細については、次を参照してください。 [TextTransform ユーティリティを使ってファイルを生成する](../modeling/generating-files-with-the-texttransform-utility.md)です。  
  
 DslTextTransform.cmd は、次のディレクトリにあります。  
  
 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**  
  
 DslTextTransform.cmd への入力として、次の引数を指定できます。  
  
-   ドメイン モデル プロジェクトの出力ディレクトリです。  
  
-   デザイナー定義がプロジェクトの出力ディレクトリです。  
  
-   テキスト テンプレート ファイルの場所です。  
  
 DslTextTransform.cmd は、既定のディレクティブ プロセッサとアセンブリを使用して指定されたテキスト テンプレート ファイルを処理します。 カスタム ディレクティブ プロセッサを作成する場合は、TextTransform.exe を呼び出す独自のバッチ ファイルを作成できます。 このバッチ ファイルで、アセンブリと関連付けられているカスタム ディレクティブ プロセッサを指定することができます。