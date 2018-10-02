---
title: 共有およびバージョン管理 Vspackage の選択 |Microsoft Docs
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
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 14b2ec1884fcbbebb28667e04d03e2c1424175dd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47549178"
---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>共有 VSPackage とバージョン管理 VSPackage の選択
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[共有間で選択してバージョン管理 Vspackage](https://docs.microsoft.com/visualstudio/extensibility/choosing-between-shared-and-versioned-vspackages)します。  
  
異なるバージョンの Visual Studio は、同じコンピューターに共存できます。 Vspackage が任意の組み合わせをサポートできる[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]バージョン。  
  
 Vspackage の 2 つの方法、共有戦略またはバージョン管理戦略のいずれかでのサイド バイ サイドでインストールを有効にすることができます。 複数のバージョンの存在を合わせて両方[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]のバージョンに関連付けられていると、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]します。  
  
 複数のバージョンで使用するため共有戦略の 1 つの VSPackage が登録されている[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。 バージョン管理戦略の VSPackage の複数の Dll がインストールされている、1 つのバージョンごとに[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]サポートしています。  
  
## <a name="shared-vspackages"></a>共有 Vspackage  
 複数のバージョンで同じ VSPackage を使用する場合は適切な共有 VSPackage を使用して、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。 共有 VSPackage を実装するには、次の手順を行う必要があります。  
  
-   VSPackage の複数のバージョンの互換性を確保[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。 そのため、その 2 つの方法を使用できます。  
  
    -   制限の最も古いバージョンの機能のみを使用するように VSPackage[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]サポートしています。  
  
    -   プログラムのバージョンに適応するために VSPackage[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]が実行されています。 次に、新しいサービスのクエリが失敗した場合、VSPackage を提供できますの旧バージョンでサポートされている他のサービス[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。  
  
-   VSPackage を適切に登録します。 詳細については、次を参照してください。 [VSPackage の登録](../extensibility/internals/vspackage-registration.md)と[マネージ VSPackage の登録](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)します。  
  
-   ファイルの拡張機能を適切に登録します。 詳細については、次を参照してください。[サイド バイ サイドで配置のファイル名拡張子を登録する](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)します。  
  
-   VSPackage の適切なバージョンをデプロイするインストーラーを作成[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]です。 詳細については、次を参照してください。 [Windows インストーラーで Vspackage をインストールする](../extensibility/internals/installing-vspackages-with-windows-installer.md)と[コンポーネント管理](../extensibility/internals/component-management.md)します。  
  
-   登録の競合の問題に対処します。 詳細については、次を参照してください。 [VSPackage の登録](../extensibility/internals/vspackage-registration.md)します。  
  
-   共有およびバージョン管理の両方のファイルが参照カウントの複数のバージョンの安全なインストールと削除を許可するを考慮することを確認します。 詳細については、次を参照してください。[コンポーネント管理](../extensibility/internals/component-management.md)します。  
  
## <a name="versioned-vspackages"></a>Vspackage のバージョン管理  
 バージョン管理 VSPackage 戦略では、下のバージョンごとに 1 つの VSPackage を作成する[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]サポートしています。 これは、以降のバージョンのによって提供されるサービスの利用を行うには適切な[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]、VSPackage ごとが、他の影響を与えずに進化させることができます。 それにもかかわらず、1 つのコード ベースから、または複数の独立したコード ベースから複数のバイナリの作成のバージョン管理戦略では、共有戦略よりも多くの初期開発が必要になる可能性があります。 また、追加のセットアップ作業がいずれかのバージョンごとに別々 にセットアップまたはのバージョンを検出する 1 つのセットアップを作成する必要がありますので、必要と[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]にインストールされていると、VSPackage をサポートしています。  
  
## <a name="binary-compatibility"></a>バイナリの互換性  
 一般に、バイナリの互換性はネイティブ コードの Vspackage では、以降のバージョンの Visual Studio を実行する Visual Studio の以前のバージョンを使用して開発できます。 ただし、これには次の 3 つの重要な例外があります。  
  
-   かどうかは、VSPackage が、共通言語ランタイムの特定のバージョンに依存してでのバージョンを確認する必要がありますし[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]が実行されています。  
  
-   VSPackage では、別の VSPackage または他の製品の特定の機能の依存関係があります。 その結果、VSPackage では、依存関係を満たす場所にのみ実行できます。  
  
-   VSPackage のセキュリティ問題の修正に影響を受ける、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] service pack または以降のバージョンの[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。 以前のバージョンのような場合、VSPackage が開発した、[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]のバージョンで実行されない可能性[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]セキュリティ修正プログラムが適用された後にします。 ただしより新しいバージョンで、パッケージを再構築し、以前のバージョンも実行できます。  
  
 バージョンを使用して、マネージ Vspackage をビルドする必要があります[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]と[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]のターゲット バージョンに一致する[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。  
  
 だけでなく、VSPackage のバイナリのバイナリの互換性の計画、するもする必要がありますソリューションを検討してプロジェクト ファイル形式。 VSPackage では、新しいプロジェクトの種類を作成する場合、または複数のバージョンの 1 つのバージョンで実行できるかどうかを決定する必要があります[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。 詳細については、次を参照してください。[カスタム プロジェクトのアップグレード](../misc/upgrading-custom-projects.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Windows インストーラーによる Vspackage のインストール](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [コンポーネント管理](../extensibility/internals/component-management.md)

