---
title: "コマンドの外観を変更します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "外観を変更するコマンド"
  - "メニュー コマンド、外観を変更します。"
  - "メニュー、コマンドの外観を変更します。"
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# コマンドの外観を変更します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

コマンドの外観を変更することで、ユーザーにフィードバックを提供できます。 たとえば、コマンドを使用できない場合、異なる外観にできます。 コマンド使用可能を非表示にまたはを表示すること、またはを確認または使用できますメニューでそれをオフにします。  
  
 コマンドの外観を変更するには、これらのアクションのいずれかの手順に従います。  
  
-   コマンド テーブルのファイルでのコマンド定義では、適切なフラグを指定します。  
  
-   使用して、 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> サービスです。  
  
-   実装、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> インターフェイスし、生のコマンド オブジェクトを変更します。  
  
 次の手順では、検索して管理されているパッケージ フレームワーク \(MPF\) を使用して、コマンドの外観を更新する方法を示します。  
  
### メニュー コマンドの外観を変更するには  
  
1.  指示に従って、 [メニュー コマンドのテキストを変更します。](../extensibility/changing-the-text-of-a-menu-command.md) という名前のメニュー項目を作成する `New Text`です。  
  
2.  ChangeMenuText.cs ファイルに次のコードを追加ステートメントを使用します。  
  
    ```c#  
    using System.Security.Permissions;  
    ```  
  
3.  ChangeMenuTextPackageGuids.cs ファイルでは、次の行を追加します。  
  
    ```c#  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4.  ChangeMenuText.cs ファイルでは、次のように ShowMessageBox メソッドのコードを置き換えます。  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5.  更新するコマンドを取得、 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> オブジェクトし、コマンド オブジェクトで、適切なプロパティを設定します。 たとえば、次のメソッド使用して、指定した VSPackage コマンドから利用または利用不可に設定します。 次のコードは、という名前の項目\] メニューの \[ `New Text` がクリックした後に使用できません。  
  
    ```c#  
    public bool ChangeMyCommand(int cmdID, bool enableCmd)  
    {  
        bool cmdUpdated = false;  
        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService))  
            as OleMenuCommandService;  
        var newCmdID = new CommandID(new Guid(ChangeMenuTextPackageGuids.guidChangeMenuTextPackageCmdSet), cmdID);  
        MenuCommand mc = mcs.FindCommand(newCmdID);  
        if (mc != null)  
        {  
            mc.Enabled = enableCmd;  
            cmdUpdated = true;  
        }  
        return cmdUpdated;    }  
    }  
    ```  
  
6.  プロジェクトをビルドし、デバッグを開始します。 Visual Studio の実験用インスタンスが表示されます。  
  
7.  **ツール** \] メニューのをクリックして、 **呼び出す ChangeMenuText** コマンドです。 コマンド名は、この時点で **呼び出す ChangeMenuText**, コマンド ハンドラーが ChangeMyCommand\(\) を呼び出していないため、します。  
  
8.  **ツール** メニューが表示されます **新しいテキスト**します。 クリックして **新しいテキスト**します。 コマンドを灰色に今すぐ必要があります。  
  
## 参照  
 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Vspackage でのユーザー インターフェイス要素を追加する方法](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [拡張メニューとコマンド](../extensibility/extending-menus-and-commands.md)   
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)