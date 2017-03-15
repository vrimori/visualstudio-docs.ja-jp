---
title: "フォントおよび Visual Studio の書式設定 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# フォントおよび Visual Studio の書式設定
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="BKMK_TheEnvironmentFont"></a> 環境フォント  
 Visual Studio 内のすべてのフォントは、カスタマイズ用のユーザーに公開する必要があります。 これは、主に行うには、 **フォントおよび色** \] ページで、 **ツール \> オプション** ダイアログ。 フォントの設定の 3 つの主なカテゴリは次のとおりです。  
  
-   **環境フォント** — プライマリ フォント IDE \(統合開発環境\) のダイアログ ボックス、メニューのツール ウィンドウおよびドキュメント ウィンドウを含む、すべてのインターフェイス要素を使用します。 既定では、環境フォントは現在のバージョンの Windows での 9 pt Segoe UI として表示されるシステム フォントに関連付けられます。 すべてのインターフェイス要素の 1 つのフォントを使用してでは、IDE 全体で一貫性のあるフォントの外観を確実できます。  
  
-   **テキスト エディター** \-画面で、コードおよびその他のテキスト ベースのエディターことができます、カスタマイズすること、テキスト エディターでの要素がページに **ツール \> オプション**します。  
  
-   **特定のコレクション** — で独自の設定\] ページでユーザー インターフェイス要素のカスタマイズが設計に固有のフォントを公開することは、デザイナー ウィンドウのサーフェス **ツール \> オプション**します。  
  
### エディターのフォントのカスタマイズとサイズ変更  
 ユーザー多くの場合は拡大、またはサイズや一般的なユーザー インターフェイスに依存しないの意向に合わせて、エディターのテキストの色を拡大します。 組織内またはエディターとデザイナーの一部として表示されるような要素では、環境フォントを使用するためには、以下のいずれかのフォントが変更されると予想される動作に注意してください必要があります。  
  
 含まれていませんがエディターに表示される UI 要素の作成時に、 *コンテンツ*, 、環境フォントとテキストのフォントを使用して、予測可能な方法で要素のサイズを変更できるようにすることが重要です。  
  
1.  コード内のテキスト エディターには、コードのテキストのフォント設定に合わせてサイズが、エディターのテキストのズーム レベルに対応しています。  
  
2.  インターフェイスの他のすべての要素は、環境フォントの設定に関連付けられている必要があり、環境内のグローバル変更に応答します。 これが含まれます \(に制限されていません\)。  
  
    -   コンテキスト メニュー内のテキスト  
  
    -   電球メニュー テキスト、クイックなどのエディター表示要素内のテキストがエディター ウィンドウを検索し、ウィンドウへの移動  
  
    -   ファイルまたはリファクタリングの検索などのダイアログ ボックス内のテキストにラベルを付ける  
  
### 環境フォントにアクセスします。  
 ネイティブ モードまたは WinForms のコードで環境フォントをメソッドを呼び出すことによってアクセスできる **IUIHostLocale::GetDialogFont** SID\_SUIHostLocale サービスからインターフェイスを照会した後です。  
  
 Windows Presentation Foundation \(WPF\) では、シェルからのダイアログ ウィンドウ クラスの派生 **ダイアログ ウィンドウ** WPF のではなくクラス **ウィンドウ** クラスです。  
  
 XAML では、コードは、次のようになります。  
  
```  
<ui:DialogWindow x:Class"MyNameSpace.MyWindow" xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0" ShowInTaskbar="False" WindowStartupLocation="CenterOwner" Title="My Dialog"> </ui:DialogWindow> code behind: internal partial class WebConfigModificationWindow : DialogWindow { }  
  
```  
  
 \(置換 `Microsoft.VisualStudio.Shell.11.0` MPF dll の現在のバージョンとします\)。  
  
 ダイアログ ボックスを表示するに"**ShowModal\(\)**"でクラスに **ShowDialog\(\)**します。**ShowModal\(\)** シェルでは、適切なモーダル状態を設定、により、ダイアログ ボックスが親ウィンドウの中央に配置します。  
  
 コードは次のとおりです。  
  
