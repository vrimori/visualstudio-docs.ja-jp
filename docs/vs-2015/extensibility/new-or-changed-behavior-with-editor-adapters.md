---
title: アダプターのエディターで新しいまたは変更された動作 |Microsoft Docs
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
- editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 740fc83a9ded8ad35b93120d6fdec5767ceeea82
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49178959"
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>エディターのアダプターを搭載した新規または変更された動作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

以前のバージョンの Visual Studio コア エディターと照らして記述されたコードを更新する、新しい API を使用するのではなく、エディターのアダプター (または shim) を使用する場合は、エディターのアダプターの動作に次の相違点の注意する必要があります。に関しては、前のコア エディター。  
  
## <a name="features"></a>フィーチャー  
  
#### <a name="using-setsite"></a>SetSite() を使用します。  
 呼び出す必要があります<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A>テキスト バッファーのテキストのビューを作成し、それらの他の操作を実行する前に、コード ウィンドウ。 ただし、これを使用する場合は必要はありません、<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>このサービスの Create() メソッド自体を呼び出すために、それを作成する<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A>します。  
  
#### <a name="hosting-ivscodewindow-and-ivstextview-in-your-own-content"></a>独自のコンテンツで IVsCodeWindow と IVsTextView をホストしています。  
 両方をホストできる<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>Win32 モードまたは WPF モードのいずれかを使用して、独自のコンテンツ。 ただし、2 つのモードでは、いくつか違いがあることに注意してくださいおく必要があります。  
  
##### <a name="using-win32-and-wpf-versions-of-ivscodewindow"></a>IVsCodeWindow の Win32 と WPF のバージョンを使用します。  
 派生したエディターのコード ウィンドウは<xref:Microsoft.VisualStudio.Shell.WindowPane>、古い Win32 を実装する<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>インターフェイスの新しい WPF と<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane>インターフェイス。 使用することができます、 <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> HWND ベースのホスティング環境を作成するメソッドまたは<xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A>WPF のホスティング環境を作成します。 基になるエディターは、常に、WPF を使用しますが、このウィンドウを独自のコンテンツに直接埋め込む場合は、ホスティングの要件に合ったウィンドウの種類を作成することができます。  
  
##### <a name="using-win32-and-wpf-versions-of-ivstextview"></a>IVsTextView の Win32 と WPF のバージョンを使用します。  
 設定することができます、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Win32 モードまたは WPF モードにします。  
  
 エディター ファクトリを既定では、HWND 内でホストされているテキスト ビューを作成するときに、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> HWND を返します。 WPF コントロール内のエディターを埋め込むには、このモードを使用する必要があります。  
  
 テキスト ビューを WPF モードに設定するに呼び出す必要がある<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A>を渡します<xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3>のフラグ、初期化の 1 つとして、`InitView`パラメーター。 取得することができます、<xref:System.Windows.FrameworkElement>呼び出して<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A>します。  
  
 WPF のモードは、2 つの方法で Win32 モードによって異なります。 まず、テキスト ビューは、WPF のコンテキストでホストできます。 キャストすることによって、WPF ウィンドウを表示できます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>に<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane>を呼び出すと<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A>します。 2 番目、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A>も返しますが、HWND がこの HWND の位置を確認し、フォーカスの設定にのみ使用できます。 エディターで、ウィンドウを描画する方法には影響があるため、WM_PAINT メッセージに応答するこの HWND を使用する必要がありますできません。 この HWND では、アダプターを使用して新しいエディター コードへの移行を容易にするためにのみ存在します。 使用する必要がありますしないことを強くお勧め`VIF_NO_HWND_SUPPORT`コンポーネントから返される HWND の制限のため、操作する HWND を必要とする場合`GetWindowHandle`このモードでいます。  
  
