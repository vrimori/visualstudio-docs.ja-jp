---
title: "Vspackage でのセキュリティのベスト プラクティス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c7ceb884ad060ea45c0fd204b5611ce284d3d2af
ms.lasthandoff: 02/22/2017

---
# <a name="best-practices-for-security-in-vspackages"></a>Vspackage でのセキュリティのベスト プラクティス
インストールする、[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]する、コンピューターに管理者資格情報でのコンテキストで実行する必要があります。 セキュリティおよび配置の基本単位、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]アプリケーションは、 [VSPackages](../../extensibility/internals/vspackages.md)します。 使用して、VSPackage を登録する必要があります[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、管理者の資格情報も必要があります。  
  
 管理者は、レジストリとファイル システムへの書き込みおよびすべてのコードを実行する完全なアクセス許可があります。 開発、展開、または、VSPackage をインストールするこれらのアクセス許可が必要です。  
  
 インストールされていると、すぐに VSPackage が完全に信頼します。 この高レベルの VSPackage に関連付けられているアクセス許可のためには、誤って悪意のある VSPackage をインストールすることはできます。  
  
 ユーザーは、信頼できるソースからのみ Vspackage をインストールすることを確認する必要があります。 Vspackage を開発している企業の名前を指定し、それらに署名する必要があります強く、改ざんされることをユーザーに保証するためには許可されません。 Vspackage を開発している企業では、web サービスを評価し、セキュリティの問題を解決へのリモート インストールなど、外部依存関係を調べる必要があります。  
  
 詳細については、.NET Framework の安全なコーディングのガイドラインを参照してください ([http://msdn.microsoft.com/library/d55zzx87.aspx](http://msdn.microsoft.com/library/d55zzx87.aspx))。  
  
## <a name="see-also"></a>関連項目  
 [追加のセキュリティ](http://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [DDEX セキュリティ](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)
