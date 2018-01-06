---
title: "言語サービスとエディター拡張機能ポイント |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
caps.latest.revision: "33"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7e62f1f3cac8f279dedbc79f283b908119d66ff2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="language-service-and-editor-extension-points"></a>言語サービスとエディターの拡張点
エディターでは、ほとんどの言語サービス機能を含め、Managed Extensibility Framework (MEF) コンポーネント パーツとして拡張できる拡張ポイントを提供します。 主要な拡張機能ポイントのカテゴリを次に示します。  
  
-   コンテンツの種類  
  
-   分類の種類と分類の形式  
  
-   マージンやスクロール バー  
  
-   Tags  
  
-   修飾  
  
-   マウスのプロセッサ  
  
-   ハンドラーを削除します。  
  
-   オプション  
  
-   IntelliSense  
  
## <a name="extending-content-types"></a>コンテンツの種類の拡張  
 コンテンツの種類は、たとえば、エディターによって処理されるテキスト、"text"、"code"または"CSharp"の種類の定義です。 型の変数を宣言することで、新しいコンテンツの種類を定義する<xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>し、新しいコンテンツの種類の一意の名前を与えることです。 エディターでは、コンテンツの種類を登録するには次の属性と共にエクスポートします。  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>コンテンツの種類の名前です。  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>このコンテンツの種類の派生元のコンテンツの種類の名前です。 コンテンツ型は、他の複数のコンテンツ タイプから継承することができます。  
  
 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>クラスはシールされている型のパラメーターなしでエクスポートすることができます。  
  
 次の例では、コンテンツの種類定義のエクスポート属性を示します。  
  
```  
[Export]  
[Name("test")]  
[BaseDefinition("code")]  
[BaseDefinition("projection")]  
internal static ContentTypeDefinition TestContentTypeDefinition;  
```  
  
 コンテンツの種類は、0 個以上の既存コンテンツの種類に基づくことができます。 組み込みの型を次に示します。  
  
-   いずれか: 基本的なコンテンツの種類。 その他のすべてのコンテンツ タイプの親です。  
  
-   Text: プロジェクション以外のコンテンツの基本型。 "Any"から継承されます。  
  
-   : プレーン テキストのコード以外のテキストです。 「テキスト」から継承されます。  
  
-   コードに示します。 すべての種類のコードにします。 「テキスト」から継承されます。  
  
-   模擬: 処理の任意の種類から、テキストを除外します。 このコンテンツの種類のテキストは、対象となる任意の拡張機能を必要がなくなります。  
  
-   プロジェクション: の投影のバッファーの内容。 "Any"から継承されます。  
  
-   Intellisense: の IntelliSense の内容。 「テキスト」から継承されます。  
  
-   Sighelp: 署名のヘルプ。 "Intellisense"から継承されます。  
  
-   Sighelp doc: 署名ヘルプが開きます。 "Intellisense"から継承されます。  
  
 一部の Visual Studio によって定義されているコンテンツの種類と Visual Studio でホストされている言語のいくつか次に示します。  
  
-   Basic  
  
-   C/C++  
  
-   ConsoleOutput  
  
-   CSharp  
  
-   CSS  
  
-   ENC  
  
-   FindResults  
  
-   F#  
  
-   HTML  
  
-   JScript  
  
-   XAML  
  
-   XML  
  
 使用可能なコンテンツの種類のリストを検出、インポート、<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>エディターのコンテンツの種類のコレクションを保持します。 次のコードは、このサービスをプロパティとしてインポートします。  
  
```  
[Import]  
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }  
```  
  
 ファイル名拡張子を持つコンテンツの種類を関連付けるには使用<xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>です。  
  
> [!NOTE]
>  使用して Visual Studio で、ファイル名拡張子が登録されている、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>言語サービス パッケージにします。 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> MEF コンテンツの種類には、この方法で登録されているファイル名拡張子を関連付けます。  
  
 ファイル名拡張子をコンテンツの種類の定義をエクスポートするには、次の属性を含める必要があります。  
  
-   <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: ファイル名拡張子を指定します。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: コンテンツの種類を指定します。  
  
 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>クラスはシールされている型のパラメーターなしでエクスポートすることができます。  
  
 次の例では、コンテンツの種類の定義にファイル名拡張子にエクスポート属性を示します。  
  
