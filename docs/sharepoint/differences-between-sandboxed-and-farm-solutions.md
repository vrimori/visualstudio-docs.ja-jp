---
title: "サンドボックス ソリューションとファーム ソリューションの違い | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ファーム ソリューション [Visual Studio での SharePoint 開発]"
  - "サンドボックス ソリューション [Visual Studio での SharePoint 開発]"
  - "Visual Studio での SharePoint 開発, ファーム ソリューション"
  - "Visual Studio での SharePoint 開発, サンドボックス ソリューション"
ms.assetid: 43beb7e7-0cd9-4a8f-bb72-6b1e0cba5be8
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# サンドボックス ソリューションとファーム ソリューションの違い
  SharePoint ソリューションをコンパイルすると、ソリューションは SharePoint サーバー上に配置され、デバッグ用にデバッガーがアタッチされます。  ソリューションのデバッグに使用されるプロセスは、\[サンドボックス ソリューション\] プロパティの設定 \(サンドボックス ソリューションまたはファーム ソリューション\) によって異なります。  
  
 詳細については、「[サンドボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)」を参照してください。  
  
## ファーム ソリューション  
 ファーム ソリューションは、IIS ワーカー プロセス \(W3WP.exe\) でホストされ、ファーム全体に影響するコードを実行します。  \[サンドボックス ソリューション\] プロパティが "ファーム ソリューション" に設定されている SharePoint プロジェクトをデバッグすると、IIS ワーカー プロセスによってロックされたすべてのファイルが解放されるように SharePoint が機能を取り消すまたは配置する前に、システムの IIS アプリケーション プールがリサイクルされます。  SharePoint プロジェクトのサイト URL にサービスを提供する IIS アプリケーション プールのみがリサイクルされます。  
  
## サンドボックス ソリューション  
 サンドボックス ソリューションは、SharePoint ユーザー コード ソリューション ワーカー プロセス \(SPUCWorkerProcess.exe\) でホストされ、ソリューションのサイト コレクションにのみ影響するコードを実行します。  サンドボックス ソリューションは IIS ワーカー プロセスでは実行されないため、IIS アプリケーション プールと IIS サーバーはどちらも再起動する必要がありません。  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] は、SharePoint の SPUserCodeV4 サービスが自動的にトリガーして制御する SPUCWorkerProcess プロセスにデバッガーをアタッチします。  SPUCWorkerProcess プロセスをリサイクルしてソリューションの最新バージョンを読み込む必要はありません。  
  
## いずれかの種類のソリューション  
 いずれかの種類のソリューションを使用して、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] はブラウザーにもデバッガーをアタッチし、クライアント側スクリプトのデバッグを有効にします。  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] は、この目的のためにスクリプト デバッグ エンジンを使用します。  スクリプト デバッグを有効にするには、メッセージが表示されたときに既定のブラウザーの設定を変更する必要があります。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] は、現在のサイトを実行している W3WP または SPUCWorkerProcess プロセスにのみ、デバッガーをアタッチします。  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] は、マネージ COM\+ およびワークフローのデバッグ エンジンもアタッチします。  
  
## 参照  
 [SharePoint ソリューションのデバッグ](../sharepoint/debugging-sharepoint-solutions.md)   
 [SharePoint ソリューションのビルドとデバッグ](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [サンドボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)  
  
  