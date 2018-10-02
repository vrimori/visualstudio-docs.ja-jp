---
title: Visual Studio のフォントと書式 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f563bf607c0951d1ecaaeb8cc08ccdd64f5f0ad
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548977"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Visual Studio のフォントと書式
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[フォントと Visual Studio の書式](https://docs.microsoft.com/visualstudio/extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio)します。  
  
##  <a name="BKMK_TheEnvironmentFont"></a> 環境フォント  
 Visual Studio 内のすべてのフォントは、カスタマイズのユーザーに公開する必要があります。 これは、主に、**フォントおよび色**ページで、**ツール > オプション**ダイアログ。 フォントの設定の 3 つの主なカテゴリは次のとおりです。  
  
-   **環境フォント**— プライマリ フォント IDE (統合開発環境) をダイアログ ボックス、メニューのツール ウィンドウ、およびドキュメント ウィンドウを含む、すべてのインターフェイス要素を使用します。 既定では、環境フォントは、最新バージョンの Windows での 9 pt Segoe UI として表示されるシステム フォントに関連付けられています。 1 つのフォントを使用して、すべてのインターフェイス要素により、IDE 全体で一貫性のあるフォントの外観を確認します。  
  
-   **テキスト エディター** — ことサーフェスでは、コードおよびその他のテキスト ベースのエディターをカスタマイズできますテキスト エディターで要素をページに**ツール > オプション**します。  
  
-   **特定のコレクション**: ユーザー インターフェイス要素のカスタマイズは、設計に固有のフォントで公開される可能性が提供するデザイナーのウィンドウの画面で、独自の設定 ページで**ツール > オプション**します。  
  
### <a name="editor-font-customization-and-resizing"></a>エディターのフォントのカスタマイズとサイズ変更  
 ユーザー多くの場合は拡大またはズーム サイズやに応じて、全般的なユーザー インターフェイスの独立したエディターのテキストの色。 環境フォント内、またはエディターとデザイナーの一部として表示される要素を使用しているためには、これらのフォントの分類が変更された場合に想定される動作に注意してください。  
  
 含まれていませんが、エディターで表示される UI 要素を作成するときに、*コンテンツ*、環境フォントとテキストのフォントを使用して、予測可能な方法で要素のサイズを変更できるようにすることが重要です。  
  
1.  コード エディターでテキストのコード テキストのフォント設定サイズを変更し、エディターのテキストのズーム レベルに対応します。  
  
2.  インターフェイスの他のすべての要素は、環境フォントの設定に関係している必要があり、グローバル環境の変更に応答します。 これが含まれています (ただしに限定されません)。  
  
    -   コンテキスト メニューのテキスト  
  
    -   電球メニュー テキスト、クイックなどのエディター表示要素内のテキストがエディター ウィンドウを検索して、ウィンドウに移動します  
  
    -   ファイルまたはリファクタリングには、検索などのダイアログ ボックスのラベル テキスト  
  
### <a name="accessing-the-environment-font"></a>環境フォントへのアクセス  
 ネイティブ モードまたは WinForms のコードでメソッドを呼び出すことによって、環境フォントをアクセスできる**IUIHostLocale::GetDialogFont** SID_SUIHostLocale サービスからインターフェイスを照会しました。  
  
 Windows Presentation Foundation (WPF) では、シェルからのダイアログ ウィンドウ クラスの派生**ダイアログ ウィンドウ**WPF のではなくクラス**ウィンドウ**クラス。  
  
 XAML、コードは、次のようになります。  
  
```  
<ui:DialogWindow  
    x:Class"MyNameSpace.MyWindow"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"  
    ShowInTaskbar="False"  
    WindowStartupLocation="CenterOwner"  
    Title="My Dialog">  
</ui:DialogWindow>  
  
code behind:  
  
internal partial class WebConfigModificationWindow : DialogWindow  
{  
}  
  
```  
  
 (置換`Microsoft.VisualStudio.Shell.11.0`MPF dll の現在のバージョンとします)。  
  
 ダイアログ ボックスを表示するに"**ShowModal()**"経由でクラスの**ShowDialog()** します。 **ShowModal()** シェルで適切なモーダル状態を設定すると、ダイアログ ボックスと親ウィンドウの中央に配置します。  
  
 コードは次のとおりです。  
  
```  
MyWindow window = new MyWindow();  
window.ShowModal()  
  
```  
  
 **ShowModal**ブール値を返します。 (null 許容のブール値) で、 **DialogResult**、必要な場合に使用されます。 戻り値はで、ダイアログ ボックスが閉じられた場合は true。 **OK**します。  
  
 独自のダイアログ ボックスではありませんし、ホストされている WPF の UI を表示する必要がある場合**HwndSource**、ポップアップ ウィンドウや Win32/WinForms の親ウィンドウの WPF の子ウィンドウなどを設定する必要があります、 **FontFamily**と**FontSize** WPF 要素のルート要素。 (シェルのメイン ウィンドウでプロパティを設定するが、過去の HWND を継承できません。) シェルでは、プロパティはバインドする、このようなリソースを提供します。  
  
```  
<Setter property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />  
<Setter property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />  
  
```  
  
###  <a name="BKMK_Formatting"></a> (スケール/太字) の参照を書式設定  
 一部のダイアログでは、特定のテキストを太字または環境フォント以外のサイズが必要です。 以前は、「環境フォント +2」としてコード化されたまたは類似した環境フォントよりも大きいフォントができました。 提供されているコード スニペットを使用して、高 DPI のモニターのサポートし、表示テキストが常に適切なサイズと重量 (Light Semilight など) に表示されることを確認します。  
  
> **注: 書式設定を適用する前に確認の指針をフォローしている[テキストのスタイル](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)します。**  
  
 環境フォントをスケーリングするには、TextBlock またはとおりのラベルのスタイルを設定します。 適切なサイズや重量のバリエーションを含む適切なフォントを適切に使用、これらのコード スニペットの各生成されます。  
  
 場所"vsui"Microsoft.VisualStudio.Shell 名前空間への参照を示します。  
  
```  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
```  
  
#### <a name="375-environment-font--light"></a>375% 環境フォント + Light  
 **として表示されます:** 34 pt Segoe UI Light  
  
 **使用:** (まれな) 一意ブランド化された UI、スタート ページのように  
  
 **手続き型コード:** 場所"textBlock"は、以前に定義された TextBlock と"label"は、以前に定義されたラベル。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** に示すように TextBlock やラベルのスタイルを設定します。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>  
  
```  
  
#### <a name="310-environment-font--light"></a>310% 環境フォント + Light  
 **として表示されます:** 28 pt Segoe UI Light  
  
 **使用:** 大きな署名ダイアログのタイトル、メイン レポートの見出し  
  
 **手続き型コード:** 場所"textBlock"は、以前に定義された TextBlock と"label"は、以前に定義されたラベル。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** に示すように TextBlock やラベルのスタイルを設定します。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>  
  
```  
  
#### <a name="200-environment-font--semilight"></a>200% 環境フォント + Semilight  
 **として表示されます:** 18 pt Segoe UI Semilight  
  
 **使用:** 小見出し、小規模および中規模のダイアログ ボックスのタイトル  
  
 **手続き型コード:** 場所"textBlock"は、以前に定義された TextBlock と"label"は、以前に定義されたラベル。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** に示すように TextBlock やラベルのスタイルを設定します。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>  
  
```  
  
#### <a name="155-environment-font"></a>155% 環境フォント  
 **として表示されます:** 14 pt Segoe UI  
  
 **使用:** ドキュメントのセクション見出しも UI またはレポート  
  
 **手続き型コード:** 場所"textBlock"は、以前に定義された TextBlock と"label"は、以前に定義されたラベル。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** に示すように TextBlock やラベルのスタイルを設定します。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>  
  
```  
  
#### <a name="133-environment-font"></a>133% 環境フォント  
 **として表示されます:** 12 pt Segoe UI  
  
 **使用:** 署名ダイアログとドキュメントに小規模な注釈を小見出しも UI  
  
 **手続き型コード:** 場所"textBlock"は、以前に定義された TextBlock と"label"は、以前に定義されたラベル。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** に示すように TextBlock やラベルのスタイルを設定します。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>  
  
```  
  
#### <a name="122-environment-font"></a>122% 環境フォント  
 **として表示されます:** 11 pt Segoe UI  
  
 **使用:** 署名ダイアログの見出しのセクションでトップのツリー ビューで、垂直タブ ナビゲーション ノード  
  
 **手続き型コード:** 場所"textBlock"は、以前に定義された TextBlock と"label"は、以前に定義されたラベル。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** に示すように TextBlock やラベルのスタイルを設定します。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>  
  
```  
  
#### <a name="environment-font--bold"></a>環境フォント + 太字  
 **として表示されます:** 9 pt Segoe UI で太字で表示されます。  
  
 **使用:** も UI のラベルと署名のダイアログ ボックス、レポート、およびドキュメントの小見出し  
  
 **手続き型コード:** 場所"textBlock"は、以前に定義された TextBlock と"label"は、以前に定義されたラベル。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironmentBoldStyleKey);  
  
