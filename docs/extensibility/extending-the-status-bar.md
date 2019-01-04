---
title: ステータス バーの拡張 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eed1810f91358e514d2cd8085d73c030f81085b3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53962902"
---
# <a name="extend-the-status-bar"></a>ステータス バーを拡張します。
IDE の下部にある Visual Studio のステータス バーを使用して、情報を表示することができます。  
  
 情報と UI を表示 4 つのリージョンで、ステータス バーを拡張するとき: フィードバック領域、進行状況バー、アニメーションの領域、およびデザイナー領域。 フィードバック領域のテキストを表示し、表示されるテキストを強調表示することができます。 進行状況バーには、ファイルの保存などの操作を短時間での増分の進行状況が表示されます。 アニメーションの領域には、実行時間の長い操作または複数のプロジェクトのソリューションの構築など、未確定の長さの操作のための継続的にループのアニメーションが表示されます。 デザイナーの領域には、カーソル位置の行と列数が表示されます。  
  
 ステータス バーを使用して取得できます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar>インターフェイス (から、<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>サービス)。 ウィンドウ フレーム上にある任意のオブジェクトを実装することで、ステータス バーのクライアント オブジェクトとして登録できますさらに、<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>インターフェイス。 Visual Studio がそのウィンドウの上にあるオブジェクトをクエリ ウィンドウがアクティブになるたびに、`IVsStatusbarUser`インターフェイス。 かどうか、呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>返されたインターフェイスとオブジェクトのメソッドは、そのメソッド内でのステータス バーを更新できます。 たとえば、windows のドキュメント、使用できる、<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>アクティブになったときに、デザイナーの領域内の情報を更新するメソッド。  
  
 次の手順では、VSIX プロジェクトを作成し、カスタム メニュー コマンドを追加する方法を理解することを前提としています。 詳しくは、次を参照してください。[メニュー コマンドを使用して拡張機能を作成する](../extensibility/creating-an-extension-with-a-menu-command.md)します。  
  
## <a name="modify-the-status-bar"></a>ステータス バーを変更します。  
 この手順では、設定、テキストを取得し、静的テキストを表示、およびステータス バーのフィードバック領域に表示されるテキストを強調表示する方法を示します。  
  
### <a name="read-and-write-to-the-status-bar"></a>読み取りし、書き込みをステータス バー  
  
1.  という名前の VSIX プロジェクトを作成する**TestStatusBarExtension**という名前のメニュー コマンドを追加および**TestStatusBarCommand**します。  
  
2.  *TestStatusBarCommand.cs*、コマンド ハンドラー メソッドのコードに置き換えます (`MenuItemCallback`) に次の。  
  
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
  
4.  開く、**ツール**Visual Studio の実験用インスタンスでのメニュー。 をクリックして、**呼び出す TestStatusBarCommand**ボタンをクリックします。  
  
     表示されるステータス バーの現在の読み取りでテキスト**ステータス バーに閉じずします。** メッセージ ボックスが表示されるが、同じテキスト。  
  
### <a name="update-the-progress-bar"></a>進行状況バーを更新します。  
  
1.  この手順では、初期化、および進行状況バーを更新する方法を紹介します。  
  
2.  開く、 *TestStatusBarCommand.cs*ファイルを開き、`MenuItemCallback`メソッドを次のコード。  
  
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
  
4.  開く、**ツール**Visual Studio の実験用インスタンスでのメニュー。 クリックして**呼び出す TestStatusBarCommand**ボタンをクリックします。  
  
     表示されるステータス バーの現在の読み取りでテキスト**進行状況バーへの書き込み。** 毎秒 20 秒の更新の進行状況バーも表示されます。 その後、ステータス バーと、進行状況バーはクリアされます。  
  
### <a name="display-an-animation"></a>アニメーションを表示します。  
  
1.  ステータス バーには、いずれかを示すアニメーションをループ (たとえば、ソリューション内の複数のプロジェクトの構築) の実行時間の長い操作が表示されます。 このアニメーションが表示されない場合がある、正しい確認**ツール** > **オプション**設定。  
  
     移動して、**ツール** > **オプション** > **全般** タブでオフにし、**クライアントに基づいて視覚的効果を自動的に調整パフォーマンス**します。 サブ オプションを確認し、**リッチ クライアントの視覚的効果を有効にする**します。 今すぐできる Visual Studio の実験用インスタンスでプロジェクトをビルドするときに、アニメーションを参照してください。  
  
     この手順では、プロジェクトまたはソリューションの構築を表す標準の Visual Studio のアニメーションを表示します。  
  
2.  開く、 *TestStatusBarCommand.cs*ファイルを開き、`MenuItemCallback`メソッドを次のコード。  
  
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
  
4.  開く、**ツール** メニューのをクリックし、Visual Studio の実験用インスタンスで**呼び出す TestStatusBarCommand**します。  
  
     メッセージ ボックスが表示されたら、右端にステータス バーのアニメーションも表示されます。 メッセージ ボックスを消去するときに、アニメーションは表示されなくなります。