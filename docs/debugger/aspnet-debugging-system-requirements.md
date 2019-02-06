---
title: 'ASP.NET のデバッグ: システム要件 |Microsoft Docs'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: d86b27a27884c0b8764c28a25ffb8ea9623efd9c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55025376"
---
# <a name="aspnet-debugging-system-requirements"></a>ASP.NET のデバッグ: システム要件
ここでは、 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] のデバッグ シナリオに必要なソフトウェアとセキュリティの要件について説明します。  
  
- ローカル デバッグ。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] と Web アプリケーションが同じコンピューターで実行されている場合のデバッグです。 このシナリオには、2 つのバージョンがあります。  
  
  - [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] コードがファイル システムに存在する場合  
  
  - [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] コードが IIS の Web サイトに存在する場合  
  
- リモート デバッグ。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] はクライアント コンピューターで実行され、リモート サーバー コンピューターで実行されている Web アプリケーションをデバッグします。  
  
## <a name="security-requirements"></a>セキュリティ要件  
 リモート デバッグでは、ローカル コンピューターとリモート コンピューターが同じドメイン内または同じワークグループ内にセットアップされている必要があります。  
  
 デバッグ、 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] (アプリケーション プールでホストされる) のワーカー プロセスをそのプロセスをデバッグする権限がある必要があります。 既定では、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]として IIS 6.0 より前のアプリケーションの実行、 **ASPNET**ユーザー。 IIS 6.0 および IIS 7.0 で、**ネットワーク サービス**アカウントが既定値。 ワーカー プロセスが **ASPNET**(既定) または **NETWORK SERVICE**として実行されている場合、そのプロセスをデバッグするには管理者特権が必要です。

 > [!IMPORTANT]
 > 使用はお勧め以降 Windows Server 2008 R2 では、 [ApplicationPoolIdentity](/iis/manage/configuring-security/application-pool-identities)として各アプリケーション プールの id。
  
 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスの名前は、デバッグ シナリオや IIS のバージョンによって異なります。 詳細については、「[方法 :ASP.NET プロセスの名前を見つける](../debugger/how-to-find-the-name-of-the-aspnet-process.md)」を参照してください。  
  
 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスを実行しているユーザー アカウントは、IIS を実行しているサーバーの machine.config ファイルを編集することによって変更できます。 これを行うには、 **インターネット インフォメーション サービス (IIS) マネージャー**を使用するのが最善です。 詳細については、「[方法 :ユーザー アカウントでワーカー プロセスを実行する](../debugger/how-to-run-the-worker-process-under-a-user-account.md)」を参照してください。  
  
 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスを自分のユーザー アカウントで実行するように変更する場合、IIS を実行しているサーバーの管理者である必要はありません。  
  
> [!CAUTION]
>  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスを別のアカウントで実行するように変更する場合は、 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスがそのアカウントで実行中にハックされた場合の影響を考慮する必要があります。 ASPNET および NETWORK SERVICE の各ユーザー アカウントは最小限のアクセス許可で実行されるので、プロセスがハックされた場合の損害が少なくなります。 高い権限のアクセス許可を持つアカウントで [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスを実行する必要がある場合、損害が大きくなる可能性があります。  
  
## <a name="see-also"></a>関連項目
 [ASP.NET アプリケーションをデバッグする](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [方法: ユーザー アカウントでワーカー プロセスを実行する](../debugger/how-to-run-the-worker-process-under-a-user-account.md)
