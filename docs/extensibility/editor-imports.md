---
title: エディターのインポート |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 24fb5b51dbb2d377aee4f4bcd376c3e3745e6a26
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037864"
---
# <a name="editor-imports"></a>エディターのインポート
エディター サービス、ファクトリ、およびコア エディターをさまざまな種類のアクセスの拡張機能を提供するブローカーの数値をインポートすることができます。 たとえば、インポート、<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>を提供するために、<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>の特定のコンテンツ タイプ。 (このナビゲーターは、テキスト バッファーにさまざまな検索を実行します。)  
  
 エディター インポートを使用するには、フィールドまたは Managed Extensibility Framework コンポーネントの一部をエクスポートするクラスのプロパティとしてインポートします。  
  
> [!NOTE]
>  Managed Extensibility Framework の詳細については、次を参照してください。 [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)します。  
  
## <a name="import-syntax"></a>構文をインポートします。  
 次の例では、オプションのファクトリ サービス、エディターにインポートする方法を示します。  
  
```  
[Import]  
internal IEditorOptionsFactoryService EditorOptions { get; set; }  
```  
  
 フィールドとプロパティではなく、サービスをインポートする場合に設定する必要があります`null`変数に割り当てないに関するコンパイラの警告を回避するために、宣言で。  
  
```  
[Import]  
internal IEditorOptionsFactoryService m_editorOptions = null;  
```  
  
 インポートを使用する例については、次のチュートリアルを参照してください。  
  
 [チュートリアル: 余白のグリフを作成します。](../extensibility/walkthrough-creating-a-margin-glyph.md)  
  
 [チュートリアル: テキスト ビューをカスタマイズします。](../extensibility/walkthrough-customizing-the-text-view.md)  
  
 [チュートリアル: テキストを強調表示します。](../extensibility/walkthrough-highlighting-text.md)  
  
 [チュートリアル: クイック ヒントを表示します。](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [チュートリアル: シグネチャ ヘルプを表示します。](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [チュートリアル: 入力候補の表示](../extensibility/walkthrough-displaying-statement-completion.md)  
  
 [チュートリアル: 電球候補を表示します。](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)  
  
## <a name="import-the-service-provider"></a>サービス プロバイダーをインポートします。  
 インポートすることも、 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (アセンブリ Microsoft.VisualStudio.Shell.Immutable.10.0 内で見つかった) Visual Studio services にアクセスするために同じ方法で。  
  
```csharp  
[Import]  
internal SVsServiceProvider ServiceProvider = null;   
```  
  
 「[チュートリアル:エディター拡張機能から DTE オブジェクトにアクセス](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md)詳細についてはします。  
  
## <a name="services"></a>Services  
 エディター サービスは、サービスを提供し、複数のコンポーネント間で共有される通常の 1 つのエンティティです。  
  
|インポート|提供します|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|ファイル拡張子の間のリレーションシップと<xref:Microsoft.VisualStudio.Utilities.IContentType>オブジェクト。|  
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|<xref:Microsoft.VisualStudio.Utilities.IContentType> オブジェクトのコレクション。|  
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation> オブジェクト|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|多くのエディター アダプター オブジェクト。<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|  
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch>テキストを指定したビューのオブジェクト。|  
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextBuffer>。|  
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextDocument>。|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>の相違点。|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>の相違点。|  
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>または<xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>します。|  
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>一連の<xref:Microsoft.VisualStudio.Text.ITextBuffer>オブジェクト。|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>の<xref:Microsoft.VisualStudio.Text.ITextBuffer>します。|  
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>の<xref:Microsoft.VisualStudio.Text.Editor.ITextView>します。|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>の<xref:Microsoft.VisualStudio.Text.Editor.ITextView>します。|  
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap>の<xref:Microsoft.VisualStudio.Text.Editor.ITextView>します。|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|コレクションを保持<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>オブジェクト。|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>テキスト バッファー。|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>テキスト表示。|  
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions>指定されたスコープの。|  
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMap>テキスト表示。|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent>の<xref:Microsoft.VisualStudio.Text.Editor.ITextView>します。|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|自動インデントを取得、<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider>オブジェクト。|  
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|管理、<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>の<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>します。|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>。|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|スナップショットの範囲のセットから RTF 形式のテキストを生成します。|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer>の<xref:Microsoft.VisualStudio.Text.Editor.ITextView>します。|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|A<xref:System.Windows.Media.TextFormatting.TextParagraphProperties>ビュー内のテキスト行を書式設定します。|  
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|A<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations>オブジェクト、<xref:Microsoft.VisualStudio.Text.Editor.ITextView>します。|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|テキストのスナップショットを検索します。|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>の<xref:Microsoft.VisualStudio.Text.ITextBuffer>によって<xref:Microsoft.VisualStudio.Utilities.IContentType>します。|  
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>テキスト表示。|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|グリフの標準セットです。|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack>の<xref:Microsoft.VisualStudio.Text.Editor.ITextView>します。|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|キーボード処理を追跡します。|  
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|標準<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>オブジェクト。|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|テキスト バッファー間の関係を維持し、<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory>オブジェクト。|  
  
## <a name="other-imports"></a>他のインポート  
 プロバイダー ファクトリとブローカーは、通常、複数のコンポーネントで複数のインスタンスがエンティティです。  
  
|インポート|提供します|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|<xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>型の<xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>) の指定したバッファー。|  
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|テキスト マーカー タガー (、<xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>型の<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>)。|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider>の指定された<xref:Microsoft.VisualStudio.Text.Editor.ITextView>します。|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>。|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>。|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>。|  
  
## <a name="see-also"></a>関連項目  
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)
