---
title: "言語サービスとエディターの拡張ポイント | Microsoft Docs"
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
  - "エディター [Visual Studio SDK] - 新しい拡張ポイント"
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
caps.latest.revision: 33
caps.handback.revision: 33
ms.author: "gregvanl"
manager: "ghogen"
---
# 言語サービスとエディターの拡張ポイント
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

エディターでは、ほとんどの言語サービス機能を含む、Managed Extensibility Framework \(MEF\) コンポーネント部分として拡張可能な拡張ポイントを提供します。 主要な拡張機能ポイント カテゴリを次に示します。  
  
-   コンテンツの種類  
  
-   分類の種類および分類の形式  
  
-   余白とスクロール バー  
  
-   タグ  
  
-   表示要素  
  
-   マウスのプロセッサ  
  
-   ハンドラーを削除します。  
  
-   オプション  
  
-   IntelliSense  
  
## コンテンツの種類を拡張します。  
 コンテンツの種類は、たとえば、エディターによって処理されるテキスト、"text"、"code"または"CSharp"の種類の定義です。 型の変数を宣言することで新しいコンテンツ タイプを定義する <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> し、新しいコンテンツ タイプに一意の名前を指定します。 エディターでは、コンテンツの種類を登録するには、次の属性と共にエクスポートします。  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute> コンテンツの種類の名前です。  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> このコンテンツの種類の派生元となるコンテンツの種類の名前です。 コンテンツの種類は、その他の複数のコンテンツ タイプから継承できます。  
  
 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> クラスはシールされている型のパラメーターなしでエクスポートすることができます。  
  
 次の例では、コンテンツ タイプの定義のエクスポート属性を示します。  
  
```  
[Export]  
[Name("test")]  
[BaseDefinition("code")]  
[BaseDefinition("projection")]  
internal static ContentTypeDefinition TestContentTypeDefinition;  
```  
  
 コンテンツの種類は、0 個以上の既存のコンテンツ タイプに基づくことができます。 組み込みの型を次に示します。  
  
-   いずれか: 基本的なコンテンツの種類。 その他のすべてのコンテンツ タイプの親です。  
  
-   テキスト: 基本的なプロジェクション以外のコンテンツの種類。 "Any"から継承します。  
  
-   : プレーン テキストの非コード テキストです。 "Text"から継承します。  
  
-   コード: すべての種類のコードにします。 "Text"から継承します。  
  
-   模擬: 任意の種類の処理から、テキストを除外します。 このコンテンツの種類のテキストは、対象となる任意の拡張機能を必要がなくなります。  
  
-   投影: の投影のバッファーの内容。 "Any"から継承します。  
  
-   Intellisense: の IntelliSense の内容。 "Text"から継承します。  
  
-   Sighelp: 署名のヘルプ。 "Intellisense"から継承します。  
  
-   Sighelp doc: 署名ヘルプが開きます。 "Intellisense"から継承します。  
  
 これらは、一部の Visual Studio によって定義されているコンテンツの種類と Visual Studio でホストされている言語のいくつか示します。  
  
-   Basic  
  
-   C\/C\+\+  
  
-   ConsoleOutput  
  
-   CSharp  
  
-   CSS  
  
-   ENC  
  
-   FindResults  
  
-   F\#  
  
-   HTML  
  
-   JScript  
  
-   XAML  
  
-   XML  
  
 使用可能なコンテンツの種類の一覧を検出するには、インポート、 <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>, 、エディターのコンテンツの種類のコレクションを保持します。 次のコードは、このサービスをプロパティとしてインポートします。  
  
```  
[Import]  
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }  
```  
  
 ファイル名拡張子のコンテンツの種類を関連付けるには使用 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>します。  
  
> [!NOTE]
>  使用して Visual Studio で、ファイル名拡張子が登録されている、 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> 言語サービス パッケージにします。<xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> MEF コンテンツ タイプをこの方法で登録されているファイル名拡張子と関連付けます。  
  
 ファイル名拡張子をコンテンツ タイプの定義をエクスポートするには、次の属性を含める必要があります。  
  
-   <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: ファイル名拡張子を指定します。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: コンテンツ タイプを指定します。  
  
 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> クラスはシールされている型のパラメーターなしでエクスポートすることができます。  
  
 次の例では、コンテンツ タイプの定義をファイル名拡張子にエクスポート属性を示します。  
  
