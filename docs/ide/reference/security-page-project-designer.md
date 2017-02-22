---
title: "[セキュリティ] ページ (プロジェクト デザイナー) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesSecurity"
  - "vb.XBAPProjectPropertiesSecurity"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "プロジェクト デザイナー、[セキュリティ] ページ"
  - "[セキュリティ] ページ (プロジェクト デザイナー)"
ms.assetid: 641d9cd3-fa07-498a-8568-3c169bb4d3d5
caps.latest.revision: 34
caps.handback.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# [セキュリティ] ページ (プロジェクト デザイナー)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

**プロジェクト デザイナー**の **\[セキュリティ\]** ページでは、[!INCLUDE[ndptecclick](../../deployment/includes/ndptecclick_md.md)] 配置によって配置されるアプリケーション用のコード アクセス セキュリティ設定を構成します。  詳細については、「[ClickOnce アプリケーションのコード アクセス セキュリティ](../../deployment/code-access-security-for-clickonce-applications.md)」を参照してください。  
  
 **\[セキュリティ\]** ページを表示するには、**ソリューション エクスプローラー**でプロジェクト ノードをクリックし、**\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  **プロジェクト デザイナー**が表示されたら、**\[セキュリティ\]** タブをクリックします。  
  
## セキュリティ設定  
 **\[ClickOnce セキュリティ設定を有効にする\]**  
 セキュリティ設定をデザイン時に有効にするかどうかを指定します。  このオプションがオフの場合は、**\[セキュリティ\]** ページの他のオプションもすべて無効になります。  
  
> [!NOTE]
>  **発行**ウィザードを使用してアプリケーションを発行するときは、このオプションが自動的に有効になります。  
  
 このオプションをオンにすると、**\[これは完全に信頼するアプリケーションです\]** と **\[これは部分的に信頼するアプリケーションです\]** の 2 つのオプション ボタンの一方を選択できるようになります。  
  
 WPF Web ブラウザー アプリケーション プロジェクトでは、このオプションは既定でオンになります。  
  
 それ以外のすべての種類のプロジェクトでは、このオプションは既定でオフになります。  
  
 **\[これは完全に信頼するアプリケーションです\]**  
 このオプションをオンにすると、アプリケーションをクライアント コンピューターにインストールしたり実行したりするときに、完全信頼のアクセス許可が要求されます。  ファイル システムやレジストリなどのリソースへの無制限のアクセス許可がアプリケーションに与えられるため、完全信頼の使用はできるだけ避けてください。  
  
 WPF Web ブラウザー アプリケーション プロジェクトでは、このオプションは既定で部分信頼に設定されます。  
  
 それ以外のすべての種類のプロジェクトでは、このオプションは既定で完全信頼に設定されます。  
  
 **\[これは部分的に信頼するアプリケーションです\]**  
 このオプションをオンにすると、アプリケーションをクライアント コンピューターにインストールしたり実行したりするときに、部分信頼アクセス許可が要求されます。  *部分信頼*とは、要求したコード アクセス セキュリティ許可で許可されたアクションのみが実行されることを意味します。  セキュリティ アクセス許可の構成方法の詳細については、「[ClickOnce アプリケーションのコード アクセス セキュリティ](../../deployment/code-access-security-for-clickonce-applications.md)」を参照してください。  
  
 部分信頼セキュリティの設定は、**\[ClickOnce セキュリティのアクセス許可\]** 領域のオプションを構成することで指定できます。  
  
## \[ClickOnce セキュリティのアクセス許可\]  
 **\[アプリケーションがインストールされるゾーン\]**  
 コード アクセス セキュリティ許可の既定のセットを指定します。  制限されたアクセス許可セットを使用するには **\[インターネット\]** または **\[ローカル イントラネット\]** を選択し、カスタムのアクセス許可セットを設定するには **\[\(カスタム\)\]** を選択します。  ゾーンで付与されているよりも多くのアクセス許可がアプリケーションで要求される場合、エンド ユーザーのアクセス許可を追加するために、ClickOnce 信頼プロンプトが表示されます。  セキュリティ アクセス許可の構成方法の詳細については、「[ClickOnce アプリケーションのコード アクセス セキュリティ](../../deployment/code-access-security-for-clickonce-applications.md)」を参照してください。  
  
 WPF Web ブラウザー アプリケーション プロジェクトでは、このオプションは既定で **\[インターネット\]** に設定されます。  
  
 **アクセス許可の XML の編集**  
 **\[\(カスタム\)\]** アクセス許可セットのアクセス許可を構成するには、アプリケーション マニフェスト テンプレート \(app.manifest\) を開きます。  
  
 **\[詳細\]**  
 [\[セキュリティの詳細設定\] ダイアログ ボックス](../Topic/Advanced%20Security%20Settings%20Dialog%20Box.md)が開きます。このダイアログ ボックスでは、制限されたアクセス許可でのアプリケーションのデバッグ用の設定を構成できます。  これらの設定はデバッグ中にチェックされます。アクセス許可例外は、ゾーンで定義されているよりも多くのアプリケーション許可がアプリケーションで必要であることを示します。  
  
## 参照  
 <xref:System.Security.Permissions.WebBrowserPermission>   
 <xref:System.Security.Permissions.MediaPermission>   
 [ClickOnce アプリケーションのコード アクセス セキュリティ](../../deployment/code-access-security-for-clickonce-applications.md)   
 [方法 : ClickOnce のセキュリティ設定を有効にする](../../deployment/how-to-enable-clickonce-security-settings.md)   
 [方法 : ClickOnce アプリケーションのセキュリティ ゾーンを設定する](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [方法 : ClickOnce アプリケーションのカスタム アクセス許可を設定する](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [方法 : アクセス許可が制限された ClickOnce アプリケーションをデバッグする](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [ClickOnce のセキュリティと配置](../../deployment/clickonce-security-and-deployment.md)   
 [プロジェクトのプロパティのリファレンス](../../ide/reference/project-properties-reference.md)   
 [\[セキュリティの詳細設定\] ダイアログ ボックス](../Topic/Advanced%20Security%20Settings%20Dialog%20Box.md)