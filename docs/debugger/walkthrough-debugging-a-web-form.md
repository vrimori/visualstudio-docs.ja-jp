---
title: 'チュートリアル: Web フォームのデバッグ |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web pages [.NET Framework], debugging
- Web sites [.NET Framework], debugging
- ASP.NET, debugging Web applications
- Web applications [.NET Framework], debugging
- ASP.NET Web sites, debugging
- ASP.NET Web pages, debugging
- debugging ASP.NET Web applications, Web Forms
- debugging [Visual Studio], Web Forms
ms.assetid: e2b4fa14-8f5b-444d-a903-54070b784bd4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1fbd7250aef7becd3dc2d29b38eccf9cc6c0f430
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-debugging-a-web-form"></a>チュートリアル : Web フォームのデバッグ
このチュートリアルでは、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーション (Web フォーム) をデバッグする方法について説明します。 開始し、実行を停止および、ブレークポイントの設定で変数を確認する方法を示します、**ウォッチ**ウィンドウです。  
  
> [!NOTE]
>  このチュートリアルを完了するには、サーバー コンピューターに対する管理者特権が必要です。 既定では、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] プロセス (aspnet_wp.exe または w3wp.exe) は、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] プロセスとして実行されます。 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] をデバッグするには、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] が実行されているコンピューターに対する管理者特権が必要です。 詳細については、次を参照してください。[システム要件](../debugger/aspnet-debugging-system-requirements.md)です。  
  
 使用している設定またはエディションによっては、ヘルプの記載と異なるダイアログ ボックスやメニュー コマンドが表示される場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
### <a name="to-create-the-web-form"></a>Web フォームを作成するには  
  
1.  既に開いているソリューションがある場合は、そのソリューションを閉じます。  
  
2.  **ファイル** メニューのをクリックして**新規**、クリックして**Web サイト**です。  
  
     **新しい Web サイト** ダイアログ ボックスが表示されます。  
  
3.  **テンプレート** ウィンドウで、をクリックして**ASP.NET Web サイト**です。  
  
4.  **場所**行で、 **HTTP**リストから、テキスト ボックスに、入力 **http://localhost/WebSite**です。  
  
5.  **言語**一覧で、クリックして**Visual c#**または**Visual Basic**です。  
  
6.  **[OK]**をクリックします。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で新しいプロジェクトが作成され、既定の HTML ソース コードが表示されます。 という名前の新しい仮想ディレクトリも作成**web サイト** **Default Web Site** IIS でします。  
  
7.  クリックして、**デザイン**下余白のタブです。  
  
8.  クリックして、**ツールボックス**左の余白のタブまたは選択、**ビュー**メニュー。  
  
     **ツールボックス** が表示されます。  
  
9. **ツールボックス**をクリックして、**ボタン**を制御し、Default.aspx、メインのデザイン サーフェイスに追加します。  
  
10. **ツールボックス**、 をクリックして、 **Textbox**を制御して、Default.aspx、メインのデザイン サーフェイスにドラッグします。  
  
11. ドロップしたボタン コントロールをダブルクリックします。  
  
     これで、コード ページが表示されます。C# の場合は Default.aspx.cs、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] の場合は Default.aspx.vb です。 `Button1_Click` 関数の場所にカーソルがあります。  
  
12. `Button1_Click` 関数に次のコードを追加します。  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    TextBox1.Text = "Button was clicked!";  
    ```  
  
13. **[ビルド]** メニューの **[ソリューションのビルド]**をクリックします。  
  
     プロジェクトがエラーのない状態でビルドされます。  
  
     これで、デバッグを開始する準備ができました。  
  
### <a name="to-debug-the-web-form"></a>Web フォームをデバッグするには  
  
1.  Default.aspx.cs または Default.aspx.vb ウィンドウで、テキストを追加した行の左の余白をクリックします。  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
     赤い点が表示され、その行のテキストが赤く強調表示されます。 赤い点はブレークポイントを表します。 デバッガーを起動した状態でアプリケーションを実行すると、そのコードに達したときにデバッガーが実行を中断します。 アプリケーションの状態を表示し、デバッグできます。 詳細については、次を参照してください。[ブレークポイント](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)です。  
  
2.  **[デバッグ]** メニューの **[デバッグの開始]** をクリックします。  
  
3.  **デバッグが無効** ダイアログ ボックスが表示されます。 選択**Web.config ファイルを変更してデバッグを有効に** をクリックし、 **OK**です。  
  
     Internet Explorer が起動し、デザインしたページが表示されます。  
  
4.  Internet Explorer で、作成したボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] では、コード ページ Default.aspx.cs または Default.aspx.vb のブレークポイントを設定した行に移動します。 行は黄色で強調表示されます。 ここで、アプリケーションの変数を確認し、実行を制御できます。 アプリケーションの実行が中断され、コマンドの入力を待っている状態です。  
  
5.  **デバッグ** メニューのをクリックして**Windows**をクリックし、**ウォッチ**、順にクリック**ウォッチ 1**です。  
  
6.  **ウォッチ**ウィンドウで、「 **textbox1.text」と入力**です。  
  
     **ウォッチ**ウィンドウは、変数の値を示しています`TextBox1.Text`:。  
  
    ```  
    ""  
    ```  
  
7.  **デバッグ** メニューのをクリックして**ステップ オーバー**です。  
  
     値`TextBox1.Text`での変更内容、**ウォッチ**を読み取るウィンドウ。  
  
    ```  
    "Button was clicked!"  
    ```  
  
8.  **デバッグ** メニューのをクリックして**続行**です。  
  
9. Internet Explorer で、作成したボタンを再度クリックします。  
  
     ブレークポイントで再度実行が中断されます。  
  
10. Default.aspx.cs ウィンドウまたは Default.aspx.vb ウィンドウの左のマージンにある赤い点をクリックします。  
  
     ブレークポイントが削除されます。  
  
11. **デバッグ** メニューのをクリックして**デバッグの停止**です。  
  
### <a name="to-attach-to-the-web-form-for-debugging"></a>デバッグする Web フォームにアタッチするには  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] では、デバッガーを実行中のプロセスにアタッチできます。 デバッグの効率を最も高くするには、シンボル (PDB) ファイルを持つデバッグ バージョンとして実行可能ファイルをコンパイルします。  
  
2.  Default.aspx.cs ウィンドウまたは Default.aspx.vb ウィンドウの左のマージンをクリックして、追加した行に再度ブレークポイントを設定します。  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
3.  **デバッグ** メニューのをクリックして**デバッグなしで開始**です。  
  
     Internet Explorer で Web フォームが起動しますが、デバッガーはアタッチされません。  
  
4.  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] プロセスにアタッチします。 詳細については、次を参照してください。[展開されている Web アプリケーションのデバッグ](../debugger/debugging-deployed-web-applications.md)です。  
  
5.  Internet Explorer で、フォームのボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で、Default.aspx.cs、Default.aspx.vb、または Default.aspx のブレークポイントにヒットします。  
  
6.  終了したらデバッグで、**デバッグ** メニューのをクリックして**デバッグの停止**です。  
  
## <a name="see-also"></a>関連項目  
 [ASP.NET アプリケーションをデバッグします。](../debugger/how-to-enable-debugging-for-aspnet-applications.md)