```  
[Export]  
[FileExtension(".test")]  
[ContentType("test")]  
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>ファイル名拡張子とコンテンツの種類間の関連付けを管理します。  
  
## <a name="extending-classification-types-and-classification-formats"></a>分類の種類と分類を拡張する書式設定します。  
 (たとえば、blue 社の「キーワード」テキストと「コメント」テキストを緑色に色分け) のさまざまな処理を提供するテキストの種類を定義するのに分類の種類を使用することができます。 型の変数を宣言することによって新しい分類の種類を定義する<xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition>一意の名前を付けます。  
  
 エディターでは、分類の種類を登録するには次の属性と共にエクスポートします。  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 分類の種類の名前。  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: この分類の種類の継承元である分類の種類の名前。 すべての分類の種類が"text"から継承し、その他の複数の分類の種類から分類の種類を継承できます。  
  
 <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition>クラスはシールされている型のパラメーターなしでエクスポートすることができます。  
  
 次の例では、分類の種類の定義のエクスポート属性を示します。  
  
```  
[Export]  
[Name("csharp.test")]  
[BaseDefinition("test")]  
internal static ClassificationTypeDefinition CSharpTestDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>標準的な分類へのアクセスを提供します。 組み込みの分類の種類には、これらが含まれます。  
  
-   「テキスト」  
  
-   「自然言語」("text"から派生)  
  
-   「形式言語」("text"から派生)  
  
-   "string"("literal"から派生)  
  
-   "character"("literal"から派生)  
  
-   「数値」("literal"から派生)  
  
 エラーの種類のセットを継承<xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>です。 これらは、次のエラーの種類を示します。  
  
-   「構文エラー」  
  
-   「コンパイラ エラー」  
  
-   「その他のエラー」  
  
-   「警告」  
  
 使用可能な分類の種類の一覧を検出、インポート、<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>エディターの分類の種類のコレクションを保持します。 次のコードは、このサービスをプロパティとしてインポートします。  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }  
