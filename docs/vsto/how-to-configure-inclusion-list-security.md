---
title: "方法: 信頼リストのセキュリティの構成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
ms.assetid: 0609d8f0-4630-4e17-aeb3-14f3134165cf
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 09ea283b17a980ff9be1fae54ecc8b24912b70ad
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-inclusion-list-security"></a>方法: 信頼のリストのセキュリティを構成する
  管理者権限を付与する場合は、構成、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信頼プロンプトのコントロールにエンドユーザーが信頼のリストに、信頼の決定を保存することによって、Office ソリューションをインストールするオプションを指定されたかどうか。 信頼のリストについては、次を参照してください。[リストによる Office ソリューションを信頼する](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)です。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 5 つのゾーンのそれぞれにソリューションの場合は、次のオプションを設定できます。  
  
-   有効にする、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]プロンプトのキーを信頼し、信頼のリスト。 任意の証明書で署名されている Office ソリューションに信頼を付与するエンドユーザーを許可することができます。  
  
-   制限、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]プロンプトのキーを信頼し、信頼のリスト。 エンドユーザー、パブリッシャーを識別するがされていないに既に信頼された証明書で署名されている Office ソリューションをインストールすることができます。  
  
-   無効にする、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]プロンプトのキーを信頼し、信頼のリスト。 明示的に信頼された証明書で署名されていない Office ソリューションのインストールからエンドユーザーができなくなります。  
  
## <a name="enabling-the-inclusion-list"></a>信頼のリストを有効にします。  
 インストールして、そのゾーンから取得した Office ソリューションを実行しているのオプションを使用して表示するユーザーが終了するときに、ゾーンの信頼のリストを有効にします。  
  
#### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>レジストリ エディターを使用して、信頼のリストを有効にするには  
  
1.  レジストリ エディターを開きます。  
  
    1.  をクリックして**開始**、順にクリック**実行**です。  
  
    2.  **開いている**ボックスに、入力**regedt32.exe**、順にクリック**OK**です。  
  
2.  次のレジストリ キーを検索します。  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\です。NETFramework\Security\TrustManager\PromptingLevel  
  
     キーが存在しない場合は、それを作成します。  
  
3.  次のサブキーとして追加**文字列値**がまだ存在しない、関連付けられている値を持つ場合は、します。  
  
    |文字列値のサブキー|[値]|  
    |-------------------------|-----------|  
    |**インターネット**|**AuthenticodeRequired**|  
    |**UntrustedSites**|**無効**|  
    |**MyComputer**|**有効**|  
    |**ローカル イントラネット**|**有効**|  
    |**しません**|**有効**|  
  
     既定では、**インターネット**プロパティ値を持つ**AuthenticodeRequired**と**UntrustedSites**プロパティ値を持つ**無効になっている**です。  
  
#### <a name="to-enable-the-inclusion-list-programmatically"></a>信頼のリストをプログラムで有効にするには  
  
1.  Visual Basic または Visual c# コンソール アプリケーションを作成します。  
  
2.  編集 Program.vb ファイルまたは Program.cs ファイルを開き、次のコードを追加します。  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "AuthenticodeRequired")  
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
  
## <a name="restricting-the-inclusion-list"></a>信頼のリストを制限します。  
 信頼のリストを制限して、ソリューションは、ユーザーは、信頼の決定に求められる前に、既知の id を持つ Authenticode 証明書で署名する必要があります。  
  
#### <a name="to-restrict-the-inclusion-list"></a>信頼のリストを制限するには  
  
1.  レジストリ エディターを開きます。  
  
    1.  をクリックして**開始**、順にクリック**実行**です。  
  
    2.  **開いている**ボックスに、入力**regedt32.exe**、順にクリック**OK**です。  
  
2.  次のレジストリ キーを検索します。  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\です。NETFramework\Security\TrustManager\PromptingLevel  
  
     キーが存在しない場合は、それを作成します。  
  
3.  次のサブキーとして追加**文字列値**がまだ存在しない、関連付けられている値を持つ場合は、します。  
  
    |文字列値のサブキー|[値]|  
    |-------------------------|-----------|  
    |**UntrustedSites**|**無効**|  
    |**インターネット**|**AuthenticodeRequired**|  
    |**MyComputer**|**AuthenticodeRequired**|  
    |**ローカル イントラネット**|**AuthenticodeRequired**|  
    |**しません**|**AuthenticodeRequired**|  
  
     既定では、**インターネット**プロパティ値を持つ**AuthenticodeRequired**と**UntrustedSites**プロパティ値を持つ**無効になっている**です。  
  
#### <a name="to-restrict-the-inclusion-list-programmatically"></a>プログラムで信頼のリストを制限するには  
  
1.  Visual Basic または Visual c# コンソール アプリケーションを作成します。  
  
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
  
## <a name="disabling-the-inclusion-list"></a>信頼のリストを無効にします。  
 信頼のリストを無効にするには、エンドユーザーでは署名されているソリューションを信頼できると既知の証明書にのみインストールできるようにします。  
  
#### <a name="to-disable-the-inclusion-list"></a>信頼のリストを無効にするには  
  
1.  レジストリ エディターを開きます。  
  
    1.  をクリックして**開始**、順にクリック**実行**です。  
  
    2.  **開いている**ボックスに、入力**regedt32.exe**、順にクリック**OK**です。  
  
2.  これが存在しない場合は、次のレジストリ キーを作成します。  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\です。NETFramework\Security\TrustManager\PromptingLevel**  
  
3.  次のサブキーとして追加**文字列値**がまだ存在しない、関連付けられている値を持つ場合は、します。  
  
    |文字列値のサブキー|[値]|  
    |-------------------------|-----------|  
    |**UntrustedSites**|**無効**|  
    |**インターネット**|**無効**|  
    |**MyComputer**|**無効**|  
    |**ローカル イントラネット**|**無効**|  
    |**しません**|**無効**|  
  
#### <a name="to-disable-the-inclusion-list-programmatically"></a>信頼のリストをプログラムで無効にするには  
  
1.  Visual Basic または Visual c# コンソール アプリケーションを作成します。  
  
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
  
## <a name="see-also"></a>参照  
 [信頼のリストを使用して Office ソリューションを信頼します。](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Office ソリューションのセキュリティ保護](../vsto/securing-office-solutions.md)  
  
  