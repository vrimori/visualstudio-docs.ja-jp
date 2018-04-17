---
title: Visual Studio の複数のバージョンをサポートする |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 317ec1f214d18989c3b2c5c27fe9df9309239631
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Visual Studio の複数のバージョンをサポートします。
用語*サイド バイ サイド*インストールおよび同じコンピューター上で製品の複数のバージョンを維持できることを意味します。 つまり、Vspackage の場合、ユーザーが同じコンピューターにインストールされているいくつかの Visual Studio のバージョンを持つことができます。 ただし、1 つのバージョンの Visual Studio に読み込まれる、Vspackage のバージョンをサイド バイ サイドを持つことはできません。  
  
 サイド バイ サイドのバージョンの Visual Studio に読み込まれること、VSPackage を行う前に、次の操作を検討してください。  
  
-   実行するどのサイド バイ サイドの実装戦略を決定する必要があります。  
  
     詳細については、次を参照してください。[共有間で選択するとバージョン管理された Vspackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md)です。  
  
-   ソリューションおよびプロジェクト ファイルの形式は、実装戦略を収める必要があります。  
  
     詳細については、次を参照してください。[カスタム プロジェクトのアップグレード](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects)と[のサイド バイ サイド展開ファイル名拡張子を登録する](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)です。  
  
-   バージョン管理されたコンポーネントは、およびも、すべてのバージョン間で共有されるコンポーネントを正しくインストールおよび登録できるように、インストーラーは、実装戦略を処理する必要があります。  
  
     詳細については、次を参照してください。 [Windows インストーラーで Vspackage をインストールする](../extensibility/internals/installing-vspackages-with-windows-installer.md)、さらに[コンポーネント管理](../extensibility/internals/component-management.md)です。  
  
    > [!NOTE]
    >  対応するバージョンの Visual Studio のバージョンをインストールするインストールも、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]です。 たとえば、同じコンピューターに Visual Studio 2010 と Visual Studio 2012 のインストールもインストールされますのバージョン 4.0 および 4.5、 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]、それぞれします。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [共有 VSPackage と バージョン管理 VSPackage の選択](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 VSPackage でサイド バイ サイドの問題を解決する方法について説明します。  
  
 [side-by-side 配置に対してファイル名拡張子を登録する](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 サイド バイ サイドのシナリオでは、VSPackage がファイルの関連付けを登録する方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [Windows インストーラーによる VSPackage のインストール](../extensibility/internals/installing-vspackages-with-windows-installer.md)  
