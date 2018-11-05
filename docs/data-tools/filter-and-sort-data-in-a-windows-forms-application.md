---
title: Windows フォーム アプリケーションのデータのフィルター処理および並べ替えを行う
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 1868d670458e204f6e503b132aaceab17f3da742
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750924"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Windows フォーム アプリケーションのデータのフィルター処理および並べ替えを行う

データをフィルター処理するには、<xref:System.Windows.Forms.BindingSource.Filter%2A> プロパティに目的のレコードを返す文字列式を設定します。

設定してデータを並べ替える、<xref:System.Windows.Forms.BindingSource.Sort%2A>プロパティを並べ替える。 追加の列名を`DESC`を降順で並べ替える付加したり`ASC`を昇順で並べ替えます。

> [!NOTE]
> アプリケーションを使用しない場合<xref:System.Windows.Forms.BindingSource>フィルター処理できる、コンポーネントを使用してデータを並べ替えると<xref:System.Data.DataView>オブジェクト。 詳細については、次を参照してください。 [Dataview](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews)します。

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>BindingSource コンポーネントを使用してデータをフィルター処理するには

-   <xref:System.Windows.Forms.BindingSource.Filter%2A> プロパティに取得する式を設定します。 たとえば、以下のコードは、`CompanyName` が "B" で始まる顧客を返します。

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>BindingSource コンポーネントを使用してデータを並べ替える

-   <xref:System.Windows.Forms.BindingSource.Sort%2A> プロパティに並べ替える列を設定します。 たとえば、以下のコードは、`CompanyName` 列に基づいて降順に顧客を並べ替えます。

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)