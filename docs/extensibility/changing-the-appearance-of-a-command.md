---
title: コマンドの外観を変更する |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa212ec1c01a19668cafd951ea5defe5383b17ed
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232245"
---
# <a name="change-the-appearance-of-a-command"></a>コマンドの外観を変更します。
コマンドの外観を変更することで、ユーザーにフィードバックを提供できます。 たとえば、ご利用いただけませんが異なって表示するコマンドをたい場合があります。 非ことができますコマンドを使用できないか使用できないこと、または、それらを表示するまたは確認メニューでそれらをオフにします。  
  
 コマンドの外観を変更するには、これらの操作を実行します。  
  
-   コマンド テーブルのファイルでコマンドの定義では、適切なフラグを指定します。  
  
-   使用して、<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>サービス。  
  
-   実装、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスおよび生のコマンド オブジェクトを変更します。  
  
 次の手順では、検索およびマネージ パッケージ フレームワーク (MPF) を使用して、コマンドの外観を更新する方法を示します。  
  
### <a name="to-change-the-appearance-of-a-menu-command"></a>メニュー コマンドの外観を変更するには  
  
1.  指示に従って[メニュー コマンドのテキストを変更する](../extensibility/changing-the-text-of-a-menu-command.md)という名前のメニュー項目を作成する`New Text`します。  
  
2.  *ChangeMenuText.cs*ファイルに追加し、次のステートメントを使用します。  
  
    ```csharp  
    using System.Security.Permissions;  
    ```  
  
3.  *ChangeMenuTextPackageGuids.cs*ファイルに、次の行を追加します。  
  
    ```csharp  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4.  *ChangeMenuText.cs*ファイルで、次の ShowMessageBox メソッドのコードに置き換えます。  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5.  更新するコマンドを取得、<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>オブジェクトし、コマンド オブジェクトで、適切なプロパティを設定します。 たとえば、次のメソッドは、使用または使用できない設定 VSPackage のコマンドから、指定したコマンドです。 次のコードでという名前の項目] メニューの [`New Text`がクリックしてされた後に使用できません。  
  
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
  
7.  **ツール** メニューのをクリックして、**呼び出す ChangeMenuText**コマンド。 コマンド名は、この時点で**呼び出す ChangeMenuText**コマンド ハンドラーを呼び出さないため、 **ChangeMyCommand()** します。  
  
8.  **ツール**メニューが表示**新しいテキスト**します。 クリックして**新しいテキスト**します。 コマンドを灰色に今すぐ必要があります。  
  
## <a name="see-also"></a>関連項目  
 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Vspackage がユーザー インターフェイス要素を追加する方法](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [拡張メニューとコマンド](../extensibility/extending-menus-and-commands.md)   
 [Visual Studio コマンド テーブル (します。Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)