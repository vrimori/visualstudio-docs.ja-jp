---
title: "従来の言語サービスでの構文の色分け |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b9d98323b3957108746b22702306c9155b142fb9
ms.contentlocale: ja-jp
ms.lasthandoff: 02/22/2017

---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>従来の言語サービスでの構文の色分け
構文の色表示機能は、さまざまな色とスタイルのソース ファイルに表示されるプログラミング言語のさまざまな要素を原因となる機能です。 この機能をサポートするには、パーサーまたは構文の要素またはファイル内のトークンの種類を識別できるスキャナーを指定する必要があります。 多くの言語は、さまざまな方法でそれらを色分けして、キーワード、区切り記号 (丸かっこまたは中かっこを使用)、およびコメントを区別します。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は、MEF の拡張機能を使用します。 詳細については、次を参照してください。[エディター、言語のサービスを拡張する](../../extensibility/extending-the-editor-and-language-services.md)です。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く始めることをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
## <a name="implementation"></a>実装  
 マネージ パッケージ フレームワーク (MPF) が含まれています色付けをサポートするために、<xref:Microsoft.VisualStudio.Package.Colorizer>クラスを実装する、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>インターフェイス</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer></xref:Microsoft.VisualStudio.Package.Colorizer>。 このクラスの対話、<xref:Microsoft.VisualStudio.Package.IScanner>トークンおよび色を決定します</xref:Microsoft.VisualStudio.Package.IScanner>。 スキャナーの詳細については、次を参照してください。[レガシ言語サービス パーサーとスキャナー](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)します。 <xref:Microsoft.VisualStudio.Package.Colorizer>クラスは、各文字の色の情報を含むトークンをマークされ、ソース ファイルを表示するエディターにその情報を返します</xref:Microsoft.VisualStudio.Package.Colorizer>。  
  
 エディターに返される色の情報は、一連の装飾が可能な項目にインデックスです。 各装飾が可能な項目は、太字など、色の値と一連のフォント属性を指定または取り消し線。 エディターには、言語サービスで使用できる既定の装飾が可能な項目のセットが用意されています。 行う必要があるすべては、適切な色の各トークンの種類のインデックスを指定します。 ただし、トークンの場合、カスタムの装飾が可能な項目と指定したインデックスのセットを提供して、既定の一覧ではなく装飾が可能な項目の一覧を参照します。 設定する必要があります、`RequestStockColors`を 0 にレジストリ エントリ (を指定しないか、`RequestStockColors`すべてにあるエントリ) カスタム カラーをサポートするためにします。 名前付きパラメーターには、このレジストリ エントリを設定することができます、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>ユーザー定義の属性</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>。 言語サービスを登録して、そのオプションの設定の詳細については、次を参照してください。[レガシ言語サービスを登録する](../../extensibility/internals/registering-a-legacy-language-service1.md)です。  
  
## <a name="custom-colorable-items"></a>カスタムの装飾が可能な項目  
 独自のカスタムの装飾が可能な項目を指定するには<xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A>および<xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A><xref:Microsoft.VisualStudio.Package.LanguageService>クラス</xref:Microsoft.VisualStudio.Package.LanguageService>のメソッド</xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A></xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A>をオーバーライドする必要があります。 最初のメソッドは、言語サービスがサポートするカスタムの装飾が可能な項目の数を返し、2 つ目は、インデックスによって、カスタムの装飾が可能な項目を取得します。 カスタムの装飾が可能な項目の既定の一覧を作成します。 言語サービスのコンス トラクターを行うだけで済みますが、名前の装飾が可能な各アイテムを指定します。 Visual Studio では、ユーザーがさまざまな一連の装飾が可能な項目を選択する場合に自動的に処理します。 この名前に表示される内容、**フォントおよび色**プロパティ ページ、**オプション** ダイアログ ボックス (Visual Studio から利用可能な**ツール**メニュー) し、この名前は、ユーザーには、どの色がオーバーライドを決定します。 ユーザーの選択は、レジストリ内のキャッシュに格納され、色の名前でアクセスします。 **フォントおよび色** プロパティ ページではすべてのアルファベット順に色の名前が表示されるためより前の言語の名前です。 各色の名前で、カスタム カラーをグループ化することができますたとえば、"**TestLanguage コメント**"と"**TestLanguage キーワード**"です。 または、装飾が可能な項目の種類でグループ化できます"**コメント (TestLanguage)**「と」**キーワード (TestLanguage)**"です。 言語名でグループ化をお勧めします。  
  
> [!CAUTION]
>  既存の装飾が可能な項目の名前の衝突を避けるために、装飾が可能な項目の名前に言語名を含めることを強くお勧めします。  
  
> [!NOTE]
>  開発時に、色のいずれかの名前を変更する場合は、Visual Studio に初めてアクセスしたため、色が作成されたキャッシュをリセットする必要があります。 できるように実行して、**実験用ハイブをリセット**Visual Studio SDK のプログラム メニューからコマンドです。  
  
 装飾が可能な項目の一覧の最初の項目が参照されないことに注意してください。 Visual Studio は、常に、既定のテキストの色とそのアイテムの属性を指定します。 これに対処する最も簡単な方法は、最初の項目としてプレース ホルダーの装飾が可能な項目を提供することです。  
  
