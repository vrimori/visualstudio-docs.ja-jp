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
translationtype: Human Translation
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: 99397f8f0c6e0e261451cae642cf6e48fe5bba56
ms.lasthandoff: 04/04/2017

---
# <a name="sample-excel-extension-propertyprovider-class"></a>Excel 拡張子のサンプル: PropertyProvider クラス
この内部クラスは <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> クラスを拡張し、[!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 要素がユーザー インターフェイス (UI) のテストを記録し再生するためのプロパティ サービスを提供します。  
  
## <a name="getcontrolsupportlevel-method"></a>GetControlSupportLevel メソッド  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A> メソッドは、指定したコントロールに対してプロパティのプロバイダーが提供できるサポートのレベルを示す番号を返します。 戻り値が大きくなるほど、コントロールに対するプロパティ プロバイダーのサポート レベルは高くなります。 この場合、このメソッドは指定されたコントロールの <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> プロパティの値を確認します。 値が "Excel" であり、<xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> が `CellElement` であることを示す場合、このメソッドは最も高い値を返します。そうでない場合は、サポートが指定されていないことを示す 0 を返します。  
  
## <a name="getpropertynames-method"></a>GetPropertyNames メソッド  
 Excel Cell コントロールのサポートされているプロパティに関して、プロパティ名とプロパティ記述子のディクショナリを返します。  
  
## <a name="getpropertydescriptor-method"></a>GetPropertyDescriptor メソッド  
 このメソッドは、指定されたプロパティ名の定義済みプロパティ記述子を取得するために、テスト フレームワークによって呼び出されます。  
  
## <a name="getpropertyvalue-and-setpropertyvalue-methods"></a>GetPropertyValue メソッドと SetPropertyValue メソッド  
 `GetPropertyValue` メソッドはこの拡張機能の `Communicator` クラスを使用して Excel のプロパティ値を返します。 `SetPropertyValue` メソッドは <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> クラスおよび `Communicator` コンポーネントを使用してプロパティ値を設定します。 これらのメソッドはテスト フレームワークによって呼び出されます。  
  
## <a name="code-generation-customization-methods"></a>コード生成カスタマイズ メソッド  
 この拡張機能でこれらのメソッドは実装されていません。 そのため、`null` が返されるか、<xref:System.NotImplementedException> がスローされます。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>   
 [コード化された UI テストと操作の記録を拡張して Microsoft Excel をサポート](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

