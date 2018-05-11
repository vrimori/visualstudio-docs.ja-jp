---
title: エディターのアダプターで新しいまたは変更された動作 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 22028b1b2725f184c3d5748f2885a17d4bff0c60
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>エディターのアダプターで新しいまたは変更された動作
以前のバージョンの Visual Studio コア エディターと照らして記述されたコードを更新して、新しい API を使用するのではなくエディター アダプター (または shim) を使用する場合は、注意してください、次の相違点エディター アダプターの動作に関しては、以前のコア エディターです。  
  
## <a name="features"></a>フィーチャー  
  
#### <a name="using-setsite"></a>SetSite() を使用します。  
 呼び出す必要があります<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A>テキスト バッファーのテキスト ビューを作成し、それらの他の操作を実行する前に、コード ウィンドウです。 ただし、これを使用する場合は必要はありません、<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>をこのサービスの Create() メソッド自体を呼び出すために、それらを作成する<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A>です。  
  
#### <a name="hosting-ivscodewindow-and-ivstextview-in-your-own-content"></a>独自のコンテンツで IVsCodeWindow と IVsTextView をホストしています。  
 両方をホストできる<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>Win32 モードまたは WPF モードを使用して、独自のコンテンツにします。 ただし、2 つのモードでは、いくつか違いがあることに注意おく必要があります。  
  
##### <a name="using-win32-and-wpf-versions-of-ivscodewindow"></a>IVsCodeWindow の Win32 と WPF のバージョンを使用します。  
 派生したエディターのコード ウィンドウは<xref:Microsoft.VisualStudio.Shell.WindowPane>、古い Win32 を実装する<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>だけでなく、新しい WPF インターフェイス<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane>インターフェイスです。 使用することができます、 <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> HWND ベースのホスティング環境を作成するメソッド、または<xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A>WPF ホスティング環境を作成するメソッド。 基になるエディターでは、WPF では、常に使用しますが、独自のコンテンツに直接このウィンドウを埋め込む場合、ホスティングの要件に適したウィンドウの種類を作成することができます。  
  
##### <a name="using-win32-and-wpf-versions-of-ivstextview"></a>IVsTextView の Win32 と WPF のバージョンを使用します。  
 設定することができます、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Win32 モードまたは WPF モードにします。  
  
 エディター ファクトリは、既定では、HWND 内でホストされますテキスト ビューを作成するときに、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> HWND を返します。 WPF コントロール内のエディターを埋め込むにはこのモードを使用する必要があります。  
  
 テキスト ビューを WPF モードに設定するに呼び出す必要があります<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A>を渡して<xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3>のフラグ、初期化の 1 つとして、`InitView`パラメーター。 取得することができます、<xref:System.Windows.FrameworkElement>を呼び出して<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A>です。  
  
 WPF のモードは、2 つの方法で Win32 モードによって異なります。 最初に、テキスト ビューの場合は、WPF のコンテキストでホストされていることができます。 キャスト WPF ウィンドウにアクセスすることができます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>に<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane>および呼び出し<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A>です。 2 番目、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A>引き続きの位置を確認し、それにフォーカスを設定にのみ使用できます、HWND がこの HWND を返します。 影響を与えないため、エディターで、ウィンドウを描画する方法が WM_PAINT メッセージに応答するこの HWND を使用する必要がありますできません。 この HWND は、アダプターを使用して新しいエディター コードへの移行を容易にするためにのみ存在します。 使用する必要がありますしないことを強くお勧め`VIF_NO_HWND_SUPPORT`コンポーネントには、HWND から返された HWND の制限のため、作業が必要な場合`GetWindowHandle`このモードでいます。  
  
#### <a name="passing-arrays-as-parameters-in-native-code"></a>ネイティブ コードでパラメーターとしての配列の受け渡し  
 これは、配列とその数を含むパラメーターが設定されているレガシ エディター API での多くの方法です。 例を示します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 ネイティブ コードでこれらのメソッドを呼び出す場合、一度に 1 つだけの要素に渡す必要があります。 複数の要素に渡す場合、プライマリ相互運用機能の実装の問題のため、呼び出しは拒否されます。  
  
 問題がなどのメソッドより複雑な<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A>します。 このメソッドが呼び出されるたびには、単にこのメソッドを呼び出す 3 回 3 つの異なるマーカーの種類で考えられるにないために、無視されたマーカーの種類、前の一覧をクリアします。 唯一の対処法では、このメソッドを呼び出すマネージ コードでのみです。  
  