### <a name="high-color-colorable-items"></a>High Color の装飾が可能な項目  
 装飾が可能な項目ではを通じて 24 ビットまたは高の色値をサポートしても、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>インターフェイス</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>。 MPF<xref:Microsoft.VisualStudio.Package.ColorableItem>クラスでサポート、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>インターフェイスと 24 ビット色は標準の色とコンス トラクターで指定します</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem></xref:Microsoft.VisualStudio.Package.ColorableItem>。 参照してください、<xref:Microsoft.VisualStudio.Package.ColorableItem>詳細についてはクラスです</xref:Microsoft.VisualStudio.Package.ColorableItem>。 次の例では、キーワードとコメントの 24 ビット カラーを設定する方法を示します。 24 ビット カラーがユーザーのデスクトップでサポートされている場合に、24 ビット色が使用されます。それ以外の場合、通常のテキストの色が使用されます。  
  
 言語の既定の色ユーザーは、好きなにこれらの色を変更できます。  
  
### <a name="example"></a>例  
 この例を宣言して<xref:Microsoft.VisualStudio.Package.ColorableItem>クラス</xref:Microsoft.VisualStudio.Package.ColorableItem>を使用してカスタムの装飾が可能な項目の配列を設定する方法を示しています。 この例では、24 ビット色を使用して、キーワードとコメントの色を設定します。  
  
```c#  
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
 基本<xref:Microsoft.VisualStudio.Package.LanguageService>クラスには、<xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A>メソッドその instantiantes<xref:Microsoft.VisualStudio.Package.Colorizer>クラス</xref:Microsoft.VisualStudio.Package.Colorizer></xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A></xref:Microsoft.VisualStudio.Package.LanguageService> 返される、スキャナー、<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>にメソッドが渡される、<xref:Microsoft.VisualStudio.Package.Colorizer>クラスのコンス トラクター</xref:Microsoft.VisualStudio.Package.Colorizer> </xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 。  
  
 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A><xref:Microsoft.VisualStudio.Package.LanguageService>クラス</xref:Microsoft.VisualStudio.Package.LanguageService>のバージョンのメソッド</xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>を実装する必要があります。 <xref:Microsoft.VisualStudio.Package.Colorizer>クラスでは、スキャナーを使用して、すべてのトークンの色の情報を取得します</xref:Microsoft.VisualStudio.Package.Colorizer>。  
  
 スキャナーを設定する必要がある、<xref:Microsoft.VisualStudio.Package.TokenInfo>構造のすべてのトークンが検索されます</xref:Microsoft.VisualStudio.Package.TokenInfo>。 この構造体は、トークンの範囲が占める、色のインデックスを使用するように情報を格納は、トークンとトークンのトリガーの種類 (を参照してください<xref:Microsoft.VisualStudio.Package.TokenTriggers>).</xref:Microsoft.VisualStudio.Package.TokenTriggers> <xref:Microsoft.VisualStudio.Package.Colorizer>クラス</xref:Microsoft.VisualStudio.Package.Colorizer>で色付けの範囲と色のインデックスのみが必要な  
  
 格納されている色のインデックス、<xref:Microsoft.VisualStudio.Package.TokenInfo>構造体は、通常の値、<xref:Microsoft.VisualStudio.Package.TokenColor>列挙体は、キーワードと演算子などのさまざまな言語要素に対応する名前付きのインデックスを多数用意されています</xref:Microsoft.VisualStudio.Package.TokenColor></xref:Microsoft.VisualStudio.Package.TokenInfo>。 項目が表示される、カスタムの装飾が可能な項目の一覧と一致する場合、<xref:Microsoft.VisualStudio.Package.TokenColor>列挙型、ことができますだけを使用する列挙体の色と各トークンです</xref:Microsoft.VisualStudio.Package.TokenColor>。 ただし、追加の装飾が可能なアイテムがある場合、またはその順序で、既存の値を使用しないようにするには、ニーズに合うよう、このリストに適切なインデックスを返す、カスタムの装飾が可能な項目の一覧を配置できます。 だけに<xref:Microsoft.VisualStudio.Package.TokenInfo>構造体に格納するときに、<xref:Microsoft.VisualStudio.Package.TokenColor>にインデックスをキャストすることを確認します。[!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)]インデックスのみが表示されます</xref:Microsoft.VisualStudio.Package.TokenColor></xref:Microsoft.VisualStudio.Package.TokenInfo>。  
  
### <a name="example"></a>例  
 次の例は、スキャナーが&3; つのトークンの種類を特定する方法を示しています。 数字、句読点、および識別子 (数字や区切り記号ではないもの)。 この例では、説明のためには、包括的なパーサーとスキャナーの実装ではありません。 あることを前提としていますが、`Lexer`クラス、`GetNextToken()`メソッドの文字列を返します。  
  
```c#  
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
 [従来の言語サービスの機能](../../extensibility/internals/legacy-language-service-features1.md)   
 [従来の言語サービス パーサーとスキャナー](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [従来の言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service1.md)
