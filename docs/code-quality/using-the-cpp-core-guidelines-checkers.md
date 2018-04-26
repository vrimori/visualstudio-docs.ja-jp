---
title: C++ の主要なガイドライン チェッカーを使用します。
ms.date: 11/04/2016
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
dev_langs:
- CPP
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.openlocfilehash: 607b4f2d96e809f9c8b5aedf8362c5d5f54e097d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="using-the-c-core-guidelines-checkers"></a>C++ の主要なガイドライン チェッカーを使用します。
C++ の主要なガイドラインは、ポータブル ガイドライン、ルール、および C++ の専門家とデザイナーで作成された C++ で記述に関するベスト プラクティスのセットです。 現在、visual Studio は、c++ のコード分析ツールの一部としてこれらの規則のサブセットをサポートします。 コア ガイドライン チェッカーが Visual Studio 2017 で既定でインストールされ[Visual Studio 2015 用の NuGet パッケージとして入手できます](#vs2015_corecheck)です。

## <a name="the-c-core-guidelines-project"></a>プロジェクトの C++ の主要なガイドライン
 Bjarne stroustrup 共著やその他のユーザーによって作成された、C++ コア ガイドラインは、安全で効果的に最新の C++ を使用します。 ガイドラインは、静的な型の安全性とリソースの安全性を強調します。 削除するか、言語のエラーを起こしやすい部分を最小限に抑える方法を特定し、信頼性の高い方法でパフォーマンスとコードを簡素化する方法を提案します。 次のガイドラインは、標準の C++ Foundation によって保持されます。 詳細については、ドキュメントを参照してください。 [C++ コア ガイドライン](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)、C++ の主要なガイドラインのドキュメントのプロジェクト ファイルにアクセスし[GitHub](https://github.com/isocpp/CppCoreGuidelines)です。

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>コード分析のコアを確認して C++ ガイドラインを有効にします。
 選択して、プロジェクトでコード分析を有効にすることができます、**ビルドに対するコード分析を有効にする**のチェック ボックス、**コード分析**のセクションで、**プロパティ ページ**のダイアログ ボックスプロジェクトです。

 ![コード分析の全般設定のプロパティ ページ](../code-quality/media/cppcorecheck_codeanalysis_general.png "CPPCoreCheck_CodeAnalysis_General")

 C++ コアの確認規則は、コード分析が有効になっているときに実行される既定の規則セットの拡張機能です。 C++ コア チェックの規則では、開発中であるため一部のルールが準備されて、およびいくつか、すべてのコードで使用する準備ができていない可能性がありますがわかりやすくします。 ルールは、次の 2 つのグループに分けられます: リリースし、実験用です。 プロジェクトのプロパティでリリースされたか、実験用の規則を実行するかどうかを選択できます。

 ![コード分析の拡張機能設定のプロパティ ページ](../code-quality/media/cppcorecheck_codeanalysis_extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")

 有効にするにまたは C++ コアの確認規則セットを無効にする、開く、**プロパティ ページ**プロジェクトのダイアログ。 **構成プロパティ**、展開**コード分析**、**拡張**です。 横にドロップダウン リストで制御**を有効にする C++ Core のチェック (リリース済み)** または**を有効にする C++ コアを確認 (します試験段階)** を選択**はい**または**いいえ**です。 選択**OK**または**適用**して変更を保存します。

## <a name="examples"></a>使用例
 C++ コア チェックの規則を検索する問題のいくつかの例を次に示します。

```cpp
// CoreCheckExample.cpp
// Add CppCoreCheck package and enable code analysis in build for warnings.

int main()
{
    int arr[10];           // warning C26494
    int* p = arr;          // warning C26485

    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
    {
        int* q = p + 1;    // warning C26481 (suppressed)
        p = q++;           // warning C26481 (suppressed)
    }

    return 0;
}
```

 この例では、C++ コア チェックの規則を検索する警告のいくつかを示します。

-   C26494 はルール Type.5: 常にオブジェクトを初期化します。

-   C26485 はルール Bounds.3: 配列とポインター減衰しません。

-   C26481 はルール Bounds.1: ポインター演算を使用しません。 代わりに、`span` を使用してください。

 コード分析のコアを確認して C++ ruleset はインストールされている、このコードをコンパイルすると、最初の 2 つの警告は、出力が、3 番目の抑制を有効になっている場合。 コード例のビルド出力を次に示します。

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

C++ の主要なガイドラインより、安全なコードを作成するのに役立つは。 ただし場合は、ルール、またはプロファイルを適用しないようにするインスタンスがある場合は、簡単に、コード内で直接抑制です。 使用することができます、`gsl::suppress`を検出して、次のコード ブロック内の規則の違反をレポートから C++ Core のチェックを保持する属性。 特定のルールを抑制する個々 のステートメントをマークすることができます。 記述して、境界プロファイル全体を抑制することができますも`[[gsl::suppress(bounds)]]`特定のルールの数を含めずにします。

## <a name="supported-rule-sets"></a>規則セットのサポート
C++ コア ガイドライン チェックには、新しい規則が追加されるの既存のコードを生成する警告の数を増やすことがあります。 有効にするためのルールの種類をフィルター処理、定義済みの規則セットを使用できます。
ほとんどのルールのリファレンス トピックでは、下にある[Visual Studio C コア チェック リファレンス](code-analysis-for-cpp-corecheck.md)です。

Visual Studio 2017 15.3 のバージョンの時点でサポートされている規則セットは次のとおりがあります。
  - **所有者ポインター ルール**強制[所有者に関連するリソース管理のチェック<T>、C++ の主要なガイドラインから](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)です。

  - **Const ルール**強制[、C++ の主要なガイドラインから const に関連するチェック](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability)です。

  - **生のポインター ルール**強制[リソース管理は、C++ の主要なガイドラインから未処理に関連するポインターをチェック](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)です。

  - **一意のポインター ルール**強制[、C++ の主要なガイドラインから一意のポインターのセマンティクスを持つ型に関連するリソース管理のチェック](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)です。

  - **ルールに外接**適用、 [、C++ の主要なガイドラインのプロファイルに外接](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile)です。

  - **規則の入力**適用、 [、C++ の主要なガイドラインのプロファイルを入力](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile)です。

  **Visual Studio 2017 バージョン 15.5**:
  - **クラスのルール**特殊なメソッドと仮想の仕様の適切な使用に関連するいくつかの規則。 これは、チェックの推奨のサブセット[クラスおよびクラスの階層構造](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-class)です。
  - **同時実行規則**単一のルールが正しくない宣言ガード オブジェクトをキャッチします。 詳細については、次を参照してください。[同時実行に関連するガイドライン](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-concurrency)です。
  - **宣言の規則が**からの規則のいくつか、[インターフェイス ガイドライン](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-interfaces)グローバル変数に重点を置いたが宣言されます。
  - **機能ルール**導入の際に役立つ 2 つのチェック、`noexcept`指定子。 これはに関するガイドラインの一部[関数の設計と実装をオフに](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-functions)です。
  - **共有ポインター規則**の一部として[リソース管理](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-resource)ガイドライン実施が追加されました共有ポインターに固有のいくつかの規則が関数に渡されたか、ローカルで使用します。
  - **スタイル ルール**1 単純ですが、重要なチェックの使用を禁止[goto](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-goto)です。 これは、コーディング スタイルと式および C++ ではステートメントの使用の改善の最初の手順です。

  **Visual Studio 2017 バージョン 15.6**:
  - **算術規則**算術演算子を検出する規則を[オーバーフロー](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-overflow)、[操作の符号付き-符号なし](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-unsigned)と[ビット操作](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-nonnegative)です。


 1 つまたはいくつかのグループの警告を制限することができます。 **ネイティブ最小**と**ネイティブ推奨**ルール セットには、他の PREfast チェックだけでなく C++ コア チェック ルールが含まれます。 確認には、使用可能なルール セット、プロジェクトのプロパティ ダイアログを開き、次のように選択します**コード Analysis\General**、にあるボックスを開き、**規則セット**コンボ ボックス、および選択**複数の規則セットの選択**。 詳細については、Visual Studio でのルール セットを使用して、次を参照してください。[ルール セットのコード分析規則のグループを使用して](using-rule-sets-to-group-code-analysis-rules.md)です。

## <a name="macros"></a>[マクロ]
 C++ の主要なガイドライン チェックをコードで警告のカテゴリ全体を抑制するより簡単にするマクロを定義するヘッダー ファイルが付属します。

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

これらのマクロは、規則セットに対応し、警告番号のスペースで区切られた一覧に展開します。 適切なプラグマ コンストラクトを使用すると、プロジェクトの興味深いは、有効な一連の規則またはコードのセクションを構成できます。 次の例では、コード分析に関する注意事項についてのみ定数修飾子がありません。

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>属性
 Microsoft Visual C コンパイラでは、属性を抑制する、GSL の制限付きサポートがします。 式および関数の内部でのブロックのステートメントで警告を抑制するために使用されます。

```cpp
// Supress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Supress all warnings from the 'r' rule group (resource management) in block.
[[gsl::suppress(r)]]
{
    new int;
}

// Suppress only one specific warning number.
// For declarations, you may need to use the surrounding block.
// Macros are not expanded inside of attributes.
// Use plain numbers instead of macros from the warnings.h.
[[gsl::suppress(26400)]]
{
    int *p = new int;
}
```

## <a name="suppressing-analysis-by-using-command-line-options"></a>コマンド ライン オプションを使用して分析を抑制します。
 #Pragmas、代わりに、プロジェクトまたはファイルを 1 つの警告を抑制する、ファイルのプロパティ ページでコマンド ライン オプションを使用できます。 たとえば、警告を無効にするため、ファイルの 26400。

 1) ファイルを右クリックして**ソリューション エクスプ ローラー**

 2) 選択**プロパティ |C または C++ |コマンドライン**

 3) **追加オプション**ウィンドウで、追加`/wd26400`です。

 指定して、ファイルのすべてのコード分析を一時的に無効にするコマンド ライン オプションを使用することができます`/analyze-`です。 これにより、警告が生成されます。 *D9025 をオーバーライドする '/analyze' と '/analyze -'*、をが後でコード分析を再び有効にすることを知らせます。

 ## <a name="corecheck_per_file"></a> 特定のプロジェクト ファイルでは、C++ コア ガイドライン チェックを有効にします。
