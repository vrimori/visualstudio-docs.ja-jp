---
title: "従来の言語サービス パーサーとスキャナー | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "パーサー、言語サービス [マネージ パッケージ framework]"
  - "パーサーの言語サービス [マネージ パッケージ framework]"
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# 従来の言語サービス パーサーとスキャナー
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

パーサーは、言語サービスの中核です。 管理されているパッケージ フレームワーク \(MPF\) 言語のクラスでは、表示されているコードに関する情報を選択する言語パーサーが必要です。 パーサーは、レキシカル トークンにテキストを分離し、種類と機能を使用してそれらのトークンを識別します。  
  
## 説明  
 C\# のメソッドを次に示します。  
  
```c#  
namespace MyNamespace { class MyClass { public void MyFunction(int arg1) { int var1 = arg1; } } }  
```  
  
 この例では、トークンは、単語と区切り記号です。 トークンの種類は次のとおりです。  
  
|トークンの名前|トークン型|  
|-------------|-----------|  
|名前空間、クラスの public void int|keyword|  
|\=|operator|  
|{ } \( \) ;|区切り記号|  
|MyNamespace、MyClass、MyFunction、arg1、var1|identifier|  
|MyNamespace|namespace|  
|MyClass|クラス|  
|MyFunction|メソッド|  
|arg1|パラメーター|  
|var1|ローカル変数|  
  
 パーサーの役割は、トークンを識別するためにです。 いくつかのトークンには複数の種類を使用できます。 パーサーがトークンを識別したら、言語サービスは、照合、かっこの構文を強調表示などの便利な機能を提供する情報と、IntelliSense の操作に使用できます。  
  
## パーサーの種類  
 言語サービス パーサーは、同じコンパイラの一部として使用されるパーサーではありません。 ただし、このようなパーサーでは、コンパイラのパーサーと同様に、スキャナーと、パーサーの両方を使用する必要があります。  
  
-   スキャナーを使用して、トークンの種類を識別します。 この情報は、構文の強調表示し、トークンの種類など、他の操作をトリガーできるかっこの一致を迅速に識別するために使用されます。 このスキャナーがによって表される、 <xref:Microsoft.VisualStudio.Package.IScanner> インターフェイスです。  
  
-   パーサーを使用して、機能と、トークンのスコープを記述します。 メソッド、変数、パラメーター、および宣言などの言語要素を識別するために、メンバーとコンテキストに基づいて、メソッド シグネチャの一覧を提供する、この情報は IntelliSense の操作で使用されます。 このパーサーは、中かっことかっこなどの一致する言語の要素ペアを検索するも使用されます。 このパーサーは、 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> メソッドで、 <xref:Microsoft.VisualStudio.Package.LanguageService> クラスです。  
  
 言語サービス スキャナーとパーサーを実装する方法が行います。 いくつかのリソースが利用可能なパーサーのしくみ、および独自のパーサーを記述する方法を説明します。 また、いくつかの無償および商用製品は使用可能なパーサーを作成することです。  
  
### ParseSource パーサー  
 \(が、トークンから実行可能コードの何らかの形式に変換される\) コンパイラの一部として使用されるパーサーとは異なりさまざまな理由と、さまざまな異なるコンテキストで、言語サービス パーサーを呼び出すことができます。 この方法を実装するか、 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> メソッドで、 <xref:Microsoft.VisualStudio.Package.LanguageService> クラスは、開発者ができます。 留意することが重要です、 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> バック グラウンド スレッドでメソッドを呼び出すことがあります。  
  
