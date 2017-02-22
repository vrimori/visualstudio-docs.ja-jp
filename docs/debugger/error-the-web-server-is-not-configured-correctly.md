---
title: "エラー : Web サーバーは正しく構成されていません。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.remote.projnotconfigured"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "デバッガー, Web アプリケーション エラー"
ms.assetid: 875ba87f-c372-4126-8fe3-e33931cf26c0
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# エラー : Web サーバーは正しく構成されていません。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このエラーでは以下の原因が考えられます。  
  
-   デバッグしようとした .NET Web アプリケーションは、別のコンピューターにコピーされたか、手動で名前が変更されたか、または別の場所に移動されています。  
  
-   インターネット インフォメーション サービス \(IIS\) の接続が確立していません  IIS への Web サイトの配置に関する詳細については、「[Web サイトの作成](http://www.iis.net/learn/get-started/getting-started-with-iis/create-a-web-site)」を参照してください。  
  
-   ASP.NET アプリケーションをデバッグしようとしている場合、IIS 8 以降を実行しているリモート コンピューターに配置する手順については、「[IIS への発行](https://docs.asp.net/en/latest/publishing/iis.html)」を参照してください。また、IIS 7.5 を実行しているリモート コンピューターに配置する手順については、「[リモートの IIS 7.5 コンピューター上の ASP.NET のリモート デバッグ](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)」を参照してください。  
  
## 参照  
 [Web アプリケーションのデバッグ : エラーおよびトラブルシューティング](../debugger/debugging-web-applications-errors-and-troubleshooting.md)