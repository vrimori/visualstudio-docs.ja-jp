---
title: 'Excel 拡張機能のサンプル: PropertyProvider クラス | Microsoft Docs'
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: a3da33b0c99c84f3680f323b483cebf31448ba62
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sample-excel-extension-propertyprovider-class"></a>Excel 拡張子のサンプル: PropertyProvider クラス
この内部クラスによって <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> クラスが拡張されます。また、この内部クラスは、ユーザー インターフェイス (UI) テストの記録と再生に使用する [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 要素のプロパティ サービスを提供します。

## <a name="getcontrolsupportlevel-method"></a>GetControlSupportLevel メソッド
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A> メソッドは、指定されたコントロールに対してプロパティ プロバイダーが提供できるサポート レベルを示す数値を返します。 戻り値が大きくなるほど、コントロールに対するプロパティ プロバイダーのサポート レベルは高くなります。 このメソッドの例では、指定されたコントロールの <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> プロパティの値が確認されます。 値が "Excel" で、<xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> が `CellElement` であると指定されている場合、メソッドからは最も高い値が返されます。それ以外の場合はゼロが返されます。これは、サポートが提供されていないことを示します。

## <a name="getpropertynames-method"></a>GetPropertyNames メソッド
 Excel Cell コントロールのサポートされているプロパティに関して、プロパティ名とプロパティ記述子のディクショナリを返します。

## <a name="getpropertydescriptor-method"></a>GetPropertyDescriptor メソッド
 このメソッドは、指定されたプロパティ名の定義済みプロパティ記述子を取得するために、テスト フレームワークによって呼び出されます。

## <a name="getpropertyvalue-and-setpropertyvalue-methods"></a>GetPropertyValue メソッドと SetPropertyValue メソッド
 `GetPropertyValue` メソッドはこの拡張機能の `Communicator` クラスを使用して Excel のプロパティ値を返します。 `SetPropertyValue` メソッドは <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> クラスと `Communicator` コンポーネントを使用してプロパティ値を設定しています。 これらのメソッドはテスト フレームワークによって呼び出されます。

## <a name="code-generation-customization-methods"></a>コード生成カスタマイズ メソッド
 この拡張機能でこれらのメソッドは実装されていません。 そのため、`null` が返されるか、<xref:System.NotImplementedException> がスローされます。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>
- [コード化された UI テストと操作の記録を拡張して Microsoft Excel をサポート](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
