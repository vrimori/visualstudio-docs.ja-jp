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
translationtype: Human Translation
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: dc4805133aef7247e25ac4de123de084d5918304
ms.lasthandoff: 04/04/2017

---
# <a name="sample-excel-extension-actionfilter-class"></a>Excel 拡張子のサンプル: ActionFilter クラス
この内部クラスは UITestActionFilter クラスを拡張し、[!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 要素のテスト アクションのフィルターを表します。  
  
## <a name="simple-properties"></a>単純なプロパティ  
 開発者は、これらの読み取り専用プロパティを使用して、コード化された UI テスト フレームワークでこのテスト アクション フィルターをどのように実行するかを指定できます。 たとえば、Name プロパティによって、アクション フィルターの名前を指定します。 その他にも、アクション フィルターのカテゴリを取得するプロパティ (Category)、フィルターの種類を取得するプロパティ (FilterType)、このテスト アクション フィルターによってフィルター処理されるテスト アクションのグループ名を取得するプロパティ (Group) を取得するプロパティがあります。 また、タイムアウトを適用するかどうかを示すプロパティ (ApplyTimeout) や、テスト アクションが有効かどうかを示すプロパティ (Enabled) もあります。  
  
## <a name="processrule-method"></a>ProcessRule メソッド  
 このメソッドは、コード化された UI テスト フレームワークによって呼び出され、指定された IUITestActionStack に対してフィルターを実行します。 このオーバーライドによって、スタックの次のアクションがセルに対してキーストロークを送る場合はマウスを選択するセルのアクションを削除します。 その後で `false` が返されます。  
  
## <a name="private-methods"></a>プライベート メソッド  
 `IsLeftClick` メソッドは、指定されたアクションがマウスの左クリックを表すかどうかを判断します。 `AreActionsOnSameExcelCell` メソッドは、2 つの指定されたアクションが Excel の同じセルに対して実行されるかどうかを判断します。  
  
## <a name="see-also"></a>関連項目  
 UITestActionFilter   
 IUITestActionStack   
 [コード化された UI テストと操作の記録を拡張して Microsoft Excel をサポート](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

