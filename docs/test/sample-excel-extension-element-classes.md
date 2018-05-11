---
title: 'Excel 拡張機能のサンプル: Element クラス | Microsoft Docs'
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 1dce9745db1acf031c67d5221f6a176d94fb6f77
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sample-excel-extension-element-classes"></a>Excel 拡張子のサンプル: 要素クラス
この拡張機能は、<xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> から派生し、[!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 内の Worksheet コントロールと Cell コントロールを表すクラスを使用します。

 この拡張機能の基本要素は `ExcelElement` です。 `ExcelWorksheetElement` クラスおよび `ExcelCellElement` クラスは、この要素を継承します。

## <a name="element-and-elementinformation-classes"></a>Element クラスと ElementInformation クラス
 `Element` は、Excel 拡張機能のすべてのユーザー インターフェイス要素の基底クラスです。<xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> クラスから継承されます。 `ElementInformation` はサンプルの要素情報クラスの基底クラスであり、メンバーを持ちません。

#### <a name="simple-properties-and-methods"></a>単純なプロパティとメソッド
 これらのメンバーは、`Name` プロパティの値や `ClassName` プロパティの値などの単純な値を返し、コードも明快で読みやすいものです。 一部の値は、`Utility` クラスを使用して返されます。これについては、後で説明します。 その他は、このサンプル拡張機能には関連しないので、`null` を返します。 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> プロパティという <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.CacheProperties%2A> メソッドの 2 つは他のメンバーよりも興味深いメンバーです。

#### <a name="queryid-property"></a>QueryId プロパティ
 このプロパティは、再生中にコントロールを一意に識別する、プロパティ名と値のペアから成る条件を返します。 開発者は、各派生コントロール クラスのこのプロパティを上書きし、フレームワークが UI 内のコントロールを見つけるために使用できる <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> オブジェクトを返すようにする必要があります。

#### <a name="cacheproperties-method"></a>CacheProperties メソッド
 このメソッドは、記録処理中にテスト フレームワークによって呼び出され、重要なプロパティのスナップショットを保存するよう要素に指示します。 そうすることで、実際の UI コントロールが画面上に存在しなくなった場合でも、プロパティが使用可能な状態で維持されます。

## <a name="worksheetelement-and-worksheetinformation-classes"></a>WorksheetElement クラスと WorksheetInformation クラス
 `WorksheetElement` クラスはテスト フレームワーク内の Excel ワークシートを表し、`Element` 基底クラスを継承します。 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ClassName%2A>、<xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ControlTypeName%2A>、および <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.Name%2A> の 3 つのプロパティはオーバーライドされ、Excel ワークシート オブジェクトに関する特定の情報が提供されます。

 また、<xref:System.Runtime.InteropServices.ComVisibleAttribute> もこのクラスに適用され、COM から参照できるようになります。

 `WorksheetInformation` クラスは Excel ワークシートに関する情報を表します。 `SheetName` プロパティという 1 つのメンバーしかありませんが、このサンプルの場合はそれで十分です。

## <a name="cellelement-and-cellinformation-classes"></a>CellElement クラスと CellInformation クラス
 `CellElement` クラスは Excel のセルを表し、`Element` 基底クラスを継承します。 唯一のオーバーライドされるメンバーは <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> です。これは、セルを識別する `RowIndex` および `ColumnIndex` プロパティを使用する <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> を返します。

## <a name="utilities-and-excelutilities-classes"></a>Utilities クラスと ExcelUtilities クラス
 内部 `ExcelUtilities` クラスには、テクノロジ名などの定数値や、指定されたウィンドウ ハンドルが Excel ワークシートを表すかどうかを判断するメソッドなどが用意されています。

 `Utilities` クラスには、UI に関するさまざまな情報を返すヘルパー メソッドがあります。 一部のメソッドは、**USER32.DLL** や **OLEACC.DLL** などの外部システム DLL への直接呼び出しを使用して、UI のウィンドウ ハンドルを取得します**。**

## <a name="see-also"></a>関連項目

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>
- [コード化された UI テストと操作の記録を拡張して Microsoft Excel をサポート](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
