---
title: Managed Package Framework クラス |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed package framework, helper classes
- managed package helper classes
- Visual Studio SDK, managed package helper classes
- classes [Visual Studio SDK], managed package framework
ms.assetid: 15aedcc3-c79a-460b-b620-43223f1ae81e
caps.latest.revision: 24
manager: douge
ms.openlocfilehash: 931e73af72d2239ec04ac248b9fa426fe24f249a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188995"
---
# <a name="managed-package-framework-classes"></a>Managed Package Framework クラス
Managed Package Framework (MPF) クラスを使用して、マネージド コードを使用する VSPackages を作成できます。 このクラスには多くの VSPackage インターフェイス用の既定の実装が備わっています。 MPF は実装の詳細と複雑さを隠すため、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 統合製品を最小限のコードで作成できます。  
  
> [!WARNING]
>  Managed Package Framework クラスが含まれるほとんどのアセンブリが、Visual Studio SDK に付属しています。 [プロジェクト用 Managed Package Framework](http://mpfproj11.codeplex.com/)で、プロジェクト用 Managed Package Framework のソース コードをダウンロードできます。  
  
## <a name="mpf-namespaces"></a>MPF 名前空間  
 次の表に、 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]で提供されている MPF 名前空間を一覧にして示します。  
  
|名前空間|目次|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio>|COM エラー、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 定数、Win32 Windows を処理するときに役立つクラスが含まれています。|  
|<xref:Microsoft.VisualStudio.Package>|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロジェクト、エディター、MSBuild 用のマネージド コード ラッパーが入っています。|  
|<xref:Microsoft.VisualStudio.Shell>|多くの一般的な Visual Studio オブジェクトの実装の派生元となる MPF 基底クラスが含まれます。|  
|<xref:Microsoft.VisualStudio.Shell.Design>|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] デザイナーの拡張機能が含まれます。|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization>|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] シリアル化デザイナーの拡張機能が含まれます。|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization.CodeDom>|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] CodeDom デザイナーの拡張機能が含まれます。|  
|<xref:Microsoft.VisualStudio.Shell.Flavor>|プロジェクトのサブタイプ (「フレーバー」とも呼ばれます) をサポートしています。|  
  
## <a name="see-also"></a>関連項目  
 [VSPackages およびマネージ パッケージ フレームワーク](../misc/vspackages-and-the-managed-package-framework.md)   
 [Visual Studio 相互運用機能アセンブリを使用します。](../extensibility/internals/using-visual-studio-interop-assemblies.md)   
 [VSPackages およびマネージド パッケージ フレームワーク](../misc/vspackages-and-the-managed-package-framework.md)