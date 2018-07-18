---
title: Roslyn アナライザーと ImmutableArrays 用のコードに対応するライブラリ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6ebafdd09e6fca0e1266c4eb03c4f6cb66554d06
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148520"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Roslyn アナライザーと ImmutableArrays 用のコードに対応するライブラリ

[.NET コンパイラ プラットフォーム](https://github.com/dotnet/roslyn)("Roslyn") を使用して、コードに対応するライブラリを作成できます。  コードに対応するライブラリは、機能を使用することができますを最適な方法で、またはエラーを回避するには、ライブラリを使用するためのツール (Roslyn アナライザー) を提供します。  このトピックでは、現実世界の Roslyn アナライザーを使用する場合は、一般的なエラーをキャッチするを構築する方法、 [System.Collections.Immutable](https://www.nuget.org/packages/System.Collections.Immutable) NuGet パッケージです。  この例では、アナライザーによって検出されたコードの問題のコードの修正プログラムを提供する方法も示します。  ユーザーは、コード修正を行いました。 Visual Studio 電球 UI を表示したり、コードの修正プログラムを自動的に適用できます。

## <a name="getting-started"></a>作業の開始

この例をビルドするには、次のとおりです。

* Visual Studio 2015 (、Express エディション以外) またはそれ以降のバージョン。  無料を使用することができます[Visual Studio Community エディション](https://www.visualstudio.com/products/visual-studio-community-vs)
* [Visual Studio SDK](../extensibility/visual-studio-sdk.md)です。  確認することも、Visual Studio をインストールするときに、同時に、SDK をインストールする一般的なツール Visual Studio 機能拡張ツールです。  Visual Studio が既にインストールされて場合、メイン メニューに移動してこの SDK をインストールすることも、**ファイル&#124;新規&#124;プロジェクト.** 左側のナビゲーション ウィンドウで、c# を選択し、機能拡張を選択し、します。  選択すると、"**Visual Studio 機能拡張ツールをインストール**"階層リンクのプロジェクト テンプレートをするよう求められますをダウンロードして、SDK をインストールします。
* [.NET コンパイラ プラットフォーム ("Roslyn") SDK](http://aka.ms/roslynsdktemplates)です。  メイン メニューに移動して、この SDK をインストールすることもできます**ファイル&#124;新規&#124;プロジェクト.。** 選択、 **c#** 左側のナビゲーション ペインで、クリックして、 **Extensibility**です。  選択すると"**.NET コンパイラ プラットフォーム SDK をダウンロードして**"階層リンクのプロジェクト テンプレートをするよう求められますをダウンロードして、SDK をインストールします。  この SDK に含まれています、 [Roslyn 構文ビジュアライザー](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer)です。  この非常に便利なツールでは、どのようなコード モデルの種類を理解する必要があります内で検索、アナライザーです。  アナライザー インフラストラクチャ コードを呼び出すの特定のコード モデルの種類のコードはのみに必要なときに実行し、関連するコードを分析することのみに集中できます。

## <a name="whats-the-problem"></a>何がそんなに問題ですか。

Immutablearray をライブラリに提供する想像してください (たとえば、 <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>) をサポートします。  C# 開発者では、.NET アレイを備えたエクスペリエンスの多くがあります。  ただし、実装で使用される ImmutableArrays および最適化の手法の性質上、c# 開発者 intuitions と、ユーザー、ライブラリの破損のコードを記述する以下に示すよう。  さらに、ユーザーは、これはグループを使用して .NET で Visual Studio で、高品質なエクスペリエンスでは実行時まで、エラー表示されません。

ユーザーは、次のようなコードの記述に慣れています。

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

後続の行のコードをコピーする空の配列を作成して、コレクション初期化子構文の使用は、c# の開発者に非常に習熟しています。  ただし、同じを書き込み、ImmutableArray のコードがクラッシュする実行時に。

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

最初のエラーでは、基になるデータ ストレージをラップする構造体を使用した immutablearray を実装のためです。 構造体は、パラメーターなしのコンス トラクターを持つ必要がありますように`default(T)`式には、すべての構造体を返す 0 または null のメンバーです。  コードにアクセスするときに`b1.Length`、immutablearray を構造体の基になる記憶域配列がないために、実行時に null がエラーを逆参照があります。  空の ImmutableArray を作成するための正しい方法は`ImmutableArray<int>.Empty`します。

ImmutableArray.Add メソッドはこのメソッドを呼び出すたびに新しいインスタンスを返すために、コレクション初期化子を含むエラーが発生します。  ImmutableArrays 決して変更されるため、新しい要素を追加するときに、オブジェクトを取得する戻り新しい immutablearray を (これは以前から存在 ImmutableArray とパフォーマンス向上のための記憶域を共有することがあります)。  `b2`呼び出す前に最初の immutablearray を指す`Add()`5 回`b2`immutablearray を既定値は、します。  エラーを逆参照の呼び出しの長さにも null でクラッシュします。  手動で追加の呼び出しは、使用することがなく、ImmutableArray を初期化するための正しい方法`ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`です。

## <a name="finding-relevant-syntax-node-types-to-trigger-your-analyzer"></a>関連する構文、アナライザーをトリガーするノードの種類を検索します。

 アナライザーをビルドするには、まず把握 SyntaxNode の種類確認する必要があります。 構文ビジュアライザー メニューから起動され、**ビュー&#124;その他のウィンドウ&#124;Roslyn 構文ビジュアライザー**です。

宣言する行のエディターのキャレットを配置する`b1`です。  使用するビジュアライザーの構文を示していますが表示されます、`LocalDeclarationStatement`構文ツリーのノードです。  このノードには、`VariableDeclaration`がさらに、`VariableDeclarator`がさらに、 `EqualsValueClause`、最後には、`ObjectCreationExpression`です。  構文のビジュアライザーのツリーで、ノードをクリックすると、そのノードによって表されるコードを表示する、エディター ウィンドウ内の構文が強調表示されます。  SyntaxNode サブ型の名前では、c# の文法で使用する名前と一致します。

## <a name="creating-the-analyzer-project"></a>アナライザー プロジェクトを作成します。

メイン メニューから選択**ファイル&#124;新規&#124;プロジェクト.**.**新しいプロジェクト**ダイアログで、 **c#** プロジェクト、左側のナビゲーション バーで、拡張性を選択し、右側のペインで選択、**で修正するコード分析**プロジェクトテンプレートです。  名前を入力し、ダイアログ ボックスを確認します。

テンプレートは、DiagnosticAnalyzer.cs ファイルを開きます。  エディター バッファー タブを選択します。このファイルには、アナライザー クラス (形成されるプロジェクトを指定した名前から) から派生した`DiagnosticAnalyzer`(Roslyn API 型)。  新しいクラスが、`DiagnosticAnalyzerAttribute`アナライザーを宣言することが設定されて、c# 言語に関連するコンパイラを検出し、アナライザーを読み込みます。

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

C# のコードを対象とする Visual Basic を使用して、アナライザーを実装して、その逆です。  アナライザーが、1 つの言語またはその両方を対象かどうかを選択する DiagnosticAnalyzerAttribute でより重要になります。  言語の詳細なモデリングを必要とする高度なアナライザーは、1 つの言語を対象のみできます。  場合、アナライザーでは、たとえば、のみチェック型の名前またはパブリック メンバーの名前は、Roslyn は、Visual Basic および c# の間で共通の言語モデルを使用する可能性があります。  たとえば、FxCop にクラスを実装する警告<xref:System.Runtime.Serialization.ISerializable>、クラスはありません、<xref:System.SerializableAttribute>属性は、言語に依存しないし、Visual Basic および c# のコードで動作します。

## <a name="initalizing-the-analyzer"></a>品詞アナライザー

 少し下へスクロール、`DiagnosticAnalyzer`を表示するクラス、`Initialize`メソッドです。  コンパイラは、アナライザーをアクティブ化するときに、このメソッドを呼び出します。  メソッドは、`AnalysisContext`コンテキスト情報を取得し、分析するコードの種類のイベント用のコールバックを登録する、アナライザーをできるようにするオブジェクト。

```csharp
public override void Initialize(AnalysisContext context) {}

```

このメソッドと型"のコンテキストでします"の新しい行を開く IntelliSense コンプリート リストを表示します。  多数ある、コンプリート リストで確認できます`Register...`さまざまな種類のイベントを処理するメソッド。  たとえば、1 つ目、 `RegisterCodeBlockAction`、中かっこの間にコードでは通常、ブロックのコードにコールバックします。  ブロックを登録するもを呼び出して、コード、フィールド、属性に渡された値、または省略可能なパラメーターの値の初期化子にします。

別の例として`RegisterCompilationStartAction`、さまざまな場所にわたって状態を収集する必要がある場合に有用なコンパイルの開始時、コードにコールバックします。  作成、データ構造を使用すると、すべてのシンボルを収集して、アナライザーがいくつかの構文またはシンボルの戻る呼び出されるたびに、データ構造で各場所に関する情報を保存することができます。  コンパイル終了のためコールバックしている、ときに、保存した、たとえば、各からコードを使用してシンボルを報告するすべての場所を分析できます`using`ステートメントです。

使用して、**構文ビジュアライザー**コンパイラ、ObjectCreationExpression を処理するときに呼び出されることを学習しました。  コールバックを設定するには、このコードを使用します。

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

構文ノードおよびオブジェクト作成構文ノードだけのフィルターを登録します。  慣例によりは、アナライザー作成者は、ステートレスなアナライザーを保護するのに役立ちますアクションを登録するときに、ラムダを使用できます。  Visual Studio の機能を使用する**使用法から生成**を作成する、`AnalyzeObjectCreation`メソッドです。  これは、コンテキスト パラメーターの正しい型を生成するすぎるします。

## <a name="setting-properties-for-users-of-your-analyzer"></a>アナライザーのユーザーのプロパティの設定

表示されるよう、アナライザー Visual Studio UI で適切に、検索し、アナライザーを識別するコードの次の行を変更します。

```csharp
internal const string Category = "Naming";
```

Change `"Naming"` to `"API Guidance"`.

次に検索して開く、`Resources.resx`を使用して、プロジェクト内のファイル、**ソリューション エクスプ ローラー**です。  説明は、アナライザー、タイトルなどにことができます。これらのすべての値を変更することができます`"Don't use ImmutableArray<T> constructor"`今のところです。  文字列の書式設定 ({0}、{1} など)、文字列に引数を配置することができ、後で呼び出すときに`Diagnostic.Create()`を指定できます、`params`渡される引数の配列。

## <a name="analyzing-an-object-creation-expression"></a>オブジェクトの作成式の分析

`AnalyzeObjectCreation`メソッドは、コード アナライザー framework によって提供されるコンテキストの別の種類を使用します。  Initialize メソッドの`AnalysisContext`アナライザーを設定する操作のコールバックを登録することができます。  `SyntaxNodeAnalysisContext`、たとえばには、`CancellationToken`の周囲に渡すことができます。  ユーザーは、エディターで入力を開始する場合、Roslyn は作業を保存し、パフォーマンスが向上する実行中のアナライザーをキャンセルします。  別の例としては、このコンテキストは、オブジェクトの作成の構文ノードを返すノード プロパティを持ちます。

構文ノードのアクションをフィルター処理する型が前提としているノードを取得します。

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launching-visual-studio-with-your-analyzer-the-first-time"></a>最初に、アナライザーを使用して Visual Studio を起動します。

構築し、アナライザーを実行する Visual Studio を起動 (キーを押して**f5 キーを押して**)。  スタートアップ プロジェクトであるため、**ソリューション エクスプ ローラー**コードと VSIX、コード ビルドを実行して、VSIX プロジェクトは、その VSIX のインストールを使って Visual Studio を起動します。  この方法で Visual Studio を起動するときに起動され、個別のレジストリ ハイブで Visual Studio のメイン使用ない影響されることは、テスト インスタンス アナライザーの構築中にできるようにします。  初めてこのようにしてを起動する Visual Studio では、いくつかの初期化と最初に起動した Visual Studio インストール後に似ています。

コンソール プロジェクトを作成し、コンソール アプリケーションの Main メソッドに配列のコードを入力します。

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

使用してコードの行`ImmutableArray`波線があるため、変更できない NuGet パッケージを取得し、追加する必要があります、`using`ステートメントをコードにします。  プロジェクト ノードの右のポインター ボタンを押して、**ソリューション エクスプ ローラー**選択**NuGet パッケージの管理.**.NuGet マネージャーで、検索ボックスに「変更不可」を入力し、項目"System.Collections.Immutable"を選択 ("Microsoft.Bcl.Immutable"を選択しないでください) で、左側と右側のウィンドウで [インストール] ボタンを押します。  パッケージをインストールするには、プロジェクト参照への参照が追加されます。

下の赤い波線が引き続き表示`ImmutableArray`、したがってその識別子とキーを押してにキャレットを配置**CTRL + です。** (ピリオド) で推奨される修正プログラムのメニューを表示し、適切な追加`using`ステートメントです。

**すべてを保存して閉じる**クリーンな状態を続行するにここでは Visual Studio の 2 番目のインスタンス。

## <a name="finishing-the-analyzer-using-edit-and-continue"></a>フィニッシュ アナライザーを使用して、エディット コンティニュ

Visual Studio の最初のインスタンスの先頭にブレークポイントを設定、`AnalyzeObjectCreation`キーを押してメソッド**F9**最初の行にカーソルをします。

使用して、アナライザーを起動**f5 キーを押して**、Visual Studio の 2 番目のインスタンスで最後に作成したコンソール アプリケーションを再度開いてとします。

Roslyn コンパイラ オブジェクトの作成式を確認し、アナライザーと呼ばれるため、ブレークポイントで Visual Studio の最初のインスタンスに戻ります。

**オブジェクトの作成 ノードを取得します。** ステップ オーバーを設定する行、`objectCreation`キーを押して変数**F10**、し、、**イミディ エイト ウィンドウ**式の評価`"objectCreation.ToString()"`です。  変数が指す構文ノードが、コードを参照してください`"new ImmutableArray<int>()"`、何を探しています。

**ImmutableArray を get < T\>型オブジェクト。** 作成される型が ImmutableArray を確認する必要があります。  最初に、この型を表すオブジェクトを取得します。  正しい型では正確にし、ToString() から文字列を比較しないようにする、セマンティック モデルを使用して型をチェックします。  次の関数の終了時のコード行に入力します。

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

ジェネリック型では、バッククォート (') でメタデータとジェネリック パラメーターの数を指定します。  これは、"... 表示されない理由Immutablearray を\<T >"のメタデータ名にします。

セマンティック モデルでは、シンボル、データ フロー、変数の有効期間などに関する質問を投稿するためにさまざまな方法で便利ですがあります。Roslyn は、さまざまなエンジニア リング理由 (パフォーマンス、誤ったコードなどのモデリング)、セマンティック モデルから構文ノードを区分します。  正確な比較のための参照に含まれている情報を検索するコンパイル モデルが必要です。

エディター ウィンドウの左側にある黄色の実行のポインターをドラッグできます。  設定する行までドラッグ、`objectCreation`変数とステップ オーバー、新しい行を使用してコードの**F10**です。  マウス ポインターを変数に合わせる場合`immutableArrayOfType`、セマンティック モデルで見つかったこと正確な型を参照してください。

**オブジェクトの作成式の型を取得します。** "Type"は、この記事で、いくつかの方法で使用されるが、つまり"新しい Foo"を持つかどうか、式では、Foo のモデルを取得する必要があります。  ImmutableArray がかどうかか、オブジェクトの作成式の種類を取得する必要があります\<T > 型。  セマンティック モデルを使用して、もう一度オブジェクトの作成式で型のシンボル (ImmutableArray) のシンボル情報を取得します。  次の関数の終了時のコード行に入力します。

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

アナライザーが不完全または不正確のコード エディターのバッファーで処理する必要があるため (などがありますが、見つからない`using`ステートメント) を確認する必要があります`symbolInfo`されている`null`です。  分析が完了するシンボル情報オブジェクトから名前付きの型 (INamedTypeSymbol) を取得する必要があります。

**型を比較します。** (オープン ジェネリック型) から構築はどのような型のシンボル情報のクエリを実行しその取得した結果を比較しております、T のオープン ジェネリック型があるため、コードの型は、具体的なジェネリック型`immutableArrayOfTType`です。  メソッドの最後で次のように入力します。

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**診断を報告します。** 診断を報告することは簡単です。  初期化メソッドの前に定義されているプロジェクト テンプレートで作成する規則を使用するとします。  置換するルールが初期化されている行を変更するには、コードでこのような状況がエラーのため、 `DiagnosticSeverity.Warning` (緑の波線) と`DiagnosticSeverity.Error`(赤の波線)。  ルールの残りの部分は、チュートリアルの最初の近くで編集するリソースを初期化します。  また、オブジェクトの作成式の型指定の場所であると、波線の場所を報告する必要があります。  このコードを入力、`if`ブロック。

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

関数は、(異なる書式、) 次のようになります。

```csharp
private void AnalyzeObjectCreation(SyntaxNodeAnalysisContext context)
{
    var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
    var immutableArrayOfTType =
        context.SemanticModel
               .Compilation
               .GetTypeByMetadataName(
                   "System.Collections.Immutable.ImmutableArray`1");
    var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as
        INamedTypeSymbol;
    if (symbolInfo != null &&
        symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
    {
        context.ReportDiagnostic(
            Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
    }
}
```

ようにすることができます、アナライザー作業を参照してください (Visual Studio の最初のインスタンスを返すことを停止) は、ブレークポイントを削除します。  メソッド、およびキーを押しての先頭に、実行ポインターをドラッグして**f5 キーを押して**の実行を続行します。  Visual Studio の 2 番目のインスタンスに切り替えるし、コンパイラは、コードを調べる、もう一度開始、アナライザーが呼び出されます。  下の波線を表示できます`ImmutableType<int>`です。

## <a name="adding-a-code-fix-for-the-code-issue"></a>コードの問題の「コード修正」を追加します。

開始する前に、Visual Studio の 2 番目のインスタンスを閉じて (は開発している、アナライザー) Visual Studio の最初のインスタンスでデバッグを停止します。

**新しいクラスを追加します。** ソリューション エクスプ ローラーでプロジェクト ノードのショートカット メニュー (右のポインター ボタン) を使用して、新しい項目の追加を選択します。  というクラスを追加`BuildCodeFixProvider`です。  このクラスから派生する必要がある`CodeFixProvider`、使用する必要があります**CTRL + です。** 正しいを追加するコードの修正プログラムを起動するには、(ピリオド)`using`ステートメントです。  またこのクラスで注釈を付ける必要があります`ExportCodeFixProvider`属性、およびするが、追加する必要が、`using`ステートメントを解決するのには、`LanguageNames`列挙型。  これで次のコードにクラス ファイルが必要です。

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}

```

**派生メンバーを消去します。** ここで、識別子に、エディターのキャレットを配置`CodeFixProvider`とキーを押します**CTRL + です。** (ピリオド) をこの抽象基本クラスの実装をスタブです。  プロパティとメソッドが生成されます。

**プロパティを実装します。** 入力、`FixableDiagnosticIds`プロパティの`get`を次のコードの本文。

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn は診断をまとめるし、これらの識別子では、単なる文字列を照合することによって修正します。  プロジェクト テンプレートが、診断の ID を生成しを自由に変更します。  プロパティ内のコードには、アナライザー クラスからの ID だけを返します。

**RegisterCodeFixAsync メソッドは、コンテキストを受け取ります。** コンテキストは、コードを修正、複数の診断に適用するか、またはでした問題がある 1 つ以上のコード行のために重要です。  「コンテキスト」を入力する場合 メソッドの本文に、IntelliSense コンプリート リストはメンバーを表示するいくつかに便利です。  修正プログラムをキャンセルしよう何かをチェックできる CancellationToken メンバーが存在します。  多数の便利なメンバーがあり、プロジェクトとソリューションのモデル オブジェクトを取得することができますをドキュメント メンバーが存在します。  開始される Span メンバー コードの場所の末尾を指定して、診断を報告したときにします。

**ある非同期メソッドを作成します。** 最初に行う必要はある生成されたメソッドの宣言を修正、`async`メソッドです。  抽象クラスの実装をスタブのコード修正が含まれていない、`async`キーワード、メソッドが返す場合でも、`Task`です。

**構文ツリーのルートを取得します。** 変更内容を新しい構文ツリーを生成するために必要なコードを変更するのには、コードの修正します。  必要があります、`Document`を呼び出してコンテキストから`GetSyntaxRootAsync`です。  これは、可能性のあるディスクからファイルを取得する、解析、およびその Roslyn コード モデルの構築を含めて、構文ツリーを取得する不明な作業があるので、非同期メソッドです。  使用する、この期間中に、Visual Studio UI が応答する必要があります`async`を有効にします。  次のように、メソッドのコードの行に置き換えます。

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**問題のノードが見つかりません。** コンテキストの範囲が、コードを変更する必要がある可能性がありますいないを見つけたら、ノードを渡します。  報告された診断では、(、波線が属していた)、型識別子の範囲だけが指定されていますが、オブジェクト全体の作成式を交換する必要がありますを含め、`new`先頭と末尾のかっこにキーワードを指定します。  メソッドに次のコードを追加 (を使用して**CTRL + です。** 追加する、`using`の声明`ObjectCreationExpressionSyntax`)。

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**電球 UI のコード修正を登録します。** コードの修正を登録するときに Roslyn は自動的に Visual Studio 電球 UI に接続されます。  エンドユーザーが使用できる表示**CTRL + です。** アナライザーが不良を示す波線と (ピリオド)`ImmutableArray<T>`コンス トラクターを使用します。  コードの修正プログラムのプロバイダーは、問題がある場合にのみ実行するため、探していたオブジェクトの作成式がある場合を想定することができます。  末尾に次のコードを追加することで、新しいコードを修正を登録するコンテキスト パラメーターから`RegisterCodeFixAsync`メソッド。

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

識別子に、エディターのキャレットを配置する必要があります`CodeAction`を使用して**CTRL + です。** 適切なを追加するには、(ピリオド)`using`この種類のステートメント。

内のエディターのキャレットを配置、`ChangeToImmutableArrayEmpty`識別子と使用**CTRL + です。** このメソッドのスタブを生成をもう一度します。

追加したこの最後のコード スニペットでは、コードの修正を登録を渡すことによって、`CodeAction`と検出された問題の種類の診断の ID。  この例でが 1 つだけのこのコードを提供する診断の ID が修正ためだけの診断の Id の配列の最初の要素を渡すことができます。  作成するときに、 `CodeAction`、電球 UI がコード修正の説明として使用するテキストに渡します。  CancellationToken を取得し、新しいドキュメントを返す関数も渡します。  この新しいドキュメントを呼び出すパッチが適用されたコードを含む新しい構文ツリーにある`ImmutableArray.Empty`です。  このコード スニペットでは、ラムダを使用するので、オブジェクト作成ノードとコンテキストのドキュメントを閉じることができます。

**新しい構文ツリーを構築します。** `ChangeToImmutableArrayEmpty`メソッドがスタブが、前に生成したコードの行を入力してください:`ImmutableArray<int>.Empty;`です。  構文のビジュアライザーのツール ウィンドウをもう一度表示する場合、この構文は SimpleMemberAccessExpression ノードが表示できます。  このメソッドを作成して、新しいドキュメントに返す必要があります。

最初の変更を`ChangeToImmutableArrayEmpty`を追加するには`async`する前に`Task<Document>`コード ジェネレーターはメソッドを非同期にする必要がありますを想定できないためです。

メソッドに次のように見えるように、本文を次のコードを入力します。

```csharp
private async Task<Document> ChangeToImmutableArrayEmpty(
    ObjectCreationExpressionSyntax objectCreation, Document document,
    CancellationToken c)
{
    var generator = SyntaxGenerator.GetGenerator(document);
    var memberAccess =
        generator.MemberAccessExpression(objectCreation.Type, "Empty");
    var oldRoot = await document.GetSyntaxRootAsync(c);
    var newRoot = oldRoot.ReplaceNode(objectCreation, memberAccess);
    return document.WithSyntaxRoot(newRoot);
}
```

エディターのキャレットを配置する必要があります、`SyntaxGenerator`識別子と使用**CTRL + です。** 適切なを追加するには、(ピリオド)`using`この種類のステートメント。

このコードで使用`SyntaxGenerator`、新しいコードを構築するために役立ちます型です。  コードの問題には、ドキュメントのジェネレーターを取得後`ChangeToImmutableArrayEmpty`呼び出し`MemberAccessExpression`メンバーにアクセスする必要のある型を渡すこと、およびメンバーの名前を文字列として渡します。

次に、メソッドは、ドキュメントのルートをフェッチし、コードがこの呼び出しを待機し、キャンセル トークンを渡します一般的なケースで任意の作業があります、ためです。  Roslyn コード モデルは不変であると同じように .NET の文字列です。文字列を更新するときに、戻り値、新しい文字列オブジェクトを取得します。  呼び出すと`ReplaceNode`、新しいルート ノードが返されます。  (変更可能ではない) ために、構文ツリーのほとんどが共有されるが、`objectCreation`ノードが置き換え、`memberAccess`ノード、だけでなく、構文ツリーのルートまでのすべての親ノードです。

## <a name="trying-your-code-fix"></a>コードの修正しようとしています。

これでキーを押します**f5 キーを押して**を Visual Studio の 2 番目のインスタンスで、アナライザーを実行します。  以前に使用したコンソール プロジェクトを開きます。  これで、表示、新しいオブジェクトの作成式が、電球が表示されます`ImmutableArray<int>`です。  キーを押す場合**CTRL + です。** (ピリオド)、修正、コードが表示されます、電球 UI で、自動的に生成されたコードの違いにプレビューが表示されます。  Roslyn はこれを作成します。

**Pro ヒント:** 、Visual Studio の 2 番目のインスタンスを起動して、コードの修正プログラムと電球が表示されない場合、Visual Studio コンポーネント キャッシュをクリアする必要があります。  キャッシュをクリアする強制的に Visual Studio で Visual Studio は、最新コンポーネントを選択し、必要がありますので、コンポーネントを再度確認します。  最初に、Visual Studio の 2 つ目のインスタンスをシャット ダウンします。  エクスプ ローラーで、ディレクトリに移動し、ユーザー (c:\users\\< userid\>) AppData\Local\Microsoft\VisualStudio\14.0Roslyn を見つけて\\です。  このディレクトリでは、ComponentModelCache のサブディレクトリを削除します。  「14」の変更をバージョンごとに Visual Studio とします。

## <a name="talk-video-and-finish-code-project"></a>トーク ビデオとコード プロジェクトの完了

この例の開発し、説明を表示できますでさらに[このトーク](http://channel9.msdn.com/events/Build/2015/3-725)です。  作業アナライザーとビルド手順について説明する、説明します。

すべての終了コードを確認できます[ここ](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)です。  DoNotUseImmutableArrayCollectionInitializer と DoNotUseImmutableArrayCtor サブ フォルダーでは、問題と、Visual Studio 電球 UI に表示されるコード修正を実装する c# ファイルを検索するための c# ファイルがあります。  メモ、終了コードが ImmutableArray をフェッチを回避する少し多くの抽象化\<T > オブジェクトを何度も入力します。  使用可能なコンテキスト型のオブジェクトを保存する入れ子にされた登録済みのアクションを使用するたびにサブ操作 (オブジェクトの作成を分析し、コレクションの初期化を分析) を実行します。

## <a name="see-also"></a>関連項目

* [\\\Build 2015 講演](http://channel9.msdn.com/events/Build/2015/3-725)
* [GitHub でコードが完了しました](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [アナライザーの 3 種類にグループ化、GitHub のいくつかの例](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [GitHub OSS サイトでは、その他のドキュメント](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [GitHub の Roslyn アナライザーを使用して実装 FxCop 規則](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
