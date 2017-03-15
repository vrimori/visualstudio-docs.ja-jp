---
title: "コマンドを使用できるようにします。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "メニュー [Visual Studio SDK] コマンド"
  - "ベスト プラクティスでコマンドをメニューとツールバー"
  - "ツールバー [Visual Studio] のベスト プラクティス"
  - "メニュー コマンド、ベスト プラクティス"
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
caps.latest.revision: 35
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 35
---
# コマンドを使用できるようにします。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

複数ある Vspackage が Visual Studio に追加されると、ユーザー インターフェイス \(UI\) をコマンドで overcrowded になる場合があります。 次のように、この問題を減らすために、パッケージをプログラムすることができます。  
  
-   パッケージのプログラム、ユーザー場合にのみ読み込まれるように必要があります。  
  
-   統合開発環境 \(IDE\) の現在の状態のコンテキストで受ける必要がある場合にのみ、そのコマンドが表示されるように、パッケージをプログラムします。  
  
## 遅延読み込み  
 一般的な方法を有効にするのには、UI では、そのコマンドが表示されますが、ユーザーが、コマンドのいずれかをクリックするまで、パッケージ自体が読み込まれていないように VSPackage を設計するには遅延読み込みです。 .Vsct ファイルで、これを実現するには、コマンドのフラグが設定されていないコマンドを作成します。  
  
 .Vsct ファイルからメニュー コマンドの定義を次の例に示します。 これは、Visual Studio パッケージ テンプレートによって生成されるコマンドと、 **メニュー コマンド** テンプレートのオプションを選択します。  
  
 [!CODE [TopLevelMenu#03](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#03)]  
  
 例では場合、親グループ `MyMenuGroup`, などトップレベルのメニューの子では、 **ツール** \] メニューの \[は、コマンドは、そのメニューに表示されますが、コマンドを実行するパッケージは、コマンドが、ユーザーがクリックされるまで読み込まれません。 プログラミングを実装するコマンドを <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> インターフェイス、コマンドが含まれたメニューが最初に展開されているときに読み込まれるパッケージを有効にできます。  
  
 遅延読み込みが起動時のパフォーマンスを向上させることがも注目してください。  
  
## 現在のコンテキストとコマンドの表示\/非表示  
 VSPackage のコマンドを表示または非表示、VSPackage データまたは現在の関連性のあるアクションの現在の状態によってをプログラムすることができます。 VSPackage の実装を使用して、通常、コマンドの状態を設定することができます、 <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> メソッドから、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> が、これは、コードを実行するには読み込まれる VSPackage を必要とします。 代わりに、パッケージを読み込むことがなく、コマンドの表示状態を管理するための IDE を有効にすることをお勧めします。 .Vsct ファイルで、これには、コマンドを 1 つまたは複数の特別な UI コンテキストに関連付けます。 これらの UI コンテキストと呼ばれる GUID で識別される、 *コマンド コンテキスト GUID*します。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] プロジェクトの読み込みや編集を構築しようなどのユーザーの操作に起因する変更を監視します。 変更が発生した場合、IDE の外観が自動的に変更します。 次の表は、IDE の 4 つの主要なコンテキストを変更する [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] モニターします。  
  
|コンテキストの種類|説明|  
|---------------|--------|  
|アクティブなプロジェクトの種類|ほとんどのプロジェクト タイプでは、この `GUID` 値は、プロジェクトを実装する VSPackage の GUID と同じです。 ただし、 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] プロジェクト、プロジェクトの種類を使用して `GUID` 値として。|  
|アクティブなウィンドウ|通常、これは、ショートカット キーの現在の UI コンテキストを確立する最後の作業中のドキュメント ウィンドウです。 ただし、ツール ウィンドウを内部の Web ブラウザーのようなキーの組み合わせの一覧を持つ可能性があります。 HTML エディターなど、マルチタブのドキュメント ウィンドウをすべて\] タブが異なるコマンド コンテキスト `GUID`します。|  
|アクティブな言語サービス|テキスト エディターで現在表示されているファイルに関連付けられている言語サービスです。|  
|アクティブなツール ウィンドウ|開いているし、フォーカスのあるツール ウィンドウです。|  
  
 5 番目のコンテキストの主要な領域は、IDE の UI の状態です。 UI のコンテキストがアクティブなコマンドのコンテキストで識別される `GUID`秒で、次のようにします。  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionBuilding>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Debugging>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Dragging>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_FullScreenMode>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_DesignMode>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_NoSolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionExists>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_CodeWindow>  
  
 これらの Guid は、アクティブまたは IDE の現在の状態によって、非アクティブとしてマークされます。 複数の UI コンテキストは、同時にアクティブにできません。  
  
### コンテキストに基づいてコマンドの表示と非表示  
 表示したり、パッケージ自体を読み込むことがなく、IDE の package コマンドを非表示にすることができます。 これを行うを使用して、パッケージの .vsct ファイルで、コマンドを定義します。、 `DefaultDisabled`, 、`DefaultInvisible`, 、および `DynamicVisibility` フラグと追加する 1 つ以上のコマンド [VisibilityItem](../../extensibility/visibilityitem-element.md) 要素を、 [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) セクションです。 ときに指定されたコマンド コンテキスト `GUID` がアクティブで、コマンドが表示されます、パッケージを読み込むことがなく。  
  
### カスタム コンテキストの Guid  
 適切なコマンド コンテキストの GUID が定義されていない場合、VSPackage でいずれかを定義し、アクティブまたはコマンドの表示を制御する必要に応じて非アクティブにすることをプログラムできます。 使用して、 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> サービスに。  
  
-   コンテキストの Guid を登録する \(呼び出すことによって、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> メソッド\)。  
  
-   コンテキストの状態の取得 `GUID` \(を呼び出して、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> メソッド\)。  
  
-   コンテキストを有効にする `GUID`s オンとオフ \(を呼び出して、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> メソッド\)。  
  
    > [!CAUTION]
    >  VSPackage 影響を及ぼさないように既存のコンテキストの GUID の状態の他の vspackages にある場合がありますそれらに依存していることを確認します。  
  
## 例  
 VSPackage コマンドの次の例では、VSPackage を読み込むことがなく、コマンドのコンテキストで管理されているコマンドの動的な可視性を示します。  
  
 コマンドが有効にし、ソリューションが存在するときに表示するのに設定されています。つまり、次のコマンド コンテキストの Guid の 1 つはアクティブなときにします。  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>  
  
 この例では、確認するすべてのコマンド フラグが個別の [コマンド フラグ](../../extensibility/command-flag-element.md) 要素。  
  
 [!CODE [DynamicVisibility#01](DynamicVisibility#01)]  
  
 別個のすべての UI コンテキストを指定する必要があります通知も `VisibilityItem` 要素は、次のようにします。  
  
 [!CODE [DynamicVisibility#02](DynamicVisibility#02)]  
  
## 参照  
 [MenuCommand と  OleMenuCommand](../../misc/menucommands-vs-olemenucommands.md)   
 [Vspackage でのユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Vspackage でルーティング コマンド](../../extensibility/internals/command-routing-in-vspackages.md)   
 [メニュー項目を動的に追加します。](../../extensibility/dynamically-adding-menu-items.md)