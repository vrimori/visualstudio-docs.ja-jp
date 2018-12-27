---
title: IDE またはコマンドラインからのコード メトリックスを生成します。
ms.date: 11/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 83ec85855e17f8798f55b01f043d47d7140278e7
ms.sourcegitcommit: c7b16358a5d6f7ea1dd2f70a6ac2a8266efa9c15
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2018
ms.locfileid: "53425774"
---
# <a name="how-to-generate-code-metrics-data"></a>方法: コード メトリックス データを生成します。

1 つまたは複数のプロジェクトまたはソリューション全体のコード メトリックスの結果を生成することができます。 コード メトリックスは Visual Studio の対話型開発環境 (IDE) 内であり、さらに利用可能なC#およびコマンドラインでの Visual Basic プロジェクト。

さらに、インストール、 [NuGet パッケージ](https://dotnet.myget.org/feed/roslyn-analyzers/package/nuget/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.2-beta2-63202-01)4 つのコード メトリックスを含む[アナライザー](roslyn-analyzers-overview.md)規則。CA1501、CA1502、CA1505、および CA1506 します。 既定では、これらの規則が無効になっていますが、それらから有効にすることができます**ソリューション エクスプ ローラー**または、[ルール セット](using-rule-sets-to-group-code-analysis-rules.md)ファイル。

## <a name="visual-studio-ide-code-metrics"></a>Visual Studio IDE のコード メトリックス

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>ソリューション全体のコード メトリックスの結果を生成します。

次のような方法では、ソリューション全体のコード メトリックスの結果を生成できます。

- メニュー バーから選択**分析** > **コード メトリックスの計算** > **ソリューションの**します。

- **ソリューション エクスプ ローラー**、ソリューションを右クリックし、**コード メトリックスの計算**します。

- **コード メトリックスの結果**ウィンドウで、選択、**ソリューションのコード メトリックスの計算**ボタンをクリックします。

結果を生成し、**コード メトリックスの結果**ウィンドウが表示されます。 結果の詳細を表示するには、ツリーを展開、**階層**列。

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>1 つまたは複数のプロジェクトのコード メトリックスの結果を生成します。

1. **ソリューション エクスプ ローラー**、1 つまたは複数のプロジェクトを選択します。

1. メニュー バーから選択**分析** > **コード メトリックスの計算** > **プロジェクトの選択の**します。

結果を生成し、**コード メトリックスの結果**ウィンドウが表示されます。 結果の詳細を表示するには、ツリーを展開、**階層**します。

## <a name="command-line-code-metrics"></a>コマンド ライン コード メトリックス

コード メトリックス データを生成するにはコマンドラインからC#および .NET Framework、.NET Core、および .NET Standard のアプリの Visual Basic プロジェクト。 コマンド ライン コード メトリックスのツールと呼ばれる*Metrics.exe*します。

取得する、 *Metrics.exe*あります実行可能ファイル、[自分で生成](#generate-the-executable)します。 近い将来に、[の発行済みバージョン*Metrics.exe*できる](https://github.com/dotnet/roslyn-analyzers/issues/1756)のため、自分でビルドする必要はありません。

### <a name="generate-the-executable"></a>実行可能ファイルを生成します。

実行可能ファイルを生成する*Metrics.exe*、これらの手順に従います。

1. 複製、 [dotnet/roslyn アナライザー](https://github.com/dotnet/roslyn-analyzers)リポジトリ。
2. Visual Studio の開発者コマンド プロンプトを管理者として開きます。
3. ルートから、 **roslyn アナライザー**リポジトリでは、次のコマンドを実行します。 `Restore.cmd`
4. ディレクトリに*src\Tools*します。
5. ビルドするには、次のコマンドを実行、 **Metrics.csproj**プロジェクト。

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   実行可能ファイルという*Metrics.exe*で生成される、 *artifacts\bin*リポジトリのルート ディレクトリ。

   > [!TIP]
   > 構築する*Metrics.exe*で[レガシ モード](#legacy-mode)、次のコマンドを実行します。
   >
   > ```shell
   > msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
   > ```

### <a name="usage"></a>使用法

実行する*Metrics.exe*ソリューションと、出力 XML ファイルを引数として、プロジェクトを指定します。 例:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

### <a name="output"></a>出力

生成された XML 出力は、次の形式を取ります。

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeMetricsReport Version="1.0">
  <Targets>
    <Target Name="ConsoleApp20.csproj">
      <Assembly Name="ConsoleApp20, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null">
        <Metrics>
          <Metric Name="MaintainabilityIndex" Value="100" />
          <Metric Name="CyclomaticComplexity" Value="1" />
          <Metric Name="ClassCoupling" Value="1" />
          <Metric Name="DepthOfInheritance" Value="1" />
          <Metric Name="LinesOfCode" Value="11" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="LinesOfCode" Value="11" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="LinesOfCode" Value="7" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\Users\mavasani\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="LinesOfCode" Value="4" />
                    </Metrics>
                  </Method>
                </Members>
              </NamedType>
            </Types>
          </Namespace>
        </Namespaces>
      </Assembly>
    </Target>
  </Targets>
</CodeMetricsReport>
```

### <a name="tool-differences"></a>ツールの相違点

など、Visual Studio 2015、Visual Studio の以前のバージョンには、というコマンド ライン コード メトリックス ツールが含まれている*Metrics.exe*します。 このツールの以前のバージョンは、アセンブリに基づく分析は、バイナリ分析を行いました。 新しいツールでは、代わりにソース コードを分析します。 新しい*Metrics.exe*はソース コードに基づいて、結果が以前のバージョンのによって生成されたものに異なる*Metrics.exe*と Visual Studio 2017 IDE 内で。

新しい*Metrics.exe*ソリューションとプロジェクトを読み込むことがあれば、ツールはソース コードのエラーがある場合でも、メトリックを計算できます。

#### <a name="metric-value-differences"></a>メトリック値の相違点

`LinesOfCode`メトリックがより正確で信頼性の高い、新しい*Metrics.exe*します。 Codegen の違いに依存しないし、ツールセットやランタイムの変更されたときに変更されません。 新しい*Metrics.exe*空白行とコメントを含め、コードの実際の行数をカウントします。

などの他のメトリック`CyclomaticComplexity`と`MaintainabilityIndex`として以前のバージョンのと同次数式を使用して*Metrics.exe*が、新しい*Metrics.exe*の数をカウント`IOperations`(論理指示をソース) 中間言語 (IL) 命令ではなく。 数値が以前のバージョンの若干異なる場合があります*Metrics.exe*と Visual Studio 2017 IDE のコード メトリックスの結果から。

### <a name="legacy-mode"></a>レガシ モード

ビルドを選択することもできます。 *Metrics.exe*で*レガシ モード*します。 ツールのレガシ モード バージョンは、どのような以前のバージョンのツールによって生成されたに近いメトリックの値を生成します。 レガシ モードでさらに、 *Metrics.exe*メソッドの同じセットの型を以前のバージョンのツールによって生成されたコード メトリックスのコード メトリックスを生成します。 たとえば、フィールドおよびプロパティの初期化子のコード メトリックス データが生成されないこと。 レガシ モードは、下位互換性またはゲート チェックインがコードがあるかどうかはメトリックに基づくコード番号に役立ちます。 ビルドするコマンド*Metrics.exe*レガシ モードでは。

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

詳細については、次を参照してください。[レガシ モードでのコード メトリックスの生成を有効にする](https://github.com/dotnet/roslyn-analyzers/pull/1841)します。

## <a name="see-also"></a>関連項目

- [コード メトリックスの結果 ウィンドウを使用します。](../code-quality/working-with-code-metrics-data.md)
- [コード メトリックス値](../code-quality/code-metrics-values.md)
