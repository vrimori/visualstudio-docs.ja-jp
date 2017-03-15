---
title: "Roslyn アナライザーや ImmutableArrays 用ライブラリをコードに注意してください。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# Roslyn アナライザーや ImmutableArrays 用ライブラリをコードに注意してください。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[.NET コンパイラ プラットフォーム](https://github.com/dotnet/roslyn) \("Roslyn"\) ではコード対応ライブラリを作成できます。  コード対応ライブラリでは、最良の方法で、またはエラーを回避する機能を使用して、ライブラリを使用するためのツール \(Roslyn アナライザー\) を提供します。  このトピックを使用する場合は、一般的なエラーをキャッチする現実の世界 Roslyn アナライザーを構築する方法、 [変更できないコレクション](../Topic/NIB:%20Immutable%20Collections.md) NuGet パッケージ。  この例では、アナライザーによって検出されたコードの問題のコード修正を提供する方法も示します。  ユーザーは、Visual Studio の電球 UI 内のコード修正を参照し、コードの修正プログラムを自動的に適用することができます。  
  
## このトピックの内容  
 このトピックでは、次のセクションでがあります。  
  
-   作業の開始  
  
-   この問題は何ですか。  
  
-   アナライザーをトリガーする関連コード モデルの型の検索  
  
-   アナライザー プロジェクトを作成します。  
  
-   アナライザーの初期化  
  
-   アナライザーのユーザーのプロパティの設定  
  
-   オブジェクト作成式の分析  
  
-   最初に、アナライザーを使用して Visual Studio の起動  
  
-   仕上げアナライザーを使用して、エディット コンティニュ  
  
-   コードの問題の「コード修正」を追加します。  
  
-   コード修正しようとしています。  
  
-   ビデオ、および完成したコード プロジェクトを説明します。  
  
## 作業の開始  
 この例をビルドするには、次のとおりです。  
  
-   Visual Studio 2015 \(、Express エディション以外\) またはそれ以降のバージョン。  無料のを使用する [Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs)  
  
