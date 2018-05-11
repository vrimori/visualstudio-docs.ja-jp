---
title: Excel 用にコード化された UI テストの拡張子のサンプル
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
helpviewer_keywords:
- coded UI tests, extensions for Excel
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 2c76ba569a6f9f34d28d6aaaa268a366c1be7b31
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="sample-coded-ui-test-extension-for-excel"></a>Excel 用にコード化された UI テストの拡張子のサンプル
サンプルの拡張機能コンポーネントは [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のコード化された UI テスト プロセスで実行され、`ExtensionPackage` クラスをベースにして多少階層的になります。 コントロール要素が最上位レベルで、`TechnologyManager` クラス、`ActionFilter` クラス、および `PropertyProvider` クラスはその次のレベルにあります。

 ![Excel のテスト拡張機能アーキテクチャ](../test/media/excel_extarch.png "Excel_ExtArch") Excel 拡張アーキテクチャ

## <a name="extension-points"></a>拡張ポイント
 これらのクラスはサンプルに実装される拡張ポイントを表し、[!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 用のコード化された UI テストを可能にします。

### <a name="extensionpackage"></a>ExtensionPackage
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> から継承されます。これはコード化された UI テスト拡張機能のエントリ ポイントです。 この抽象クラスを実装すると、コード化された UI テスト フレームワークが、新しい UI をテストするために、カスタム UI テスト テクノロジ マネージャー、UI テスト プロパティ プロバイダー、および UI テスト アクション フィルターに内部アクセスできるようになります。 詳細については、「[ExtensionPackage Class (ExtensionPackage クラス)](../test/sample-excel-extension-extensionpackage-class.md)」を参照してください。

### <a name="technologymanager"></a>TechnologyManager
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> クラスから継承されます。このクラスには、テスト記録および再生用のテクノロジ マネージャーが用意されています。 詳細については、「[TechnologyManager Class (TechnologyManager クラス)](../test/sample-excel-extension-technologymanager-class.md)」を参照してください。

### <a name="actionfilter"></a>ActionFilter
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> クラスから継承されます。このクラスには、似たテスト アクション結果を単一のテスト結果に集約する基底クラスがあります。 詳細については、「[ActionFilter Class (ActionFilter クラス)](../test/sample-excel-extension-actionfilter-class.md)」を参照してください。

### <a name="technology-elements"></a>テクノロジ要素
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> クラスから継承された基底クラスには、UI テストで記録および再生に使用できるテクノロジ要素の基礎が用意されています。 詳細については、「[Element Classes (要素クラス)](../test/sample-excel-extension-element-classes.md)」を参照してください。

### <a name="propertyprovider"></a>PropertyProvider
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> クラスから継承されます。このクラスには、テスト記録および再生に使用できる UI 要素のプロパティをサポートする基底クラスがあります。 詳細については、「[PropertyProvider Class (PropertyProvider クラス)](../test/sample-excel-extension-propertyprovider-class.md)」を参照してください。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [ExtensionPackage クラス](../test/sample-excel-extension-extensionpackage-class.md)
- [TechnologyManager クラス](../test/sample-excel-extension-technologymanager-class.md)
- [ActionFilter クラス](../test/sample-excel-extension-actionfilter-class.md)
- [要素クラス](../test/sample-excel-extension-element-classes.md)
- [PropertyProvider Class (PropertyProvider クラス)](../test/sample-excel-extension-propertyprovider-class.md)
