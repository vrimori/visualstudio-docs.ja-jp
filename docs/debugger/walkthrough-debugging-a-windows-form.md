---
title: 'チュートリアル: Windows フォームのデバッグ |Microsoft ドキュメント'
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
ms.openlocfilehash: b4e256aeef1a068ddc46d13e98b344bcce56d08b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477954"
---
# <a name="walkthrough-debugging-a-windows-form"></a>チュートリアル : Windows フォームのデバッグ
Windows フォームは、最も一般的なマネージ アプリケーションの 1 つです。 Windows フォームは、標準 Windows アプリケーションを作成します。 このチュートリアルは、Visual Basic、C#、または C++ を使用して実行できます。  
  
 開いているソリューションがある場合は、ソリューションを閉じる必要があります。  
  
### <a name="to-prepare-for-this-walkthrough"></a>このチュートリアルの準備をするには  
  
-   既に開いているソリューションがある場合は、そのソリューションを閉じます。 (上、**ファイル**メニューの **ソリューションを閉じる**)。  
  
## <a name="create-a-new-windows-form"></a>新しい Windows フォームを作成する  
 次に、新しい Windows フォームを作成します。  
  
#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>このチュートリアルの Windows フォームを作成するには  
  
1.  **ファイル** メニューの 選択**新規** をクリック**プロジェクト**です。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  プロジェクトの種類 ウィンドウで開く、 **Visual Basic**、 **Visual c#**、または**Visual C**しノード  
  
    1.  Visual Basic または Visual C# の場合、選択、 **Windows**  ノードを選択し、 **Windows フォーム アプリケーション**で、**テンプレート**ウィンドウ。  
  
    2.  Visual C は、選択、 **CLR**  ノードを選択し、 **Windows フォーム アプリケーション**で、**テンプレート**ウィンドウ.  
  
3.  **テンプレート**ペインで、 **Windows アプリケーション**です。  
  
4.  **名前**ボックスで、プロジェクトの一意名 (Walkthrough_SimpleDebug など) を付けます。  
  
5.  **[OK]** をクリックします。  
  
     新しいプロジェクトが作成され、Windows フォーム デザイナーに新しいフォームが表示されます。 詳細については、次を参照してください。 [Windows フォーム デザイナー](http://msdn.microsoft.com/en-us/3c3d61f8-f36c-4d41-b9c3-398376fabb15)です。  
  
6.  **ビュー**メニューの **ツールボックス**です。  
  
     ツールボックスが表示されます。 詳細については、「[ツールボックス](../ide/reference/toolbox.md)」をご覧ください。  
  
7.  ツールボックスで、をクリックして、**ボタン**を制御し、コントロールをフォームのデザイン サーフェイスにドラッグします。 フォームに [Button] をドロップします。  
  
8.  ツールボックスで、をクリックして、 **TextBox**を制御し、コントロールをフォームのデザイン サーフェイスにドラッグします。 削除、 **TextBox**フォームにします。  
  
9. フォームのデザイン サーフェイスで、ボタンをダブルクリックします。  
  
     コード ページが表示されます。 カーソルは `button1_Click` 内にあります。  
  
10. `button1_Click` 関数に、次のコードを追加します。  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
11. **[ビルド]** メニューの **[ソリューションのビルド]** を選択します。  
  
     プロジェクトがエラーのない状態でビルドされます。  
  
## <a name="debug-your-form"></a>フォームをデバッグする  
 これで、デバッグを開始する準備ができました。  
  
#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>このチュートリアルで作成した Windows フォームをデバッグするには  
  
1.  ソース ウィンドウで、テキストを追加した行の左マージンをクリックします。  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
     赤い点が表示され、その行のテキストが赤く強調表示されます。 赤い点はブレークポイントを表します。 詳細については、次を参照してください。[ブレークポイント](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)です。 デバッガーを起動した状態でアプリケーションを実行すると、そのコードに達したときにデバッガーが実行を中断します。 アプリケーションの状態を表示し、デバッグできます。  
  
    > [!NOTE]
    >  また、任意の行を右クリックすることもできます。 コード、の順にポイント**ブレークポイント**、クリックして**ブレークポイントの挿入**その行のブレークポイントを追加します。  
  
2.  ON、**デバッグ**] メニューの [選択**開始**です。  
  
     Windows フォームの実行が開始されます。  
  
3.  Windows フォームで、追加したボタンをクリックします。  
  
     Visual Studio では、コード ページのブレークポイントを設定した行に移動します。 行は黄色で強調表示されます。 ここで、アプリケーションの変数を確認し、実行を制御できます。 アプリケーションの実行は中断され、ユーザーのアクションを待っている状態です。  
  
4.  **デバッグ** メニューの 選択**Windows**、し**ウォッチ**、 をクリック**ウォッチ 1**です。  
  
5.  **[ウォッチ 1]** ウィンドウで、空白行をクリックします。 **名前**列に「 `textBox1.Text` (使用するかどうか Visual Basic または Visual c#) または`textBox1->Text`(使用するかどうか C++)、ENTER キーを押します。  
  
     **[ウォッチ 1]** ウィンドウは、引用符でこの変数の値を示しています。  
  
    ```  
    ""  
    ```  
  
6.  **デバッグ**] メニューの [選択**ステップ イン**です。  
  
     Textbox1.text」と入力の変更の値、 **[ウォッチ 1]** ウィンドウ。  
  
    ```  
    Button was clicked!  
    ```  
  
7.  **デバッグ**] メニューの [選択**続行**プログラムのデバッグを再開します。  
  
8.  Windows フォームで、再びボタンをクリックします。  
  
     Visual Studio の実行が再び中断されます。  
  
9. ブレークポイントを表す赤丸をクリックします。  
  
     これにより、ブレークポイントがコードから削除されます。  
  
10. **デバッグ** メニューの 選択**デバッグの停止**です。  
  
## <a name="attach-to-your-windows-form-application-for-debugging"></a>デバッグする Windows フォーム アプリケーションにアタッチする  
 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] では、デバッガーを実行中のプロセスにアタッチできます。 Express Edition を使用している場合、この機能はサポートされません。  
  
#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>デバッグする Windows フォーム アプリケーションにアタッチするには  
  
1.  作成したプロジェクトで、追加した行の左マージンをクリックして、再度ブレークポイントを設定します。  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!"  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
2.  **デバッグ**メニューの **デバッグなしで開始**です。  
  
     Windows フォームは、実行可能ファイルをダブルクリックしたときと同様に、Windows で実行を開始します。 デバッガーはアタッチされていません。  
  
3.  **デバッグ**メニューの **プロセスにアタッチする**です。 (このコマンドはできるもの**ツール**メニューです)。  
  
     **[プロセスにアタッチ]** ダイアログ ボックスが表示されます。  
  
4.  **選択可能なプロセス** ウィンドウで、プロセス名 (Walkthrough_SimpleDebug.exe) 検索、**プロセス**列をクリックします。  
  
5.  クリックして、**アタッチ**ボタンをクリックします。  
  
6.  Windows フォームで、1 つだけあるボタンをクリックします。  
  
     ブレークポイントの位置で、Windows フォームの実行が中断します。  
  
## <a name="see-also"></a>関連項目  
 [マネージ コードをデバッグする](../debugger/debugging-managed-code.md)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)