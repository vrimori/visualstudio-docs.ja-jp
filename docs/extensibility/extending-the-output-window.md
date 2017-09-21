---
title: "[出力] ウィンドウを拡張します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[出力] ウィンドウの [出力] ウィンドウ"
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# [出力] ウィンドウを拡張します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**出力** ウィンドウは、読み取り\/書き込みテキスト ペインのセットです。 Visual Studio はこれらの組み込みペイン: **ビルド**, 、プロジェクトのビルドについてのメッセージの通信と **全般**, を [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE に関するメッセージを伝えます。 プロジェクトへの参照を取得する、 **ビルド** ウィンドウを使用して自動的に、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> インターフェイスのメソッド、および Visual Studio への直接アクセスを提供しています。、 **全般** を通じてペイン、 <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> サービスです。 組み込みのペインだけでなくは作成して、独自のカスタム ペインを管理します。  
  
 制御することができます、 **出力** ウィンドウ経由で直接、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> インターフェイスです。<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> によって提供されるインターフェイス、 <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> サービスを作成、取得、および破棄するためのメソッドを定義 **出力** ウィンドウ ペイン。<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> インターフェイスがペインに表示、ウィンドウを非表示、およびそれぞれのテキストを操作するためのメソッドを定義します。 別の方法を制御する、 **出力** ウィンドウは、 <xref:EnvDTE.OutputWindow> と <xref:EnvDTE.OutputWindowPane> Visual Studio オートメーション オブジェクト モデル内のオブジェクト。 これらのオブジェクトをカプセル化の機能のほぼすべて、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> インターフェイスです。 さらに、 <xref:EnvDTE.OutputWindow> と <xref:EnvDTE.OutputWindowPane> オブジェクトを列挙するが容易に高度なレベルの機能の追加、 **出力** ウィンドウ ペインと\] ペインからテキストを取得します。  
  
## \[出力\] ペインを使用する拡張機能の作成  
 \[出力\] ペインのさまざまな側面を実行する拡張機能を行うことができます。  
  
1.  という名前の VSIX プロジェクトを作成する `TestOutput` メニュー コマンドを使用して名前付き **TestOutput**します。 詳細については、「[メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)」を参照してください。  
  
2.  次の参照を追加します。  
  
    1.  EnvDTE  
  
    2.  EnvDTE80  
  
3.  TestOutput.cs で次のコードを追加ステートメントを使用します。  
  
    ```f#  
    using EnvDTE; using EnvDTE80;  
    ```  
  
4.  TestOutput.cs、ShowMessageBox メソッドを削除します。 次のメソッド スタブを追加します。  
  
    ```c#  
    private void OutputCommandHandler(object sender, EventArgs e) { }  
    ```  
  
5.  TestOutput コンス トラクターでは、OutputCommandHandler するコマンド ハンドラーを変更します。 コマンドが追加されている部分を次に示します。  
  
    ```c#  
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService; if (commandService != null) { CommandID menuCommandID = new CommandID(MenuGroup, CommandId); EventHandler eventHandler = OutputCommandHandler; MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID); commandService.AddCommand(menuItem); }  
    ```  
  
6.  以下のセクションでは、\[出力\] ペインの処理のさまざまな方法を示す別の方法があります。 OutputCommandHandler\(\) メソッドの本体にこれらのメソッドを呼び出すことができます。 たとえば、次のコードは、次のセクションで指定された CreatePane\(\) メソッドを追加します。  
  
    ```c#  
    private void OutputCommandHandler(object sender, EventArgs e) { CreatePane(new Guid(), "Created Pane", true, false); }  
    ```  
  
## IVsOutputWindow と出力ウィンドウを作成します。  
 この例は、新しいを作成する方法を示しています。 **出力** ウィンドウ ペインを使用して、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> インターフェイスです。  
  
