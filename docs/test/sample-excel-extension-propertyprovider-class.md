---
title: "Excel 拡張子のサンプル: PropertyProvider クラス | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 075d9b8d-8658-4fca-8711-08304dbac1c5
caps.latest.revision: 9
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 9
---
# Excel 拡張子のサンプル: PropertyProvider クラス
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この内部クラスは、<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> クラスを拡張すると共に、ユーザー インターフェイス \(UI\) テストを記録および再生するためのプロパティ サービスを [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 要素に提供します。  
  
## GetControlSupportLevel メソッド  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A> メソッドは、指定されたコントロールに対するプロパティ プロバイダーのサポート レベルを示す数値を返します。  数値が大きくなるほど、コントロールに対するプロパティ プロバイダーのサポート レベルは高くなります。  この場合、このメソッドでは、指定されたコントロールの <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> プロパティの値を確認します。  値が "Excel" で、<xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> によってこの値が `CellElement` であることが示されている場合、このメソッドは最も高い値を返します。それ以外の場合は 0 が返され、コントロールはサポートされません。  
  
## GetPropertyNames メソッド  
 Excel Cell コントロールのサポートされているプロパティに関して、プロパティ名とプロパティ記述子のディクショナリを返します。  
  
## GetPropertyDescriptor メソッド  
 このメソッドは、指定されたプロパティ名の定義済みプロパティ記述子を取得するために、テスト フレームワークによって呼び出されます。  
  
## GetPropertyValue メソッドと SetPropertyValue メソッド  
 `GetPropertyValue` メソッドは、この拡張の `Communicator` クラスを使用して、Excel のプロパティ値を返します。  `SetPropertyValue` メソッドは、<xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> クラスおよび `Communicator` コンポーネントを使用して、プロパティ値を設定します。  これらのメソッドは、テスト フレームワークによって呼び出されます。  
  
## コード生成カスタマイズ メソッド  
 これらのメソッドは、この拡張用に実装されていません。  したがって、`null` が返されるか、<xref:System.NotImplementedException> がスローされます。  
  
## 参照  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>   
 [コード化された UI テストと操作の記録を拡張して Microsoft Exce をサポート](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)