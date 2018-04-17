---
title: これは、関連メソッドは、次の既定の挿入、更新、または削除メソッドのバッキング メソッド |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 89421c61e34bf4ed98bcb8c2c8bd6ef93e1dae0b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>この関連メソッドは、次の既定の挿入、更新、または削除メソッドのバッキング メソッドです
この関連メソッドは、次の既定の挿入、更新、または削除メソッドのバッキング メソッドです。 削除されると、これらのメソッドも削除されます。 続行しますか?  
  
 選択した `DataContext` メソッドは、O/R デザイナーで、いずれかのエンティティ クラスの挿入、更新、または削除メソッドとして現在使用されています。 選択したメソッドを削除すると、このメソッドを使用していたエンティティ クラスの更新時の挿入、更新、または削除の動作は、既定のランタイムの動作に戻ることになります。  
  
### <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>選択したメソッドを削除して、エンティティ クラスでランタイムの更新動作が使用されるようにするには  
  
-   **[はい]**をクリックします。  
  
     選択されたメソッドが削除され、このメソッドを使用して更新動作をオーバーライドしていたすべてのクラスは、既定の LINQ to SQL ランタイムの動作を使用するように戻されます。  
  
### <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>メッセージ ボックスを閉じて、選択したメソッドが変更されないようにするには  
  
-   **[いいえ]** をクリックします。  
  
     メッセージ ボックスが閉じ、変更は行われません。  
  
## <a name="see-also"></a>関連項目
[O/R デザイナーのメッセージ](../data-tools/o-r-designer-messages.md)  
[Visual Studio での LINQ to SQL ツールします。](../data-tools/linq-to-sql-tools-in-visual-studio2.md)