---
title: 'ASP.NET のデバッグ: システムの要件 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: d928b290a4156df07baa2a1bb88009853a7916cb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="aspnet-debugging-system-requirements"></a>ASP.NET のデバッグ : システム要件
ここでは、 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] のデバッグ シナリオに必要なソフトウェアとセキュリティの要件について説明します。  
  
-   ローカル デバッグ。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] と Web アプリケーションが同じコンピューターで実行されている場合のデバッグです。 このシナリオには、2 つのバージョンがあります。  
  
    -   [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] コードがファイル システムに存在する場合  
  
    -   [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] コードが IIS の Web サイトに存在する場合  
  
-   リモート デバッグ。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] はクライアント コンピューターで実行され、リモート サーバー コンピューターで実行されている Web アプリケーションをデバッグします。  
  
## <a name="security-requirements"></a>セキュリティ要件  
 リモート デバッグでは、ローカル コンピューターとリモート コンピューターが同じドメイン内または同じワークグループ内にセットアップされている必要があります。  
  
 デバッグ、 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] (アプリケーション プールでホストされる) ワーカー プロセスでは、そのプロセスをデバッグする権限が必要です。 既定では、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]として IIS 6.0 する前にアプリケーションを実行、 **ASPNET**ユーザー。 IIS 6.0 および IIS 7.0 で、 **NETWORK SERVICE**アカウントは、既定値です。 ワーカー プロセスが **ASPNET**(既定) または **NETWORK SERVICE**として実行されている場合、そのプロセスをデバッグするには管理者特権が必要です。

 > [!IMPORTANT]
 > Windows Server 2008 R2 以降では、ことをお勧めの使用、 [ApplicationPoolIdentity](/iis/manage/configuring-security/application-pool-identities)各アプリケーション プールの id として。
  
 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスの名前は、デバッグ シナリオや IIS のバージョンによって異なります。 詳細については、「[方法 : ASP.NET プロセスの名前を見つける](../debugger/how-to-find-the-name-of-the-aspnet-process.md)」を参照してください。  
  
 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスを実行しているユーザー アカウントは、IIS を実行しているサーバーの machine.config ファイルを編集することによって変更できます。 これを行うには、 **インターネット インフォメーション サービス (IIS) マネージャー**を使用するのが最善です。 詳細については、次を参照してください。[する方法: ワーカー プロセスで、ユーザー アカウントの実行](../debugger/how-to-run-the-worker-process-under-a-user-account.md)です。  
  
 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスを自分のユーザー アカウントで実行するように変更する場合、IIS を実行しているサーバーの管理者である必要はありません。  
  
> [!CAUTION]
>  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスを別のアカウントで実行するように変更する場合は、 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスがそのアカウントで実行中にハックされた場合の影響を考慮する必要があります。 ASPNET および NETWORK SERVICE の各ユーザー アカウントは最小限のアクセス許可で実行されるので、プロセスがハックされた場合の損害が少なくなります。 高い権限のアクセス許可を持つアカウントで [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスを実行する必要がある場合、損害が大きくなる可能性があります。  
  
## <a name="see-also"></a>関連項目  
 [ASP.NET アプリケーションをデバッグします。](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [方法 : ユーザー アカウントでワーカー プロセスを実行する](../debugger/how-to-run-the-worker-process-under-a-user-account.md)