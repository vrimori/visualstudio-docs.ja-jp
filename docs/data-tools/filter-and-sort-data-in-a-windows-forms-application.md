---
title: "Windows フォーム アプリケーションでデータのフィルターと並べ替え |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 58117773f1f5fb973bf3ab741425d3ad7492c63f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Windows フォーム アプリケーションでデータのフィルターと並べ替え
データをフィルター処理するには、<xref:System.Windows.Forms.BindingSource.Filter%2A> プロパティに目的のレコードを返す文字列式を設定します。  
  
 データを並べ替えるには、<xref:System.Windows.Forms.BindingSource.Sort%2A> プロパティに並べ替える列の名前を設定し、降順の場合は末尾に `DESC` を、昇順の場合は末尾に `ASC` を付けます。  
  
> [!NOTE]
>  アプリケーションを使用しない場合<xref:System.Windows.Forms.BindingSource>コンポーネントをフィルター処理できますを使用してデータを並べ替えると<xref:System.Data.DataView>オブジェクト。 詳細については、次を参照してください。 [Dataview](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews)です。  
  
## <a name="to-filter-data-by-using-a-bindingsource-component"></a>BindingSource コンポーネントを使用してデータをフィルター処理するには  
  
-   <xref:System.Windows.Forms.BindingSource.Filter%2A> プロパティに取得する式を設定します。 たとえば、以下のコードは、`CompanyName` が "B" で始まる顧客を返します。  
  
     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]  
  
## <a name="to-sort-data-by-using-a-bindingsource-component"></a>BindingSource コンポーネントを使用してデータを並べ替える  
  
-   <xref:System.Windows.Forms.BindingSource.Sort%2A> プロパティに並べ替える列を設定します。 たとえば、以下のコードは、`CompanyName` 列に基づいて降順に顧客を並べ替えます。  
  
     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]  
  
## <a name="see-also"></a>参照  
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)