---
title: メニュー コマンドのテキストの変更 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 717e360e08cbdfee23221b9384a5574530f92e23
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="changing-the-text-of-a-menu-command"></a>メニュー コマンドのテキストを変更します。
次の手順を使用して、メニュー コマンドのテキスト ラベルを変更する方法を示します、<xref:System.ComponentModel.Design.IMenuCommandService>サービス。  
  
## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>IMenuCommandService とメニュー コマンドのラベルを変更します。  
  
1.  という名前の VSIX プロジェクトを作成する`MenuText`メニュー コマンドを使用して名前付き**ChangeMenuText**です。 詳細については、次を参照してください。[メニュー コマンドを使用して、拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)です。  
  
2.  .Vstc ファイルで追加、`TextChanges`の次の例に示すように、メニュー コマンドにフラグを設定します。  
  
    ```xml  
    <Button guid="guidChangeMenuTextPackageCmdSet" id="ChangeMenuTextId" priority="0x0100" type="Button">  
        <Parent guid="guidChangeMenuTextPackageCmdSet" id="MyMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <CommandFlag>TextChanges</CommandFlag>  
        <Strings>  
            <ButtonText>Invoke ChangeMenuText</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
3.  ChangeMenuText.cs ファイルでは、メニュー コマンドが表示される前に呼び出されるイベント ハンドラーを作成します。  
  
    ```csharp  
    private void OnBeforeQueryStatus(object sender, EventArgs e)  
    {  
        var myCommand = sender as OleMenuCommand;  
        if (null != myCommand)  
        {  
            myCommand.Text = "New Text";  
        }  
    }  
    ```  
  
     変更することで、このメソッドでメニュー コマンドの状態を更新することも、 <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>、 <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>、および<xref:System.ComponentModel.Design.MenuCommand.Enabled%2A>プロパティを<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>オブジェクト。  
  
4.  ChangeMenuText コンス トラクターでコードを置き換えます元コマンドの初期化と配置を作成するコード、 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (ではなく、 `MenuCommand`) するには、メニュー コマンドを表す、追加、 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> 、イベント ハンドラーと、メニューメニュー コマンド サービスするコマンドです。  
  
     新機能のようになります次に示します。  
  
    ```csharp  
    private ChangeMenuText(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.ShowMessageBox;  
            OleMenuCommand menuItem = new OleMenuCommand(ShowMessageBox, menuCommandID);  
            menuItem.BeforeQueryStatus +=  
                new EventHandler(OnBeforeQueryStatus);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
5.  プロジェクトをビルドし、デバッグを開始します。 Visual Studio の実験用インスタンスが表示されます。  
  
6.  **ツール**メニューという名前のコマンドを表示する必要があります**呼び出す ChangeMenuText**です。  
  
7.  コマンドをクリックします。 メッセージ ボックス announcing MenuItemCallback が呼び出されたことが表示されます。 メッセージ ボックスを破棄するときにする必要がありますを参照してください [ツール] メニュー コマンドの名前が、**新しいテキスト**です。
