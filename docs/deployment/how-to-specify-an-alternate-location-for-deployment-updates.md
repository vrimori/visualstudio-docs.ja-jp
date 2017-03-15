---
title: "方法 : 配置の更新用に別の場所を指定する | Microsoft Docs"
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
  - "ClickOnce 配置, 更新"
  - "配置の更新, 代替位置"
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : 配置の更新用に別の場所を指定する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションの初期インストールは CD やファイル共有から行うことができますが、更新プログラムの確認を行うには、定期的に Web サイトにアクセスする必要があります。  配置マニフェストでは、初期インストール後に Web サイトからアプリケーションを更新できるように、更新プログラム用の別の場所を指定できます。  
  
> [!NOTE]
>  この機能を使用するには、アプリケーションをローカル コンピューターにインストールするように構成する必要があります。  詳細については、「[チュートリアル : ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)」を参照してください。  また、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションをネットワーク経由でインストールするように構成した場合に、別の場所を設定すると、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] では、初期インストールでも以降の更新プログラムでもその場所が使用されます。  CD など、ローカル メディアからアプリケーションをインストールする場合には、初期インストールは元のメディアから行われ、以降の更新は指定した別の場所から行われます。  
  
### Windows フォーム ベースのユーティリティ MageUI.exe を使用して更新プログラム用の別の場所を指定する  
  
1.  .NET Framework のコマンド プロンプトを開き、次のように入力します。  
  
     **mageui.exe**  
  
2.  **\[File\]** メニューの **\[Open\]** をクリックし、アプリケーションの配置マニフェストを開きます。  
  
3.  **\[Deployment Options\]** タブをクリックします。  
  
4.  **\[Launch Location\]** ボックスに、アプリケーションを更新するための配置マニフェストが格納してあるディレクトリの URL を入力します。  
  
5.  配置マニフェストを保存します。  
  
### Mage.exe を使用して更新プログラム用の別の場所を指定する  
  
1.  .NET Framework のコマンド プロンプトを開きます。  
  
2.  次のコマンドを実行して、更新プログラムの場所を指定します。  この例では、**HelloWorld.exe.application** が [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーション マニフェストのパスで、拡張子は常に .application です。**http:\/\/adatum.com\/Update\/Path** は、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] でアプリケーションの更新プログラムを確認する URL です。  
  
     **Mage \-Update HelloWorld.exe.application \-ProviderUrl http:\/\/adatum.com\/Update\/Path**  
  
3.  ファイルを保存します。  
  
    > [!NOTE]
    >  この時点で、Mage.exe を使用してファイルに再署名する必要があります。  詳細については、「[チュートリアル : ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)」を参照してください。  
  
## .NET Framework セキュリティ  
 アプリケーションを CD などオフラインのメディアからインストールするときに、コンピューターがオンラインになっていると、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] では、最初に配置マニフェストの `<deploymentProvider>` タグで指定された URL の更新プログラムの場所にアクセスして、より新しいバージョンのアプリケーションが格納されていないかどうかを確認します。  存在する場合、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] では、初期インストール ディレクトリではなく、Web サイトから直接アプリケーションをインストールします。このときのアプリケーションの信頼レベルは、共通言語ランタイム \(CLR: Common Language Runtime\) で `<deploymentProvider>` を使用して決定されます。  コンピューターがオフラインになっているか、または `<deploymentProvider>` にアクセスできない場合、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] では、インストールを CD から行い、インストール ポイントに基づく信頼レベルが CLR によって与えられます。たとえば CD からインストールする場合であれば、完全な信頼がアプリケーションに与えられます。  以降の各更新では、この信頼レベルが継承されます。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] を使用する `<deploymentProvider>` アプリケーションでは、アプリケーション マニフェストで必要なアクセス許可を明示的に宣言し、コンピューターが異なっても与えられる信頼のレベルが等しくなるようにする必要があります。  
  
## 参照  
 [チュートリアル : ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)   
 [ClickOnce アプリケーションのセキュリティ](../deployment/securing-clickonce-applications.md)   
 [ClickOnce の更新方法の選択](../deployment/choosing-a-clickonce-update-strategy.md)