```  
  
 新しい分類の種類の分類の形式の定義を定義できます。 クラスを派生<xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition>および型とエクスポート<xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>次の属性と連携して、します。  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 形式の名前。  
  
-   <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: 形式の表示名。  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: の形式を表示するかどうかを指定、**フォントおよび色**のページ、**オプション** ダイアログ ボックス。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 形式の優先度。 有効な値は<xref:Microsoft.VisualStudio.Text.Classification.Priority>します。  
  
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
  
 使用可能な形式のリストを検出、インポート、<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>エディターの形式のコレクションを保持します。 次のコードは、このサービスをプロパティとしてインポートします。  
  
```  
[Import]  
internal IEditorFormatMapService FormatMapService { get; set; }  
```  
  
## <a name="extending-margins-and-scrollbars"></a>拡張の余白およびスクロール バー  
 マージンやスクロール バーは、テキスト ビュー自体に加え、エディターのメイン ビュー要素です。 テキスト ビューの周囲に表示される標準的な余白に加えて余白の任意の数を指定できます。  
  
 実装する<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin>余白を定義するインターフェイスです。 実装することも必要があります、<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider>余白を作成するインターフェイスです。  
  
 エディターでは、余白プロバイダーを登録するには次の属性と共に、プロバイダーをエクスポートする必要があります。  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 余白の名前。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 余白が表示される、他のマージンに対して相対的順序。  
  
     組み込みの余白を次に示します。  
  
    -   「Wpf 水平スクロール バー」  
  
    -   「Wpf 垂直スクロール バー」  
  
    -   「Wpf 行番号余白」  
  
     水平方向の余白の順序属性を持つ`After="Wpf Horizontal Scrollbar"`下、組み込みの余白との順序属性を持つ水平方向の余白に表示されて`Before ="Wpf Horizontal Scrollbar"`組み込みの余白が表示されます。 順序属性を持つ、左右の余白を右`After="Wpf Vertical Scrollbar"`スクロール バーの右側に表示されます。 順序属性を持つ、左右の余白を左`After="Wpf Line Number Margin"`(表示されている場合)、行番号の余白の左側に表示されます。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: 余白 (左、右、上または下) の種類。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: マージン設定の有効期限 (たとえば、"text"または「コード」) のコンテンツの種類。  
  
 次の例では、行番号の余白の右側に表示される余白の余白のプロバイダーにエクスポート属性を示します。  
  
```  
[Export(typeof(IWpfTextViewMarginProvider))]  
[Name("TestMargin")]  
[Order(Before = "Wpf Line Number Margin")]  
[MarginContainer(PredefinedMarginNames.Left)]  
[ContentType("text")]   
```  
  
## <a name="extending-tags"></a>タグを拡張します。  
 タグは、さまざまな種類のテキストとデータを関連付ける方法です。 多くの場合、視覚効果として、関連するデータが表示されますがないすべてのタグ、視覚的な表示。 実装することで、独自の種類のタグを定義する<xref:Microsoft.VisualStudio.Text.Tagging.ITag>です。 実装することも必要があります<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>テキスト範囲の指定されたセットのタグを提供して、<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>タガーを提供します。 次の属性と共にタガー プロバイダーをエクスポートする必要があります。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: タグの有効期限 (たとえば、"text"または「コード」) のコンテンツの種類。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: タグの種類。  
  
 次の例では、タガー プロバイダーをエクスポート属性を示します。  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 タグの次のような組み込みのとおりです。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: に関連付けられている、<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>です。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: エラーの種類に関連付けられています。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: 表示要素に関連付けられています。  
  
    > [!NOTE]
    >  例については、 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>、HighlightWordTag 定義を参照して[チュートリアル: テキストを強調表示](../extensibility/walkthrough-highlighting-text.md)です。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: 拡張したりできるアウトラインで折りたたまれた領域に関連付けられています。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: テキスト ビューで表示要素が占める領域を定義します。 空間ネゴシエート表示要素の詳細については、次のセクションを参照してください。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: 自動間隔と表示要素のサイズを提供します。  
  
 検索し、buffers、およびビューのタグを使用して、インポート、<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>または<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>、提供する、<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>要求された型のです。 次のコードは、このサービスをプロパティとしてインポートします。  
  
```  
[Import]  
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }  
```  
  
#### <a name="tags-and-markerformatdefinitions"></a>タグと MarkerFormatDefinitions  
 拡張することができます、<xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>タグの外観を定義するクラス。 クラスをエクスポートする必要があります (として、 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>) 次の属性を持つ。  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: この形式を参照するための名前  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: これにより、UI に表示する形式  
  
 コンス トラクターでは、表示名とタグの外観を定義します。 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A>塗りつぶしの色を定義および<xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A>境界線の色を定義します。 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A>形式の定義のローカライズ可能な名前を指定します。  
  
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
  
 この形式の定義をタグに適用するには、(表示名ではない) のクラスの name 属性で設定した名前を参照します。  
  
> [!NOTE]
>  例については、 <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>、HighlightWordFormatDefinition クラスを参照してください[チュートリアル: テキストを強調表示](../extensibility/walkthrough-highlighting-text.md)です。  
  
## <a name="extending-adornments"></a>表示要素の拡張  
 修飾では、テキスト ビューに表示されるテキストを追加できるかをテキスト自体を表示する視覚効果を定義します。 任意の型として独自の表示要素を定義する<xref:System.Windows.UIElement>です。  
  
 装飾クラスで宣言する必要があります、<xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>です。 装飾層を登録するには、次の属性と共にエクスポートします。  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 表示要素の名前。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 他の装飾層に対して表示要素の順序付けします。 クラス<xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers>デフォルトの 4 つのレイヤーを定義します。 選択、アウトライン、カレット、そのテキスト。  
  
 次の例では、装飾層定義のエクスポート属性を示します。  
  
```  
[Export]  
[Name("TestEmbeddedAdornment")]  
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testLayerDefinition;  
```  
  
 実装する 2 番目のクラスを作成する必要があります<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>処理とその<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>イベント表示要素をインスタンス化します。 次の属性と共に、このクラスをエクスポートする必要があります。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 表示要素の有効期限 (たとえば、"text"または「コード」) のコンテンツの種類。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: この表示要素の有効期限、テキスト ビューの種類。 クラス<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles>ビュー ロールの定義済みのテキスト セットを持ちます。 たとえば、<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>ファイルのテキスト ビューは、主に使用します。 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>テキスト ビュー、ユーザーが編集または、マウスとキーボードを使用して移動できますが使用されます。 例については<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>ビューは、エディターのテキスト ビュー、および**出力**ウィンドウです。  
  
 次の例では、装飾プロバイダーにエクスポート属性を示します。  
  
```  
[Export(typeof(IWpfTextViewCreationListener))]  
[ContentType("csharp")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener  
```  
  
 空間ネゴシエート装飾はテキストと同じレベルでの領域を占有する 1 つです。 この種類の表示要素を作成するから継承するクラスをタグを定義する必要があります<xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>、表示要素が占める領域の量を定義します。  
  
 同様に、すべての表示要素には、レイヤーの表示要素の定義をエクスポートする必要があります。  
  
```  
[Export]  
[Name("TestAdornment")]  
[Order(After = DefaultAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testAdornmentLayer;  
```  
  
 空間ネゴシエート表示要素のインスタンスを作成するを実装するクラスを作成する必要があります<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>を実装するクラスに加えて<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>(表示要素の他の種類と同様)。  
  
 タガー プロバイダーを登録するには、次の属性と共にエクスポートする必要があります。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>:、表示要素の有効期限 (たとえば、"text"または「コード」) のコンテンツの種類。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: 対象のテキスト ビューの種類タグまたは表示要素が無効です。 クラス<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles>ビュー ロールの定義済みのテキスト セットを持ちます。 たとえば、<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>ファイルのテキスト ビューは、主に使用します。 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>テキスト ビュー、ユーザーが編集または、マウスとキーボードを使用して移動できますが使用されます。 例については<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>ビューは、エディターのテキスト ビュー、および**出力**ウィンドウです。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: タグまたは定義されている表示要素の種類。 2 番目を追加する必要があります<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>の<xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>します。  
  
 次の例では、空間ネゴシエート装飾タグのタガー プロバイダーをエクスポート属性を示します。  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
[TagType(typeof(SpaceNegotiatingAdornmentTag))]  
[TagType(typeof(TestSpaceNegotiatingTag))]  
internal sealed class TestTaggerProvider : ITaggerProvider  
```  
  
## <a name="extending-mouse-processors"></a>マウスのプロセッサを拡張します。  
 マウス入力に対して特別な処理を追加することができます。 継承するクラスを作成する<xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>を処理する入力のマウス イベントをオーバーライドします。 実装する必要があります<xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>2 番目のクラスでと共にエクスポートし、<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>マウスのハンドラーの有効期限 (たとえば、"text"または「コード」) のコンテンツの種類を指定します。  
  
 次の例では、マウス プロセッサ プロバイダーに対してエクスポート属性を示します。  
  
```  
[Export(typeof(IMouseProcessorProvider))]  
[Name("test mouse processor")]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Interactive)]   
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider  
```  
  
## <a name="extending-drop-handlers"></a>ドロップのハンドラーを拡張します。  
 実装するクラスを作成してテキストの特定の種類のハンドラーをドロップの動作をカスタマイズできます<xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler>と 2 番目のクラスを実装する<xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider>ドロップ ハンドラーを作成します。 ドロップ ハンドラーと共に、次の属性をエクスポートする必要があります。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: このドロップ ハンドラーの有効期限、テキスト形式です。 次の形式は、最上位から最下位までの優先順位に従って処理されます。  
  
    1.  任意のカスタム書式指定  
  
    2.  FileDrop  
  
    3.  EnhancedMetafile  
  
    4.  WaveAudio  
  
    5.  Riff  
  
    6.  差分  
  
    7.  ロケール  
  
    8.  [パレット]  
  
    9. PenData  
  
    10. シリアル化可能です  
  
    11. シンボリック リンク  
  
    12. Xaml  
  
    13. XamlPackage  
  
    14. tiff  
  
    15. ビットマップ  
  
    16. Dib  
  
    17. MetafilePicture  
  
    18. CSV  
  
    19. System.String  
  
    20. HTML 形式  
  
    21. UnicodeText  
  
    22. OEMText  
  
    23. テキスト  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: ドロップ ハンドラーの名前。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 既定のドロップ ハンドラーの前後にドロップ ハンドラーの順序。 Visual Studio の既定のドロップ ハンドラー"DefaultFileDropHandler"と呼びます。  
  
 次の例では、ドロップ ハンドラー プロバイダーに対してエクスポート属性を示します。  
  
```  
[Export(typeof(IDropHandlerProvider))]  
[DropFormat("Text")]   
[Name("TestDropHandler")]  
[Order(Before="DefaultFileDropHandler")]   
internal class TestDropHandlerProvider : IDropHandlerProvider  
```  
  
## <a name="extending-editor-options"></a>エディターのオプションの拡張  
 テキスト ビューで特定のスコープ、たとえばでのみ有効にするオプションを定義することができます。 エディターには、この定義済みオプションのセットが用意されています: エディターのオプション、表示オプション、および Windows Presentation Foundation (WPF) ビューのオプションです。 これらのオプションは含まれて<xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>、 <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>、および<xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>です。  
  
 新しいオプションを追加するには、これらのオプション定義クラスのいずれかからクラスを派生します。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>  
  
 次の例では、ブール値を持つオプションの定義をエクスポートする方法を示します。  
  
```  
[Export(typeof(EditorOptionDefinition))]  
internal sealed class TestOption : EditorOptionDefinition<bool>  
```  
  
## <a name="extending-intellisense"></a>IntelliSense の拡張  
 IntelliSense とは、構造化テキスト、に関する情報を提供する機能のグループの一般的な用語とそのステートメント入力候補です。 これらの機能には、ステートメント入力候補、シグネチャ ヘルプ、クイック ヒント、および代わって電球が含まれます。 ステートメント入力候補を使用して、言語のキーワードまたはメンバー名を正しく入力できます。 署名のヘルプには、ユーザーが入力したばかりのメソッドの署名または署名が表示されます。 クイック ヒントでは、それにマウスを合わせると、型またはメンバー名の完全な署名が表示されます。 電球は、1 つの名前が変更された後に出現するすべての変数の名前を変更する特定のコンテキストで、たとえば、特定の識別子に対して追加の操作を提供します。  
  
 IntelliSense 機能のデザインは、常に同じです。  
  
-   IntelliSense が*broker*は全体的な処理を担当します。  
  
-   IntelliSense が*セッション*発表者とコミット、または選択範囲の取り消しのトリガーを起動する間のイベントのシーケンスを表します。 セッションは、通常、いくつかユーザー ジェスチャによってトリガーされます。  
  
-   IntelliSense が*コント ローラー*はときに、セッションの始まりし、終わりを決定します。 また、場合については、コミットする必要が、セッションを取り消す必要がある場合を決定します。  
  
-   IntelliSense が*ソース*コンテンツを提供し、最適な一致を決定します。  
  
-   IntelliSense が*プレゼンター*は、コンテンツの表示を担当します。  
  
 ほとんどの場合に、少なくとも、ソースとコント ローラーを提供することをお勧めします。 表示をカスタマイズする場合、発表者を指定することもできます。  
  
### <a name="implementing-an-intellisense-source"></a>IntelliSense ソースの実装  
 ソースをカスタマイズするには、次のソース インターフェイスの 1 つ (または複数) を実装する必要があります。  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource>代わりには廃止されて<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>です。  
  
 さらに、同じ種類のプロバイダーを実装する必要があります。  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider>代わりには廃止されて<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>です。  
  
 次の属性と共に、プロバイダーをエクスポートする必要があります。  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: ソースの名前。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: ソースが適用されます (たとえば、"text"または「コード」) のコンテンツの種類。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: (その他のソース) に関して、ソースを表示する順序です。  
  
-   次の例では、入力候補のソース プロバイダーでエクスポート属性を示します。  
  
```  
Export(typeof(ICompletionSourceProvider))]  
[Name(" Test Statement Completion Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestCompletionSourceProvider : ICompletionSourceProvider  
```  
  
 IntelliSense のソースの実装の詳細については、次のチュートリアルを参照してください。  
  
 [チュートリアル: クイック ヒントの表示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [チュートリアル: シグネチャ ヘルプの表示](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [チュートリアル: 入力候補の表示](../extensibility/walkthrough-displaying-statement-completion.md)  
  
### <a name="implementing-an-intellisense-controller"></a>IntelliSense のコント ローラーの実装  
 コント ローラーをカスタマイズする必要がありますを実装する、<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>インターフェイスです。 さらに、次の属性と共にコント ローラー プロバイダーを実装する必要があります。  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: コント ローラーの名前。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: コント ローラーが適用されます (たとえば、"text"または「コード」) のコンテンツの種類。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: (他のコント ローラー) に関して、コント ローラーを表示する順序です。  
  
 次の例では、完了コント ローラーのプロバイダーにエクスポート属性を示します。  
  
```  
Export(typeof(IIntellisenseControllerProvider))]  
[Name(" Test Controller Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider  
```  
  
 詳細については、IntelliSense のコント ローラーを使用して、次のチュートリアルを参照してください。  
  
 [チュートリアル: クイック ヒントの表示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)