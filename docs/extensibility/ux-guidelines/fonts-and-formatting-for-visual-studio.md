---
title: "Visual Studio のフォントと書式 |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5a252e22cda234f6a45bee084522b2add2bafada
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Visual Studio のフォントと書式
##  <a name="BKMK_TheEnvironmentFont"></a>環境フォント  
 Visual Studio 内のすべてのフォントは、カスタマイズのユーザーに公開する必要があります。 主に、これには、**フォントおよび色** ページで、**ツール > オプション**ダイアログ。 フォントの設定の 3 つのカテゴリは次のとおりです。  
  
-   **環境フォント**-IDE (統合開発環境) のプライマリ フォント ダイアログ ボックス、メニューのツール ウィンドウおよびドキュメント ウィンドウを含む、すべてのインターフェイス要素を使用します。 既定では、環境フォントは現在のバージョンの Windows で 9 pt Segoe UI として表示されるシステム フォントに関連付けられています。 インターフェイスのすべての要素の 1 つのフォントを使用すると、IDE 全体で一貫したフォントの外観を確認できます。  
  
-   **テキスト エディター** -ことでコードおよびその他の画面エディターのテキスト ベース カスタマイズできるテキスト エディターで要素をページに**ツール > オプション**です。  
  
-   **特定のコレクション**-独自の設定 ページで、設計に特有のフォントが公開されるインターフェイス要素のユーザーによるカスタマイズを提供しているデザイナーのウィンドウが画面**ツール > オプション**です。  
  
### <a name="editor-font-customization-and-resizing"></a>エディターのフォントのカスタマイズおよびサイズ変更  
 ユーザー多くの場合を拡大またはサイズや、必要に応じて、設定は、全般的なユーザー インターフェイスの独立したエディターのテキストの色を拡大します。 組織内またはデザイナー/エディターの一部として表示されるような要素で環境フォントを使用するためには、以下のいずれかのフォントが変更されたときに予期しない動作に注意する必要です。  
  
 含まれていませんがエディターに表示される UI 要素の作成時に、*コンテンツ*、環境フォントとテキストのフォントを使用して、予測可能な方法で要素のサイズを変更できるようにすることが重要です。  
  
1.  コード内のテキスト エディター、テキスト フォントの設定がコードのサイズを変更し、エディターのテキストのズーム レベルに対応します。  
  
2.  インターフェイスの他のすべての要素では、環境フォントの設定に関係している必要があります、環境内のグローバル変更に対応しています。 これが含まれます (に限定されません)。  
  
    -   コンテキスト メニューのテキスト  
  
    -   エディターの表示要素内のテキストなどの電球メニューのテキスト、クイック検索エディター ウィンドウで、およびウィンドウへの移動  
  
    -   ようなダイアログ ボックス内のテキストにラベルを付ける**ファイル内の検索**または**リファクタリング**  
  
### <a name="accessing-the-environment-font"></a>環境フォントにアクセスします。  
 ネイティブ モードまたは WinForms のコードで環境フォントをメソッドを呼び出すことによってアクセスできる`IUIHostLocale::GetDialogFont`からインターフェイスのクエリを実行した後、`SID_SUIHostLocale`サービス。  
  
 Windows Presentation Foundation (WPF) では、シェルからダイアログ ウィンドウ クラスを派生させる`DialogWindow`WPF のではなくクラス`Window`クラスです。  
  
 XAML では、コードは、次のようになります。  
  
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
  
 (交換`Microsoft.VisualStudio.Shell.11.0`MPF dll の現在のバージョンにします)。  
  
 ダイアログを表示するには、呼び出す"`ShowModal()`"経由でクラスに`ShowDialog()`です。 `ShowModal()`により、親ウィンドウで、ダイアログ ボックスの中心は、シェルで正しいモーダル状態を設定します。  
  
 コードは次のとおりです。  
  
