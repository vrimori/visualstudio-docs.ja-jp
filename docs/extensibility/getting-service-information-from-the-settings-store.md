---
title: "設定ストアからサービス情報の取得 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# 設定ストアからサービス情報の取得
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

設定ストアを使用するには、すべての利用可能なサービスを検索するかを特定のサービスがインストールされているかどうかを確認します。 サービス クラスの型を確認する必要があります。  
  
### 使用可能なサービスを一覧表示するには  
  
1.  FindServicesExtension をという名前の VSIX プロジェクトを作成し、FindServicesCommand という名前のカスタム コマンドを追加します。 カスタム コマンドを作成する方法の詳細については、次を参照してください。 [メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  次のコードを追加、FindServicesCommand.cs でステートメントを使用します。  
  
    ```vb  
    using System.Collections.Generic; using Microsoft.VisualStudio.Settings; using Microsoft.VisualStudio.Shell.Settings; using System.Windows.Forms;  
    ```  
  
3.  構成設定ストアを取得し、名前付きサービス サブコレクションを検索します。 このコレクションには、使用可能なすべてのサービスが含まれています。 MenuItemCommand メソッドでは、既存のコードを削除し、次のように置き換えます。  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration); string message = "Available services:\n"; IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services"); int n = 0; foreach (string service in collection) { message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n"; } MessageBox.Show(message); }  
    ```  
  
4.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
5.  実験用インスタンスで、 **ツール** \] メニューのをクリックして **呼び出す FindServicesCommand**します。  
  
     すべてのサービスを一覧表示するメッセージ ボックスが表示されます。  
  
     これらの設定を確認するには、レジストリ エディターを使用することができます。  
  
## 特定のサービスを検索します。  
 使用することも、 <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> 特定のサービスがインストールされているかどうかを決定する方法です。 サービス クラスの型を確認する必要があります。  
  
1.  前の手順で作成したプロジェクトの MenuItemCallback での構成設定ストアを検索、 `Services` サブコレクションを付けた名前に、サービスの GUID を持つコレクションです。 ここで、ヘルプのサービスを見ていきます。  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration); string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper(); bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID); string message = "Help Service Available: " + hasHelpService; MessageBox.Show(message); }  
    ```  
  
2.  プロジェクトをビルドし、デバッグを開始します。  
  
3.  実験用インスタンスで、 **ツール** \] メニューのをクリックして **呼び出す FindServicesCommand**します。  
  
     テキスト メッセージが表示 **利用できるサービスのヘルプ:**  続けて **True** または **False**します。 この設定を確認するには、前の手順で示すように、レジストリ エディターを使用できます。