---
title: Vspackage ではセキュリティのベスト プラクティス |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e294995a25b0369ab839680a97fe670f9a99508d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536042"
---
# <a name="best-practices-for-security-in-vspackages"></a>VSPackage のセキュリティのベスト プラクティス
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Vspackage のセキュリティのためのベスト プラクティス](https://docs.microsoft.com/visualstudio/extensibility/internals/best-practices-for-security-in-vspackages)します。  
  
インストールする、[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]する、コンピューターには、管理者の資格情報のコンテキストで実行する必要があります。 セキュリティおよび配置の基本単位、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]アプリケーションは、 [Vspackage](../../extensibility/internals/vspackages.md)します。 使用して VSPackage を登録する必要があります[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]、資格情報を管理する必要があります。  
  
 管理者は、レジストリとファイル システムに書き込むと、任意のコードを実行する完全なアクセス許可があります。 開発、デプロイ、または VSPackage をインストールするこれらのアクセス許可が必要です。  
  
 インストールされているとすぐに VSPackage が完全に信頼されます。 この高レベルの VSPackage に関連付けられている権限、ためには、誤って悪意のある VSPackage をインストールすることはできます。  
  
 ユーザーは、信頼できるソースからのみ Vspackage をインストールすることを確認してください。 VSPackages を開発する企業の名前を指定し、それらに署名する必要があります厳密に、ユーザーのため、その改ざんを防止します。 企業の VSPackages を開発するには、web サービスを評価し、セキュリティの問題の修正のリモート インストールなど、外部依存関係を調べる必要があります。  
  
 詳細については、.NET Framework の安全なコーディングのガイドラインを参照してください。 ([http://msdn.microsoft.com/library/d55zzx87.aspx](http://msdn.microsoft.com/library/d55zzx87.aspx))。  
  
## <a name="see-also"></a>関連項目  
 [追加のセキュリティ](http://msdn.microsoft.com/library/44a5c651-6246-4310-b371-65378917c799)   
 [DDEX セキュリティ](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)

