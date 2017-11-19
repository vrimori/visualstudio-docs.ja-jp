---
title: "出力ウィンドウを拡張 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8e183413446bbca2ffed0642619ab63538fae0f3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="extending-the-output-window"></a>出力ウィンドウを拡張します。
**出力**ウィンドウは、読み取り/書き込みテキスト ペインのセット。 Visual Studio はこれらの組み込みペイン:**ビルド**、プロジェクトのビルドに関するメッセージを通信し、**全般**を[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]IDE に関するメッセージを伝えます。 プロジェクトへの参照を取得する、**ビルド**ペインを使用して自動的に、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>インターフェイスのメソッド、および Visual Studio に直接アクセスするには、**全般**でウィンドウを<xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane>サービス。 組み込みのペインでは、だけでなくを作成して管理する独自のカスタム ペインです。  
  
 制御することができます、**出力**ウィンドウ経由で直接、<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>インターフェイスです。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>によって提供されるインターフェイス、<xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow>サービスを作成、取得、および破棄するためのメソッドを定義**出力**ウィンドウです。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>インターフェイス ウィンドウを表示、ペイン、非表示にする、およびそれぞれのテキストを操作するためのメソッドを定義します。 別の方法を制御する、**出力**ウィンドウは、<xref:EnvDTE.OutputWindow>と<xref:EnvDTE.OutputWindowPane>Visual Studio オートメーション オブジェクト モデル内のオブジェクト。 これらのオブジェクトをカプセル化の機能のほぼすべて、<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>インターフェイスです。 さらに、<xref:EnvDTE.OutputWindow>と<xref:EnvDTE.OutputWindowPane>オブジェクトを列挙しやすく上位レベルの機能の追加、**出力**ウィンドウのウィンドウからテキストを取得するとします。  
  
## <a name="creating-an-extension-that-uses-the-output-pane"></a>[出力] ペインを使用する拡張機能の作成  
 [出力] ペインのさまざまな側面を実行する拡張を行うことができます。  
  
1.  という名前の VSIX プロジェクトを作成する`TestOutput`メニュー コマンドを使用して名前付き**TestOutput**です。 詳細については、次を参照してください。[メニュー コマンドを使用して、拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)です。  
  
2.  次の参照を追加します。  
  
    1.  EnvDTE  
  
    2.  EnvDTE80  
  
3.  次のコードを追加、TestOutput.cs でステートメントを使用します。  
  
    ```f#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  TestOutput.cs、ShowMessageBox メソッドを削除します。 次のメソッド スタブを追加します。  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
5.  TestOutput コンス トラクターでは、OutputCommandHandler にコマンド ハンドラーを変更します。 コマンドを追加する部分を次に示します。  
  
    ```csharp  
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    if (commandService != null)  
    {  
        CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
        EventHandler eventHandler = OutputCommandHandler;  
        MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
        commandService.AddCommand(menuItem);  
    }  
    ```  
  
6.  以下のセクションでは、出力ウィンドウを処理する場合のさまざまな方法を示す別の方法があります。 OutputCommandHandler() メソッドの本体にこれらのメソッドを呼び出すことができます。 たとえば、次のコードは、次のセクションで指定された CreatePane() メソッドを追加します。  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
        CreatePane(new Guid(), "Created Pane", true, false);  
    }  
    ```  
  
## <a name="creating-an-output-window-with-ivsoutputwindow"></a>IVsOutputWindow を出力ウィンドウを作成します。  
 この例は、新しいを作成する方法を示しています。**出力**ウィンドウ ペインを使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>インターフェイスです。  
  