-   [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  確認することも、Visual Studio をインストールするときに、同時に、SDK をインストールする一般的なツール \[Visual Studio Extensibility Tools。  Visual Studio を既にインストールして場合のメイン メニューに移動してこの SDK をインストールすることも、 **ファイル &#124;新しい &#124;プロジェクト...**, 、左側のナビゲーション ウィンドウでは、c\# を選択して、機能拡張を選択します。  選択すると、"**Visual Studio Extensibility Tools をインストール**"階層リンク プロジェクト テンプレートでは、入力を求められたをダウンロードして、SDK をインストールします。  
  
-   [.NET コンパイラ プラットフォーム \("Roslyn"\) SDK](http://aka.ms/roslynsdktemplates)します。  メイン メニューに移動して、この SDK をインストールすることも **ファイル &#124;新しい &#124;プロジェクト...**, を選択する、 **c\#** で、左側のナビゲーション ウィンドウで、選択して、 **拡張**します。  選択すると"**.NET コンパイラ プラットフォーム SDK をダウンロードして**"階層リンク プロジェクト テンプレートでは、入力を求められたをダウンロードして、SDK をインストールします。  この SDK に含まれる、 [Roslyn Syntax Visualizer](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer)します。  この非常に便利なツールでは、どのようなコード モデルの種類を理解のことを確認、アナライザーでします。  アナライザー インフラストラクチャを呼び出し、コードの特定のコード モデルの種類のコードはのみ必要なときに実行し、関連するコードを分析するだけに集中できます。  
  
## この問題は何ですか。  
 ライブラリを提供する ImmutableArray を想像してください \(たとえば、 <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>\) をサポートします。  C\# 開発者には、多数の .NET 配列の使用経験があります。  ただし、実装で使われる ImmutableArrays と最適化の手法の性質上、c\# 開発者 intuitions、切断されたコードを記述する、ライブラリのユーザー次に示す。  さらに、ユーザーでは、これは、高品質なエクスペリエンスを .NET で Visual Studio で使用する実行時までのエラーは表示はされません。  
  
 ユーザーは、次のようにコードを記述に慣れています。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 後続の行のコードをコピーする空の配列を作成して、コレクション初期化子の構文を使用してに慣れ親しんでいる c\# 開発者にします。  ただし、同じを書き込み、ImmutableArray のコードがクラッシュした実行時。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 最初のエラーでは、ImmutableArray 実装の基になるデータ ストレージをラップする構造体を使用するためです。  構造体は、パラメーターなしのコンス トラクターを持つ必要がありますように `default(T)` 式には、すべての構造体を返す 0 または null のメンバーです。  コードにアクセスするとき `b1.Length`, 、ImmutableArray 構造体の基になる記憶域配列がないために、実行時の null 値がエラーを逆参照があります。  空の ImmutableArray を作成するための正しい方法 `ImmutableArray<int>.Empty`します。  
  
 ImmutableArray.Add メソッドはこのメソッドを呼び出すたびに新しいインスタンスを返すために、コレクション初期化子とエラーが発生します。  ImmutableArrays 決して変更されないため、新しい要素を追加するが返されます \(これは以前から存在 ImmutableArray とパフォーマンスのための記憶域を共有することがあります\)、新しい ImmutableArray オブジェクト。`b2` 呼び出す前に最初の ImmutableArray 指す `Add()` 5 回 `b2` 既定 ImmutableArray します。  エラーの呼び出しの長さにもクラッシュが null の逆参照します。  手動で追加の呼び出しは、使用することがなく、ImmutableArray を初期化する正しい方法 `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`します。  
  
## アナライザーをトリガーする適切な構文ノードの型の検索  
 アナライザーをビルドするには、まず解明 SyntaxNode の種類を検索する必要があります。    起動メニュー Syntax Visualizer **表示 &#124;その他の Windows &#124;Roslyn Syntax Visualizer**します。  
  
 宣言する行に、エディターのカーソルを置きます `b1`します。  Syntax Visualizer を示していますが表示されます、 `LocalDeclarationStatement` 構文ツリーのノードです。  このノードには、 `VariableDeclaration`, 、段落では、 `VariableDeclarator`, 、段落では、 `EqualsValueClause`, 、最後には、 `ObjectCreationExpression`です。  ノードの Syntax Visualizer ツリー内をクリックすると、そのノードで表されるコードを表示するエディター ウィンドウ内の構文が強調表示されます。  SyntaxNode サブ型の名前では、c\# の文法で使用される名前と一致します。  
  
## アナライザー プロジェクトを作成します。  
 メイン メニューから選択 **ファイル &#124;新しい &#124;プロジェクト...**します。**新しいプロジェクト** ダイアログで、 **c\#** プロジェクト、左側のナビゲーション バーで拡張性を選択し、右側のウィンドウで次のように選択します。、 **with Code Fix アナライザー** プロジェクト テンプレートです。  名前を入力し、ダイアログ ボックスを確認します。  
  
 テンプレートは、DiagnosticAnalyzer.cs ファイルを開きます。  そのエディター バッファーのタブをクリックします。  このファイルは、アナライザー クラス \(形式プロジェクトに付けた名前から\) から派生した `DiagnosticAnalyzer` \(Roslyn API の種類\)。  新しいクラスが、 `DiagnosticAnalyzerAttribute` アナライザーを宣言することは、c\# 言語に関連するようにコンパイラを検出し、アナライザーを読み込みます。  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 C\# のコードを対象とする Visual Basic を使用して、アナライザーを実装することができ、その逆です。  アナライザーが 1 つの言語またはその両方を対象かどうかを選択する DiagnosticAnalyzerAttribute でより重要になります。  高度なアナライザーを言語の詳細なモデリングを必要とする 1 つの言語のみ対象にできます。  場合、アナライザーなどのみチェック型の名前またはパブリック メンバーの名前、Roslyn は Visual Basic および C\# の場合にわたって共通の言語モデルを使用することがあります。  たとえば、FxCop は警告クラスで実装する <xref:System.Runtime.Serialization.ISerializable>, 、クラスがない、 <xref:System.SerializableAttribute> 属性は、言語に依存しないし、Visual Basic および c\# のコードで動作します。  
  
## 品詞、アナライザー  
 下へ少しスクロール、 `DiagnosticAnalyzer` クラスを参照、 `Initialize` メソッドです。  コンパイラは、アナライザーをアクティブ化する際に、このメソッドを呼び出します。  このメソッドには、 `AnalysisContext` コンテキスト情報を取得し、分析するコードの種類のイベントのコールバックを登録するアナライザーをできるようにするオブジェクト。  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 このメソッド、および型""コンテキスト内に新しい行を開く Intellisense 入力候補一覧を表示します。  多数あるコンプリート リストに表示できる `Register…` をさまざまな種類のイベントを処理するメソッドです。  たとえば、1 つ目、 `RegisterCodeBlockAction`, 、これは通常、中かっこの間にコード ブロックのコードにコールバックします。  ブロック用の登録も返信をコードに、フィールド、属性に渡された値、または省略可能なパラメーターの値の初期化子。  
  
 別の例として `RegisterCompilationStartAction`, 、さまざまな場所にわたって状態を収集する必要がある場合に便利ですのコンパイルの開始時に、コードにコールバックします。  作成、データ構造と答えると、このオプションを使用すると、すべてのシンボルを収集して、アナライザーがいくつか構文エラーやシンボル、戻る呼び出されるたびにデータ構造でそれぞれの場所に関する情報を保存することができます。  コンパイルの終了のためコールバックして場合、は、保存した、たとえば、各からコードを使用してどのようなシンボルを報告するすべての場所を分析できます `using` ステートメントです。  
  
 使用して、 **Syntax Visualizer**, 、コンパイラ、ObjectCreationExpression を処理するときに呼び出されるをすることを学習しました。  コールバックを設定するには、このコードを使用します。  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
 構文ノードとオブジェクトの作成の構文ノードだけのフィルターを登録します。  規則は、アナライザーの作成者は、アナライザーをステートレスようにすることがアクションを登録するときに、ラムダを使用できます。  Visual Studio の機能を使用する **使用法から生成** を作成する、 `AnalyzeObjectCreation` メソッドです。  これは、コンテキスト パラメーターの正しい型を生成するすぎるします。  
  
## アナライザーのユーザーのプロパティの設定  
 表示されるよう、アナライザー Visual Studio UI で適切を検索し、アナライザーを識別するコードの次の行を変更します。  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
 変更 `"Naming"` に `"API Guidance"`します。  
  
 次の検索し、使用して、プロジェクトで Resources.resx ファイルを開き、 **ソリューション エクスプ ローラー**します。  アナライザー、タイトルなどの説明を配置できます。これらのすべての値を変更する `“Don’t use ImmutableArray<T> constructor”` ここでは。  文字列に引数を書式設定文字列を配置することができます \({0}, \\{1\\} など\) を呼び出すときに後で、 `Diagnostic.Create()`, 、渡される引数のパラメーター配列を指定することができます。  
  
## オブジェクト作成式の分析  
 `AnalyzeObjectCreation` メソッドは、異なる種類のコード アナライザーのフレームワークから提供されたコンテキストを受け取ります。  Initialize メソッドの `AnalysisContext` アナライザーを設定する操作のコールバックを登録することができます。`SyntaxNodeAnalysisContext`, 、たとえばは、 `CancellationToken` の周囲に渡すことができます。  ユーザーは、エディターで入力を開始する場合、Roslyn は作業を保存し、パフォーマンスが向上する実行中のアナライザーをキャンセルします。  このコンテキストでは別の例として、オブジェクトの作成の構文ノードを返すノード プロパティがあります。  
  
 構文ノード アクションをフィルター処理する型は、前提としているノードを取得します。  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
### 最初に、アナライザーを使用して Visual Studio の起動  
 Visual Studio を起動するには、作成して、アナライザーを実行する \(キーを押して **f5 キーを押して**\)。  スタートアップ プロジェクトであるため、 **ソリューション エクスプ ローラー** 、コードと VSIX、コードのビルドを実行している、VSIX プロジェクトは、インストールされているその VSIX に Visual Studio を起動します。  この方法で Visual Studio を起動するときにアナライザーのビルド中に、Visual Studio の主な使用が、テスト インスタンスによって影響されないように、個別のレジストリ ハイブとでが起動します。  初めてこの方法を起動する Visual Studio では、ときに最初に起動した Visual Studio インストールしてのようないくつかの初期化。  
  
 コンソール プロジェクトを作成し、コンソール アプリケーションの Main メソッドに配列のコードを入力します。  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
 行のコードで `ImmutableArray` 波線がある変更できない NuGet パッケージの取得を追加する必要があるため、 `using` ステートメントをコードにします。  プロジェクト ノードを右のポインター ボタンを押して、 **ソリューション エクスプ ローラー** 選択 **NuGet パッケージの管理...**します。  NuGet マネージャーで、検索ボックスに「不変」を入力し、項目"System.Collections.Immutable"を選択 \("Microsoft.Bcl.Immutable"を選択しないで\) で、左側と右側のウィンドウで \[インストール\] ボタンを押します。  パッケージをインストールして、プロジェクトの参照への参照を追加します。  
  
 下にある赤い波線が引き続き表示 `ImmutableArray`, 、ようにキャレットを配置するには、その識別子とキーを押して **CTRL \+.** 修正候補がメニューを表示し、適切なを追加するには、\(ピリオド\) `using` ステートメントです。  
  
 **すべてを保存して閉じます** を続行するクリーンな状態にここでは Visual Studio の 2 番目のインスタンス。  
  
## 仕上げアナライザーを使用して、エディット コンティニュ  
 Visual Studio の最初のインスタンス内の先頭にブレークポイントを設定、 `AnalyzeObjectCreation` キーを押してメソッド **F9** 最初の行にキャレットをします。  
  
 使用して、アナライザーを起動 **f5 キーを押して**, 、Visual Studio の 2 番目のインスタンスで最後に作成したコンソール アプリケーションを開き直します。  
  
 Roslyn コンパイラ オブジェクト作成の式を指定し、アナライザーと呼ばれるため、ブレークポイントで Visual Studio の最初のインスタンスに戻ります。  
  
 **オブジェクトの作成のノードを取得します。**手順を設定する行で、 `objectCreation` キーを押して変数 **f10 キーを押して**, 、し、\[、 **イミディ エイト ウィンドウ** 式の評価 `“objectCreation.ToString()”`します。  変数が指す構文ノードが、コードを参照してください `"new ImmutableArray<int>()"`, 、だけを探しているものです。  
  
 **ImmutableArray \< T \> 型のオブジェクトを取得します。**作成される型が ImmutableArray を確認する必要があります。  最初に、この型を表すオブジェクトを取得します。  セマンティック モデルを使用して、正しい型では正確にし、ToString\(\) から文字列を比較しないように型を確認します。  次の関数の末尾のコード行を入力します。  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 ジェネリック型では、バッククォート \('\) でメタデータとジェネリック パラメーターの数を指定します。  "... 表示されない理由です。ImmutableArray \< T \>"のメタデータ名。  
  
 セマンティック モデルでは、シンボル、データ フロー、変数の有効期間などに関する質問を投稿することに多くの便利なことがあります。Roslyn は、セマンティック モデルから、さまざまな理由でエンジニア リング \(パフォーマンス、誤ったコードなどのモデリング\) 構文ノードを分離します。  正確な比較のための参照に含まれている情報を検索するコンパイル モデルが必要です。  
  
 エディター ウィンドウの左側にある黄色の実行のポインターをドラッグできます。  設定する行までドラッグ、 `objectCreation` 変数とステップ オーバー、新しい行を使用してコードの **f10 キーを押して**します。  マウス ポインターを合わせると、変数の上 `immutableArrayOfType`, 、セマンティック モデルの正確な型が見つかったことを参照してください。  
  
 **オブジェクト作成式の型を取得します。**この記事で、いくつかのように"type"が使用されますが、つまり、"新しい Foo"があるかどうかは式、Foo のモデルを取得する必要があります。  ImmutableArray \< T \> 型であるかどうかをオブジェクトの作成の式の種類を取得する必要があります。  セマンティック モデルを使用して、もう一度をオブジェクト作成の式で型のシンボル \(ImmutableArray\) のシンボル情報を取得します。  次の関数の末尾のコード行を入力します。  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
 アナライザーが不完全または不正確コード エディターのバッファーを処理する必要があるため \(たとえばが指定 `using` ステートメント\) をチェックする必要があります `symbolInfo` されている `null`します。  分析が完了するシンボル情報オブジェクトから名前付きの型 \(INamedTypeSymbol\) を取得する必要があります。  
  
 **型を比較します。**\(オープン ジェネリック型\) はどのような種類で構成のシンボル情報をクエリし、その結果とを比較する探していた T のオープン ジェネリック型があるため、コードの型は、具体的なジェネリック型 `immutableArrayOfTType`します。  メソッドの末尾で次のコマンドを入力します。  
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
 **診断を報告します。**診断を報告することは非常に簡単です。  Initialize メソッドの前に定義されているプロジェクト テンプレートに作成した規則を使用するとします。  置換するルールを初期化する行を変更するには、コードでこのような状況がエラーのため `DiagnosticSeverity.Warning` \(緑色の波線\) と `DiagnosticSeverity.Error` \(赤の波線\)。  ルールの残りの部分は、チュートリアルの最初の近くで編集するリソースを初期化します。  また、オブジェクト作成 expresssion の型指定の場所を指定すると、波線の場所を報告する必要があります。  このコードを入力、 `if` ブロック。  
  
<CodeContentPlaceHolder>11</CodeContentPlaceHolder>  
 関数は、\(異なる形式などで\) 次のようになります。  
  
<CodeContentPlaceHolder>12</CodeContentPlaceHolder>  
 ブレークポイントを削除するは、そのアナライザー作業を参照してください \(および Visual Studio の最初のインスタンスを返すことを停止\) できます。  メソッド、およびキーを押しての先頭に、実行ポインターをドラッグして **f5 キーを押して** の実行を続行します。  Visual Studio の 2 つ目のインスタンスに切り替えるときに、コードをもう一度チェックする、コンパイラが起動し、アナライザーが呼び出されます。  下の波線が表示できる `ImmutableType<int>`です。  
  
## コードの問題の「コード修正」を追加します。  
 開始する前に、Visual Studio の 2 つ目のインスタンスを終了し、\(ここで、アナライザーを開発する\) Visual Studio の最初のインスタンスでのデバッグを停止します。  
  
 **新しいクラスを追加します。**ソリューション エクスプ ローラーでプロジェクト ノードのショートカット メニュー \(右のポインター ボタン\) を使用して、新しい項目の追加を選択します。  というクラスを追加 `BuildCodeFixProvider`します。  このクラスから派生する必要が `CodeFixProvider`, を使用する必要がある **CTRL \+.** \(ピリオド\) を追加、適切なコード修正を呼び出す `using` ステートメントです。  またこのクラスを使って注釈を付ける必要があります `ExportCodeFixProvider` して、属性を追加する必要が、 `using` ステートメントを解決するのには、 `LanguageNames` 列挙型。  次のコードにクラス ファイルが必要です。  
  
<CodeContentPlaceHolder>13</CodeContentPlaceHolder>  
 **派生メンバーを消します。**これで、識別子の中で、エディターのカーソルを配置 `CodeFixProvider` とキーを押します **CTRL \+.** \(ピリオド\) をこの抽象基本クラスの実装をスタブです。  プロパティとメソッドが生成されます。  
  
 **プロパティを実装します。**入力、 `FixableDiagnosticIds` プロパティの `get` を次のコードの本文。  
  
<CodeContentPlaceHolder>14</CodeContentPlaceHolder>  
 Roslyn では、診断にまとめること、この id は、単なる文字列を照合することによって修正します。  プロジェクト テンプレートは、診断 ID を生成し、自由に変更します。  プロパティ内のコードには、アナライザー クラスからの ID だけを返します。  
  
 **RegisterCodeFixAsync メソッドは、コンテキストを受け取ります。**コンテキストは、コード修正は、複数の診断に適用できるまたはでした問題がある 1 つ以上のコード行のために重要です。  「コンテキスト」を入力する場合 メソッドの本文に、Intellisense コンプリート リストはメンバーを表示するいくつかに便利です。  修正プログラムをキャンセルするには何かかどうかかを確認できる CancellationToken メンバーがあります。  多数の便利なメンバーがあり、使用すると、プロジェクトやソリューションのモデルのオブジェクトを取得するドキュメント メンバーがあります。  開始される Span のメンバーが存在し、診断を報告したコードの場所の末尾を指定します。  
  
 **非同期にする方法を確認します。**最初に行う必要である生成されたメソッドの宣言を修正、 `async` メソッドです。  抽象クラスの実装をスタブのコード修正が含まれていない、 `async` キーワード、メソッドが戻るとしても、 `Task`です。  
  
 **構文ツリーのルートを取得します。**変更された新しい構文ツリーを作成する必要があるコードを変更するには、コード修正が使用できます。  必要があります、 `Document` を呼び出してコンテキストから `GetSyntaxRootAsync`します。  これは、ディスクからファイルを取得する、解析すること、およびその用 Roslyn コード モデルの構築を含む場合もあります構文ツリーを取得する不明な作業があるために、非同期メソッドです。  Visual Studio の UI は、使用する、この期間中に応答する必要があります `async` 有効にします。  次のように、メソッド内のコード行を置き換えます。  
  
<CodeContentPlaceHolder>15</CodeContentPlaceHolder>  
 **問題のノードが見つかりません。**コンテキストの範囲がコードを変更する必要がありますが見つかったら、ノードを渡します。  報告された診断は、\(破線が属していた\) 型の識別子の範囲を提供するだけが、オブジェクト全体の作成式を置き換える必要があるなど、 `new` 、先頭と末尾のかっこ keywoard します。  メソッドに次のコードを追加 \(を使用して、 **CTRL \+.** を追加する、 `using` の声明 `ObjectCreationExpressionSyntax`\)。  
  
<CodeContentPlaceHolder>16</CodeContentPlaceHolder>  
 **電球の UI のコード修正を登録します。**コード修正を登録するときに Roslyn は自動的に Visual Studio の電球 UI に接続されます。  エンドユーザーに使用できる表示は **CTRL \+.** アナライザー波線の無効な場合 \(ピリオド\) `ImmutableArray<T>` コンス トラクターを使用します。  コード修正プロバイダーは、問題がある場合にのみ実行するため、探していたオブジェクトの作成の式があるを想定することができます。  末尾に次のコードを追加することで、新しいコード修正を登録するコンテキスト パラメーターから `RegisterCodeFixAsync` メソッド。  
  
<CodeContentPlaceHolder>17</CodeContentPlaceHolder>  
 Id に、エディターのカーソルを配置する必要があります `CodeAction`, 、を使用して **CTRL \+。** 。適切なを追加するには、\(ピリオド\) `using` このタイプのステートメントです。  
  
 内のエディターのキャレットを配置、 `ChangeToImmutableArrayEmpty` 識別子と使用 **CTRL \+.** のメソッド スタブを生成するためです。  
  
 この最後のコード スニペットを追加したを渡すことによって、コード修正の登録、 `CodeAction` と検出された問題の種類の診断の ID。  この例では 1 つだけ、このコードは、診断 ID を修正ため、同じ診断 Id の配列の最初の要素を渡すことができます。  作成するとき、 `CodeAction`, 、電球 UI がコード修正の説明として使用するテキストで渡します。  また、キャンセル トークンを取得し、新しいドキュメントを返す関数に渡します。  新しいドキュメントにはパッチが適用されたコードを呼び出すを含む新しい構文ツリー `ImmutableArray.Empty`します。  次のコード スニペットは、オブジェクト作成ノードとコンテキストのドキュメントを閉じることができますので、ラムダを使用します。  
  
 **新しい構文ツリーを構築します。** `ChangeToImmutableArrayEmpty` メソッドがスタブが以前に生成するコード行を入力してください: `ImmutableArray<int>.Empty;`です。  Syntax Visualizer ツール ウィンドウをもう一度表示する場合、この構文は SimpleMemberAccessExpression ノードが確認できます。  つまりを作成して、新しいドキュメントの返すこのメソッドで必要があります。  
  
 最初の変更 `ChangeToImmutableArrayEmpty` は、追加する `async` する前に `Task<Document>` ため、コード ジェネレーターと考えないでメソッドを非同期にする必要があります。  
  
 メソッドは、次のように見えるように、本文を次のコードを入力します。  
  
<CodeContentPlaceHolder>18</CodeContentPlaceHolder>  
 エディターのカーソルを配置する必要があります、 `SyntaxGenerator` 識別子と使用 **CTRL \+.** 適切なを追加するには、\(ピリオド\) `using` このタイプのステートメントです。  
  
 このコードを使用して `SyntaxGenerator`, 、非常に便利な型では新しいコードを構築します。  コードの問題を持つドキュメントのジェネレーターを取得した後 `ChangeToImmutableArrayEmpty` 呼び出し `MemberAccessExpression`, にアクセスするメンバーを持つ型を渡すこと、およびメンバーの名前を文字列として渡します。  
  
 次に、このメソッドは、ドキュメントのルートをフェッチし、コードがこの呼び出しを待機し、キャンセル トークンを渡すため、これには、一般的なケースで任意の作業が含まれます、します。  Roslyn コード モデルは不変と同じように .NET の文字列です。文字列を更新するときに、戻り値、新しい文字列オブジェクトを取得します。  呼び出すと `ReplaceNode`, 、新しいルート ノードが返されます。  \(変更可能ではない\) ために、構文ツリーのほとんどが共有されるが、 `objectCreation` ノードに置き換え、 `memberAccess` ノード、だけでなく、構文ツリーのルートに達するまでのすべての親ノードです。  
  
## コード修正しようとしています。  
 ここで押す **f5 キーを押して** を Visual Studio の 2 つ目のインスタンスでアナライザーを実行します。  以前に使用したコンソール プロジェクトを開きます。  ここでは、新しいオブジェクトの作成の式を表示、light bulb を確認したら `ImmutableArray<int>`します。  キーを押した場合 **CTRL \+.** \(ピリオド\) を修正するコードが表示され、light bulb UI での自動生成されたコードの違いプレビューが表示されます。  Roslyn は、これをするを作成します。  
  
 Pro ヒント: Visual Studio の 2 番目のインスタンスを起動するコード修正と電球が表示されない場合は、必要がありますを Visual Studio コンポーネントのキャッシュをオフにします。  キャッシュをクリアする強制的に Visual Studio で Visual Studio は、最新のコンポーネントを選択し、必要がありますので、コンポーネントを再度確認します。  最初に、Visual Studio の 2 つ目のインスタンスをシャット ダウンします。  Windows エクスプ ローラーでは、ユーザー ディレクトリ \(c:\\users\\ \< ユーザー id \>\) に移動し、\[AppData\\Local\\Microsoft\\VisualStudio\\14.0Roslyn\\ を検索します。  このディレクトリで、ComponentModelCache のサブディレクトリを削除します。  「14」の変更バージョン Visual Studio を使用します。  
  
## 説明ビデオとコード プロジェクトの完了  
 この例で開発された説明を確認できますで詳しく [このセッション](http://channel9.msdn.com/events/Build/2015/3-725)します。  議論作業アナライザーと構築について説明します。  
  
 完成したすべてのコードを確認できます [ここ](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)します。  DoNotUseImmutableArrayCollectionInitializer と DoNotUseImmutableArrayCtor サブ フォルダーがある問題と、Visual Studio light bulb UI に表示されるコード修正を実装する c\# ファイルを検索するための c\# ファイルです。  完成したコードが何度も ImmutableArray \< T \> 型のオブジェクトをフェッチを回避する簡単な複数の抽象化に注意してください。  入れ子にされた登録済みのアクションを使用して提供されるコンテキストで型のオブジェクトを保存するたびにサブ操作 \(オブジェクトの作成を分析し、コレクションの初期化を分析\) を実行します。  
  
## 参照  
 [\\\\Build 2015年トーク](http://channel9.msdn.com/events/Build/2015/3-725)   
 [Github の完全なコード](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)   
 [Github、アナライザーの 3 種類にグループ化にいくつかの例](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)   
 [OS の github サイトでは、その他のドキュメント](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)   
 [Github の Roslyn アナライザーを使用して実装 FxCop ルール](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)