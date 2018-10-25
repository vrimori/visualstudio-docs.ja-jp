---
title: 従来の言語サービスでの構文の色分け |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5c938f6d4a08e164638e70be969fe310fe2a324c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223498"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>従来の言語サービスでの構文の配色変更
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

構文の色表示機能は、さまざまな色とスタイルのソース ファイルに表示されるプログラミング言語のさまざまな要素を原因となる機能です。 この機能をサポートするには、パーサーや構文の要素またはファイル内のトークンの種類を識別できるスキャナーを指定する必要があります。 多くの言語は、さまざまな方法でそれらを色分けして、キーワード、区切り記号 (丸かっこまたは中かっこを使用)、およびコメントを区別します。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は MEF 拡張機能を使用します。 詳細については、次を参照してください。[エディターと言語サービス拡張](../../extensibility/extending-the-editor-and-language-services.md)します。  
  
> [!NOTE]
>  新しいエディターの API をできるだけ早く使用を開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用することができます。  
  
## <a name="implementation"></a>実装  
 Managed package framework (MPF) を含む色付けをサポートするために、<xref:Microsoft.VisualStudio.Package.Colorizer>クラスを実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>インターフェイス。 このクラスの対話、<xref:Microsoft.VisualStudio.Package.IScanner>トークンと色を決定します。 スキャナーの詳細については、次を参照してください。[レガシ言語サービス パーサーとスキャナー](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)します。 <xref:Microsoft.VisualStudio.Package.Colorizer>クラスは、マークの色の情報を使用して、トークンの各文字と、ソース ファイルを表示するエディターにその情報を返します。  
  
 エディターに返されるカラー情報は、装飾が可能な項目の一覧にインデックスです。 各装飾が可能な項目は、太字など、色の値とフォントの属性のセットを指定しますまたは取り消し線。 エディターでは、言語サービスが使用できる既定の配色可能な項目のセットが用意されています。 行う必要があるすべては、適切な色のトークンの種類ごとのインデックスを指定します。 ただし、トークンの場合、カスタムの配色可能な項目と指定したインデックスのセットを提供し、既定の一覧ではなくの配色可能な項目の一覧を参照できます。 設定する必要があります、`RequestStockColors`を 0 にレジストリ エントリ (を指定しないか、`RequestStockColors`エントリすべてに) カスタム カラーをサポートするためにします。 名前付きパラメーターを使用には、このレジストリ エントリを設定することができます、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>ユーザー定義の属性。 言語サービスを登録して、そのオプションの設定の詳細については、次を参照してください。[従来の言語サービスを登録する](../../extensibility/internals/registering-a-legacy-language-service1.md)します。  
  
## <a name="custom-colorable-items"></a>カスタムの配色可能な項目  
 オーバーライドする必要があります、独自のカスタムの配色可能な項目を指定する、<xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A>と<xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A>メソッドを<xref:Microsoft.VisualStudio.Package.LanguageService>クラス。 最初のメソッドは、言語サービスをサポートするカスタムの配色可能な項目の数を返し、2 つ目は、インデックスを使用してカスタムの装飾が可能な項目を取得します。 カスタムの配色可能な項目の既定の一覧を作成します。 言語サービスのコンス トラクター、行う必要があるすべてが各装飾が可能な項目を名前を指定します。 Visual Studio では、ユーザーがさまざまな配色可能な項目を選択する場合に自動的に処理します。 この名前に表示されます、**フォントおよび色**プロパティ ページで、**オプション** ダイアログ ボックス (Visual Studio から使用可能な**ツール**メニュー) し、この名前を決定します。ユーザーがオーバーライドされる色。 ユーザーの選択肢では、レジストリ内のキャッシュに格納され、色の名前でアクセスします。 **フォントおよび色**プロパティ ページではすべての色の名前をアルファベット順が表示される前に各色の名前、言語名で追加して、カスタム カラーをグループ化することができますので、"**TestLanguage-コメント**「と」**TestLanguage-キーワード**"。 または、配色可能な項目の種類によってグループ化することができます"**コメント (TestLanguage)**「と」**キーワード (TestLanguage)**"。 言語名でグループ化をお勧めします。  
  
> [!CAUTION]
>  既存の装飾が可能な項目の名前の競合を回避する装飾が可能な項目の名前に言語名を含めることを強くお勧めします。  
  
