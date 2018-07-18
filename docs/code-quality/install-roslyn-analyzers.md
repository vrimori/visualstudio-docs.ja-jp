---
title: Visual Studio での Roslyn アナライザーをインストールします。
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: fb2f681de16a53c97954c8c37b8dd28b163998ee
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31927534"
---
# <a name="install-net-compiler-platform-analyzers"></a>.NET コンパイラ プラットフォーム アナライザーをインストールします。

Visual Studio 2017 には .NET コンパイラ プラットフォームのコア セットが含まれています (*Roslyn*) アナライザーです。 これらのアナライザーは常にオンです。 追加のアナライザーをインストールするには、NuGet パッケージとして、または Visual Studio の拡張機能として*VSIX*ファイル。

## <a name="to-install-nuget-package-analyzers"></a>NuGet パッケージ アナライザーをインストールするには

1. [アナライザー パッケージ バージョンが判断](https://github.com/dotnet/roslyn-analyzers#recommended-version-of-analyzer-packages)をインストールするには、Visual Studio のバージョンに基づいています。

1. いずれかを使用して、Visual Studio でパッケージをインストール、 [Package Manager Console](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)または[パッケージ マネージャー UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)です。

   > [!NOTE]
   > アナライザーの各パッケージの nuget.org ページに、コマンドに貼り付けるには表示、 **Package Manager Console**です。 テキストをクリップボードにコピーするための便利なボタンはであってもです。
   >
   > ![パッケージ マネージャー コンソール コマンドを表示する NuGet.org ページ](media/nuget-package-manager-command.png)

   アナライザー アセンブリがインストールされに表示される**ソリューション エクスプ ローラー** **参照** > **アナライザー**です。

   ![ソリューション エクスプ ローラーでアナライザー ノード](media/solution-explorer-analyzers-node.png)

## <a name="to-install-vsix-analyzers"></a>アナライザーの VSIX をインストールするには

1. Visual Studio で、次のように選択します。**ツール** > **拡張機能と更新プログラム**です。

   **[拡張機能と更新プログラム]** ダイアログ ボックスが表示されます。

   > [!NOTE]
   > また、ダウンロードから直接、拡張機能[Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017)です。

1. 展開**オンライン**クリックし、左側のウィンドウで**Visual Studio Marketplace**です。

1. [検索] ボックスに「コード分析」を入力し、検索、 **Microsoft コード分析 2017**拡張機能です。

   ![Microsoft コード分析の拡張機能](media/extensions-and-updates-code-analysis.png)

1. 選択**ダウンロード**です。

   拡張機能をダウンロードします。

1. 選択 **[ok]** にダイアログ ボックスを閉じを起動する Visual Studio のすべてのインスタンスを閉じて、 **VSIX インストーラー**です。

   **VSIX インストーラー**  ダイアログ ボックスが表示されます。

   ![Microsoft コード分析のための VSIX インストーラー](media/vsix-installer-code-analysis.png)

1. 選択**変更**インストールを開始します。

1. 1 分または 2 つの場合は、インストールが完了するとします。 選択**閉じる**です。

1. Visual Studio をもう一度開きます。

拡張機能がインストールされている、選択するかどうかを確認するかどうかは**ツール** > **拡張機能と更新プログラム**です。 **拡張機能と更新**ダイアログ ボックスで、**インストール**左側のカテゴリ名を指定して、拡張機能の検索とします。

## <a name="next-steps"></a>次の手順

- [Visual Studio での Roslyn アナライザーを使用します。](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>関連項目

- [Visual Studio での Roslyn アナライザーの概要](../code-quality/roslyn-analyzers-overview.md)