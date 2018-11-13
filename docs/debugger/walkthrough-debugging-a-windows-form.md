---
title: 'チュートリアル: Windows フォームのデバッグ |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- debugging managed code, Windows Forms
- debugging [Visual Studio], Windows Forms
- Attach to Process dialog box
- debugger, attaching to programs
- Attach to Process dialog box, walkthroughs
- Windows Forms, debugging
- debugging Windows Forms, walkthroughs
ms.assetid: 529db1e2-d9ea-482a-b6a0-7c543d17f114
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dd847a4db232d32c941722d5ee537a21bdaf33a8
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349167"
---
# <a name="walkthrough-debugging-a-windows-form"></a>チュートリアル : Windows フォームのデバッグ
Windows フォームは、最も一般的なマネージド アプリケーションの 1 つです。 Windows フォームは、標準 Windows アプリケーションを作成します。 このチュートリアルは、Visual Basic、C#、または C++ を使用して実行できます。  
  
 開いているソリューションがある場合は、ソリューションを閉じる必要があります。  
  
### <a name="to-prepare-for-this-walkthrough"></a>このチュートリアルの準備をするには  
  
-   既に開いているソリューションがある場合は、そのソリューションを閉じます。 (上、**ファイル**メニューの **ソリューションを閉じる**)。  
  
## <a name="create-a-new-windows-form"></a>新しい Windows フォームを作成する  
 次に、新しい Windows フォームを作成します。  
  
#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>このチュートリアルの Windows フォームを作成するには  
  