```c#  
void CreatePane(Guid paneGuid, string title, bool visible, bool clearWithSolution) { IVsOutputWindow output = (IVsOutputWindow)GetService(typeof(SVsOutputWindow)); IVsOutputWindowPane pane; // Create a new pane. output.CreatePane( ref paneGuid, title, Convert.ToInt32(visible), Convert.ToInt32(clearWithSolution)); // Retrieve the new pane. output.GetPane(ref paneGuid, out pane); pane.OutputString("This is the Created Pane \n"); }  
```  
  
 クリックすると、前のセクションで割り当てられた内線番号をこのメソッドを追加する場合、 **呼び出す TestOutput** コマンドが表示されます、 **出力** というヘッダーを持つウィンドウ **から出力を表示: CreatedPane** と、単語 **は、作成ウィンドウ** ウィンドウ自体にします。  
  
## OutputWindow と出力ウィンドウを作成します。  
 この例を作成する方法を示しています、 **出力** ウィンドウ ペインを使用して、 <xref:EnvDTE.OutputWindow> オブジェクトです。  
  
```c#  
void CreatePane(string title) { DTE2 dte = (DTE2)GetService(typeof(DTE)); OutputWindowPanes panes = dte.ToolWindows.OutputWindow.OutputWindowPanes; try { // If the pane exists already, write to it. panes.Item(title); } catch (ArgumentException) { // Create a new pane and write to it. return panes.Add(title); } }  
```  
  
 ですが、 <xref:EnvDTE.OutputWindowPanes> コレクションを取得できます、 **出力** ウィンドウで、タイトルが、一意であるウィンドウのタイトルは保証されません。 タイトルに一意かどうかを疑問とを使用して、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> をその GUID で、正しい \[ウィンドウを取得します。  
  
 クリックすると、前のセクションで割り当てられた内線番号をこのメソッドを追加する場合、 **呼び出す TestOutput** コマンドというヘッダーを出力ウィンドウを確認する必要があります **から出力を表示: DTEPane** と、単語 **DTE ウィンドウの追加** ウィンドウ自体にします。  
  
## 出力ウィンドウを削除します。  
 この例では、削除、 **出力** ウィンドウ ペイン。  
  
```c#  
void DeletePane(Guid paneGuid) { IVsOutputWindow output = (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow)); IVsOutputWindowPane pane; output.GetPane(ref paneGuid, out pane); if (pane == null) { CreatePane(paneGuid, "New Pane\n", true, true); } else { output.DeletePane(ref paneGuid); } }  
```  
  
 クリックすると、前のセクションで割り当てられた内線番号をこのメソッドを追加する場合、 **呼び出す TestOutput** コマンドというヘッダーを出力ウィンドウを確認する必要があります **から出力を表示: 新しいウィンドウ** と、単語 **作成ウィンドウの追加** ウィンドウ内で。 クリックすると、 **呼び出す TestOutput** 、ウィンドウが削除されたコマンドを再、します。  
  
## \[出力\] ウィンドウの \[全般\] ペインを取得します。  
 この例は、組み込みを取得する方法を示します **全般** のウィンドウ、 **出力** ウィンドウです。  
  
```c#  
void GetGeneralPane() { return (IVsOutputWindowPane)GetService( typeof(SVsGeneralOutputWindowPane)); }  
```  
  
 クリックすると、前のセクションで割り当てられた内線番号をこのメソッドを追加する場合、 **呼び出す TestOutput** コマンドが表示される、 **出力** ウィンドウは、単語を示します **検出の \[全般\] ペイン** ウィンドウでします。  
  
## \[出力\] ウィンドウの \[ビルド\] ウィンドウを取得します。  
 この例では、検索のビルド領域と書き込みをする方法を示します。 ビルド ウィンドウは、既定でアクティブ化されていないからアクティブにしてもなります。  
  
```c#  
void OutputTaskItemStringExExample(string buildMessage) { EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE)); EnvDTE.OutputWindowPanes panes = dte.ToolWindows.OutputWindow.OutputWindowPanes; foreach (EnvDTE.OutputWindowPane pane in panes) { if (pane.Name.Contains("Build")) { pane.OutputString(buildMessage + "\n"); pane.Activate(); return; } } }  
```