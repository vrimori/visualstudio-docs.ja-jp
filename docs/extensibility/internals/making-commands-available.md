---
title: "コマンドを使用できるようにする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
caps.latest.revision: "35"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0c3a9edc754070c7bb0aabdc76b2d52efd32a453
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="making-commands-available"></a>コマンドを使用できるようにします。
複数 VSPackages を Visual Studio に追加するとき、ユーザー インターフェイス (UI) は、コマンドで overcrowded になる可能性があります。 次のように、この問題を軽減するためにパッケージをプログラムすることができます。  
  
-   パッケージのプログラム ユーザー場合にのみ読み込まれるように必要があります。  
  
-   統合開発環境 (IDE) の現在の状態のコンテキストで、必要な場合がある場合のみ、そのコマンドが表示されるように、パッケージをプログラムできます。  
  
## <a name="delayed-loading"></a>遅延読み込み  
 有効にする一般的な方法は、UI では、そのコマンドが表示されますが、ユーザーが、コマンドのいずれかをクリックするまで、パッケージ自体が読み込まれていませんように、VSPackage を設計するには遅延読み込みです。 これを実現するには、.vsct ファイルでは、コマンド フラグがないコマンドを作成します。  
  
 次の例は、.vsct ファイルからのメニュー コマンドの定義を示しています。 これは、Visual Studio パッケージ テンプレートによって生成されるコマンドと、**メニュー コマンド**テンプレートのオプションを選択します。  
  
```xml  
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <Strings>  
    <CommandName>cmdidTestCommand</CommandName>  
    <ButtonText>Test Command</ButtonText>  
  </Strings>  
</Button>  
  
```  
  
 例では場合、親グループ`MyMenuGroup`、トップレベルのメニューの子であるなど、**ツール**メニューのコマンドは、そのメニューに表示されますが、コマンドがクリックされるまで、コマンドを実行するパッケージを読み込むことができませんがユーザーです。 ただしでプログラミングを実装するコマンド、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイス、コマンドが含まれたメニューが最初に展開されているときに読み込まれるパッケージを有効にできます。  
  
 遅延読み込みが起動時のパフォーマンスを向上させることがありますも注目してください。  
  
## <a name="current-context-and-the-visibility-of-commands"></a>現在のコンテキストとコマンドの可視性  
 VSPackage のコマンドを表示または非表示、VSPackage のデータまたは現在関連性のあるアクションの現在の状態に応じてをプログラムすることができます。 VSPackage の実装を使用して、通常、そのコマンドの状態を設定することができます、<xref:EnvDTE.IDTCommandTarget.QueryStatus%2A>メソッドから、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>が、これは、コードを実行する前に読み込まれる VSPackage が必要です。 代わりに、パッケージを読み込むことがなく、コマンドの可視性を管理するための IDE を有効にすることをお勧めします。 これを行う、.vsct ファイルで、コマンドを 1 つまたは複数の特別な UI コンテキストに関連付けます。 これらの UI コンテキストと呼ばれる GUID で識別される、*コマンド コンテキスト GUID*です。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクトの読み込みまたは編集から構築などのユーザー アクションに起因する変更を監視します。 変更が発生した場合、IDE の外観が自動的に変更します。 次の表は、IDE の 4 つの主要なコンテキストを変更する[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]モニターします。  
  
|コンテキストの種類|説明|  
|---------------------|-----------------|  
|アクティブなプロジェクトの種類|ほとんどのプロジェクト タイプでは、この`GUID`値は、プロジェクトを実装する VSPackage の GUID と同じにします。 ただし、[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]プロジェクト、プロジェクトの種類を使用して`GUID`値として。|  
|アクティブなウィンドウ|通常、これは、キー バインドの現在の UI コンテキストを確立する最後の作業中のドキュメント ウィンドウです。 ただし、内部の Web ブラウザーのようなキーの組み合わせのテーブルのあるツール ウィンドウがあってもかまいません。 HTML エディターなど、マルチタブのドキュメント ウィンドウ、すべてのタブが別のコマンド コンテキスト`GUID`です。|  
|アクティブな言語サービス|テキスト エディターで現在表示されているファイルに関連付けられている言語サービスです。|  
|アクティブなツール ウィンドウ|ツール ウィンドウが開いていて、フォーカスがあります。|  
  
 5 番目のメジャーのコンテキスト領域は、IDE の UI 状態です。 UI コンテキストがアクティブなコマンドのコンテキストで識別される`GUID`s、次のようにします。  
  
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
  
 これらの Guid は、アクティブまたは IDE の現在の状態に応じて、非アクティブとしてマークされます。 複数の UI コンテキストは、同時にアクティブにできます。  
  
