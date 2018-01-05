---
title: "オブジェクトからデータをデータベースに保存する |Microsoft ドキュメント"
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
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: e7078e6814abeb0db2afd2cffe698f923e530179
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="save-data-from-an-object-to-a-database"></a>オブジェクトからデータをデータベースに保存します。
オブジェクトをデータベースでデータを保存するには、TableAdapter の DBDirect メソッドのいずれかに、オブジェクトから値を渡すことで (たとえば、 `TableAdapter.Insert`)。 詳細については、次を参照してください。 [TableAdapter](../data-tools/create-and-configure-tableadapters.md)です。  
  
 オブジェクトのコレクションからデータを保存するには、(次のループなど) のオブジェクトのコレクションをループし、TableAdapter の DBDirect メソッドのいずれかを使用して、各オブジェクトの値をデータベースに送信します。  
  
 既定では、DBDirect メソッドは、データベースに対して直接実行できる TableAdapter で作成されます。 これらのメソッドは、直接呼び出すことができ、必要としない<xref:System.Data.DataSet>または<xref:System.Data.DataTable>データベースへの更新を送信するために変更を反映させるためのオブジェクト。  
  
> [!NOTE]
>  TableAdapter を構成する際、メインのクエリは DBDirect メソッドを作成するのに十分な情報を提供する必要があります。 たとえば、TableAdapter が定義されている主キー列がないテーブルからデータのクエリに構成されている場合に生成しません DBDirect メソッド。  
  
|TableAdapter DBDirect メソッド|説明|  
|----------------------------------|-----------------|  
|`TableAdapter.Insert`|データベースに新しいレコードを追加して、個々 の列の値をメソッド パラメーターとして渡すことができます。|  
|`TableAdapter.Update`|既存のデータベース内のレコードを更新します。 `Update`メソッドはメソッド パラメーターとして元と新しい列の値を受け取ります。 元の値は、元のレコードを検索するために使用され、そのレコードを更新する、新しい値が使用されます。<br /><br /> `TableAdapter.Update`データセットの変更をデータベースに実行することで調整するためにメソッドを使用しても、 <xref:System.Data.DataSet>、 <xref:System.Data.DataTable>、 <xref:System.Data.DataRow>、または配列の<xref:System.Data.DataRow>メソッド パラメーターとして。|  
|`TableAdapter.Delete`|メソッドのパラメーターとして渡された元の列値に基づいて、データベースから既存のレコードを削除します。|  
  
### <a name="to-save-new-records-from-an-object-to-a-database"></a>オブジェクトから新しいレコードをデータベースに保存するには  
  
-   値を渡すことによって、レコードを作成、`TableAdapter.Insert`メソッドです。  
  
     次の例で、新しい顧客レコードを作成する、`Customers`テーブル内の値を渡すことによって、`currentCustomer`オブジェクトを`TableAdapter.Insert`メソッドです。  
  
     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]  
  
### <a name="to-update-existing-records-from-an-object-to-a-database"></a>オブジェクトからデータベースへの既存のレコードを更新するには  
  
-   呼び出すことによって、レコードの編集、`TableAdapter.Update`メソッドをレコードを更新する新しい値を渡すと、レコードを検索する元の値を渡します。  
  
    > [!NOTE]
    >  オブジェクトに渡すために、元の値を維持するために必要のある、`Update`メソッドです。 この例でのプロパティを使用して、`orig`元の値を格納するプレフィックスです。  
  
     次の例の既存のレコードを更新する、`Customers`テーブルに新しいと元の値を渡すことによって、`Customer`オブジェクトを`TableAdapter.Update`メソッドです。  
  
     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]  
  
### <a name="to-delete-existing-records-from-a-database"></a>データベースから既存のレコードを削除するには  
  
-   呼び出すことにより、レコードを削除、`TableAdapter.Delete`メソッドと、レコードを検索する元の値を渡すことです。  
  
    > [!NOTE]
    >  オブジェクトに渡すために、元の値を維持するために必要のある、`Delete`メソッドです。 この例でのプロパティを使用して、`orig`元の値を格納するプレフィックスです。  
  
     次の例からレコードを削除する、`Customers`テーブルの元の値を渡すことによって、`Customer`オブジェクトを`TableAdapter.Delete`メソッドです。  
  
     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 選択した挿入を実行する権限が必要更新、または、データベース内のテーブルを削除します。  
  
## <a name="see-also"></a>参照  
 [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)