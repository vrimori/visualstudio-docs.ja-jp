---
title: Managed Package Framework クラス |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: 38f159df52c99554ed931269f29ad57e72745b5d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546819"
---
# <a name="managed-package-framework-classes"></a>Managed Package Framework クラス
Managed Package Framework (MPF) クラスを使用して、マネージド コードを使用する VSPackages を作成できます。 このクラスには多くの VSPackage インターフェイス用の既定の実装が備わっています。 実装の詳細と複雑さを非表示、MPF を使用すると、作成[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]最小限のコードで製品を統合します。  
  
> [!WARNING]
>  Managed Package Framework クラスが含まれるほとんどのアセンブリが、Visual Studio SDK に付属しています。 [プロジェクト用 Managed Package Framework](http://mpfproj11.codeplex.com/)で、プロジェクト用 Managed Package Framework のソース コードをダウンロードできます。  
  
## <a name="mpf-namespaces"></a>MPF 名前空間  
 次の表に、によって提供される MPF 名前空間、[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]します。  
  
|名前空間|目次|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio>|COM のエラーを処理するための便利なクラスが含まれます[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]定数、および Win32 windows。|  
|<xref:Microsoft.VisualStudio.Package>|マネージ コード ラッパーが含まれています[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]プロジェクト、エディター、および MSBuild です。|  
|<xref:Microsoft.VisualStudio.Shell>|多くの一般的な Visual Studio オブジェクトの実装の派生元となる MPF 基底クラスが含まれます。|  
|<xref:Microsoft.VisualStudio.Shell.Design>|含む[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]デザイナーの拡張機能。|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization>|含む[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]デザイナーの拡張機能をシリアル化します。|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization.CodeDom>|含む[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]CodeDom デザイナーの拡張機能。|  
|<xref:Microsoft.VisualStudio.Shell.Flavor>|プロジェクトのサブタイプ (「フレーバー」とも呼ばれます) をサポートしています。|  
  
## <a name="see-also"></a>関連項目  
 [VSPackages およびマネージ パッケージ フレームワーク](../misc/vspackages-and-the-managed-package-framework.md)   
 [Visual Studio 相互運用機能アセンブリを使用します。](../extensibility/internals/using-visual-studio-interop-assemblies.md)   
 [VSPackages およびマネージド パッケージ フレームワーク](../misc/vspackages-and-the-managed-package-framework.md)