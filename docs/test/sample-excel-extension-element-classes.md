---
title: "Excel 拡張子のサンプル: 要素クラス | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c251098-00aa-49cf-9e37-5717c0c6b3f1
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "mlearned"
manager: "douge"
---
# Excel 拡張子のサンプル: 要素クラス
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

拡張は、<xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> から派生する、[!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] の Worksheet コントロールおよび Cell コントロールを表すクラスを使用します。  
  
 この拡張の基本要素は、`ExcelElement` です。  `ExcelWorksheetElement` クラスおよび `ExcelCellElement` クラスは、この要素を継承します。  
  
## Element クラスと ElementInformation クラス  
 `Element`  は Excel 拡張機能のすべてのユーザー インターフェイス要素の基本クラスであり、<xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> クラスを継承しています。  `ElementInformation` はサンプルの要素情報クラスの基本クラスであり、メンバーを持ちません。  
  
#### 単純なプロパティとメソッド  
 これらのメンバーは、`Name` プロパティの値や `ClassName` プロパティの値などの単純な値を返し、コードも明快で読みやすいものです。  一部の値は、`Utility` クラスを使用して返されます。これについては、後で説明します。  その他は、このサンプル拡張には関連しないので、`null` を返します。  他のメンバーよりも注意が必要な 2 つのメンバーが、<xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> プロパティと <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.CacheProperties%2A> メソッドです。  
  
#### QueryId プロパティ  
 このプロパティは、再生中にコントロールを一意に識別する、プロパティ名と値のペアから成る条件を返します。  開発者は、各派生コントロール クラスのこのプロパティをオーバーライドし、フレームワークが UI 内のコントロールを見つけるために使用できる <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> オブジェクトを返すようにする必要があります。  
  
#### CacheProperties メソッド  
 このメソッドは、記録処理中にテスト フレームワークによって呼び出され、重要なプロパティのスナップショットを保存するよう要素に指示します。  そうすることで、実際の UI コントロールが画面上に存在しなくなった場合でも、プロパティが使用可能な状態で維持されます。  
  
## WorksheetElement クラスと WorksheetInformation クラス  
 `WorksheetElement`  クラスは、テスト フレームワーク内の Excel ワークシートを表しており、`Element` 基本クラスを継承しています。  Excel ワークシート オブジェクトの固有の情報を提供するために、<xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ClassName%2A>、<xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ControlTypeName%2A>、および <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.Name%2A> という 3 つのプロパティがオーバーライドされています。  
  
 このクラスには、COM から参照できるように、<xref:System.Runtime.InteropServices.ComVisibleAttribute> も適用されています。  
  
 `WorksheetInformation`  クラスは、Excel ワークシートに関する情報を表しています。  このクラスのメンバーは `SheetName` プロパティだけですが、このサンプルではそれで十分です。  
  
## CellElement クラスと CellInformation クラス  
 `CellElement`  クラスは Excel のセルを表し、`Element` 基本クラスを継承しています。  オーバーライドされているメンバーは <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> プロパティのみです。このプロパティは、`RowIndex` および `ColumnIndex` プロパティを使用してセルを特定する <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> を返します。  
  
## Utilities クラスと ExcelUtilities クラス  
 内部 `ExcelUtilities` クラスには、テクノロジ名のようないくつかの定数値と、指定されたウィンドウ ハンドルが Excel ワークシートを表しているかどうかを判断するメソッドがあります。  
  
 `Utilities`  クラスには、UI に関するさまざまな情報を返すヘルパー メソッドがあります。  一部のメソッドは、**USER32.DLL** や **OLEACC.DLL** などの外部システム DLL への直接呼び出しを使用して、UI のウィンドウ ハンドルを取得します。  
  
## 参照  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>   
 [コード化された UI テストと操作の記録を拡張して Microsoft Exce をサポート](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)