```  
  
 **XAML:** に示すように TextBlock やラベルのスタイルを設定します。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>  
  
```  
  
### <a name="localizable-styles"></a>ローカライズ可能なスタイル  
 場合によっては、ローカライザーは、異なるロケールから東アジア言語のテキストが太字を削除するなどのフォント スタイルを変更する必要があります。 フォント スタイルのローカライズを可能にするには、これらのスタイルは、.resx ファイル内にする必要があります。 これを実現し、Visual Studio のフォーム デザイナーでのフォント スタイルを編集する最善の方法では、デザイン時にフォント スタイルを明示的に設定します。 これにより、完全なフォント オブジェクトを作成し、親のフォントの継承を停止すると思われる場合があります、FontStyle プロパティだけは、フォントの設定を使用します。  
  
 ソリューションでは、ダイアログ フォームの**FontChanged**イベント。 **FontChanged**イベントは、すべてのコントロールについて説明し、そのフォントが設定されているかどうかは確認します。 設定されている場合は、フォームのフォントとコントロールの以前のフォント スタイルに基づく新しいフォントを変更します。 このコード例を示します。  
  
```  
private void Form1_FontChanged(object sender, System.EventArgs e)  
{  
          SetFontStyles();  
}  
  
/// <summary>  
/// SetFontStyles - This function will iterate all controls on a page  
/// and recreate their font with the desired fontstyle.  
/// It should be called in the OnFontChanged handler (and also in the constructor  
/// in case the IUIService is not available so OnFontChange doesn't fire).  
/// This way, when the VS shell font is given to us the controls that have  
/// a different style for the font (bolded for example) will recreate their font  
/// and use the VS shell font but with a style variation (bolded ...).  
/// </summary>   
protected void SetFontStyles()  
{  
     SetFontStyles(this, this, this.Font);  
}  
  
protected static void SetFontStyles(Control topControl, Control parent, Font referenceFont)  
{  
     foreach(Control c in parent.Controls)  
     {  
          if (c.Controls != null && c.Controls.Count > 0) {  
               SetFontStyles(topControl, c, referenceFont);  
          }  
          if (c.Font != topControl.Font) {  
               c.Font = new Font(referenceFont, c.Font.Style);  
          }  
     }  
}  
```  
  
 このコードを使用するには、フォームのフォントが更新されると、コントロールのフォントもに更新されますが保証されます。 ダイアログ ボックスが失敗するのインスタンスを取得するためも、このメソッドを呼び出して、フォームのコンス トラクターからください**IUIService**と**FontChanged**イベントは起動しません。 フック**FontChanged**ダイアログのダイアログ ボックスが既に開いている場合でも、新しいフォントを動的に選択できるようになります。  
  
