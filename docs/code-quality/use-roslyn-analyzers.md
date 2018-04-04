---
title: Visual Studio で Roslyn アナライザーを構成して使用する |Microsoft ドキュメント
ms.date: 03/26/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 4f2929771d6aa50931a9e84dea8806d2fbe8db39
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2018
---
# <a name="configure-and-use-roslyn-analyzer-rules"></a>構成および Roslyn アナライザー ルールの使用

.NET コンパイラ プラットフォーム ("Roslyn") アナライザー ルール、または*診断*、入力すると、c# または Visual Basic コードを分析します。 各診断、既定の重要度および非表示の状態を持つ、プロジェクトを上書きします。 この記事では、設定ルールの重要度、規則セットを使用して、違反の抑制について説明します。

## <a name="analyzers-in-solution-explorer"></a>ソリューション エクスプ ローラーでアナライザー

アナライザー診断からのカスタマイズの大部分を行うことができます**ソリューション エクスプ ローラー**です。 場合する[インストール アナライザー](../code-quality/install-roslyn-analyzers.md) NuGet パッケージとして、**アナライザー**ノードが表示されます、**参照**または**の依存関係**内のノード**ソリューション エクスプ ローラー**です。 展開する場合**アナライザー**、アナライザー アセンブリのいずれかの順に展開し、アセンブリ内のすべての診断情報を参照してください。

![ソリューション エクスプ ローラーでアナライザー ノード](media/analyzers-expanded-in-solution-explorer.png)

説明と既定の重大度を含む、診断のプロパティを表示することができます、**プロパティ**ウィンドウです。 クリックし、ルールを右クリックし、プロパティを表示する**プロパティ**、またはルールを選択し、キーを押します**Alt**+**Enter**です。

![診断のプロパティの [プロパティ] ウィンドウ](media/analyzer-diagnostic-properties.png)

診断のヘルプを表示するには、診断を右クリックし、選択**ヘルプの表示**です。

各診断の横にあるアイコン**ソリューション エクスプ ローラー**規則セット エディターで開くと、表示アイコンに対応します。

