---
title: "デザイナーが現在使用して、デザイナーに追加するオブジェクトが別のデータ接続を使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: cb6b3e747db497b80893f271c97bb0f6d8c86894
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer-is-currently-using"></a>デザイナーに追加する対象のオブジェクトは、デザイナーが現在使用しているのとは異なるデータ接続を使用しています
デザイナーに追加する対象のオブジェクトは、デザイナーが現在使用しているのとは異なるデータ接続を使用しています。 デザイナーが使用している接続に置き換えますか?  
  
 項目を追加すると、 [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)])、すべての項目が 1 つの共有データ接続を使用します。 デザイン サーフェイスは、サーフェイス上のすべてのオブジェクトに対して単一の接続を使用する <xref:System.Data.Linq.DataContext> を表します。デザイナーで現在使用されているデータ接続とは異なるデータ接続を使用するオブジェクトをデザイナーに追加すると、このメッセージが表示されます。 このエラーを解決するために、既存の接続を維持するように選択できます。 その場合、選択したオブジェクトは追加されません。 または、オブジェクトを追加してリセットできます、<xref:System.Data.Linq.DataContext>新しい接続に接続します。  
  
> [!NOTE]
>  クリックすると**はい**のすべてのエンティティ クラス、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]新しい接続にマップされます。  
  
### <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>選択したオブジェクトで使用されている接続で既存の接続を置換するには  
  
-   **[はい]**をクリックします。  
  
     選択したオブジェクトが [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]に追加され、DataContext.Connection が新しい接続に設定されます。  
  
### <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>既存の接続を引き続き使用し、選択したオブジェクトの追加を取り消すには  
  
-   **[いいえ]** をクリックします。  
  
     操作がキャンセルされます。 DataContext.Connection は、既存の接続に設定されたままになります。  
  
## <a name="see-also"></a>関連項目
[O/R デザイナー メッセージ](../data-tools/o-r-designer-messages.md)  
[Visual Studio での LINQ to SQL ツールします。](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
 