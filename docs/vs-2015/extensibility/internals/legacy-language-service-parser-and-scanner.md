---
title: 従来の言語サービス パーサーとスキャナー |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5bd5fa0fd23f2608e7cfd00896b0632cfb13fa38
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2018
ms.locfileid: "48880247"
---
# <a name="legacy-language-service-parser-and-scanner"></a>従来の言語サービスのパーサーとスキャナー
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[レガシ言語サービス パーサーとスキャナー](https://docs.microsoft.com/visualstudio/extensibility/internals/legacy-language-service-parser-and-scanner)します。  
  
パーサーは、言語サービスの中核です。 マネージ パッケージ フレームワーク (MPF) 言語のクラスには、表示されているコードに関する情報を選択する言語のパーサーが必要です。 パーサーは、テキストを構文トークンに分割し、し、それらのトークンの種類と機能を識別します。  
  
## <a name="discussion"></a>説明  
 C# メソッドを次に示します。  
  
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
  
 この例で、トークンは、単語および区切り記号です。 トークンの種類は次のとおりです。  
  
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
  
 パーサーのロールでは、トークンを特定します。 一部のトークンには、1 つ以上の型を持つことができます。 パーサーがトークンを特定した後、言語サービスは、照合、かっこの構文の強調表示などの便利な機能を提供する情報と IntelliSense の操作に使用できます。  
  
## <a name="types-of-parsers"></a>パーサーの種類  
 言語サービス パーサーは、コンパイラの一部として使用されるパーサーと同じではありません。 ただし、この種のパーサーは、コンパイラのパーサーと同様に、スキャナーとパーサーの両方を使用する必要があります。  
  
-   スキャナーを使用して、トークンの種類を識別します。 この情報は、構文の強調表示し、トークンの種類など、他の操作をトリガーできるかっこの一致をすばやく識別するために使用されます。 このスキャナーがによって表される、<xref:Microsoft.VisualStudio.Package.IScanner>インターフェイス。  
  
-   パーサーを使用して、機能と、トークンのスコープを記述します。 この情報は、メソッド、変数、パラメーター、および宣言などの言語要素を識別するために、メンバーおよびメソッド シグネチャのコンテキストに基づいての一覧を指定して、IntelliSense の操作で使用されます。 このパーサーは、中かっこおよびかっこなどの一致する言語要素ペアを検索するも使用されます。 このパーサーは、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.LanguageService>クラス。  
  
 言語サービス スキャナーとパーサーを実装する方法は自由です。 利用できるいくつかのリソースは、パーサーのしくみと、独自のパーサーを作成する方法について説明します。 また、いくつかの無償および商用製品は使用可能なパーサーを作成するのに役立ちます。  
  
### <a name="the-parsesource-parser"></a>ParseSource パーサー  
 (場所、トークンから実行可能コードのいくつかの形式に変換されます) コンパイラの一部として使用されるパーサーとは異なりさまざまな理由と、多数の異なるコンテキストで、言語サービス パーサーを呼び出すことができます。 このアプローチを実装する方法、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.LanguageService>クラスは自由です。 留意することが重要です、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>バック グラウンド スレッドでメソッドを呼び出すことがあります。  
  
> [!CAUTION]
>  <xref:Microsoft.VisualStudio.Package.ParseRequest>構造体にはへの参照が含まれています、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>オブジェクト。 これは、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>バック グラウンド スレッドでオブジェクトを使用することはできません。 実際には、バック グラウンド スレッドでの基本の MPF クラスの多くは使用できません。 以下の<xref:Microsoft.VisualStudio.Package.Source>、 <xref:Microsoft.VisualStudio.Package.ViewFilter>、<xref:Microsoft.VisualStudio.Package.CodeWindowManager>クラス、およびその他のビューとの直接または間接的に通信するクラス。  
  
 このパーサーは通常呼び出されたまたは解析がの値を判断するときに全体のソース ファイルの最初の時間を解析して<xref:Microsoft.VisualStudio.Package.ParseReason>が与えられます。 後続の呼び出し、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドは、解析されたコードのごく一部を処理し、前の完全な解析操作の結果を使用してより迅速に実行できることができます。 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドによって解析操作の結果を通信する、<xref:Microsoft.VisualStudio.Package.AuthoringSink>と<xref:Microsoft.VisualStudio.Package.AuthoringScope>オブジェクト。 <xref:Microsoft.VisualStudio.Package.AuthoringSink>オブジェクトは特定解析のため、中かっこまたはパラメーターのリストを持つメソッドのシグネチャに一致する範囲に関する情報などの情報を収集するために使用します。 <xref:Microsoft.VisualStudio.Package.AuthoringScope>宣言とメソッドのシグネチャおよびサポートのコレクションを移動する高度な編集オプションを提供します (**定義へ移動**、**宣言へ移動**、**に移動参照**)。  
  
### <a name="the-iscanner-scanner"></a>IScanner スキャナー  
 実装するスキャナーを実装することも必要があります。<xref:Microsoft.VisualStudio.Package.IScanner>します。 ただしで 1 行ずつごとにこのスキャナーが動作するため、<xref:Microsoft.VisualStudio.Package.Colorizer>クラスでは通常より簡単に実装します。 MPF は、各行の先頭には、<xref:Microsoft.VisualStudio.Package.Colorizer>クラスの値が、スキャナーに渡される状態変数として使用します。 各行の末尾には、スキャナーは、更新された状態変数を返します。 MPF は、スキャナーがソース ファイルの先頭から開始することがなく、任意の行から解析を開始できるように、それぞれの行の場合は、この状態情報をキャッシュします。 この 1 行のスキャンを高速には、ユーザーに迅速なフィードバックを提供する、エディターが使用できます。  
  
## <a name="parsing-for-matching-braces"></a>対応するかっこの解析  
 この例では、ユーザーが入力する終わりかっこの一致の制御のフローを示します。 このプロセスで色付けに使用するスキャナーもトークンとトークンが中かっこの一致操作をトリガーするかどうかの種類を決定する使用されます。 トリガーが見つかった場合、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドが呼び出され、対応するかっこを検索します。 最後に、2 つの中かっこが強調表示されます。  
  
 場合でも、中かっこは、トリガーの名前で使用され、解析上の理由から、このプロセスは実際の中かっこに限定されません。 一致するペアに指定されている文字のペアがサポートされています。 例としては、(と)、 \< >、および [と]。  
  
 言語サービスに対応する中かっこがサポートするいると仮定します。  
  
1.  ユーザーは、右中かっこ (}) を入力します。  
  
