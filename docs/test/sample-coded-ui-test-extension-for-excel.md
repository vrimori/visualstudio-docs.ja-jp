---
title: "Excel 用にコード化された UI テストの拡張機能のサンプル | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- coded UI tests, extensions for Excel
ms.assetid: 451e4d14-7fac-42f9-af56-2bdc8414c6c7
caps.latest.revision: 13
ms.author: douge
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: 46e8adfd4e4b66e743af8a0db5aecd3f40eb2de7
ms.lasthandoff: 04/04/2017

---
# <a name="sample-coded-ui-test-extension-for-excel"></a>Excel 用にコード化された UI テストの拡張子のサンプル
サンプルの拡張機能コンポーネントは [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のコード化された UI テスト プロセスで実行され、`ExtensionPackage` クラスをベースにして多少階層的になります。 コントロール要素が最上位レベルで、`TechnologyManager` クラス、`ActionFilter` クラス、および `PropertyProvider` クラスはその次のレベルにあります。  
  
 ![Excel のテスト拡張機能アーキテクチャ](../test/media/excel_extarch.png "Excel_ExtArch")  
Excel 拡張機能アーキテクチャ  
  
## <a name="extension-points"></a>拡張ポイント  
 これらのクラスはサンプルに実装される拡張ポイントを表し、[!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 用のコード化された UI テストを可能にします。  
  
### <a name="extensionpackage"></a>ExtensionPackage  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> クラスから継承されます。これはコード化された UI テストの拡張用のエントリ ポイントです。 この抽象クラスを実装すると、コード化された UI テスト フレームワークが、新しい UI をテストするために、カスタム UI テスト テクノロジ マネージャー、UI テスト プロパティ プロバイダー、および UI テスト アクション フィルターに内部アクセスできるようになります。 詳細については、「[ExtensionPackage Class (ExtensionPackage クラス)](../test/sample-excel-extension-extensionpackage-class.md)」を参照してください。  
  
### <a name="technologymanager"></a>TechnologyManager  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> クラスから継承されます。このクラスは、テストの記録と再生用のテクノロジ マネージャーを提供します。 詳細については、「[TechnologyManager Class (TechnologyManager クラス)](../test/sample-excel-extension-technologymanager-class.md)」を参照してください。  
  
### <a name="actionfilter"></a>ActionFilter  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> クラスから継承されます。このクラスは、類似のテスト アクション結果を単一のテスト結果にまとめる基底クラスを提供します。 詳細については、「[ActionFilter Class (ActionFilter クラス)](../test/sample-excel-extension-actionfilter-class.md)」を参照してください。  
  
### <a name="technology-elements"></a>テクノロジ要素  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> クラスから継承される基底クラスは、記録と再生が可能な UI テストでのテクノロジ要素の基盤を提供します。 詳細については、「[Element Classes (要素クラス)](../test/sample-excel-extension-element-classes.md)」を参照してください。  
  
### <a name="propertyprovider"></a>PropertyProvider  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> クラスから継承されます。このクラスは、テストの記録と再生用の UI 要素のプロパティをサポートする基底クラスを提供します。 詳細については、「[PropertyProvider Class (PropertyProvider クラス)](../test/sample-excel-extension-propertyprovider-class.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [ExtensionPackage Class (ExtensionPackage クラス)](../test/sample-excel-extension-extensionpackage-class.md)   
 [TechnologyManager Class (TechnologyManager クラス)](../test/sample-excel-extension-technologymanager-class.md)   
 [ActionFilter Class (ActionFilter クラス)](../test/sample-excel-extension-actionfilter-class.md)   
 [Element Classes (要素クラス)](../test/sample-excel-extension-element-classes.md)   
 [PropertyProvider Class (PropertyProvider クラス)](../test/sample-excel-extension-propertyprovider-class.md)

