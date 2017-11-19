---
title: "設定ストアを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f1d62e3ccc47a2b74629cd1468b023c787a1289e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="using-the-settings-store"></a>設定ストアを使用します。
2 つの種類の設定ストアがあります。  
  
-   構成設定は読み取り専用の Visual Studio と VSPackage の設定があります。 Visual Studio では、このストアにすべての既知の .pkgdef ファイルから設定をマージします。  
  
-   ユーザーの設定は、書き込み可能な設定のページに表示されるものなど、**オプション** ダイアログ ボックス、プロパティ ページ、およびその他の特定のダイアログ ボックス。 Visual Studio 拡張機能は、これらの少量のデータのローカル記憶域を使用して可能性があります。  
  
 このチュートリアルでは、構成設定ストアからデータを読み取る方法を示します。 参照してください[ユーザー設定ストアへの書き込み](../extensibility/writing-to-the-user-settings-store.md)については、ユーザー設定ストアに書き込む方法です。  
  
## <a name="creating-the-example-project"></a>サンプル プロジェクトを作成します。  
 このセクションでは、デモについては、メニュー コマンドを使用して簡単な拡張機能プロジェクトを作成する方法を示します。  
  
1.  すべての Visual Studio 拡張機能は、資産を拡張機能を含んでいる VSIX 配置プロジェクトを開始します。 作成、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]という名前の VSIX プロジェクト`SettingsStoreExtension`です。 VSIX プロジェクトのテンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#/機能拡張**です。  
  
2.  という名前のカスタム コマンド項目テンプレートを追加するようになりました**SettingsStoreCommand**です。 **新しい項目の追加**ダイアログ ボックスに移動して**Visual c#/機能拡張**選択と**にカスタム コマンド**です。 **名前**ウィンドウの下部にあるフィールドに、コマンド ファイルの名前を変更する**SettingsStoreCommand.cs**です。 カスタム コマンドを作成する方法の詳細については、次を参照してください[メニュー コマンドを使用して、拡張機能の作成。](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## <a name="using-the-configuration-settings-store"></a>構成設定ストアを使用します。  
 このセクションでは、検出され、構成設定を表示する方法を示します。  
  
1.  次のコードを追加、SettingsStorageCommand.cs ファイルでステートメントを使用します。  
  
    ```  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
2.  `MenuItemCallback`メソッドの本体を削除して、これらの行を取得、構成設定ストアを追加します。  
  
    ```  
    SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
    SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager>マネージ ヘルパー クラスを経由では、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager>サービス。  
  
3.  Windows Phone ツールがインストールされているかどうかを調べるようになりました。 コードは、次のようになります。  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools");  
        string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled;  
        MessageBox.Show(message);  
    }  
    ```  
  
4.  コードをテストします。 プロジェクトをビルドし、デバッグを開始します。  
  
5.  実験用インスタンスの上、**ツール** メニューのをクリックして**呼び出す SettingsStoreCommand**です。  
  
     示すメッセージ ボックスが表示されるはず**Microsoft Windows Phone 開発者ツール:**続く**True**または**False**です。  
  
 Visual Studio では、システム レジストリの設定ストアを保存します。  
  
#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>レジストリ エディターを使用して、構成設定を確認するには  
  
1.  Regedit.exe を開きます。  
  
2.  HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts に移動\\です。  
  
    > [!NOTE]
    >  \14.0Exp_Config\ といない \14.0_Config を含むキーで検索するかどうかを確認\\です。 Visual Studio の実験用インスタンスを実行すると、構成設定はレジストリ ハイブ"14.0Exp_Config"です。  
  
3.  \Installed Products\ ノードを展開します。 前の手順でメッセージがある場合**Microsoft Windows Phone 開発者ツールをインストールします。 True**、\Installed Products\ 場合に、Microsoft Windows Phone 開発者ツール ノードが含まれている必要があります。 場合は、メッセージが**Microsoft Windows Phone 開発者ツールをインストールします。 False**、\Installed Products\ は Microsoft Windows Phone 開発者ツールのノードを含めることはできませんし、します。