### <a name="hiding-and-displaying-commands-based-on-context"></a>非表示にして、コンテキストに基づいてコマンドを表示します。  
 表示したり、パッケージ自体を読み込むことがなく、IDE でパッケージのコマンドを非表示にすることができます。 これを行うを使用して、パッケージの .vsct ファイルで、コマンドを定義します、 `DefaultDisabled`、 `DefaultInvisible`、および`DynamicVisibility`フラグと追加する 1 つ以上のコマンド[VisibilityItem](../../extensibility/visibilityitem-element.md)要素を、 [ 。VisibilityConstraints](../../extensibility/visibilityconstraints-element.md)セクションです。 ときに指定されたコマンド コンテキスト`GUID`がアクティブで、コマンドが表示されます、パッケージを読み込むことがなくです。  
  
### <a name="custom-context-guids"></a>カスタムのコンテキストの Guid  
 適切なコマンドは、GUID が定義されていないコンテキスト場合、VSPackage のいずれかを定義し、アクティブまたは、コマンドの可視性を制御するために必要と非アクティブにすることをプログラムできます。 使用して、<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>サービスを。  
  
-   コンテキストの Guid を登録する (呼び出すことによって、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A>メソッド)。  
  
-   コンテキストの状態の取得`GUID`(を呼び出して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>メソッド)。  
  
-   コンテキストを有効にする`GUID`s オンとオフ (を呼び出して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A>メソッド)。  
  
    > [!CAUTION]
    >  VSPackage 影響を及ぼさないように既存のコンテキストの GUID の状態に依存するその他の Vspackage のため確認してください。  
  
## <a name="example"></a>例  
 VSPackage のコマンドの次の例では、VSPackage を読み込むことがなくコマンドのコンテキストで管理されているコマンドの動的な可視性を示します。  
  
 コマンドが有効にし、ソリューションが存在するときに表示するのに設定されています。つまり、次のコマンド コンテキストの Guid のいずれかがアクティブなときに。  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>  
  
 例では、すべてのコマンド フラグが個別であることを確認します[コマンド フラグ](../../extensibility/command-flag-element.md)要素。  
  
```  
<Button guid="guidDynamicVisibilityCmdSet" id="cmdidMyCommand"   
        priority="0x0100" type="Button">  
  <Parent guid="guidDynamicVisibilityCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <CommandFlag>DefaultDisabled</CommandFlag>  
  <CommandFlag>DefaultInvisible</CommandFlag>  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <CommandName>cmdidMyCommand</CommandName>  
    <ButtonText>My Command name</ButtonText>  
  </Strings>  
</Button>  
  
```  
  
 別のすべての UI コンテキストを指定する必要があります通知も`VisibilityItem`要素は、次のようにします。  
  
```xml  
<VisibilityConstraints>  
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"  
                  id="cmdidMyCommand" context="UICONTEXT_EmptySolution" />  
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"  
                      id="cmdidMyCommand" context="UICONTEXT_SolutionHasSingleProject" />  
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"  
                  id="cmdidMyCommand" context="UICONTEXT_SolutionHasMultipleProjects" />  
</VisibilityConstraints>  
  
```  
  
## <a name="see-also"></a>参照  
 [MenuCommand と OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [Vspackage がユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Vspackage でルーティング コマンド](../../extensibility/internals/command-routing-in-vspackages.md)   
 [メニュー項目の動的な追加](../../extensibility/dynamically-adding-menu-items.md)