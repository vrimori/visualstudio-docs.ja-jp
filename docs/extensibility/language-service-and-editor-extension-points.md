---
title: 言語サービスとエディターの拡張ポイント |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 88ec5affddb814e350b2edbab7b44efc95371bff
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639764"
---
# <a name="language-service-and-editor-extension-points"></a>言語サービスとエディターの拡張ポイント
エディターでは、ほとんどの言語サービスの機能を含む、Managed Extensibility Framework (MEF) コンポーネント パーツとして拡張する拡張ポイントを提供します。 これらには、主要な拡張機能ポイントのカテゴリです。  
  
-   コンテンツの種類  
  
-   分類の種類と分類の形式  
  
-   余白とスクロール バー  
  
-   Tags  
  
-   修飾  
  
-   マウスのプロセッサ  
  
-   ハンドラーを削除します。  
  
-   オプション  
  
-   IntelliSense  
  
## <a name="extend-content-types"></a>コンテンツの種類を拡張します。  
 コンテンツの種類は、たとえば、エディターによって処理されるテキスト、"text"、"code"または"CSharp"の種類の定義です。 型の変数を宣言することで新しいコンテンツ タイプを定義する<xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>新しいコンテンツ タイプに一意の名前を提供します。 エディターを使用して、コンテンツの種類を登録するには、次の属性とエクスポートします。  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute> コンテンツの種類の名前です。  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> このコンテンツの種類の派生元となるコンテンツの種類の名前です。 コンテンツ型は、その他の複数のコンテンツ タイプから継承することができます。  
  
 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>クラスはシールされている型のパラメーターなしでエクスポートすることができます。  
  
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
  
-   テキスト: 基本的なプロジェクション以外のコンテンツの種類。 "Any"から継承されます。  
  
-   : プレーン テキストのコード以外のテキスト。 "Text"から継承されます。  
  
-   コード: すべての種類のコード。 "Text"から継承されます。  
  
-   模擬: は、処理の任意の種類からテキストを除外します。 このコンテンツの種類のテキストには、対象となる任意の拡張機能がなくなります。  
  
-   投影: の投影のバッファーの内容。 "Any"から継承されます。  
  
-   Intellisense: の IntelliSense の内容。 "Text"から継承されます。  
  
-   Sighelp: シグネチャ ヘルプ。 [Intellisense] から継承されます。  
  
-   Sighelp doc: シグネチャ ヘルプが開きます。 [Intellisense] から継承されます。  
  
 これらは、一部の Visual Studio で定義されているコンテンツの種類と Visual Studio でホストされている言語の一部です。  
  
-   Basic  
  
-   C/C++  
  
-   ConsoleOutput  
  
-   CSharp  
  
-   CSS  
  
-   ENC  
  
-   検索  
  
-   F#  
  
-   HTML  
  
-   JScript  
  
-   XAML  
  
-   XML  
  
 使用可能なコンテンツの種類のリストを検出するには、インポート、<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>エディターのコンテンツの種類のコレクションを保持します。 次のコードは、このサービスをプロパティとしてインポートします。  
  
```  
[Import]  
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }  
```  
  
 ファイル名拡張子とコンテンツの種類を関連付けるには使用<xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>します。  
  
> [!NOTE]
>  使用して Visual Studio で、ファイル名拡張子が登録されている、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>言語サービスのパッケージにします。 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> MEF コンテンツの種類をこの方法で登録されているファイル名拡張子を関連付けます。  
  
 ファイル名拡張子をコンテンツ タイプの定義をエクスポートするには、次の属性を含める必要があります。  
  
-   <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: ファイル名拡張子を指定します。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: コンテンツの種類を指定します。  
  
 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>クラスはシールされている型のパラメーターなしでエクスポートすることができます。  
  
 次の例では、コンテンツ タイプの定義をファイル名拡張子にエクスポート属性を示します。  
  
