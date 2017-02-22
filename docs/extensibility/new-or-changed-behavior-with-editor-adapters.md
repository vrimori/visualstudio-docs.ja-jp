---
title: "エディターのアダプターで新しいまたは変更された動作 | Microsoft Docs"
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
  - "エディター [Visual Studio SDK] レガシー - アダプターの動作"
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# エディターのアダプターで新しいまたは変更された動作
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

以前のバージョンの Visual Studio の中核となるエディターに対して記述したコードを更新するし、新しい API を使用するのではなく、エディターのアダプター \(shim\) を使用する場合、前のコア エディターに関してエディター アダプターの動作に次の相違点の留意必要があります。  
  
## 機能  
  
#### SetSite\(\) を使用します。  
 呼び出す必要があります <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> テキスト バッファーのテキスト ビューを作成し、それらの他の処理を実行する前に、コード ウィンドウです。 ただし、これを使用する場合は必要はありません、 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> このサービスの Create\(\) メソッド自体を呼び出すために、それを作成する <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A>です。  
  
#### 独自のコンテンツで IVsCodeWindow と IVsTextView をホストしています。  
 両方をホストする <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> と <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Win32 モードまたは WPF モードのいずれかを使用して、独自のコンテンツにします。 ただし、2 つのモードでは、いくつか違いがあることに留意おく必要があります。  
  
##### IVsCodeWindow の Win32 と WPF のバージョンを使用します。  
 コード エディターがから派生した <xref:Microsoft.VisualStudio.Shell.WindowPane>, 、古い Win32 を実装する <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> だけでなく、新しい WPF インターフェイス <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> インターフェイスです。 使用することができます、 <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> HWND ベースのホスティング環境を作成する方法、または <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> WPF ホスティング環境を作成します。 基になるエディターは、常に、WPF を使用しますが、独自のコンテンツに直接このウィンドウを埋め込む場合、ホスティングの要件に適合するウィンドウの種類を作成することができます。  
  
##### IVsTextView の Win32 と WPF のバージョンを使用します。  
 設定することができます、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Win32 モードまたは WPF モードにします。  
  
 エディター ファクトリは、既定では、HWND 内でホストされているテキスト ビューを作成するときと <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> HWND を返します。 WPF コントロール内のエディターを埋め込むには、このモードを使用する必要があります。  
  
 テキスト ビューを WPF モードに設定するに呼び出す必要があります <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> を渡して <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> のフラグ、初期化の 1 つとして、 `InitView` パラメーター。 取得できます、 <xref:System.Windows.FrameworkElement> を呼び出して <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A>します。  
  
 WPF のモードは、2 つの方法で Win32 モードによって異なります。 最初に、テキスト ビューの場合は、WPF のコンテキストでホストされていることができます。 キャストして WPF ウィンドウにアクセスすることができます、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> に <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> を呼び出すと <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A>です。 2 番目、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> もの位置を確認し、それにフォーカスを設定にのみ使用できますは HWND がこの HWND を返します。 エディターで、ウィンドウを描画する方法には影響があるためこの HWND に WM\_PAINT メッセージに応答する使用する必要があります。 この hwnd の分離は、アダプターを使用して新しいエディターのコードへの移行を容易にするためにのみ存在します。 使用する必要がありますしないことを強くお勧め `VIF_NO_HWND_SUPPORT` コンポーネントから返された HWND における制限事項が原因で、機能する hwnd の分離が必要な場合 `GetWindowHandle` このモードでは while です。  
  
#### ネイティブ コードで配列をパラメーターとして渡す  
 これは、配列とその数を含むパラメーターが設定されているレガシ エディター API での多くの方法です。 例を示します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 ネイティブ コードでこれらのメソッドを呼び出す場合、一度に 1 つだけの要素に渡す必要があります。 複数の要素を渡す場合、プライマリ相互運用機能の実装に関する問題のため、呼び出しは拒否されます。  
  
 問題がなどのメソッドより複雑な <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A>です。 このメソッドが呼び出されるたびには、単に 3 つの異なるマーカーの種類を 3 回このメソッドを呼び出すことはできませんので、無視のマーカーの種類の前の一覧をクリアします。 唯一の対処法では、このメソッドを呼び出すマネージ コードでのみです。  
  
#### スレッド  
 バッファーのアダプターは、UI スレッドから常に呼び出す必要があります。 バッファー アダプターは、マネージ オブジェクト、つまり、マネージ コードからそれを呼び出すことは COM マーシャ リングが省略され、呼び出しは UI スレッドに自動的にマーシャ リングされませんです。  使用する必要があります、バック グラウンド スレッドからバッファー アダプターを呼び出す場合 <xref:System.Windows.Threading.Dispatcher.Invoke%2A> または同様の方法です。  
  
#### LockBuffer メソッド  
 すべての LockBuffer\(\) メソッドが使用されていません。 例を示します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### イベントをコミットします。  
 コミット イベントがサポートされていません。 これらのイベントにアドバイスするメソッドを呼び出すと、エラー コードを返すメソッドとします。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### TextEditorEvents  
 <xref:EnvDTE.TextEditorEvents> Commit\(\) 上に起動しません。 代わりにテキスト変更されるごとに起動します。  
  
#### テキスト マーカー  
 呼び出す必要があります <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> に <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> オブジェクトを削除します。 以前のバージョンでは、マーカーのリリースにのみ必要です。  
  
#### \[行番号\]  
 上のメソッドのさまざまな <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> と <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>, いない行番号をその要素のアウトライン表示し、Visual Studio 2008 と同様に、ワード ラップ、行番号を基になるバッファー行の番号に対応します。  
  
 \(一覧は完全ではありません\)、次の影響を受ける方法。  
  
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
  
#### アウトライン  
 クライアントの <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> を使用して追加されたアウトライン領域のみを参照してください <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>または <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A>です。 エディターのアダプターを追加されないのでない暫定的な領域が表示されます。 同様に、これらのクライアントでは、アウトライン エディター アダプターではなく、新しいエディターのコードを使用している言語 \(c\# および C\+\+ を含む\) によって追加された領域はわかりません。  
  
#### 行の高さ  
 新しいエディターには、テキストの行はフォント サイズ、およびその他の行を基準とした行に移動が可能な行変換によって、さまざまな高さを設定できます。 などのメソッドによって返される行の高さ <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> を適用しない行の変換を含む既定のフォント サイズを使用して線の高さ。 この高さは、ビュー内の行の実際の高さを反映しない可能性があります。  
  
#### イベント処理および元に戻す  
 新しいエディター ビューをレンダリングして、元に戻すクラスターが開いている場合でも、継続的にイベントを発生させるなどの操作の実行が続行されます。 この動作は異なること従来のビューは、元に戻すクラスターの終了後になるまでこれらの操作を実行しませんでした。  
  
#### IntelliSense  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> メソッドは、いずれかが実装されていないクラスを渡す場合は失敗 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> または <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3>です。 カスタムの Win32 オーナー描画ポップアップがサポートされていません。  
  
#### スマート タグ  
 作成のスマート タグのアダプターはサポートされていません <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>, 、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow>, 、および <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> インターフェイスです。  
  
#### DTE  
 <xref:EnvDTE80.IncrementalSearch> 実装されていません。  
  
## 未実装のメソッド  
 テキスト バッファー アダプター、テキスト ビュー アダプター、およびテキスト レイヤー アダプターにいくつかのメソッドが実装されていません。  
  
|インターフェイス|実装されていません|  
|--------------|---------------|  
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