> [!CAUTION]
>  <xref:Microsoft.VisualStudio.Package.ParseRequest> 構造体への参照を格納する、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> オブジェクトです。 これは、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> オブジェクトは、バック グラウンド スレッドでは使用できません。 実際には、バック グラウンド スレッドでの基本の MPF クラスの多くは使用できません。 以下の <xref:Microsoft.VisualStudio.Package.Source>, 、<xref:Microsoft.VisualStudio.Package.ViewFilter>, 、<xref:Microsoft.VisualStudio.Package.CodeWindowManager> クラス、および直接または間接的に、ビューとの通信、他のクラスです。  
  
 このパーサーが通常と呼ばれますかと解析の理由の値全体のソース ファイルの最初の時間を解析して <xref:Microsoft.VisualStudio.Package.ParseReason> が与えられます。 以降の呼び出し、 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> メソッドは、解析されたコードの一部を処理し、以前の完全な解析操作の結果を使用して、はるかに速く実行できます。<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> メソッドを通じて解析操作の結果を通信する、 <xref:Microsoft.VisualStudio.Package.AuthoringSink> と <xref:Microsoft.VisualStudio.Package.AuthoringScope> オブジェクトです。<xref:Microsoft.VisualStudio.Package.AuthoringSink> オブジェクトは特定の解析を行って理由の中かっこまたはパラメーターのリストを持つメソッドのシグネチャに一致する範囲に関する情報などの情報を収集するために使用します。<xref:Microsoft.VisualStudio.Package.AuthoringScope> 宣言とメソッドのシグネチャおよびサポートのコレクションを移動するには、高度な編集オプションは、\(**定義へ移動**, 、**宣言へ移動**, 、**参照へジャンプ**\)。  
  
### IScanner スキャナー  
 実装するスキャナーを実装することも必要があります。 <xref:Microsoft.VisualStudio.Package.IScanner>します。 ただし、このスキャナーを経由して 1 行ごとに動作するため、 <xref:Microsoft.VisualStudio.Package.Colorizer> クラスでは通常より簡単に実装します。 MPF は、各行の先頭に、 <xref:Microsoft.VisualStudio.Package.Colorizer> クラスのスキャナーに渡される状態変数として使用する値。 各行の最後には、スキャナーは、更新された状態変数を返します。 スキャナーは、ソース ファイルの先頭から開始することがなく、任意の行から解析を開始できるように、MPF は行ごとにこの状態情報をキャッシュします。 この単一行に高速スキャンでは、ユーザーに高速なフィードバックを提供するエディター。  
  
## 中かっこの一致の解析  
 この例では、ユーザーが入力した右中かっこに一致する制御フローを示します。 このプロセスではトークンとトークンが中かっこの一致操作をトリガーするかどうかの種類を判断色付けに使用するスキャナーを使用します。 トリガーが見つかった場合、 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> メソッドが呼び出され、対応する中かっこを検索します。 最後に、2 つの中かっこが強調表示されます。  
  
 中かっこは、トリガーの名前で使用され、解析上の理由から、にもかかわらず、このプロセスを実際の中かっこを制限することはありません。 ペアになったマッチングに指定されている文字のペアがサポートされています。 例としては、\(と\)、\<、\>、および \[と\] です。  
  
 言語サービスに対応する中かっこがサポートするいると仮定します。  
  
1.  右中かっこ \(}\) を入力します。  
  
2.  中かっこをソース ファイル内のカーソル位置に挿入し、いずれかによって、カーソルが高度な。  
  
3.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> メソッドで、 <xref:Microsoft.VisualStudio.Package.Source> クラスは、型指定された右中かっこで呼び出されます。  
  
4.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> メソッドの呼び出し、 <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> メソッドで、 <xref:Microsoft.VisualStudio.Package.Source> クラスを現在のカーソル位置の直前の位置にあるトークンを取得します。 このトークンは、型指定された右中かっこ\)。  
  
    1.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> メソッドの呼び出し、 <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> メソッドを <xref:Microsoft.VisualStudio.Package.Colorizer> を現在の行のすべてのトークンを取得するオブジェクト。  
  
    2.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> メソッドの呼び出し、 <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> メソッドを <xref:Microsoft.VisualStudio.Package.IScanner> オブジェクトが現在の行のテキストを使用します。  
  
    3.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> メソッドを繰り返し呼び出す、 <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> メソッドを <xref:Microsoft.VisualStudio.Package.IScanner> オブジェクトを現在の行からすべてのトークンを収集します。  
  
    4.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> メソッドの呼び出しで、プライベート メソッド、 <xref:Microsoft.VisualStudio.Package.Source> を目的の位置を含むトークンを取得するクラスおよびから取得したトークンの一覧で、パス、 <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> メソッドです。  
  