#### <a name="passing-arrays-as-parameters-in-native-code"></a>ネイティブ コードで配列をパラメーターとして渡す  
 配列とその数を含むパラメーターを持つ API のレガシのエディターで多くの方法はあります。 例を示します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 ネイティブ コードでこれらのメソッドを呼び出す場合は、一度に 1 つだけの要素で渡す必要があります。 1 つ以上の要素を渡す場合、プライマリ相互運用機能の実装の問題が原因、呼び出しは拒否されます。  
  
 問題がなどの方法でより複雑な<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A>します。 このメソッドが呼び出されるたびには、単に 3 つの異なるマーカーの種類を 3 回このメソッドを呼び出すことはできませんので、無視のマーカーの種類の前の一覧をクリアします。 唯一の対処法では、マネージ コードでのみこのメソッドを呼び出します。  
  
#### <a name="threading"></a>スレッド  
 バッファーのアダプターは、UI スレッドから常に呼び出す必要があります。 バッファーのアダプターは、マネージ オブジェクト、つまり、呼び出しが自動的にマーシャ リングできない、UI スレッドへとマネージ コードからそれを呼び出すことは COM マーシャ リングをバイパスします。  使用する必要があります、バック グラウンド スレッドからバッファー アダプターを呼び出す場合<xref:System.Windows.Threading.Dispatcher.Invoke%2A>または同様のメソッド。  
  
#### <a name="lockbuffer-methods"></a>LockBuffer メソッド  
 すべての LockBuffer() メソッドが非推奨とされます。 例を示します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>イベントをコミットします。  
 コミット イベントがサポートされていません。 これらのイベントを通知するメソッドを呼び出すと、エラー コードを返すメソッドがします。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>TextEditorEvents  
 <xref:EnvDTE.TextEditorEvents> Commit() で起動しません。 代わりにテキスト変更されるごとに起動されます。  
  
#### <a name="text-markers"></a>テキスト マーカー  
 呼び出す必要があります<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A>で<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>オブジェクトの削除を行うときにします。 以前のバージョンでは、マーカーのリリースにのみ必要です。  
  
#### <a name="line-numbers"></a>[行番号]  
 メソッドのさまざまな<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>いない行番号をその要素のアウトラインと Visual Studio 2008 のように、ワード ラップ、行番号は、基になるバッファーの行番号に対応します。  
  
 影響を受ける方法 (リストはすべてを網羅) 次に示します。  
  
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
 クライアントの<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>を使用して追加されているアウトライン領域のみが表示されます<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>または<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A>します。 アドホックのリージョンは、エディター アダプターを介して追加されないので、表示されなくなります。 同様に、これらのクライアントでは、アウトライン、エディターのアダプターではなく、新しいエディターのコードを使用している言語 (c# および C++ を含む) によって追加された領域が見えない。  
  
#### <a name="line-heights"></a>行の高さ  
 新しいエディターでテキスト行はフォント サイズやその他の行を基準とした行が移動可能な行の変換によって、異なる高さを持つことができます。 などのメソッドによって返される行の高さ<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A>が適用された行変換なしで既定のフォント サイズを使用して行の高さ。 この高さは、ビュー内の行の実際の高さを反映しない可能性があります。  
  
#### <a name="eventing-and-undo"></a>イベント処理および元に戻す  
 新しいエディターでは、ビューをレンダリングし、元に戻すクラスターが開いている場合でも継続的に、イベントの発生などの操作を実行が続行されます。 この動作は従来のビューは、これらの操作を元に戻すクラスターの終了が終了するまでに実行されなかったは異なります。  
  
#### <a name="intellisense"></a>IntelliSense  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A>メソッドは、いずれかを実装しないクラスを渡す場合は失敗<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2>または<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3>します。 カスタム Win32 オーナー描画のポップアップがサポートされていません。  
  
#### <a name="smarttags"></a>スマート タグ  
 使用すると、作成されたスマート タグのアダプターのサポートはありません<xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow>、および<xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2>インターフェイス。  
  
#### <a name="dte"></a>DTE  
 <xref:EnvDTE80.IncrementalSearch> 実装されていません。  
  
## <a name="unimplemented-methods"></a>未実装のメソッド  
 テキスト バッファー アダプター、テキスト ビュー アダプター、およびテキスト レイヤー アダプターにはいくつかのメソッドが実装されていません。  
  
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
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> アウトラインの UI では無視されるが、アダプターに実装されます。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> アウトラインの UI では無視されるが、アダプターに実装されます。|

