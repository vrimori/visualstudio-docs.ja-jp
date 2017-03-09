---
title: "Managed Package Framework クラス | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Managed Package Framework、ヘルパー クラス"
  - "マネージ パッケージのヘルパー クラス"
  - "Visual Studio SDK、マネージ パッケージのヘルパー クラス"
  - "クラス [Visual Studio SDK]、Managed Package Framework"
ms.assetid: 15aedcc3-c79a-460b-b620-43223f1ae81e
caps.latest.revision: 24
caps.handback.revision: 24
manager: "douge"
---
# Managed Package Framework クラス
Managed Package Framework \(MPF\) クラスを使用して、マネージ コードを使用する VSPackages を作成できます。 このクラスには多くの VSPackage インターフェイス用の既定の実装が備わっています。 MPF は実装の詳細と複雑さを隠すため、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 統合製品を最小限のコードで作成できます。  
  
> [!WARNING]
>  Managed Package Framework クラスが含まれるほとんどのアセンブリが、Visual Studio SDK に付属しています。[プロジェクト用 Managed Package Framework](http://mpfproj11.codeplex.com/) で、プロジェクト用 Managed Package Framework のソース コードをダウンロードできます。  
  
## MPF 名前空間  
 次の表に、[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] で提供されている MPF 名前空間を一覧にして示します。  
  
|名前空間|目次|  
|----------|--------|  
|<xref:Microsoft.VisualStudio>|COM エラー、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 定数、Win32 Windows を処理するときに役立つクラスが含まれています。|  
|<xref:Microsoft.VisualStudio.Package>|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクト、エディター、MSBuild 用のマネージ コード ラッパーが入っています。|  
|<xref:Microsoft.VisualStudio.Shell>|多くの一般的な Visual Studio オブジェクトの実装の派生元となる MPF 基底クラスが含まれます。|  
|<xref:Microsoft.VisualStudio.Shell.Design>|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] デザイナーの拡張機能が含まれます。|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization>|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] シリアル化デザイナーの拡張機能が含まれます。|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization.CodeDom>|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CodeDom デザイナーの拡張機能が含まれます。|  
|<xref:Microsoft.VisualStudio.Shell.Flavor>|プロジェクトのサブタイプ \(「フレーバー」とも呼ばれます\) をサポートしています。|  
  
## 参照  
 [VSPackages およびマネージ パッケージ フレームワーク](/visual-cpp/misc/vspackages-and-the-managed-package-framework)   
 [Visual Studio の相互運用機能アセンブリを使用します。](../extensibility/internals/using-visual-studio-interop-assemblies.md)   
 [VSPackages およびマネージ パッケージ フレームワーク](/visual-cpp/misc/vspackages-and-the-managed-package-framework)