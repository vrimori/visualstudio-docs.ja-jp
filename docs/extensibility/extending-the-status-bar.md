---
title: "ステータス バーの拡張 | Microsoft Docs"
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
  - "ステータス バー、ステータス バーの概要"
  - "ステータス バー, 概要"
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
---
# ステータス バーの拡張
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

IDE の下部にある Visual Studio のステータス バーを使用して、情報を表示することができます。  
  
 情報と UI を表示 4 つの領域で、ステータス バーを拡張するときに: フィードバック領域、進行状況バー、アニメーションの領域、およびデザイナーの領域です。 フィードバックの領域を使用すると、テキストを表示し、表示されるテキストを強調表示できます。 進行状況バーは、ファイルの保存などの実行時間が短い操作の進行状況の増分を示しています。 アニメーションの領域には、実行時間の長い操作またはソリューション内の複数のプロジェクトの構築など、何らかの長さの操作のための継続的にループのアニメーションが表示されます。 デザイナーの領域は、カーソル位置の行と列の数を示します。  
  
 ステータス バーを使用して取得できます、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> インターフェイス \(から、 <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> サービス\)。 ウィンドウ フレーム上にある任意のオブジェクトを実装することで、ステータス バーのクライアント オブジェクトとして登録できますさらに、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> インターフェイスです。 Visual Studio がそのウィンドウの上にあるオブジェクトをクエリ ウィンドウがアクティブになるたびに、 `IVsStatusbarUser` インターフェイスです。 見つかった呼び出します、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> 、返されたインターフェイスとオブジェクトのメソッドは、そのメソッド内でのステータス バーを更新できます。 たとえば windows を文書化を使用して、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> 、アクティブになったときに、デザイナーの領域内の情報を更新するメソッドです。  
  
 次の手順では、VSIX プロジェクトを作成し、カスタム メニュー コマンドを追加する方法を理解することを前提としています。 詳細については、「[メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)」を参照してください。  
  
## ステータス バーを変更します。  
 この手順では、設定、テキストを取得し、静的テキストを表示、およびステータス バーのフィードバックの領域に表示されるテキストを強調表示する方法を示します。  
  
#### 読み取りと書き込み、ステータス バー  
  
1.  という名前の VSIX プロジェクトを作成する **TestStatusBarExtension** という名前のメニュー コマンドを追加および **TestStatusBarCommand**します。  
  
2.  TestStatusBarCommand.cs では、次のようにコマンドのハンドラー メソッド コード \(MenuItemCallback\) を置き換えます。  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
  
        // Make sure the status bar is not frozen  
        int frozen;  
  
        statusBar.IsFrozen(out frozen);  
  
        if (frozen != 0)   
        {  
            statusBar.FreezeOutput(0);  
        }  
  
        // Set the status bar text and make its display static.  
        statusBar.SetText("We just wrote to the status bar.");  
  
        // Freeze the status bar.  
        statusBar.FreezeOutput(1);  
  
        // Get the status bar text.   
        string text;  
        statusBar.GetText(out text);  
        System.Windows.Forms.MessageBox.Show(text);  
  
        // Clear the status bar text.  
        statusBar.FreezeOutput(0);  
        statusBar.Clear();  
    }  
    ```  
  
3.  コードをコンパイルし、デバッグを開始します。  
  
4.  開いている、 **ツール** Visual Studio の実験用インスタンスのメニュー。 クリックして、 **呼び出す TestStatusBarCommand** \] ボタンをクリックします。  
  
     表示されるステータス バーの現在の読み取りでテキスト **「記述したばかりのステータス バーに」** 表示されるメッセージ ボックスのテキストと同じ。  
  
#### 進行状況バーを更新  
  
1.  ここでは、初期化し、進行状況バーを更新する方法を説明します。  
  
2.  TestStatusBarCommand.cs ファイルを開き、MenuItemCallback メソッドを次のコードに置き換えます。  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
        uint cookie = 0;  
        string label = "Writing to the progress bar";  
  
        // Initialize the progress bar.  
        statusBar.Progress(ref cookie, 1, "", 0, 0);  
  
        for (uint i = 0, total = 20; i <= total; i++)  
        {  
            // Display progress every second.  
            statusBar.Progress(ref cookie, 1, label, i, total);  
            System.Threading.Thread.Sleep(1000);  
        }  
  
        // Clear the progress bar.  
        statusBar.Progress(ref cookie, 0, "", 0, 0);  
    }  
    ```  
  
3.  コードをコンパイルし、デバッグを開始します。  
  
4.  開いている、 **ツール** Visual Studio の実験用インスタンスのメニュー。 クリックして **呼び出す TestStatusBarCommand** \] ボタンをクリックします。  
  
     表示されるステータス バーの現在の読み取りでテキスト **「進行状況バーへの書き込み」**毎秒 20 秒間の更新の進行状況バーも表示されます。 その後に、ステータス バーと進行状況バーが消去されます。  
  
#### アニメーションを表示します。  
  
1.  ステータス バーには、いずれかを示すループ アニメーション \(たとえば、複数のプロジェクト、ソリューションのビルド\) の実行時間の長い操作が表示されます。 このアニメーションが表示されない場合が正しいことを確認する **ツール\/オプション** 設定。  
  
     移動して、 **ツール\/オプション\/全般** \] タブでオフにし、 **クライアントのパフォーマンスに基づいて視覚的効果を自動的に調整**します。 サブ オプションをオンにし、 **リッチ クライアントの視覚的効果を有効にする**します。 Visual Studio の実験用インスタンスで、プロジェクトをビルドするときにアニメーションを表示できるようになりましたにします。  
  
     この手順では、プロジェクトまたはソリューションの構築を表す標準の Visual Studio アニメーションを表示します。  
  
2.  TestStatusBarCommand.cs ファイルを開き、MenuItemCallback メソッドを次のコードに置き換えます。  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar =(IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
  
        // Use the standard Visual Studio icon for building.  
        object icon = (short)Microsoft.VisualStudio.Shell.Interop.Constants.SBAI_Build;  
  
        // Display the icon in the Animation region.  
        statusBar.Animation(1, ref icon);  
  
        // The message box pauses execution for you to look at the animation.  
        System.Windows.Forms.MessageBox.Show("showing?");  
  
        // Stop the animation.   
        statusBar.Animation(0, ref icon);  
    }  
    ```  
  
3.  コードをコンパイルし、デバッグを開始します。  
  
4.  開いている、 **ツール** \] メニューの \[Visual Studio の実験用インスタンスで **呼び出す TestStatusBarCommand**します。  
  
     メッセージ ボックスが表示されたら、右端でのステータス バーにアニメーションも表示されます。 メッセージ ボックスを閉じると、アニメーション表示されなくなります。