---
title: "Excel 用にコード化された UI テストの拡張子のサンプル | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コード化された UI テスト、Excel 用の拡張機能"
ms.assetid: 451e4d14-7fac-42f9-af56-2bdc8414c6c7
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "mlearned"
manager: "douge"
---
# Excel 用にコード化された UI テストの拡張子のサンプル
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

サンプルの拡張コンポーネントは [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のコード化された UI テスト プロセスで実行し、`ExtensionPackage` クラスをベースにして多少階層的になります。  コントロール要素が最上位レベルで、`TechnologyManager` クラス、`ActionFilter` クラス、および `PropertyProvider` クラスはその次のレベルにあります。  
  
 ![Excel のテスト拡張アーキテクチャ](../test/media/excel_extarch.png "Excel\_ExtArch")  
Excel 拡張機能のアーキテクチャ  
  
## 拡張ポイント  
 これらのクラスはサンプルに実装される拡張ポイントを表し、[!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 用のコード化された UI テストを可能にします。  
  
### ExtensionPackage  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> クラスから継承されます。これはコード化された UI テストを拡張するための開始ポイントです。  この抽象クラスを実装すると、コード化された UI テスト フレームワークが、新しい UI をテストするために、カスタム UI テスト テクノロジ マネージャー、UI テスト プロパティ プロバイダー、および UI テスト アクション フィルターに内部アクセスできるようになります。  詳細については、「[ExtensionPackage クラス](../test/sample-excel-extension-extensionpackage-class.md)」を参照してください。  
  
### TechnologyManager  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> クラスから継承されます。このクラスは、テストの記録と再生用のテクノロジ マネージャーを提供します。  詳細については、「[TechnologyManager クラス](../test/sample-excel-extension-technologymanager-class.md)」を参照してください。  
  
### ActionFilter  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> クラスから継承されます。このクラスは、類似のテスト アクション結果を単一のテスト結果にまとめる基本クラスを提供します。  詳細については、「[ActionFilter クラス](../test/sample-excel-extension-actionfilter-class.md)」を参照してください。  
  
### テクノロジ要素  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> クラスから継承される基本クラスは、記録と再生が可能な UI テストでのテクノロジ要素の基盤を提供します。  詳細については、「[要素クラス](../test/sample-excel-extension-element-classes.md)」を参照してください。  
  
### PropertyProvider  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> クラスから継承されます。このクラスは、テストの記録と再生用の UI 要素のプロパティをサポートする基本クラスを提供します。  詳細については、「[PropertyProvider クラス](../test/sample-excel-extension-propertyprovider-class.md)」を参照してください。  
  
## 参照  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [ExtensionPackage クラス](../test/sample-excel-extension-extensionpackage-class.md)   
 [TechnologyManager クラス](../test/sample-excel-extension-technologymanager-class.md)   
 [ActionFilter クラス](../test/sample-excel-extension-actionfilter-class.md)   
 [要素クラス](../test/sample-excel-extension-element-classes.md)   
 [PropertyProvider クラス](../test/sample-excel-extension-propertyprovider-class.md)