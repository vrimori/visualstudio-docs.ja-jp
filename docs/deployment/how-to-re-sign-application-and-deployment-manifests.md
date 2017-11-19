---
title: "方法: アプリケーション マニフェストと配置マニフェストに再署名 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Office applications, signing manifests
- deploying applications [ClickOnce], signing manifests
- deploying applications, signing manifests
- ClickOnce deployment, signing manifests
- Office development in Visual Studio, signing manifests
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
caps.latest.revision: "17"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: baa3e9310946482a4c7c64fdb619ce612a21dbda
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>方法: アプリケーション マニフェストおよび配置マニフェストに再署名する
Windows フォーム アプリケーション、Windows Presentation Foundation アプリケーション (xbap)、Office ソリューション用アプリケーション マニフェストにある展開プロパティを変更した後、両方のアプリケーションを再署名する必要がありでの配置マニフェスト、証明書です。 このプロセスにより、エンドユーザーのコンピューターに改ざんされたファイルがインストールされていないことを確認してください。  
  
 マニフェストを再署名が別のシナリオは、お客様が、アプリケーションに署名して、配置が、独自の証明書でマニフェストです。  
  
## <a name="re-signing-the-application-and-deployment-manifests"></a>マニフェストに、アプリケーションおよび配置を再署名  
 この手順では、アプリケーションのマニフェスト ファイル (.manifest が付いたもの) に変更が既に行われたことを前提としています。 詳細については、次を参照してください。[する方法: 配置プロパティを変更](http://msdn.microsoft.com/en-us/66052a3a-8127-4964-8147-2477ef5d1472)です。  
  
#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Mage.exe を使用してマニフェストに、アプリケーションおよび配置を再署名するには  
  
1.  開く、 **Visual Studio コマンド プロンプト**ウィンドウです。  
  
2.  マニフェスト ファイルに署名するが含まれるフォルダーにディレクトリを変更します。  
  
3.  アプリケーション マニフェスト ファイルに署名するには、次のコマンドを入力します。 ManifestFileName を拡張子が付いた、マニフェスト ファイルの名前に置き換えます。 証明書、証明書ファイルの相対パスまたは完全修飾パスを置き換えるし、証明書のパスワードにパスワードを置き換えます。  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     たとえば、アドインを Windows フォーム アプリケーション、または Windows Presentation Foundation ブラウザー アプリケーションのアプリケーション マニフェストに署名するには、次のコマンドを実行します。 Visual Studio によって作成された一時的な証明書は実稼働環境に展開するため推奨されません。  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  更新し、前の手順と同様にプレース ホルダー名を置き換えて、配置マニフェスト ファイルに署名するには、次のコマンドを入力します。  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     たとえば、更新および Excel のアドインで、Windows フォーム アプリケーション、または Windows Presentation Foundation ブラウザー アプリケーションの配置マニフェストに署名するには、次のコマンドを実行します。  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  必要に応じて、マスターの配置マニフェストにコピー (発行\\*appname*.application) バージョン配置ディレクトリに (publish\Application ファイル\\*appname*_*バージョン*)。  
  
## <a name="updating-and-re-signing-the-application-and-deployment-manifests"></a>更新と、アプリケーション マニフェストと配置マニフェストに再署名  
 この手順は、マニフェスト ファイル (マニフェスト) アプリケーションへの変更が既に行われたことが、更新されたその他のファイルがあることを想定しています。 ファイルが更新されると、ファイルを表すハッシュも更新する必要があります。  
  
#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Mage.exe を使用してマニフェストを更新して、アプリケーションおよび配置を再署名  
  
1.  開く、 **Visual Studio コマンド プロンプト**ウィンドウです。  
  
2.  マニフェスト ファイルに署名するが含まれるフォルダーにディレクトリを変更します。  
  
3.  発行の出力フォルダー内のファイルから、.deploy ファイル拡張子を削除します。  
  
4.  更新されたファイル用の新しいハッシュをアプリケーション マニフェストを更新して、アプリケーション マニフェスト ファイルに署名するには、次のコマンドを入力します。 ManifestFileName を拡張子が付いた、マニフェスト ファイルの名前に置き換えます。 証明書、証明書ファイルの相対パスまたは完全修飾パスを置き換えるし、証明書のパスワードにパスワードを置き換えます。  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     たとえば、アドインを Windows フォーム アプリケーション、または Windows Presentation Foundation ブラウザー アプリケーションのアプリケーション マニフェストに署名するには、次のコマンドを実行します。 Visual Studio によって作成された一時的な証明書は実稼働環境に展開するため推奨されません。  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  更新し、前の手順と同様にプレース ホルダー名を置き換えて、配置マニフェスト ファイルに署名するには、次のコマンドを入力します。  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     たとえば、更新および Excel のアドインで、Windows フォーム アプリケーション、または Windows Presentation Foundation ブラウザー アプリケーションの配置マニフェストに署名するには、次のコマンドを実行します。  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  ただし、アプリケーション マニフェストと配置マニフェスト ファイル、ファイルに .deploy ファイル拡張子を追加します。  
  
7.  必要に応じて、マスターの配置マニフェストにコピー (発行\\*appname*.application) バージョン配置ディレクトリに (publish\Application ファイル\\*appname*_*バージョン*)。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションのセキュリティ](../deployment/securing-clickonce-applications.md)   
 [ClickOnce アプリケーション用のコード アクセス セキュリティ](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce と Authenticode](../deployment/clickonce-and-authenticode.md)   
 [信頼されたアプリケーションの配置の概要](../deployment/trusted-application-deployment-overview.md)   
 [方法: ClickOnce のセキュリティ設定を有効にします。](../deployment/how-to-enable-clickonce-security-settings.md)   
 [方法: ClickOnce アプリケーションのセキュリティ ゾーンを設定](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [How to: Set Custom Permissions for a ClickOnce Application](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [方法: アクセス許可が制限された ClickOnce アプリケーションのデバッグ](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [方法: ClickOnce アプリケーション用のクライアント コンピューターに信頼された発行元を追加](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [方法: ClickOnce 信頼プロンプトの動作を構成する](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)