---
title: 出力ウィンドウの拡張 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0608d8f6c4c9d9c0ae1454110e6db212f16bfe9b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49300548"
---
# <a name="extending-the-output-window"></a>出力ウィンドウの拡張
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**出力**ウィンドウはテキスト ペインの読み取り/書き込みのセットです。 Visual Studio がこれらの組み込みペイン:**ビルド**、プロジェクトのビルドに関するメッセージを通信および**全般**を[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]は IDE に関するメッセージを伝えます。 プロジェクトへの参照を取得する、**ビルド**ペインを使用して自動的に、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>インターフェイスのメソッド、および Visual Studio への直接アクセスを提供しています、**全般**ウィンドウを通じて、 <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> 。サービス。 だけでなく、組み込みのペインには、作成および独自のカスタム ペインを管理することができます。  
  
 制御することができます、**出力**ウィンドウ経由で直接、<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>インターフェイス。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>によって提供される、インターフェイス、<xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow>サービスを作成、取得、および破棄のメソッドを定義**出力**ウィンドウ ペインがあります。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>インターフェイス ウィンドウを表示、ウィンドウを非表示、およびそれぞれのテキストを操作するためのメソッドを定義します。 別の方法を制御する、**出力**ウィンドウは、<xref:EnvDTE.OutputWindow>と<xref:EnvDTE.OutputWindowPane>Visual Studio オートメーション オブジェクト モデル内のオブジェクト。 これらのオブジェクトをカプセル化の機能のほぼすべて、<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>インターフェイス。 さらに、<xref:EnvDTE.OutputWindow>と<xref:EnvDTE.OutputWindowPane>オブジェクトを列挙しやすく上位レベルの機能の追加、**出力**ウィンドウ ペインからテキストを取得するとします。  
  
## <a name="creating-an-extension-that-uses-the-output-pane"></a>[出力] ペインを使用する拡張機能の作成  
 [出力] ウィンドウのさまざまな側面を実行する拡張機能を行うことができます。  
  
1.  という名前の VSIX プロジェクトを作成する`TestOutput`メニュー コマンドを使用して名前付き**TestOutput**します。 詳細については、次を参照してください。[メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)です。  
  
2.  次の参照を追加します。  
  
    1.  EnvDTE  
  
    2.  EnvDTE80  
  
3.  TestOutput.cs で、次のコードを追加ステートメントを使用します。  
  
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
  
6.  以下のセクションでは、出力ウィンドウの処理のさまざまな方法を示すとおりの方法があります。 OutputCommandHandler() メソッドの本体にこれらのメソッドを呼び出すことができます。 たとえば、次のコードは、次のセクションで指定された CreatePane() メソッドを追加します。  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
        CreatePane(new Guid(), "Created Pane", true, false);  
    }  
    ```  
  
## <a name="creating-an-output-window-with-ivsoutputwindow"></a>IVsOutputWindow で出力ウィンドウを作成します。  
 この例は、新たに作成する方法を示しています。**出力**ウィンドウ ペインを使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>インターフェイス。  
  
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
  
 このメソッドをクリックすると、前のセクションで指定された拡張機能を追加する場合、**呼び出す TestOutput**コマンドが表示、**出力**というヘッダーを持つウィンドウ**の出力を表示: CreatedPane**と単語**は、作成ウィンドウ**ウィンドウ自体にします。  
  
## <a name="creating-an-output-window-with-outputwindow"></a>OutputWindow で出力ウィンドウを作成します。  
 この例は、作成する方法を示します、**出力**ウィンドウ ペインを使用して、<xref:EnvDTE.OutputWindow>オブジェクト。  
  
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
  
 ただし、<xref:EnvDTE.OutputWindowPanes>コレクションを取得できます。、**出力**をタイトルでウィンドウで、一意であるウィンドウのタイトルは保証されません。 タイトルの一意性を疑いを使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A>その GUID で適切なウィンドウを取得するメソッド。  
  
 このメソッドをクリックすると、前のセクションで指定された拡張機能を追加する場合、**呼び出す TestOutput**コマンドと書かれたヘッダーを出力ウィンドウを参照する必要があります**から出力の表示: DTEPane**と単語**DTE ウィンドウの追加**ウィンドウ自体にします。  
  
## <a name="deleting-an-output-window"></a>出力ウィンドウを削除します。  
 この例では、削除、**出力**ウィンドウ ペイン。  
  
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
  
 クリックすると、前のセクションで指定された拡張機能をこのメソッドを追加する場合、**呼び出す TestOutput**コマンドと書かれたヘッダーを出力ウィンドウを参照する必要があります**から出力の表示: 新しいウィンドウ**と単語**作成ウィンドウの追加**ウィンドウ自体にします。 クリックすると、**呼び出す TestOutput**コマンド、ウィンドウの削除をもう一度、します。  
  
## <a name="getting-the-general-pane-of-the-output-window"></a>出力ウィンドウの [全般] ペインを取得します。  
 この例は、組み込みを取得する方法を示します**全般**のウィンドウ、**出力**ウィンドウ。  
  
```csharp  
void GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 クリックすると、前のセクションで指定された拡張機能をこのメソッドを追加する場合、**呼び出す TestOutput**コマンドが表示される、**出力**ウィンドウには、単語が表示されます**全般が見つかりました。ウィンドウ**ウィンドウ。  
  
## <a name="getting-the-build-pane-of-the-output-window"></a>出力ウィンドウの [ビルド] ウィンドウを取得します。  
 この例では、ビルド ウィンドウの検索し、書き込みをする方法を示します。 ビルド ウィンドウが既定でアクティブになって、ため、アクティブ化しても。  
  
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

