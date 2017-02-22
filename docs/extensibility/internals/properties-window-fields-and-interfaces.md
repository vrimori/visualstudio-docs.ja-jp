---
title: "プロパティ ウィンドウのフィールドとインターフェイス | Microsoft Docs"
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
  - "[プロパティ] ウィンドウ、フィールド、およびインターフェイス"
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# プロパティ ウィンドウのフィールドとインターフェイス
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

どの情報を ENT8ENT \[出力\] ウィンドウに表示されるかを決定する選択のモデルはIDE でフォーカスのあるウィンドウに基づいています。  選択したウィンドウ内のすべてのウィンドウとオブジェクトは押されたグローバルな選択のコンテキストへの任意のコンテキスト オブジェクトを持つことができます。  環境はウィンドウにフォーカスがあるときにウィンドウ フレームの値を使用してグローバルな選択のコンテキストを更新します。  フォーカス変更は次のコンテキストを選択します。  
  
## IDE の追跡の選択  
 IDE が所有するフレーム ウィンドウまたはサイトには <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> というサービスがあります。  次の手順では\[出力\] ウィンドウに表示 ENT5ENT の内容を変更するために別の開いているウィンドウにフォーカスを移動するか **ソリューション エクスプローラー**  で別のプロジェクト項目を選択したときに選択されるの変更がどのように実装されるかを示します。  
  
1.  選択したウィンドウに配置される VSPackage によって作成されたオブジェクトは <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> を <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> を開始するに <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> を呼び出します。  
  
2.  選択コンテナーは選択したウィンドウで<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> のオブジェクトを作成します。  環境のリスナーを変更 ENT0ENT の \[ウィンドウ\] のが通知するために選択が変更 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>VSPackage を呼び出す場合。  また新しい階層に選択項目との関連情報へのアクセスを提供します。  
  
3.  <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> を呼び出し`VSHPROPID_BrowseObject` のパラメーターで選択した項目の階層を渡します <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> のオブジェクトを作成します。  
  
4.  [IDispatch Interface](http://msdn.microsoft.com/ja-jp/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) から派生したオブジェクトは要求された項目の <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> の戻り <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 環境はそれをラップします \(次の手順を参照してください。  呼び出しが失敗した場合その環境は階層の項目を指定する選択コンテナー <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> を渡す `IVsHierarchy::GetProperty` に目を作成します。  
  
     \(\)  **ソリューション エクスプローラー**  実行環境指定されたウィンドウが <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> する VSPackage を構成するときは <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> VSPackage プロジェクトは作成されません。  
  
5.  環境ではオブジェクトを ENT0ENT \[出力\] ウィンドウに表示するに `IDispatch` のインターフェイスに基づいて取得するに <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> のメソッドを呼び出します。  
  
 \[入力\] ENT0ENT ウィンドウの値が変更されると要素の値に対する変更を報告する VSPackage の実装 `IVsTrackSelectionEx::OnElementValueChangeEx` と `IVsTrackSelectionEx::OnSelectionChangeEx`。  環境はプロパティ値と同期する ENT0ENT \[出力\] ウィンドウに情報が表示されます <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> ままに <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> またはを呼び出します。  詳細については、「[\[プロパティ\] ウィンドウでプロパティ値を更新](../Topic/Updating%20Property%20Values%20in%20the%20Properties%20Window.md)」を参照してください。  
  
 その項目に関連するプロパティを表示するに  **ソリューション エクスプローラー**  の別のプロジェクト項目を選択するだけでなく\[ENT1ENT\] ウィンドウのドロップダウン リストを使用してからフォームまたはドキュメント ウィンドウ内のオブジェクトを選択できます。  詳細については、「[プロパティ ウィンドウのオブジェクトの一覧](../../extensibility/internals/properties-window-object-list.md)」を参照してください。  
  
 情報がアルファベット順のカテゴリ別に属するへの ENT0ENT \[出力\] ウィンドウのグリッドに表示されます \(存在する場合\)または \[ENT1ENT\] ウィンドウの適切なボタンをクリックして選択したオブジェクトのプロパティ ページを開く方法を変更できます。  詳細については、「[プロパティ ウィンドウのボタン](../../extensibility/internals/properties-window-buttons.md)」および「[\[プロパティ ページ\]](../../extensibility/internals/property-pages.md)」を参照してください。  
  
 最後に\[出力\] ウィンドウ ENT0ENT の下 ENT1ENT は\[出力\] ウィンドウのグリッドで選択したフィールドについて説明します。  詳細については、「[\[プロパティ\] ウィンドウからのフィールドの説明の取得](../Topic/Getting%20Field%20Descriptions%20from%20the%20Properties%20Window.md)」を参照してください。  
  
## 参照  
 [プロパティを拡張します。](../../extensibility/internals/extending-properties.md)