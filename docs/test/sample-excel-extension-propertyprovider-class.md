---
title: "Excel 拡張機能のサンプル: PropertyProvider クラス | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 075d9b8d-8658-4fca-8711-08304dbac1c5
caps.latest.revision: 9
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: 99397f8f0c6e0e261451cae642cf6e48fe5bba56
ms.contentlocale: ja-jp
ms.lasthandoff: 05/19/2017

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
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>   
 [コード化された UI テストと操作の記録を拡張して Microsoft Excel をサポート](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