```  
MyWindow window = new MyWindow(); window.ShowModal()  
  
```  
  
 **ShowModal** ブール値を返します。 \(null 許容のブール値\) で、 **DialogResult**, 、必要な場合に使用されます。 戻り値は true を設定すると、ダイアログ ボックスが閉じられました **OK**します。  
  
 独自のダイアログ ボックスではなく、ホストされる WPF の UI を表示する必要がある場合 **HwndSource**, 、ポップアップ ウィンドウや Win32\/WinForms の親ウィンドウの WPF の子ウィンドウなどを設定する必要がある、 **FontFamily** と **FontSize** WPF 要素のルート要素にします。 \(シェルは、メイン ウィンドウのプロパティを設定が過去の HWND 継承されません\)。 シェルは、プロパティが連結される、次のようにリソースを提供します。  
  
```  
<Setter property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" /> <Setter property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />  
  
```  
  
###  <a name="BKMK_Formatting"></a> \(拡大\/縮小\/太字\) 参照を書式設定  
 一部のダイアログは、特定のテキストを太字や環境フォント以外のサイズが必要です。 以前は、環境フォントよりも大きいフォントは、「環境フォント \+2」としてコード化されたまたは類似したでした。 提供されているコード スニペットを使用して、高解像度のモニターをサポートし、表示するテキストが常に適切なサイズと重量 \(Light Semilight など\) が表示されるようにします。  
  
> **注: 書式設定を適用する前に確認で見つかったガイダンスに従っている [テキストのスタイル](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)します。**  
  
 環境フォントを拡張するためには、TextBlock またはとおりのラベルのスタイルを設定します。 適切なサイズおよび重みのバリエーションを含む適切なフォントが適切に使用されたこれらのコード スニペットの各生成されます。  
  
 ここで"vsui"は、Microsoft.VisualStudio.Shell 名前空間への参照を示します。  
  
```  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
```  
  
#### 375% 環境フォント \+ Light  
 **として表示されます:** 34 pt Segoe UI Light  
  
 **の使用:** \(まれな\) 一意なブランド化された UI のようにスタート ページ  
  
 **手続き型コード:** ここで"textBlock"は、以前に定義された TextBlock は、"label"は、以前に定義されたラベル。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** のように TextBlock またはラベルのスタイルを設定します。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>  
  
```  
  
#### 310% 環境フォント \+ Light  
 **として表示されます:** 28 pt Segoe UI Light  
  
 **の使用:** 大きな署名ダイアログ ボックスのタイトル、メイン レポートの見出し  
  
 **手続き型コード:** ここで"textBlock"は、以前に定義された TextBlock は、"label"は、以前に定義されたラベル。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** のように TextBlock またはラベルのスタイルを設定します。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>  
  
```  
  
#### 200% 環境フォント \+ Semilight  
 **として表示されます:** 18 pt Segoe UI Semilight  
  
 **の使用:** 下位、中小規模のダイアログ ボックスのタイトル  
  
 **手続き型コード:** ここで"textBlock"は、以前に定義された TextBlock は、"label"は、以前に定義されたラベル。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** のように TextBlock またはラベルのスタイルを設定します。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>  
  
```  
  
#### 155% 環境フォント  
 **として表示されます:** 14 pt Segoe UI  
  
 **の使用:** ドキュメントでセクションの見出しも UI またはレポート  
  
 **手続き型コード:** ここで"textBlock"は、以前に定義された TextBlock は、"label"は、以前に定義されたラベル。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** のように TextBlock またはラベルのスタイルを設定します。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>  
  
```  
  
#### 133% 環境フォント  
 **として表示されます:** 12 pt Segoe UI  
  
 **の使用:** と文書のシグネチャのダイアログ ボックスに小さい小見出しも UI  
  
 **手続き型コード:** ここで"textBlock"は、以前に定義された TextBlock は、"label"は、以前に定義されたラベル。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** のように TextBlock またはラベルのスタイルを設定します。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>  
  
```  
  
#### 122% 環境フォント  
 **として表示されます:** 11 pt Segoe UI  
  
 **の使用:** 署名ダイアログ ボックスの見出しのセクションで、ツリー ビューで、垂直タブ ナビゲーション ノードのトップ  
  
 **手続き型コード:** ここで"textBlock"は、以前に定義された TextBlock は、"label"は、以前に定義されたラベル。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** のように TextBlock またはラベルのスタイルを設定します。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>  
  
```  
  