```  
MyWindow window = new MyWindow();  
window.ShowModal()  
```  
  
 `ShowModal`ブール値を返します。 (null 許容のブール値) で、 `DialogResult`、必要な場合に使用されます。 戻り値は true を設定すると、ダイアログ ボックスが閉じられました**OK**です。  
  
 独自のダイアログ ボックスではありませんし、ホストされている一部 WPF UI を表示する必要がある場合`HwndSource`、ポップアップ ウィンドウ、または Win32/WinForms の親ウィンドウの WPF 子ウィンドウなどを設定する必要があります、`FontFamily`と`FontSize`WPF e のルート要素にlement です。 (シェル メイン ウィンドウで、プロパティを設定するが、過去の継承されません、 `HWND`)。 シェルは、プロパティをバインドする、次のようにリソースを提供します。  
  
```  
<Setter property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />  
<Setter property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />  
```  
  
###  <a name="BKMK_Formatting"></a>書式設定 (スケーリング/太字) リファレンス  
 一部のダイアログは、特定のテキストを太字や環境フォント以外のサイズが必要です。 環境フォントよりも大きいフォントが、以前は、各としてコード化された"`environment font +2`"または同様です。 提供されているコード スニペットを使用して、高 DPI モニターをサポートおよび (ライト Semilight など) の重みと正しいサイズで表示するテキストが常に表示されることを確認します。  
  
> **注: 書式設定を適用する前に確認のガイダンスに従っている[テキストのスタイル](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)です。**  
  
 環境フォントを拡張するためには、TextBlock または記載されているラベルのスタイルを設定します。 適切なサイズや重量のバリエーションを含め、適切なフォントが生成それぞれこれらのコード スニペットを適切に使用されます。  
  
 ここで"`vsui`"名前空間への参照は、 `Microsoft.VisualStudio.Shell`:  
  
```  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0" 
```  
  
#### <a name="375-environment-font--light"></a>375% 環境フォント + Light  
 **として表示されます:** 34 pt Segoe UI Light  
 **使用:** (まれな) 一意ブランド化された UI と同様に、スタート ページで

 **プロシージャ コード:**場所`textBlock`は、以前に定義された TextBlock と`label`以前に定義されたラベルします。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);  
```  
  
 **XAML:** TextBlock またはラベルのスタイルを示すように設定します。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>  
```  
  
#### <a name="310-environment-font--light"></a>310% 環境フォント + Light  
 **として表示されます:** 28 pt Segoe UI Light   
 **使用:**大きな署名ダイアログ タイトル、メイン レポートの見出し  
  
 **プロシージャ コード:**場所`textBlock`は、以前に定義された TextBlock と`label`以前に定義されたラベルします。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);    
```  
  
 **XAML:** TextBlock またはラベルのスタイルを示すように設定します。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>     
```  
  
#### <a name="200-environment-font--semilight"></a>200% 環境フォント + Semilight  
 **として表示されます:** 18 pt Segoe UI Semilight    
 **使用:**小見出し、小規模および中規模のダイアログ ボックスのタイトル  
  
 **プロシージャ コード:**場所`textBlock`は、以前に定義された TextBlock と`label`以前に定義されたラベルします。 
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);    
```  
  
 **XAML:** TextBlock またはラベルのスタイルを示すように設定します。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>    
```  
  
#### <a name="155-environment-font"></a>155% 環境フォント  
 **として表示されます:** 14 pt Segoe UI    
 **使用:**ドキュメント内のセクションの見出しと共に UI またはレポート  
  
 **プロシージャ コード:**場所`textBlock`は、以前に定義された TextBlock と`label`以前に定義されたラベルします。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);    
```  
  
 **XAML:** TextBlock またはラベルのスタイルを示すように設定します。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>  
```  
  
#### <a name="133-environment-font"></a>133% 環境フォント  
 **として表示されます:** 12 pt Segoe UI    
 **使用:**署名ダイアログおよびドキュメントのより小さな小見出しでも UI  
  
 **プロシージャ コード:**場所`textBlock`は、以前に定義された TextBlock と`label`以前に定義されたラベルします。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);    
```  
  
 **XAML:** TextBlock またはラベルのスタイルを示すように設定します。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>    
```  
  
#### <a name="122-environment-font"></a>122% 環境フォント  
 **として表示されます:** 11 pt Segoe UI    
 **使用:**署名ダイアログの見出しのセクションで、ツリー ビューで、垂直タブ ナビゲーション ノードの上位  
  
 **プロシージャ コード:**場所`textBlock`は、以前に定義された TextBlock と`label`以前に定義されたラベルします。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);    
