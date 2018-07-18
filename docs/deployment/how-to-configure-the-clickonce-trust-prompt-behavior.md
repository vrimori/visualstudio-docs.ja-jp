---
title: '方法: ClickOnce 信頼プロンプトの動作の構成 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- deploying applications [ClickOnce], trust prompt
- ClickOnce applications, install without prompting
- ClickOnce applications, trust prompt
- ClickOnce deployment, trust prompt
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d37e5fa465a5e19b1bfb7577f6ab06c61782f775
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31561556"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>方法: ClickOnce 信頼プロンプトの動作を構成する
コントロールに ClickOnce 信頼プロンプトを構成するには、エンドユーザーには、Windows フォーム アプリケーション、Windows Presentation Foundation アプリケーション、コンソール アプリケーション、WPF ブラウザーなどの ClickOnce アプリケーションをインストールするオプションが指定されたかどうかアプリケーション、および Office ソリューションです。 信頼プロンプトを構成するには、各エンドユーザーのコンピューターでレジストリ キーを設定します。  
  
 次の表は、5 つのゾーン (インターネット、UntrustedSites、MyComputer、ローカル イントラネット、およびしません) のそれぞれに適用できる構成オプションを示します。  
  
|オプション|レジストリの設定値|説明|  
|------------|----------------------------|-----------------|  
|信頼プロンプトの表示を有効にします。|`Enabled`|ClickOnce 信頼プロンプトは、エンドユーザーが ClickOnce アプリケーションに信頼を付与するために、表示です。|  
|信頼プロンプトの表示を制限します。|`AuthenticodeRequired`|ClickOnce 信頼プロンプトが ClickOnce アプリケーションが、パブリッシャーを識別する証明書で署名されている場合にのみ表示されます。|  
|信頼プロンプトを無効にします。|`Disabled`|明示的に信頼された証明書で署名されていない ClickOnce アプリケーションでは、ClickOnce 信頼プロンプトは表示されません。|  
  
 次の表は、各ゾーンの既定の動作を示します。 アプリケーションの列は、Windows フォーム アプリケーション、Windows Presentation Foundation アプリケーション、WPF ブラウザー アプリケーション、およびコンソール アプリケーションを指します。  
  
|ゾーン|アプリケーション|Office ソリューション|  
|----------|------------------|----------------------|  
|`MyComputer`|`Enabled`|`Enabled`|  
|`LocalIntranet`|`Enabled`|`Enabled`|  
|`TrustedSites`|`Enabled`|`Enabled`|  
|`Internet`|`Enabled`|`AuthenticodeRequired`|  
|`UntrustedSites`|`Disabled`|`Disabled`|  
  
 有効にすると、制限、または ClickOnce 信頼プロンプトを無効にすると、これらの設定をオーバーライドできます。  
  
## <a name="enabling-the-clickonce-trust-prompt"></a>ClickOnce 信頼プロンプトの有効化  
 インストールして、そのゾーンから派生した任意の ClickOnce アプリケーションを実行して、オプションで提示するユーザーが終了するときに、ゾーンに対する信頼プロンプトの表示を有効にします。  
  
#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>レジストリ エディターを使用して ClickOnce 信頼プロンプトの表示を有効にするには  
  
1.  レジストリ エディターを開きます。  
  
    1.  をクリックして**開始**、順にクリック**実行**です。  
  
    2.  **開いている**ボックスに、入力`regedit32`、順にクリック**OK**です。  
  
2.  次のレジストリ キーを検索します。  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\です。NETFramework\Security\TrustManager\PromptingLevel  
  
     キーが存在しない場合は、それを作成します。  
  
3.  次のサブキーとして追加**文字列値**がまだ存在しない、次の表に示すように関連付けられている値を持つ場合は、します。  
  
    |文字列値のサブキー|[値]|  
    |-------------------------|-----------|  
    |`Internet`|`Enabled`|  
    |`UntrustedSites`|`Disabled`|  
    |`MyComputer`|`Enabled`|  
    |`LocalIntranet`|`Enabled`|  
    |`TrustedSites`|`Enabled`|  
  
     Office ソリューションの`Internet`既定値を持つ`AuthenticodeRequired`と`UntrustedSites`プロパティ値を持つ`Disabled`します。 他のユーザーの`Internet`既定値を持つ`Enabled`します。  
  
#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>ClickOnce 信頼プロンプトをプログラムで有効にするには  
  
1.  Visual Studio で Visual Basic または Visual c# コンソール アプリケーションを作成します。  
  
