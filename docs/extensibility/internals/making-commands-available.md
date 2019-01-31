---
title: コマンドを使用できるようにする |Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a14998b8dca3c14bdae4f00f1940c19b696646ff
ms.sourcegitcommit: a916ce1eec19d49f060146f7dd5b65f3925158dd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2019
ms.locfileid: "55231858"
---
# <a name="making-commands-available"></a>コマンドを使用できるようにします。

Visual Studio には、複数の Vspackage を追加するときにユーザー インターフェイス (UI) をコマンドで overcrowded になる可能性があります。 次のように、この問題を軽減するためにパッケージをプログラムすることができます。

- パッケージをプログラムするときにのみが読み込まれるように必要があります。

- 統合開発環境 (IDE) の現在の状態のコンテキストで、必要な場合にのみ、そのコマンドが表示されるように、パッケージをプログラムします。

## <a name="delayed-loading"></a>遅延読み込み

有効にするには、一般的な方法としては、UI では、そのコマンドが表示されますが、パッケージ自体では、ユーザーが、コマンドのいずれかをクリックするまでは読み込まれませんように VSPackage を設計するには遅延読み込み。 .Vsct ファイルで、これを実現するには、コマンドのフラグが設定されていないコマンドを作成します。

次の例では、.vsct ファイルからのメニュー コマンドの定義を示します。 これは、Visual Studio パッケージ テンプレートによって生成されるコマンドと、**メニュー コマンド**テンプレートのオプションを選択します。

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

例では場合、親グループ`MyMenuGroup`などトップレベルのメニューの子である、**ツール**メニューのコマンドは、そのメニューに表示されますが、コマンドを実行するパッケージは、コマンドがクリックされるまで読み込まれませんユーザー。 ただしを実装するためにコマンドをプログラミング、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイス、最初のコマンドを含むメニューが展開されている場合に読み込まれるパッケージ有効にすることができます。

遅延読み込みが起動時のパフォーマンスを向上させることがありますもことを確認します。

## <a name="current-context-and-the-visibility-of-commands"></a>現在のコンテキストとコマンドの可視性

VSPackage のコマンドを表示または非表示で、VSPackage のデータまたは現在に関連するアクションの現在の状態に応じてをプログラミングできます。 VSPackage の実装を使用して、通常、そのコマンドの状態を設定することができます、<xref:EnvDTE.IDTCommandTarget.QueryStatus%2A>からメソッド、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>が、このコードを実行するには読み込まれる VSPackage が必要です。 代わりに、パッケージを読み込むことがなく、コマンドの可視性を管理するための IDE を有効にすることをお勧めします。 .Vsct ファイルで、これには、特別な UI コンテキストが 1 つまたは複数のコマンドを関連付けます。 これらの UI コンテキストと呼ばれる GUID によって識別されます、*コマンド コンテキスト GUID*します。

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] プロジェクトの読み込みまたはビルドから編集しようとしてなどのユーザー アクションの結果として変更を監視します。 変更が発生すると、IDE の外観が自動的に変更します。 次の表は、IDE の 4 つの主要なコンテキストを変更する[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]モニター。

| コンテキストの種類 | 説明 |
|-------------------------| - |
| アクティブなプロジェクトの種類 | ほとんどの種類のプロジェクトのこの`GUID`値は、プロジェクトを実装する VSPackage の GUID と同じです。 ただし、[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]プロジェクト、プロジェクトの種類を使用して、`GUID`値として。 |
| アクティブなウィンドウ | 通常、これは、現在の UI コンテキスト キー バインドを確立する最後のアクティブなドキュメント ウィンドウです。 ただし、ツール ウィンドウを内部 Web ブラウザーのようなキー バインドのテーブルを持つ可能性があります。 HTML エディターなどの複数タブ付きドキュメント ウィンドウ、すべてのタブが別のコマンド コンテキスト`GUID`します。 |
| アクティブな言語サービス | テキスト エディターで現在表示されているファイルに関連付けられている言語サービス。 |
| アクティブなツール ウィンドウ | 開いていて、フォーカスのあるツール ウィンドウです。 |

5 番目のコンテキストの主要な領域は、IDE の UI 状態です。 UI コンテキストがアクティブなコマンドのコンテキストによって識別される`GUID`s は、次のようにします。

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Dragging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.FullScreenMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.DesignMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.NoSolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.CodeWindow_guid>

これらの Guid は、アクティブまたは IDE の現在の状態に応じて、非アクティブとしてマークされます。 同時にアクティブにできる複数の UI コンテキストです。

### <a name="hide-and-display-commands-based-on-context"></a>非表示にして、コンテキストに基づいてコマンドが表示されます。

表示したり、パッケージ自体を読み込むことがなく、IDE でパッケージのコマンドを非表示にすることができます。 これを行うを使用して、パッケージの .vsct ファイルで、コマンドを定義します、 `DefaultDisabled`、 `DefaultInvisible`、および`DynamicVisibility`フラグと追加する 1 つ以上のコマンド[VisibilityItem](../../extensibility/visibilityitem-element.md)要素を、 [ 。VisibilityConstraints](../../extensibility/visibilityconstraints-element.md)セクション。 ときに指定されたコマンド コンテキスト`GUID`がアクティブで、コマンドが表示されます、パッケージを読み込むことがなく。

### <a name="custom-context-guids"></a>カスタム コンテキストの Guid

適切なコマンドは、GUID が定義されていないコンテキスト場合、VSPackage のいずれかを定義し、アクティブまたはコマンドの表示を制御する必要に応じて非アクティブにすることをプログラムできます。 使用して、<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>サービス。

- コンテキストの Guid を登録する (呼び出すことによって、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A>メソッド)。

- コンテキストの状態を取得する`GUID`(呼び出すことによって、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>メソッド)。

- コンテキストを有効にする`GUID`s のオンとオフ (呼び出すことによって、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A>メソッド)。

    > [!CAUTION]
    > 確認して、VSPackage 影響を及ぼさないように既存のコンテキストの GUID の状態の他の Vspackage がそれらに依存している可能性があります。

## <a name="example"></a>例

VSPackage のコマンドの次の例では、VSPackage を読み込むことがなく、コマンドのコンテキストで管理されているコマンドの動的な可視性を示します。

コマンドが有効にし、ソリューションが存在するときに表示するのに設定されています。つまり、次のコマンド コンテキストの Guid のいずれかがアクティブなときに。

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

例では、すべてのコマンド フラグが個別に注意してください[コマンド フラグ](../../extensibility/command-flag-element.md)要素。

```xml
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

別のすべての UI コンテキストを指定する必要がありますに注意も`VisibilityItem`要素は、次のようにします。

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

## <a name="see-also"></a>関連項目

- [ソリューション エクスプ ローラーのツールバーにコマンドを追加します。](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [MenuCommand と OleMenuCommand](../../extensibility/menucommands-vs-olemenucommands.md)
- [VSPackage でユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Vspackage のコマンド ルーティング](../../extensibility/internals/command-routing-in-vspackages.md)
- [メニュー項目の動的な追加](../../extensibility/dynamically-adding-menu-items.md)