#### <a name="threading"></a>スレッド  
 バッファーのアダプターは、UI スレッドから常に呼び出す必要があります。 バッファーのアダプターは、マネージ オブジェクト、つまり、マネージ コードからそれを呼び出すことは COM マーシャ リングをバイパスし、呼び出しは UI スレッドに自動的にマーシャ リングされませんです。  使用する必要があります、バック グラウンド スレッドからバッファー アダプターを呼び出す場合<xref:System.Windows.Threading.Dispatcher.Invoke%2A>または同様の方法です。  
  
#### <a name="lockbuffer-methods"></a>LockBuffer メソッド  
 すべての LockBuffer() メソッドの使用は推奨されていません。 例を示します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>イベントをコミットします。  
 コミット イベントがサポートされていません。 これらのイベントをアドバイスするメソッドを呼び出すと、メソッドはエラー コードを返しますが、します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>TextEditorEvents  
 <xref:EnvDTE.TextEditorEvents> Commit() 上に起動しません。 代わりに、これらはテキスト変更されるたびに起動します。  
  
#### <a name="text-markers"></a>テキスト マーカー  
 呼び出す必要があります<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A>で<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>それらを削除するときのオブジェクトします。 以前のバージョンでは、マーカーのリリースにのみ必要です。  
  
#### <a name="line-numbers"></a>[行番号]  
 上のメソッドのさまざまな<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>いない行番号をその要素のアウトライン表示とテキストの折り返し、Visual Studio 2008 のように、行番号を基になるバッファーの行番号に対応しています。  
  
 影響を受ける方法 (リストは完全ではありません) 次のとおりです。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A>  
  
#### <a name="outlining"></a>アウトライン  
 クライアント<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>を使用して追加されたアウトライン領域のみを参照してください<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>または<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A>です。 エディター アダプターを介して追加されないので、アドホック地域は表示されません。 同様に、これらのクライアントは表示しますされません (c# および C++ を含む) のエディターのアダプターではなく、新しいエディター コードを使用している言語で追加の領域のアウトライン表示。  
  
#### <a name="line-heights"></a>行の高さ  
 エディターで、新しいテキスト行は、フォント サイズやその他の行を基準とした行を移動することがありますした変換が可能な行によって、さまざまな高さを持つことができます。 などのメソッドによって返される行の高さ<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A>が適用された行変換なしで既定のフォント サイズを使用して行の高さ。 この高さは、ビュー内の行の実際の高さを表さない場合があります。  
  
#### <a name="eventing-and-undo"></a>イベント処理と元に戻す  
 新しいエディターで、ビューはレンダリングと元に戻すクラスターが開いている場合でも、継続的にイベントを発生させるなどの操作の実行が続行します。 この動作は従来のビューは、これらの操作を元に戻すクラスターの終了が終了するまでに実行されなかったの場合と異なります。  
  
#### <a name="intellisense"></a>IntelliSense  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A>メソッドは、いずれかが実装されていないクラスを渡す場合は失敗<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2>または<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3>です。 カスタム Win32 オーナー描画のポップアップがサポートされていません。  
  
#### <a name="smarttags"></a>スマート タグ  
 作成されたスマート タグのアダプターはサポートされていません<xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow>、および<xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2>インターフェイスです。  
  
#### <a name="dte"></a>DTE  
 <xref:EnvDTE80.IncrementalSearch> 実装されていません。  
  
## <a name="unimplemented-methods"></a>実装されていないメソッド  
 一部のメソッドがテキスト バッファー アダプター、テキスト ビュー アダプター、およびテキスト レイヤー アダプターで実装されていません。  
  
|Interface|実装されていません|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` 実装されていません。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> アウトラインの UI では無視されますが、アダプターに実装されます。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> アウトラインの UI では無視されますが、アダプターに実装されます。|