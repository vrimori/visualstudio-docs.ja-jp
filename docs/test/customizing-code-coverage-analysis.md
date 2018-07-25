---
title: Visual Studio でコード カバレッジ分析をカスタマイズする
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 7b48fc77dd88cf327050c0bf8ba893f8d4a626fa
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36303004"
---
# <a name="customize-code-coverage-analysis"></a>コード カバレッジ分析のカスタマイズ

既定では、コード カバレッジは、単体テスト中に読み込まれるすべてのソリューション アセンブリを分析します。 多くの場合は、この設定が効果的なので、この既定のビヘイビアーを使用することをお勧めします。 詳細については、「[コード カバレッジを使用した、テストされるコード割合の確認](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)」を参照してください。

テスト コードをコード カバレッジの結果から除外して、アプリケーション コードのみを含めるには、<xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> 属性をテスト クラスに追加します。

ソリューションの一部ではないアセンブリを含めるには、これらのアセンブリの *.pdb* ファイルを取得し、アセンブリ *.dll* ファイルと同じフォルダーにコピーします。

## <a name="run-settings-file"></a>実行設定ファイル

[実行設定ファイル](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)は、単体テスト ツールによって使用される構成ファイルです。 詳細なコード カバレッジの設定は、*.runsettings* ファイルで指定されます。

コード カバレッジをカスタマイズするには、次の手順を行います。

1. 実行設定ファイルをソリューションに追加します。 **ソリューション エクスプローラー**でソリューションのショートカット メニューを開き、**[追加]** > **[新しい項目]**、**[XML ファイル]** の順に選択します。 *CodeCoverage.runsettings* などの名前でファイルを保存します。

1. この記事の最後にあるサンプル ファイルの内容を追加し、後続の各セクションの説明に従って、ニーズに合わせてカスタマイズします。

1. 実行設定ファイルを選択するには、**[テスト]** メニューで **[テストの設定]** > **[テスト設定ファイルの選択]** の順に選択します。 コマンドラインから、またはビルド ワークフローでテストを実行するための実行設定ファイルを指定するには、「[*.runsettings* ファイルを使用して単体テストを構成する](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#specify-a-run-settings-file)」を参照してください。

   **[コード カバレッジの分析]** を選択すると、実行設定ファイルから構成情報が読み取られます。

   > [!TIP]
   > 前のコード カバレッジの結果とコードの色分けは、テストを実行したりコードを更新したりしても、自動的に非表示にはなりません。

カスタム設定のオンとオフを切り替えるには、**[テストの設定]** メニューの **[テスト]** でファイルを選択したり選択解除したりします。

![カスタム設定ファイルを持つ [テストの設定] メニュー](../test/media/codecoverage-settingsfile.png)

### <a name="specify-symbol-search-paths"></a>シンボル検索パスの指定

コード カバレッジには、アセンブリのシンボル ファイル (*.pdb* ファイル) が必要です。 ソリューションによってビルドされたアセンブリには、通常、バイナリ ファイルと共にシンボル ファイルも存在しており、コード カバレッジは自動的に動作します。 ただし、場合によっては、参照されるアセンブリをコード カバレッジ分析に追加したいこともあります。 そのような場合、*.pdb* ファイルがバイナリと同じ場所にないこともありますが、シンボル検索パスを *.runsettings* ファイルで指定できます。

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!NOTE]
> シンボルの解決には、特に多数のアセンブリでリモートのファイルの場所を使用している場合、時間がかかることがあります。 そのため、*.pdb* ファイルをバイナリ (*.dll* または *.exe*) ファイルと同じローカルの場所にコピーすることを検討してください。

### <a name="exclude-and-include"></a>Exclude (除外) と Include (包含)

指定したアセンブリをコード カバレッジ分析から除外できます。 例:

