---
title: "メニュー コマンドを使用して拡張機能の作成 | Microsoft Docs"
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
  - "vspackage を作成します。"
  - "vspackage"
  - "チュートリアル"
  - "visual studio パッケージ"
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
caps.latest.revision: 56
caps.handback.revision: 56
ms.author: "gregvanl"
manager: "ghogen"
---
# メニュー コマンドを使用して拡張機能の作成
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このチュートリアルでは、メモ帳を起動するメニュー コマンドを使用して拡張機能を作成する方法を示します。  
  
## 必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、「[Visual Studio SDK をインストールします。](../extensibility/installing-the-visual-studio-sdk.md)」を参照してください。  
  
## メニュー コマンドの作成  
  
1.  という名前の VSIX プロジェクトを作成する **FirstMenuCommand**します。 VSIX プロジェクトのテンプレートを見つけることができます、 **新しいプロジェクト** \] ダイアログ ボックス \[ **Visual c\#\/機能拡張**します。  
  
2.  プロジェクトを開いたら、という名前のカスタム コマンド項目テンプレートを追加 **FirstCommand**します。**ソリューション エクスプ ローラー**, プロジェクト ノードを右クリックして、選択 **追加\/\[新しい項目の**します。**新しい項目の追加** ダイアログ ボックスに移動 **Visual c\#\/機能拡張** を選択して **にカスタム コマンド**します。**名** ウィンドウの下部にあるフィールドに、コマンド ファイルの名前を変更する **FirstCommand.cs**します。  
  
3.  プロジェクトをビルドし、デバッグを開始します。  
  
     Visual Studio の実験用インスタンスが表示されます。 実験用インスタンスの詳細については、次を参照してください。 [実験用インスタンス](../extensibility/the-experimental-instance.md)します。  
  
4.  実験用インスタンスで開き、  **ツール\/拡張機能と更新プログラム** ウィンドウです。 確認する必要があります、 **FirstMenuCommand** 拡張機能は、ここです。 \(開く場合 **拡張機能と更新プログラム** 、作業には、Visual Studio のインスタンスでは表示されません **FirstMenuCommand**\)。  
  
     進んでください、 **ツール** 実験用インスタンスのメニュー。 はず **呼び出す FirstCommand** コマンドです。 この時点でのみ表示"FirstCommandPackage 内 FirstMenuCommand.FirstCommand.MenuItemCallback\(\)"を示すメッセージ ボックスです。 実際には、次のセクションで、このコマンドからメモ帳を起動する方法を見ていきます。  
  
## メニュー コマンドのハンドラーを変更します。  
 ここでメモ帳を起動するコマンド ハンドラーを更新します。  
  
1.  デバッグを停止し、作業用インスタンスの Visual Studio に戻ります。 FirstCommand.cs ファイルを開き、次の追加ステートメントを使用します。  
  
    ```c#  
    using System.Diagnostics;  
    ```  
  
2.  プライベート FirstCommand コンス トラクターを検索します。 ここコマンド サービスにコマンドがフックし、コマンド ハンドラーを指定します。 コマンド ハンドラーの名前を StartNotepad、次のように変更します。  
  
    ```c#  
    private FirstCommand(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
         OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(CommandSet, CommandId);  
            // Change to StartNotepad handler.  
            MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
3.  MenuItemCallback メソッドを削除し、メモ帳が起動した StartNotepad メソッドを追加します。  
  
    ```c#  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4.  試してみましょう。 プロジェクトのデバッグを開始し、をクリックして **ツール\] を呼び出す FirstCommand**, 、メモ帳のインスタンスからエラーが表示されます。  
  
     インスタンスを使用する、 <xref:System.Diagnostics.Process> クラスはすべて、実行可能ファイルだけでなくメモ帳を実行します。 と共に使用して、calc.exe などです。  
  
## 実験用の環境をクリーンアップします。  
 複数の拡張機能の開発またはだけさまざまなバージョンの拡張機能のコードの結果を表示する場合、実験用の環境が動作することを停止します。 この場合、リセット スクリプトを実行する必要があります。 呼び出された **Visual Studio 2015 の実験用インスタンスをリセット**, 、Visual Studio SDK の一部として出荷とします。 このスクリプトは、最初から起動できるように、実験用の環境から、拡張機能に対するすべての参照を削除します。  
  
 2 つの方法のいずれかでこのスクリプトを取得できます。  
  
1.  デスクトップで、検索 **Visual Studio 2015 の実験用インスタンスをリセット**します。  
  
2.  コマンド プロンプトから次の手順を実行します。  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## 拡張機能を展開します。  
 これで、思いどおりに実行されているツールの拡張機能がある場合は、ある友人や同僚と共有について考えてみましょう。 インストールされている Visual Studio 2015 を持っていればは、簡単です。 行う必要があるすべては、ビルドした .vsix ファイルを送信します。 \(必ずリリース モードでビルドする\)。  
  
 この拡張機能に .vsix ファイル FirstMenuCommand bin ディレクトリにあります。 具体的には、リリース構成を作成したと仮定した場合、それになります。  
  
 **\< コード ディレクトリ \> \\FirstMenuCommand\\FirstMenuCommand\\bin\\Release\\ FirstMenuCommand.vsix**  
  
 友人を拡張機能をインストールするには、Visual Studio の開いているすべてのインスタンスを閉じてから、起動を .vsix ファイルをダブルクリックする必要がある、 **VSIX インストーラー**します。 ファイルがコピー、 **%LocalAppData%\\Microsoft\\VisualStudio\\14.0\\Extensions** ディレクトリ。  
  
 友人は、Visual Studio をもう一度表示、彼がわかります FirstMenuCommand 拡張子 **ツール\/拡張機能と更新プログラム**します。 アクセスする彼が **拡張機能と更新プログラム** をアンインストールするかも、拡張機能を無効にします。  
  
## 次の手順  
 このチュートリアルでは、Visual Studio 拡張機能で何ができるのごく一部のみを説明します。 Visual Studio 拡張機能で行うことができます \(比較的簡単\) などの簡単な一覧を次に示します。  
  
1.  多くの単純なメニュー コマンドを使用して行うことができます。  
  
    1.  独自のアイコンを追加します。 [メニュー コマンドにアイコンを追加します。](../extensibility/adding-icons-to-menu-commands.md)  
  
    2.  メニュー コマンドのテキストを変更します。 [メニュー コマンドのテキストを変更します。](../extensibility/changing-the-text-of-a-menu-command.md)  
  
    3.  コマンドをメニューのショートカットを追加します。 [メニュー項目にバインドのキーボード ショートカット](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2.  さまざまな種類のコマンド、メニューのおよびツールバーを追加します。 [拡張メニューとコマンド](../extensibility/extending-menus-and-commands.md)  
  
3.  ツール ウィンドウを追加し、組み込みの Visual Studio のツール ウィンドウを拡張します。 [拡張とカスタマイズ ツール ウィンドウ](../extensibility/extending-and-customizing-tool-windows.md)  
  
4.  既存のコード エディターには、IntelliSense、コードの推奨事項、およびその他の機能を追加します。 [エディターと言語サービスの拡張](../extensibility/extending-the-editor-and-language-services.md)  
  
5.  オプションとプロパティ ページやユーザー設定、拡張機能を追加します [プロパティと \[プロパティ\] ウィンドウの拡張](../Topic/Extending%20Properties%20and%20the%20Property%20Window.md) と。 [ユーザー設定の拡張とオプション](../extensibility/extending-user-settings-and-options.md)  
  
 その他の種類の拡張機能プロジェクトの新しい種類の作成などのもう少し作業が必要に \([プロジェクトの拡張](../extensibility/extending-projects.md)\)、エディターの新しい型を作成する \([カスタム エディターとデザイナーを作成します。](../extensibility/creating-custom-editors-and-designers.md)\)、または分離されたシェルで、拡張機能を実装します。 [Visual Studio シェルの分離](../extensibility/visual-studio-isolated-shell.md)