### <a name="testing-the-environment-font"></a>環境フォントのテスト  
 UI が、環境フォントを使用して、サイズの設定を尊重ことを確認して、開きます**ツール > オプション > 環境 > フォントおよび色**「環境フォント」を選択し、"設定の表示:"ドロップダウン メニュー。  
  
 ![ツールのフォントおよび色 ページ&#62;オプション ダイアログ ボックス](../../extensibility/ux-guidelines/media/0201-a-optionsfonts.png "0201 a_OptionsFonts")  
  
 **フォントおよび色の設定、ツール > オプション ダイアログ ボックス**  
  
 既定値よりも非常に別のものにフォントを設定します。 明確では UI が更新されないが、("Times New Roman") などのセリフ付きフォントを選択し、非常に大きなサイズを設定します。 次に、環境を考慮することを確認するように UI をテストします。 ライセンスのダイアログを使用する例を次に示します。  
  
 ![環境フォントを使用していないダイアログの例](../../extensibility/ux-guidelines/media/0201-b-wrongfontdialog.png "0201 b_WrongFontDialog")  
  
 **環境フォントを優先しません UI テキストの例**  
  
 この場合は、「ユーザー情報」と「製品情報」が、このフォントを尊重しはありません。 場合によっては、明示的な設計選択では、この可能性がありますの赤線仕様の一部として明示的なフォントが指定されていない場合、バグがあることができます。  
  
 リセットするフォントをクリックして「既定値を使用」**ツール > オプション > 環境 > フォントおよび色**します。  
  
##  <a name="BKMK_TextStyle"></a> テキストのスタイル  
 テキストのスタイルは、フォント サイズ、太さ、および大文字小文字の区別を参照します。 実装のガイダンスについては、次を参照してください。[環境フォント](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)します。  
  
### <a name="text-casing"></a>テキストの大文字小文字の区別  
  
#### <a name="all-caps"></a>すべて大文字  
 タイトルまたは Visual Studio でのラベルをすべて大文字を使用しないでください。  
  
#### <a name="all-lowercase"></a>すべて小文字  
 使用しないでくださいすべて小文字のタイトルまたは Visual Studio でのラベル。  
  
#### <a name="sentence-and-title-case"></a>文とタイトル ケース  
 Visual Studio でのテキストには、タイトル ケースまたは文の場合も、状況に応じてを使用する必要があります。  
  
|先頭文字が大文字を使用します。|ケースは文を使用します。|  
|-------------------------|----------------------------|  
|ダイアログ ボックスのタイトル|ラベル|  
|グループ ボックス|チェック ボックス|  
|メニュー項目|オプション ボタン|  
|コンテキスト メニュー項目|リスト ボックス項目|  
|ボタン|ステータス バー|  
|テーブルのラベル||  
|列ヘッダー||  
|ツールヒント||  
  
##### <a name="title-case"></a>大文字  
 タイトルの場合は、ほとんどまたはすべての語句内の単語の最初の文字が大文字で入力スタイルです。 Visual Studio など、多くの項目の先頭文字が大文字を使用します。  
  
-   **ツールヒント。** 例:「プレビュー選択した項目」  
  
-   **列ヘッダー。** 例:「システム応答」  
  
-   **メニュー項目。** 例:「すべてを保存」  
  
 大文字を使用する場合は、単語を大文字に変換する場合と小文字のままにする場合のガイドライン。  
  
|大文字|コメントと例|  
|---------------|---------------------------|  
|すべての名詞||  
|すべての動詞|"Is"やその他の"be"を含む|  
|すべて指定する副詞|「より」および"When"を含む|  
|すべての形容詞|"This"および"That"を含む|  
|すべての代名詞|など、格「、」も「は、」代名詞の省略形「、」と動詞"is"|  
|品詞に関係なく、最初と最後の単語||  
|前置詞動詞句の一部であります。|「すべての Windows を閉じる」または「システムのシャット ダウン」|  
|頭字語のすべての英字|HTML、XML、URL、IDE、RGB|  
|2 つ目は、名詞または形容詞として解釈の適切なである場合、または単語が同じ重み付け複合語で word します。|相互参照、前の Microsoft ソフトウェア、読み取り/書き込みアクセス、実行時|  
  
|小文字|使用例|  
|---------------|--------------|  
|別の品詞または最初の単語を変更する分詞である場合に、複合語では、2 番目の word|オフの操作方法|  
|この記事のタイトルの最初の単語がある場合を除き、|a、an、the|  
|接続詞を調整します。|nor、または|  
|動詞句以外の 4 つ以下の文字の単語の前置詞|としての上で帯|  
|"To"調べての句で使用する場合|「ハード_ディスクをフォーマットする方法」|  
  
##### <a name="sentence-case"></a>文のケース  
 文のケースの文の最初の単語のみが大文字で入力することで、任意の名詞と代名詞は書き込み用の標準的な大文字と小文字メソッドは、"I" 一般に、文の場合は、世界中のユーザーを読み取る、特にときに、コンテンツによって変換されます、マシンは簡単です。 ケースは文を使用します。  
  
1.  **ステータス バー メッセージです。** これらは、簡単に言えば、簡単なと、ステータス情報だけを提供します。 例:「プロジェクト ファイルを読み込んでいます」  
  
2.  **その他のすべての UI 要素**ラベル、チェック ボックス、ラジオ ボタン、およびボックスの項目を一覧表示します。 例:"すべての項目を選択リストで"  
  
### <a name="text-formatting"></a>テキストの書式設定  
 Visual Studio 2013 で既定の書式がによって制御される、[環境フォント](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)します。 このサービスにより、IDE (統合開発環境) 全体で一貫性のあるフォントの外観を確認し、ユーザーの一貫したエクスペリエンスを保証するために使用する必要があります。  
  
 Visual Studio のフォントのサービスで使用される既定のサイズは、Windows から取得され、9 pt として表示されます。  
  
 環境フォントを書式設定を適用することができます。 このトピックでは、方法と場所について説明します。 スタイルを使用します。 実装についてを参照してください[環境フォント](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)します。  
  
#### <a name="bold-text"></a>太字のテキスト  
 太字のテキストは、Visual Studio で慎重に使用され、用に予約する必要があります。  
  
-   ウィザードで質問ラベル  
  
-   ソリューション エクスプ ローラーでアクティブなプロジェクトを指定します。  
  
-   プロパティの [ツール] ウィンドウで値のオーバーライド  
  
-   Visual Basic エディターのドロップダウン リストで特定のイベント  
  
-   web ページの ドキュメント アウトライン内のサーバーで生成されたコンテンツ  
  
-   セクションのヘッダーの複雑なダイアログまたはデザイナーの UI  
  
#### <a name="italics"></a>[斜体]  
 Visual Studio では、斜体または太字斜体テキストは使用しません。  
  
#### <a name="color"></a>色  
  
-   青では、ハイパーリンク (ナビゲーションとコマンド実行) の予約されており、印刷の向きに使用することはありません。  
  
-   大規模な見出し (環境フォント x 155% 以上) は、次の目的で色付けすることができます。  
  
    -   Visual Studio の UI の署名に視覚的な効果を提供するには  
  
    -   特定の領域に注意を促す  
  
    -   標準的な濃いグレーまたは黒の環境のテキストの色を安全に提供するには  
  
-   見出しの色は、既存 Visual Studio のブランドの色、主にメイン紫色の #FF68217A を活用する必要があります。  
  
-   見出しの色を使用する場合に従う必要があります、 [Windows カラー ガイドライン](https://msdn.microsoft.com/library/dn742482.aspx)コントラスト比やその他のユーザー補助機能に関する考慮事項など、します。  
  
### <a name="font-size"></a>Font Size  
 Visual Studio の UI デザインには、複数の空白文字で軽量の外観が機能します。 可能であれば、chrome とタイトル バーを削減または削除されています。 情報密度は Visual Studio での要件よりオープンの行間やフォント サイズや重量のバリエーションに重点を置いて、重要であるに文字体裁が続行されます。  
  
 次の表には、デザインの詳細と Visual Studio で使用される表示フォントを視覚的な例が含まれています。 いくつか表示フォントのバリエーションは、サイズと Semilight や外観にコード化されたライトなどの重みの両方があります。  
  
 ディスプレイのすべてのフォントの実装のコード スニペットが記載されて[(スケーリング/太字) の参照を書式設定](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)します。  
  
#### <a name="375-environment-font--light"></a>375% 環境フォント + Light  
  
|||  
|-|-|  
|**使用法:** まれです。 一意なブランド化された UI のみです。<br /><br /> **操作を行います。**<br /><br /> -文のケースを使用します。<br />-常に使用して、ライト ウェイト<br /><br /> **できません：**<br /><br /> -使用して UI の署名などのスタート ページの UI 以外<br />-太字、斜体または太字斜体<br />本文テキストの使用<br />-ツール ウィンドウで使用します。|**として表示されます:** 34 pt Segoe UI Light<br /><br /> **ビジュアルの使用例:**<br /><br /> *現在は使用されません。スタート ページで使用できます。*|  
  
#### <a name="310-environment-font--light"></a>310% 環境フォント + Light  
  
|||  
|-|-|  
|**使用法:**<br /><br /> 署名のダイアログ ボックスよりも大きな見出し<br />-メイン レポートの見出し<br /><br /> **操作を行います。**<br /><br /> -文のケースを使用します。<br />-常に使用して、ライト ウェイト<br /><br /> **できません：**<br /><br /> -使用して UI の署名などのスタート ページの UI 以外<br />-太字、斜体または太字斜体<br />本文テキストの使用<br />-ツール ウィンドウで使用します。|**として表示されます:** 28 pt Segoe UI Light<br /><br /> **ビジュアルの使用例:**<br /><br /> ![310% 環境フォントの例&#43;Light の見出し](../../extensibility/ux-guidelines/media/0202-a-ef310.png "0202 a_EF310")|  
  
#### <a name="200-environment-font--semilight"></a>200% 環境フォント + Semilight  
  
|||  
|-|-|  
|**使用法:**<br /><br /> 注釈を小見出し<br />の小規模および中規模のダイアログ タイトル<br /><br /> **操作を行います。**<br /><br /> -文のケースを使用します。<br />-Always Semilight の重みを使用してください。<br /><br /> **できません：**<br /><br /> -太字、斜体または太字斜体<br />本文テキストの使用<br />-ツール ウィンドウで使用します。|**として表示されます:** 18 pt Segoe UI Semillight<br /><br /> **ビジュアルの使用例:**<br /><br /> ![200% 環境フォントの例&#43;Semilight](../../extensibility/ux-guidelines/media/0202-b-ef200.png "0202 b_EF200")|  
  
#### <a name="155-environment-font"></a>155% 環境フォント  
  
|||  
|-|-|  
|**使用法:**<br /><br /> ドキュメントのセクション見出しも UI<br />-レポート<br /><br /> **操作を行います**ユース ケースの文。<br /><br /> **できません：**<br /><br /> -太字、斜体または太字斜体<br />本文テキストの使用<br />-Visual Studio の標準コントロールで使用します。<br />-ツール ウィンドウで使用します。|**として表示されます:** 14 pt Segoe UI<br /><br /> **ビジュアルの使用例:**<br /><br /> ![155% 環境フォントの見出しの例](../../extensibility/ux-guidelines/media/0202-c-ef155.png "0202 c_EF155")|  
  
#### <a name="133-environment-font"></a>133% 環境フォント  
  
|||  
|-|-|  
|**使用法:**<br /><br /> 署名のダイアログ ボックスで小さく小見出し<br />ドキュメントで小さく小見出しも UI<br /><br /> **操作を行います**ユース ケースの文。<br /><br /> **できません：**<br /><br /> -太字、斜体または太字斜体<br />本文テキストの使用<br />-Visual Studio の標準コントロールで使用します。<br />-ツール ウィンドウで使用します。|**として表示されます:** 12 pt Segoe UI<br /><br /> **ビジュアルの使用例:**<br /><br /> ![133% 環境フォントの見出しの例](../../extensibility/ux-guidelines/media/0202-d-ef133.png "0202 d_EF133")|  
  
#### <a name="122-environment-font"></a>122% 環境フォント  
  
|||  
|-|-|  
|**使用法:**<br /><br /> 署名のダイアログ ボックスのセクション見出し<br />のツリー ビュー内最上位ノード<br />垂直タブ ナビゲーション<br /><br /> **操作を行います**ユース ケースの文。<br /><br /> **できません：**<br /><br /> -太字、斜体または太字斜体<br />本文テキストの使用<br />-Visual Studio の標準コントロールで使用します。<br />-ツール ウィンドウで使用します。|**として表示されます:** 11 pt Segoe UI<br /><br /> **ビジュアルの使用例:**<br /><br /> ![122% 環境フォントの見出しの例](../../extensibility/ux-guidelines/media/0202-e-ef122.png "0202 e_EF122")|  
  
#### <a name="environment-font--bold"></a>環境フォント + 太字  
  
|||  
|-|-|  
|**使用法:**<br /><br /> -ラベルや署名ダイアログの小見出し<br />-ラベルやレポートでの小見出し<br />-ラベルで文書の小見出しのあるように UI<br /><br /> **操作を行います。**<br /><br /> -文のケースを使用します。<br />-太字を使用します。<br /><br /> **できません：**<br /><br /> -斜体または太字斜体<br />本文テキストの使用<br />-Visual Studio の標準コントロールで使用します。<br />-ツール ウィンドウで使用します。|**として表示されます:** 9 pt Segoe UI で太字で表示されます。<br /><br /> **ビジュアルの使用例:**<br /><br /> ![環境フォントの例&#43;太字の見出し](../../extensibility/ux-guidelines/media/0202-f-efb.png "0202 f_EFB")|  
  
#### <a name="environment-font"></a>環境フォント  
  
|||  
|-|-|  
|**使用法:** 他のすべてのテキスト<br /><br /> **操作を行います**ユース ケースの文。<br /><br /> **しない:** 斜体または太字斜体|**として表示されます:** 9 pt Segoe UI<br /><br /> **ビジュアルの使用例:**<br /><br /> ![環境フォントの例](../../extensibility/ux-guidelines/media/0202-g-ef.png "0202 g_EF")|  
  
### <a name="padding-and-spacing"></a>パディングとの間隔  
 見出しを適切な強調の周囲の空白が必要です。 この領域は、ポイントのサイズと水平方向の規則など、環境フォント内のテキストの行の見出しの近くには他に何かによって異なります。  
  
-   大文字の文字の高さの容量の 90% を単独で、見出しの理想的な余白があります。 たとえば、28 pt Segoe UI Light の見出しが 26 pt のキャップの高さと 23 pt、(約 31 ピクセル)、余白が約にする必要があります。  
  
-   見出しの周りに最小の空白文字が大文字の高さの 50% があります。 見出しは、ルール、またはその他の密接な調整要素と共に発生する場合、小さい領域を使用できます。  
  
-   環境フォントのテキストを太字で表示されるには、既定行の高さの間隔とパディングを従う必要があります。  
  
## <a name="see-also"></a>関連項目  
 [MSDN: フォント (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742483\(v=vs.85\).aspx)   
 [MSDN: ユーザー インターフェイスのテキスト (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx)

