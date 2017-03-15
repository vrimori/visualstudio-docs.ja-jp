---
title: "Prerequistes for Remote Debugging Web Applications (方法 : リモート サーバーで Web アプリケーションをデバッグする) | Microsoft Docs"
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
  - "デバッグ (ASP.NET Web アプリケーションを), リモート サーバー"
  - "リモート デバッグ, 必要条件"
  - "リモート サーバー, デバッグ (Web アプリケーションを)"
ms.assetid: 1cd777b5-6d20-4ca6-a0df-51653b118469
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Prerequistes for Remote Debugging Web Applications (方法 : リモート サーバーで Web アプリケーションをデバッグする)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] デバッガーを使用すると、ローカル コンピューターやリモート サーバーで、Web アプリケーションを透過的にデバッグできます。  これは、どちらのコンピューターでもデバッガーの動作は同じであり、同じ機能を使用できることを意味します。  ただし、リモート デバッグを正常に機能させるには、いくつかの必要条件があります。  
  
-   デバッグを実行するサーバーに [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] リモート デバッグ コンポーネントをインストールする必要があります。  詳細については、「[リモート デバッグのセットアップ](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)」を参照してください。  
  
-   既定で、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスは ASPNET ユーザー プロセスとして実行されます。  このため、それをデバッグするには、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] が実行されているコンピューターに対する管理者特権が必要です。  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスの名前は、デバッグ シナリオや IIS のバージョンによって変わります。  詳細については、「[方法 : ASP.NET プロセスの名前を見つける](../debugger/how-to-find-the-name-of-the-aspnet-process.md)」を参照してください。  
  
## 参照  
 [ASP.NET アプリケーションおよび AJAX アプリケーションのデバッグ](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [システム要件](../debugger/aspnet-debugging-system-requirements.md)