#### 環境フォント \+ 太字  
 **として表示されます:** 9 pt Segoe UI 太字で表示されます。  
  
 **の使用:** も UI のラベルと署名のダイアログ ボックス、レポート、およびドキュメントの小見出し  
  
 **手続き型コード:** ここで"textBlock"は、以前に定義された TextBlock は、"label"は、以前に定義されたラベル。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironmentBoldStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironmentBoldStyleKey);  
  
```  
  
 **XAML:** のように TextBlock またはラベルのスタイルを設定します。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>  
  
```  
  
### ローカライズ可能なスタイル  
 場合によっては、ローカライズが東アジア言語のテキストに太字を削除するなど、別のロケールを使用する場合は、フォント スタイルを変更する必要があります。 フォント スタイルのローカライズを可能にするには、これらのスタイルは、.resx ファイル内になければなりません。 これを実現し、Visual Studio のフォーム デザイナーでのフォント スタイルを編集する最善の方法では、デザイン時にフォント スタイルを明示的に設定します。 フォントが完全なオブジェクトを作成し、親のフォントの継承を停止するよう、FontStyle プロパティのみを使用してフォントを設定します。  
  
 ソリューションでは、フォームの **FontChanged** イベントです。**FontChanged** イベント、すべてのコントロールについて説明し、そのフォントが設定されているかどうかは確認します。 設定されている場合は、フォームのフォントとコントロールの前のフォント スタイルに基づく新しいフォントを変更します。 このコード例を示します。  
  
```  
private void Form1_FontChanged(object sender, System.EventArgs e) { SetFontStyles(); } /// <summary> /// SetFontStyles - This function will iterate all controls on a page /// and recreate their font with the desired fontstyle. /// It should be called in the OnFontChanged handler (and also in the constructor /// in case the IUIService is not available so OnFontChange doesn't fire). /// This way, when the VS shell font is given to us the controls that have /// a different style for the font (bolded for example) will recreate their font /// and use the VS shell font but with a style variation (bolded ...). /// </summary> protected void SetFontStyles() { SetFontStyles(this, this, this.Font); } protected static void SetFontStyles(Control topControl, Control parent, Font referenceFont) { foreach(Control c in parent.Controls) { if (c.Controls != null && c.Controls.Count > 0) { SetFontStyles(topControl, c, referenceFont); } if (c.Font != topControl.Font) { c.Font = new Font(referenceFont, c.Font.Style); } } }  
```  
  
 このコードを使用して、フォームのフォントが更新されると、コントロールのフォントもに更新されますが保証されます。 インスタンスを取得するダイアログ ボックスが失敗するため、このメソッドをフォームのコンス トラクターから呼び出されますが **IUIService** と **FontChanged** イベントは起動しません。 フック **FontChanged** ダイアログ ボックスに、ダイアログ ボックスが既に開いている場合でも、新しいフォントを動的に取得できるようになります。  
  
