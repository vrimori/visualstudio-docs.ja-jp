---
title: "レガシ言語サービス パーサーとスキャナー |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 30453237dcd95607a4f3524f115d16bc1cf4859a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="legacy-language-service-parser-and-scanner"></a>レガシ言語サービス パーサーとスキャナー
パーサーは、言語サービスの中核です。 Managed Package Framework (MPF) 言語のクラスでは、表示されているコードに関する情報を選択する言語パーサーが必要です。 パーサーは、構文のトークンにテキストを分離し、型と機能を使用してこれらのトークンを識別します。  
  
## <a name="discussion"></a>説明  
 C# のメソッドを次に示します。  
  
```csharp  
namespace MyNamespace  
{  
    class MyClass  
    {  
        public void MyFunction(int arg1)  
        {  
            int var1 = arg1;  
        }  
    }  
}  
```  
  
 この例では、トークンは、単語や句読点がします。 トークンの種類は次のとおりです。  
  
|トークン名|トークン型|  
|----------------|----------------|  
|名前空間、クラス、パブリック、void、int|keyword|  
|=|operator|  
|{ } ( ) ;|区切り記号|  
|MyNamespace、MyClass、MyFunction、arg1、var1|identifier|  
|MyNamespace|namespace|  
|MyClass|class|  
|MyFunction|メソッド|  
|arg1|パラメーター|  
|var1|ローカル変数|  
  
 パーサーの役割は、トークンを識別します。 いくつかのトークンには、1 種類以上を持つことができます。 パーサーがトークンを識別したら、言語サービスは、構文の強調表示などの便利な機能は、照合、左中かっこを提供する情報と IntelliSense の操作に使用できます。  
  
## <a name="types-of-parsers"></a>パーサーの種類  
 言語サービス パーサーは、コンパイラの一部として使用するパーサーと同じではありません。 ただし、この種のパーサーは、コンパイラのパーサーと同じ方法で、スキャナーと、パーサーの両方を使用する必要があります。  
  
-   スキャナーを使用して、トークンの種類を識別します。 この情報は、構文の強調表示し、トークンの種類など、他の操作をトリガーする中かっこの一致を迅速に識別するために使用されます。 このスキャナーがによって表される、<xref:Microsoft.VisualStudio.Package.IScanner>インターフェイスです。  
  
-   パーサーを使用して、機能と、トークンのスコープを記述します。 この情報は、メソッド、変数、パラメーター、および宣言などの言語要素を識別しをメンバーとメソッドのシグネチャのコンテキストに基づいての一覧を提供する IntelliSense 操作で使用されます。 このパーサーは、一致する言語要素のペア、中かっこおよびかっこなどの検索にも使用されます。 このパーサーは、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.LanguageService>クラスです。  
  
 ユーザーの責任は、言語サービス スキャナーとパーサーを実装する方法です。 いくつかのリソースが利用可能なパーサーのしくみ、および独自のパーサーを作成する方法を説明します。 また、いくつかの無償および商用の製品は、パーサーを作成するのに役立ちます。  
  
### <a name="the-parsesource-parser"></a>ParseSource パーサー  
 (ここで、トークンから実行可能コードのいくつかの形式に変換されます) コンパイラの一部として使用されるパーサーとは異なりさまざまな理由と、多数の異なるコンテキストで、言語サービス パーサーを呼び出すことができます。 このアプローチを実装する方法、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.LanguageService>クラスは自由です。 留意することが重要です、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>バック グラウンド スレッドでメソッドを呼び出すことがあります。  
  