```  
[Export]  
[FileExtension(".test")]  
[ContentType("test")]  
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> ファイル名拡張子とコンテンツの種類の関連付けを管理します。  
  
## 分類の種類と分類を拡張する書式設定します。  
 分類の種類を使用すると、さまざまな処理 \(たとえば、「コメント」テキストと、青の「キーワード」テキストを緑色に色分けなど\) を提供するテキストの種類を定義します。 型の変数を宣言することで新しい分類型を定義する <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> 一意の名前を付けます。  
  
 エディターでは、分類の種類を登録するには、次の属性と共にエクスポートします。  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 分類の種類の名前。  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: この分類型の継承元である分類の種類の名前。 すべての分類の種類が"text"から継承し、分類の種類を他の複数の分類型から継承可能性があります。  
  
 <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> クラスはシールされている型のパラメーターなしでエクスポートすることができます。  
  
 次の例では、分類の種類の定義のエクスポート属性を示します。  
  
```  
[Export]  
[Name("csharp.test")]  
[BaseDefinition("test")]  
internal static ClassificationTypeDefinition CSharpTestDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> 標準的な分類へのアクセスを提供します。 組み込みの分類の種類では、これらがあります。  
  
-   「テキスト」  
  
-   「自然言語」\("text"から派生\)  
  
-   「形式言語」\("text"から派生\)  
  
-   「文字列」\(「リテラル」から派生\)  
  
-   "character"\(「リテラル」から派生\)  
  
-   「数値」\(「リテラル」から派生\)  
  
 エラーの種類別のセットを継承 <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>します。 次のエラーの種類を示します。  
  
-   「構文エラー」  
  
-   「コンパイラ エラー」  
  
-   「その他のエラー」  
  
-   「警告」  
  
 使用可能な分類の種類の一覧を検出するには、インポート、 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>, 、エディターの分類の種類のコレクションを保持します。 次のコードは、このサービスをプロパティとしてインポートします。  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }  
```  
  
 新しい分類タイプの分類形式の定義を定義できます。 クラスを派生 <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> および型とエクスポート <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>, 、次の属性と組み合わせて使用します。  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 形式の名前。  
  
-   <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: 形式の表示名。  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: に形式を表示するかどうかを、 **フォントおよび色** のページ、 **オプション** \] ダイアログ ボックス。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 形式の優先度。 有効な値は <xref:Microsoft.VisualStudio.Text.Classification.Priority>です。  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: この形式の割り当て先となる、分類の名前を入力します。  
  
 次の例では、分類形式の定義のエクスポート属性を示します。  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[ClassificationType(ClassificationTypeNames = "test")]  
[Name("test")]  
[DisplayName("Test")]  
[UserVisible(true)]  
[Order(After = Priority.Default, Before = Priority.High)]  
internal sealed class TestFormat : ClassificationFormatDefinition  
```  
  
 使用可能な形式のリストを検出するには、インポート、 <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>, 、エディターの形式のコレクションを保持します。 次のコードは、このサービスをプロパティとしてインポートします。  
  
```  
[Import]  
internal IEditorFormatMapService FormatMapService { get; set; }  
```  
  
