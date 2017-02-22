---
title: "方法: ClickOnce 信頼プロンプトの動作を構成する | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce アプリケーション, プロンプトを表示せずにインストール"
  - "ClickOnce アプリケーション, 信頼プロンプト"
  - "ClickOnce 配置, プロンプトを表示せずにインストール"
  - "ClickOnce 配置, 信頼プロンプト"
  - "配置 (アプリケーションを) [ClickOnce], 信頼プロンプト"
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法: ClickOnce 信頼プロンプトの動作を構成する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ClickOnce 信頼プロンプトを構成して、エンド ユーザーに ClickOnce アプリケーションのインストール オプションを表示するかどうかを制御できます。たとえば、Windows フォーム アプリケーション、Windows Presentation Foundation アプリケーション、コンソール アプリケーション、WPF ブラウザー アプリケーション、Office ソリューションなどのアプリケーションです。  信頼プロンプトを構成するには、各エンド ユーザーのコンピューターでレジストリ キーを設定します。  
  
 次の表は、5 つのゾーン \(Internet、UntrustedSites、MyComputer、LocalIntranet、および TrustedSites\) にそれぞれ適用できる構成オプションを示しています。  
  
|オプション|レジストリの設定値|Description|  
|-----------|---------------|-----------------|  
|信頼プロンプトを有効にする。|`Enabled`|ClickOnce 信頼プロンプトを表示して、エンド ユーザーが ClickOnce アプリケーションへの信頼を許可できるようにします。|  
|信頼プロンプトを制限する。|`AuthenticodeRequired`|ClickOnce 信頼プロンプトは、ClickOnce アプリケーションが発行者を特定する証明書で署名されている場合にのみ表示されます。|  
|信頼プロンプトを無効にする。|`Disabled`|ClickOnce 信頼プロンプトは、明示的に信頼されている証明書で署名されていない ClickOnce アプリケーションの場合には表示されません。|  
  
 各ゾーンの既定の動作を次の表に示します。  アプリケーション列は、Windows フォーム アプリケーション、Windows Presentation Foundation アプリケーション、WPF ブラウザー アプリケーション、およびコンソール アプリケーションを意味します。  
  
|ゾーン|Applications|Office ソリューション|  
|---------|------------------|--------------------|  
|`MyComputer`|`Enabled`|`Enabled`|  
|`ローカル イントラネット`|`Enabled`|`Enabled`|  
|`TrustedSites`|`Enabled`|`Enabled`|  
|`インターネット`|`Enabled`|`AuthenticodeRequired`|  
|`UntrustedSites`|`Disabled`|`Disabled`|  
  
 ClickOnce 信頼プロンプトを有効、制限、または無効にすることで、これらの設定をオーバーライドできます。  
  
## ClickOnce 信頼プロンプトの有効化  
 あるゾーンに属する ClickOnce アプリケーションをエンド ユーザーがインストールして実行できるようにするには、そのゾーンの信頼プロンプトを有効にします。  
  
#### レジストリ エディターを使用して ClickOnce 信頼プロンプトを有効にするには  
  
1.  レジストリ エディターを開きます。  
  
    1.  **\[スタート\]** ボタンをクリックし、**\[ファイル名を指定して実行\]** をクリックします。  
  
    2.  **\[名前\]** ボックスに「`regedit32`」と入力し、**\[OK\]** をクリックします。  
  
2.  次のレジストリ キーを探します。  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     このキーが存在しない場合は作成します。  
  
3.  次のサブキーが存在しない場合は、**文字列値**として追加し、次の表に示すような関連する値を指定します。  
  
    |文字列値サブキー|値|  
    |--------------|-------|  
    |`インターネット`|`Enabled`|  
    |`UntrustedSites`|`Disabled`|  
    |`MyComputer`|`Enabled`|  
    |`ローカル イントラネット`|`Enabled`|  
    |`TrustedSites`|`Enabled`|  
  
     Office ソリューションの場合は、`Internet` の既定値は `AuthenticodeRequired`、`UntrustedSites` の既定値は `Disabled` です。  その他のソリューションの場合、`Internet` の既定値は `Enabled` です。  
  
#### ClickOnce 信頼プロンプトをプログラムによって有効にするには  
  
1.  Visual Studio で Visual Basic または Visual C\# のコンソール アプリケーションを作成します。  
  
2.  Program.vb ファイルまたは Program.cs ファイルを編集用に開き、次のコードを追加します。  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "Enabled")  
    key.SetValue("TrustedSites", "Enabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Enabled");  
    key.SetValue("LocalIntranet", "Enabled");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "Enabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  アプリケーションをビルドして実行します。  
  