2.  編集 Program.vb ファイルまたは Program.cs ファイルを開き、次のコードを追加します。  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "Enabled")  
    key.SetValue("TrustedSites", "Enabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
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
  
## <a name="restricting-the-clickonce-trust-prompt"></a>ClickOnce 信頼プロンプトの表示を制限します。  
 信頼プロンプトの表示を制限して、ソリューションは、ユーザーは、信頼の決定に求められる前に、既知の id を持つ Authenticode 証明書で署名する必要があります。  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>レジストリ エディターを使用して ClickOnce 信頼プロンプトの表示を制限するには  
  
1.  レジストリ エディターを開きます。  
  
    1.  をクリックして**開始**、順にクリック**実行**です。  
  
    2.  **開いている**ボックスに、入力`regedit`、順にクリック**OK**です。  
  
2.  次のレジストリ キーを検索します。  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\です。NETFramework\Security\TrustManager\PromptingLevel  
  
     キーが存在しない場合は、それを作成します。  
  
3.  次のサブキーとして追加**文字列値**がまだ存在しない、次の表に示すように関連付けられている値を持つ場合は、します。  
  
    |文字列値のサブキー|[値]|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`AuthenticodeRequired`|  
    |`MyComputer`|`AuthenticodeRequired`|  
    |`LocalIntranet`|`AuthenticodeRequired`|  
    |`TrustedSites`|`AuthenticodeRequired`|  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>ClickOnce 信頼プロンプトをプログラムで制限するには  
  
1.  Visual Studio で Visual Basic または Visual c# コンソール アプリケーションを作成します。  
  
2.  編集 Program.vb ファイルまたは Program.cs ファイルを開き、次のコードを追加します。  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "AuthenticodeRequired")  
    key.SetValue("LocalIntranet", "AuthenticodeRequired")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "AuthenticodeRequired")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
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
  
## <a name="disabling-the-clickonce-trust-prompt"></a>ClickOnce 信頼プロンプトを無効にします。  
 信頼プロンプトを無効にするには、できるように、エンドユーザーでは、そのセキュリティ ポリシーで既に信頼されていないソリューションをインストールするオプションは表示されません。  
  
#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>レジストリ エディターを使用して、ClickOnce 信頼プロンプトを無効にするには  
  
1.  レジストリ エディターを開きます。  
  
    1.  をクリックして**開始**、順にクリック**実行**です。  
  
    2.  **開いている**ボックスに、入力`regedit`、順にクリック**OK**です。  
  
2.  次のレジストリ キーを検索します。  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\です。NETFramework\Security\TrustManager\PromptingLevel  
  
     キーが存在しない場合は、それを作成します。  
  
3.  次のサブキーとして追加**文字列値**がまだ存在しない、次の表に示すように関連付けられている値を持つ場合は、します。  
  
    |文字列値のサブキー|[値]|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`Disabled`|  
    |`MyComputer`|`Disabled`|  
    |`LocalIntranet`|`Disabled`|  
    |`TrustedSites`|`Disabled`|  
  
#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>プログラムで、ClickOnce 信頼プロンプトを無効にするには  
  
1.  Visual Studio で Visual Basic または Visual c# コンソール アプリケーションを作成します。  
  
2.  編集 Program.vb ファイルまたは Program.cs ファイルを開き、次のコードを追加します。  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Disabled")  
    key.SetValue("LocalIntranet", "Disabled")  
    key.SetValue("Internet", "Disabled")  
    key.SetValue("TrustedSites", "Disabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
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
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションのセキュリティ](../deployment/securing-clickonce-applications.md)   
 [ClickOnce アプリケーションのコード アクセス セキュリティ](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce と Authenticode](../deployment/clickonce-and-authenticode.md)   
 [信頼されたアプリケーションの配置の概要](../deployment/trusted-application-deployment-overview.md)   
 [方法 : ClickOnce のセキュリティ設定を有効にする](../deployment/how-to-enable-clickonce-security-settings.md)   
 [方法 : ClickOnce アプリケーションのセキュリティ ゾーンを設定する](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [方法 : ClickOnce アプリケーションのカスタム アクセス許可を設定する](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [方法 : アクセス許可が制限された ClickOnce アプリケーションをデバッグする](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [方法: ClickOnce アプリケーション用のクライアント コンピューターに信頼された発行元を追加](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [方法: アプリケーション マニフェストおよび配置マニフェストに再署名する](../deployment/how-to-re-sign-application-and-deployment-manifests.md)