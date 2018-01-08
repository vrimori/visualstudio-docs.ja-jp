---
title: "ステータス バーを拡張 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: cb8ea7f78b964ee828993c09e59af5b5e83fd031
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-status-bar"></a>ステータス バーの拡張
IDE の下部にある、Visual Studio のステータス バーを使用して、情報を表示することができます。  
  
 情報と UI を表示 4 つの領域で拡張すると、ステータス バー、: フィードバック領域、進行状況バー、アニメーションの領域、およびデザイナーの領域。 フィードバック領域を使用すると、テキストを表示し、表示されるテキストを強調表示できます。 進行状況バーには、ファイルの保存などの実行時間が短い操作の進行状況の増分が示されます。 アニメーションの領域には、実行時間の長い操作またはソリューション内の複数のプロジェクトを構築するなど、何らかの長さの操作の継続的にループのアニメーションが表示されます。 デザイナーの領域は、カーソル位置の行と列数を示します。  
  
 使用して、ステータス バーを取得することができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar>インターフェイス (から、<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>サービス)。 ウィンドウ フレーム上にある任意のオブジェクトを実装することで、ステータス バーのクライアント オブジェクトとして登録できますさらに、<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>インターフェイスです。 Visual Studio がそのウィンドウの上にあるオブジェクトをクエリ ウィンドウがアクティブにするたびに、`IVsStatusbarUser`インターフェイスです。 かどうかを呼び出して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>返されたインターフェイスとオブジェクトのメソッドは、そのメソッド内から、ステータス バーを更新できます。 ドキュメント ウィンドウ、たとえば、使用できる、<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>アクティブになったときに、デザイナーの領域内の情報を更新する方法です。  
  
 次の手順では、VSIX プロジェクトを作成し、カスタムのメニュー コマンドを追加する方法を理解するいると仮定します。 詳細については、次を参照してください。[メニュー コマンドを使用して、拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)です。  
  
## <a name="modifying-the-status-bar"></a>ステータス バーを変更します。  
 この手順では、設定、テキストを取得し、静的テキストを表示、およびステータス バーのフィードバック領域に表示されるテキストを強調表示する方法を示します。  
  
#### <a name="reading-and-writing-to-the-status-bar"></a>読み取りと書き込み、ステータス バー  
  
1.  という名前の VSIX プロジェクトを作成する**TestStatusBarExtension**という名前のメニュー コマンドを追加および**TestStatusBarCommand**です。  
  
2.  TestStatusBarCommand.cs では、次のようにコマンド ハンドラー メソッドのコード (MenuItemCallback) を置き換えます。  
  
    ```csharp  
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
  
4.  開く、**ツール**Visual Studio の実験用インスタンスのメニュー。 クリックして、**呼び出す TestStatusBarCommand**ボタンをクリックします。  
  
     表示する必要があります、ステータス バーの現在の読み取りでテキスト**「おだけに書き込みましたステータス バー」。** 表示されるメッセージ ボックスには、同じテキスト。  
  
#### <a name="updating-the-progress-bar"></a>進行状況バーを更新  
  
1.  この手順で初期化し、進行状況バーを更新する方法を示します。  
  
2.  TestStatusBarCommand.cs ファイルを開き、MenuItemCallback メソッドを次のコードに置き換えます。  
  
    ```csharp  
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
  
4.  開く、**ツール**Visual Studio の実験用インスタンスのメニュー。 をクリックして**呼び出す TestStatusBarCommand**ボタンをクリックします。  
  
     表示する必要があります、ステータス バーの現在の読み取りでテキスト**「進行状況バーを書き込んでいます」。** 毎秒 20 秒の更新の進行状況バーを表示する必要があります。 その後に、ステータス バーおよび進行状況バーをクリアします。  
  
#### <a name="displaying-an-animation"></a>アニメーションを表示します。  
  
1.  ステータス バーには、いずれかを示すアニメーションをループ (たとえば、ソリューション内の複数のプロジェクトのビルド) の実行時間の長い操作が表示されます。 このアニメーションが表示されない場合、正しいして確認**ツール/オプション**設定。  
  
     移動して、**ツール/オプション/[全般]**タブおよびボックスをオフに**クライアントのパフォーマンスに基づいて視覚的効果を自動的に調整**です。 サブ オプションをオンにし、**リッチ クライアントの視覚的効果を有効にする**です。 今すぐできる Visual Studio の実験用インスタンスで、プロジェクトをビルドするときに、アニメーションを参照してください。  
  
     この手順では、プロジェクトまたはソリューションのビルドを表す標準の Visual Studio アニメーションを表示します。  
  
2.  TestStatusBarCommand.cs ファイルを開き、MenuItemCallback メソッドを次のコードに置き換えます。  
  
    ```csharp  
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
  
4.  開く、**ツール**メニューをクリックして、Visual Studio の実験用インスタンスで**呼び出す TestStatusBarCommand**です。  
  
     メッセージ ボックスが表示される場合は、右端で、ステータス バーでアニメーションも表示されます。 メッセージ ボックスを閉じるアニメーション表示されなくなります。