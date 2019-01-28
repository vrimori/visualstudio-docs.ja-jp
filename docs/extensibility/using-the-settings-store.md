---
title: 設定ストアの使用 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7476208c52884f82a7277d8cbcd69208831efeb3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54944307"
---
# <a name="using-the-settings-store"></a>設定ストアの使用
設定ストアの 2 つの種類があります。  
  
- 構成設定は読み取り専用の Visual Studio および VSPackage の設定を示します。 Visual Studio では、このストアにすべての既知の .pkgdef ファイルから設定をマージします。  
  
- ユーザーの設定は、書き込み可能な設定のページに表示されるものなど、**オプション** ダイアログ ボックス、プロパティ ページ、およびその他の特定のダイアログ ボックス。 Visual Studio 拡張機能は、これらの少量のデータのローカル記憶域を使用できます。  
  
  このチュートリアルでは、構成設定ストアからデータを読み取る方法を示します。 参照してください[ユーザー設定ストアへの書き込み](../extensibility/writing-to-the-user-settings-store.md)ユーザー設定ストアに書き込む方法の詳細について。  
  
## <a name="creating-the-example-project"></a>サンプル プロジェクトを作成します。  
 このセクションでは、デモについては、メニュー コマンドを使用して単純な拡張機能プロジェクトを作成する方法を示します。  
  
1. すべての Visual Studio 拡張機能は、拡張機能資産が含まれる VSIX 配置プロジェクトで開始します。 作成、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]という名前の VSIX プロジェクト`SettingsStoreExtension`します。 VSIX プロジェクト テンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#/機能拡張**します。  
  
2. という名前のカスタム コマンド項目テンプレートを追加するようになりました**SettingsStoreCommand**します。 **新しい項目の追加**ダイアログ ボックスに移動して**Visual c#/機能拡張**選択と**カスタム コマンド**。 **名前**ウィンドウの下部にあるフィールドに、コマンド ファイル名を変更して**SettingsStoreCommand.cs**します。 カスタム コマンドを作成する方法の詳細については、次を参照してください[メニュー コマンドを使用して拡張機能の作成。](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## <a name="using-the-configuration-settings-store"></a>構成設定ストアの使用  
 このセクションでは、検出し、構成設定を表示する方法を示します。  
  
1. 次の追加、SettingsStorageCommand.cs ファイルでステートメントを使用します。  
  
   ```  
   using System.Collections.Generic;  
   using Microsoft.VisualStudio.Settings;  
   using Microsoft.VisualStudio.Shell.Settings;  
   using System.Windows.Forms;  
   ```  
  
2. `MenuItemCallback`構成設定のストアを取得する次の行を追加、削除、メソッドの本体。  
  
   ```  
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
   ```  
  
    <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager>マネージ ヘルパー クラスを経由では、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager>サービス。  
  
3. Windows Phone ツールがインストールされているかどうかを調べるようになりました。 コードは、次のようになります。  
  
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
  
4. コードをテストします。 プロジェクトをビルドし、デバッグを開始します。  
  
5. 実験用インスタンスでは、上、**ツール** メニューのをクリックして**呼び出す SettingsStoreCommand**します。  
  
    メッセージ ボックスというを表示する必要があります**Microsoft Windows Phone Developer Tools:** 続けて**True**または**False**します。  
  
   Visual Studio では、システム レジストリに設定ストアを保持します。  
  
#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>レジストリ エディターを使用して、構成設定を確認するには  
  
1.  Regedit.exe を開きます。  
  
2.  HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts に移動します\\します。  
  
    > [!NOTE]
    >  \14.0Exp_Config\ といない \14.0_Config を含むキーを検索するかどうかを確認\\します。 Visual Studio の実験用インスタンスを実行すると、構成設定はレジストリ ハイブ"14.0Exp_Config"です。  
  
3.  \Installed Products\ ノードを展開します。 前の手順でメッセージがある場合**Microsoft Windows Phone 開発者ツールをインストールします。True**、\Installed Products\ 場合に、Microsoft Windows Phone Developer Tools ノードが含まれている必要があります。 メッセージが場合**Microsoft Windows Phone 開発者ツールをインストールします。False**、し \Installed Products\ は Microsoft Windows Phone Developer Tools ノードを含めることはできません。