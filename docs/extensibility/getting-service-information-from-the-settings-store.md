---
title: 設定ストアからサービス情報の取得 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 11731e36517ae6245dddd1ebdd3b002fb3c37391
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127504"
---
# <a name="getting-service-information-from-the-settings-store"></a>設定ストアからサービス情報を取得します。
すべての利用可能なサービスを検索するか、特定のサービスがインストールされているかどうかを決定する設定ストアを使用することができます。 サービス クラスの種類を知る必要があります。  
  
### <a name="to-list-the-available-services"></a>使用可能なサービスを一覧表示するには  
  
1.  FindServicesExtension をという名前の VSIX プロジェクトを作成し、FindServicesCommand をという名前のカスタム コマンドを追加します。 カスタム コマンドを作成する方法の詳細については、次を参照してください[メニュー コマンドを使用して、拡張機能の作成。](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  次のコードを追加、FindServicesCommand.cs でステートメントを使用します。  
  
    ```vb  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
3.  構成設定ストアを取得し、名前付きサービス サブコレクションを検索します。 このコレクションには、使用可能なすべてのサービスが含まれています。 MenuItemCommand メソッドで、既存のコードを削除し、次のように置き換えます。  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        string message = "Available services:\n";  
        IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services");  
        int n = 0;  
        foreach (string service in collection)  
        {  
            message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n";  
        }  
  
        MessageBox.Show(message);  
    }  
    ```  
  
4.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
5.  実験用インスタンスの上、**ツール** メニューのをクリックして**呼び出す FindServicesCommand**です。  
  
     すべてのサービスを一覧表示するメッセージ ボックスが表示されます。  
  
     これらの設定を確認するには、レジストリ エディターを使用することができます。  
  
## <a name="finding-a-specific-service"></a>特定のサービスを検索します。  
 使用することも、<xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A>特定のサービスがインストールされているかどうかを調べます。 サービス クラスの種類を知る必要があります。  
  
1.  前の手順で作成したプロジェクトの MenuItemCallback で、設定の構成ストアを検索、`Services`を付けた名前に、サービスの GUID、サブコレクションを持つコレクション。 ここでは、ヘルプ サービスを見ていきます。  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper();  
        bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID);  
        string message = "Help Service Available: " + hasHelpService;  
  
        MessageBox.Show(message);  
    }  
    ```  
  
2.  プロジェクトをビルドし、デバッグを開始します。  
  
3.  実験用インスタンスの上、**ツール** メニューのをクリックして**呼び出す FindServicesCommand**です。  
  
     テキスト メッセージが表示されます**ヘルプで使用できるサービス:** 続く**True**または**False**です。 この設定を確認するには、前の手順で示すように、レジストリ エディターを使用できます。