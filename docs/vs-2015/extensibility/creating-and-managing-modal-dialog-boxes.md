---
title: 作成して、モーダル ダイアログ ボックスの管理 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b79ec93ae3783355d41d78a25dd5083dd5cd6361
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546689"
---
# <a name="creating-and-managing-modal-dialog-boxes"></a>モーダル ダイアログ ボックスの作成と管理
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[モーダル ダイアログ ボックスの管理の作成と](https://docs.microsoft.com/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes)します。  
  
Visual Studio 内でのモーダル ダイアログ ボックスを作成するときにダイアログ ボックスが表示されますが、ダイアログ ボックスの親ウィンドウが無効になっていることを確認し、ダイアログ ボックスが閉じられた後に、親ウィンドウを再度有効にする必要があります。 これを行わないと、エラーが表示される可能性があります:"Microsoft Visual Studio をシャット ダウンできないモーダル ダイアログがアクティブになっているためです。 アクティブなダイアログを閉じてもう一度やり直してください。"  
  
 これを行う 2 つの方法はあります。 推奨される方法、WPF ダイアログ ボックスがある場合から派生させます<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>を呼び出して<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A>ダイアログ ボックスを表示します。 これを行う場合は、親ウィンドウのモーダル状態を管理する必要はありません。  
  
 ダイアログ ボックスが、WPF ではない場合や、その他のダイアログ ボックスを派生できない理由クラス<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>、呼び出すことで、ダイアログ ボックスの親を取得する必要がありますし、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A>と呼び出すことによって、自分でモーダルの状態を管理、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A>メソッドをダイアログ ボックスを表示し、ダイアログ ボックスを閉じた後 1 (true) のパラメーターを使用してメソッドを呼び出す前に 0 (false) のパラメーター。  
  
## <a name="creating-a-dialog-box-derived-from-dialogwindow"></a>ダイアログ ウィンドウから派生したダイアログ ボックスの作成  
  
1.  という名前の VSIX プロジェクトを作成する**OpenDialogTest**という名前のメニュー コマンドを追加および**ダイアログ**します。 これを行う方法の詳細については、次を参照してください。[メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)です。  
  
2.  使用する、<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>クラスでは、次のアセンブリへの参照を追加する必要があります (の Framework タブで、**参照の追加** ダイアログ ボックス)。  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
    -   System.Xaml  
  
3.  OpenDialog.cs で、次のコードを追加`using`ステートメント。  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    ```  
  
4.  という名前のクラスを宣言**TestDialogWindow**から派生した<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>:  
  
    ```csharp  
    class TestDialogWindow : DialogWindow  
    {. . .}  
    ```  
  
5.  ダイアログ ボックスを最大化を最小限に抑え、次のように設定します。<xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A>と<xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A>を true にします。  
  
    ```csharp  
    internal TestDialogWindow()  
    {  
        this.HasMaximizeButton = true;  
        this.HasMinimizeButton = true;  
    }  
    ```  
  
6.  **OpenDialog.ShowMessageBox**メソッドを次の既存のコードに置き換えます。  
  
    ```csharp  
    TestDialogWindow testDialog = new TestDialogWindow();  
    testDialog.ShowModal();  
    ```  
  
7.  アプリケーションをビルドして実行します。 Visual Studio の実験用インスタンスが表示されます。 **ツール**実験用インスタンスのメニューという名前のコマンドを表示する必要があります**呼び出すダイアログ**します。 このコマンドをクリックすると、ダイアログ ウィンドウが表示されます。 最小化し、ウィンドウを最大化できる必要があります。  
  
## <a name="creating-and-managing-a-dialog-box-not-derived-from-dialogwindow"></a>作成と管理ダイアログ ウィンドウから派生していないダイアログ ボックス  
  
1.  この手順で使用することができます、 **OpenDialogTest**同じアセンブリの参照を前の手順で作成したソリューションです。  
  
2.  次の追加`using`宣言。  
  
    ```csharp  
    using System.Windows;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    ```  
  
3.  という名前のクラスを作成する**TestDialogWindow2**から派生した<xref:System.Windows.Window>:  
  
    ```csharp  
    class TestDialogWindow2 : Window  
    {. . .}  
    ```  
  
4.  プライベートの参照を追加<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```  
    private IVsUIShell shell;  
    ```  
  
5.  参照に設定するコンス トラクターを追加<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```csharp  
    public TestDialogWindow2(IVsUIShell uiShell)  
    {  
        shell = uiShell;  
    }  
    ```  
  
6.  **OpenDialog.ShowMessageBox**メソッドを次の既存のコードに置き換えます。  
  
    ```csharp  
    IVsUIShell uiShell = (IVsUIShell)ServiceProvider.GetService(typeof(SVsUIShell));  
  
    TestDialogWindow2 testDialog2 = new TestDialogWindow2(uiShell);  
    //get the owner of this dialog  
    IntPtr hwnd;  
    uiShell.GetDialogOwnerHwnd(out hwnd);  
    testDialog2.WindowStartupLocation = System.Windows.WindowStartupLocation.CenterOwner;  
    uiShell.EnableModeless(0);  
    try  
    {  
        WindowHelper.ShowModal(testDialog2, hwnd);  
    }  
    finally  
    {  
        // This will take place after the window is closed.  
        uiShell.EnableModeless(1);  
    }  
    ```  
  
7.  アプリケーションをビルドして実行します。 **ツール**メニューという名前のコマンドを表示する必要があります**呼び出すダイアログ**します。 このコマンドをクリックすると、ダイアログ ウィンドウが表示されます。

