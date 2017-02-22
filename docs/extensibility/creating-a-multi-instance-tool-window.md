---
title: "複数インスタンスのツール ウィンドウを作成します。 | Microsoft Docs"
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
  - "マルチ"
  - "ツール ウィンドウ"
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 複数インスタンスのツール ウィンドウを作成します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

複数のインスタンスが同時に開くできるように、ツール ウィンドウをプログラミングできます。 既定では、ツール ウィンドウ インスタンスが 1 つだけを開くことができます。  
  
 複数インスタンスのツール ウィンドウを使用する場合は、同時に情報のいくつかの関連するソースを表示できます。 たとえば、複数行に配置する <xref:System.Windows.Forms.TextBox> プログラミング セッション中にいくつかのコード スニペットが同時に使用できるように、複数インスタンスのツール ウィンドウで制御します。 たとえばも置いたり、 <xref:System.Windows.Forms.DataGrid> コントロールとドロップダウン リスト ボックスに複数インスタンスのツール ウィンドウいくつかのリアルタイムのデータ ソースを同時に追跡できるようにします。  
  
## Basic \(単独\) のツール ウィンドウを作成します。  
  
1.  という名前のプロジェクトを作成する **MultiInstanceToolWindow** VSIX のテンプレートを使用し、という名前のカスタム ツール ウィンドウの項目テンプレートを追加 **MIToolWindow**します。  
  
    > [!NOTE]
    >  ツール ウィンドウで拡張機能の作成の詳細については、次を参照してください。 [ツール ウィンドウで、拡張機能を作成します。](../extensibility/creating-an-extension-with-a-tool-window.md)します。  
  
## ツール ウィンドウのマルチ インスタンスの作成  
  
1.  開いている、 **MIToolWindowPackage.cs** ファイルを見つけて、 `ProvideToolWindow` 属性です。 および `MultiInstances=true` パラメーターは、次の例で示すようにします。  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
        [ProvideMenuResource("Menus.ctmenu", 1)]  
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]  
        [Guid(MIToolWindowPackageGuids.PackageGuidString)]  
        public sealed class MIToolWindowPackage : Package  
    {. . .}  
    ```  
  
2.  MIToolWindowCommand.cs ファイルでは、ShowToolWindos\(\) メソッドを見つけます。 このメソッドを呼び出して、 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> メソッドとその `create` フラグを `false` には、使用可能なまでツール ウィンドウの既存のインスタンスを反復処理できるように `id` が見つかった。  
  
3.  ツール ウィンドウのインスタンスを作成するには、 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> メソッドとその `id` 使用可能な値をその `create` フラグを `true`します。  
  
     既定では、値、 `id` のパラメーター、 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> メソッドは `0`です。 これにより、単一インスタンスのツール ウィンドウです。 複数のインスタンスをホストする、すべてのインスタンスがありますが独自の一意 `id`します。  
  
4.  呼び出す、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> メソッドを <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> によって返されるオブジェクト、 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> ツール ウィンドウのインスタンスのプロパティです。  
  
5.  既定では、 `ShowToolWindow` ツール ウィンドウの項目テンプレートによって作成されるメソッドは、単一インスタンスのツール ウィンドウを作成します。 次の例を変更する方法を示しています、 `ShowToolWindow` メソッドを複数のインスタンスを作成します。  
  
    ```c#  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        for (int i = 0; i < 10; i++)  
        {  
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);  
            if (window == null)  
            {  
                // Create the window with the first free ID.   
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);  
                if ((null == window) || (null == window.Frame))  
                {  
                    throw new NotSupportedException("Cannot create tool window");  
                }  
  
            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
            break;  
            }  
        }  
    }  
    ```