2.  カーソルのソース ファイル内に中かっこが挿入され、いずれかによって、カーソルが高度な。  
  
3.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.Source>クラスは、型指定された右中かっこで呼び出されます。  
  
4.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>メソッドの呼び出し、<xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.Source>クラスを現在のカーソル位置の直前の位置でトークンを取得します。 このトークンに対応する型指定された右中かっこ)。  
  
    1.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>メソッドの呼び出し、<xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>メソッドを<xref:Microsoft.VisualStudio.Package.Colorizer>現在の行にすべてのトークンを取得するオブジェクト。  
  
    2.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>メソッドの呼び出し、<xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A>メソッドを<xref:Microsoft.VisualStudio.Package.IScanner>現在の行のテキストを含むオブジェクト。  
  
    3.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>メソッドを繰り返し呼び出す、<xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A>メソッドを<xref:Microsoft.VisualStudio.Package.IScanner>オブジェクトを現在の行からすべてのトークンを収集します。  
  
    4.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>メソッド プライベート メソッドの呼び出しで、<xref:Microsoft.VisualStudio.Package.Source>目的の位置を含むトークンを取得するクラスし、から取得したトークンの一覧で、パス、<xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>メソッド。  
  
5.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>メソッドのトークンのトリガーのフラグは検索<xref:Microsoft.VisualStudio.Package.TokenTriggers>から返されるトークンで、<xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>メソッド、つまり右中かっこを表すトークン)。  
  
