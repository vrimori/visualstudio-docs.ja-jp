---
title: DslTextTransform コマンド
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
ms.openlocfilehash: a3605dd3d6cd7615a2afd4dba18bf2f7bed994f4
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2018
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