```  
[Export]  
[FileExtension(".test")]  
[ContentType("test")]  
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>ファイル名拡張子とコンテンツの種類間の関連付けを管理します。  
  
## <a name="extend-classification-types-and-classification-formats"></a>分類の種類と分類の形式を拡張します。  
 分類の種類を使用すると、さまざまな処理 (たとえば、緑「コメント」テキストと、青の「キーワード」テキストを色分け表示など) を提供するテキストの種類を定義します。 型の変数を宣言することで、新しい分類の種類を定義する<xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition>一意の名前を付けます。  
  
 エディターを使用して分類の種類を登録するには、次の属性と共にエクスポートします。  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 分類の種類の名前。  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: この分類の種類の継承元である分類の種類の名前。 すべての分類の種類が"text"から継承し、分類の種類を他の複数の分類の種類から継承できます。  
  
 <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition>クラスはシールされている型のパラメーターなしでエクスポートすることができます。  
  
 次の例では、分類の種類の定義のエクスポート属性を示します。  
  
```  
[Export]  
[Name("csharp.test")]  
[BaseDefinition("test")]  
internal static ClassificationTypeDefinition CSharpTestDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>標準分類へのアクセスを提供します。 組み込みの分類の種類には、これらが含まれます。  
  
-   「テキスト」  
  
-   「自然言語」("text"から派生)  
  
-   「正式な言語」("text"から派生)  
  
-   "string"("literal"から派生)  
  
-   "character"("literal"から派生)  
  
-   「数値」("literal"から派生)  
  
 エラーの種類別のセットを継承<xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>します。 これらには、次のエラーの種類が含まれます。  
  
-   「syntax error"  
  
-   「コンパイラ エラー」  
  
-   「その他のエラー」  
  
-   「警告」  
  
 使用可能な分類の種類のリストを検出するには、インポート、<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>エディターの分類の種類のコレクションを保持します。 次のコードは、このサービスをプロパティとしてインポートします。  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }  
```  
  
 分類形式の定義は、新しい分類の種類を定義できます。 クラスを派生<xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition>型と共にエクスポートし、<xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>と共に、次の属性。  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 形式の名前。  
  
-   <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: 形式の表示名。  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: の形式を表示するかどうかを指定します、**フォントおよび色**のページ、**オプション** ダイアログ ボックス。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 形式の優先順位。 有効な値は<xref:Microsoft.VisualStudio.Text.Classification.Priority>します。  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: この形式をマップする、分類の名前を入力します。  
  
 次の例では、分類の形式の定義のエクスポート属性を示します。  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[ClassificationType(ClassificationTypeNames = "test")]  
[Name("test")]  
[DisplayName("Test")]  
[UserVisible(true)]  
[Order(After = Priority.Default, Before = Priority.High)]  
internal sealed class TestFormat : ClassificationFormatDefinition  
```  
  
 使用可能な形式のリストを検出するには、インポート、<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>エディターの形式のコレクションを保持します。 次のコードは、このサービスをプロパティとしてインポートします。  
  
```  
[Import]  
internal IEditorFormatMapService FormatMapService { get; set; }  
```  
  
## <a name="extend-margins-and-scrollbars"></a>余白とスクロール バーを拡張します。  
 余白とスクロール バーは、テキスト ビュー自体だけでなく、エディターのメイン ビューの要素です。 任意の数だけでなく、テキスト ビューの周囲に表示される標準の余白に余白を行うことができます。  
  
 実装を<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin>に余白を定義するインターフェイス。 実装することも必要があります、<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider>余白を作成するインターフェイス。  
  
 エディターを使用して余白プロバイダーを登録するには次の属性とプロバイダーをエクスポートする必要があります。  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 余白の名前。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 余白が表示される、他の余白を基準とした順序。  
  
     これらは、組み込みの余白です。  
  
    -   「Wpf の水平スクロール バー」  
  
    -   「Wpf の垂直スクロール バー」  
  
    -   「Wpf 行番号余白」  
  
     水平方向の余白の順序属性を持つ`After="Wpf Horizontal Scrollbar"`、組み込みの余白と水平方向の余白の順序属性を持つ下に表示されます`Before ="Wpf Horizontal Scrollbar"`組み込みの余白が表示されます。 右の順序属性を持つ、左右の余白`After="Wpf Vertical Scrollbar"`がスクロール バーの右側に表示されます。 順序属性を持つ、左右の余白を左`After="Wpf Line Number Margin"`(表示されている) 場合に、行番号の余白の左側に表示されます。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: 余白 (左、右、上または下) の種類。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>:、余白の有効期限 (たとえば、"text"または「コード」) のコンテンツの種類。  
  
 次の例では、行番号の余白の右側に表示される余白の余白のプロバイダーにエクスポート属性を示します。  
  