6.  トリガーのフラグを付ける場合<xref:Microsoft.VisualStudio.Package.TokenTriggers>が見つかると、<xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.Source>クラスが呼び出されます。  
  
7.  <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>メソッドでは、解析操作を開始の解析の理由の値を持つ<xref:Microsoft.VisualStudio.Package.ParseReason>します。 この操作は最終的に呼び出し、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドを<xref:Microsoft.VisualStudio.Package.LanguageService>クラス。 この呼び出しによってに非同期の解析が有効になっている場合、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドがバック グラウンド スレッドで発生します。  
  
8.  解析操作が終了すると、という名前の内部の完了ハンドラー (コールバック メソッドとも呼ばれます)`HandleMatchBracesResponse`で呼び出される、<xref:Microsoft.VisualStudio.Package.Source>クラス。 この呼び出し、<xref:Microsoft.VisualStudio.Package.LanguageService>パーサーではなく基本クラス。  
  
9. `HandleMatchBracesResponse`から範囲の一覧を取得するメソッド、<xref:Microsoft.VisualStudio.Package.AuthoringSink>オブジェクトに格納されている、<xref:Microsoft.VisualStudio.Package.ParseRequest>オブジェクト。 (範囲は、<xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>ソース ファイル内の行や文字の範囲を指定する構造体)。通常、この範囲の一覧には、開始タグと右中かっこの 1 つずつ、2 つの範囲が含まれています。  
  
10. `HandleBracesResponse`メソッドの呼び出し、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>オブジェクトに格納されている、<xref:Microsoft.VisualStudio.Package.ParseRequest>オブジェクト。 これは、指定されたスパンを示しています。  
  
11. 場合、<xref:Microsoft.VisualStudio.Package.LanguagePreferences>プロパティ<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>が有効になって、`HandleBracesResponse`メソッドは一致する範囲に包含され、ステータス バーにその範囲の最初の 80 文字を表示するテキストを取得します。 これは、場合に最適の<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドに一致するペアに付属している言語要素が含まれています。 詳細については、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> プロパティを参照してください。  
  
12. 完成です。  
  
### <a name="summary"></a>まとめ  
 中かっこの一致操作では、通常、言語要素のペアを単純に制限されます。 3 要素に一致するようより複雑な要素 ("`if(…)`「,」`{`「と」`}`"、または"`else`「,」`{`「と」`}`")、単語補完操作の一環として強調表示されることができます。 たとえば、"else"という単語が完了すると、一致する"`if`"ステートメントを強調表示されます。 一連があった場合`if` / `else if`中かっこの一致するものと同じメカニズムを使用して、それらのすべてのステートメントを強調表示でした。 <xref:Microsoft.VisualStudio.Package.Source>基本クラスは、次のように、このサポート既に: スキャナーはトークンのトリガーの値を返す必要があります<xref:Microsoft.VisualStudio.Package.TokenTriggers>トリガー値と組み合わせると<xref:Microsoft.VisualStudio.Package.TokenTriggers>トークンでカーソル位置の前にします。  
  
 詳細については、次を参照してください。[従来の言語サービスでかっこの照合](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)します。  
  
