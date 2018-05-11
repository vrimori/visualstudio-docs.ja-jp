---
title: 'Excel 拡張子のサンプル: ActionFilter クラス | Microsoft Docs'
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 6f98afa819fceb4f8b8b34d5aa268f11f7b16993
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sample-excel-extension-actionfilter-class"></a>Excel 拡張子のサンプル: ActionFilter クラス

この内部クラスによって <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> クラスが拡張されます。また、この内部クラスは、[!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 要素に対するテスト アクションのフィルターを表します。

## <a name="simple-properties"></a>単純なプロパティ

これらの読み取り専用プロパティでは、コード化された UI テスト フレームワークでこのテスト アクション フィルターをどのように実行するかを指定します。 たとえば、<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> プロパティには、アクション フィルター名が設定されています。 他のプロパティには、アクション フィルターの <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>、<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>、このテスト アクション フィルターでフィルター処理されるテスト アクションの <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> の名前が設定されています。 また、<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A> を適用するかどうか、テスト アクションが <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A> かどうかを示すプロパティもあります。

## <a name="processrule-method"></a>ProcessRule メソッド

このメソッドは、コード化された UI テスト フレームワークによって呼び出され、指定された <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack> に対してフィルターを実行します。 このオーバーライドによって、スタックの次のアクションがセルに対してキーストロークを送る場合はマウスを選択するセルのアクションを削除します。 その後で `false` が返されます。

## <a name="private-methods"></a>プライベート メソッド

`IsLeftClick` メソッドは、指定されたアクションがマウスの左クリックを表すかどうかを判断します。 `AreActionsOnSameExcelCell` メソッドは、2 つの指定されたアクションが Excel の同じセルに対して実行されるかどうかを判断します。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>
- [コード化された UI テストと操作の記録を拡張して Microsoft Excel をサポート](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
