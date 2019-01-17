---
title: MenuCommand とOleMenuCommands |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, creating in VSPackages
- command buttons, creating and placing
- menus, creating commands
ms.assetid: 553d5e07-3e19-4aba-b490-6c7dd05fd82e
manager: douge
ms.openlocfilehash: 3b33d84f62db9cfe1371ffc540830f63d93e67d1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926240"
---
# <a name="menucommands-vs-olemenucommands"></a>MenuCommand とOleMenuCommand
メニュー コマンドを作成するにはいずれかから派生することによって<xref:System.ComponentModel.Design.MenuCommand>またはから<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>オブジェクト、および適切なイベント ハンドラーを実装します。 ほとんどのケースでは、VSPackage プロジェクト テンプレートの場合と同様に <xref:System.ComponentModel.Design.MenuCommand>を使用できますが、 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>を使用することが必要になることもあります。  
  
 VSPackage によって IDE で使用可能になるコマンドをユーザーが使用するには、そのコマンドを表示し、有効にする必要があります。 コマンドを作成するときに、 *.vsct*ファイルが、Visual Studio パッケージ プロジェクト テンプレートを使用すると、種類表示され、既定で有効になっています。 一部のコマンド フラグ ( `DynamicItemStart`など) を設定すると、この既定の動作を変更できます。 コマンドの可視性や有効な状態などのプロパティは、コマンドに関連付けられている <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> オブジェクトにアクセスすることによって、コードで実行時に変更することもできます。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)します。  
  
## <a name="template-locations-for-the-visual-studio-package-template"></a>Visual Studio パッケージ テンプレートのテンプレートの保存場所  
 Visual Studio パッケージ テンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual Basic** > **拡張** >  **C#** > **拡張**、または**他のプロジェクト タイプ** > **拡張**します。  
  
