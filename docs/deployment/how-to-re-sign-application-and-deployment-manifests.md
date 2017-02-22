---
title: "方法: アプリケーション マニフェストおよび配置マニフェストに再署名する | Microsoft Docs"
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
  - "ClickOnce 配置, 署名 (マニフェストに)"
  - "配置 (アプリケーションを) [ClickOnce], 署名 (マニフェストに)"
  - "配置 (アプリケーションを), 署名 (マニフェストに)"
  - "Office アプリケーション, 署名 (マニフェストに)"
  - "Visual Studio での Office 開発, 署名 (マニフェストに)"
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法: アプリケーション マニフェストおよび配置マニフェストに再署名する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Windows フォーム アプリケーション、Windows Presentation Foundation アプリケーション \(xbap\)、または Office ソリューションのアプリケーション マニフェストの配置プロパティを変更した場合、証明書を使用してアプリケーション マニフェストと配置マニフェストの両方に再署名する必要があります。  このプロセスによって、改ざんされたファイルがエンド ユーザーのコンピューターにインストールされないようにすることができます。  
  
 マニフェストへの再署名は、顧客が独自の証明書を使用してアプリケーション マニフェストおよび配置マニフェストに署名する場合にも行います。  
  
## アプリケーション マニフェストと配置マニフェストへの再署名  
 この手順は、アプリケーション マニフェスト ファイル \(.manifest\) への変更を既に行っていることを前提としています。  詳細については、「[方法: 配置プロパティを変更する](http://msdn.microsoft.com/ja-jp/66052a3a-8127-4964-8147-2477ef5d1472)」を参照してください。  
  
#### Mage.exe を使用してアプリケーション マニフェストと配置マニフェストに再署名するには  
  
1.  **Visual Studio コマンド プロンプト** ウィンドウを開きます。  
  
2.  署名するマニフェスト ファイルが含まれるフォルダーに移動します。  
  
3.  次のコマンドを入力し、アプリケーション マニフェスト ファイルに署名します。  ManifestFileName の部分はマニフェスト ファイルの名前に拡張子を付けたものに置き換えます。  Certificate の部分は証明書ファイルの相対パスまたは絶対パスに置き換え、Password の部分は証明書のパスワードに置き換えます。  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     たとえば、次のコマンドを実行すると、アドイン、Windows フォーム アプリケーション、または Windows Presentation Foundation ブラウザー アプリケーションのアプリケーション マニフェストに署名できます。  Visual Studio によって作成される一時的な証明書を、稼動環境に配置する場合に使用することは推奨されません。  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  次のコマンドを入力して、配置マニフェスト ファイルの更新と署名を行います。プレースホルダー名の部分は、前の手順で説明したとおりに置き換えてください。  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     たとえば、次のコマンドを実行すると、Excel アドイン、Windows フォーム アプリケーション、または Windows Presentation Foundation ブラウザー アプリケーションの配置マニフェストを更新したり、それらに署名したりできます。  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  必要に応じて、マスター配置マニフェスト \(publish\\*appname*.application\) をバージョン配置ディレクトリ \(publish\\Application Files\\*appname*\_*version*\) にコピーします。  
  
## アプリケーション マニフェストと配置マニフェストの更新および再署名  
 この手順は、アプリケーション マニフェスト ファイル \(.manifest\) への変更を既に行っており、更新されたその他のファイルが存在することを前提としています。  ファイルが更新されるときは、そのファイルを表すハッシュも更新する必要があります。  
  
#### Mage.exe を使用してアプリケーション マニフェストと配置マニフェストを更新し、再署名するには  
  
1.  **Visual Studio コマンド プロンプト** ウィンドウを開きます。  
  
2.  署名するマニフェスト ファイルが含まれるフォルダーに移動します。  
  
3.  publish 出力フォルダー内のファイルから、拡張子 .deploy を削除します。  
  
4.  次のコマンドを入力して、更新されるファイル用の新しいハッシュでアプリケーション マニフェストを更新し、アプリケーション マニフェスト ファイルに署名します。  ManifestFileName の部分はマニフェスト ファイルの名前に拡張子を付けたものに置き換えます。  Certificate の部分は証明書ファイルの相対パスまたは絶対パスに置き換え、Password の部分は証明書のパスワードに置き換えます。  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     たとえば、次のコマンドを実行すると、アドイン、Windows フォーム アプリケーション、または Windows Presentation Foundation ブラウザー アプリケーションのアプリケーション マニフェストに署名できます。  Visual Studio によって作成される一時的な証明書を、稼動環境に配置する場合に使用することは推奨されません。  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  次のコマンドを入力して、配置マニフェスト ファイルの更新と署名を行います。プレースホルダー名の部分は、前の手順で説明したとおりに置き換えてください。  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     たとえば、次のコマンドを実行すると、Excel アドイン、Windows フォーム アプリケーション、または Windows Presentation Foundation ブラウザー アプリケーションの配置マニフェストを更新したり、それらに署名したりできます。  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  アプリケーション マニフェスト ファイルと配置マニフェストを除くファイルの拡張子を .deploy に戻します。  
  
7.  必要に応じて、マスター配置マニフェスト \(publish\\*appname*.application\) をバージョン配置ディレクトリ \(publish\\Application Files\\*appname*\_*version*\) にコピーします。  
  
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
 [方法: ClickOnce 信頼プロンプトの動作を構成する](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)