### 環境フォントのテスト  
 UI は、環境フォントを使用して、サイズの設定を尊重を開きます **ツール \> オプション \> 環境 \> フォントおよび色** \[「環境フォント」\] を選択し、"設定の表示:"ドロップダウン メニュー。  
  
 ![Fonts and Colors page in Tools &#62; Options dialog](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201\-a\_OptionsFonts")  
  
 **ツールのフォントおよび色の設定 \> オプション\] ダイアログ ボックス**  
  
 フォント サイズを非常に別の既定値に設定します。 明確な UI が更新されないが、\("Times New Roman"\) などのセリフ付きフォントを選択し、非常に大きなサイズを設定します。 次は、環境を優先することを確認するように UI をテストします。 ライセンスのダイアログ ボックスを使用する例を次に示します。  
  
 ![Example of dialog not using the environment font](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201\-b\_WrongFontDialog")  
  
 **環境フォントを順守しない UI テキストの例**  
  
 この場合は、「ユーザー情報」と「製品情報」が、このフォントを考慮しはありません。 場合によっては、明示的な設計の選択肢のこが、明示的なフォントが赤線仕様の一部として指定されていない場合、バグであることができます。  
  
 フォントをリセットする\] で \[「既定値を使用」 **ツール \> オプション \> 環境 \> フォントおよび色**します。  
  
##  <a name="BKMK_TextStyle"></a> テキストのスタイル  
 テキストのスタイルは、フォント サイズ、太さ、および大文字小文字の区別を参照します。 実装に関するガイダンスを参照してください。 [環境フォント](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)します。  
  
### テキストの大文字と小文字  
  
#### すべて大文字  
 タイトルまたは Visual Studio でのラベルをすべて大文字を使用しないでください。  
  
#### すべて小文字  
 使用しないですべて小文字のタイトルまたは Visual Studio でのラベル。  
  
#### 文とタイトル ケース  
 Visual Studio でのテキストには、先頭文字が大文字または文の場合も、状況に応じたを使用する必要があります。  
  
|先頭文字が大文字を使用します。|文の用途:|  
|---------------------|-----------|  
|ダイアログ ボックスのタイトル|ラベル|  
|グループ ボックス|チェック ボックス|  
|メニュー項目|オプション ボタン|  
|コンテキスト メニュー項目|リスト ボックス項目|  
|ボタン|ステータス バー|  
|テーブルのラベル||  
|列ヘッダー||  
|ツール ヒント||  
  
##### 先頭文字が大文字  
 タイトル ケースは、ほとんどまたはすべての語句内の単語の最初の文字を大文字にするスタイルです。 Visual Studio を含む多くの項目の先頭文字が大文字を使用します。  
  
-   **ツール ヒント。**例:「プレビュー選択した項目」  
  
-   **列のヘッダー。**例:「システムの応答」  
  
-   **メニュー項目。**例:「\[save All\]」  
  
 先頭文字が大文字を使用して、次の単語を大文字に変換する場合および小文字のままにするためのガイドラインに示します。  
  
|大文字|コメントと例|  
|---------|------------|  
|すべての名詞||  
|すべての動詞|"Is"と他の形式の"be"を含む|  
|すべての副詞|「以上」、"When"を含む|  
|すべての形容詞|"This"および「を」を含む|  
|すべての代名詞|など、格「、」も「これは、」代名詞の省略形"it"と動詞"is"|  
|品詞に関係なく、最初と最後の単語||  
|動詞句の一部である前置詞|「すべてのウィンドウを閉じる」または「システムのシャット ダウン」|  
|頭字語のすべての英字|HTML、XML、URL、IDE、RGB|  
|2 つ目は、名詞または固有名詞形容詞であるか、という単語がある同じ重み複合語で word します。|前の Microsoft ソフトウェアの相互参照は、読み取り\/書き込みアクセス、実行時|  
  
|小文字|例|  
|---------|-------|  
|別の品詞または最初の単語を変更する分詞形である場合、複合語では、2 番目の単語|再開可能の方法|  
|この記事のいずれかのタイトルの最初の単語でない限り、|、|  
|接続詞を調整します。|nor、または|  
|動詞句以外の 4 つ以下の文字の文字が含まれる前置詞|のとしての先頭で、チェック アウト|  
|"To"無限長の句で使用する場合|「ハード ディスクをフォーマットする方法」|  
  
##### 文の場合  
 文の場合は、文の最初の単語のみが大文字で、任意の名詞と代名詞は書き込み用の標準的な大文字と小文字メソッド"I" 一般に、文の場合は、読み取るには、特にコンテンツは変換場合、マシンが世界中のユーザーに簡単です。 文の用途:  
  
1.  **ステータス バー メッセージです。**シンプルで簡単に言えば、され、ステータス情報だけを提供します。 例:「読み込みプロジェクト ファイル」  
  
2.  **他のすべての UI 要素**, 、ラベル、チェック ボックス、ラジオ ボタン、および、ボックスの項目を一覧表示します。 例:"Select すべての項目\] ボックスの一覧で"  
  
### テキストの書式設定  
 Visual Studio 2013 で既定の書式を制御、 [環境フォント](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)です。 このサービスを使用して、IDE \(統合開発環境\) 全体で一貫性のあるフォントの外観を確認し、ユーザーの一貫したエクスペリエンスを保証するために使用する必要があります。  
  
 Visual Studio フォント サービスで使用される既定のサイズは Windows から取得され、9 pt として表示されます。  
  
 環境フォントの書式を適用することができます。 このトピックで説明される状況、およびスタイルを使用します。 実装に関する情報を参照してください [環境フォント](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)します。  
  
#### 太字のテキスト  
 太字のテキストは、Visual Studio で控え目に使用し、用に予約する必要があります。  
  
-   ウィザードの質問のラベル  
  
-   ソリューション エクスプ ローラーでアクティブなプロジェクトを指定します。  
  
-   プロパティの \[ツール\] ウィンドウで値をオーバーライドします。  
  
-   Visual Basic エディターのドロップダウン リストで特定のイベント  
  
-   web ページの \[ドキュメント アウトライン\] で、サーバーによって生成されたコンテンツ  
  
-   複雑なダイアログまたはデザイナーの UI セクション ヘッダー  
  
#### 斜体  
 Visual Studio では、斜体または太字になっているのいずれかの斜体文字は使用しません。  
  
#### 色  
  
-   青はハイパーリンク \(ナビゲーションおよびコマンドの実行\) の予約されており、印刷の向きに使用することはありません。  
  
-   大規模な見出し \(環境フォント 5x 155% 以降\) は、この目的で色付けすることができます。  
  
    -   Visual Studio の UI のシグネチャに視覚的な効果を提供するには  
  
    -   特定の領域に注目  
  
    -   ダーク グレーまたは黒環境が標準的なテキストの色のリリーフを提供するには  
  
-   見出しの色には、既存 Visual Studio ブランドの色、主にメイン紫色の \#FF68217A を利用します。  
  
-   見出しの色を使用している場合に従う必要があります、 [Windows カラー ガイドライン](https://msdn.microsoft.com/en-us/library/dn742482.aspx), コントラスト比やその他のユーザー補助に関する考慮事項など、します。  
  
### Font Size  
 Visual Studio の UI のデザインは、複数の空白と明るい外観を備えています。 可能であれば、chrome とタイトル バー削減されたり、削除します。 情報密度は Visual Studio での要件では、文字体裁引き続き重要なより多くの行間隔やフォント サイズおよび重みのバリエーションの 1 つに重点を置いてです。  
  
 次の表には、デザインの詳細と Visual Studio で使用される表示フォントを視覚的な例が含まれています。 いくつか表示フォントのバリエーションは、サイズと Semilight などの外観に組み込まれていれば、ライトの重みの両方があります。  
  
 フォントを参照してすべての表示用実装コード スニペット [(拡大/縮小/太字) 参照を書式設定](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)します。  
  
#### 375% 環境フォント \+ Light  
  
|||  
|-|-|  
|**使用法:** まれに発生します。 一意なブランド化された UI だけです。<br /><br /> **操作を行います。**<br /><br /> -   文の使用例<br />-   ライト ウェイトを常に使用します。<br /><br /> **行わないでください。**<br /><br /> -   UI のスタート ページなどの UI の署名以外の使用<br />-   太字、斜体または太字斜体<br />-   本文テキストの使用<br />-   ツール ウィンドウを使用します。|**として表示されます:** 34 pt Segoe UI Light<br /><br /> **表示の例:**<br /><br /> *現在は使用されていません。 スタート ページで使用できます。*|  
  
#### 310% 環境フォント \+ Light  
  
|||  
|-|-|  
|**使用法:**<br /><br /> -   ヘッダーの署名のダイアログ ボックスの拡大<br />-   メイン レポートの見出し<br /><br /> **操作を行います。**<br /><br /> -   文の使用例<br />-   ライト ウェイトを常に使用します。<br /><br /> **行わないでください。**<br /><br /> -   UI のスタート ページなどの UI の署名以外の使用<br />-   太字、斜体または太字斜体<br />-   本文テキストの使用<br />-   ツール ウィンドウを使用します。|**として表示されます:** 28 pt Segoe UI Light<br /><br /> **表示の例:**<br /><br /> ![Example of 310% Environment font &#43; Light heading](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202\-a\_EF310")|  
  
#### 200% 環境フォント \+ Semilight  
  
|||  
|-|-|  
|**使用法:**<br /><br /> -   小見出し<br />-   小規模および中規模のダイアログ ボックスのタイトル<br /><br /> **操作を行います。**<br /><br /> -   文の使用例<br />-   Semilight 重みを常に使用します。<br /><br /> **行わないでください。**<br /><br /> -   太字、斜体または太字斜体<br />-   本文テキストの使用<br />-   ツール ウィンドウを使用します。|**として表示されます:** 18 pt Segoe UI Semillight<br /><br /> **表示の例:**<br /><br /> ![Example of 200% Environment font &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202\-b\_EF200")|  
  
#### 155% 環境フォント  
  
|||  
|-|-|  
|**使用法:**<br /><br /> -   ドキュメント内のセクションの見出しも UI<br />-   レポート<br /><br /> **操作を行います:** のみ大文字を使用<br /><br /> **行わないでください。**<br /><br /> -   太字、斜体または太字斜体<br />-   本文テキストの使用<br />-   Visual Studio を制御する標準を使用します。<br />-   ツール ウィンドウを使用します。|**として表示されます:** 14 pt Segoe UI<br /><br /> **表示の例:**<br /><br /> ![Example of 155% Environment font heading](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202\-c\_EF155")|  
  
#### 133% 環境フォント  
  
|||  
|-|-|  
|**使用法:**<br /><br /> -   署名のダイアログ ボックスで小さい小見出し<br />-   ドキュメント内の小さい小見出しも UI<br /><br /> **操作を行います:** のみ大文字を使用<br /><br /> **行わないでください。**<br /><br /> -   太字、斜体または太字斜体<br />-   本文テキストの使用<br />-   Visual Studio を制御する標準を使用します。<br />-   ツール ウィンドウを使用します。|**として表示されます:** 12 pt Segoe UI<br /><br /> **表示の例:**<br /><br /> ![Example of 133% Environment font heading](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202\-d\_EF133")|  
  
#### 122% 環境フォント  
  
|||  
|-|-|  
|**使用法:**<br /><br /> -   署名のダイアログ ボックスでセクションの見出し<br />-   ツリー ビューの最上位のノード<br />-   垂直タブ ナビゲーション<br /><br /> **操作を行います:** のみ大文字を使用<br /><br /> **行わないでください。**<br /><br /> -   太字、斜体または太字斜体<br />-   本文テキストの使用<br />-   Visual Studio を制御する標準を使用します。<br />-   ツール ウィンドウを使用します。|**として表示されます:** 11 pt Segoe UI<br /><br /> **表示の例:**<br /><br /> ![Example of 122% Environment font heading](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202\-e\_EF122")|  
  
#### 環境フォント \+ 太字  
  
|||  
|-|-|  
|**使用法:**<br /><br /> -   ラベルと署名のダイアログ ボックスの小見出し<br />-   ラベルとレポートの小見出し<br />-   ラベルと小見出しのあるドキュメントにも UI<br /><br /> **操作を行います。**<br /><br /> -   文の使用例<br />-   太字を使用します。<br /><br /> **行わないでください。**<br /><br /> -   斜体または太字斜体<br />-   本文テキストの使用<br />-   Visual Studio を制御する標準を使用します。<br />-   ツール ウィンドウを使用します。|**として表示されます:** 9 pt Segoe UI 太字で表示されます。<br /><br /> **表示の例:**<br /><br /> ![Example of Environment font &#43; Bold heading](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202\-f\_EFB")|  
  
#### 環境フォント  
  
|||  
|-|-|  
|**使用法:** その他のすべてのテキスト<br /><br /> **操作を行います:** のみ大文字を使用<br /><br /> **しない:** 斜体または太字斜体|**として表示されます:** 9 pt Segoe UI<br /><br /> **表示の例:**<br /><br /> ![Example of Environment font](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202\-g\_EF")|  
  
### 余白とスペース  
 見出しは、それらを適切なの重点を置いてをつける周囲の空白が必要です。 この領域は、ポイントのサイズと他に何が水平方向の規則など、環境フォントのテキストの行の見出しに近いによって異なります。  
  
-   単独で、見出しの理想的な埋め込みは、大文字高さ容量の 90% にする必要があります。 たとえば、28 pt Segoe UI Light の見出しは 26 pt のキャップの高さを持ち 23 pt または約 31 ピクセル、余白が約する必要があります。  
  
-   最小の周囲の空白の見出しは、大文字の文字の高さの 50% にする必要があります。 領域を削減は、ルールまたはその他の密接な調整要素で、見出しがと共に発生する場合に使用できます。  
  
-   環境フォントのテキストを太字になっているは、既定の行の高さの間隔とスペースに従う必要があります。  
  
## 参照  
 [MSDN: フォント \(Windows\)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742483\(v=vs.85\).aspx)   
 [MSDN: ユーザー インターフェイスのテキスト \(Windows\)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)