Do 重点を置いてコードの分析やまだ Visual Studio IDE を使用する役に立つ場合があります。 ビルド時間を節約し、結果をフィルター処理を容易にできるように、大規模なプロジェクトの次のサンプル シナリオを使用できます。

1.  コマンド シェルで次のように設定します。、`esp.extension`と`esp.annotationbuildlevel`環境変数。
2.  これらの変数を継承するには、コマンド シェルから Visual Studio を起動します。
3.  プロジェクトを読み込むし、そのプロパティを開きます。
4.  コード分析を有効にする、適切なルール セットの選択がコード分析の拡張機能を有効にしません。
5.  C++ の主要なガイドライン チェッカーで分析し、そのプロパティを開くファイルに移動します。
6.  選択**C/c++ \Command 行オプション**し、追加 `/analyze:plugin EspXEngine.dll`
7.  プリコンパイル済みヘッダーの使用を無効にする (**C/c++ \Precompiled ヘッダー**)。 これは、拡張機能エンジンは、プリコンパイル済みヘッダー (PCH); からその内部情報の読み取りを試行可能性があります。PCH は、既定のプロジェクトのオプションでコンパイルされた場合、に互換性がないです。
8.  プロジェクトをリビルドします。 一般的な PREFast チェックは、すべてのファイルに対して実行する必要があります。 C++ の主要なガイドライン チェッカーが既定で有効でないために必要があります、これを使用するように構成ファイルでのみ実行します。

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Visual Studio の外部では、C++ コア ガイドライン チェッカーの使用方法
自動ビルドで、C++ の主要なガイドラインのチェックを行うこともできます。

