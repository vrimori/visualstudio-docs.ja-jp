---
title: 'ASP.NET のデバッグ: システム要件 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
caps.latest.revision: 41
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f5386390261028fd635f93bc06d3a3fc8805ebdd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533892"
---
# <a name="aspnet-debugging-system-requirements"></a>ASP.NET のデバッグ : システム要件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ASP.NET デバッグ: システム要件](https://docs.microsoft.com/visualstudio/debugger/aspnet-debugging-system-requirements)します。  
  
このトピックでは、のソフトウェアとセキュリティの要件を説明します。[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]デバッグ シナリオ。  
  
-   ローカル デバッグ。[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] と Web アプリケーションが同じコンピューターで実行されている場合のデバッグです。 このシナリオには、2 つのバージョンがあります。  
  
    -   [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] コードがファイル システムに存在する場合  
  
    -   [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] コードが IIS の Web サイトに存在する場合  
  
-   リモート デバッグ。[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] はクライアント コンピューターで実行され、リモート サーバー コンピューターで実行されている Web アプリケーションをデバッグします。  
  
## <a name="security-requirements"></a>セキュリティ要件  
 リモート デバッグでは、ローカル コンピューターとリモート コンピューターが同じドメイン内または同じワークグループ内にセットアップされている必要があります。  
  
 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ワーカー プロセスをデバッグするには、そのプロセスをデバッグするアクセス許可が必要です。 既定では、[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]アプリケーションとして実行、 **ASPNET**ユーザー。 ワーカー プロセスが **ASPNET**(既定) または **NETWORK SERVICE**として実行されている場合、そのプロセスをデバッグするには管理者特権が必要です。  
  
 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ワーカー プロセスの名前は、デバッグ シナリオや IIS のバージョンによって異なります。 詳細については、「 [How to: Find the Name of the ASP.NET Process](../debugger/how-to-find-the-name-of-the-aspnet-process.md)」を参照してください。  
  
 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ワーカー プロセスを実行しているユーザー アカウントは、IIS を実行しているサーバーの machine.config ファイルを編集することによって変更できます。 これを行うには、 **インターネット インフォメーション サービス (IIS) マネージャー**を使用するのが最善です。 詳細については、次を参照してください。[方法: 実行、ワーカー プロセス ユーザー アカウントで](../debugger/how-to-run-the-worker-process-under-a-user-account.md)します。  
  
 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ワーカー プロセスを自分のユーザー アカウントで実行するように変更する場合、IIS を実行しているサーバーの管理者である必要はありません。  
  
> [!CAUTION]
>  [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ワーカー プロセスを別のアカウントで実行するように変更する場合は、[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ワーカー プロセスがそのアカウントで実行中にハックされた場合の影響を考慮する必要があります。 ASPNET および NETWORK SERVICE の各ユーザー アカウントは最小限のアクセス許可で実行されるので、プロセスがハックされた場合の損害が少なくなります。 高い権限のアクセス許可を持つアカウントで [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ワーカー プロセスを実行する必要がある場合、損害が大きくなる可能性があります。  
  
## <a name="see-also"></a>関連項目  
 [ASP.NET および AJAX アプリケーションのデバッグ](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [方法 : ユーザー アカウントでワーカー プロセスを実行する](../debugger/how-to-run-the-worker-process-under-a-user-account.md)



