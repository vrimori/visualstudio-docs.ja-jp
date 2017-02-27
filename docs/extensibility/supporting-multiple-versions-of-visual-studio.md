---
title: "Visual Studio の複数のバージョンをサポートします。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio で複数のバージョンをサポートします。"
  - "Vspackages にある、サイド バイ サイドの互換性"
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Visual Studio の複数のバージョンをサポートします。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

用語 *サイド バイ サイド* インストールして、同じコンピューター上で製品の複数のバージョンを保持できることを意味します。 Vspackages にある、同じコンピューターにインストールされているいくつかの Visual Studio のバージョンをユーザーがいないことを意味します。 ただし、1 つのバージョンの Visual Studio に読み込まれる、VSPackages のサイド バイ サイド バージョンを持つことはできません。  
  
 VSPackage をサイド バイ サイド バージョンの Visual Studio に読み込まれることを行う前に、次の操作を検討してください。  
  
-   従おうと思っているサイド バイ サイドの実装方法を決定する必要があります。  
  
     詳細については、「[共有およびバージョン管理の VSPackages の使い分け](../extensibility/choosing-between-shared-and-versioned-vspackages.md)」を参照してください。  
  
-   ソリューションとプロジェクトのファイル形式は、実装戦略に収まる必要があります。  
  
     詳細については、次のトピックを参照してください。[カスタム プロジェクトのアップグレード](../misc/upgrading-custom-projects.md) および[サイド バイ サイド配置のファイル名拡張子を登録します。](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   インストーラーは、バージョン管理されたコンポーネントとも、すべてのバージョン間で共有されるコンポーネントを正しくインストールおよび登録できるようにの実装方法を処理する必要があります。  
  
     詳細については、次を参照してください。 [Windows インストーラーである Vspackage をインストールします。](../extensibility/internals/installing-vspackages-with-windows-installer.md) 、さらに [コンポーネントの管理](../extensibility/internals/component-management.md)します。  
  
    > [!NOTE]
    >  対応するバージョンの Visual Studio のバージョンをインストールするインストールも、 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]です。 たとえば、バージョン 4.0 と 4.5 の Visual Studio 2010 と Visual Studio 2012 を同じコンピューターにインストールするインストールも、 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], 、それぞれします。  
  
## このセクションの内容  
 [共有およびバージョン管理の VSPackages の使い分け](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 VSPackage でのサイド バイ サイドの問題を解決する方法について説明します。  
  
 [サイド バイ サイド配置のファイル名拡張子を登録します。](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 サイド バイ サイドのシナリオでは、VSPackage がファイルの関連付けを登録する方法について説明します。  
  
## 関連項目  
 [VSPackage のインストール](../misc/installing-vspackages.md)  
 ビルドし、Vspackage をインストールする方法と、同時に複数のバージョンの Visual Studio を実行しているユーザーをサポートする方法について説明します。