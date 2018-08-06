---
title: Vspackage ではセキュリティのベスト プラクティス |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b5b3b86736a5425640c1a87df6a3e2c6e6cec0c5
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513349"
---
# <a name="best-practices-for-security-in-vspackages"></a>Vspackage のセキュリティのためのベスト プラクティス
インストールする、[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]する、コンピューターには、管理者の資格情報のコンテキストで実行する必要があります。 セキュリティおよび配置の基本単位、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]アプリケーションは、 [VSPackage](../../extensibility/internals/vspackages.md)します。 使用して VSPackage を登録する必要があります[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、資格情報を管理する必要があります。  
  
 管理者は、レジストリとファイル システムに書き込むと、任意のコードを実行する完全なアクセス許可があります。 開発、デプロイ、または VSPackage をインストールするこれらのアクセス許可が必要です。  
  
 インストールされているとすぐに VSPackage が完全に信頼されます。 この高レベルの VSPackage に関連付けられている権限、ためには、誤って悪意のある VSPackage をインストールすることはできます。  
  
 ユーザーは、信頼できるソースからのみ Vspackage をインストールすることを確認してください。 VSPackages を開発する企業の名前を指定し、それらに署名する必要があります厳密に、ユーザーのため、その改ざんを防止します。 企業の VSPackages を開発するには、web サービスを評価し、セキュリティの問題の修正のリモート インストールなど、外部依存関係を調べる必要があります。  
  
 詳細については、次を参照してください。[コーディングのガイドラインを .NET Framework のセキュリティで保護された](http://msdn.microsoft.com/library/d55zzx87.aspx)します。  
  
## <a name="see-also"></a>関連項目  
 [追加のセキュリティ](http://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [DDEX セキュリティ](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)