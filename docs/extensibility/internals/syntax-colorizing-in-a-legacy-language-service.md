---
title: 従来の言語サービスでの構文が色分け |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1d82a85958fd979a3d9d44375656b08356ef09d9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>従来の言語サービスでの構文の色分け
構文の色表示機能は、さまざまな色とスタイルのソース ファイルに表示されるプログラミング言語のさまざまな要素の原因となる機能です。 この機能をサポートするには、パーサーや構文の要素またはファイル内のトークンの種類を識別できるスキャナーを指定する必要があります。 多くの言語は、さまざまな方法でそれらを色分けしてキーワード、区切り記号 (丸かっこまたは中かっこ)、およびコメントを区別します。  
  
 レガシ言語サービスは、VSPackage の一部として実装されますが、MEF 拡張機能を使用する言語サービスの機能を実装する新しい方法です。 詳細については、次を参照してください。[エディターと言語サービスの拡張](../../extensibility/extending-the-editor-and-language-services.md)です。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
## <a name="implementation"></a>実装  
 Managed package framework (MPF) が含まれていますの色づけをサポートするために、<xref:Microsoft.VisualStudio.Package.Colorizer>クラスを実装する、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>インターフェイスです。 このクラスの対話、<xref:Microsoft.VisualStudio.Package.IScanner>トークンと色を決定します。 スキャナーの詳細については、次を参照してください。[レガシ言語サービス パーサーとスキャナー](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)です。 <xref:Microsoft.VisualStudio.Package.Colorizer>クラス色の情報とトークンの各文字をマークし、ソース ファイルを表示するエディターにその情報を返します。  
  
 エディターに返される色の情報は、装飾が可能な項目のリストをインデックスです。 装飾が可能な各アイテムは、太字など、色の値とフォントの属性のセットを指定または取り消し線。 エディターは、言語サービスが使用できる既定の装飾が可能な項目のセットを提供します。 行うには必要なは適切な色の各トークンの種類のインデックスを指定します。 ただし、トークンの場合、カスタムの装飾が可能なアイテムと指定したインデックスのセットを提供し、既定の一覧ではなく装飾が可能な項目の一覧を参照できます。 設定する必要があります、`RequestStockColors`を 0 にレジストリ エントリ (かを指定しない、`RequestStockColors`まったくエントリ) カスタム カラーをサポートするためにします。 名前付きパラメーターには、このレジストリ エントリを設定することができます、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>ユーザー定義の属性です。 言語サービスを登録して、そのオプションの設定の詳細については、次を参照してください。[レガシ言語サービスを登録する](../../extensibility/internals/registering-a-legacy-language-service1.md)です。  
  
## <a name="custom-colorable-items"></a>カスタムの装飾が可能な項目  
 オーバーライドする必要があります、独自のカスタムの装飾が可能な項目を指定する、<xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A>と<xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A>メソッドを<xref:Microsoft.VisualStudio.Package.LanguageService>クラスです。 最初のメソッドは、言語サービスがサポートするカスタムの装飾が可能な項目の数を返し、2 つ目は、インデックスによって、カスタムの装飾が可能な項目を取得します。 カスタムの装飾が可能な項目の既定のリストを作成します。 言語サービスのコンス トラクターを行う必要があるすべてが、名前の装飾が可能な各アイテムを指定します。 Visual Studio では、ユーザーが、異なる一連の装飾が可能な項目を選択する場合に自動的に処理します。 この名前に表示される内容、**フォントおよび色**プロパティ ページで、**オプション** ダイアログ ボックス (Visual Studio から使用可能な**ツール**メニュー) し、この名前を決定します。ユーザーがオーバーライドされる色です。 ユーザーの選択は、レジストリ内のキャッシュに格納されているし、色の名前でアクセスします。 **フォントおよび色**プロパティ ページではすべてのアルファベット順に色の名前が表示されるためより前の言語の名前に対して各色の名前で、カスタム カラーをグループ化することができます、"**TestLanguage-コメント**「と」**TestLanguage キーワード**"です。 または、装飾が可能な項目の種類でグループ化できます"**コメント (TestLanguage)**「と」**キーワード (TestLanguage)**"です。 言語名でグループ化をお勧めします。  
  
> [!CAUTION]
>  既存の装飾が可能な項目の名前と衝突を避けるために装飾が可能な項目の名前に言語名を含めることを強くお勧めします。  
  
> [!NOTE]
>  開発中に、色のいずれかの名前を変更する場合は、Visual Studio が初めてアクセスしたため、色を作成する、キャッシュをリセットする必要があります。 これを行うを実行して、**実験用ハイブをリセット**Visual Studio SDK プログラム メニュー コマンド。  
  
 装飾が可能な項目の一覧の最初の項目が参照されていないことに注意してください。 Visual Studio は、常に、既定のテキストの色とその項目の属性を指定します。 これを処理する場合の最も簡単な方法では、最初の項目としてプレース ホルダーの装飾が可能な項目を指定します。  
  