```  
  
 **XAML:** TextBlock またはラベルのスタイルを示すように設定します。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>    
```  
  
#### <a name="environment-font--bold"></a>環境フォント + 太字  
 **として表示されます:**太字になっている 9 pt Segoe UI    
 **使用:**でも UI のラベルと署名のダイアログ ボックス、レポート、およびドキュメントの小見出し  
  
 **プロシージャ コード:**場所`textBlock`は、以前に定義された TextBlock と`label`以前に定義されたラベルします。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironmentBoldStyleKey);    
```  
  
 **XAML:** TextBlock またはラベルのスタイルを示すように設定します。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>    
```  
  
### <a name="localizable-styles"></a>ローカライズ可能なスタイル  
 場合によっては、ローカライザーは東アジア言語のテキストから太字の削除など、別のロケールを使用する場合は、フォント スタイルを変更する必要があります。 フォント スタイルのローカリゼーションを可能にするには、これらのスタイルが .resx ファイル内で必要があります。 これを実行しても、Visual Studio のフォーム デザイナーでのフォントのスタイルを編集する最善の方法では、デザイン時にフォント スタイルを明示的に設定します。 フォントが完全なオブジェクトを作成し、親のフォントの継承を停止するように思えるかもしれません、FontStyle プロパティのみを使用してフォント設定をします。  
  
 ダイアログ フォームのフックするために`FontChanged`イベント。 `FontChanged`イベント、すべてのコントロールについて説明し、そのフォントが設定されているかどうかは確認します。 設定されている場合は、フォームのフォントとコントロールの前のフォント スタイルに基づいて新しいフォントを変更します。 コードでこの例を示します。  
  
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
  
 このコードを使用して、フォームのフォントが更新されると、コントロールのフォントもに更新されますが保証されます。 インスタンスを取得するダイアログ ボックスが失敗するため、このメソッドをフォームのコンス トラクターから呼び出されますが`IUIService`と`FontChanged`イベントは起動しません。 フック`FontChanged`ダイアログ ボックスが既に開いている場合でも、新しいフォントを動的に取得するダイアログが許可されます。  
  