> [!CAUTION]
>  <xref:Microsoft.VisualStudio.Package.ParseRequest>構造にはへの参照が含まれています、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>オブジェクト。 これは、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>オブジェクトは、バック グラウンド スレッドでは使用できません。 実際には、バック グラウンド スレッドでの基本の MPF クラスの多くは使用できません。 ように、 <xref:Microsoft.VisualStudio.Package.Source>、 <xref:Microsoft.VisualStudio.Package.ViewFilter>、<xref:Microsoft.VisualStudio.Package.CodeWindowManager>クラス、および直接または間接的に、ビューとの通信、他のクラスです。  
  
 このパーサーが通常に呼び出されますかと解析の理由の値全体のソース ファイルの最初の時間を解析して<xref:Microsoft.VisualStudio.Package.ParseReason>が与えられます。 後続の呼び出し、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドが解析されたコードの一部を処理し、以前の完全な解析操作の結果を使用して、はるかに高速実行することができます。 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドを介して解析操作の結果を通信し、<xref:Microsoft.VisualStudio.Package.AuthoringSink>と<xref:Microsoft.VisualStudio.Package.AuthoringScope>オブジェクト。 <xref:Microsoft.VisualStudio.Package.AuthoringSink>オブジェクトの使用を特定の解析を行って理由の中かっこまたはパラメーターのリストを持つメソッドのシグネチャと一致する範囲に関する情報などの情報を収集します。 <xref:Microsoft.VisualStudio.Package.AuthoringScope>宣言とメソッドのシグネチャとサポートのコレクションを移動するには、高度な編集オプションを提供 (**定義へ移動**、**宣言へ移動**、**に移動参照**)。  
  
### <a name="the-iscanner-scanner"></a>IScanner スキャナー  
 実装するスキャナーを実装することも必要があります。<xref:Microsoft.VisualStudio.Package.IScanner>です。 ただし、このスキャナーが経由で 1 行ごとに動作するため、<xref:Microsoft.VisualStudio.Package.Colorizer>クラスでは通常より簡単に実装します。 MPF は、各行の先頭には、<xref:Microsoft.VisualStudio.Package.Colorizer>クラス、スキャナーに渡される状態変数として使用する値。 各行の最後に、スキャナーは、更新された状態変数を返します。 MPF は、スキャナーのソース ファイルの先頭から開始することがなく、任意の行から解析を開始するために、行ごとにこの状態情報をキャッシュします。 この単一行に高速スキャンをユーザーに高速なフィードバックを提供するエディターを使用できます。  
  
## <a name="parsing-for-matching-braces"></a>対応するかっこの解析  
 この例では、ユーザーが入力する終わりかっこの照合の制御フローを示します。 このプロセスもトークンとトークンが中かっこの一致操作をトリガーするかどうかの種類を確認するにカラー表示に使用するスキャナーが使用されます。 トリガーが見つかった場合、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>を対応するかっこを検索するメソッドが呼び出されます。 最後に、2 つの中かっこが強調表示されます。  
  
 中かっこは、トリガーの名前に使用され、解析上の理由から、場合でも、このプロセスを実際の中かっこを制限することはありません。 ペアになったマッチングに指定されている文字のペアはサポートされています。 例としては、(と)、 \< >、および [と] です。  
  
 言語サービスが対応する中かっこをサポートするいると仮定します。  
  
1.  ユーザーは、右中かっこ (}) を入力します。  
  
2.  ソース ファイルのカーソル位置に中かっこを挿入し、いずれかによって、カーソルが前進します。  
  
3.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.Source>クラスが型指定された右中かっこで呼び出されます。  
  
4.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>メソッドの呼び出し、<xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.Source>クラスを現在のカーソル位置の直前の位置にあるトークンを取得します。 このトークンに対応、型指定された右中かっこ) します。  
  
    1.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>メソッドの呼び出し、<xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>メソッドを<xref:Microsoft.VisualStudio.Package.Colorizer>を現在の行のすべてのトークンを取得するオブジェクト。  
  
    2.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>メソッドの呼び出し、<xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A>メソッドを<xref:Microsoft.VisualStudio.Package.IScanner>現在の行のテキストを含むオブジェクト。  
  
    3.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>メソッドを繰り返し呼び出す、<xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A>メソッドを<xref:Microsoft.VisualStudio.Package.IScanner>オブジェクトを現在の行からすべてのトークンを収集します。  
  
    4.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>メソッド プライベート メソッドの呼び出しで、 <xref:Microsoft.VisualStudio.Package.Source> 、目的の位置を含むトークンを取得するクラスおよびから取得したトークンの一覧で、パス、<xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>メソッドです。  
  
