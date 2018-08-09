---
title: Roslyn アナライザーと ImmutableArrays 用コード認識ライブラリ |Microsoft Docs
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
ms.openlocfilehash: ad8f58e1d576a738c17095b6306261964e448651
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637722"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Roslyn アナライザーと ImmutableArrays 用コード認識ライブラリ

[.NET コンパイラ プラットフォーム](https://github.com/dotnet/roslyn)("Roslyn") を使用して、コードに対応したライブラリを作成できます。  コードに対応したライブラリでは、またはエラーを回避する最善の方法で使用できる機能とライブラリを使用するためのツール (Roslyn アナライザー) を提供します。  このトピックでは、現実の世界を使用する場合は、一般的なエラーをキャッチする Roslyn アナライザーを構築する方法、 [System.Collections.Immutable](https://www.nuget.org/packages/System.Collections.Immutable) NuGet パッケージ。  この例では、アナライザーが見つけたコードの問題のコード修正を提供する方法も示します。  ユーザーは、Visual Studio 電球 UI でのコード修正を参照してくださいし、コードの修正プログラムを自動的に適用できます。

## <a name="get-started"></a>作業開始

この例をビルドするには、次が必要です。

* Visual Studio 2015 (Express Edition されません) またはそれ以降のバージョン。  無料で使用できます[Visual Studio Community エディション](https://visualstudio.microsoft.com/vs/community/)
* [Visual Studio SDK](../extensibility/visual-studio-sdk.md)します。  確認することも、Visual Studio をインストールするときに**Visual Studio Extensibility Tools** **一般的なツール**と同時に、SDK をインストールします。  既に Visual Studio をインストールする場合、メイン メニューに移動してこの SDK をインストールすることができますもする**ファイル** > **新規** > **プロジェクト**、選択**c#** で、左側のナビゲーション ウィンドウで、選択して、 **Extensibility**します。  選択した場合、"**Visual Studio 機能拡張ツールをインストール**"階層リンクのプロジェクト テンプレートを求められますをダウンロードして、SDK をインストールします。
* [.NET コンパイラ プラットフォーム ("Roslyn") SDK](http://aka.ms/roslynsdktemplates)します。  メイン メニューに移動して、この SDK をインストールすることも**ファイル** > **新規** > **プロジェクト**選択、 **c#** 左側のナビゲーション ウィンドウで、選択して、 **Extensibility**します。  選択した場合"**.NET コンパイラ プラットフォーム SDK をダウンロードして**"階層リンクのプロジェクト テンプレートを求められますをダウンロードして、SDK をインストールします。  この SDK には、 [Roslyn Syntax Visualizer](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer)します。  この非常に便利なツールでは、どのようなコード モデルの種類を把握する必要があります内で検索アナライザーです。  特定のコード モデルの種類のコードは、のみ必要な場合に実行し、関連するコードを分析のみに集中できますので、コードにアナライザーのインフラストラクチャは呼び出し。

## <a name="whats-the-problem"></a>何がそんなに問題ですか。

ImmutableArray を提供するライブラリを想像してみてください (たとえば、 <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>) をサポートします。  C# 開発者には、多数の .NET 配列の使用経験があります。  ただし、実装で使用される ImmutableArrays と最適化の手法の性質上、c# 開発者 intuitions、ライブラリのユーザーが、破損したコードの記述を次に示すように。  さらに、ユーザーはこれで .NET を使用した Visual Studio を使用する高品質なエクスペリエンスは、実行時までのエラー表示されません。

ユーザーは、次のようなコードの記述に慣れています。

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

後続の行のコードをコピーする空の配列を作成して、コレクション初期化子構文を使用して c# 開発者にとって非常に馴染みのあります。  ただし、同じ書き込み ImmutableArray、用のコードがクラッシュした実行時に。

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

最初のエラーは、ImmutableArray 実装の構造体を使用して、基になるデータ ストレージをラップするためです。 構造体は、パラメーターなしコンス トラクターを持つ必要がありますように`default(T)`式は、すべての構造体を返すことができます 0 または null のメンバー。  コードにアクセスするときに`b1.Length`、ImmutableArray 構造体の基になる記憶域配列がないために、実行時の null がエラーを逆参照があります。  空の ImmutableArray を作成する正しい方法は、`ImmutableArray<int>.Empty`します。

に、コレクション初期化子を含むエラーが発生、`ImmutableArray.Add`メソッドはこのメソッドを呼び出すたびに新しいインスタンスを返します。  ImmutableArrays 決して変更ので、新しい要素を追加するときに、オブジェクトを取得するバックアップ新しい ImmutableArray (これは以前から存在 ImmutableArray とパフォーマンス上の理由からストレージを共有する可能性があります)。  `b2`呼び出す前に、最初の ImmutableArray を指す`Add()`の 5 回`b2`既定 ImmutableArray が。  エラーを逆参照呼び出しの長さにも null でクラッシュします。  手動で追加の呼び出しは、使用することがなく、ImmutableArray を初期化する正しい方法`ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`します。

## <a name="find-relevant-syntax-node-types-to-trigger-your-analyzer"></a>関連する構文アナライザーをトリガーするノードの種類を検索します。

 アナライザーをビルドするには、最初見つけ出す SyntaxNode の種類確認する必要があります。 起動、 **Syntax Visualizer**  メニューから**ビュー** > **その他の Windows** > **Roslyn Syntax Visualizer**.

宣言する行のエディターのキャレットを配置する`b1`します。  表示では、Syntax Visualizer を示しています、`LocalDeclarationStatement`構文ツリーのノード。  このノードには、`VariableDeclaration`がさらに、`VariableDeclarator`がさらに、 `EqualsValueClause`、最後には、`ObjectCreationExpression`します。  Syntax Visualizer ツリーのノードをクリックすると、そのノードによって表されるコードを表示するエディター ウィンドウで構文が強調表示されます。  SyntaxNode のサブ型の名前では、c# の文法で使用される名前と一致します。

## <a name="create-the-analyzer-project"></a>アナライザー プロジェクトを作成します。

メイン メニューから選択**ファイル** > **新規** > **プロジェクト**します。  **新しいプロジェクト**ダイアログで、 **c#** 、左側のナビゲーション バーでプロジェクトを選択**拡張**、右側のウィンドウで次のように選択します、 **Analyzer with。コードの修正プログラム**プロジェクト テンプレート。  名前を入力し、ダイアログ ボックスを確認します。

テンプレートが表示されます、 *DiagnosticAnalyzer.cs*ファイル。  エディター バッファー タブを選択します。このファイルには、アナライザー クラス (形成されたプロジェクトを指定した名前から) から派生した`DiagnosticAnalyzer`(Roslyn API の種類)。  新しいクラスが、`DiagnosticAnalyzerAttribute`コンパイラを検出し、アナライザーを読み込むように c# 言語に関連するが、アナライザーを宣言することです。

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

C# のコードを対象とする Visual Basic を使用して、アナライザーを実装する、またはその逆です。  アナライザーが 1 つの言語またはその両方を対象とするかどうかを選択する DiagnosticAnalyzerAttribute でより重要になります。  言語の詳細なモデリングを必要とするアナライザーをより高度な 1 つの言語のみ対象にできます。  場合、アナライザーは、たとえば、のみチェック型名またはパブリック メンバーの名前は、Roslyn は、Visual Basic および c# で一般的な言語モデルを使用する可能性があります。  たとえば、FxCop は警告クラスを実装する<xref:System.Runtime.Serialization.ISerializable>、クラスはありません、<xref:System.SerializableAttribute>属性は、言語に依存しないし、Visual Basic および c# のコードで動作します。

## <a name="initalize-the-analyzer"></a>アナライザーの初期化

 下へ少しスクロール、`DiagnosticAnalyzer`クラスを参照して、`Initialize`メソッド。  コンパイラは、アナライザーをアクティブ化する際に、このメソッドを呼び出します。  メソッドには、`AnalysisContext`アナライザー コンテキスト情報を取得して、分析するコードの種類のイベントのコールバックを登録できるようにするオブジェクト。

```csharp
public override void Initialize(AnalysisContext context) {}

```

このメソッドと型「コンテキスト」で新しい行を開く IntelliSense の入力候補一覧を確認します。  多数あります入力候補一覧に表示できる`Register...`さまざまな種類のイベントを処理するメソッド。  たとえば、1 つ目、 `RegisterCodeBlockAction`、中かっこの間のコードでは、通常は、ブロックのコードにコールバックします。  ブロック用の登録もコールバックをコードに、フィールド、属性に渡された値やオプションのパラメーターの値の初期化子にします。

別の例として`RegisterCompilationStartAction`、さまざまな場所経由で状態を収集する必要がある場合に便利ですが、コンパイルの開始時、コードにコールバックします。  作成、データ構造と答えると、使用すると、すべてのシンボルを収集して、アナライザーがいくつかの構文やシンボル、戻る呼び出されるたびに、データ構造で各場所に関する情報を保存することができます。  コンパイル終了コールバックしている、ときに、保存した、たとえば、各からコードを使用して、どのようなシンボルを報告するすべての場所を分析できます`using`ステートメント。

使用して、 **Syntax Visualizer**コンパイラ、ObjectCreationExpression を処理するときに呼び出されることを学習しました。  コールバックを設定するには、このコードを使用します。

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

構文ノードとオブジェクトの作成の構文ノードのみにフィルターを登録します。  規則により、アナライザーをステートレスようにすることが、アクションを登録するときに、アナライザーの作成者は、ラムダを使用します。  Visual Studio の機能を使用する**使用法から生成**を作成する、`AnalyzeObjectCreation`メソッド。  これは、コンテキスト パラメーターの正しい型を生成するすぎるします。

## <a name="set-properties-for-users-of-your-analyzer"></a>アナライザーのユーザーのプロパティを設定します。

表示されるよう、アナライザー Visual Studio UI で適切に、検索し、アナライザーを識別するためにコードの次の行の変更します。

```csharp
internal const string Category = "Naming";
```

変更`"Naming"`に`"API Guidance"`します。

次に検索して開く、 *Resources.resx*を使用して、プロジェクト ファイル、**ソリューション エクスプ ローラー**します。  アナライザー、タイトルなどの説明を配置することができます。これらのすべての値を変更することができます`"Don't use ImmutableArray<T> constructor"`今のところです。  文字列引数を書式設定文字列を配置することができます ({0}、{1}など)、し、呼び出すときに後で`Diagnostic.Create()`を指定することができます、`params`渡される引数の配列。

## <a name="analyze-an-object-creation-expression"></a>オブジェクト作成式を分析します。

`AnalyzeObjectCreation`メソッドは、異なる種類のコード アナライザーのフレームワークから提供されたコンテキストを受け取ります。  `Initialize`メソッドの`AnalysisContext`アナライザーを設定する操作のコールバックを登録することができます。  `SyntaxNodeAnalysisContext`などが、`CancellationToken`の周囲に渡すことができます。  ユーザーは、エディターで入力を開始する場合、Roslyn は作業を保存し、パフォーマンスが向上するアナライザーを実行中を取り消します。  このコンテキストでは、別の例として、オブジェクトの作成の構文ノードを返すノード プロパティがあります。

構文ノードのアクションをフィルター処理する型が前提としているノードを取得します。

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launch-visual-studio-with-your-analyzer-the-first-time"></a>最初に、アナライザーを使用して Visual Studio の起動します。

構築とアナライザーを実行して Visual Studio を起動 (キーを押して**F5**)。  スタートアップ プロジェクトのため、**ソリューション エクスプ ローラー**コード ビルドを実行して、コードと、VSIX、VSIX プロジェクトは、次をインストールする VSIX と共に Visual Studio を起動します。  この方法で Visual Studio を起動するときにアナライザーのビルド中に、Visual Studio の主な使用が、テスト インスタンスによって影響されないように、個別のレジストリ ハイブな起動されます。  初めてこの方法を起動する Visual Studio ではいくつかの初期化を最初に起動したときに Visual Studio にインストールした後に似ています。

コンソール プロジェクトを作成し、コンソール アプリケーションの Main メソッドに配列のコードを入力します。

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

使用したコードの行`ImmutableArray`不変の NuGet パッケージを取得し、追加する必要があるため、波線がある、`using`ステートメントをコードにします。  プロジェクト ノードを右のポインター ボタンを押して、**ソリューション エクスプ ローラー**選択**NuGet パッケージの管理**します。  NuGet マネージャーでは、"Immutable"を検索 ボックスに入力し、項目を選択**System.Collections.Immutable** (選択しないでください**Microsoft.Bcl.Immutable**) で、左側のウィンドウとキーを押して、 **インストール**右側のウィンドウでボタンをクリックします。  パッケージをインストールすると、プロジェクト参照への参照が追加されます。

下の赤い波線が引き続き表示`ImmutableArray`、ためキーを押してその識別子にキャレットを配置**Ctrl**+**します。** (ピリオド) で推奨される修正プログラムのメニューを表示し、適切な追加`using`ステートメント。

**すべてを保存して閉じる**続行クリーンな状態で皆さんをここでは Visual Studio の 2 番目のインスタンス。

## <a name="finish-the-analyzer-using-edit-and-continue"></a>編集を使用して、アナライザーを終了し、続行

Visual Studio の最初のインスタンスの先頭にブレークポイントを設定、`AnalyzeObjectCreation`キーを押してメソッド**F9**最初の行にキャレットをします。

使用して、アナライザーを起動**F5**、Visual Studio の 2 番目のインスタンスで最後に作成したコンソール アプリケーションを再度開きます。

Roslyn コンパイラのオブジェクト作成式を見たし、アナライザーと呼ばれるため、ブレークポイントで Visual Studio の最初のインスタンスに戻ります。

**オブジェクトの作成のノードを取得します。** 設定する行の上の手順、`objectCreation`キーを押して変数**F10**、し、**イミディ エイト ウィンドウ**式の評価`"objectCreation.ToString()"`します。  変数が指す構文ノードが、コードを参照してください`"new ImmutableArray<int>()"`、何を探しています。

**取得 ImmutableArray < T\>型オブジェクト。** 作成される型が ImmutableArray を確認する必要があります。  最初に、この型を表すオブジェクトを取得します。  正確に右の型があるし、元の文字列を比較しないことを確認して、セマンティック モデルを使用して型をチェックする`ToString()`します。  次の関数の最後のコード行を入力します。

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

ジェネリック型では、バッククォート (') を使用してメタデータと、ジェネリック パラメーターの数を指定します。  "... 表示されない理由します。ImmutableArray\<T >"でメタデータの名前。

セマンティック モデルでは、記号、データ フロー、変数の有効期間などに関する質問をするために多くの便利なことがあります。Roslyn では、さまざまな理由でエンジニア リング (パフォーマンス、エラー コードなどのモデリング)、セマンティック モデルから構文ノードを分離します。  コンパイル モデルの正確な比較参照に含まれている情報を確認します。

エディター ウィンドウの左側にある黄色の実行のポインターをドラッグできます。  設定する行までドラッグ、`objectCreation`変数とステップ オーバー、新しい行を使用してコードの**F10**します。  マウス ポインターを変数に合わせる場合`immutableArrayOfType`、セマンティック モデルで見つかったこと正確な型を参照してください。

**オブジェクト作成式の型を取得します。** "Type"は、この記事では、いくつかの方法で使用されますが、つまり、"新しい Foo"があるかどうか、式の Foo のモデルを取得する必要があります。  ImmutableArray をオブジェクト作成式の型を取得する必要がある\<T > 型。  セマンティック モデルを使用して、もう一度オブジェクト作成式で型のシンボル (ImmutableArray) のシンボル情報を取得します。  次の関数の最後のコード行を入力します。

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

アナライザーがエディターのバッファーに不完全なまたは正しくないコードを処理する必要があるため (などがありますが、不足している`using`ステートメント)、確認する必要があります`symbolInfo`される`null`します。  分析が完了するシンボル情報オブジェクトから名前付きの型 (INamedTypeSymbol) を取得する必要があります。

**型を比較します。** (オープン ジェネリック型) から構築型のシンボル情報をクエリし、その結果とを比較する探して T のオープン ジェネリック型があるため、コードの型は、具体的なジェネリック型`immutableArrayOfTType`します。  メソッドの最後で次のコマンドを入力します。

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**診断を報告します。** 診断を報告することは非常に簡単です。  Initialize メソッドの前に定義されているプロジェクト テンプレートで作成する規則を使用するとします。  置換するルールを初期化する行を変更するには、コードでこのような状況がエラーであるため、 `DiagnosticSeverity.Warning` (緑色の波線) と`DiagnosticSeverity.Error`(赤い波線)。  ルールの残りの部分は、チュートリアルの最初の近くで編集するリソースを初期化します。  また、オブジェクト作成 expresssion の型指定の場所であると、波線の場所を報告する必要があります。  このコードを入力、`if`ブロック。

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

関数は必要があります (異なる形式などで) 次のようになります。

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

ブレークポイントを削除、アナライザーの機能を参照してください (および Visual Studio の最初のインスタンスを返すことを停止) できます。  実行ポインターをドラッグして、メソッド、およびキーを押しての先頭に**F5**の実行を続行します。  Visual Studio の 2 番目のインスタンスに切り替えることと、コンパイラはコードをもう一度、調査を開始、アナライザーに呼び出します。  下に波線を表示できます`ImmutableType<int>`します。

## <a name="adding-a-code-fix-for-the-code-issue"></a>コードの問題の「コード修正」の追加

開始する前に、Visual Studio の 2 番目のインスタンスを閉じて (場所、アナライザーを開発している) Visual Studio の最初のインスタンスでのデバッグを停止します。

**新しいクラスを追加します。** プロジェクト ノードのショートカット メニュー (右のポインター ボタン) を使用して、**ソリューション エクスプ ローラー**と新しい項目を追加します。  という名前のクラスを追加`BuildCodeFixProvider`します。  このクラスから派生する必要が`CodeFixProvider`、使用する必要があります**Ctrl**+**します。** (ピリオド) を追加、適切なコードの修正を呼び出す`using`ステートメント。  このクラスを使って注釈を付ける必要があります`ExportCodeFixProvider`属性、およびするが、追加する必要が、`using`ステートメントを解決するのには、`LanguageNames`列挙型。  これで次のコードでクラス ファイルが必要です。

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}

```

**派生メンバーを消します。** ここで、id に、エディターのキャレットを置き`CodeFixProvider`キーを押します**Ctrl**+**します。** (ピリオド) をこの抽象基本クラスの実装をスタブします。  プロパティとメソッドが生成されます。

**プロパティを実装します。** 入力、`FixableDiagnosticIds`プロパティの`get`を次のコードの本文。

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn では、診断をまとめるし、文字列だけでは、これらの識別子を照合することによって修正します。  プロジェクト テンプレートは、診断 ID を生成し、自由に変更します。  プロパティ内のコードは、アナライザー クラスからのみ ID を返します。

**RegisterCodeFixAsync メソッドでは、コンテキストを取得します。** コード修正は、複数の診断に適用できますか、行のコードで問題の 1 つ以上ありますでしたので、コンテキストが重要です。  。「コンテキスト」を入力する場合 メソッドの本文で IntelliSense 入力候補の一覧はメンバーを表示するいくつか便利です。  修正プログラムを取り消したいものを表示するか確認できる CancellationToken メンバーがあります。  多数の便利なメンバーがあり、プロジェクトとソリューションのモデル オブジェクトを取得することができますをドキュメントのメンバーがあります。  開始される Span のメンバーがあるし、コードの場所の末尾では、診断を報告したときに指定されました。

**非同期メソッドを作成します。** 最初に行う必要があるものがある生成されたメソッドの宣言を修正、`async`メソッド。  抽象クラスの実装をスタブするに対してコード修正が含まれていない、`async`キーワード、メソッドが返されます場合でも、`Task`します。

**構文ツリーのルートを取得します。** 変更された新しい構文ツリーを生成するために必要なコードを変更するには、コード修正します。  必要があります、`Document`を呼び出すコンテキストから`GetSyntaxRootAsync`します。  これは、ディスクからファイルを取得する、解析すること、およびその Roslyn コード モデルの構築を含めることも、構文ツリーを取得する不明な作業があるため、非同期メソッドです。  Visual Studio の UI はどのを使用して、この期間中に応答する必要があります`async`有効にします。  次のように、メソッドのコードの行に置き換えます。

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**問題のノードが見つかりません。** コンテキストの範囲がコードを変更する必要がない場合がありますを検索するノードを渡します。  報告された診断では、(、波線が属していた) 型識別子の範囲のみが提供されているが、オブジェクト全体の作成式を置き換える必要があるなど、`new`先頭と末尾のかっこにキーワードを指定します。  メソッドに次のコードを追加 (および使用**Ctrl**+**します。** 追加する、`using`ステートメント`ObjectCreationExpressionSyntax`)。

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**電球の UI のコード修正を登録します。** コード修正を登録するときに Roslyn は自動的に Visual Studio 電球 UI に接続されます。  エンドユーザーが使用できる表示**Ctrl**+**します。** アナライザー波線を表示する、無効な場合 (期間)`ImmutableArray<T>`コンス トラクターを使用します。  コード修正プロバイダーは、問題がある場合にのみ実行するため、探してオブジェクト作成式があると想定することができます。  末尾に次のコードを追加することで、新しいコード修正を登録するコンテキスト パラメーターから`RegisterCodeFixAsync`メソッド。

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Id に、エディターのキャレットを配置する必要がある`CodeAction`を使用して**Ctrl**+**します。** 適切なを追加するには、(ピリオド)`using`この種類のステートメント。

内のエディターのキャレットを配置し、`ChangeToImmutableArrayEmpty`識別子と使用**Ctrl**+**。** するには、このメソッド スタブを生成します。

この最後のコード スニペットを追加したコードの修正プログラムを登録しますを渡すことによって、`CodeAction`と検出された問題の種類の診断の ID。  この例では、1 つしかない診断 ID をこのコードは、修正ため、診断の Id の配列の最初の要素を単に渡すことができます。  作成するときに、 `CodeAction`、電球 UI がコード修正の説明として使用するテキストを渡します。  CancellationToken を受け取り、新しいドキュメントを返す関数も渡します。  新しいドキュメントが呼び出すパッチが適用されたコードを含む新しい構文ツリー`ImmutableArray.Empty`します。  このコード スニペットでは、ラムダを使用するので、オブジェクト作成ノードとコンテキストのドキュメントに閉じることができます。

**新しい構文ツリーを構築します。** `ChangeToImmutableArrayEmpty`メソッドがスタブが以前に生成するコード行を入力します:`ImmutableArray<int>.Empty;`します。  表示する場合、 **Syntax Visualizer**ツール ウィンドウ、もう一度確認できますこの構文は SimpleMemberAccessExpression ノード。  このメソッドを構築して新しい文書を返す必要があります。

最初の変更を`ChangeToImmutableArrayEmpty`を追加するには`async`する前に`Task<Document>`のためコード ジェネレーターが、メソッドが非同期にする必要がありますを想定することはできません。

メソッドに、次のように見えるように、本文を次のコードを入力します。

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

エディターのキャレットを配置する必要があります、`SyntaxGenerator`識別子と使用**Ctrl**+**します。** 適切なを追加するには、(ピリオド)`using`この種類のステートメント。

このコードを使用して`SyntaxGenerator`、これは、また非常に便利な型は、新しいコードを構築するためです。  コードの問題には、ドキュメントのジェネレーターを取得後`ChangeToImmutableArrayEmpty`呼び出し`MemberAccessExpression`メンバーにアクセスする必要のある型を渡すと、メンバーの名前を文字列として渡します。

次に、メソッドは、ドキュメントのルートをフェッチし、任意の作業の一般的なケースがあります、ため、コードはこの呼び出しを待機し、キャンセル トークンを渡します。  Roslyn コード モデルは不変であり、.NET の文字列の操作など文字列を更新するときに、代わりに、新しい文字列オブジェクトを取得します。  呼び出すと`ReplaceNode`、新しいルート ノードを取得します。  (変更可能でない) ために、構文ツリーのほとんどが共有されるが、`objectCreation`はノードに置き換え、`memberAccess`ノード、だけでなく、構文ツリーのルートまでのすべての親ノード。

## <a name="try-your-code-fix"></a>コード修正を実行してください。

これでキーを押して**f5 キーを押して**を Visual Studio の 2 番目のインスタンスでアナライザーを実行します。  前に使用したコンソール プロジェクトを開きます。  場所は、新しいオブジェクトの作成式を表示する電球を表示する必要があります`ImmutableArray<int>`します。  キーを押す場合**Ctrl**+**します。** (ピリオド)、修正、コードが表示され、light bulb UI で、自動的に生成されたコードの違いにプレビューが表示されます。  Roslyn はこれを作成します。

**Pro ヒント:** 、Visual Studio の 2 番目のインスタンスを起動して、コード修正に電球が表示されない場合、Visual Studio コンポーネント キャッシュをクリアする必要があります。  キャッシュをクリアする Visual Studio で Visual Studio は、最新コンポーネントを選択し、必要がありますので、コンポーネントを再度確認を強制します。  最初に、Visual Studio の 2 番目のインスタンスをシャット ダウンします。  次に**Windows エクスプ ローラー**で、ユーザー ディレクトリに移動 (*c:\users\\< userid\>*) を見つけて*AppData\Local\Microsoft\VisualStudio\14.0Roslyn\\*.  このディレクトリにサブディレクトリ ComponentModelCache を削除します。  「14」の変更バージョン Visual Studio を使用します。

## <a name="talk-video-and-finish-code-project"></a>ビデオの説明し、コード プロジェクトの完了

この例で開発された説明を確認できますでさらに[ここ](http://channel9.msdn.com/events/Build/2015/3-725)。  後半は、作業のアナライザーを示し、それをビルドする手順します。

完成したすべてのコードを確認できます[ここ](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)します。  サブ フォルダー *DoNotUseImmutableArrayCollectionInitializer*と*DoNotUseImmutableArrayCtor*問題を検出する (C#) ファイルがある各とコードを実装する c# ファイルでその表示を修正しますVisual Studio 電球 UI。  ただし、完成したコードが、ImmutableArray をフェッチを回避するために少し多くの抽象化\<T > オブジェクトを繰り返し入力します。  入れ子にされた登録済みのアクションを使用して利用可能なコンテキストでの型のオブジェクトの保存をされるたびに、サブ操作 (オブジェクトの作成を分析し、コレクションの初期化を分析) を実行します。

## <a name="see-also"></a>関連項目

* [\\\Build 2015 トーク](http://channel9.msdn.com/events/Build/2015/3-725)
* [GitHub で完成したコード](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [GitHub、アナライザーの 3 種類にグループ化にいくつかの例](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [GitHub の OSS サイトでは、その他のドキュメント](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [FxCop ルールが GitHub で Roslyn アナライザーの実装](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