### <a name="testing-the-environment-font"></a>環境フォントのテスト  
 UI が環境フォントを使用して、サイズの設定を尊重を開きます**ツール > オプション > 環境 > フォントおよび色**「環境フォント」を選択し、"設定の表示:"ドロップ ダウン メニュー。  
  
 ![フォントおよび色の設定、ツールで&gt;オプション ダイアログ ボックス](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201 a_OptionsFonts")<br />フォントおよび色の設定、ツールで&gt;オプション ダイアログ ボックス
  
 フォント サイズを既定値とは非常に異なるものに設定します。 明白な UI が更新されないが、("Times New Roman") などのセリフ フォントを選択し、非常に大きいサイズを設定します。 次に、環境を考慮することを確認するように UI をテストします。 ライセンス ダイアログを使用する例を次に示します。  
  
 ![環境フォントを考慮せず UI テキストの例の](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201 b_WrongFontDialog")<br />環境フォントを考慮せず UI テキストの例
  
 この場合、「製品情報」、「ユーザー情報」が、このフォントを考慮しはありません。 場合によっては、明示的な設計の選択肢可能性がありますが、赤線仕様の一部として、明示的なフォントが指定されていない場合、バグであることができます。  
  
 フォントをリセットするには、をクリックして「既定値を使用」**ツール > オプション > 環境 > フォントおよび色**です。  
  
##  <a name="BKMK_TextStyle"></a>テキストのスタイル  
 テキストのスタイルは、フォント サイズ、太さ、および大文字小文字の区別を参照します。 実装のガイダンスについては、次を参照してください。[環境フォント](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)です。  
  
### <a name="text-casing"></a>テキストの大文字小文字の区別  
  
#### <a name="all-caps"></a>すべて大文字  
 タイトルまたは Visual Studio でのラベルをすべて大文字を使用しないでください。  
  
#### <a name="all-lowercase"></a>すべて小文字  
 使用しないでくださいすべて小文字のタイトルまたは Visual Studio でのラベル。  
  
#### <a name="sentence-and-title-case"></a>文とタイトル ケース  
 Visual Studio でのテキストには、タイトル ケースまたは文の場合も、状況に応じてを使用する必要があります。  
  
|先頭文字が大文字を使用します。|文の用途:|  
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
 タイトル ケースは、ほとんどまたはすべての語句内の単語の最初の文字が大文字で入力スタイルです。 Visual Studio で、多くの項目を含むタイトル ケースは使用します。  
  
-   **ツール ヒントです。** 例:「プレビュー選択した項目」  
  
-   **列のヘッダー。** 応答例:"システム"  
  
-   **メニュー項目。** 例:「すべて保存する」  
  
 大文字を使用する場合は、単語を大文字に変換して小文字のままにするためのガイドライン次があります。  
  
|大文字|コメントと例|  
|---------------|---------------------------|  
|すべての名詞||  
|すべての動詞|「は」その他のフォームなどの"be"|  
|すべて指定する副詞|「以上」、"When"を含む|  
|すべての形容詞|"This"および「を」を含む|  
|すべての代名詞|など、格「、」と「は、」代名詞の省略形「、」と動詞"is"|  
|品詞に関係なく、最初と最後の単語||  
|動詞句の一部である前置詞|「すべてのウィンドウを閉じる」または「システムのシャット ダウン」|  
|頭字語のすべての英字|HTML、XML、URL、IDE、RGB|  
|同じ重みであれば、単語または名詞または適切な形容詞である場合、2 つ目の複合語でワードします。|前の Microsoft ソフトウェアの相互参照は、読み取り/書き込みアクセス、実行時|  
  
|小文字|例|  
|---------------|--------------|  
|別の品詞または最初の単語を変更する分詞形である場合に、複合語で 2 番目の単語|再開の方法|  
|この記事のタイトルの最初の単語は、いずれかの場合を除き、|a、an、the|  
|接続詞を調整します。|のも、または|  
|動詞の句の外部で 4 つ以下の文字の文字が含まれる前置詞|上の場合と同様の上部の出力|  
|「を」無限長の句で使用する場合|「、ハード_ディスクをフォーマットする方法」|  
  
##### <a name="sentence-case"></a>文の場合  
 文のケースの文の最初の単語のみが大文字で入力、および任意の固有名詞と代名詞は書き込み用の標準的な大文字と小文字メソッドは、"I"です。 一般に、文は世界中のユーザーを読み取る、特にときに、コンテンツによって変換されます、マシンを簡単にありません。 文の用途:  
  
1.  **ステータス バー メッセージです。** 単純な場合、つまり、され、ステータス情報だけを提供します。 例:「プロジェクト ファイルの読み込み」  
  
2.  **その他のすべての UI 要素**ラベル、チェック ボックス、ラジオ ボタンなど、ボックスの項目を一覧表示します。 例:「項目をすべて選択リストで」  
  
### <a name="text-formatting"></a>テキストの書式設定  
 Visual Studio 2013 で既定の書式がによって制御される[環境フォント](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)です。 このサービスにより、IDE (統合開発環境) 全体で一貫したフォントの外観と、ユーザーの一貫した使用環境を保証するために使用する必要があります。  
  
 Visual Studio フォント サービスによって使用される既定のサイズは、Windows から取得され、9 pt として表示されます。  
  
 環境フォントを書式設定を適用することができます。 このトピックの内容方法と場所スタイルを使用します。 実装についてを参照してください[環境フォント](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)です。  
  
#### <a name="bold-text"></a>太字のテキスト  
 太字のテキストは、Visual Studio でので、慎重に使用され、用に予約する必要があります。  
  
-   ウィザードの質問ラベル  
  
-   ソリューション エクスプ ローラーで、アクティブなプロジェクトを指定します。  
  
-   プロパティの [ツール] ウィンドウで値のオーバーライド  
  
-   Visual Basic エディターのドロップダウン リストに特定のイベント  
  
-   web ページの ドキュメント アウトライン内のサーバーで生成されたコンテンツ  
  
-   複雑なダイアログまたはデザイナーの UI セクション ヘッダー  
  
#### <a name="italics"></a>[斜体]  
 Visual Studio では、斜体または太字になっているのいずれかの斜体文字は使用しません。  
  
#### <a name="color"></a>色  
  
-   青はハイパーリンク (ナビゲーションとコマンド実行) の予約されており、印刷の向きに使用することはありません。  
  
-   大規模な見出し (環境フォント x 155% 以上) は、目的のための色に設定できます。  
  
    -   Visual Studio の UI の署名に視覚的な効果を提供するには  
  
    -   特定の部分に注目するには  
  
    -   標準の濃い灰色/黒環境テキストの色のリリーフを提供するには  
  
-   見出しの色には、既存 Visual Studio のブランドの色、主に、メイン紫、#FF68217A を利用します。  
  
-   準拠する必要がありますを見出しで色を使用する場合、 [Windows 色ガイドライン](https://msdn.microsoft.com/en-us/library/dn742482.aspx)コントラスト比やその他のユーザー補助機能に関する考慮事項など、します。  
  
### <a name="font-size"></a>Font Size  
 Visual Studio の UI の設計では、複数の空白文字で軽量の外観を備えています。 可能であれば、chrome とタイトル バー削減されたり削除します。 情報密度は、Visual Studio での要件は、文字体裁引き続きより多くの行間隔とフォント サイズ、および重みのバリエーションに重点を置いて、重要になります。  
  
 次の表には、デザインの詳細と Visual Studio で使用される表示フォントを視覚的な例が含まれています。 いくつか表示フォントのバリエーションは、サイズと Semilight などの外観にコード化された光の重みの両方があります。  
  
 すべての表示のフォントの実装コード スニペットは含まれて[(スケーリング/太字) 参照を書式設定](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)です。  
  
#### <a name="375-environment-font--light"></a>375% 環境フォント + Light  
  
|||  
|-|-|  
|**使用法:**まれです。 一意なブランド化された UI のみです。<br /><br /> **操作を行います。**<br /><br /> -のみ大文字を使用します。<br />-常に使用軽量<br /><br /> **できません：**<br /><br /> 使い UI のスタート ページなどの UI の署名以外<br />-太字、斜体、または太字斜体<br />本文の使用<br />ツール ウィンドウで使用します。|**として表示されます:** 34 pt Segoe UI Light<br /><br /> **ビジュアルの使用例:**<br /><br /> *使用されていません。スタート ページで使用できます。*|  
  
#### <a name="310-environment-font--light"></a>310% 環境フォント + Light  
  
|||  
|-|-|  
|**使用法:**<br /><br /> 署名のダイアログ ボックスより大きな見出し<br />-メイン レポートの見出し<br /><br /> **操作を行います。**<br /><br /> -のみ大文字を使用します。<br />-常に使用軽量<br /><br /> **できません：**<br /><br /> 使い UI のスタート ページなどの UI の署名以外<br />-太字、斜体、または太字斜体<br />本文の使用<br />ツール ウィンドウで使用します。|**として表示されます:** 28 pt Segoe UI Light<br /><br /> **ビジュアルの使用例:**<br /><br /> ![310% 環境フォント &#43; の例Light の見出し](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202 a_EF310")|  
  
#### <a name="200-environment-font--semilight"></a>200% 環境フォント + Semilight  
  
|||  
|-|-|  
|**使用法:**<br /><br /> -小見出し<br />小規模および中規模のダイアログ ボックスのタイトル<br /><br /> **操作を行います。**<br /><br /> -のみ大文字を使用します。<br />-常に Semilight 重み付けを使用します。<br /><br /> **できません：**<br /><br /> -太字、斜体、または太字斜体<br />本文の使用<br />ツール ウィンドウで使用します。|**として表示されます:** 18 pt Segoe UI Semillight<br /><br /> **ビジュアルの使用例:**<br /><br /> ![#43; (&)、200% 環境フォントの例Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202 b_EF200")|  
  
#### <a name="155-environment-font"></a>155% 環境フォント  
  
|||  
|-|-|  
|**使用法:**<br /><br /> のドキュメント内セクションの見出しと共に UI<br />-レポート<br /><br /> **操作を行います**のみ大文字を使用。<br /><br /> **できません：**<br /><br /> -太字、斜体、または太字斜体<br />本文の使用<br />-Visual Studio の標準コントロールで使用します。<br />ツール ウィンドウで使用します。|**として表示されます:** 14 pt Segoe UI<br /><br /> **ビジュアルの使用例:**<br /><br /> ![155% 環境フォントの見出しの例](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202 c_EF155")|  
  
#### <a name="133-environment-font"></a>133% 環境フォント  
  
|||  
|-|-|  
|**使用法:**<br /><br /> 署名のダイアログ ボックスで小さく小見出し<br />にドキュメント内より小さな小見出しでも UI<br /><br /> **操作を行います**のみ大文字を使用。<br /><br /> **できません：**<br /><br /> -太字、斜体、または太字斜体<br />本文の使用<br />-Visual Studio の標準コントロールで使用します。<br />ツール ウィンドウで使用します。|**として表示されます:** 12 pt Segoe UI<br /><br /> **ビジュアルの使用例:**<br /><br /> ![133% 環境フォントの見出しの例](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202 d_EF133")|  
  
#### <a name="122-environment-font"></a>122% 環境フォント  
  
|||  
|-|-|  
|**使用法:**<br /><br /> 署名のダイアログ ボックスのセクション見出し<br />のツリー ビュー内最上位ノード<br />-垂直タブ ナビゲーション<br /><br /> **操作を行います**のみ大文字を使用。<br /><br /> **できません：**<br /><br /> -太字、斜体、または太字斜体<br />本文の使用<br />-Visual Studio の標準コントロールで使用します。<br />ツール ウィンドウで使用します。|**として表示されます:** 11 pt Segoe UI<br /><br /> **ビジュアルの使用例:**<br /><br /> ![122% 環境フォントの見出しの例](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202 e_EF122")|  
  
#### <a name="environment-font--bold"></a>環境フォント + 太字  
  
|||  
|-|-|  
|**使用法:**<br /><br /> -ラベルや署名ダイアログの小見出し<br />-ラベルやレポートでの小見出し<br />-ラベルとそのドキュメント内の小見出しおよび UI<br /><br /> **操作を行います。**<br /><br /> -のみ大文字を使用します。<br />-太字を使用します。<br /><br /> **できません：**<br /><br /> -斜体または太字斜体<br />本文の使用<br />-Visual Studio の標準コントロールで使用します。<br />ツール ウィンドウで使用します。|**として表示されます:**太字になっている 9 pt Segoe UI<br /><br /> **ビジュアルの使用例:**<br /><br /> ![#43; (&)、環境フォントの例太字の見出し](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202 f_EFB")|  
  
#### <a name="environment-font"></a>環境フォント  
  
|||  
|-|-|  
|**使用法:**その他のすべてのテキスト<br /><br /> **操作を行います**のみ大文字を使用。<br /><br /> **しない:**斜体太字斜体または|**として表示されます:** 9 pt Segoe UI<br /><br /> **ビジュアルの使用例:**<br /><br /> ![環境フォントの例](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202 g_EF")|  
  
### <a name="padding-and-spacing"></a>余白および間隔  
 見出しでは、それらに適切な強調の周囲のスペースが必要です。 この領域は、ポイントのサイズと水平方向のルールや環境フォントのテキストの行など、見出し、近くの他に何がに応じて異なります。  
  
-   単独で、見出しの理想的な余白は、大文字の文字の高さの容量の 90% にする必要があります。 たとえば、28 pt Segoe UI Light の見出しは 26 pt のキャップの高さを持ち 23 pt、または約 31 ピクセル、余白が約する必要があります。  
  
-   最小の周囲のスペース、見出しには、大文字の文字の高さの 50% をする必要があります。 ルールまたは他の緊密な調整要素は、見出しと共に発生する場合は、領域が少なくを使用する可能性があります。  
  
-   太字になっている環境フォントのテキストは、既定の行の高さの間隔とスペースに従う必要があります。  
  
## <a name="see-also"></a>関連項目  
 [MSDN: フォント (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742483\(v=vs.85\).aspx)   
 [MSDN: ユーザー インターフェイスのテキスト (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)