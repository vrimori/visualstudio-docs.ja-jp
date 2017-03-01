---
title: "ユーザー設定ストアへの書き込み |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 35ca397d57906a6316543325a08b118613fc2035
ms.lasthandoff: 02/22/2017

---
# <a name="writing-to-the-user-settings-store"></a>ユーザー設定ストアへの書き込み
ユーザー設定が含まれていないような書き込み可能な設定、**ツール/オプション**ダイアログで、[プロパティ] ウィンドウ、およびその他の特定のダイアログ ボックス。 Visual Studio 拡張機能は、少量のデータの格納にこれらを使用できます。 このチュートリアルでは、ユーザー設定ストアへの書き込みから読み取りを外部ツールとして Visual Studio をメモ帳を追加する方法を示します。  
  
### <a name="backing-up-your-user-settings"></a>お客様のユーザー設定のバックアップ  
  
1.  デバッグし、手順を繰り返してとなるように、外部ツールの設定をリセットできる必要があります。 これを行うには、必要に応じてに復元できるように、元の設定を保存する必要があります。  
  
2.  Regedit.exe を開きます。  
  
3.  HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External ツールに移動\\します。  
  
    > [!NOTE]
    >  \14.0Exp\ といない \14.0 を含むキーを検索するかどうかを確認\\します。 Visual Studio の実験用インスタンスを実行すると、ユーザーの設定はレジストリ ハイブ"14.0Exp"にです。  
  
4.  \External Tools\ サブキーを右クリックし、**エクスポート**します。 確認して**選択された部分**が選択されています。  
  
5.  結果として得られる外部 Tools.reg ファイルを保存します。  
  
6.  その後、外部ツールの設定をリセットするには、HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External \ のレジストリ キーを選択し、クリックして**削除**コンテキスト メニューです。  
  
7.  ときに、**キーの削除の確認**をクリックしてダイアログ ボックスが表示されたら、**はい**します。  
  
8.  以前に保存した外部 Tools.reg ファイルを右クリックし、をクリックして**プログラムから開く**、クリックして**レジストリ エディター**します。  
  
## <a name="writing-to-the-user-settings-store"></a>ユーザー設定ストアへの書き込み  
  
1.  UserSettingsStoreExtension をという名前の VSIX プロジェクトを作成し、UserSettingsStoreCommand という名前のカスタム コマンドを追加します。 カスタム コマンドを作成する方法の詳細については、次を参照してください[メニュー コマンドを使用して拡張機能の作成。](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  次のコードを追加、UserSettingsStoreCommand.cs でステートメントを使用します。  
  
    ```c#  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3.  MenuItemCallback でメソッドの本体を削除し、設定の保存、次のようにユーザーを取得します。  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
    }  
    ```  
  
4.  ここでは、メモ帳は、外部ツールとして既に設定されているかどうかを確認します。 ToolCmd 設定が"Notepad"を次のようがあるかどうかを判断するすべての外部ツールを反復処理する必要があります。  
  
    ```c#  
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
  
5.  メモ帳が、外部ツールとして設定されていない場合は、次のように設定します。  
  
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
  
6.  コードをテストします。 あるとして追加され、メモ帳、外部ツールをロールバックしなければならない、レジストリをもう一度実行する前に、注意してください。  
  
7.  コードをビルドしてデバッグを開始します。  
  
8.  **ツール** メニューのをクリックして**呼び出す UserSettingsStoreCommand**します。 これにより、メモ帳を追加、**ツール**メニュー。  
  
9. メモ帳をツールに表示されます、オプション メニューをクリックして**メモ帳**メモ帳のインスタンスを表示する必要があります。