```xml
<ModulePaths>
  <Exclude>
   <ModulePath>Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

逆に、どのアセンブリが包含されるかを指定することもできます。 ソリューションにアセンブリを追加するときに、一覧にも忘れずに追加しなければならないのが、この方法の欠点です。

```xml
<ModulePaths>
  <Include>
   <ModulePath>Fabrikam.Math.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Include>
</ModulePaths>
```

**Include** が空の場合、コード カバレッジの処理には、読み込まれ、*.pdb* ファイルが見つかるすべてのアセンブリが含まれます。 コード カバレッジには、**Exclude** リスト内の句に一致する項目が含まれません。

**Include** は **Exclude** の前に処理されます。

### <a name="regular-expressions"></a>正規表現

Include ノードと Exclude ノードでは、正規表現を使用できます。 詳細については、[Visual Studio で正規表現を使用する](../ide/using-regular-expressions-in-visual-studio.md)方法に関するページを参照してください。 正規表現は、ワイルドカードと同じではありません。 特に次の点に注意してください。

- **.\*** は任意の文字の文字列と一致します

- **\\.** はピリオド "." と一致します

- **\\(   \\)** は "(  )" と一致します

- **\\\\** はファイル パス区切り記号 "\\" と一致します

- **^** は文字列の先頭と一致します

- **$** は文字列の末尾と一致します

すべての一致で、大文字と小文字が区別されます。

例:

```xml
<ModulePaths>
  <Include>
    <!-- Include all loaded .dll assemblies (but not .exe assemblies): -->
    <ModulePath>.*\.dll$</ModulePath>
  </Include>
  <Exclude>
    <!-- But exclude some assemblies: -->
    <ModulePath>.*\\Fabrikam\.MyTests1\.dll$</ModulePath>
    <!-- Exclude all file paths that contain "Temp": -->
    <ModulePath>.*Temp.*</ModulePath>
  </Exclude>
