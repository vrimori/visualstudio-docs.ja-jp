---
title: FxCop アナライザーのインストール
ms.date: 08/03/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 7690d1c67797c3a13dc22364d93d8af686e4f90c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892052"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>FxCop アナライザーを Visual Studio をインストールします。

Microsoft と呼ばれるアナライザーのセットを作成する[Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)、静的コード分析、Roslyn アナライザーへの変換から最も重要な"FxCop"ルールを格納しています。 これらのアナライザーは、セキュリティ、パフォーマンス、およびその他の設計上の問題のコードを確認します。

これらの FxCop アナライザーを NuGet パッケージとして、または Visual Studio に VSIX 拡張機能としてインストールできます。 長所と短所をそれぞれの詳細については、次を参照してください。 [NuGet パッケージとします。VSIX 拡張機能](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension)します。

## <a name="to-install-fxcop-analyzers-as-a-nuget-package"></a>FxCop アナライザーを NuGet パッケージとしてインストールするには

1. [アナライザー パッケージ バージョンを決定](#fxcopanalyzers-package-versions)をインストールするには、Visual Studio のバージョンに基づいています。

2. いずれかを使用して、Visual Studio でパッケージをインストール、[パッケージ マネージャー コンソール](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)または[パッケージ マネージャー UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)します。

   > [!NOTE]
   > 各アナライザー パッケージ nuget.org のページに貼り付けるコマンドが表示されます、**パッケージ マネージャー コンソール**します。 テキストをクリップボードにコピーする便利なボタンもいます。
   >
   > ![パッケージ マネージャー コンソール コマンドを示す、NuGet.org のページ](media/nuget-package-manager-command.png)

   アナライザー アセンブリがインストールされているとに表示される**ソリューション エクスプ ローラー** **参照** > **アナライザー**します。

   ![ソリューション エクスプ ローラー ノード アナライザー](media/solution-explorer-analyzers-node.png)

### <a name="fxcopanalyzers-package-versions"></a>FxCopAnalyzers パッケージ バージョン

次のガイドラインを使用すると、Visual Studio のバージョンをインストールするのに FxCop アナライザー パッケージのバージョンを特定します。

| Visual Studio のバージョン | FxCop アナライザー パッケージ バージョン |
| - | - |
| Visual Studio 2017 バージョン 15.5 以降 | たとえば、2.6.2 https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.2 |
| Visual Studio 2017 バージョン 15.3 を 15.4 | たとえば、2.3.0-beta1 https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1 |
| Visual Studio 2017 バージョン 15.0 を 15.2 | たとえば、2.0.0-beta2 https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2 |
| Visual Studio 2015 update 2 と 3 | たとえば、バージョン 1.2.0-beta2 https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2 |
| Visual Studio 2015 更新プログラム 1 | 例については、バージョン 1.1.0、 https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1します。 |
| Visual Studio 2015 RTW | たとえば、バージョン 1.0.1、 https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1 |

## <a name="to-install-fxcop-analyzers-as-a-vsix"></a>VSIX として FxCop アナライザーをインストールするには

Visual Studio 2017 バージョン 15.5 以降にインストールすることができます、 [Microsoft コード分析 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017)拡張機能をすべてのマネージ プロジェクトの FxCop アナライザーが含まれています。

1. Visual Studio で、次のように選択します。**ツール** > **拡張機能と更新**します。

   **[拡張機能と更新プログラム]** ダイアログ ボックスが表示されます。

   > [!NOTE]
   > またはから直接、拡張機能をダウンロード[Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017)します。

1. 展開**オンライン**選択し、左側のウィンドウで**Visual Studio Marketplace**します。

1. 検索ボックスに「"コード分析"を探して、 **Microsoft コード分析 2017**拡張機能。

   ![Microsoft コード分析の拡張機能](media/extensions-and-updates-code-analysis.png)

1. 選択**ダウンロード**します。

   拡張機能をダウンロードします。

1. 選択**OK**に、ダイアログ ボックスを閉じ、起動する Visual Studio のすべてのインスタンスを閉じます、 **VSIX インストーラー**します。

   **VSIX インストーラー**  ダイアログ ボックスが表示されます。

   ![Microsoft コード分析のための VSIX インストーラー](media/vsix-installer-code-analysis.png)

1. 選択**変更**インストールを開始します。

1. しばらくすると、2 つのインストールを完了します。 選択**閉じる**します。

1. Visual Studio を再度開きます。

拡張機能がインストール済みになっているかどうかを確認したいかどうか**ツール** > **拡張機能と更新**します。 **拡張機能と更新**ダイアログ ボックスで、**インストール済み**左側のカテゴリ、名前で、拡張機能を検索します。

## <a name="see-also"></a>関連項目

- [Visual Studio で Roslyn アナライザーの概要](../code-quality/roslyn-analyzers-overview.md)
- [Visual Studio で Roslyn アナライザーを使用します。](../code-quality/use-roslyn-analyzers.md)
- [FxCop から Roslyn アナライザーへの移行します。](../code-quality/fxcop-analyzers.yml)