1.  **ファイル**] メニューの [選択**新規**クリック**プロジェクト**。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  プロジェクトの種類 ウィンドウで開く、 **Visual Basic**、 **Visual c#**、または**Visual C**しノード  
  
    1.  Visual Basic または Visual c#、次のように選択します。 **Windows デスクトップ** > **Windows フォーム アプリ**します。  
  
    2.  Visual c は、次のように選択します。 **Windows デスクトップ アプリケーション**します。  
  
3.  **名前**ボックスで、プロジェクトの一意の名前 (Walkthrough_SimpleDebug など) を付けます。  
  
4.  **[OK]** をクリックします。  
  
     新しいプロジェクトが作成され、Windows フォーム デザイナーに新しいフォームが表示されます。 詳細については、次を参照してください。 [Windows フォーム デザイナー](/previous-versions/visualstudio/visual-studio-2010/e06hs424\(v\=vs.100\))します。  
  
5.  **ビュー**メニューの **ツールボックス**します。  
  
     ツールボックスが表示されます。 詳細については、「[ツールボックス](../ide/reference/toolbox.md)」をご覧ください。  
  
6.  ツールボックスで、クリックして、**ボタン**を制御し、フォームのデザイン サーフェイスにドラッグします。 フォームに [Button] をドロップします。  
  
7.  ツールボックスで、クリックして、 **TextBox**を制御し、フォームのデザイン サーフェイスにドラッグします。 削除、 **TextBox**フォームにします。  
  
8. フォームのデザイン サーフェイスで、ボタンをダブルクリックします。  
  
     コード ページが表示されます。 カーソルは `button1_Click` 内にあります。  
  
10. `button1_Click` 関数に、次のコードを追加します。  
  
    ```vb  
    textBox1.Text = "Button was clicked!"
    ```  
  
    ```csharp 
    textBox1.Text = "Button was clicked!";
    ```  
  
    ```cpp  
    textBox1->Text = "Button was clicked!";  
    ```  
  
11. **[ビルド]** メニューの **[ソリューションのビルド]** を選択します。  
  
     プロジェクトがエラーのない状態でビルドされます。  
  
## <a name="debug-your-form"></a>フォームをデバッグする  
 これで、デバッグを開始する準備ができました。  
  
#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>このチュートリアルで作成した Windows フォームをデバッグするには  
  
1.  ソース ウィンドウで、テキストを追加した行の左マージンをクリックします。  
  
     ```vb  
    textBox1.Text = "Button was clicked!"
    ```  
  
    ```csharp 
    textBox1.Text = "Button was clicked!";
    ```  
  
    ```cpp  
    textBox1->Text = "Button was clicked!";  
    ``` 
  
     赤い点が表示され、その行のテキストが赤く強調表示されます。 赤い点はブレークポイントを表します。 詳細については、次を参照してください。[ブレークポイント](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)します。 デバッガーを起動した状態でアプリケーションを実行すると、そのコードに達したときにデバッガーが実行を中断します。 アプリケーションの状態を表示し、デバッグできます。  
  
    > [!NOTE]
    >  また、任意の行を右クリックすることもできます。 ポイントして、コードの**ブレークポイント**、順にクリックします**ブレークポイントの挿入**その行にブレークポイントを追加します。  
  
2.  ON、**デバッグ**] メニューの [選択**開始**します。  
  
     Windows フォームの実行が開始されます。  
  
3.  Windows フォームで、追加したボタンをクリックします。  
  
     Visual Studio では、コード ページのブレークポイントを設定した行に移動します。 行は黄色で強調表示されます。 ここで、アプリケーションの変数を確認し、実行を制御できます。 アプリケーションの実行は中断され、ユーザーのアクションを待っている状態です。  
  
4.  **デバッグ** メニューの 選択**Windows**、し**ウォッチ**、 をクリック**ウォッチ 1**します。  
  
5.  **[ウォッチ 1]** ウィンドウで、空白行をクリックします。 **名前**列に「 `textBox1.Text` (使用するかどうか Visual Basic または Visual c#) または`textBox1->Text`(使用するかどうか C++)、ENTER キーを押します。  
  
     **[ウォッチ 1]** ウィンドウとして引用符でこの変数の値が表示されます。  
  
    `""`  
 
6.  **デバッグ**] メニューの [選択**ステップ イン**します。  
  
     TextBox1.Text の変更の値、 **[ウォッチ 1]** ウィンドウ。  
  
    `Button was clicked!`  
  
7.  **デバッグ**] メニューの [選択**続行**プログラムのデバッグを再開します。  
  
8.  Windows フォームで、再びボタンをクリックします。  
  
     Visual Studio の実行が再び中断されます。  
  
9. ブレークポイントを表す赤丸をクリックします。  
  
     これにより、ブレークポイントがコードから削除されます。  
  
10. **デバッグ** メニューの 選択**デバッグの停止**します。  
  
## <a name="attach-to-your-windows-form-application-for-debugging"></a>デバッグする Windows フォーム アプリケーションにアタッチする  
 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] では、デバッガーを実行中のプロセスにアタッチできます。 Express Edition を使用している場合、この機能はサポートされません。  
  
#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>デバッグする Windows フォーム アプリケーションにアタッチするには  
  
1.  作成したプロジェクトで、追加した行の左マージンをクリックして、再度ブレークポイントを設定します。  
  
     ```vb  
    textBox1.Text = "Button was clicked!"
    ```  
  
    ```csharp 
    textBox1.Text = "Button was clicked!";
    ```  
  
    ```cpp  
    textBox1->Text = "Button was clicked!";   
  
2.  On the **Debug** menu, select **Start Without Debugging**.  
  
     The Windows Form starts running under Windows, just as if you had double-clicked its executable. The debugger is not attached.  
  
3.  On the **Debug** menu, select **Attach to Process**. (This command is also available on the **Tools** menu.)  
  
     The **Attach to Process** dialog box appears.  
  
4.  In the **Available Processes** pane, find the process name (Walkthrough_SimpleDebug.exe) in the **Process** column and click it.  
  
5.  Click the **Attach** button.  
  
6.  In your Windows Form, click the one and only button.  
  
     The debugger breaks execution of the Windows Form at the breakpoint.  
  
## See Also  
 [Debugging Managed Code](../debugger/debugging-managed-code.md)   
 [Debugger Security](../debugger/debugger-security.md)