## <a name="parsing-for-colorization"></a>色づけの解析  
 ソース コードの色分けは簡単です、その型に関する情報をトークンと戻り値の色の種類を識別するだけです。 <xref:Microsoft.VisualStudio.Package.Colorizer>クラスは、エディターとスキャナーの色のすべてのトークン情報を提供する間の仲介役として機能します。 <xref:Microsoft.VisualStudio.Package.Colorizer>クラスで使用、<xref:Microsoft.VisualStudio.Package.IScanner>オブジェクトのヘルプで、行の色分けし、ソース ファイル内のすべての行の状態情報を収集します。 MPF の言語サービス クラスで、<xref:Microsoft.VisualStudio.Package.Colorizer>クラスは、スキャナーと通信するためにオーバーライドする必要はありませんを通してのみ、<xref:Microsoft.VisualStudio.Package.IScanner>インターフェイス。 実装するオブジェクトを指定する、<xref:Microsoft.VisualStudio.Package.IScanner>インターフェイスをオーバーライドすることで、<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>メソッドを<xref:Microsoft.VisualStudio.Package.LanguageService>クラス。  
  
 <xref:Microsoft.VisualStudio.Package.IScanner>スキャナーがソース コードの行を指定した、<xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A>メソッド。 呼び出し、<xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A>トークンの行がなくなるまで、行では、次のトークンを取得するメソッドが繰り返されます。 色付け、MPF はすべてのソース コードは行のシーケンスとして扱います。 そのため、スキャナーは、ソース行として受信してそれに対処できる必要があります。 さらに、任意の行は、いつでもでも、スキャナーに渡すことができ、唯一の保証は、スキャナーがスキャンされる直前の行の前に、の行から、状態変数を受け取っています。  
  
 <xref:Microsoft.VisualStudio.Package.Colorizer>クラスは、トークンのトリガーを識別するためにも使用します。 これらのトリガーは、特定のトークンが単語補完などのより複雑な操作を開始できること、MPF を指示または中かっこの一致します。 このようなトリガーを識別すると、高速である必要があるあり、任意の場所で行う必要があります、ため、スキャナーはこのタスクに最適です。  
  
 詳細については、次を参照してください。[従来の言語サービスでの構文の色分け](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)します。  
  
## <a name="parsing-for-functionality-and-scope"></a>機能とスコープの解析  
 機能とスコープの解析中には、多くの労力が発生したトークンの種類を識別するだけが必要です。 パーサーは、トークンの種類だけでなく、トークンが使用されている機能を識別する必要があります。 たとえば、識別子は名だけですが、言語、識別子のクラス、名前空間、メソッド、または、コンテキストに応じて、変数の名前可能性があります。 トークンの一般的な種類の識別子、可能性がありますが、識別子には何によって異なりますしが定義されているその他の意味があります。 この id は、パーサーが解析される言語に関するより広範な知識が必要です。 これは、ような場合、<xref:Microsoft.VisualStudio.Package.AuthoringSink>クラスを受信します。 <xref:Microsoft.VisualStudio.Package.AuthoringSink>クラスは、識別子、メソッド、(中かっこやかっこを使用)、一致する言語および言語の 3 要素に関する情報を収集します (たとえば、3 つの部分があること以外の言語の組み合わせに似ています"`foreach()`""`{`「と」`}`")。 さらに、オーバーライドすることができます、<xref:Microsoft.VisualStudio.Package.AuthoringSink>デバッガーが読み込まれる必要があるないように、ブレークポイントの事前検証に使用される、コードの識別をサポートするクラスと **[自動変数]** デバッグ ウィンドウで、ローカルの表示変数とパラメーターに自動的にプログラムがデバッグ中と適切なローカル変数と、デバッガーの表示に加えてパラメーターを識別するために、パーサーが必要です。  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink>の一部としてオブジェクトが、パーサーに渡される、<xref:Microsoft.VisualStudio.Package.ParseRequest>オブジェクト、および新しい<xref:Microsoft.VisualStudio.Package.AuthoringSink>オブジェクトがするたびに作成される新しい<xref:Microsoft.VisualStudio.Package.ParseRequest>オブジェクトが作成されます。 さらに、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドが返す必要があります、 <xref:Microsoft.VisualStudio.Package.AuthoringScope> IntelliSense のさまざまな操作を処理するために使用するオブジェクト。 <xref:Microsoft.VisualStudio.Package.AuthoringScope>オブジェクト宣言の一覧と維持方法については、一覧か、うちが作成されますが、解析の理由によって。 <xref:Microsoft.VisualStudio.Package.AuthoringScope>クラスを実装する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [従来の言語サービスを実装します。](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [従来の言語サービスの概要](../../extensibility/internals/legacy-language-service-overview.md)   
 [従来の言語サービスでの構文の色分け](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [従来の言語サービスでのかっこの一致](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