## 拡張の余白とスクロール バー  
 余白とスクロール バーは、テキスト ビュー自体に加え、エディターのメイン ビューの要素です。 テキスト ビューの周囲に表示される標準的な余白だけでなく余白の任意の数を指定できます。  
  
 実装、 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> 余白を定義するインターフェイスです。 実装する必要がありますも、 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> インターフェイス、余白を作成します。  
  
 エディターでは、余白のプロバイダーを登録するには次の属性とプロバイダーをエクスポートする必要があります。  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 余白の名前。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 余白が表示される、他のマージンに対して相対的順序。  
  
     組み込みの余白を次に示します。  
  
    -   「\[Wpf 水平スクロール バー」  
  
    -   「\[Wpf 垂直スクロール バー」  
  
    -   「Wpf 行番号余白」  
  
     水平方向の余白の順序属性を持つ `After="Wpf Horizontal Scrollbar"` 組み込みの余白と水平方向の余白の順序を持つを下に表示されて `Before ="Wpf Horizontal Scrollbar"` 組み込みの余白の上に表示されます。 右の順序を持つ、左右の余白 `After="Wpf Vertical Scrollbar"` 、スクロール バーの右側に表示されます。 順序属性を持つ、左右の余白を左 `After="Wpf Line Number Margin"` \(表示されている場合\)、行番号の余白の左側に表示されます。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: 余白 \(左、右、上、または下部\) の種類。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: マージン設定の有効期限 \(たとえば、"text"または「コード」\) のコンテンツの種類。  
  
 次の例では、行番号の余白の右側に表示される余白の幅を余白プロバイダーにエクスポート属性を示します。  
  
```  
[Export(typeof(IWpfTextViewMarginProvider))]  
[Name("TestMargin")]  
[Order(Before = "Wpf Line Number Margin")]  
[MarginContainer(PredefinedMarginNames.Left)]  
[ContentType("text")]   
```  
  
## タグを拡張します。  
 タグは、さまざまな種類のテキスト データを関連付けるための手段です。 多くの場合、視覚効果として、関連付けられたデータが表示されますが、すべてのタグ必要はビジュアルな表示します。 実装することで、独自の種類のタグを定義する <xref:Microsoft.VisualStudio.Text.Tagging.ITag>です。 実装する必要があります <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> テキスト範囲の指定された一連のタグを提供して、 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> 、タガーを提供します。 次の属性と共にタガー プロバイダーをエクスポートする必要があります。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: タグの有効期限 \(たとえば、"text"または「コード」\) のコンテンツの種類。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: タグの種類。  
  
 次の例では、タガー プロバイダーにエクスポート属性を示します。  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 タグの次のような組み込みのとおりです。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: に関連付けられている、 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>です。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: エラーの種類に関連付けられています。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: 表示要素に関連付けられています。  
  
    > [!NOTE]
    >  例については、 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, 、HighlightWordTag 定義を参照して [チュートリアル: テキストの強調表示](../extensibility/walkthrough-highlighting-text.md)します。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: 拡張したりできるアウトラインで折りたたまれた領域に関連付けられています。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: テキスト ビューで表示要素が占める領域を定義します。 領域ネゴシエートする表示要素の詳細については、次のセクションを参照してください。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: 自動間隔と、表示要素のサイズに変更を提供します。  
  
 検索し、バッファーやビューのタグを使用して、インポート、 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> または <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>, 、提供する、 <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> 要求された型のです。 次のコードは、このサービスをプロパティとしてインポートします。  
  
```  
[Import]  
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }  
```  
  
#### タグと MarkerFormatDefinitions  
 拡張する、 <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> タグの外観を定義するクラス。 クラスをエクスポートする必要があります \(として、 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>\)、次の属性。  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: この形式を参照するための名前  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: これが原因で UI に表示する形式  
  
 コンス トラクターでは、表示名とタグの外観を定義します。<xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> 塗りつぶしの色を定義し、 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> 境界線の色を定義します。<xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> 形式の定義のローカライズ可能な名前を指定します。  
  
 形式の定義の例を次に示します。  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
[UserVisible(true)]  
internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
{  
    public HighlightWordFormatDefinition()  
    {  
        this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";   
        this.ZOrder = 5;  
    }  
}  
  
```  
  
 タグには、この形式の定義を適用するには、クラス \(表示名ではなく\) の name 属性で設定した名前を参照します。  
  
> [!NOTE]
>  例については、 <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>, 、HighlightWordFormatDefinition クラスを参照してください [チュートリアル: テキストの強調表示](../extensibility/walkthrough-highlighting-text.md)します。  
  
## 表示要素を拡張します。  
 表示要素では、テキスト ビューに表示されるテキストを追加できるかをテキスト自体を表示する視覚効果を定義します。 独自の表示要素を定義するには任意の種類のとして <xref:System.Windows.UIElement>します。  
  
 Adornment クラスで宣言する必要があります、 <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>です。 Adornment レイヤーに登録するには、次の属性と共にエクスポートします。  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 表示要素の名前。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: に関して他の表示要素のレイヤー表示要素の順序付けします。 クラス <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> 4 つの既定の層を定義します。 選択、アウトライン、カレット、およびテキスト。  
  
 次の例では、装飾レイヤー定義のエクスポート属性を示します。  
  
```  
[Export]  
[Name("TestEmbeddedAdornment")]  
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testLayerDefinition;  
```  
  
 実装する 2 番目のクラスを作成する必要があります <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> し、処理、 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> 表示要素をインスタンス化するイベントです。 次の属性と共にこのクラスをエクスポートする必要があります。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 表示要素の有効期限 \(たとえば、"text"または「コード」\) のコンテンツの種類。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: テキスト ビューがこの表示要素の有効期限の種類。 クラス <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> ロールを表示する定義済みの文字セットを持ちます。 たとえば、 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> ファイルのテキスト ビューは主に使用します。<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> テキスト ビュー、ユーザーが編集またはマウスとキーボードを使用して移動できますが使用されます。 例として <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> ビュー エディターのテキスト ビューは、および **出力** ウィンドウです。  
  
 次の例では、装飾プロバイダーにエクスポート属性を示します。  
  
```  
[Export(typeof(IWpfTextViewCreationListener))]  
[ContentType("csharp")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener  
```  
  
 空間ネゴシエート表示要素とは、テキストと同じレベルでの領域を占有です。 このような表示要素を作成するには、継承されたタグ クラスを定義する必要があります <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, 、表示要素が占める領域の量を定義します。  
  
 すべての表示要素と同様には、レイヤーの表示要素の定義をエクスポートする必要があります。  
  
```  
[Export]  
[Name("TestAdornment")]  
[Order(After = DefaultAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testAdornmentLayer;  
```  
  
 空間ネゴシエート表示要素をインスタンス化するを実装するクラスを作成する必要があります <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, 、クラスを実装するだけでなく <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> \(他の種類の表示要素と同様\)。  
  
 タガー プロバイダーを登録するには、次の属性と共にエクスポートする必要があります。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>:、表示要素の有効期限 \(たとえば、"text"または「コード」\) のコンテンツの種類。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: 対象のテキスト ビューのようなタグまたは表示要素が有効です。 クラス <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> ロールを表示する定義済みの文字セットを持ちます。 たとえば、 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> ファイルのテキスト ビューは主に使用します。<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> テキスト ビュー、ユーザーが編集またはマウスとキーボードを使用して移動できますが使用されます。 例として <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> ビュー エディターのテキスト ビューは、および **出力** ウィンドウです。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: タグまたは定義済みの表示要素の種類。 1 秒間を追加する必要があります <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> の <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>です。  
  
 次の例では、空間ネゴシエート表示要素タグのタガー プロバイダーにエクスポート属性を示します。  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
[TagType(typeof(SpaceNegotiatingAdornmentTag))]  
[TagType(typeof(TestSpaceNegotiatingTag))]  
internal sealed class TestTaggerProvider : ITaggerProvider  
```  
  
## マウスのプロセッサを拡張します。  
 マウス入力に対して特別な処理を追加することができます。 継承するクラスを作成 <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> し処理する入力のマウス イベントをオーバーライドします。 実装する必要があります <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> で 2 番目のクラスと共にエクスポートし、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> マウス ハンドラーの有効期限 \(たとえば、"text"または「コード」\) のコンテンツの種類を指定します。  
  
 次の例では、マウス プロセッサ プロバイダーにエクスポート属性を示します。  
  
```  
[Export(typeof(IMouseProcessorProvider))]  
[Name("test mouse processor")]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Interactive)]   
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider  
```  
  
## ドロップ ハンドラーを拡張します。  
 実装するクラスを作成して特定の種類のテキストのドロップ ハンドラーの動作をカスタマイズできます <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> と 2 番目のクラスを実装する <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> ドロップ ハンドラーを作成します。 次の属性と共にドロップ ハンドラーをエクスポートする必要があります。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: このドロップ ハンドラーが有効なテキスト形式です。 次の形式は、最上位から最下位までの優先順位に従って処理されます。  
  
    1.  任意のカスタム書式指定  
  
    2.  FileDrop  
  
    3.  EnhancedMetafile  
  
    4.  WaveAudio  
  
    5.  Riff  
  
    6.  差分  
  
    7.  ロケール  
  
    8.  \[パレット\]  
  
    9. PenData  
  
    10. シリアル化可能です  
  
    11. シンボリック リンク  
  
    12. Xaml  
  
    13. XamlPackage  
  
    14. Tiff  
  
    15. ビットマップ  
  
    16. Dib  
  
    17. MetafilePicture  
  
    18. CSV  
  
    19. System.String  
  
    20. HTML 形式  
  
    21. UnicodeText  
  
    22. OEMText  
  
    23. Text  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: ドロップ ハンドラーの名前。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 既定のドロップ ハンドラーの前後に、ドロップ ハンドラーの順序。 Visual Studio の既定のドロップ ハンドラーを"DefaultFileDropHandler"と呼びます。  
  
 次の例では、ドロップ ハンドラー プロバイダーにエクスポート属性を示します。  
  
```  
[Export(typeof(IDropHandlerProvider))]  
[DropFormat("Text")]   
[Name("TestDropHandler")]  
[Order(Before="DefaultFileDropHandler")]   
internal class TestDropHandlerProvider : IDropHandlerProvider  
```  
  
## エディターのオプションを拡張します。  
 テキスト ビューで、特定のスコープなどでのみ有効にするオプションを定義することができます。 エディターには、この定義済みオプションのセットが用意されています: エディターのオプション、表示オプション、および Windows Presentation Foundation \(WPF\) ビューのオプションです。 これらのオプションを参照して <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>, 、<xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>, 、および <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>です。  
  
 新しいオプションを追加するには、これらのオプションの定義クラスのいずれかからクラスを派生します。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>  
  
 次の例では、ブール値を持つオプションの定義をエクスポートする方法を示します。  
  
```  
[Export(typeof(EditorOptionDefinition))]  
internal sealed class TestOption : EditorOptionDefinition<bool>  
```  
  
## IntelliSense の拡張  
 IntelliSense は、構造化テキストの情報を提供する機能のグループの一般的な用語とその入力候補です。 これらの機能には、ステートメント入力候補、シグネチャ ヘルプ、クイック ヒント、および電球が含まれます。 ステートメント入力候補により、ユーザーが正しく言語のキーワードまたはメンバーの名前を入力します。 シグニチャ ヘルプには、署名またはユーザーが入力したばかりのメソッドのシグネチャが表示されます。 クイック ヒントでは、上にマウスを置いたときに、型またはメンバーの名前のシグネチャ全体が表示されます。 電球は、たとえば、特定のコンテキストでの特定の識別子の 1 つの名前が変更された後に出現するすべての変数の名前を変更する追加のアクションを提供します。  
  
 IntelliSense 機能の仕様は、常に同じです。  
  
-   IntelliSense、 *ブローカー* は全体的な処理を担当します。  
  
-   IntelliSense、 *セッション* 間の発表者、およびコミットまたは選択範囲の取り消しをトリガーするイベントのシーケンスを表します。 セッションは通常、一部のユーザー ジェスチャによってトリガーされます。  
  
-   IntelliSense、 *コント ローラー* は、セッションの始まりし、終わりとを決定します。 また、ときに情報をコミットになるし、セッションを取り消す必要がある場合を決定します。  
  
-   IntelliSense、 *ソース* コンテンツを提供し、最適な一致を判断します。  
  
-   IntelliSense *プレゼンター* は、コンテンツの表示を担当します。  
  
 ほとんどの場合、少なくとも、ソースとコント ローラーを指定することをお勧めします。 表示をカスタマイズする場合、発表者を指定することもできます。  
  
### IntelliSense ソースの実装  
 ソースをカスタマイズするには、次のソース インターフェイスのいずれか \(またはそれ以上\) を実装する必要があります。  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> 優先の使用は推奨されて <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>します。  
  
 さらに、同じ種類のプロバイダーを実装する必要があります。  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> 優先の使用は推奨されて <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>します。  
  
 次の属性とプロバイダーをエクスポートする必要があります。  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: ソースの名前。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: ソースが適用されます \(たとえば、"text"または「コード」\) のコンテンツの種類。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: ソース \(に関して他のソース\) を表示する順序です。  
  
-   次の例では、入力候補のソース プロバイダーにエクスポート属性を示します。  
  
```  
Export(typeof(ICompletionSourceProvider))]  
[Name(" Test Statement Completion Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestCompletionSourceProvider : ICompletionSourceProvider  
```  
  
 IntelliSense のソースの実装の詳細については、次のチュートリアルを参照してください。  
  
 [チュートリアル: クイック ヒントの表示](../Topic/Walkthrough:%20Displaying%20QuickInfo%20Tooltips.md)  
  
 [チュートリアル: シグニチャ ヘルプの表示](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [チュートリアル: 候補の表示](../extensibility/walkthrough-displaying-statement-completion.md)  
  
### IntelliSense のコント ローラーの実装  
 コント ローラーをカスタマイズするには実装、 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> インターフェイスです。 さらに、次の属性とコント ローラー プロバイダーを実装する必要があります。  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: コント ローラーの名前。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: コント ローラーが適用されます \(たとえば、"text"または「コード」\) のコンテンツの種類。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: に関して他のコント ローラー\)、コント ローラーを表示する順序です。  
  
 次の例では、入力候補のコント ローラー プロバイダーにエクスポート属性を示します。  
  
```  
Export(typeof(IIntellisenseControllerProvider))]  
[Name(" Test Controller Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider  
```  
  
 詳細については、IntelliSense のコント ローラーを使用して、次のチュートリアルを参照してください。  
  
 [チュートリアル: クイック ヒントの表示](../Topic/Walkthrough:%20Displaying%20QuickInfo%20Tooltips.md)