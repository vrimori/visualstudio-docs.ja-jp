---
title: "チュートリアル: ClickOnce アプリケーションのカスタム インストーラーの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "ClickOnce 配置, カスタム インストーラー"
  - "カスタム インストーラー [ClickOnce]"
  - "配置 (アプリケーションを) [ClickOnce], カスタム インストーラー"
  - "InPlaceHostingManager [ClickOnce], カスタム インストーラー"
  - "インストーラー [ClickOnce], カスタム"
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
caps.latest.revision: 34
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 34
---
# チュートリアル: ClickOnce アプリケーションのカスタム インストーラーの作成
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

.exe ファイルに基づく ClickOnce アプリケーションは、カスタム インストーラーによってサイレント インストールおよび更新できます。  カスタム インストーラーでは、インストール時のユーザー エクスペリエンスをカスタマイズでき、セキュリティや保守の操作に使用するカスタム ダイアログ ボックスなどを実装できます。  インストール操作を実行するには、カスタム インストーラーで <xref:System.Deployment.Application.InPlaceHostingManager> クラスを使用します。  このチュートリアルでは、ClickOnce アプリケーションをサイレント インストールするカスタム インストーラーの作成方法を示します。  
  
## 必須コンポーネント  
  
### ClickOnce アプリケーションのカスタム インストーラーを作成するには  
  
1.  ClickOnce アプリケーションで、System.Deployment および System.Windows.Forms への参照を追加します。  
  
2.  新しいクラスをアプリケーションに追加し、任意の名前を指定します。  このチュートリアルでは、`MyInstaller` という名前を使用します。  
  
3.  次の `Imports` ステートメントまたは `using` ステートメントを新しいクラスの先頭に追加します。  
  
    ```vb#  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```c#  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4.  次のメソッドをクラスに追加します。  
  
     これらのメソッドでは、<xref:System.Deployment.Application.InPlaceHostingManager> メソッドを呼び出して、配置マニフェストをダウンロードし、適切なアクセス許可を与え、インストールの許可をユーザーに確認し、アプリケーションをダウンロードして ClickOnce キャッシュにインストールします。  カスタム インストーラーでは、ClickOnce アプリケーションを事前に信頼しておくことも、<xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> メソッドの呼び出し時に信頼の決定を行うこともできます。  このコードでは、アプリケーションを事前に信頼しておきます。  
  
    > [!NOTE]
    >  事前に信頼することで割り当てられるアクセス許可は、カスタム インストーラー コードのアクセス許可の範囲内でのみ有効です。  
  
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-cs[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]  
  
5.  コードからインストールを実行するには、`InstallApplication` メソッドを呼び出します。  たとえば、クラス名を `MyInstaller` にした場合、次のように `InstallApplication` を呼び出します。  
  
    ```vb#  
    Dim installer As New MyInstaller()  
    installer.InstallApplication("\\myServer\myShare\myApp.application")  
    MessageBox.Show("Installer object created.")  
    ```  
  
    ```c#  
    MyInstaller installer = new MyInstaller();  
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");  
    MessageBox.Show("Installer object created.");  
  
    ```  
  
## 次の手順  
 ClickOnce アプリケーションでは、更新プロセス時に表示されるカスタム ユーザー インターフェイスなど、カスタムの更新ロジックを追加することもできます。  詳細については、<xref:System.Deployment.Application.UpdateCheckInfo> を参照してください。  また、`<customUX>` 要素を使用して、標準のスタート メニュー エントリ、ショートカット、および \[プログラムの追加または削除\] エントリを非表示にすることもできます。  詳細については、「[\<entryPoint\> 要素](../deployment/entrypoint-element-clickonce-application.md)」および「<xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>」を参照してください。  
  
## 参照  
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)   
 [\<entryPoint\> 要素](../deployment/entrypoint-element-clickonce-application.md)