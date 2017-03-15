---
title: "ASP.NET のデバッグ : システム要件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ASP.NET Web アプリケーションのデバッグ, システム要件"
  - "ASP.NET Web アプリケーションのデバッグ, セキュリティ要件"
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
caps.latest.revision: 38
caps.handback.revision: 38
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ASP.NET のデバッグ : システム要件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ここでは、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] のデバッグ シナリオに必要なソフトウェアとセキュリティの要件について説明します。  
  
-   ローカル デバッグ。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] と Web アプリケーションが同じコンピューターで実行されている場合のデバッグです。 このシナリオには、2 つのバージョンがあります。  
  
    -   [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] コードがファイル システムに存在する場合  
  
    -   [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] コードが IIS の Web サイトに存在する場合  
  
-   リモート デバッグ。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] はクライアント コンピューターで実行され、リモート サーバー コンピューターで実行されている Web アプリケーションをデバッグします。  
  
## セキュリティ要件  
 リモート デバッグでは、ローカル コンピューターとリモート コンピューターが同じドメイン内または同じワークグループ内にセットアップされている必要があります。  
  
 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスをデバッグするには、そのプロセスをデバッグするアクセス許可が必要です。[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] アプリケーションは、既定では **ASPNET** ユーザーとして実行されます。 ワーカー プロセスが **ASPNET** \(既定\) または **NETWORK SERVICE** として実行されている場合、そのプロセスをデバッグするには管理者特権が必要です。  
  
 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスの名前は、デバッグ シナリオや IIS のバージョンによって異なります。 詳細については、「[方法 : ASP.NET プロセスの名前を見つける](../debugger/how-to-find-the-name-of-the-aspnet-process.md)」を参照してください。  
  
 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスを実行しているユーザー アカウントは、IIS を実行しているサーバーの machine.config ファイルを編集することによって変更できます。 これを行うには、**インターネット インフォメーション サービス \(IIS\) マネージャー**を使用するのが最善です。 詳細については、「[方法 : ユーザー アカウントでワーカー プロセスを実行する](../debugger/how-to-run-the-worker-process-under-a-user-account.md)」を参照してください。  
  
 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスを自分のユーザー アカウントで実行するように変更する場合、IIS を実行しているサーバーの管理者である必要はありません。  
  
> [!CAUTION]
>  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスを別のアカウントで実行するように変更する場合は、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスがそのアカウントで実行中にハックされた場合の影響を考慮する必要があります。 ASPNET および NETWORK SERVICE の各ユーザー アカウントは最小限のアクセス許可で実行されるので、プロセスがハックされた場合の損害が少なくなります。 高い権限のアクセス許可を持つアカウントで [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスを実行する必要がある場合、損害が大きくなる可能性があります。  
  
## 参照  
 [ASP.NET アプリケーションおよび AJAX アプリケーションのデバッグ](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [方法 : ユーザー アカウントでワーカー プロセスを実行する](../debugger/how-to-run-the-worker-process-under-a-user-account.md)