### <a name="high-color-colorable-items"></a>High Color 装飾が可能な項目  
 装飾が可能な項目を使用して 24 ビット、または高の色値もサポートできます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>インターフェイスです。 MPF<xref:Microsoft.VisualStudio.Package.ColorableItem>クラスでサポート、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>インターフェイスと 24 ビット色は通常の色と共にコンス トラクターで指定します。 詳細については、<xref:Microsoft.VisualStudio.Package.ColorableItem> クラスのトピックを参照してください。 次の例では、キーワードとコメントの 24 ビット色を設定する方法を示します。 24 ビット カラーがユーザーのデスクトップ; でサポートされている場合 24 ビット色が使用されます。それ以外の場合、通常のテキストの色が使用されます。  
  
 ただし、これらは、既定の色を使用する言語です。ユーザーは、どのようなをこれらの色を変更できます。  
  
### <a name="example"></a>例  
 この例を宣言しを使用してカスタムの装飾が可能な項目の配列を設定する方法を示しています、<xref:Microsoft.VisualStudio.Package.ColorableItem>クラスです。 この例では、24 ビット色を使用して、キーワードやコメントの色を設定します。  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private ColorableItem[] m_colorableItems;  
  
        TestLanguageService() : base()  
        {  
            m_colorableItems = new ColorableItem[] {  
                new ColorableItem("TestLanguage - Text",  
                                  "Text",  
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.Empty,  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT),  
                new ColorableItem("TestLanguage - Keyword",  
                                  "Keyword",  
                                  COLORINDEX.CI_MAROON,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.FromArgb(192,32,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_BOLD),  
                new ColorableItem("TestLanguage - Comment",  
                                  "Comment",  
                                  COLORINDEX.CI_DARKGREEN,  
                                  COLORINDEX.CI_LIGHTGRAY,  
                                  System.Drawing.Color.FromArgb(32,128,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT)  
                // ...  
                // Add as many colorable items as you want to support.  
            };  
        }  
    }  
}  
```  
  
## <a name="the-colorizer-class-and-the-scanner"></a>Colorizer クラスとスキャナー  
 基本<xref:Microsoft.VisualStudio.Package.LanguageService>クラスには、<xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A>メソッドその instantiantes、<xref:Microsoft.VisualStudio.Package.Colorizer>クラスです。 返される、スキャナー、<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>にメソッドが渡される、<xref:Microsoft.VisualStudio.Package.Colorizer>クラスのコンス トラクターです。  
  
 実装する必要があります、<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>バージョンのメソッド、<xref:Microsoft.VisualStudio.Package.LanguageService>クラスです。 <xref:Microsoft.VisualStudio.Package.Colorizer>クラスでは、スキャナーを使用して、すべてのトークンの色の情報を取得します。  
  
 スキャナーを設定する必要があります、<xref:Microsoft.VisualStudio.Package.TokenInfo>構成をすべてのトークンを検索します。 この構造体は、トークンのスパンを占有、色のインデックスを使用するように情報を格納、トークン、およびトークンのトリガーの種類 (を参照してください<xref:Microsoft.VisualStudio.Package.TokenTriggers>)。 色づけの期間と色のインデックスのみが必要な<xref:Microsoft.VisualStudio.Package.Colorizer>クラスです。  
  
 格納されている色のインデックス、<xref:Microsoft.VisualStudio.Package.TokenInfo>構造体は、通常はから、<xref:Microsoft.VisualStudio.Package.TokenColor>列挙体は、キーワードと演算子などのさまざまな言語要素に対応する名前付きのインデックスの数を提供します。 項目が表示される、カスタムの装飾が可能なアイテムの一覧と一致する場合、<xref:Microsoft.VisualStudio.Package.TokenColor>列挙してを使用できます列挙色として各トークンです。 ただし、追加の装飾が可能なアイテムがある場合、またはその順序で既存の値を使用したくない、ニーズに合うよう、そのリストに適切なインデックスを返す、カスタムの装飾が可能な項目の一覧を配置できます。 だけにするインデックスをキャストすることを確認する、<xref:Microsoft.VisualStudio.Package.TokenColor>で格納するときに、<xref:Microsoft.VisualStudio.Package.TokenInfo>構造体です。[!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)]インデックスのみを表示します。  
  
### <a name="example"></a>例  
 次の例は、スキャナーが 3 つのトークンの種類を識別する方法を示しています。 数字、句読点、および識別子 (数または句読点ではないもの)。 この例では、わかりやすくするためだけはし、包括的なパーサーとスキャナーの実装を表していません。 あることを前提としています、`Lexer`クラス、`GetNextToken()`文字列を返すメソッド。  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    private Lexer lex;  
  
    public class TestScanner : IScanner  
    {  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false;  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                char firstChar = token[0];  
                if (Char.IsPunctuation(firstChar))  
                {  
                    tokenInfo.Type = TokenType.Operator;  
                    tokenInfo.Color = TokenColor.Keyword;  
                }  
                else if (Char.IsNumber(firstChar))  
                {  
                    tokenInfo.Type = TokenType.Literal;  
                    tokenInfo.Color = TokenColor.Number;  
                }  
                else  
                {  
                    tokenInfo.Type = TokenType.Identifier;  
                    tokenInfo.Color = TokenColor.Identifier;  
                }  
            }  
            return foundToken;  
        }  
```  
  
## <a name="see-also"></a>関連項目  
 [レガシ言語サービス機能](../../extensibility/internals/legacy-language-service-features1.md)   
 [レガシ言語サービス パーサーとスキャナー](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [レガシ言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service1.md)