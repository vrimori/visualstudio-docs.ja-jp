---
title: "Excel 拡張子のサンプル: ActionFilter クラス | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 11
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
ms.openlocfilehash: dc4805133aef7247e25ac4de123de084d5918304
ms.contentlocale: ja-jp
ms.lasthandoff: 05/19/2017

---
# <a name="sample-excel-extension-actionfilter-class"></a>Excel 拡張子のサンプル: ActionFilter クラス
この内部クラスによって <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> クラスが拡張されます。また、この内部クラスは、[!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 要素に対するテスト アクションのフィルターを表します。  
  
## <a name="simple-properties"></a>単純なプロパティ  
 開発者は、これらの読み取り専用プロパティを使用して、コード化された UI テスト フレームワークでこのテスト アクション フィルターをどのように実行するかを指定できます。 たとえば、<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> プロパティには、アクション フィルター名が設定されています。 他のプロパティには、アクション フィルターの <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>、<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>、このテスト アクション フィルターでフィルター処理されるテスト アクションの <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> の名前が設定されています。 また、<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A> を適用するかどうか、テスト アクションが <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A> かどうかを示すプロパティもあります。  
  
## <a name="processrule-method"></a>ProcessRule メソッド  
 このメソッドは、コード化された UI テスト フレームワークによって呼び出され、指定された <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack> に対してフィルターを実行します。 このオーバーライドによって、スタックの次のアクションがセルに対してキーストロークを送る場合はマウスを選択するセルのアクションを削除します。 その後で `false` が返されます。  
  
## <a name="private-methods"></a>プライベート メソッド  
 `IsLeftClick` メソッドは、指定されたアクションがマウスの左クリックを表すかどうかを判断します。 `AreActionsOnSameExcelCell` メソッドは、2 つの指定されたアクションが Excel の同じセルに対して実行されるかどうかを判断します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>   
 [コード化された UI テストと操作の記録を拡張して Microsoft Excel をサポート](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