5.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>メソッドのトークンの trigger フラグを探します<xref:Microsoft.VisualStudio.Package.TokenTriggers>から返されるトークンに、<xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>メソッドです。 つまり、右中かっこを表すトークン)。  
  
6.  トリガーのフラグを付ける場合<xref:Microsoft.VisualStudio.Package.TokenTriggers>が見つかると、<xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.Source>クラスが呼び出されます。  
  
7.  <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>メソッドは、解析理由の値は解析操作を開始<xref:Microsoft.VisualStudio.Package.ParseReason>です。 この操作は最終的に呼び出し、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドを<xref:Microsoft.VisualStudio.Package.LanguageService>クラスです。 この呼び出しによってに非同期の解析が有効になっている場合、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドはバック グラウンド スレッドで発生します。  
  
8.  解析操作が完了すると、名前付き内部完了ハンドラー (コールバック メソッドとも呼ばれます)`HandleMatchBracesResponse`で呼び出される、<xref:Microsoft.VisualStudio.Package.Source>クラスです。 この呼び出しがによって自動的に行われる、<xref:Microsoft.VisualStudio.Package.LanguageService>パーサーではなく基本クラスです。  
  
9. `HandleMatchBracesResponse`から範囲の一覧を取得するメソッド、<xref:Microsoft.VisualStudio.Package.AuthoringSink>オブジェクトに格納されている、<xref:Microsoft.VisualStudio.Package.ParseRequest>オブジェクト。 (範囲は、<xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>ソース ファイル内の行と文字の範囲を指定する構造体です)。通常、この範囲の一覧には、開始タグと右中かっこの 1 つずつ、2 つの範囲が含まれています。  
  
10. `HandleBracesResponse`メソッドの呼び出し、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>オブジェクトに格納されている、<xref:Microsoft.VisualStudio.Package.ParseRequest>オブジェクト。 これには、指定された範囲が強調表示されます。  
  
11. 場合、<xref:Microsoft.VisualStudio.Package.LanguagePreferences>プロパティ<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>が有効になって、`HandleBracesResponse`メソッドは一致する範囲に包含され、ステータス バーにその範囲の最初の 80 文字を表示するテキストを取得します。 最適な結果は場合、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドに一致するペアに付属している言語要素が含まれています。 詳細については、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> プロパティを参照してください。  
  
12. 完成です。  
  
### <a name="summary"></a>概要  
 中かっこの一致の操作は、通常、言語要素のペアを単純に制限されます。 3 要素に一致するなどのより複雑な要素 ("`if(...)`「,」`{`「と」`}`"、または"`else`「,」`{`「と」`}`")、入力語の完了操作の一部として強調表示されます。 たとえば、"else"という単語が完了すると、一致する"`if`"ステートメントが強調表示されます。 一連があった場合`if` / `else if`中かっこの一致するものと同じメカニズムを使用して、それらのすべてのステートメントを強調表示されますでした。 <xref:Microsoft.VisualStudio.Package.Source>基本クラスは、次のように、このサポート既に: スキャナーは、トークンのトリガー値を返す必要があります<xref:Microsoft.VisualStudio.Package.TokenTriggers>トリガー値と組み合わせると<xref:Microsoft.VisualStudio.Package.TokenTriggers>のカーソル位置の前に、トークンです。  
  
 詳細については、次を参照してください。[レガシ言語サービスでかっこの照合](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)です。  
  
