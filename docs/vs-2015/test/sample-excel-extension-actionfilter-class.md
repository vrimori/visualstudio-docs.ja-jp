---
title: Excel 拡張子のサンプル:ActionFilter クラス |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 13
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 86c1dda46ed0e62649a576a12c9f9e48561ec891
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54767845"
---
# <a name="sample-excel-extension-actionfilter-class"></a>Excel 拡張子のサンプル:ActionFilter クラス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

この内部クラスによって <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> クラスが拡張されます。また、この内部クラスは、[!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 要素に対するテスト アクションのフィルターを表します。  
  
## <a name="simple-properties"></a>単純なプロパティ  
 開発者は、これらの読み取り専用プロパティを使用して、コード化された UI テスト フレームワークでこのテスト アクション フィルターをどのように実行するかを指定できます。 たとえば、<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> プロパティには、アクション フィルター名が設定されています。 他のプロパティには、アクション フィルターの <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>、<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>、このテスト アクション フィルターでフィルター処理されるテスト アクションの <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> の名前が設定されています。 また、<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A> を適用するかどうか、テスト アクションが <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A> かどうかを示すプロパティもあります。  
  
## <a name="processrule-method"></a>ProcessRule メソッド  
 このメソッドは、コード化された UI テスト フレームワークによって呼び出され、指定された <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack> に対してフィルターを実行します。 このオーバーライドによって、スタックの次のアクションがセルに対してキーストロークを送る場合はマウスを選択するセルのアクションを削除します。 その後で `false` が返されます。  
  
## <a name="private-methods"></a>プライベート メソッド  
 `IsLeftClick` メソッドは、指定されたアクションがマウスの左クリックを表すかどうかを判断します。 `AreActionsOnSameExcelCell` メソッドは、2 つの指定されたアクションが Excel の同じセルに対して実行されるかどうかを判断します。  
  
## <a name="see-also"></a>「  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>   
 [コード化された UI テストと操作の記録を拡張して Microsoft Excel をサポート](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
