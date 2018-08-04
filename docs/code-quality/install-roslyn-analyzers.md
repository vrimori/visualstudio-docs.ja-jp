---
title: Roslyn アナライザーをインストールします。
ms.date: 08/03/2018
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
ms.openlocfilehash: 5977275b352bf11914760d9cdf7ccada22caccc8
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512032"
---
# <a name="install-net-compiler-platform-analyzers"></a>.NET コンパイラ プラットフォームのアナライザーをインストールします。

Visual Studio 2017 には、.NET コンパイラ プラットフォームのコア セットが含まれています (*Roslyn*) アナライザーです。 これらのアナライザーが常に動作します。 その他のアナライザーをインストールするには、NuGet パッケージの場合、または Visual Studio の拡張機能として*VSIX*ファイル。

## <a name="to-install-nuget-analyzer-packages"></a>NuGet アナライザー パッケージをインストールするには

1. Www.nuget.org をインストールするアナライザー パッケージを検索します。たとえば、したい場合があります[Microsoft FxCop アナライザーをインストール](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package)コードの他のユーザーの間でのセキュリティとパフォーマンスの問題を確認します。

1. いずれかを使用して、Visual Studio でパッケージをインストール、[パッケージ マネージャー コンソール](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)または[パッケージ マネージャー UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)します。

   > [!NOTE]
   > 各アナライザー パッケージ www.nuget.org ページに貼り付けるコマンドが表示されます、**パッケージ マネージャー コンソール**します。 テキストをクリップボードにコピーする便利なボタンもいます。
   >
   > ![パッケージ マネージャー コンソール コマンドを示す、NuGet.org のページ](media/nuget-install-command.png)

   アナライザー アセンブリがインストールされに表示**ソリューション エクスプ ローラー** **参照** > **アナライザー**します。

## <a name="to-install-vsix-analyzers"></a>VSIX のアナライザーをインストールするには

1. Visual Studio で、次のように選択します。**ツール** > **拡張機能と更新**します。

   **[拡張機能と更新プログラム]** ダイアログ ボックスが表示されます。

   > [!NOTE]
   > または、検索し、アナライザー拡張機能から直接ダウンロード[Visual Studio Marketplace](https://marketplace.visualstudio.com)します。

1. 展開**オンライン**選択し、左側のウィンドウで**Visual Studio Marketplace**します。

1. 検索ボックスで、インストールするアナライザーの拡張機能の名前を入力します。 たとえば、したい場合があります[Microsoft FxCop アナライザーをインストール](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix)コードの他のユーザーの間でのセキュリティとパフォーマンスの問題を確認します。

1. 選択**ダウンロード**します。

   拡張機能をダウンロードします。

1. 選択**OK**に、ダイアログ ボックスを閉じ、起動する Visual Studio のすべてのインスタンスを閉じます、 **VSIX インストーラー**します。

   **VSIX インストーラー**  ダイアログ ボックスが表示されます。

   ![Microsoft コード分析のための VSIX インストーラー](media/vsix-installer-code-analysis.png)

1. 選択**変更**インストールを開始します。

1. しばらくすると、2 つのインストールを完了します。 選択**閉じる**します。

1. Visual Studio を再度開きます。

拡張機能がインストール済みになっているかどうかを確認したいかどうか**ツール** > **拡張機能と更新**します。 **拡張機能と更新**ダイアログ ボックスで、**インストール済み**左側のカテゴリ、名前で、拡張機能を検索します。

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [Visual Studio で Roslyn アナライザーを使用します。](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>関連項目

- [Visual Studio で Roslyn アナライザーの概要](../code-quality/roslyn-analyzers-overview.md)
- [FxCop アナライザーをインストールします。](../code-quality/install-fxcop-analyzers.md)