## <a name="create-a-command"></a>コマンドを作成します。  
 すべてのコマンド、コマンド グループ、メニューのツールバー、およびツール ウィンドウがで定義されている、 *.vsct*ファイル。 詳細については、次を参照してください。 [Visual Studio コマンド テーブル (.vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)します。  
  
 パッケージ テンプレートを使用して VSPackage を作成する場合は、選択**メニュー コマンド**を作成する、 *.vsct*ファイルし、既定のメニュー コマンドを定義します。 詳細については、次を参照してください。[メニュー コマンドを使用して拡張機能を作成する](../extensibility/creating-an-extension-with-a-menu-command.md)します。  
  
### <a name="to-add-a-command-to-the-ide"></a>IDE にコマンドを追加するには  
  
1. 開く、 *.vsct*ファイル。  
  
2. `Symbols` セクションで、グループおよびコマンドが含まれている [GuidSymbol](../extensibility/guidsymbol-element.md) 要素を探します。  
  
3. 次の例に示すように、追加するメニュー、グループ、またはコマンドごとに [IDSymbol](../extensibility/idsymbol-element.md) 要素を作成します。  
  
    <!--FIXME [!CODE [ButtonGroup#01](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#01)]  -->
   ```xaml  
   <GuidSymbol name="guidButtonGroupCmdSet" value="{f69209e9-975a-4543-821d-1f4a2c52d737}">
     <IDSymbol name="MyMenuGroup" value="0x1020" />
     <IDSymbol name="cmdidMyCommand" value="0x0100" />
   </GuidSymbol>
   ```  
  
   `name` 要素と `GuidSymbol` 要素の `IDSymbol` 属性は、新規のメニュー、グループ、またはコマンドごとに GUID:ID のペアを提供します。 `guid` は、VSPackage に対して定義されているコマンド セットを表します。 複数のコマンド セットを定義できます。 GUID:ID の各ペアは、一意である必要があります。  
  
4. [[ボタン]](../extensibility/buttons-element.md) セクションで、次の例に示すように、コマンドを定義する [Button](../extensibility/button-element.md) 要素を作成します。  
  
    <!--FIXME [!CODE [ButtonGroup#03](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#03)]  -->
   ```xaml  
   <Button guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
     <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
       <CommandName>cmdidMyCommand</CommandName>
       <ButtonText>My Command name</ButtonText>
     </Strings>
   </Button>
   ```  
  
   1.  新しいコマンドの GUID:ID が一致するように `guid` フィールドと `id` フィールドを設定します。  
  
   2.  `priority` 属性を設定します。  
  
        `priority` 属性は、ボタンの場所を親グループ内の他のオブジェクトの中から特定するために .vsct で使用されます。  
  
        優先順位値が低いコマンドは、優先順位値の高いコマンドの上または左に表示されます。 優先順位値の重複は許容されますが、優先順位が同じコマンドの相対的な位置は実行時に処理される VSPackage の順序によって決まり、その順序を事前に設定することはできません。  
  
        `priority` 属性を省略すると、その値は 0 に設定されます。  
  
   3.  `type` 属性を設定します。 ほとんどの場合、その値は `"Button"`になります。 その他の有効なボタンの種類の説明については、次を参照してください。[ボタン要素](../extensibility/button-element.md)します。  
  
5. ボタンの定義には、 [Strings](../extensibility/strings-element.md) 要素を作成します。この要素には、IDE に表示されるメニューの名前を格納する [ButtonText](../extensibility/buttontext-element.md) 要素と、 [[コマンド]](../extensibility/commandname-element.md) ウィンドウのメニューにアクセスするときに使用されるコマンドの名前を格納する **CommandName** 要素を含めます。  
  
    ボタンのテキスト文字列には、'&' 文字が含まれている場合、ユーザーがキーを押して、メニューを開くことができます**Alt**直後に続く文字は、さらに、'&'。  
  
    `Tooltip` 要素を追加すると、ユーザーがボタンの上にポインターを置いたときに、その要素に含まれているテキストが表示されるようになります。  
  
6. [Icon](../extensibility/icon-element.md) 要素を追加してアイコンを指定した場合は、コマンドと共にそのアイコンも表示されます。 アイコンは、ツール バーのボタンには必要ですが、メニュー項目には必要ありません。 `guid` 要素の `id` と `Icon` は、 [セクションに定義されている](../extensibility/bitmap-element.md) Bitmap `Bitmaps` 要素のものと一致する必要があります。  
  
7. ボタンの外観と動作を変更するには、必要に応じて、コマンド フラグを追加します。 これを行うには、メニュー定義に [CommandFlag](../extensibility/command-flag-element.md) 要素を追加します。  
  
8. コマンドの親グループを設定します。 親グループは、自分で作成するグループ、別のパッケージからのグループ、IDE からのグループのいずれかになります。 たとえば、Visual Studio の編集ツール バーの **[コメント]** ボタンと **[コメントの削除]** ボタンの横にコマンドを追加するには、親を guidStdEditor:IDG_VS_EDITTOOLBAR_COMMENT に設定します。 親がユーザー定義グループである場合、親は IDE に表示されるメニュー、ツール バー、または ツール ウィンドウの子である必要があります。  
  
    これは、設計に応じて次の 2 つの方法のいずれかで行うことができます。  
  
   - `Button` 要素に、 [Parent](../extensibility/parent-element.md) 要素を作成し、その要素の `guid` フィールドと `id` フィールドにコマンドをホストするグループ ( *プライマリ親グループ*とも呼ばれます) の Guid と ID を設定します。  
  
      次の例では、ユーザー定義メニューに表示されるコマンドを定義しています。  
  
      <!--FIXME [!CODE [TopLevelMenu#03](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#03)]  -->
     ```xaml  
     <Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
       <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
       <Icon guid="guidImages" id="bmpPic1" />
       <Strings>
         <CommandName>cmdidTestCommand</CommandName>
         <ButtonText>Test Command</ButtonText>
       </Strings>
     </Button>
     ```  
  
   - コマンド配置を使用してコマンドを配置する場合には、 `Parent` 要素を省略することもできます。 次の例に示すように、 [セクションの前に](../extensibility/commandplacements-element.md) CommandPlacements `Symbols` 要素を作成し、コマンドの [と](../extensibility/commandplacement-element.md) を持つ `guid` CommandPlacement `id` 要素、 `priority`、および親を追加します。  
  
      <!-- FIXME [!CODE [ButtonGroup#04](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#04)] -->  
     ```xaml  
     <CommandPlacements>
       <CommandPlacement guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x105">
         <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
       </CommandPlacement>
     </CommandPlacements>
     ```  
  
      GUID:ID が同じで親が異なるコマンド配置を複数作成すると、メニューが複数の場所に表示されます。 詳細については、「 [CommandPlacements](../extensibility/commandplacements-element.md) 要素」を参照してください。  
  
     コマンド グループおよびペアレンティングの詳細については、次を参照してください。[ボタンの再利用可能なグループ作成](../extensibility/creating-reusable-groups-of-buttons.md)です。  
  
   この時点で、コマンドは IDE に表示されますが、機能はありません。 パッケージ テンプレートによってコマンドを作成した場合、既定ではメッセージを表示するクリック ハンドラーがコマンドに設定されます。  
  
## <a name="handle-the-new-command"></a>新しいコマンドを処理します。  
 マネージド コードのほとんどのコマンドは、コマンドを <xref:System.ComponentModel.Design.MenuCommand> オブジェクトまたは <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> オブジェクトに関連付け、そのイベント ハンドラーを実装することで、管理パッケージ フレームワーク (MPF) で処理できます。  
  
 コマンド処理のために直接 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> インターフェイスを使用するコードの場合、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> インターフェイスとそのメソッドを実装する必要があります。 2 つの最も重要なメソッドが <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> と <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>です。  
  
1.  次の例に示すように、 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> インスタンスを取得します。  
  
     [!code-csharp[ButtonGroup#21](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_5.cs)]  
  
2.  次の例に示すように、処理するコマンドの GUID と ID をパラメーターとして持つ <xref:System.ComponentModel.Design.CommandID> オブジェクトを作成します。  
  
     [!code-csharp[ButtonGroup#22](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_6.cs)]  
  
     Visual Studio パッケージ テンプレートには、コマンドの GUID と ID を保持するために `GuidList` と `PkgCmdIDList` という 2 つのコレクションが用意されています。 これらは、テンプレートで追加するコマンドに対して自動的に設定されます。手動で追加するコマンドについては、 `PkgCmdIdList` クラスに ID エントリを追加する必要があります。  
  
     また、GUID の生の文字列値と ID の整数値を使用して、 <xref:System.ComponentModel.Design.CommandID> オブジェクトを設定することもできます。  
  
3.  次の例に示すように、 <xref:System.ComponentModel.Design.MenuCommand> と共にコマンドを処理するメソッドを指定する <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> オブジェクトまたは <xref:System.ComponentModel.Design.CommandID>オブジェクトをインスタンス化します。  
  
     [!code-csharp[ButtonGroup#23](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_7.cs)]  
  
     <xref:System.ComponentModel.Design.MenuCommand> は、静的コマンドに適しています。 動的メニュー項目を表示するには、QueryStatus イベント ハンドラーが必要です。 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> は、 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> イベント (コマンドのホスト メニューを開くと発生します) と、その他のプロパティ ( <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>など) を追加します。  
  
     パッケージ テンプレートで作成したコマンドは、既定ではパッケージ クラスの `Initialize()` メソッドの <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> オブジェクトに渡されます。  
  
4.  <xref:System.ComponentModel.Design.MenuCommand> は、静的コマンドに適しています。 動的メニュー項目を表示するには、QueryStatus イベント ハンドラーが必要です。 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> は、 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> イベント (コマンドのホスト メニューを開くと発生します) と、その他のプロパティ ( <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>など) を追加します。  
  
     パッケージ テンプレートで作成したコマンドは、既定ではパッケージ クラスの <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> メソッドの `Initialize()` オブジェクトに渡されます。 Visual Studio ウィザードは、 `Initialize` を使用して `MenuCommand`メソッドを実装します。 動的メニュー項目を表示するには、次の手順に示すように、これを `OleMenuCommand`に変更する必要があります。 さらに、メニュー項目のテキストを変更するには、次の例に示すように、.vsct ファイルでメニュー コマンド ボタンに TextChanges コマンド フラグを追加する必要があります。  
  
     <!--FIXME [!CODE [MenuText#02](../CodeSnippet/VS_Snippets_VSSDK/menutext#02)]-->  
    ```xaml  
    <Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
      <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
      <Icon guid="guidImages" id="bmpPic1" />
      <CommandFlag>TextChanges</CommandFlag>
      <Strings>
        <CommandName>cmdidMyCommand</CommandName>
        <ButtonText>My Command name</ButtonText>
      </Strings>
    </Button>
    ```
  
5.  この新しいメニュー コマンドを <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> インターフェイスの <xref:System.ComponentModel.Design.IMenuCommandService> メソッドに渡します。 これは、次の例に示すように、既定ではパッケージ テンプレートで作成したコマンドに対して行われます。  
  
     [!code-csharp[ButtonGroup#24](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_9.cs)]  
  
6.  コマンドを処理するメソッドを実装します。  
  
### <a name="to-implement-querystatus"></a>QueryStatus を実装するには  
  
1. コマンドが表示される前に、QueryStatus イベントが発生します。 これにより、コマンドがユーザーに到達する前に、そのコマンドのプロパティをイベント ハンドラーに設定できます。 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> オブジェクトとして追加したコマンドのみが、このメソッドにアクセスできます。  
  
    次の例に示すように、コマンドを処理するために作成する `EventHandler` オブジェクト内の <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> イベントに <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> オブジェクトを追加します (`menuItem` は <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> インスタンスです)。  
  
    [!code-csharp[MenuText#14](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_10.cs)]
    [!code-vb[MenuText#14](../extensibility/codesnippet/VisualBasic/menucommands-vs-olemenucommands_10.vb)]  
  
    `EventHandler` オブジェクトには、メニュー コマンドの状態を照会するときに呼び出すメソッドの名前を付けます。  
  
2. コマンドの状態照会ハンドラー メソッドを実装します。  `object` `sender` パラメーターは、 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> オブジェクトにキャストできます。これは、テキストなどメニュー コマンドのさまざまな属性を設定するために使用します。 次の表に、 <xref:System.ComponentModel.Design.MenuCommand> フラグに対応する <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> クラス (MPF クラス <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> の派生元) のプロパティを示します。  
  
   |MenuCommand プロパティ|OLECMDF フラグ|  
   |--------------------------|------------------|  
   |<xref:System.ComponentModel.Design.MenuCommand.Checked%2A> = `true`|OLECMDF_LATCHED|  
   |<xref:System.ComponentModel.Design.MenuCommand.Visible%2A> = `false`|OLECMDF_INVISIBLE|  
   |<xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> = `true`|OLECMDF_ENABLED|  
  
    メニュー コマンドのテキストを変更するには、次の例に示すように、 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A> オブジェクトの <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> プロパティを使用します。  
  
    [!code-csharp[MenuText#11](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_11.cs)]
    [!code-vb[MenuText#11](../extensibility/codesnippet/VisualBasic/menucommands-vs-olemenucommands_11.vb)]  
  
   MPF は、グループがサポートされていないか不明な場合、自動的に処理します。 コマンドは、 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> メソッドを使用して <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> に追加しない限り、サポートされません。  
  
### <a name="handle-commands-by-using-the-iolecommandtarget-interface"></a>IOleCommandTarget インターフェイスを使用してハンドル コマンド  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> インターフェイスを直接使用するコードの場合、VSPackage は <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> インターフェイスの <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> メソッドと <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> メソッドの両方を実装する必要があります。 VSPackage がプロジェクト階層を実装する場合は、代わりに <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> インターフェイスの <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> メソッドと <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> メソッドを実装する必要があります。  
  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> メソッドと <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> メソッドの両方が、入力として 1 つのコマンド セット `GUID` とコマンド ID の配列とを受け取るように設計されています。 1 回の呼び出しで複数の ID というこの概念を VSPackage で完全にサポートすることをお勧めします。 ただし、VSPackage を他の VSPackage から呼び出さない限り、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> メソッドと <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> メソッドは適切に定義された順序で実行されるため、コマンド配列には 1 つのコマンド ID のみが含まれていると見なすことができます。 ルーティングの詳細については、次を参照してください。 [Vspackage でのコマンド ルーティング](../extensibility/internals/command-routing-in-vspackages.md)します。  
  
 コマンド処理のために直接 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> インターフェイスを使用するコードの場合、コマンドを処理するには、次のように VSPackage に <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> メソッドを実装する必要があります。  
  
#### <a name="to-implement-the-querystatus-method"></a>QueryStatus メソッドを実装するには  
  
1. 有効なコマンドの <xref:Microsoft.VisualStudio.VSConstants.S_OK> を返します。  
  
2. `prgCmds` パラメーターの `cmdf` 要素を設定します。  
  
    `cmdf` 要素の値は、論理 OR ( <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> ) 演算子を使用して結合された、`|`列挙型からの値の論理的な和集合です。  
  
    コマンドの状態に基づいて、適切な列挙型を使用します。  
  
   - コマンドがサポートされていない場合:  
  
      `prgCmds[0].cmdf = OLECMDF_SUPPORTED;`  
  
   - 現時点ではコマンドが表示されないようにする必要がある場合:  
  
      `prgCmds[0].cmdf |= OLECMDF_INVISIBLE;`  
  
   - コマンドがトグルされ、クリックされたように見える場合:  
  
      `prgCmds[0].cmdf |= OLECMDF_LATCHED;`  
  
      型 `MenuControllerLatched`のメニューにホストされているコマンドを処理する場合、 `OLECMDF_LATCHED` フラグでマークされている最初のコマンドが、起動時にメニューに表示される既定のコマンドです。 詳細については`MenuController`種類のメニューを参照してください[メニュー要素](../extensibility/menu-element.md)します。  
  
   - コマンドが現在有効になっている場合:  
  
      `prgCmds[0].cmdf |= OLECMDF_ENABLED;`  
  
   - コマンドがショートカット メニューの一部で、既定では非表示になっている場合:  
  
      `prgCmds[0] cmdf |= OLECMDF_DEFHIDEONCTXTMENU`  
  
   - コマンドが `TEXTCHANGES` フラグを使用している場合は、`pCmdText` パラメーターの `rgwz` 要素をコマンドの新しいテキストに設定し、`pCmdText` パラメーターの `cwActual` 要素をコマンド文字列のサイズに設定します。  
  
     エラー条件の場合、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> メソッドで次のエラー ケースを処理する必要があります。  
  
   - GUID が不明であるかサポートされていない場合は、 `OLECMDERR_E_UNKNOWNGROUP`を返します。  
  
   - GUID は既知であるものの、コマンド ID が不明であるかサポートされていない場合は、 `OLECMDERR_E_NOTSUPPORTED`を返します。  
  
   <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> メソッドの VSPackage 実装では、コマンドがサポートされているかどうかと、コマンドが正常に処理されたかどうかに応じて、特定のエラー コードを返す必要もあります。  
  
#### <a name="to-implement-the-exec-method"></a>Exec メソッドを実装するには  
  
-   コマンド `GUID` が不明である場合は、 `OLECMDERR_E_UNKNOWNGROUP`を返します。  
  
-   `GUID` は既知であるものの、コマンド ID が不明である場合は、 `OLECMDERR_E_NOTSUPPORTED`を返します。  
  
-   場合、`GUID`とコマンド ID で、コマンドによって使用される GUID:ID のペアの一致、 *.vsct*ファイル、およびコマンドの戻り値に関連付けられているコードが実行<xref:Microsoft.VisualStudio.VSConstants.S_OK>します。  
  
## <a name="see-also"></a>関連項目  
 [VSCT XML スキーマ リファレンス](../extensibility/vsct-xml-schema-reference.md)   
 [メニューとコマンドを拡張します。](../extensibility/extending-menus-and-commands.md)