```  
[Export(typeof(IWpfTextViewMarginProvider))]  
[Name("TestMargin")]  
[Order(Before = "Wpf Line Number Margin")]  
[MarginContainer(PredefinedMarginNames.Left)]  
[ContentType("text")]   
```  
  
## <a name="extend-tags"></a>タグを拡張します。  
 タグは、さまざまな種類のテキスト データを関連付ける方法です。 多くの場合、関連付けられているデータは、視覚効果として表示されますがいないすべてのタグがある視覚的に。 実装することで、独自の種類のタグを定義する<xref:Microsoft.VisualStudio.Text.Tagging.ITag>します。 実装する必要がありますも<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>テキストの範囲の指定されたセットのタグを提供する、<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>タガーを提供します。 次の属性と共にタガー プロバイダーをエクスポートする必要があります。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: タグの有効期限 (たとえば、"text"または「コード」) のコンテンツの種類。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: タグの種類。  
  
 次の例では、タガー プロバイダーにエクスポート属性を示します。  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 タグの次のような組み込みのとおりです。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: に関連付けられている、<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>します。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: エラーの種類に関連付けられています。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: 表示要素に関連付けられています。  
  
    > [!NOTE]
    >  例については、 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>、HighlightWordTag 定義を参照してください。[チュートリアル: テキストの強調表示](../extensibility/walkthrough-highlighting-text.md)します。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: に関連付けられたリージョン展開またはアウトラインで折りたたまれていることができます。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: テキスト ビューで表示要素が占める領域を定義します。 空間の表示要素の詳細については、次のセクションを参照してください。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: 自動間隔と、表示要素のサイズを提供します。  
  
 検索し、バッファーとビューのタグを使用して、インポート、<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>または<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>を提供する、<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>要求された型。 次のコードは、このサービスをプロパティとしてインポートします。  
  
```  
[Import]  
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }  
```  
  
#### <a name="tags-and-markerformatdefinitions"></a>タグと MarkerFormatDefinitions  
 拡張することができます、<xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>タグの外観を定義するクラス。 クラスをエクスポートする必要があります (として、 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>) で、次の属性。  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: この形式を参照するための名前  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: これにより、UI に表示する形式  
  
 コンス トラクターでは、表示名とタグの外観を定義します。 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> 塗りつぶしの色を定義し、<xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A>境界線の色を定義します。 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A>形式の定義のローカライズ可能な名前を指定します。  
  
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
  
 タグには、この形式の定義を適用するには、クラス (表示名ではなく) の name 属性で設定した名前を参照します。  
  
> [!NOTE]
>  例については、 <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>、HighlightWordFormatDefinition クラスを参照してください。[チュートリアル: テキストの強調表示](../extensibility/walkthrough-highlighting-text.md)します。  
  
## <a name="extend-adornments"></a>表示要素を拡張します。  
 修飾は、テキスト ビューに表示されるテキストを追加できるかをテキスト自体を表示する視覚効果を定義します。 任意の型として、独自の表示要素を定義する<xref:System.Windows.UIElement>します。  
  
 表示要素のクラスを宣言する必要があります、<xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>します。 装飾層に登録するには、次の属性と共にエクスポートします。  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 表示要素の名前。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: その他の装飾層に対して表示要素の順序付けします。 クラスは、 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> 4 つの既定の層を定義します。 選択、アウトライン、カレット、およびテキスト。  
  
 次の例では、装飾層定義のエクスポート属性を示します。  
  
```  
[Export]  
[Name("TestEmbeddedAdornment")]  
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testLayerDefinition;  
```  
  
 実装する 2 番目のクラスを作成する必要があります<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>処理とその<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>表示要素をインスタンス化するイベントです。 次の属性と共にこのクラスをエクスポートする必要があります。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 表示要素の有効期限 (たとえば、"text"または「コード」) のコンテンツの種類。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: テキスト ビューをこの表示要素の有効期限の種類。 クラスは、<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles>は定義済みのテキスト ビュー ロールのセットがあります。 たとえば、<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>ファイルのテキスト ビューは主に使用します。 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> ユーザーが編集またはマウスとキーボードを使用して移動できるテキスト ビューに使用されます。 例の<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>ビューは、エディターのテキスト ビューと**出力**ウィンドウ。  
  
 次の例では、表示要素のプロバイダーにエクスポート属性を示します。  
  
