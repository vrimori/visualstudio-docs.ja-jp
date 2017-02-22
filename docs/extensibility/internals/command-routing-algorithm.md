---
title: "コマンド ルーティング アルゴリズム | Microsoft Docs"
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
  - "ルーティング コマンド"
  - "コマンド ルーティング"
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# コマンド ルーティング アルゴリズム
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio でのコマンドは、さまざまなコンポーネントによって処理されます。 コマンドは、現在の選択に基づいて、最も内側のコンテキストから \(グローバルとも呼ばれます\) の最も外側のコンテキストにルーティングされます。 詳細については、「[可用性](../../extensibility/internals/command-availability.md)」を参照してください。  
  
## コマンドの解決の順序  
 レベルは次のコマンドのコンテキストのコマンドが渡されます。  
  
1.  アドイン: 環境には、コマンドに存在するすべてのアドインを最初に用意されています。  
  
2.  コマンドの優先順位: を使用してこれらのコマンドが登録されている <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>します。 Visual Studio のすべてのコマンドを呼び出して、登録されている順序で呼び出されます。  
  
3.  コンテキスト メニュー コマンド: コンテキスト メニューにあるコマンドが最初に一般的なルーティングのコンテキスト メニューとその後に提供されるコマンドの対象に提供されています。  
  
4.  ツールバーは、コマンド ターゲットを設定します。 を呼び出すときに次のコマンドのターゲットが登録されて <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>します。`pCmdTarget` パラメーターを指定できます `null`します。 ない場合 `null`, を設定して、ツールバー上にあるすべてのコマンドを更新するコマンドは、このターゲットを使用します。 シェルでは、ツールバーを設定し、としてウィンドウ フレームを渡すかどうか、 `pCmdTarget` ため、ウィンドウ フレームを使って、ツールバーのフローのコマンドにすべての更新プログラムもときであるフォーカスがあります。  
  
5.  ツール ウィンドウ: ツール ウィンドウで、通常を実装している、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> インターフェイスを実装する必要も、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> インターフェイスのツール ウィンドウがアクティブなウィンドウ時に、Visual Studio はコマンドの対象を取得するようにします。 ただし、ツール ウィンドウを持つ場合は、フォーカスがある、 **プロジェクト** ウィンドウで、次のコマンドにルーティング、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 選択された項目の共通の親であるインターフェイスです。 コマンドにルーティングしてこの選択は、複数のプロジェクトにまたがっている場合、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> 階層です。<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> インターフェイスには、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> メソッドに対応するコマンドに似ていますが、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> インターフェイスです。  
  
6.  ドキュメント ウィンドウ: コマンドに RouteToDocs フラグが .vsct ファイルの設定がある場合は、Visual Studio によって検索、ドキュメントのビュー オブジェクトに、次のいずれかのコマンドの対象のインスタンス、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> インターフェイスまたはドキュメント オブジェクトのインスタンス \(通常、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> インターフェイスまたは <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> インターフェイス\)。 Visual Studio でのコマンドをルーティング ドキュメント ビューのオブジェクトが、コマンドをサポートしていない場合、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 返されるインターフェイスです。 \(これは、データ オブジェクトのドキュメントのオプションのインターフェイスです\)。  
  
7.  現在の階層: 現在の階層がアクティブなドキュメント ウィンドウまたはで選択されている階層を所有するプロジェクトを指定できます **ソリューション エクスプ ローラー**します。 Visual Studio によって検索、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 現在、またはアクティブな階層で実装されるインターフェイスです。 階層では、プロジェクト項目のドキュメント ウィンドウにフォーカスがある場合でも、階層がアクティブにするたびに、有効なコマンドをサポートする必要があります。 ただし、コマンドの場合にのみ適用されている **ソリューション エクスプ ローラー** を使用してフォーカスをサポートする必要があります、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> インターフェイスとその <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>メソッドです。  
  
     **切り取り**, 、**コピー**, 、**貼り付け**, 、**削除**, 、**の名前を変更**, 、**Enter**, と **DoubleClick** コマンドは、特別な処理を必要とします。 処理する方法については **削除** と **削除** 階層では、コマンドを参照してください、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> インターフェイスです。  
  
8.  Global: 場合前に説明したコンテキストでコマンドが処理されていない、Visual Studio を試みます VSPackage を実装するコマンドを所有しているにルーティング、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> インターフェイスです。 Visual Studio を呼び出すといない読み込まれる VSPackage が既に読み込まれていませんが場合、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> メソッドです。 される場合にのみ VSPackage が読み込まれる、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> メソッドが呼び出されます。  
  
## 参照  
 [コマンドのデザイン](../../extensibility/internals/command-design.md)