## ClickOnce 信頼プロンプトの制限  
 信頼プロンプトを制限すると、ユーザーに信頼するかどうかの確認を求める前に、既知の ID を持つ Authenticode 証明書でソリューションの署名が必要になります。  
  
#### レジストリ エディターを使用して ClickOnce 信頼プロンプトを制限するには  
  
1.  レジストリ エディターを開きます。  
  
    1.  **\[スタート\]** ボタンをクリックし、**\[ファイル名を指定して実行\]** をクリックします。  
  
    2.  **\[名前\]** ボックスに「`regedit`」と入力し、**\[OK\]** をクリックします。  
  
2.  次のレジストリ キーを探します。  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     このキーが存在しない場合は作成します。  
  
3.  次のサブキーが存在しない場合は、**文字列値**として追加し、次の表に示すような関連する値を指定します。  
  
    |文字列値サブキー|値|  
    |--------------|-------|  
    |`UntrustedSites`|`Disabled`|  
    |`インターネット`|`AuthenticodeRequired`|  
    |`MyComputer`|`AuthenticodeRequired`|  
    |`ローカル イントラネット`|`AuthenticodeRequired`|  
    |`TrustedSites`|`AuthenticodeRequired`|  
  
#### ClickOnce 信頼プロンプトをプログラムによって制限するには  
  
1.  Visual Studio で Visual Basic または Visual C\# のコンソール アプリケーションを作成します。  
  
2.  Program.vb ファイルまたは Program.cs ファイルを編集用に開き、次のコードを追加します。  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "AuthenticodeRequired")  
    key.SetValue("LocalIntranet", "AuthenticodeRequired")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "AuthenticodeRequired")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "AuthenticodeRequired");  
    key.SetValue("LocalIntranet", "AuthenticodeRequired");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "AuthenticodeRequired");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  アプリケーションをビルドして実行します。  
  
## ClickOnce 信頼プロンプトの無効化  
 セキュリティ ポリシーで信頼されていないソリューションをエンド ユーザーがインストールできないようにするには、信頼プロンプトを無効にします。  
  
#### レジストリ エディターを使用して ClickOnce 信頼プロンプトを無効にするには  
  
1.  レジストリ エディターを開きます。  
  
    1.  **\[スタート\]** ボタンをクリックし、**\[ファイル名を指定して実行\]** をクリックします。  
  
    2.  **\[名前\]** ボックスに「`regedit`」と入力し、**\[OK\]** をクリックします。  
  
2.  次のレジストリ キーを探します。  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     このキーが存在しない場合は作成します。  
  
3.  次のサブキーが存在しない場合は、**文字列値**として追加し、次の表に示すような関連する値を指定します。  
  
    |文字列値サブキー|値|  
    |--------------|-------|  
    |`UntrustedSites`|`Disabled`|  
    |`インターネット`|`Disabled`|  
    |`MyComputer`|`Disabled`|  
    |`ローカル イントラネット`|`Disabled`|  
    |`TrustedSites`|`Disabled`|  
  
#### ClickOnce 信頼プロンプトをプログラムによって無効にするには  
  
1.  Visual Studio で Visual Basic または Visual C\# のコンソール アプリケーションを作成します。  
  
2.  Program.vb ファイルまたは Program.cs ファイルを編集用に開き、次のコードを追加します。  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Disabled")  
    key.SetValue("LocalIntranet", "Disabled")  
    key.SetValue("Internet", "Disabled")  
    key.SetValue("TrustedSites", "Disabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Disabled");  
    key.SetValue("LocalIntranet", "Disabled");  
    key.SetValue("Internet", "Disabled");  
    key.SetValue("TrustedSites", "Disabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
  
    ```  
  
3.  アプリケーションをビルドして実行します。  
  
## 参照  
 [ClickOnce アプリケーションのセキュリティ](../deployment/securing-clickonce-applications.md)   
 [ClickOnce アプリケーションのコード アクセス セキュリティ](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce と Authenticode](../deployment/clickonce-and-authenticode.md)   
 [信頼されたアプリケーションの配置の概要](../deployment/trusted-application-deployment-overview.md)   
 [方法 : ClickOnce のセキュリティ設定を有効にする](../deployment/how-to-enable-clickonce-security-settings.md)   
 [方法 : ClickOnce アプリケーションのセキュリティ ゾーンを設定する](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [方法 : ClickOnce アプリケーションのカスタム アクセス許可を設定する](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [方法 : アクセス許可が制限された ClickOnce アプリケーションをデバッグする](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [方法: ClickOnce アプリケーション用の信頼された発行者をクライアント コンピューターに追加する](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [方法: アプリケーション マニフェストおよび配置マニフェストに再署名する](../deployment/how-to-re-sign-application-and-deployment-manifests.md)