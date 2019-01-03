---
title: 設定ストアからサービス情報の取得 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: decb5edb3e0cc243bacd3be0beda8aba621e8af2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53874473"
---
# <a name="get-service-information-from-the-settings-store"></a>設定ストアからサービス情報を取得します。
設定ストアを使用するには、すべての利用可能なサービスを検索するかを特定のサービスがインストールされているかどうかを判断します。 サービス クラスの型が必要です。  
  
## <a name="to-list-the-available-services"></a>利用可能なサービスを一覧表示するには  
  
1.  という名前の VSIX プロジェクトを作成する`FindServicesExtension`という名前のカスタム コマンドを追加し`FindServicesCommand`します。 カスタム コマンドを作成する方法の詳細については、次を参照してください[メニュー コマンドを使用して拡張機能を作成します。](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  *FindServicesCommand.cs*次を追加するステートメントを使用します。  
  
    ```vb  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
3.  構成設定ストアを取得し、名前付きサービス、サブコレクションを検索します。 このコレクションには、利用可能なすべてのサービスが含まれています。 `MenuItemCommand`方法を既存のコードを削除して、次に置き換えます。  
  
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
  
5.  実験用インスタンスでは、上、**ツール** メニューのをクリックして**呼び出す FindServicesCommand**します。  
  
     すべてのサービスを一覧表示するメッセージ ボックスが表示されます。  
  
     これらの設定を確認するには、レジストリ エディターを使用することができます。  
  
## <a name="find-a-specific-service"></a>特定のサービスを検索します。  
 使用することも、<xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A>する特定のサービスがインストールされているかどうかを判断するメソッド。 サービス クラスの型が必要です。  
  
1.  前の手順で作成したプロジェクトの MenuItemCallback での構成設定ストアを検索、`Services`という名前のサービスの GUID でサブコレクションを含むコレクション。 この場合、ヘルプ サービスを見ていきます。  
  
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
  
3.  実験用インスタンスでは、上、**ツール** メニューのをクリックして**呼び出す FindServicesCommand**します。  
  
     テキスト メッセージが表示する必要があります**使用できるサービスのヘルプ:** 続けて**True**または**False**します。 この設定を確認するには、前の手順で示すように、レジストリ エディターを使用できます。