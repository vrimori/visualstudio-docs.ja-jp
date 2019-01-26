---
title: '方法: SharePoint ソリューションのカスタムのフィーチャーとパッケージ検証規則を作成する |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 794974991216a521bf2ca4afb1e958716a3bf735
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874082"
---
# <a name="how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions"></a>方法: SharePoint ソリューションの検証規則を使用したカスタムのフィーチャーとパッケージを作成します。
  Visual Studio によって生成された、ソリューション パッケージの検証にカスタム検証規則を作成することができます。 選択して、すべての機能またはパッケージの完全な検証を行うことができます**検証**パッケージまたは機能のコンテキスト メニューから、 **PackagingExplorer**します。 かを確認するかどうか、パッケージまたは機能が有効な状態でプロジェクトを新しい SharePonit プロジェクト項目や機能を追加すると、部分検証を実行します。  
  
### <a name="to-create-a-custom-package-validation-rule"></a>カスタム パッケージの検証規則を作成するには  
  
1.  クラス ライブラリ プロジェクトを作成します。  
  
2.  次のアセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  次のインターフェイスの 1 つを実装するクラスを作成します。  
  
    -   パッケージの検証規則を作成するには、実装、<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>インターフェイス。  
  
    -   機能の検証規則を作成するには、実装、<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>インターフェイス。  
  
4.  追加、<xref:System.ComponentModel.Composition.ExportAttribute>クラスにします。 この属性は、Visual Studio を検出して読み込む、検証規則を使用します。 渡す、<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>または<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>属性コンス トラクターの型。  
  
## <a name="example"></a>例  
 次のコード例では、カスタムのフィーチャー検証規則を作成する方法を示します。  
  
 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]  
  
## <a name="compile-the-code"></a>コードのコンパイル  
 この例では、次のアセンブリへの参照が必要です。  
  
-   Microsoft.VisualStudio.SharePoint します。  
  
-   System.ComponentModel.Composition します。  
  
## <a name="deploy-the-extension"></a>拡張機能をデプロイします。  
 拡張機能を展開するには、作成、[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]アセンブリおよびその他の拡張機能を配布するファイルの拡張機能 (VSIX) にパッケージ化します。 詳細については、次を参照してください。 [、SharePoint 用の拡張機能の展開ツールの Visual Studio で](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)します。  
  
## <a name="see-also"></a>関連項目
 [SharePoint のパッケージ化と配置を拡張します。](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
