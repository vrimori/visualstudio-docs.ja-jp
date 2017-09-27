---
title: "マルチ インスタンス ツール ウィンドウを作成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: bed04fe13e7232b2c227072ab91e6a56db0c6963
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="creating-a-multi-instance-tool-window"></a>マルチ インスタンス ツール ウィンドウを作成します。
複数のインスタンスを同時に開くできるように、ツール ウィンドウをプログラムできます。 既定では、ツール ウィンドウには 1 つインスタンスのみを開くことができます。  
  
 マルチ インスタンスのツール ウィンドウを使用する場合は、同時に情報のいくつかの関連するソースを表示できます。 たとえば、複数の行を配置する可能性があります<xref:System.Windows.Forms.TextBox>プログラミング セッション中にいくつかのコード スニペットが同時に使用できるように、複数インスタンスのツール ウィンドウで制御します。 たとえばもを置いたり、<xref:System.Windows.Forms.DataGrid>コントロールおよびドロップダウン リスト ボックスに、複数インスタンスのツール ウィンドウいくつかのリアルタイムのデータ ソースを同時に追跡できるようにします。  
  
## <a name="creating-a-basic-single-instance-tool-window"></a>Basic (単一インスタンス) のツール ウィンドウを作成します。  
  
1.  という名前のプロジェクトを作成する**MultiInstanceToolWindow** VSIX テンプレートを使用して、という名前のカスタム ツール ウィンドウの項目テンプレートの追加**MIToolWindow**です。  
  
    > [!NOTE]
    >  ツール ウィンドウで、拡張機能の作成の詳細については、次を参照してください。[ツール ウィンドウで、拡張機能の作成](../extensibility/creating-an-extension-with-a-tool-window.md)です。  
  
## <a name="making-a-tool-window-multi-instance"></a>ツール ウィンドウの複数インスタンスの作成  
  
1.  開く、 **MIToolWindowPackage.cs**ファイルを見つけて、`ProvideToolWindow`属性。 および`MultiInstances=true`パラメーターは、次の例で示すようにします。  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
        [ProvideMenuResource("Menus.ctmenu", 1)]  
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]  
        [Guid(MIToolWindowPackageGuids.PackageGuidString)]  
        public sealed class MIToolWindowPackage : Package  
    {. . .}  
    ```  
  
2.  MIToolWindowCommand.cs ファイルでは、ShowToolWindos() メソッドを見つけます。 このメソッドを呼び出して、<xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>メソッドとその`create`フラグを`false`まで、使用可能なツール ウィンドウの既存のインスタンスを反復処理はそのように`id`が見つかった。  
  
3.  ツール ウィンドウのインスタンスを作成するには、<xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>メソッドと set その`id`使用可能な値をその`create`フラグを`true`です。  
  
     既定では、値、`id`のパラメーター、<xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>メソッドは`0`します。 これにより、単一インスタンスのツール ウィンドウです。 複数のインスタンスをホストする、すべてのインスタンスがありますが独自の一意`id`です。  
  
4.  呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>メソッドを<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>によって返されるオブジェクト、<xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A>ツール ウィンドウのインスタンスのプロパティです。  
  
5.  既定では、`ShowToolWindow`ツール ウィンドウの項目テンプレートによって作成されるメソッドは、単一インスタンスのツール ウィンドウを作成します。 次の例を変更する方法を示しています、`ShowToolWindow`メソッドを複数のインスタンスを作成します。  
  
    ```csharp  
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