5.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> メソッドのトークンのトリガー フラグは検索 <xref:Microsoft.VisualStudio.Package.TokenTriggers> から返されるトークンに、 <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> メソッド、つまり右中かっこを表すトークン\)。  
  
6.  トリガーのフラグを付ける場合 <xref:Microsoft.VisualStudio.Package.TokenTriggers> が見つかると、 <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> メソッドで、 <xref:Microsoft.VisualStudio.Package.Source> クラスが呼び出されます。  
  
7.  <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> メソッドは、解析理由の値は解析操作を開始 <xref:Microsoft.VisualStudio.Package.ParseReason>します。 この操作は最終的に呼び出し、 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> メソッドを <xref:Microsoft.VisualStudio.Package.LanguageService> クラスです。 この呼び出しによってに非同期の解析が有効になっている場合、 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> メソッドはバック グラウンド スレッドで発生します。  
  
8.  解析操作が完了すると、名前付き内部完了ハンドラー \(コールバック メソッドとも呼ばれます\) `HandleMatchBracesResponse` で呼び出される、 <xref:Microsoft.VisualStudio.Package.Source> クラスです。 この呼び出しがによって自動的に行われた、 <xref:Microsoft.VisualStudio.Package.LanguageService> パーサーではなく基本クラスです。  
  
9. `HandleMatchBracesResponse` メソッドから範囲の一覧の取得、 <xref:Microsoft.VisualStudio.Package.AuthoringSink> オブジェクトに格納されている、 <xref:Microsoft.VisualStudio.Package.ParseRequest> オブジェクトです。 \(範囲は、 <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> をソース ファイルの行数と文字の範囲を指定します\)。 通常、この範囲の一覧には、開始タグと右中かっこの 1 つずつ、2 つの範囲が含まれています。  
  
10. `HandleBracesResponse` メソッドの呼び出し、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> メソッドを <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> オブジェクトに格納されている、 <xref:Microsoft.VisualStudio.Package.ParseRequest> オブジェクトです。 これには、特定の範囲が強調表示されます。  
  
11. 場合、 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> プロパティ <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> が有効になって、 `HandleBracesResponse` メソッドは一致する範囲に含まれているがステータス バーにその範囲の最初の 80 文字を表示するテキストを取得します。 これが最適、 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> メソッドには、一致するペアに付属している言語要素が含まれています。 詳細については、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> プロパティを参照してください。  
  
12. 行われます。  
  
### まとめ  
 中かっこの一致の操作は、通常、言語要素のペアを単純に制限されます。 3 要素の一致処理などのより複雑な要素 \("`if(…)`「,」`{`「と」`}`"、または"`else`「,」`{`「と」`}`"\)、word 完了操作の一部として強調表示されることができます。 たとえば、"else"という単語が完了すると、一致する"`if`"ステートメントが強調表示されます。 一連があった場合 `if`\/`else if` 中かっこを一致するものと同じメカニズムを使用して、すべてのステートメントを強調表示される可能性があります。<xref:Microsoft.VisualStudio.Package.Source> 基本クラスは、次のように、このサポート既に: スキャナーはトークンのトリガー値を返す必要があります <xref:Microsoft.VisualStudio.Package.TokenTriggers> トリガー値と組み合わせて使用 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 、カーソル位置の前に、トークンです。  
  
 詳細については、「[従来の言語サービスにおけるかっこの一致](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)」を参照してください。  
  
