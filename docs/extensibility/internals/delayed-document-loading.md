---
title: "ドキュメントの読み込みの遅延 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# ドキュメントの読み込みの遅延
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ユーザーは、Visual Studio ソリューションを閉じて、ときに関連するドキュメントのほとんどはすぐに読み込まれません。 ドキュメント ウィンドウの枠が初期化が保留中の状態で作成され、\(スタブ フレームと呼ばれます\) のプレース ホルダーのドキュメントを実行しているドキュメント テーブル \(RDT\) では配置されます。  
  
 拡張機能が原因で、プロジェクトのドキュメントが読み込まれる前に、ドキュメント内の要素を照会することで不必要に読み込まれる場合があります。 これにより、Visual Studio の全体的なメモリ使用量が向上します。  
  
## ドキュメントの読み込み  
 ユーザーにアクセスすると、ドキュメントなど、ウィンドウ フレームのタブをクリックして、スタブ フレームとドキュメントが完全に初期化します。 ドキュメントは、ドキュメント データを取得するには、直接 RDT へのアクセスまたはない、RDT に直接アクセスする、次の呼び出しの 1 つのいずれかのドキュメントのデータを要求する拡張機能により初期化できます。  
  
-   ウィンドウ フレームの表示方法: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>です。  
  
-   ウィンドウ フレーム GetProperty メソッド <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 、次のプロパティのいずれかにします。  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
 拡張機能は、マネージ コードを使用している場合は、呼び出す必要はありません <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> ことを確認してから、初期化が保留中の状態では、ドキュメントまたはドキュメントが完全に初期化する. これは、このメソッドは常にドキュメントを返すので、データ オブジェクト、必要な場合は作成します。 代わりに、メソッドのいずれかを IVsRunningDocumentTable4 インターフェイスで呼び出す必要があります。  
  
 拡張機能は、C\+\+ を使用している場合は、渡す `null` したくないパラメーターです。  
  
 関連するプロパティを要求する前に、次の方法のいずれかを呼び出すことによって、不要なドキュメントの読み込みを回避できます。 その他のプロパティを要求する前にします。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 使用して <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>。 このメソッドが戻る、 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> の値を含むオブジェクトを <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> ドキュメントが初期化されていない場合。  
  
 ドキュメントが完全に初期化されるときに発生する RDT イベントをサブスクライブして、ドキュメントが読み込まれたときに調べることができます。 2 つの可能性があります。  
  
-   イベント シンクを実装する場合 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, にサブスクライブできます <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,、  
  
-   サブスクライブする場合は、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>です。  
  
 仮想的なドキュメント アクセスのシナリオを次に示します。 拡張機能が開いているドキュメントに関する情報を表示する Visual Studio、たとえば、編集カウントとロック ドキュメント データについて何か。 列挙を使用して、RDT ドキュメント <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, を呼び出して <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> 編集ロック カウント、およびドキュメント データを取得するためには、各ドキュメントのです。 ドキュメントが、初期化が保留中の状態の場合は、ドキュメント データを要求する場合は、不必要に初期化します。  
  
 効率的な方法は、これを使用する、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> 、編集のロック数を取得し、使用する <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> ドキュメントが初期化されているかどうかを判断します。 フラグが含まれない場合 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, 、ドキュメントは既に初期化されていると、ドキュメント データを要求して <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> 、不要な初期化は行われません。 フラグには含まれている場合 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, 、拡張機能では、ドキュメントが初期化されるまでドキュメント データを要求しないようにする必要があります。 これは、OnAfterAttributeChange\(Ex\) イベント ハンドラーで検出できます。  
  
## 参照のかどうかは、強制的に初期化する拡張機能のテスト  
 拡張機能が初期化を強制的検出しにくいので、ドキュメントが初期化されているかどうかを示すためにキューを表示することはありません。 テキストが完全に初期化されていないすべてのドキュメントのタイトルが発生するため、容易に確認するレジストリ キーを設定することができます `[Stub]` タイトルにします。  
  
 **HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0\\BackgroundSolutionLoad\]**, 、 **StubTabTitleFormatString** に **{0} \[Stub\]**します。