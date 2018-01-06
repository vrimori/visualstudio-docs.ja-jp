---
title: "コマンドの外観の変更 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: eec62227ec39c1758c15e83fd1d8306e807d59fd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="changing-the-appearance-of-a-command"></a>コマンドの外観を変更します。
コマンドの外観を変更することによって、ユーザーにフィードバックを提供できます。 たとえばは使用できないと異なって表示するコマンドをする可能性があります。 コマンドを可能に使用できるか、使用できませんを非表示にまたは、それらを表示するまたは確認したり、メニューでそれをオフにできます。  
  
 コマンドの外観を変更するには、これらのアクションのいずれかの手順に従います。  
  
-   コマンド テーブルのファイルでのコマンド定義に適切なフラグを指定します。  
  
-   使用して、<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>サービス。  
  
-   実装、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスし、生のコマンド オブジェクトを変更します。  
  
 次の手順では、検索し、Managed Package Framework (MPF) を使用して、コマンドの外観を更新する方法を示します。  
  
### <a name="to-change-the-appearance-of-a-menu-command"></a>メニュー コマンドの外観を変更するには  
  
1.  指示に従って[メニュー コマンドのテキストを変更する](../extensibility/changing-the-text-of-a-menu-command.md)という名前のメニュー項目を作成する`New Text`です。  
  
2.  ChangeMenuText.cs ファイルに次のコードを追加ステートメントを使用します。  
  
    ```csharp  
    using System.Security.Permissions;  
    ```  
  
3.  ChangeMenuTextPackageGuids.cs ファイルでは、次の行を追加します。  
  
    ```csharp  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4.  ChangeMenuText.cs ファイルでは、次のように ShowMessageBox メソッドのコードを置き換えます。  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5.  更新するコマンドを取得、<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>オブジェクトし、コマンド オブジェクトで、適切なプロパティを設定します。 たとえば、次のメソッドと、指定したコマンド VSPackage コマンドから利用または使用できなくなった設定なります。 という名前の項目、メニューは、次のコードは`New Text`がクリックしてされた後に使用できません。  
  
    ```csharp  
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
  
7.  **ツール** メニューのをクリックして、**呼び出す ChangeMenuText**コマンド。 コマンド名は、この時点で**呼び出す ChangeMenuText**コマンド ハンドラーは ChangeMyCommand() を呼び出していないため、します。  
  
8.  **ツール**メニューが表示されます**新しいテキスト**です。 をクリックして**新しいテキスト**です。 コマンドは今すぐグレー表示されます。  
  
## <a name="see-also"></a>参照  
 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Vspackage がユーザー インターフェイス要素を追加する方法](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [拡張メニューとコマンド](../extensibility/extending-menus-and-commands.md)   
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)