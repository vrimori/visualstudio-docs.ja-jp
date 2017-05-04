---
title: "How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, extending deployment"
  - "SharePoint development in Visual Studio, validation rules"
ms.assetid: 17e818f8-0f3a-4a96-a6fc-1634ddb4825d
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions
  Visual Studio で生成されたソリューション パッケージを検証するために、カスタム検証規則を作成できます。  **パッケージングエクスプローラー**でパッケージまたはフィーチャーのコンテキスト メニューの **\[検証\]** をクリックすると、フィーチャーまたはパッケージの全体に対する完全検証を実行できます。  新しい SharePoint プロジェクト項目またはフィーチャーをプロジェクトに追加する場合に、パッケージまたはフィーチャーが有効な状態になるかどうかを確認するには、部分検証を実行します。  
  
### カスタムのパッケージ検証規則を作成するには  
  
1.  クラス ライブラリ プロジェクトを作成します。  
  
2.  次のアセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  次のいずれかのインターフェイスを実装するクラスを作成します。  
  
    -   パッケージ検証規則を作成するには、<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> インターフェイスを実装します。  
  
    -   フィーチャー検証規則を作成するには、<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> インターフェイスを実装します。  
  
4.  クラスに <xref:System.ComponentModel.Composition.ExportAttribute> を追加します。  この属性によって、Visual Studio で検証規則を検出し、読み込むことができます。  この属性のコンストラクターに <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> 型または <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> 型を渡します。  
  
## 例  
 次のコード例は、カスタムのフィーチャー検証規則を作成する方法を示しています。  
  
 [!code-csharp[SPExtensibility.FeatureValidation#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.featurevalidation/cs/extension/customfeaturevalidationrule.cs#1)]
 [!code-vb[SPExtensibility.FeatureValidation#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.featurevalidation/vb/extension/customvalidationrule.vb#1)]  
  
## コードのコンパイル  
 この例は、次のアセンブリへの参照を必要とします。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 拡張機能の配置  
 拡張機能を配置するには、アセンブリと、拡張機能に同梱する必要のあるその他のファイルを提供するための [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) パッケージを作成します。  詳細については、「[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
## 参照  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  