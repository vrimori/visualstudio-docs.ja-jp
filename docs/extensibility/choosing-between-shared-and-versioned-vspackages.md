---
title: "共有とバージョン管理された Vspackage の使い分け |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 20613722410bbe57231177eefafec79184d7741f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>共有とバージョン管理された Vspackage の使い分け
異なるバージョンの Visual Studio は、同じコンピューターに共存できます。 Vspackage の組み合わせをサポートできる[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]バージョン。  
  
 2 つの方法、共有方法またはバージョン管理の戦略のいずれかで Vspackage のサイド バイ サイド インストールを有効にすることができます。 複数のバージョンの存在を合わせて両方[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]のバージョンが関連付けられていると、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]です。  
  
 複数のバージョンで使用する共有の戦略では、1 つの VSPackage が登録されている[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 バージョン管理の戦略では、VSPackage の複数の Dll がインストールされているのバージョンごとに 1 つ[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]サポートしています。  
  
## <a name="shared-vspackages"></a>Vspackage の共有  
 複数のバージョンので、同じ VSPackage を使用する場合に適切な共有 VSPackage を使用して[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 共有の VSPackage を実装するのには、次の手順を行う必要があります。  
  
-   複数のバージョンと互換性のある VSPackage を行う[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 そのため、その 2 つの方法を使用できます。  
  
    -   最も古いバージョンの機能のみを使用する VSPackage を制限[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]サポートしています。  
  
    -   バージョンに合わせて調整する VSPackage をプログラミング[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]これを実行しています。 次に、新しいサービスのクエリが失敗すると、VSPackage を提示できますの旧バージョンでサポートされているその他のサービス[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。  
  
-   VSPackage を適切に登録します。 詳細については、次を参照してください。 [VSPackage の登録](../extensibility/internals/vspackage-registration.md)と[マネージ VSPackage の登録](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)です。  
  
-   ファイル拡張子を適切に登録します。 詳細については、次を参照してください。[のサイド バイ サイド展開ファイル名拡張子を登録する](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)です。  
  
-   VSPackage の適切なバージョンを展開するインストーラーの作成[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 詳細については、次を参照してください。 [Windows インストーラーで Vspackage をインストールする](../extensibility/internals/installing-vspackages-with-windows-installer.md)と[コンポーネント管理](../extensibility/internals/component-management.md)です。  
  
-   登録の衝突の問題に対処します。 詳細については、次を参照してください。 [VSPackage の登録](../extensibility/internals/vspackage-registration.md)です。  
  
-   共有とバージョン管理されたファイルの両方が参照カウントの複数のバージョンの安全なインストールと削除を許可するを考慮することを確認します。 詳細については、次を参照してください。[コンポーネント管理](../extensibility/internals/component-management.md)です。  
  
## <a name="versioned-vspackages"></a>バージョン管理された Vspackage  
 バージョン管理された VSPackage 戦略では、下のバージョンごとに 1 つの VSPackage を作成する[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]サポートしています。 これは、以降のバージョンので提供されるサービスを活用するために行うには適切な[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、VSPackage ごとが、他のユーザーを及ぼさずに発展させることができます。 いずれにしても、1 つのコード ベースから、または複数の独立したコード ベースから複数のバイナリを作成するバージョン管理された方法では、共有の方法よりも多くの初期開発が必要になる可能性があります。 また、追加のセットアップ作業しなければならない場合がいずれかのバージョンごとに別々 のセットアップまたはのバージョンを検出する 1 つのセットアップを作成する必要があるため[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]にインストールされていると、VSPackage をサポートしています。  
  
## <a name="binary-compatibility"></a>バイナリの互換性  
 一般に、バイナリの互換性は、以前のバージョンの Visual Studio の最新バージョンで実行する Visual Studio で開発したネイティブ コードの Vspackage を使用できます。 ただし、次の 3 つの重要な例外があります。  
  
-   VSPackage が、共通言語ランタイムの特定のバージョンに依存しているかどうかは、バージョンのことを確認する必要があります[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]が実行されています。  
  
-   VSPackage によっては、別の VSPackage または別の製品の特定の機能に依存関係があります。 その結果、VSPackage では、依存関係を満たす場所にのみ実行できます。  
  
-   VSPackage のセキュリティ問題の修正に影響を受ける、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] service pack または以降のバージョンの[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。 以前のバージョンのような場合、VSPackage が開発された、[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]のバージョンのでが実行されない[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]セキュリティ修正プログラムが適用された後にします。 ただしより新しいバージョンでパッケージを再構築し、以前のバージョンも実行できます。  
  
 バージョンを使用してマネージ Vspackage をビルドする必要があります[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]と[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]のターゲット バージョンに一致する[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。  
  
 だけでなく、VSPackage のバイナリのバイナリの互換性の計画、するもする必要がありますソリューションを検討およびプロジェクト ファイル形式。 VSPackage では、新しいプロジェクトの種類を作成する場合は、または複数のバージョンの 1 つのバージョンで実行できるかどうかを決定する必要があります[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 詳細については、次を参照してください。[カスタム プロジェクトのアップグレード](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects)です。  
  
## <a name="see-also"></a>参照  
 [Windows インストーラーで Vspackage をインストールします。](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [コンポーネント管理](../extensibility/internals/component-management.md)