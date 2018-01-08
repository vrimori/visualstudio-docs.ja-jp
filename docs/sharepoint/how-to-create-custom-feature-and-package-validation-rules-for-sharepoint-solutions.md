---
title: "方法: SharePoint ソリューションのカスタムのフィーチャーとパッケージ検証規則を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
ms.assetid: 17e818f8-0f3a-4a96-a6fc-1634ddb4825d
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 20a56a2f6582a08270292cd86cf62a9344d8565f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions"></a>方法: SharePoint ソリューションのフィーチャーとパッケージのカスタム検証規則を作成する
  Visual Studio によって生成されるソリューション パッケージを確認するカスタム検証規則を作成することができます。 選択すると、すべての機能またはパッケージの完全な検証を行うことができます**検証**パッケージまたは機能のコンテキスト メニューから、 **PackagingExplorer**です。 新しい SharePonit プロジェクト項目または機能を決定するかどうか、パッケージまたは機能が有効な状態でプロジェクトを追加するときに、部分検証を実行します。  
  
### <a name="to-create-a-custom-package-validation-rule"></a>カスタムのパッケージ検証規則を作成するには  
  
1.  クラス ライブラリ プロジェクトを作成します。  
  
2.  次のアセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  次のインターフェイスのいずれかを実装するクラスを作成します。  
  
    -   パッケージ検証規則を作成するには、実装、<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>インターフェイスです。  
  
    -   フィーチャー検証規則を作成するには、実装、<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>インターフェイスです。  
  
4.  追加、<xref:System.ComponentModel.Composition.ExportAttribute>クラスにします。 この属性は、Visual Studio を検出して読み込むとき、検証規則を使用できます。 渡す、<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>または<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>属性コンス トラクターの型。  
  
## <a name="example"></a>例  
 次のコード例では、カスタムのフィーチャー検証規則を作成する方法を示します。  
  
 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例では、次のアセンブリへの参照が必要です。  
  
-   Microsoft.VisualStudio.SharePoint です。  
  
-   System.ComponentModel.Composition です。  
  
## <a name="deploying-the-extension"></a>拡張機能の配置  
 拡張機能を展開するには、作成、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]アセンブリおよびその他の拡張機能を配布するファイルの拡張機能 (VSIX) にパッケージ化します。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツールの拡張機能の配置](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)です。  
  
## <a name="see-also"></a>参照  
 [SharePoint のパッケージ化と配置の拡張](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  