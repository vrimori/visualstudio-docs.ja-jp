---
title: エディターのインポート |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f01567efa411187bede4f6daf15012da81c2331f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132735"
---
# <a name="editor-imports"></a>エディターのインポート
エディターのサービス、ファクトリ、およびコア エディターをさまざまな種類のアクセスと、拡張機能を提供するブローカーの番号をインポートすることができます。 たとえば、インポートすることができます、<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>を提供するために、<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>特定のコンテンツ タイプ用。 (このナビゲーター許可テキスト バッファーでさまざまな検索を実行します。)  
  
 エディター インポートを使用するには、フィールドまたは Managed Extensibility Framework コンポーネントのパートをエクスポートするクラスのプロパティとしてインポートします。  
  
> [!NOTE]
>  詳細については、Managed Extensibility Framework を参照してください。 [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)です。  
  
## <a name="import-syntax"></a>構文をインポートします。  
 次の例では、オプションのファクトリ サービス エディターにインポートする方法を示します。  
  
```  
[Import]  
internal IEditorOptionsFactoryService EditorOptions { get; set; }  
```  
  
 フィールドとプロパティではなく、サービスをインポートする場合に設定する必要があります`null`変数に代入されませんに関するコンパイラの警告を回避するために、宣言で。  
  
```  
[Import]  
internal IEditorOptionsFactoryService m_editorOptions = null;  
```  
  
 インポートを使用する例については、次のチュートリアルを参照してください。  
  
 [チュートリアル: 余白のグリフの作成](../extensibility/walkthrough-creating-a-margin-glyph.md)  
  
 [チュートリアル: テキスト ビューのカスタマイズ](../extensibility/walkthrough-customizing-the-text-view.md)  
  
 [チュートリアル: テキストの強調表示](../extensibility/walkthrough-highlighting-text.md)  
  
 [チュートリアル: クイック ヒントの表示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [チュートリアル: シグネチャ ヘルプの表示](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [チュートリアル: 入力候補の表示](../extensibility/walkthrough-displaying-statement-completion.md)  
  
 [チュートリアル: 電球アイコンによる提案の表示](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)  
  
## <a name="importing-the-service-provider"></a>サービス プロバイダーをインポートします。  
 インポートすることも、 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (アセンブリ Microsoft.VisualStudio.Shell.Immutable.10.0 内で見つかった) Visual Studio services にアクセスするために、同じ方法で。  
  
```  
[Import]  
internal SVsServiceProvider ServiceProvider = null;   
```  
  
 参照してください[チュートリアル: DTE オブジェクトにアクセスするエディターの拡張機能から](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md)詳細についてはします。  
  
## <a name="services"></a>サービス  
 エディターのサービスは、複数のコンポーネント間で共有され、サービスを提供する、通常 1 つのエンティティです。  
  
|インポート|説明|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|ファイル拡張子の間のリレーションシップと<xref:Microsoft.VisualStudio.Utilities.IContentType>オブジェクト。|  
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|<xref:Microsoft.VisualStudio.Utilities.IContentType> オブジェクトのコレクション。|  
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation> オブジェクト|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|多くのエディター アダプター オブジェクト。<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|  
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch>テキストを指定したビューのオブジェクト。|  
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextBuffer>。|  
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextDocument>。|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>の相違点です。|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>の相違点です。|  
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>または<xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>です。|  
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> 、一連の<xref:Microsoft.VisualStudio.Text.ITextBuffer>オブジェクト。|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>の<xref:Microsoft.VisualStudio.Text.ITextBuffer>です。|  
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>の<xref:Microsoft.VisualStudio.Text.Editor.ITextView>です。|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>の<xref:Microsoft.VisualStudio.Text.Editor.ITextView>です。|  
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap>の<xref:Microsoft.VisualStudio.Text.Editor.ITextView>です。|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|コレクションを保持<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>オブジェクト。|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>テキスト バッファー。|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>テキスト ビュー用です。|  
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions>指定されたスコープのです。|  
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMap>テキスト ビュー用です。|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent>の<xref:Microsoft.VisualStudio.Text.Editor.ITextView>です。|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|自動インデントを通過、<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider>オブジェクト。|  
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|管理、<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>の<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>です。|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>。|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|スナップショットの範囲のセットから RTF 形式のテキストを生成します。|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer>の<xref:Microsoft.VisualStudio.Text.Editor.ITextView>です。|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|A<xref:System.Windows.Media.TextFormatting.TextParagraphProperties>のビューの線にテキストを書式設定します。|  
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|A<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations>オブジェクトに対して、<xref:Microsoft.VisualStudio.Text.Editor.ITextView>です。|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|テキストのスナップショットを検索します。|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>の<xref:Microsoft.VisualStudio.Text.ITextBuffer>によって<xref:Microsoft.VisualStudio.Utilities.IContentType>です。|  
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>テキスト ビュー用です。|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|グリフの標準セットです。|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack>の<xref:Microsoft.VisualStudio.Text.Editor.ITextView>です。|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|トラックのキーボード処理します。|  
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|標準<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>オブジェクト。|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|テキスト バッファー間の関係を維持し、<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory>オブジェクト。|  
  
## <a name="other-imports"></a>他のインポート  
 プロバイダー ファクトリとブローカーは、通常、複数のコンポーネントで複数のインスタンスがエンティティです。  
  
|インポート|説明|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|<xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>型の<xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>) の特定のバッファー。|  
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|テキスト マーカー タガー (、<xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>型の<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>)。|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider>の指定された<xref:Microsoft.VisualStudio.Text.Editor.ITextView>です。|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>。|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>。|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>。|  
  
## <a name="see-also"></a>関連項目  
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)