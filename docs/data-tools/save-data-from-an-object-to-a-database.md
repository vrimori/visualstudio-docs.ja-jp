---
title: "方法 : オブジェクトからデータベースにデータを保存する | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "データ [Visual Studio], 保存"
  - "データ アクセス [Visual Studio], オブジェクト"
  - "保存 (データを)"
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: 9
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 方法 : オブジェクトからデータベースにデータを保存する
オブジェクトのデータは、オブジェクトから値を TableAdapter の DBDirect のメソッドの 1 つ \(`TableAdapter.Insert` など\) に渡すことによってデータベースに保存できます。  詳細については、「[TableAdapter の概要](../data-tools/tableadapter-overview.md)」を参照してください。  
  
 オブジェクトのコレクションからデータを保存するには、for\-next ループなどを使用してオブジェクトのコレクションを反復処理し、TableAdapter の DBDirect のメソッドの 1 つを使用して各オブジェクトの値をデータベースに送ります。  
  
 DBDirect のメソッドは既定で TableAdapter に作成され、データベースに対して直接実行できます。  この一連のメソッドは直接呼び出すことができ、変更内容を反映してデータベースに送るために、<xref:System.Data.DataSet> オブジェクトまたは <xref:System.Data.DataTable> オブジェクトを必要としません。  
  
> [!NOTE]
>  TableAdapter を構成する際に、メイン クエリは DBDirect のメソッドを作成するために十分な情報を提供する必要があります。  たとえば、主キー列が定義されていないテーブルのデータを照会するように TableAdapter が構成されている場合、DBDirect のメソッドは生成されません。  
  
|TableAdapter DBDirect のメソッド|Description|  
|---------------------------------|-----------------|  
|`TableAdapter.Insert`|個々の列値をメソッド パラメーターとして渡して、新しいレコードをデータベースに追加します。|  
|`TableAdapter.Update`|データベースの既存のレコードを更新します。  `Update` メソッドは、元の列値と新しい列値をメソッド パラメーターとして受け取ります。  元の値は元のレコードを探すために使用し、新しい値はレコードを更新するために使用します。<br /><br /> `TableAdapter.Update` メソッドも <xref:System.Data.DataSet>、<xref:System.Data.DataTable>、<xref:System.Data.DataRow>、または <xref:System.Data.DataRow> の配列をメソッド パラメーターとして受け取って、データセットの変更内容をデータベースに反映して戻すために使用します。|  
|`TableAdapter.Delete`|メソッド パラメーターとして渡された元の列値に基づいてデータベースから既存のレコードを削除します。|  
  
### オブジェクトからデータベースに新規レコードを保存するには  
  
-   `TableAdapter.Insert` メソッドに値を渡してレコードを作成します。  
  
     `currentCustomer` オブジェクトの値を `TableAdapter.Insert` メソッドに渡して、`Customers` テーブルに顧客レコードを新規作成する例を次に示します。  
  
     [!code-cs[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]  
  
### オブジェクトからデータベースに既存レコードを更新するには  
  
-   `TableAdapter.Update` メソッドを呼び出し、元の値を渡してレコードの場所を探し、新しい値を渡してレコードを更新してレコードを変更します。  
  
    > [!NOTE]
    >  オブジェクトは、`Update` メソッドに渡すために元の値を維持する必要があります。  この例では、`orig` プリフィックスを付けたプロパティを使用して元の値を格納します。  
  
     `Customer` オブジェクトの新しい値と元の値を `TableAdapter.Update` メソッドに渡して、`Customers` テーブルの既存のレコードを更新する例を次に示します。  
  
     [!code-cs[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]  
  
### データベースから既存のレコードを削除するには  
  
-   `TableAdapter.Delete` メソッドを呼び出し、元の値を渡してレコードを探して削除します。  
  
    > [!NOTE]
    >  オブジェクトは、`Delete` メソッドに渡すために元の値を維持する必要があります。  この例では、`orig` プリフィックスを付けたプロパティを使用して元の値を格納します。  
  
     `Customer` オブジェクトの元の値を `TableAdapter.Delete` メソッドに渡して、`Customers` テーブルからレコードを削除する例を次に示します。  
  
     [!code-cs[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]  
  
## .NET Framework セキュリティ  
 データベースのテーブルで INSERT、UPDATE、または DELETE を実行するアクセス許可が必要です。  
  
## 参照  
 [Visual Studio におけるオブジェクトのバインド](../data-tools/bind-objects-in-visual-studio.md)   
 [方法: オブジェクトのデータに接続する](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)   
 [チュートリアル: オブジェクトのデータへの接続 \(Windows フォーム\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)   
 [方法 : TableAdapter で直接データベースにアクセスする](../data-tools/directly-access-the-database-with-a-tableadapter.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)