> [!NOTE]
>  開発中に、色のいずれかの名前を変更する場合は、Visual Studio が初めてアクセスされた色を作成するキャッシュをリセットする必要があります。 実行して行うことができます、**実験用ハイブをリセット**Visual Studio SDK のプログラム メニューからコマンド。  
  
 装飾が可能な項目の一覧の最初の項目が参照されていないことに注意してください。 Visual Studio は、常に、既定のテキストの色とその項目の属性を提供します。 これに対処する最も簡単な方法では、最初の項目としてプレース ホルダーの装飾が可能な項目を指定します。  
  
### <a name="high-color-colorable-items"></a>High Color の配色可能な項目  
 装飾が可能な項目は、24 ビットまたは高の色値もサポートできます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>インターフェイス。 MPF<xref:Microsoft.VisualStudio.Package.ColorableItem>クラスでサポート、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>インターフェイスと 24 ビット カラーと通常の色のコンス トラクターで指定されます。 詳細については、<xref:Microsoft.VisualStudio.Package.ColorableItem> クラスのトピックを参照してください。 次の例では、キーワードおよびコメントの 24 ビット カラーを設定する方法を示します。 24 ビット カラーがユーザーのデスクトップでサポートされている場合、24 ビット カラーを使用します。それ以外の場合、通常のテキストの色が使用されます。  
  
 ただし、これらは、言語の既定の色ユーザーは、好きなように、これらの色を変更できます。  
  
### <a name="example"></a>例  
 この例を宣言して設定を使用してカスタムの配色可能な項目の配列の 1 つの方法を示しています、<xref:Microsoft.VisualStudio.Package.ColorableItem>クラス。 この例では、24 ビット カラーを使用して、キーワードおよびコメントの色を設定します。  
  
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
                new ColorableItem("TestLanguage – Text",  
                                  "Text",  
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.Empty,  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT),  
                new ColorableItem("TestLanguage – Keyword",  
                                  "Keyword",  
                                  COLORINDEX.CI_MAROON,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.FromArgb(192,32,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_BOLD),  
                new ColorableItem("TestLanguage – Comment",  
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
 基本<xref:Microsoft.VisualStudio.Package.LanguageService>クラスには、<xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A>メソッドその instantiantes、<xref:Microsoft.VisualStudio.Package.Colorizer>クラス。 返される、スキャナー、<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>にメソッドが渡される、<xref:Microsoft.VisualStudio.Package.Colorizer>クラスのコンス トラクター。  
  
 実装する必要があります、<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>バージョンのメソッド、<xref:Microsoft.VisualStudio.Package.LanguageService>クラス。 <xref:Microsoft.VisualStudio.Package.Colorizer>クラスは、スキャナーを使用してすべてのトークンの色の情報を取得します。  
  
 設定する必要があります、スキャナー、<xref:Microsoft.VisualStudio.Package.TokenInfo>構造体のすべてのトークンに検索します。 この構造体は、スパン、トークンが占める、色のインデックスを使用するように情報を格納、トークン、およびトークンのトリガーの種類 (を参照してください<xref:Microsoft.VisualStudio.Package.TokenTriggers>)。 色づけの span と色のインデックスに必要な<xref:Microsoft.VisualStudio.Package.Colorizer>クラス。  
  
 格納されている色のインデックス、<xref:Microsoft.VisualStudio.Package.TokenInfo>構造体は値では通常、<xref:Microsoft.VisualStudio.Package.TokenColor>列挙体は、キーワードと演算子などのさまざまな言語要素に対応する名前付きのインデックスを多数提供します。 項目が含まれる、カスタムの配色可能な項目の一覧と一致する場合、<xref:Microsoft.VisualStudio.Package.TokenColor>列挙体をだけ使用列挙色としての各トークンです。 ただし、追加の配色可能なアイテムがある場合、またはその順序で既存の値を使用したくない、ニーズに合うよう、そのリストに該当するインデックスを返すカスタムの配色可能な項目一覧を配置できます。 インデックスをキャストするようにしてください、<xref:Microsoft.VisualStudio.Package.TokenColor>で格納するときに、<xref:Microsoft.VisualStudio.Package.TokenInfo>構造体。[!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)]インデックスのみが表示されます。  
  
### <a name="example"></a>例  
 次の例は、スキャナーが 3 つのトークンの種類を識別する方法を示しています。 数字、句読点、および識別子 (数または区切り記号ではないもの)。 この例では、例示を目的としてのみが、包括的なパーサーとスキャナーの実装を表していません。 あることを前提としていますが、`Lexer`クラス、`GetNextToken()`文字列を返すメソッド。  
  
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
 [従来の言語サービスの機能](../../extensibility/internals/legacy-language-service-features1.md)   
 [従来の言語サービス パーサーとスキャナー](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [従来の言語サービスの登録](../../extensibility/internals/registering-a-legacy-language-service1.md)

