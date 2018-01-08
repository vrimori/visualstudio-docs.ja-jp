---
title: "Vspackage でセキュリティのベスト プラクティス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 71f06fdd67e4f1789637c2d935f0d25a06eb9863
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="best-practices-for-security-in-vspackages"></a>Vspackage でセキュリティのベスト プラクティス
インストールする、[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]する、コンピューターに管理者の資格情報のコンテキストで実行する必要があります。 セキュリティおよび配置の基本単位、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]アプリケーションは、 [Vspackage](../../extensibility/internals/vspackages.md)です。 使用して、VSPackage を登録する必要があります[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、管理者の資格情報も必要があります。  
  
 管理者は、レジストリおよびファイル システムへの書き込みを任意のコードを実行する完全なアクセス許可があります。 開発、配置、または VSPackage をインストールするこれらのアクセス許可が必要です。  
  
 インストールされているようになったら、VSPackage は完全に信頼されたです。 この高レベルの VSPackage に関連付けられている権限、ためには、誤って悪意のある VSPackage をインストールすることはできます。  
  
 ユーザーは、信頼できるソースからのみ、Vspackage をインストールすることを確認します。 Vspackage を開発している企業の名前を指定し、それらに署名する必要があります強く、改ざんされることを確認することはできません。 Vspackage を開発している企業では、web サービスを評価し、セキュリティの問題を解決するリモート インストールなど、外部依存関係を調べる必要があります。  
  
 詳細については、.NET Framework の安全なコーディングのガイドラインを参照してください。 ([http://msdn.microsoft.com/library/d55zzx87.aspx](http://msdn.microsoft.com/library/d55zzx87.aspx))。  
  
## <a name="see-also"></a>参照  
 [追加のセキュリティ](http://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [DDEX セキュリティ](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)