```  
[Export(typeof(IWpfTextViewCreationListener))]  
[ContentType("csharp")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener  
```  
  
 空間の表示要素とは、テキストと同じレベルで領域を占有します。 この種の表示要素を作成するから継承するクラスをタグを定義する必要があります<xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>、表示要素が占める領域の量を定義します。  
  
 すべての表示要素と同様には、レイヤーの表示要素の定義をエクスポートする必要があります。  
  
```  
[Export]  
[Name("TestAdornment")]  
[Order(After = DefaultAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testAdornmentLayer;  
```  
  
 空間ネゴシエート表示要素をインスタンス化するを実装するクラスを作成する必要があります<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>、クラスを実装するだけでなく<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>(その他の表示要素と同様)。  
  
 タガー プロバイダーを登録するには、次の属性と共にエクスポートする必要があります。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>:、表示要素の有効期限 (たとえば、"text"または「コード」) のコンテンツの種類。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: このテキスト ビューの種類タグまたは表示要素が無効です。 クラスは、<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles>は定義済みのテキスト ビュー ロールのセットがあります。 たとえば、<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>ファイルのテキスト ビューは主に使用します。 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> ユーザーが編集またはマウスとキーボードを使用して移動できるテキスト ビューに使用されます。 例の<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>ビューは、エディターのテキスト ビューと**出力**ウィンドウ。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: タグまたは定義済みの表示要素の種類。 2 番目を追加する必要があります<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>の<xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>します。  
  
 次の例では、空間ネゴシエート adornment タグのタガー プロバイダーにエクスポート属性を示します。  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