```csharp  
void CreatePane(Guid paneGuid, string title,   
    bool visible, bool clearWithSolution)  
{  
    IVsOutputWindow output =   
        (IVsOutputWindow)GetService(typeof(SVsOutputWindow));  
    IVsOutputWindowPane pane;  
  
    // Create a new pane.  
    output.CreatePane(  
        ref paneGuid,   
        title,   
        Convert.ToInt32(visible),   
        Convert.ToInt32(clearWithSolution));  
  
    // Retrieve the new pane.  
    output.GetPane(ref paneGuid, out pane);  
  
     pane.OutputString("This is the Created Pane \n");  
}  
```  
  
 このメソッドをクリックすると、前のセクションで指定された拡張機能に追加する場合、**呼び出す TestOutput**コマンドが表示されます、**出力**と表示されているヘッダーを持つウィンドウ**の出力を表示: CreatedPane**と単語**は、作成ウィンドウ**ウィンドウ自体にします。  
  
## <a name="creating-an-output-window-with-outputwindow"></a>「出力」ウィンドウと出力ウィンドウを作成します。  
 この例を作成する方法を示しています、**出力**ウィンドウ ペインを使用して、<xref:EnvDTE.OutputWindow>オブジェクト。  
  
```csharp  
void CreatePane(string title)  
{  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
  
    try  
    {  
        // If the pane exists already, write to it.  
        panes.Item(title);  
    }  
    catch (ArgumentException)  
    {  
        // Create a new pane and write to it.  
        return panes.Add(title);  
    }  
}  
```  
  
 ただし、<xref:EnvDTE.OutputWindowPanes>コレクションを取得できます、**出力**ウィンドウ ペインのタイトルをウィンドウ タイトルは一意であることは保証はありません。 タイトルの一意性を疑いを使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A>をその GUID で正しいウィンドウを取得するメソッド。  
  
 このメソッドをクリックすると、前のセクションで指定された拡張機能に追加する場合、**呼び出す TestOutput**コマンドと表示されているヘッダーを出力ウィンドウを参照する必要があります**から出力を表示: DTEPane**と単語**DTE ウィンドウの追加**ウィンドウ自体にします。  
  
## <a name="deleting-an-output-window"></a>出力ウィンドウを削除します。  
 この例では、削除、**出力**ウィンドウ ペインです。  
  
```csharp  
void DeletePane(Guid paneGuid)  
{  
    IVsOutputWindow output =  
    (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow));  
  
    IVsOutputWindowPane pane;  
    output.GetPane(ref paneGuid, out pane);  
  
    if (pane == null)  
    {  
        CreatePane(paneGuid, "New Pane\n", true, true);  
    }  
     else  
    {  
        output.DeletePane(ref paneGuid);  
    }  
}  
```  
  
 このメソッドをクリックすると、前のセクションで指定された拡張機能に追加する場合、**呼び出す TestOutput**コマンドと表示されているヘッダーを出力ウィンドウを参照する必要があります**から出力を表示: 新しいウィンドウ**と単語**作成ウィンドウの追加**ウィンドウ自体にします。 クリックした場合、**呼び出す TestOutput**ウィンドウが削除をもう一度、コマンドします。  
  
## <a name="getting-the-general-pane-of-the-output-window"></a>出力ウィンドウの [全般] ペインの取得  
 この例は、組み込みを取得する方法を示します**全般**のペイン、**出力**ウィンドウです。  
  
```csharp  
void GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 クリックすると、前のセクションで指定された拡張機能にこのメソッドを追加する場合、**呼び出す TestOutput**コマンドが表示されます、**出力**ウィンドウは、単語を示しています**全般が見つかりました。ウィンドウ**ウィンドウで、します。  
  
## <a name="getting-the-build-pane-of-the-output-window"></a>出力ウィンドウの [ビルド] ウィンドウを取得します。  
 この例では、ビルドのウィンドウを検索し、書き込みにする方法を示します。 ビルド ウィンドウは、既定でアクティブ化されていない、ため、アクティブ化してもします。  
  
```csharp  
void OutputTaskItemStringExExample(string buildMessage)  
{  
    EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE));  
  
    EnvDTE.OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
    foreach (EnvDTE.OutputWindowPane pane in panes)  
        {  
            if (pane.Name.Contains("Build"))  
            {  
                pane.OutputString(buildMessage + "\n");  
                pane.Activate();  
                return;  
             }  
        }  
}  
```