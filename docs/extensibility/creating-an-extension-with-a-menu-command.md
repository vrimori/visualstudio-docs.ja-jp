---
title: メニュー コマンドを使用して、拡張機能の作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 00c80692929ac19b55f68b8aa20306f39ddceae6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="creating-an-extension-with-a-menu-command"></a>メニュー コマンドを使用して、拡張機能の作成
このチュートリアルでは、メモ帳を起動するメニュー コマンド拡張機能を作成する方法を示します。 
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  

## <a name="creating-a-menu-command"></a>メニュー コマンドの作成  
  
1.  という名前の VSIX プロジェクトを作成する**FirstMenuCommand**です。 VSIX プロジェクトのテンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#/機能拡張**です。  
  
2.  プロジェクトを開いたら、という名前のカスタム コマンド項目テンプレートの追加**FirstCommand**です。 **ソリューション エクスプ ローラー**プロジェクト ノードを右クリックし、選択、**追加/新しい項目の**します。 **新しい項目の追加**ダイアログ ボックスに移動して**Visual c#/機能拡張**選択と**にカスタム コマンド**です。 **名前**ウィンドウの下部にあるフィールドに、コマンド ファイルの名前を変更する**FirstCommand.cs**です。  
  
3.  プロジェクトをビルドし、デバッグを開始します。  
  
     Visual Studio の実験用インスタンスが表示されます。 実験用インスタンスの詳細については、次を参照してください。 [、実験用インスタンス](../extensibility/the-experimental-instance.md)です。  
  
4.  実験用インスタンスの開く、**ツール/拡張機能と更新プログラム**ウィンドウです。 表示されるはずの**FirstMenuCommand**拡張機能は、ここです。 (開く場合**拡張機能と更新**、作業には、Visual Studio のインスタンスでは表示されません**FirstMenuCommand**)。  
  
     次に「、**ツール**実験用インスタンスのメニュー。 表示されるはず**呼び出す FirstCommand**コマンド。 この時点でのみ表示"FirstCommandPackage 内 FirstMenuCommand.FirstCommand.MenuItemCallback()"と表示されているメッセージ ボックスです。 実際には、次のセクションで、このコマンドからメモ帳を起動する方法を会いしましょう。  
  
## <a name="changing-the-menu-command-handler"></a>メニュー コマンドのハンドラーを変更します。  
 これでメモ帳を起動するコマンドのハンドラーを更新してみましょう。  
  
1.  デバッグを停止し、Visual Studio の稼働インスタンスに戻ります。 FirstCommand.cs ファイルを開き、次の追加ステートメントを使用します。  
  
    ```csharp  
    using System.Diagnostics;  
    ```  
  
2.  プライベート FirstCommand コンス トラクターを検索します。 は、コマンドがコマンドのサービスにフックしたりコマンド ハンドラーを指定します。 コマンド ハンドラーの名前を StartNotepad、次のように変更します。  
  
    ```csharp  
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
  
    ```csharp  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4.  試してみましょう。プロジェクトのデバッグを開始し、をクリックして**ツール]/[呼び出し FirstCommand**、つなげてメモ帳のインスタンスが表示されます。  
  
     インスタンスを使用することができます、<xref:System.Diagnostics.Process>クラスはすべて、実行可能ファイルだけでなくメモ帳を実行します。 試してみて calc.exe、例を示します。  
  
## <a name="cleaning-up-the-experimental-environment"></a>実験用の環境をクリーンアップします。  
 複数の拡張機能の開発またはだけ拡張機能のコードの異なるバージョンの結果を調査する場合、実験用の環境は動作を停止する可能性があります。 この場合、リセット スクリプトを実行する必要があります。 呼び出された**Visual Studio 2015 の実験用インスタンスをリセット**、Visual Studio SDK の一部として出荷とします。 このスクリプトは、最初から開始できるように、実験用の環境から、拡張機能に対するすべての参照を削除します。  
  
 2 つの方法のいずれかでこのスクリプトを取得できます。  
  
1.  デスクトップで、検索**Visual Studio 2015 の実験用インスタンスをリセット**です。  
  
2.  コマンドラインから次の手順を実行します。  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## <a name="deploying-your-extension"></a>拡張機能を展開します。  
 これで、希望どおりに実行されているツール拡張機能がある場合は、ある友人や同僚と共有について考えてみましょう。 Visual Studio 2015 がインストールされているを持っていればは、簡単です。 行う必要があるは、.vsix ファイルを作成した送信です。 (必ずをリリース モードでビルドします。)  
  
 FirstMenuCommand bin ディレクトリにこの拡張機能を探し、.vsix ファイルを見つけることができます。 具体的には、リリース構成でビルドしたと仮定した場合になります。  
  
 **\<コード ディレクトリ > \FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix**  
  
 友人を拡張機能をインストールするには、Visual Studio の開いているすべてのインスタンスを閉じ、.vsix ファイルを表示する をダブルクリックする必要があります、 **VSIX インストーラー**です。 ファイルがコピー、 **%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions**ディレクトリ。  
  
 友人は、もう一度 Visual Studio を起動と、彼は、FirstMenuCommand の拡張機能があります**ツール/拡張機能と更新プログラム**です。 彼に移動できます**拡張機能と更新プログラム**アンインストールまたはすぎる、拡張機能を無効にします。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルでは、Visual Studio の拡張を行うことができますのごく一部のみを説明しました。 次に、Visual Studio 拡張機能で行うことができます (比較的簡単) などの短い一覧を示します。  
  
1.  単純なメニュー コマンドを使用して詳細な点の多くを行うことができます。  
  
    1.  独自のアイコンを追加:[メニュー コマンドにアイコンを追加します。](../extensibility/adding-icons-to-menu-commands.md)  
  
    2.  メニュー コマンドのテキストを変更:[メニュー コマンドのテキストを変更します。](../extensibility/changing-the-text-of-a-menu-command.md)  
  
    3.  メニューのショートカット コマンドに追加する:[のメニュー項目へのキーボード ショートカットのバインド](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2.  さまざまな種類のコマンド、メニューのおよびツールバーを追加:[拡張メニューとコマンド](../extensibility/extending-menus-and-commands.md)  
  
3.  ツール ウィンドウを追加し、組み込みの Visual Studio のツール ウィンドウの拡張:[の拡張とツール ウィンドウのカスタマイズ](../extensibility/extending-and-customizing-tool-windows.md)  
  
4.  IntelliSense、コードの修正候補を追加し、その他の機能は、既存のコード エディター:[エディターと言語サービスの拡張](../extensibility/extending-the-editor-and-language-services.md)  
  
5.  オプションとプロパティ ページやユーザー設定の拡張機能を追加:[の拡張プロパティと [プロパティ] ウィンドウ](../extensibility/extending-properties-and-the-property-window.md)と[ユーザー設定の拡張とオプション](../extensibility/extending-user-settings-and-options.md)  
  
 他の種類の拡張機能の新しい種類のプロジェクトの作成など、少しの作業が必要 ([拡張プロジェクト](../extensibility/extending-projects.md))、エディターの新しい型を作成する ([を作成するカスタム エディターやデザイナー](../extensibility/creating-custom-editors-and-designers.md))、または分離シェルで、拡張機能の実装: [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)
