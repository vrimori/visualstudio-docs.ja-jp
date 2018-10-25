---
title: ユーザー設定ストアへの書き込み |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 90d34ebf751ee62fd7779a92214f42779cf84b59
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49202047"
---
# <a name="writing-to-the-user-settings-store"></a>ユーザー設定ストアへの書き込み
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ユーザーの設定は、書き込み可能の設定で使用されているように、**ツール/オプション**ダイアログ、[プロパティ] ウィンドウ、およびその他の特定のダイアログ ボックス。 Visual Studio 拡張機能は、これらを使用少量のデータを格納するのにことがあります。 このチュートリアルでは、ユーザー設定ストアへの書き込みから読み取りによって、外部ツールとして Visual Studio をメモ帳を追加する方法を示します。  
  
### <a name="backing-up-your-user-settings"></a>お客様のユーザー設定のバックアップ  
  
1.  デバッグし、手順を使用できるように、外部ツールの設定をリセットする必要があります。 これを行うには、必要に応じてに復元できるように、元の設定を保存する必要があります。  
  
2.  Regedit.exe を開きます。  
  
3.  HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External ツールに移動します\\します。  
  
    > [!NOTE]
    >  \14.0Exp\ といない \14.0 を含むキーを検索するかどうかを確認\\します。 Visual Studio の実験用インスタンスを実行すると、ユーザーの設定はレジストリ ハイブ"14.0Exp"では。  
  
4.  \External Tools\ のサブキーを右クリックし、をクリックし、**エクスポート**します。 必ず**選択されたブランチ**が選択されています。  
  
5.  結果として得られる外部 Tools.reg ファイルを保存します。  
  
6.  その後、外部ツールの設定をリセットするには、HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External tools \ のレジストリ キーを選択し、をクリックして**削除**コンテキスト メニュー。  
  
7.  ときに、**キーの削除の確認** ダイアログ ボックスが表示されたら、をクリックして**はい**します。  
  
8.  以前に保存する外部 Tools.reg ファイルを右クリックし、をクリックして**プログラムから開く**、 をクリックし、**レジストリ エディター**します。  
  
## <a name="writing-to-the-user-settings-store"></a>ユーザー設定ストアへの書き込み  
  
1.  UserSettingsStoreExtension をという名前の VSIX プロジェクトを作成し、UserSettingsStoreCommand をという名前のカスタム コマンドを追加します。 カスタム コマンドを作成する方法の詳細については、次を参照してください[メニュー コマンドを使用して拡張機能の作成。](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  UserSettingsStoreCommand.cs で、次のコードを追加ステートメントを使用します。  
  
    ```csharp  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3.  MenuItemCallback では、メソッドの本体を削除し、設定の保存、次のようにユーザーを取得します。  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
    }  
    ```  
  
4.  メモ帳は、外部ツールとして既に設定されているかどうかを調べるようになりました。 ToolCmd 設定が"Notepad"を次のようがあるかどうかを判断するすべての外部ツールを反復処理する必要があります。  
  
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
  
5.  メモ帳が外部のツールとして設定されていない場合は、次のように設定します。  
  
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
  
6.  コードをテストします。 ロールバックしなければならない、レジストリをもう一度実行する前にように、外部のツールとしてメモ帳を追加、ことに注意してください。  
  
7.  コードをビルドし、デバッグを開始します。  
  
8.  **ツール** メニューのをクリックして**呼び出す UserSettingsStoreCommand**します。 これをメモ帳に追加されます、**ツール**メニュー。  
  
9. ツールで、メモ帳を表示する必要があります]/[オプション] メニューの [クリックして**メモ帳**メモ帳のインスタンスを起動する必要があります。