</ModulePaths>
```

> [!WARNING]
> 正規表現にエラー (エスケープされていない、または一致しないかっこなど) がある場合、コード カバレッジ分析は実行されません。

### <a name="other-ways-to-include-or-exclude-elements"></a>要素を包含または除外するための別の方法

- **ModulePath** - アセンブリ ファイル パスで指定されたアセンブリと一致します。

- **CompanyName** - **Company** 属性でアセンブリと一致します。

- **PublicKeyToken** - 公開キー トークンで、署名付きアセンブリと一致します。

- **Source** - 要素が定義されているソース ファイルのパス名で要素と一致します。

- **Attribute** - 特定の属性のアタッチ先の要素と一致します。 属性の完全名を指定し、名前の末尾に "Attribute" を含めます。

- **Function** - 完全修飾名でプロシージャ、関数、またはメソッドに一致します。 関数名を一致させるには、正規表現が、名前空間、クラス名、メソッド名、およびパラメーター リストを含む関数の完全修飾名と一致する必要があります。 例:

   ```csharp
   Fabrikam.Math.LocalMath.SquareRoot(double);
   ```

   ```cpp
   Fabrikam::Math::LocalMath::SquareRoot(double)
   ```

   ```xml
   <Functions>
     <Include>
       <!-- Include methods in the Fabrikam namespace: -->
       <Function>^Fabrikam\..*</Function>
       <!-- Include all methods named EqualTo: -->
       <Function>.*\.EqualTo\(.*</Function>
     </Include>
     <Exclude>
       <!-- Exclude methods in a class or namespace named UnitTest: -->
       <Function>.*\.UnitTest\..*</Function>
     </Exclude>
   </Functions>
   ```

## <a name="sample-runsettings-file"></a>サンプル .runsettings ファイル

このコードをコピーし、自分のニーズに合わせて編集します。

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- File name extension must be .runsettings -->
<RunSettings>
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
<!--
Additional paths to search for .pdb (symbol) files. Symbols must be found for modules to be instrumented.
If .pdb files are in the same folder as the .dll or .exe files, they are automatically found. Otherwise, specify them here.
Note that searching for symbols increases code coverage runtime. So keep this small and local.
-->
<!--
            <SymbolSearchPaths>
                   <Path>C:\Users\User\Documents\Visual Studio 2012\Projects\ProjectX\bin\Debug</Path>
                   <Path>\\mybuildshare\builds\ProjectX</Path>
            </SymbolSearchPaths>
-->

<!--
About include/exclude lists:
Empty "Include" clauses imply all; empty "Exclude" clauses imply none.
Each element in the list is a regular expression (ECMAScript syntax). See http://msdn.microsoft.com/library/2k3te2cs.aspx.
An item must first match at least one entry in the include list to be included.
Included items must then not match any entries in the exclude list to remain included.
-->

            <!-- Match assembly file paths: -->
            <ModulePaths>
              <Include>
                <ModulePath>.*\.dll$</ModulePath>
                <ModulePath>.*\.exe$</ModulePath>
              </Include>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- Match fully qualified names of functions: -->
            <!-- (Use "\." to delimit namespaces in C# or Visual Basic, "::" in C++.)  -->
            <Functions>
              <Exclude>
                <Function>^Fabrikam\.UnitTest\..*</Function>
                <Function>^std::.*</Function>
                <Function>^ATL::.*</Function>
                <Function>.*::__GetTestMethodInfo.*</Function>
                <Function>^Microsoft::VisualStudio::CppCodeCoverageFramework::.*</Function>
                <Function>^Microsoft::VisualStudio::CppUnitTestFramework::.*</Function>
              </Exclude>
            </Functions>

            <!-- Match attributes on any code element: -->
            <Attributes>
              <Exclude>
                <!-- Don't forget "Attribute" at the end of the name -->
                <Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.DebuggerNonUserCodeAttribute$</Attribute>
                <Attribute>^System\.Runtime\.CompilerServices.CompilerGeneratedAttribute$</Attribute>
                <Attribute>^System\.CodeDom\.Compiler.GeneratedCodeAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.CodeAnalysis.ExcludeFromCodeCoverageAttribute$</Attribute>
              </Exclude>
            </Attributes>

            <!-- Match the path of the source files in which each method is defined: -->
            <Sources>
              <Exclude>
                <Source>.*\\atlmfc\\.*</Source>
                <Source>.*\\vctools\\.*</Source>
                <Source>.*\\public\\sdk\\.*</Source>
                <Source>.*\\microsoft sdks\\.*</Source>
                <Source>.*\\vc\\include\\.*</Source>
              </Exclude>
            </Sources>

            <!-- Match the company name property in the assembly: -->
            <CompanyNames>
              <Exclude>
                <CompanyName>.*microsoft.*</CompanyName>
              </Exclude>
            </CompanyNames>

            <!-- Match the public key token of a signed assembly: -->
            <PublicKeyTokens>
              <!-- Exclude Visual Studio extensions: -->
              <Exclude>
                <PublicKeyToken>^B77A5C561934E089$</PublicKeyToken>
                <PublicKeyToken>^B03F5F7F11D50A3A$</PublicKeyToken>
                <PublicKeyToken>^31BF3856AD364E35$</PublicKeyToken>
                <PublicKeyToken>^89845DCD8080CC91$</PublicKeyToken>
                <PublicKeyToken>^71E9BCE111E9429C$</PublicKeyToken>
                <PublicKeyToken>^8F50407C4E9E73B6$</PublicKeyToken>
                <PublicKeyToken>^E361AF139669C375$</PublicKeyToken>
              </Exclude>
            </PublicKeyTokens>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>
    </DataCollectors>
  </DataCollectionRunSettings>
</RunSettings>
```

## <a name="see-also"></a>関連項目

- [.runsettings ファイルを使用して単体テストを構成する](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [コード カバレッジを使用した、テストされるコード割合の確認](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
- [コードの単体テスト](../test/unit-test-your-code.md)