## 解析の色づけを  
 ソース コードの色分けは簡単です、だけその型のトークンと戻り値の色の情報の種類を識別します。<xref:Microsoft.VisualStudio.Package.Colorizer> クラスは、エディターとスキャナーの色のすべてのトークン情報を提供する間の仲介役として機能します。<xref:Microsoft.VisualStudio.Package.Colorizer> クラスは、 <xref:Microsoft.VisualStudio.Package.IScanner> オブジェクトのヘルプで、行の配色を変更し、ソース ファイル内のすべての行の状態情報を収集します。 MPF 言語サービス クラスで、 <xref:Microsoft.VisualStudio.Package.Colorizer> クラスは、スキャナーと通信するためにオーバーライドする必要がないを通してのみ、 <xref:Microsoft.VisualStudio.Package.IScanner> インターフェイスです。 実装するオブジェクトを指定する、 <xref:Microsoft.VisualStudio.Package.IScanner> をオーバーライドしてインターフェイス、 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> メソッドを <xref:Microsoft.VisualStudio.Package.LanguageService> クラスです。  
  
 <xref:Microsoft.VisualStudio.Package.IScanner> スキャナーがソース コードの行を指定した、 <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> メソッドです。 呼び出し、 <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> トークンの行がなくなるまで、行の次のトークンを取得するメソッドが繰り返されます。 色付けの MPF はすべてのソース コードは一連の直線として扱います。 したがって、スキャナーは、ソース行として判断に対処できる必要があります。 さらに、任意の行は、いつでも、スキャナーに渡すことができ、保証されるだけです、スキャナーがスキャンされる直前の行の前に、の行から、状態変数を受け取っているします。  
  
 <xref:Microsoft.VisualStudio.Package.Colorizer> クラスはトークンのトリガーを識別するためにも使用します。 これらのトリガーは、特定のトークンが単語の入力候補などのより複雑な操作を開始できることを MPF に指示または中かっこを照合します。 このようなトリガーを識別する、高速である必要があり、任意の場所で行う必要があります、ためスキャナーがこのタスクに最も適しています。  
  
 詳細については、「[従来の言語サービスでの構文の色分け](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)」を参照してください。  
  
## 機能とスコープの解析  
 機能とスコープの解析中には、発生したトークンの種類を特定するだけよりは多くの労力が必要です。 パーサーは、トークンの種類だけでなく、トークンが使用されている機能を識別するためには。 たとえば、識別子は、名前だけが、言語では、識別子が、クラス、名前空間、メソッド、または、コンテキストに応じて、変数の名前を指定します。 一般的に、トークンの種類は、識別子にありますが、識別子には新機能によって、定義されているその他の意味があります。 この id には、解析する言語に関するより詳細な知識を身にパーサーが必要です。 これは、ような場合、 <xref:Microsoft.VisualStudio.Package.AuthoringSink> クラスを受信します。<xref:Microsoft.VisualStudio.Package.AuthoringSink> クラス識別子、メソッド、一致する言語の組み合わせ \(中かっこおよびかっこ\) などの言語の 3 要素に関する情報を収集する \(たとえば、3 つの部分があること以外の言語の組み合わせと同じ"`foreach()`""`{`「と」`}`"\) です。 さらに、オーバーライドすることができます、 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 、デバッガーが読み込まれる必要があるないように、ブレークポイントの事前検証で使用される、コードの識別をサポートするクラスと **\[自動変数\]** デバッグ ウィンドウで、プログラムのデバッグ中に適切なローカル変数と、デバッガーを表示するだけでなくパラメーターを識別するためにパーサーを必要となるときのローカル変数とパラメーターを自動的に表示します。  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink> の一部としてオブジェクトが、パーサーに渡される、 <xref:Microsoft.VisualStudio.Package.ParseRequest> オブジェクト、および新しい <xref:Microsoft.VisualStudio.Package.AuthoringSink> オブジェクトがたびを作成、新しい <xref:Microsoft.VisualStudio.Package.ParseRequest> オブジェクトを作成します。 さらに、 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> メソッドが返す必要があります、 <xref:Microsoft.VisualStudio.Package.AuthoringScope> オブジェクトで、さまざまな IntelliSense の操作を処理するために使用します。<xref:Microsoft.VisualStudio.Package.AuthoringScope> オブジェクトを保持方法については、リストと宣言子のリストか、うちが表示されたら、解析用理由に応じて。<xref:Microsoft.VisualStudio.Package.AuthoringScope> クラスを実装する必要があります。  
  
## 参照  
 [従来の言語サービスを実装します。](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [従来の言語サービスの概要](../../extensibility/internals/legacy-language-service-overview.md)   
 [従来の言語サービスでの構文の色分け](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [従来の言語サービスにおけるかっこの一致](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)