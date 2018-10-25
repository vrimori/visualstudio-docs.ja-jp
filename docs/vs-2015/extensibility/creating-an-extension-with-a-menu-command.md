---
title: メニュー コマンドを使用して拡張機能の作成 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
caps.latest.revision: 57
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cc470e08511c7bda44bfda2012636b626ba41e83
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49925930"
---
# <a name="creating-an-extension-with-a-menu-command"></a>メニュー コマンドを使用した拡張機能の作成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このチュートリアルでは、メモ帳を起動するメニュー コマンドを使用して拡張機能を作成する方法を示します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-menu-command"></a>メニュー コマンドの作成  
  
1.  という名前の VSIX プロジェクトを作成する**FirstMenuCommand**します。 VSIX プロジェクト テンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#/機能拡張**します。  
  
2.  という名前のカスタム コマンド項目テンプレートを追加、プロジェクトが開いたら、 **FirstCommand**します。 **ソリューション エクスプ ローラー**でプロジェクト ノードを右クリックし、選択**追加/新しい項目の**します。 **新しい項目の追加**ダイアログ ボックスに移動して**Visual c#/機能拡張**選択と**カスタム コマンド**。 **名前**ウィンドウの下部にあるフィールドに、コマンド ファイル名を変更して**FirstCommand.cs**します。  
  
3.  プロジェクトをビルドし、デバッグを開始します。  
  
     Visual Studio の実験用インスタンスが表示されます。 実験用インスタンスの詳細については、次を参照してください。 [、実験用インスタンス](../extensibility/the-experimental-instance.md)します。  
  
4.  実験用インスタンスの開く、**ツール/拡張機能と更新**ウィンドウ。 表示する必要があります、 **FirstMenuCommand**拡張します。 (を開いた場合**拡張機能と更新**、Visual Studio の作業用インスタンスでは表示されません**FirstMenuCommand**)。  
  
     次に「、**ツール**実験用インスタンスのメニュー。 表示する必要があります**呼び出す FirstCommand**コマンド。 この時点でそれだけが表示されます"FirstCommandPackage 内 FirstMenuCommand.FirstCommand.MenuItemCallback()"ことを示すメッセージ ボックス。 実際には、次のセクションで、このコマンドからメモ帳を起動する方法を見ていきます。  
  
## <a name="changing-the-menu-command-handler"></a>メニュー コマンドのハンドラーを変更します。  
 ここでメモ帳を起動するコマンド ハンドラーを更新しましょう。  
  
1.  デバッグを停止し、作業のインスタンスの Visual Studio に戻ります。 FirstCommand.cs ファイルを開き、次を追加するステートメントを使用します。  
  
    ```csharp  
    using System.Diagnostics;  
    ```  
  
2.  プライベート FirstCommand コンス トラクターを検索します。 これは、コマンドがコマンド サービスにフックし、コマンド ハンドラーが指定されてです。 コマンド ハンドラーの名前を StartNotepad、としては、次のように変更します。  
  
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
  
4.  試してみましょう。プロジェクトのデバッグを開始し、をクリックして**ツール]/[呼び出し FirstCommand**、メモ帳のインスタンスが起動を表示する必要があります。  
  
     インスタンスを使用することができます、<xref:System.Diagnostics.Process>クラスは実行可能ファイル、メモ帳だけでなくを実行します。 使って試す calc.exe など。  
  
## <a name="cleaning-up-the-experimental-environment"></a>実験用の環境をクリーンアップします。  
 複数の拡張機能の開発またはだけ拡張機能のコードのさまざまなバージョンで結果を調査する場合、実験的な環境はどおりに動作を停止する可能性があります。 この場合、リセット スクリプトを実行する必要があります。 呼び出された**Visual Studio 2015 の実験用インスタンスをリセット**、Visual Studio SDK の一部としてに同梱されています。 このスクリプトは、最初から開始できるように、実験用の環境から、拡張機能をすべての参照を削除します。  
  
 2 つの方法のいずれかでこのスクリプトを取得できます。  
  
1.  デスクトップから、検索**Visual Studio 2015 の実験用インスタンスをリセット**します。  
  
2.  コマンド ラインから次を実行します。  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## <a name="deploying-your-extension"></a>拡張機能を展開します。  
 希望どおりに実行されているツールの拡張機能をしたので、友人や同僚と共有について考える時間を勧めします。 Visual Studio 2015 がインストールされているがある限りは、簡単です。 行う必要があるすべてが構築した、.vsix ファイルを送信します。 (必ずをリリース モードでビルドします。)  
  
 この拡張機能に .vsix ファイル FirstMenuCommand bin ディレクトリにあります。 具体的には、リリース構成をビルドしたと仮定すると、それになります。  
  
 **\<コード ディレクトリ > \FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix**  
  
 友人を拡張機能をインストールするには、Visual Studio の開いているすべてのインスタンスを閉じてが表示されます、.vsix ファイルをダブルクリックする必要があります、 **VSIX インストーラー**します。 ファイルをコピー、 **%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions**ディレクトリ。  
  
 友人は、Visual Studio をもう一度表示、ときに、FirstMenuCommand の拡張機能がわかります**ツール/拡張機能と更新**します。 彼に移動して**拡張機能と更新**をアンインストールまたはすぎる、拡張機能を無効にします。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルでは、Visual Studio 拡張機能で何ができるのごく一部のみを説明します。 Visual Studio 拡張機能で行えること (簡単) などの短い一覧を次に示します。  
  
1. 多くの単純なメニュー コマンドを使用して行うことができます。  
  
   1.  独自のアイコンの追加:[メニュー コマンドに追加するアイコン](../extensibility/adding-icons-to-menu-commands.md)  
  
   2.  メニュー コマンドのテキストを変更:[メニュー コマンドのテキストを変更します。](../extensibility/changing-the-text-of-a-menu-command.md)  
  
   3.  メニューのショートカットをコマンドに追加:[メニュー項目のキーボード ショートカットのバインド](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2. さまざまな種類のコマンド、メニューのおよびツールバーを追加:[拡張メニューとコマンド](../extensibility/extending-menus-and-commands.md)  
  
3. ツール ウィンドウを追加し、組み込みの Visual Studio ツール ウィンドウの拡張:[拡張とカスタマイズ ツールの Windows](../extensibility/extending-and-customizing-tool-windows.md)  
  
4. IntelliSense、コードの修正候補を追加し、その他の機能は、既存のコード エディター:[エディターと言語サービス拡張](../extensibility/extending-the-editor-and-language-services.md)  
  
5. オプションとプロパティ ページとユーザー設定、拡張機能を追加:[拡張プロパティとプロパティ ウィンドウ](../extensibility/extending-properties-and-the-property-window.md)と[Extending User Settings and オプション](../extensibility/extending-user-settings-and-options.md)  
  
   他の種類の拡張機能が、新しい種類のプロジェクトの作成などのもう少し作業が必要です ([拡張プロジェクト](../extensibility/extending-projects.md))、エディターの新しい種類の作成 ([を作成するカスタム エディターとデザイナー](../extensibility/creating-custom-editors-and-designers.md))、または分離シェルで、拡張機能を実装する: [Visual Studio 分離シェル](../extensibility/visual-studio-isolated-shell.md)