### <a name="msbuild"></a>MSBuild
 ネイティブ コード分析チェッカー (PREfast) は、カスタム ターゲット ファイルでの MSBuild 環境に統合されます。 プロジェクトのプロパティを使用して、有効にし、(PREfast に基づきます) を C++ コア ガイドライン チェックを追加することができます。

 ```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```
Microsoft.Cpp.targets ファイルをインポートする前にこれらのプロパティを追加することを確認してください。 特定のルール セットを選択またはカスタム規則セットを作成したりその他の PREfast チェックを含む既定の規則セットを使用できます。

同じアプローチを使用して、指定したファイルでのみ C++ コア チェッカーを実行することができます[前に説明した](#corecheck_per_file)、ただし、MSBuild ファイルを使用します。 使用して、環境変数を設定することができます、`BuildMacro`項目。

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>CppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

プロジェクト ファイルを変更しない場合は、コマンドラインでプロパティを渡すことができます。

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>非 MSBuild プロジェクト
MSBuild に依存しないビルド システムを使用する場合、チェックを実行することもできますが、コード分析エンジンの構成の一部の内部構造について理解する必要があります。 これらの内部構造は、今後サポートされる保証はありません。

いくつかの環境変数を設定して、コンパイラの適切なコマンド ライン オプションを使用する必要があります。 コンパイラの特定のパスを検索、ディレクトリなどを含める必要があるないように、「Native Tools コマンド プロンプト」環境下で動作することをお勧めします。

1.  **環境変数**
  - `set esp.extensions=cppcorecheck.dll` これは、主要なガイドラインを C++ モジュールを読み込むエンジンを指示します。
  - `set esp.annotationbuildlevel=ignore` これには、SAL 注釈を処理するロジックが無効にします。 注釈は、C++ コア ガイドライン チェックで、コード分析に影響しない。 ただし、処理時間 (場合によって長時間)。 この設定は、省略可能だが強くお勧めします。
  - `set caexcludepath=%include%` 標準ヘッダーで起動される警告を無効にすることを強くお勧めします。 たとえば、プロジェクトの一般的なヘッダーへのパス、ここでは、複数のパスを追加できます。
2.  **コマンド ライン オプション**
  - `/analyze`  コード分析を有効 (も使用を検討して/analyze: のみと/analyze: quiet)。
  - `/analyze:plugin EspXEngine.dll` このオプションでは、コード分析の拡張機能エンジンを PREfast に読み込みます。 このエンジンは、さらに、C++ の主要なガイドライン チェッカーを読み込みます。



## <a name="use-the-guideline-support-library"></a>ガイドライン サポート ライブラリを使用します。
 ガイドライン サポート ライブラリは、主要なガイドラインに従う役立つ設計されています。 GSL には、安全な代替関数とエラーが発生しやすい構成要素を交換するのに便利な定義が含まれます。 たとえば、置き換えることができます、`T*, length`でパラメーターのペア、`span<T>`型です。 GSL については、「 [ http://www.nuget.org/packages/Microsoft.Gsl](http://www.nuget.org/packages/Microsoft.Gsl)です。 ライブラリは、ソースの表示、コメントの作成、または投稿ためにのオープン ソース、です。 プロジェクトが存在する[ https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL)です。

 ## <a name="vs2015_corecheck"></a> Visual Studio 2015 のプロジェクトで C++ コア チェックのガイドラインを使用します。
  Visual Studio 2015 を使用する場合、C++ コア確認コード分析規則セットは既定ではインストールされていません。 Visual Studio 2015 でのコアを確認して C++ コード分析ツールを有効にする前に、は、追加の手順を実行する必要があります。 Microsoft では、Nuget パッケージを使用して、Visual Studio 2015 のプロジェクトのサポートを提供します。 パッケージが Microsoft.CppCoreCheck をという名前でありで利用可能な[ http://www.nuget.org/packages/Microsoft.CppCoreCheck](http://www.nuget.org/packages/Microsoft.CppCoreCheck)です。 このパッケージは、少なくとも Visual Studio 2015 Update 1 と共にインストールされているがある必要があります。

 パッケージには、依存関係が、ヘッダーのみガイドライン サポート ライブラリ (GSL) として別のパッケージもインストールされます。 Github で利用可能な GSL も[ https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL)です。

 コード分析ルールが読み込まれるため、Visual Studio 2015 内でチェックする C++ プロジェクトごとに Microsoft.CppCoreCheck NuGet パッケージをインストールする必要があります。

#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Visual Studio 2015 でプロジェクトに Microsoft.CppCoreCheck パッケージを追加するには

1.  **ソリューション エクスプ ローラー**、右クリックして、パッケージを追加するソリューションで、プロジェクトのショートカット メニューを表示します。 選択**NuGet パッケージの管理**を開くには、 **NuGet Package Manager**です。

2.  **NuGet Package Manager**ウィンドウで、Microsoft.CppCoreCheck を検索します。

     ![Nuget パッケージ マネージャー ウィンドウでは、CppCoreCheck パッケージを示しています](../code-quality/media/cppcorecheck_nuget_window.PNG "CPPCoreCheck_Nuget_Window。")

3.  Microsoft.CppCoreCheck パッケージを選択し、、**インストール**をプロジェクトにルールを追加するボタンをクリックします。

 NuGet パッケージを追加、追加の MSBuild *.targets*ファイルをプロジェクトでコード分析を有効にしたときに呼び出されるプロジェクト。 これは、 *.targets*ファイル拡張機能の追加として、Visual Studio コード分析ツールに C++ コア チェックの規則を追加します。 パッケージがインストールされている場合は、有効にするにまたは解放され、実験用のルールを無効にするプロパティ ページ ダイアログを使用できます。

## <a name="see-also"></a>関連項目
[Visual Studio の C++ コア チェック参照](code-analysis-for-cpp-corecheck.md)です。

