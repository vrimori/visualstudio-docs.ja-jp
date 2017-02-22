---
title: "Excel 拡張子のサンプル: ActionFilter クラス | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "mlearned"
manager: "douge"
---
# Excel 拡張子のサンプル: ActionFilter クラス
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この内部クラスは <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> クラスを拡張し、[!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 要素のテスト アクションのフィルターを表します。  
  
## 単純プロパティ  
 開発者は、これらの読み取り専用プロパティを使用して、コード化された UI テスト フレームワークでこのテスト アクション フィルターをどのように実行するかを指定できます。  たとえば、<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> プロパティによって、アクション フィルターの名前を指定します。  その他にも、アクション フィルターのカテゴリを取得するプロパティ \(<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>\)、フィルターの種類を取得するプロパティ \(<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>\)、このテスト アクション フィルターによってフィルター処理されるテスト アクションのグループ名を取得するプロパティ \(<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A>\) を取得するプロパティがあります。  また、タイムアウトを適用するかどうかを示すプロパティ \(<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A>\) や、テスト アクションが有効かどうかを示すプロパティ \(<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>\) もあります。  
  
## ProcessRule メソッド  
 このメソッドは、コード化された UI テスト フレームワークによって呼び出され、指定された <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack> に対してフィルターを実行します。  このオーバーライドによって、スタックの次のアクションがセルに対してキーストロークを送る場合はマウスを選択するセルのアクションを削除します。  その後で、`false` が返されます。  
  
## プライベート メソッド  
 `IsLeftClick` メソッドは、指定されたアクションがマウスの左クリックを表すかどうかを判断します。  `AreActionsOnSameExcelCell` メソッドは、2 つの指定されたアクションが Excel の同じセルに対して実行されるかどうかを判断します。  
  
## 参照  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>   
 [コード化された UI テストと操作の記録を拡張して Microsoft Exce をサポート](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)