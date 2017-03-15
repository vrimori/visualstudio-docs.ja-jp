---
title: "設定ストアを使用します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "設定ストアを使用します。"
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# 設定ストアを使用します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

設定ストアの 2 つの種類があります。  
  
-   構成設定には、Visual Studio と VSPackage 設定は読み取り専用です。 Visual Studio では、このストアにすべての既知の .pkgdef ファイルから設定をマージします。  
  
-   ユーザーの設定は、書き込み可能な設定のページに表示されるよう、 **オプション** \] ダイアログ ボックス、プロパティ ページ、およびその他の特定のダイアログ ボックス。 Visual Studio 拡張機能には、これらの少量のデータのローカル記憶域を使用できます。  
  
 このチュートリアルでは、構成設定ストアからデータを読み取る方法を示します。 参照してください [ユーザー設定ストアへの書き込み](../extensibility/writing-to-the-user-settings-store.md) ユーザー設定ストアに書き込む方法の詳細についてです。  
  
## サンプル プロジェクトを作成します。  
 このセクションでは、デモでは、メニュー コマンドを使用して簡単な拡張機能プロジェクトを作成する方法を示します。  
  
1.  すべての Visual Studio 拡張機能は、拡張機能の資産を格納する VSIX 配置プロジェクトから開始します。 作成、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] という名前の VSIX プロジェクト `SettingsStoreExtension`します。 VSIX プロジェクトのテンプレートを見つけることができます、 **新しいプロジェクト** \] ダイアログ ボックス \[ **Visual c\#\/機能拡張**します。  
  
2.  という名前のカスタム コマンド項目テンプレートを今すぐ追加 **SettingsStoreCommand**します。**新しい項目の追加** ダイアログ ボックスに移動 **Visual c\#\/機能拡張** を選択して **にカスタム コマンド**します。**名** ウィンドウの下部にあるフィールドに、コマンド ファイルの名前を変更する **SettingsStoreCommand.cs**します。 カスタム コマンドを作成する方法の詳細については、次を参照してください。 [メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## 構成設定ストアを使用します。  
 このセクションでは、検出され、構成設定を表示する方法を示します。  
  
1.  SettingsStorageCommand.cs ファイルに次のコードを追加ステートメントを使用します。  
  
    ```  
    using System.Collections.Generic; using Microsoft.VisualStudio.Settings; using Microsoft.VisualStudio.Shell.Settings; using System.Windows.Forms;  
    ```  
  
2.  `MenuItemCallback`, 、メソッドの本体を削除、およびこれらの行を取得、構成設定ストアを追加します。  
  
    ```  
    SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> 経由で管理対象のヘルパー クラスであり、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> サービスです。  
  
3.  ここでは、Windows Phone のツールがインストールされているかどうかを探します。 コードは、次のようになります。  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration); bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools"); string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled; MessageBox.Show(message); }  
    ```  
  
4.  コードをテストします。 プロジェクトをビルドし、デバッグを開始します。  
  
5.  実験用インスタンスで、 **ツール** \] メニューのをクリックして **呼び出す SettingsStoreCommand**します。  
  
     示すメッセージ ボックスが表示されます **Microsoft Windows Phone Developer Tools:**  続けて **True** または **False**します。  
  
 Visual Studio では、システム レジストリの設定ストアを保持します。  
  
#### レジストリ エディターを使用して、構成設定を確認するには  
  
1.  Regedit.exe を開きます。  
  
2.  HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0Exp\_Config\\InstalledProducts\\ に移動します。  
  
    > [!NOTE]
    >  \\14.0Exp\_Config\\ といない \\14.0\_Config\\ を含むキーを見ていることを確認します。 Visual Studio の実験用インスタンスを実行すると、構成設定はレジストリ ハイブ"14.0Exp\_Config"です。  
  
3.  \\Installed Products\\ ノードを展開します。 前の手順でメッセージがある場合 **Microsoft Windows Phone 開発者ツールをインストールします。 True**, 、\\Installed Products\\ には、Microsoft Windows Phone Developer Tools ノードが含まれている必要があります。 メッセージの場合 **Microsoft Windows Phone 開発者ツールをインストールします。 False**, 、\\Installed Products\\ は Microsoft Windows Phone Developer Tools ノードを含めることはできませんし、します。