[TagType(typeof(SpaceNegotiatingAdornmentTag))]  
[TagType(typeof(TestSpaceNegotiatingTag))]  
internal sealed class TestTaggerProvider : ITaggerProvider  
```  
  
## <a name="extending-mouse-processors"></a>マウスのプロセッサを拡張します。  
 マウス入力の特別な処理を追加することができます。 継承するクラスを作成<xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>を処理する入力のマウス イベントをオーバーライドします。 実装する必要があります<xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>2 番目のクラスでと共にエクスポートし、<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>マウス ハンドラーの有効期限 (たとえば、"text"または「コード」) のコンテンツの種類を指定します。  
  
 次の例では、マウスのプロセッサのプロバイダーにエクスポート属性を示します。  
  
```  
[Export(typeof(IMouseProcessorProvider))]  
[Name("test mouse processor")]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Interactive)]   
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider  
```  
  
## <a name="extend-drop-handlers"></a>ドロップ ハンドラーを拡張します。  
 実装するクラスを作成して特定の種類のテキストのドロップのハンドラーの動作をカスタマイズすることができます<xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler>と 2 番目のクラスを実装する<xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider>ドロップ ハンドラーを作成します。 次の属性と共にドロップ ハンドラーをエクスポートする必要があります。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: このドロップ ハンドラーの有効なテキスト形式。 次の形式は、最上位から最下位までの優先順位で処理されます。  
  
    1.  任意のカスタム書式指定  
  
    2.  FileDrop  
  
    3.  EnhancedMetafile  
  
    4.  Waveaudio で  
  
    5.  Riff  
  
    6.  差分  
  
    7.  ロケール  
  
    8.  [パレット]  
  
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
  
    23. テキスト  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: ドロップ ハンドラーの名前。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 既定のドロップ ハンドラーの前後にドロップ ハンドラーの順序。 Visual Studio の既定のドロップ ハンドラーを"DefaultFileDropHandler"と呼びます。  
  
 次の例では、ドロップ ハンドラー プロバイダーにエクスポート属性を示します。  
  
```  
[Export(typeof(IDropHandlerProvider))]  
[DropFormat("Text")]   
[Name("TestDropHandler")]  
[Order(Before="DefaultFileDropHandler")]   
internal class TestDropHandlerProvider : IDropHandlerProvider  
```  
  
## <a name="extending-editor-options"></a>エディターのオプションの拡張  
 テキスト ビューで、特定のスコープ、たとえばでのみ有効にするためのオプションを定義することができます。 エディターは、この定義済みオプションのセットを提供します。 エディターのオプション、表示オプション、および Windows Presentation Foundation (WPF) の表示オプション。 これらのオプションが記載<xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>、 <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>、および<xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>します。  
  
 新しいオプションを追加するには、これらのオプション定義クラスの 1 つからクラスを派生します。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>  
  
 次の例では、ブール値を持つオプションの定義をエクスポートする方法を示します。  
  
```  
[Export(typeof(EditorOptionDefinition))]  
internal sealed class TestOption : EditorOptionDefinition<bool>  
```  
  
## <a name="extend-intellisense"></a>IntelliSense を拡張します。  
 IntelliSense は、構造化テキスト、に関する情報を提供する機能のグループの一般的な用語とその入力候補です。 これらの機能には、ステートメント入力候補、シグネチャ ヘルプ、クイック ヒント、および電球が含まれます。 ステートメント入力候補を使用して、言語のキーワードまたはメンバーの名前を正確に入力できます。 署名または署名だけを入力したメソッドのシグネチャ ヘルプを表示します。 クイック ヒントでは、それにマウスを合わせると、型またはメンバー名の完全なシグネチャが表示されます。 電球は、たとえば、特定のコンテキストで特定の識別子が 1 つの名前が変更された後に出現するすべての変数の名前を変更する追加のアクションを提供します。  
  
 IntelliSense の機能の設計は、常に同じです。  
  
-   IntelliSense、 *broker*全体的なプロセスを担当します。  
  
-   IntelliSense、*セッション*プレゼンターとコミット、または選択範囲の取り消しのトリガーを起動する間のイベントのシーケンスを表します。 セッションは通常、一部ユーザー ジェスチャによってトリガーされます。  
  
-   IntelliSense、*コント ローラー*はときに、セッションを開始および終了する必要がありますを決定します。 ときに情報をコミットにされ、セッションの取り消された場合にも決定します。  
  
-   IntelliSense、*ソース*コンテンツを提供し、最適な一致を決定します。  
  
-   IntelliSense、*プレゼンター*は内容を表示する責任を負います。  
  
 ほとんどの場合、少なくとも、ソースとコント ローラーを指定することをお勧めします。 表示をカスタマイズする場合は、発表者を指定することもできます。  
  
### <a name="implement-an-intellisense-source"></a>IntelliSense、ソースを実装します。  
 ソースをカスタマイズするには、次のソース インターフェイスの 1 つ (または複数) を実装する必要があります。  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> 非推奨の好評だった<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>します。  
  
 さらに、同じ種類のプロバイダーを実装する必要があります。  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> 非推奨の好評だった<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>します。  
  
 次の属性とプロバイダーをエクスポートする必要があります。  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: ソースの名前。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: ソースが適用されます (たとえば、"text"または「コード」) のコンテンツの種類。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: (その他のソース) に関して、ソースを表示する順序。  
  
-   次の例では、入力候補のソース プロバイダーでエクスポート属性を示します。  
  
```  
Export(typeof(ICompletionSourceProvider))]  
[Name(" Test Statement Completion Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestCompletionSourceProvider : ICompletionSourceProvider  
```  
  
 IntelliSense のソースの実装の詳細については、次のチュートリアルを参照してください。  
  
 [チュートリアル: 表示クイック ヒント](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [チュートリアル: シグネチャ ヘルプを表示します。](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [チュートリアル: 入力候補の表示](../extensibility/walkthrough-displaying-statement-completion.md)  
  
### <a name="implement-an-intellisense-controller"></a>IntelliSense のコント ローラーを実装します。  
 コント ローラーをカスタマイズすることを実装する必要があります、<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>インターフェイス。 さらに、次の属性と共にコント ローラー プロバイダーを実装する必要があります。  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: コント ローラーの名前。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: コント ローラーが適用されます (たとえば、"text"または「コード」) のコンテンツの種類。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: (その他のコント ローラー) に関して、コント ローラーを表示する順序。  
  
 次の例では、完了コント ローラーのプロバイダーにエクスポート属性を示します。  
  
```  
Export(typeof(IIntellisenseControllerProvider))]  
[Name(" Test Controller Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider  
```  
  
 IntelliSense のコント ローラーの使用に関する詳細については、次のチュートリアルを参照してください。  
  
 [チュートリアル: 表示クイック ヒント](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)