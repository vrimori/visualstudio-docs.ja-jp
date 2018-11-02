---
title: オブジェクトからデータベースにデータを保存する
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c1203b3b129b42ca65b94cd7a4b9cebf108740f4
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750950"
---
# <a name="save-data-from-an-object-to-a-database"></a>オブジェクトからデータベースにデータを保存する

TableAdapter の DBDirect メソッドのいずれかに、オブジェクトから値を渡すことでオブジェクトをデータベースでデータを保存することができます (たとえば、 `TableAdapter.Insert`)。 詳細については、次を参照してください。 [TableAdapter](../data-tools/create-and-configure-tableadapters.md)します。

オブジェクトのコレクションからデータを保存するオブジェクト (次のループなど) のコレクションをループ処理し、TableAdapter のいずれかを使用して、各オブジェクトの値をデータベースに送信`DBDirect`メソッド。

既定では、`DBDirect`メソッドは、データベースに対して直接実行できる TableAdapter 上に作成します。 これらのメソッドは、直接呼び出すことができ、必要としない<xref:System.Data.DataSet>または<xref:System.Data.DataTable>データベースへの更新を送信するために変更を調整するオブジェクト。

> [!NOTE]
> メインのクエリが十分な情報を提供する必要があります TableAdapter を構成するとき、`DBDirect`メソッドを作成できます。 たとえば、TableAdapter が定義されている主キー列がないテーブルからデータのクエリに構成されている場合に生成しません`DBDirect`メソッド。

|TableAdapter DBDirect メソッド|説明|
| - |-----------------|
|`TableAdapter.Insert`|データベースに新しいレコードを追加して、個々 の列の値をメソッド パラメーターとして渡すことができます。|
|`TableAdapter.Update`|既存のデータベース内のレコードを更新します。 `Update`メソッドはメソッドのパラメーターとしての元と新しい列の値を受け取ります。 元のレコードを検索するため、元の値と新しい値は、そのレコードの更新に使用されます。<br /><br /> `TableAdapter.Update`ことで、元のデータベースにデータセットの変更を調整するメソッドを使用しても、 <xref:System.Data.DataSet>、 <xref:System.Data.DataTable>、 <xref:System.Data.DataRow>、または配列の<xref:System.Data.DataRow>メソッドのパラメーターとして。|
|`TableAdapter.Delete`|メソッドのパラメーターとして渡された元の列の値に基づいて、データベースから既存のレコードを削除します。|

## <a name="to-save-new-records-from-an-object-to-a-database"></a>オブジェクトから新しいレコードをデータベースに保存するには

-   値を渡すことによって、レコードを作成、`TableAdapter.Insert`メソッド。

     次の例は、新しい顧客レコードを作成、`Customers`テーブル内の値を渡すことによって、`currentCustomer`オブジェクトを`TableAdapter.Insert`メソッド。

     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]

## <a name="to-update-existing-records-from-an-object-to-a-database"></a>オブジェクトからデータベースへの既存のレコードを更新するには

-   呼び出すことによって、レコードの変更、`TableAdapter.Update`メソッドをレコードを更新する新しい値を渡すと、レコードを検索する元の値を渡します。

    > [!NOTE]
    > オブジェクトに渡すために、元の値を維持するために必要のある、`Update`メソッド。 この例でのプロパティを使用して、`orig`元の値を格納するプレフィックス。

     次の例の既存のレコードを更新する、`Customers`テーブル内の新しいバージョンと元の値を渡すことによって、`Customer`オブジェクトを`TableAdapter.Update`メソッド。

     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]

## <a name="to-delete-existing-records-from-a-database"></a>既存のレコードをデータベースから削除するには

-   呼び出すことにより、レコードを削除、`TableAdapter.Delete`メソッドとレコードを検索する元の値を渡すことです。

    > [!NOTE]
    > オブジェクトに渡すために、元の値を維持するために必要のある、`Delete`メソッド。 この例でのプロパティを使用して、`orig`元の値を格納するプレフィックス。

     次の例からのレコードの削除、`Customers`テーブルの元の値を渡すことによって、`Customer`オブジェクトを`TableAdapter.Delete`メソッド。

     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]

## <a name="net-framework-security"></a>.NET Framework のセキュリティ

選択されたを実行する権限が必要`INSERT`、 `UPDATE`、または`DELETE`データベース内のテーブルにします。

## <a name="see-also"></a>関連項目

- [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)