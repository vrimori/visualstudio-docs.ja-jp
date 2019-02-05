---
title: IDE またはコマンドラインからのコード メトリックスを生成します。
ms.date: 11/02/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91e32cdae7310a99021946315279736bddb094a8
ms.sourcegitcommit: 0f7411c1a47d996907a028e920b73b53c2098c9f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2019
ms.locfileid: "55690139"
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

コード メトリックス データを生成するにはコマンドラインからC#および .NET Framework、.NET Core、および .NET Standard のアプリの Visual Basic プロジェクト。 コード メトリックスをコマンドラインから実行するインストール、 [Microsoft.CodeAnalysis.Metrics NuGet パッケージ](#microsoftcodeanalysismetrics-nuget-package)またはビルド、 [Metrics.exe](#metricsexe)実行可能ファイル自分でします。

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Microsoft.CodeAnalysis.Metrics NuGet パッケージ

コマンドラインからのコード メトリックス データを生成する最も簡単な方法は、インストールすることによって、 [Microsoft.CodeAnalysis.Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) NuGet パッケージ。 パッケージをインストールした後、実行`msbuild /t:Metrics`プロジェクト ファイルを含むディレクトリから。 例:

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:29:57 PM.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics\Metrics.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:ClassLibrary3.Metrics.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'ClassLibrary3.Metrics.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

出力ファイル名を指定して上書きできます`/p:MetricsOutputFile=<filename>`します。 取得することも[レガシ スタイル](#previous-versions)メトリック データを指定することによってコード`/p:LEGACY_CODE_METRICS_MODE=true`します。 例:

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics /p:LEGACY_CODE_METRICS_MODE=true /p:MetricsOutputFile="Legacy.xml"
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:31:00 PM.
The "MetricsOutputFile" property is a global property, and cannot be modified.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics.Legacy\Metrics.Legacy.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:Legacy.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'Legacy.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

### <a name="code-metrics-output"></a>コード メトリックの出力

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
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
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

### <a name="metricsexe"></a>Metrics.exe

NuGet パッケージをインストールしない場合は、生成および使用して、 *Metrics.exe*直接実行可能ファイルです。 生成する、 *Metrics.exe*実行可能ファイル。

1. 複製、 [dotnet/roslyn アナライザー](https://github.com/dotnet/roslyn-analyzers)リポジトリ。
2. Visual Studio の開発者コマンド プロンプトを管理者として開きます。
3. ルートから、 **roslyn アナライザー**リポジトリでは、次のコマンドを実行します。 `Restore.cmd`
4. ディレクトリに*src\Tools*します。
5. ビルドするには、次のコマンドを実行、 **Metrics.csproj**プロジェクト。

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   実行可能ファイルという*Metrics.exe*で生成される、 *artifacts\bin*リポジトリのルート ディレクトリ。

#### <a name="metricsexe-usage"></a>Metrics.exe 使用状況

実行する*Metrics.exe*ソリューションと、出力 XML ファイルを引数として、プロジェクトを指定します。 例:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>レガシ モード

ビルドすることもできます*Metrics.exe*で*レガシ モード*します。 ツールのレガシ モード バージョンは、何に近いメトリックの値を生成します。[以前のバージョンのツールによって生成された](#previous-versions)します。 レガシ モードでさらに、 *Metrics.exe*メソッドの同じセットの型を以前のバージョンのツールによって生成されたコード メトリックスのコード メトリックスを生成します。 たとえば、フィールドおよびプロパティの初期化子のコード メトリックス データが生成されないこと。 レガシ モードは、下位互換性またはゲート チェックインがコードがあるかどうかはメトリックに基づくコード番号に役立ちます。 ビルドするコマンド*Metrics.exe*レガシ モードでは。

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

詳細については、次を参照してください。[レガシ モードでのコード メトリックスの生成を有効にする](https://github.com/dotnet/roslyn-analyzers/pull/1841)します。

### <a name="previous-versions"></a>以前のバージョン

など、Visual Studio 2015、Visual Studio の以前のバージョンにも呼び出されたコマンド ライン コード メトリックス ツールが含まれている*Metrics.exe*します。 このツールの以前のバージョンは、アセンブリに基づく分析は、バイナリ分析を行いました。 新しいツールでは、代わりにソース コードを分析します。 結果はの以前のバージョンによって生成されたものにさまざまな新しいコマンド ライン コード メトリックス ツールは、ソース コード ベースであるため*Metrics.exe*と Visual Studio 2017 IDE 内で。

コマンド ライン コード メトリックスの新しいツールは、ソリューションとプロジェクトを読み込むことがあれば、ソース コードのエラーがある場合でも、メトリックを計算します。

#### <a name="metric-value-differences"></a>メトリック値の相違点

`LinesOfCode`メトリックが正確と新しいコマンド ライン コード メトリックス ツールで信頼性が向上します。 Codegen の違いに依存しないし、ツールセットやランタイムの変更されたときに変更されません。 新しいツールでは、空白行とコメントを含め、コードの実際の行数をカウントします。

などの他のメトリック`CyclomaticComplexity`と`MaintainabilityIndex`として以前のバージョンのと同次数式を使用して*Metrics.exe*、新しいツールの数をカウントするが、 `IOperations` (論理ソース命令) 中間の代わりに言語 (IL) の手順です。 数値が以前のバージョンの若干異なる場合があります*Metrics.exe*と Visual Studio 2017 IDE のコード メトリックスの結果から。

## <a name="see-also"></a>関連項目

- [コード メトリックスの結果 ウィンドウを使用します。](../code-quality/working-with-code-metrics-data.md)
- [コード メトリックス値](../code-quality/code-metrics-values.md)