## <a name="parsing-for-colorization"></a>解析の色づけを  
 ソース コードの色分けは簡単です、だけその型のトークンと戻り値の色の情報の種類を識別します。 <xref:Microsoft.VisualStudio.Package.Colorizer>クラスはすべてのトークンの色の情報を提供するには、エディターとスキャナーの仲介として機能します。 <xref:Microsoft.VisualStudio.Package.Colorizer>クラスの使用、<xref:Microsoft.VisualStudio.Package.IScanner>オブジェクトを参考に、行の色分けもソース ファイル内のすべての行の状態情報を収集します。 MPF 言語サービス クラスで、<xref:Microsoft.VisualStudio.Package.Colorizer>スキャナーによる通信を行うためにオーバーライドするクラスがないを通してのみ、<xref:Microsoft.VisualStudio.Package.IScanner>インターフェイスです。 実装するオブジェクトを指定する、<xref:Microsoft.VisualStudio.Package.IScanner>をオーバーライドしてインターフェイス、<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>メソッドを<xref:Microsoft.VisualStudio.Package.LanguageService>クラスです。  
  
 <xref:Microsoft.VisualStudio.Package.IScanner>スキャナーがソース コードの行を指定した、<xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A>メソッドです。 呼び出し、<xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A>メソッドがトークンを取得する、次の行でトークンの行がなくなるまで繰り返されます。 色付けには、MPF は、すべてのソース コードを行のシーケンスとして扱います。 そのため、スキャナーに行として受信ソースに対処できる必要があります。 さらに、任意の行は、いつでも、スキャナーに渡すことができ、唯一の保証は、スキャナーがスキャンされる直前の行の前に、の行から、状態変数を受信します。  
  
 <xref:Microsoft.VisualStudio.Package.Colorizer>クラスはトークンのトリガーの識別にも使用します。 これらのトリガーは、特定のトークンが単語の入力候補などのより複雑な操作を開始できることを MPF に指示または中かっこを照合します。 このようなトリガーを識別して、高速である必要があります、任意の場所で行う必要があります、ためスキャナーはこのタスクに最適です。  
  
 詳細については、次を参照してください。[レガシ言語サービスでの構文が色分け](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)です。  
  
## <a name="parsing-for-functionality-and-scope"></a>機能とスコープの解析  
 機能とスコープの解析中には、発生したトークンの種類を識別するだけよりも多くの労力が必要です。 パーサーは、トークンの種類だけでなく、トークンが使用されている機能を識別するがします。 たとえば、識別子は、名前だけが、言語、識別子が、クラス、名前空間、メソッド、または、コンテキストに応じて、変数の名前を指定します。 トークンの一般的な種類できますが、識別子は識別子にはこれに応じておよびが定義されているその他の意味があります。 この id には、解析された言語に関するより広範な知識を身にパーサーが必要です。 これは、ような場合、<xref:Microsoft.VisualStudio.Package.AuthoringSink>クラスが役に立ちます。 <xref:Microsoft.VisualStudio.Package.AuthoringSink>クラス識別子、メソッド、(など、中かっこおよびかっこを使用)、一致する言語および言語の 3 要素に関する情報を収集する (たとえば、3 つの部分がある点を除いて言語の組み合わせに似ています"`foreach()`""`{`「と」`}`") です。 さらに、オーバーライドすることができます、<xref:Microsoft.VisualStudio.Package.AuthoringSink>デバッガーが読み込まれる必要があるないように、ブレークポイントの事前検証で使用される、コードの識別をサポートするクラスと**[自動変数]**デバッグ ウィンドウで、ローカルを示しています変数とパラメーターに自動的にプログラムは、デバッグ中と適切なローカル変数と、デバッガーを表示するだけでなくパラメーターを識別するためにパーサーが必要です。  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink>オブジェクトは、パーサーの一部として、<xref:Microsoft.VisualStudio.Package.ParseRequest>オブジェクト、および新しい<xref:Microsoft.VisualStudio.Package.AuthoringSink>オブジェクトがするたびに作成される新しい<xref:Microsoft.VisualStudio.Package.ParseRequest>オブジェクトを作成します。 さらに、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドが返す必要があります、<xref:Microsoft.VisualStudio.Package.AuthoringScope>オブジェクト、IntelliSense、さまざまな操作を処理するために使用します。 <xref:Microsoft.VisualStudio.Package.AuthoringScope>オブジェクトを保持宣言の一覧と、メソッドの一覧かされるは、によって設定されます、解析の理由。 <xref:Microsoft.VisualStudio.Package.AuthoringScope>クラスを実装する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [レガシ言語サービスを実装します。](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [レガシ言語サービスの概要](../../extensibility/internals/legacy-language-service-overview.md)   
 [従来の言語サービスでの構文の色分け](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [従来の言語サービスでのかっこの一致](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)