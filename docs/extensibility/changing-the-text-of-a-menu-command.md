---
title: "メニュー コマンドのテキストを変更します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "メニュー、テキストの変更"
  - "メニューのテキスト"
  - "テキストを変更するコマンド"
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# メニュー コマンドのテキストを変更します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

次の手順を使用してメニュー コマンドのテキスト ラベルを変更する方法を説明する、 <xref:System.ComponentModel.Design.IMenuCommandService> サービスです。  
  
## IMenuCommandService とメニュー コマンドのラベルを変更します。  
  
1.  という名前の VSIX プロジェクトを作成する `MenuText` メニュー コマンドを使用して名前付き **ChangeMenuText**します。 詳細については、「[メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)」を参照してください。  
  
2.  .Vstc ファイルで、追加、 `TextChanges` の次の例に示すように、メニュー コマンドにフラグを設定します。  
  
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
  
    ```c#  
    private void OnBeforeQueryStatus(object sender, EventArgs e)  
    {  
        var myCommand = sender as OleMenuCommand;  
        if (null != myCommand)  
        {  
            myCommand.Text = "New Text";  
                    }  
    }  
    ```  
  
     変更することで、このメソッドでメニュー コマンドの状態を更新することもできます。、 <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>, 、<xref:System.ComponentModel.Design.MenuCommand.Checked%2A>, 、および <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> プロパティを、 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> オブジェクトです。  
  
4.  ChangeMenuText コンス トラクターで元のコマンドの初期化と配置のコードを作成するコードを書き換えます、 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> \(なく `MenuCommand`\) メニュー コマンドを表し、追加する、 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> イベント ハンドラー、および、メニュー コマンド、メニュー コマンドのサービスを提供します。  
  
     次のようになりますに示します。  
  
    ```c#  
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
  
6.  **ツール** メニューという名前のコマンドを表示する必要があります **呼び出す ChangeMenuText**します。  
  
7.  コマンドをクリックします。 MenuItemCallback が呼び出されているお知らせメッセージ ボックスが表示されます。 メッセージ ボックスを閉じると、\[ツール\] メニュー コマンドの名前を参照する必要があります **新しいテキスト**します。