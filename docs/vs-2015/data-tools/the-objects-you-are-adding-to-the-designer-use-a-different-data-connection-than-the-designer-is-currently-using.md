---
title: 現在、デザイナーを使用して別のデータ接続を使用、デザイナーに追加するオブジェクト |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b2102d218ee74bc2e1a7a2787475c8005c77f2b1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545748"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer-is-currently-using"></a>デザイナーに追加する対象のオブジェクトは、デザイナーが現在使用しているのとは異なるデータ接続を使用しています
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[をデザイナーに追加するオブジェクト、デザイナーが現在使用して別のデータ接続を使用](https://docs.microsoft.com/visualstudio/data-tools/the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer-is-currently-using)します。  
  
  
デザイナーに追加する対象のオブジェクトは、デザイナーが現在使用しているのとは異なるデータ接続を使用しています。 デザイナーが使用している接続に置き換えますか?  
  
 項目を追加すると、 [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)])、すべての項目が 1 つの共有データ接続を使用します。 デザイン サーフェイスは、サーフェイス上のすべてのオブジェクトに対して単一の接続を使用する <xref:System.Data.Linq.DataContext> を表します。デザイナーで現在使用されているデータ接続とは異なるデータ接続を使用するオブジェクトをデザイナーに追加すると、このメッセージが表示されます。 このエラーを解決するために、既存の接続を維持するように選択できます。 その場合、選択したオブジェクトは追加されません。 オブジェクトを追加して、リセットを選択する代わりに、<xref:System.Data.Linq.DataContext>新しい接続に接続します。  
  
> [!NOTE]
>  クリックすると**はい**、上のすべてのエンティティ クラス、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]新しい接続にマップされます。  
  
### <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>選択したオブジェクトで使用されている接続で既存の接続を置換するには  
  
-   **[はい]** をクリックします。  
  
     選択したオブジェクトが [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]に追加され、DataContext.Connection が新しい接続に設定されます。  
  
### <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>既存の接続を引き続き使用し、選択したオブジェクトの追加を取り消すには  
  
-   **[いいえ]** をクリックします。  
  
     操作がキャンセルされます。 DataContext.Connection は、既存の接続に設定されたままになります。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to Visual Studio での SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)

