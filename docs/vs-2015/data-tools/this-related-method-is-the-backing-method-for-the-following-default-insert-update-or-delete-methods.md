---
title: これは関連メソッドは、次の既定の挿入、更新、または delete の各メソッドのバッキング メソッド |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 34c44a8d47ab1694b2af7accd76ef5432668a212
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259143"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>この関連メソッドは、次の既定の挿入、更新、または削除メソッドのバッキング メソッドです
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
この関連メソッドは、次の既定の挿入、更新、または削除メソッドのバッキング メソッドです。 削除されると、これらのメソッドも削除されます。 続行しますか?  
  
 選択した `DataContext` メソッドは、O/R デザイナーで、いずれかのエンティティ クラスの挿入、更新、または削除メソッドとして現在使用されています。 選択したメソッドを削除すると、このメソッドを使用していたエンティティ クラスの更新時の挿入、更新、または削除の動作は、既定のランタイムの動作に戻ることになります。  
  
### <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>選択したメソッドを削除して、エンティティ クラスでランタイムの更新動作が使用されるようにするには  
  
-   **[はい]** をクリックします。  
  
     選択されたメソッドが削除され、このメソッドを使用して更新動作をオーバーライドしていたすべてのクラスは、既定の LINQ to SQL ランタイムの動作を使用するように戻されます。  
  
### <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>メッセージ ボックスを閉じて、選択したメソッドが変更されないようにするには  
  
-   **[いいえ]** をクリックします。  
  
     メッセージ ボックスが閉じ、変更は行われません。  
  
## <a name="see-also"></a>関連項目  
 [DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)   
 [方法: 更新、挿入、および削除 (O/R デザイナー) を実行するストアド プロシージャを割り当てる](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [LINQ to Visual Studio での SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)