- 円で囲まれた"i"を示す、[重大度](#rule-severity)の**情報**
- "!"三角形の中を示す、[重大度](#rule-severity)の**警告**
- 円の中の"x"、[重大度](#rule-severity)の**エラー**
- 明るい色の背景に円で囲んだ"i"を示す、[重大度](#rule-severity)の**非表示**
- 円の下向きの矢印は、診断が中止になっていることを示します

![ソリューション エクスプ ローラーでの診断アイコン](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-sets"></a>規則セット

A[ルール セット](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)個々 の診断の重要度および非表示の状態を格納する XML ファイルです。 ルール セットが 1 つのプロジェクトに適用され、プロジェクトは、複数の規則セットを持つことができます。 アクティブで、規則セット エディターを表示するを右クリックし、**アナライザー**内のノード**ソリューション エクスプ ローラー**選択と**開いているアクティブなルール セット**です。 この場合、初めてルールにアクセスする設定、という名前のファイル *\<projectname > .ruleset*がプロジェクトに追加されに表示されます**ソリューション エクスプ ローラー**です。

> [!NOTE]
> ルール セットには、静的 (バイナリ) コードの分析と Roslyn アナライザー ルールの両方が含まれます。

プロジェクトの [アクティブなルールを変更することができます、**コード分析**のプロジェクトのプロパティ] タブ。 規則セットを選択、**この規則セットを実行**ドロップダウン リスト。 規則のセットを開くことも、**コード分析**プロパティ ページを選択して**開く**です。

## <a name="rule-severity"></a>ルールの重要度

アナライザー ルールの重大度を構成することができますまたは*診断*場合は、する[インストール アナライザー](../code-quality/install-roslyn-analyzers.md) NuGet パッケージとして。 次の表は、診断の重要度のオプションを示しています。

|重要度|ビルド時の動作|エディターの動作|
|-|-|-|
|Error|として違反が表示される*エラー*で、**エラー一覧**コマンド ライン ビルド出力、および問題により、ビルドが失敗します。|問題のあるコードは赤色の波、およびスクロール バーの小さな赤いボックスによってマーク付きの下線が付きます。|
|警告|として違反が表示される*警告*で、**エラー一覧**とコマンド ライン ビルド出力が失敗するビルドが発生しません。|問題のあるコードが波、およびスクロール バーの小さな緑色のボックスでマークされている緑色の下線が付きます。|
|Info|として違反が表示される*メッセージ*で、**エラー一覧**、およびコマンド ライン ビルドの出力でまったくないです。|問題のあるコードが波、およびスクロール バーの小さな灰色のボックスでマークされているグレーの下線が付きます。|
|非表示|非表示をユーザーにします。|非表示をユーザーにします。 診断については、ただし、IDE の診断エンジンに報告されます。|
|なし|完全に抑制します。|完全に抑制します。|

さらに、「リセットできます」ルールの重要度を設定することによって**既定**です。 各診断が既定の重大度でわかるように、**プロパティ**ウィンドウです。

次のスクリーン ショットは、コード エディターで、次の 3 つの異なる重大度レベルの 3 つの異なる診断違反を示します。 波、だけでなく右にスクロール バーの小さなボックスの色に注意してください。

![コード エディターでのエラー、警告、および情報の違反](media/diagnostics-severity-colors.png)

次のスクリーン ショットに示すように同じ 3 つの違反を示しています、**エラー一覧**:

![エラー一覧 に、エラー、警告、および情報の違反](media/diagnostics-severities-in-error-list.png)

取得したルールの重大度を変更することができます**ソリューション エクスプ ローラー**、内、または、  *\<projectname > .ruleset* でルールの重大度を変更した後、ソリューションに追加されるファイル**ソリューション エクスプ ローラー**です。

![ソリューション エクスプ ローラーで Ruleset ファイル](media/ruleset-in-solution-explorer.png)

### <a name="to-set-rule-severity-from-solution-explorer"></a>ソリューション エクスプ ローラーからルールの重要度を設定するには

1. **ソリューション エクスプ ローラー**、展開**参照** > **アナライザー** (**の依存関係** >  **アナライザー** .NET Core プロジェクトに)。

1. 重要度を設定する規則を含むアセンブリを展開します。

1. 右クリックし、ルール**設定ルール セットの重要度**です。 ポップアップ メニューでは、重大度オプションのいずれかを選択します。

   ルールの重大度は、アクティブなルール セット ファイルに保存されます。

### <a name="to-set-rule-severity-in-the-rule-set-file"></a>ルールの重大度のファイルの設定ルールを設定するには

1. 開いている規則セット ファイル内をダブルクリックして**ソリューション エクスプ ローラー**を選択すると、**開いているアクティブなルール セット**の右クリック メニューを開き、**アナライザー**ノード、またはを選択して**開く**上、**コード分析**プロジェクトのプロパティ ページ。

1. 含んでいるアセンブリを展開して、ルールを参照します。

1. **アクション**列では、ドロップダウン リストを開く値を選択し、一覧から目的の重大度を選択します。

   ![ルールセット ファイルをエディターで開く](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>違反を抑制します。

さまざまな方法で規則違反を抑制します。

- 現在のすべての違反を抑制するのには、選択**分析** > **コード分析を実行し、アクティブな懸案事項の抑制**メニュー バーでします。 これは、「ベース ライニング」と呼ばれます。

- 診断を抑制する**ソリューション エクスプ ローラー**に、重大度を設定**None**です。

- 規則セット エディターから診断を抑制するには、その名前の横にあるボックスをオフに設定するか**アクション**に**None**です。

- コード エディターから診断を抑制するのには、違反とキーを押してコード行にカーソルを置きます**Ctrl**+**です。** 開くには、**クイック アクション**メニュー。 選択**CAxxxx を抑制する** > **ソース**または**CAxxxx を抑制する** > **抑制ファイルで**です。

   ![クイック アクション メニューから診断を抑制します。](media/suppress-diagnostic-from-editor.png)

- 診断を非表示にする、**エラー一覧**エラー、警告、またはメッセージを右クリックし、選択、**抑制** > **でソース**または**抑制** > **抑制ファイルで**です。

   - 選択した場合**でソース**、**変更のプレビュー**ダイアログが開き、c# のプレビューを表示[#pragma 警告](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning)または Visual Basic [#Disable warning](/dotnet/visual-basic/language-reference/directives/directives)ディレクティブをソース コードに追加されます。

      ![#Pragma 警告を追加するコード ファイル内のプレビュー](media/pragma-warning-preview.png)

   - 選択した場合**抑制ファイル内**、**変更のプレビュー**ダイアログが開きのプレビューを表示、<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>グローバル抑制ファイルに追加される属性です。

      ![SuppressMessage 属性抑制ファイルを追加のプレビュー](media/preview-changes-in-suppression-file.png)

   **変更のプレビュー**ダイアログで、**適用**です。

> [!NOTE]
> .NET Core プロジェクトに NuGet アナライザーを持っているプロジェクトへの参照を追加する場合、アナライザーに自動的に追加、依存プロジェクトすぎます。 たとえば、依存プロジェクトが単体テスト プロジェクトでは、この動作を無効にする NuGet パッケージでプライベートとしてマークが付け、 *.csproj*または*.vbproj*参照先のプロジェクトのファイル。
>
> ```xml
> <PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.6.0" PrivateAssets="all" />
> ```

## <a name="see-also"></a>関連項目

- [Visual Studio での Roslyn アナライザーの概要](../code-quality/roslyn-analyzers-overview.md)
- [Roslyn アナライザー バグを送信します。](https://github.com/dotnet/roslyn-analyzers/issues)
- [ルール セットを使用します](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [コード分析の警告を抑制します。](../code-quality/in-source-suppression-overview.md)