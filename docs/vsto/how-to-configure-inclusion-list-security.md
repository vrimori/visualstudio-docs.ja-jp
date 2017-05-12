---
title: "方法: 信頼のリストのセキュリティを構成する"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "信頼のリスト [Visual Studio での Office 開発]"
  - "アクセス許可 [Visual Studio での Office 開発"
ms.assetid: 0609d8f0-4630-4e17-aeb3-14f3134165cf
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# 方法: 信頼のリストのセキュリティを構成する
  管理者アクセス許可がある場合は、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信頼プロンプトを構成することによって、エンド ユーザーが信頼のリストに信頼の決定を保存して Office ソリューションをインストールできるようにするかどうかを制御できます。  信頼のリストの詳細については、「[信頼のリストによる Office ソリューションへの信頼の付与](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)」を参照してください。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 5 つのゾーンのそれぞれに属するソリューションについて、以下のオプションを設定できます。  
  
-   [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信頼プロンプト キーおよび信頼のリストを有効にします。  エンド ユーザーに対し、証明書で署名された Office ソリューションに信頼を付与することを許可できます。  
  
-   [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信頼プロンプト キーおよび信頼のリストを制限します。  エンド ユーザーに対し、発行者が示されているものの常に信頼できるわけではない証明書で署名された Office ソリューションのインストールを許可できます。  
  
-   [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信頼プロンプト キーおよび信頼のリストを無効にします。  エンド ユーザーに対し、明示的に信頼されている証明書で署名されていない Office ソリューションのインストールを禁止できます。  
  
## 信頼のリストの有効化  
 あるゾーンに属する Office ソリューションをエンド ユーザーがインストールして実行できるようにするには、そのゾーンの信頼のリストを有効にします。  
  
#### レジストリ エディターを使用して信頼のリストを有効にするには  
  
1.  レジストリ エディターを開きます。  
  
    1.  **\[スタート\]** ボタンをクリックし、**\[ファイル名を指定して実行\]** をクリックします。  
  
    2.  **\[名前\]** ボックスに「**regedt32.exe**」と入力し、**\[OK\]** をクリックします。  
  
2.  次のレジストリ キーを探します。  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     このキーが存在しない場合は作成します。  
  
3.  次のサブキーが存在しない場合は、**文字列値**として追加し、関連する値を指定します。  
  
    |文字列値サブキー|価値|  
    |--------------|--------|  
    |**インターネット**|**AuthenticodeRequired**|  
    |**UntrustedSites**|**Disabled**|  
    |**MyComputer**|**Enabled**|  
    |**ローカル イントラネット**|**Enabled**|  
    |**TrustedSites**|**Enabled**|  
  
     **Internet** の既定値は **AuthenticodeRequired**、**UntrustedSites** の既定値は **Disabled** です。  
  
#### 信頼のリストをプログラムによって有効にするには  
  
1.  Visual Basic または Visual C\# のコンソール アプリケーションを作成します。  
  
2.  Program.vb ファイルまたは Program.cs ファイルを編集用に開き、次のコードを追加します。  
  
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
  
## 信頼のリストの制限  
 信頼のリストを制限すると、ユーザーに信頼するかどうかの確認を求める前に、既知の ID を持つ Authenticode 証明書でソリューションを署名することが必要になります。  
  
#### 信頼のリストを制限するには  
  
1.  レジストリ エディターを開きます。  
  
    1.  **\[スタート\]** ボタンをクリックし、**\[ファイル名を指定して実行\]** をクリックします。  
  
    2.  **\[名前\]** ボックスに「**regedt32.exe**」と入力し、**\[OK\]** をクリックします。  
  
2.  次のレジストリ キーを探します。  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     このキーが存在しない場合は作成します。  
  
3.  次のサブキーが存在しない場合は、**文字列値**として追加し、関連する値を指定します。  
  
    |文字列値サブキー|価値|  
    |--------------|--------|  
    |**UntrustedSites**|**Disabled**|  
    |**インターネット**|**AuthenticodeRequired**|  
    |**MyComputer**|**AuthenticodeRequired**|  
    |**ローカル イントラネット**|**AuthenticodeRequired**|  
    |**TrustedSites**|**AuthenticodeRequired**|  
  
     **Internet** の既定値は **AuthenticodeRequired**、**UntrustedSites** の既定値は **Disabled** です。  
  
#### 信頼のリストをプログラムによって制限するには  
  
1.  Visual Basic または Visual C\# のコンソール アプリケーションを作成します。  
  
2.  Program.vb ファイルまたは Program.cs ファイルを編集用に開き、次のコードを追加します。  
  
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
  
## 信頼のリストの無効化  
 信頼のリストを無効にすることにより、エンド ユーザーは信頼できる既知の証明書で署名されたソリューションのみインストールできるようになります。  
  
#### 信頼のリストを無効にするには  
  
1.  レジストリ エディターを開きます。  
  
    1.  **\[スタート\]** ボタンをクリックし、**\[ファイル名を指定して実行\]** をクリックします。  
  
    2.  **\[名前\]** ボックスに「**regedt32.exe**」と入力し、**\[OK\]** をクリックします。  
  
2.  次のレジストリ キーが存在しない場合は作成します。  
  
     **\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel**  
  
3.  次のサブキーが存在しない場合は、**文字列値**として追加し、関連する値を指定します。  
  
    |文字列値サブキー|価値|  
    |--------------|--------|  
    |**UntrustedSites**|**Disabled**|  
    |**インターネット**|**Disabled**|  
    |**MyComputer**|**Disabled**|  
    |**ローカル イントラネット**|**Disabled**|  
    |**TrustedSites**|**Disabled**|  
  
#### 信頼のリストをプログラムによって無効にするには  
  
1.  Visual Basic または Visual C\# のコンソール アプリケーションを作成します。  
  
2.  Program.vb ファイルまたは Program.cs ファイルを編集用に開き、次のコードを追加します。  
  
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
  
## 参照  
 [信頼のリストによる Office ソリューションへの信頼の付与](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Office ソリューションのセキュリティ保護](../vsto/securing-office-solutions.md)  
  
  