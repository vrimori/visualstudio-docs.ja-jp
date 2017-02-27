---
title: "共有およびバージョン管理の VSPackages の使い分け | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SxS"
  - "サイド バイ サイド インストール"
  - "サイド バイ サイドのインストール [Visual Studio SDK]"
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# 共有およびバージョン管理の VSPackages の使い分け
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

異なるバージョンの Visual Studio は、同じコンピューター上に共存できます。 Vspackages にある任意の組み合わせをサポートできる [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] バージョンです。  
  
 2 つの戦略、共有の戦略やバージョン管理の戦略のいずれかである Vspackage のサイド バイ サイド インストールを有効にすることができます。 両方に対応する複数のバージョンのプレゼンス [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のバージョンが関連付けられていると、 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]です。  
  
 複数のバージョンで使用する共有戦略の 1 つの VSPackage が登録されている [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。 バージョン管理された方法で複数の VSPackage Dll がインストールされている、1 つのバージョンごとに [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] サポートしています。  
  
## 共有 vspackages にあります。  
 複数のバージョンで同じ VSPackage を使用する場合は適切な共有 vs パッケージを使用して、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 共有 vs パッケージを実装するのには、以下の手順を実行する必要があります。  
  
-   VSPackage を複数のバージョンの互換性を持たせる [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。 そのため、その 2 つの方法を使用できます。  
  
    -   制限の最も古いバージョンの機能のみを使用する、VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] サポートしています。  
  
    -   プログラムのバージョンに合わせて、VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を実行しています。 次に、新しいサービスのクエリが失敗した場合、VSPackage を提供できますの以前のバージョンでサポートされているその他のサービス [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。  
  
-   VSPackage を適切に登録します。 詳細については、次のトピックを参照してください。[VSPackage の登録](../extensibility/internals/vspackage-registration.md) および[Managed VSPackage Registration](http://msdn.microsoft.com/ja-jp/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
-   ファイルの拡張機能を適切に登録します。 詳細については、「[サイド バイ サイド配置のファイル名拡張子を登録します。](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)」を参照してください。  
  
-   適切なバージョンについては、VSPackage を展開するインストーラーの作成 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。 詳細については、[Windows インストーラーである Vspackage をインストールします。](../extensibility/internals/installing-vspackages-with-windows-installer.md) および [コンポーネントの管理](../extensibility/internals/component-management.md) を参照してください。  
  
-   登録の競合の問題に対処します。 詳細については、「[VSPackage の登録](../extensibility/internals/vspackage-registration.md)」を参照してください。  
  
-   共有およびバージョン管理の両方のファイルが参照カウントの複数のバージョンの安全なインストールと削除を許可するようを尊重することを確認します。 詳細については、「[コンポーネントの管理](../extensibility/internals/component-management.md)」を参照してください。  
  
## バージョン管理された vspackages にあります。  
 バージョン管理された VSPackage 戦略では、下のバージョンごとに 1 つの VSPackage を作成する [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] サポートしています。 以降のバージョンのによって提供されるサービスを活用するために予測される場合に適切なこれは [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], 、各 VSPackage が、その他の影響を与えずに進化させることができます。 それにもかかわらず、バージョン管理された、シングル コード ベース、または複数の独立したコード ベースに複数のバイナリを作成する方法では、共有の方法よりも多くの初期開発を伴います。 また、追加のセットアップ作業しなければならない場合がいずれかのバージョンごとに別々 のセットアップまたはのバージョンが検出される 1 つのセットアップを作成する必要があるため [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] インストールされていて、VSPackage をサポートしています。  
  
## バイナリの互換性  
 一般に、バイナリの互換性により、以前のバージョンの Visual Studio の新しいバージョンで実行する Visual Studio で開発されているネイティブ コード vspackages にあります。 ただし、これには次の 3 つの重要な例外があります。  
  
-   VSPackage を共通言語ランタイムの特定のバージョンに依存しているかどうかは、どのバージョンのことを確認する必要があります [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] が実行されています。  
  
-   VSPackage 別 VSPackage または他の製品の特定の機能に依存している可能性があります。 その結果、VSPackage では、依存関係を満たす場所にのみ実行できます。  
  
-   VSPackage のセキュリティ問題の修正に影響を受ける、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] service pack または以降のバージョンの [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 以前のバージョンでそのような場合は、VSPackage に開発された、 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] のバージョンで実行されない [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] セキュリティ修正プログラムが適用された後です。 ただし、以降のバージョンで、パッケージを再構築し、以前のバージョンも実行できます。  
  
 バージョンを使用してマネージ VSPackages を構築する必要が [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] と [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] のターゲット バージョンに一致する [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。  
  
 VSPackage バイナリ用のバイナリの互換性の計画、だけでなくもする必要がありますソリューションを検討してプロジェクトのファイル形式です。 VSPackage では、新しいプロジェクトの種類を作成する場合は、または複数のバージョンの 1 つのバージョンで実行できるかどうかを決定する必要があります [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。 詳細については、「[カスタム プロジェクトのアップグレード](../misc/upgrading-custom-projects.md)」を参照してください。  
  
## 参照  
 [Windows インストーラーである Vspackage をインストールします。](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [コンポーネントの管理](../extensibility/internals/component-management.md)