---
title: ユーザー設定ストアへの書き込み |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0e205fa8850bdd5ee664f66c6d6bb7bf86195bfd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="writing-to-the-user-settings-store"></a>ユーザー設定ストアへの書き込み
ユーザー設定でのような書き込み可能な設定、**ツール/オプション**ダイアログ、プロパティ ウィンドウ、およびその他の特定のダイアログ ボックス。 Visual Studio 拡張機能は、これらを使用少量のデータを格納するのにことがあります。 このチュートリアルでは、ユーザー設定ストアへの書き込みから読み取りを外部ツールとしてメモ帳を Visual Studio に追加する方法を示します。  
  
### <a name="backing-up-your-user-settings"></a>自分のユーザー設定のバックアップ  
  
1.  デバッグし、手順を繰り返して可能となるように、外部ツールの設定をリセットする必要があります。 これを行うには、必要に応じてそれらを復元できるように、元の設定を保存する必要があります。  
  
2.  Regedit.exe を開きます。  
  
3.  HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External ツールに移動\\です。  
  
    > [!NOTE]
    >  \14.0Exp\ といない \14.0 を含むキーで検索するかどうかを確認\\です。 Visual Studio の実験用インスタンスを実行すると、ユーザーの設定は、レジストリ ハイブ"14.0Exp"でです。  
  
4.  \External Tools\ サブキーを右クリックし、をクリックして**エクスポート**です。 確認して**選択されたブランチ**が選択されています。  
  
5.  結果として得られる外部 Tools.reg ファイルを保存します。  
  
6.  後で、外部ツールの設定をリセットするには、HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External tools \ のレジストリ キーを選択し、をクリックして**削除**コンテキスト メニューの します。  
  
7.  ときに、**キーの削除の確認** ダイアログ ボックスが表示されたら、をクリックして**はい**です。  
  
8.  以前に保存した外部 Tools.reg ファイルを右クリックし、をクリックして**で開く**、クリックして**レジストリ エディター**です。  
  
## <a name="writing-to-the-user-settings-store"></a>ユーザー設定ストアへの書き込み  
  
1.  UserSettingsStoreExtension をという名前の VSIX プロジェクトを作成し、UserSettingsStoreCommand をという名前のカスタム コマンドを追加します。 カスタム コマンドを作成する方法の詳細については、次を参照してください[メニュー コマンドを使用して、拡張機能の作成。](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  次のコードを追加、UserSettingsStoreCommand.cs でステートメントを使用します。  
  
    ```csharp  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3.  MenuItemCallback では、メソッドの本体を削除し、設定を保存、次のようにユーザーを取得します。  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
    }  
    ```  
  
4.  メモ帳は、外部ツールとして既に設定されているかどうかを調べるようになりました。 ToolCmd 設定は、次のように"Notepad"をかどうかを決定するすべての外部ツールを反復処理する必要があります。  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
  
        // Find out whether Notepad is already an External Tool.  
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");  
        bool hasNotepad = false;  
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;  
        for (int i = 0; i < toolCount; i++)  
        {  
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)  
            {  
                hasNotepad = true;  
                break;  
            }  
        }  
    }  
  
    ```  
  
5.  メモ帳が外部ツールとして設定されていない場合は、よう設定します。  
  
    ```vb  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
  
        // Find out whether Notepad is already installed.  
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");  
        bool hasNotepad = false;  
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;  
        for (int i = 0; i < toolCount; i++)  
        {  
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)  
            {  
                hasNotepad = true;  
                break;  
            }  
        }  
  
        string message = (hasNotepad) ? "Notepad already installed" : "Installing Notepad";  
         if (!hasNotepad)  
        {  
            userSettingsStore.SetString("External Tools", "ToolTitle" + toolCount, "&Notepad");  
            userSettingsStore.SetString("External Tools", "ToolCmd" + toolCount, "C:\\Windows\\notepad.exe");  
            userSettingsStore.SetString("External Tools", "ToolArg" + toolCount, "");  
            userSettingsStore.SetString("External Tools", "ToolDir" + toolCount, "$(ProjectDir)");  
            userSettingsStore.SetString("External Tools", "ToolSourceKey" + toolCount, "");  
            userSettingsStore.SetUInt32("External Tools", "ToolOpt" + toolCount, 0x00000011);  
  
            userSettingsStore.SetInt32("External Tools", "ToolNumKeys", toolCount + 1);  
        }  
    }  
    ```  
  
6.  コードをテストします。 追加するメモ帳、外部ツールとしてロールバックしなければならない、レジストリをもう一度実行する前にので注意してください。  
  
7.  コードをビルドし、デバッグを開始します。  
  
8.  **ツール** メニューのをクリックして**呼び出す UserSettingsStoreCommand**です。 メモ帳に追加されます、**ツール**メニュー。  
  
9. これで、メモ帳をツールに表示されます]/[オプション] メニューの [クリックして**メモ帳**メモ帳のインスタンスを表示する必要があります。