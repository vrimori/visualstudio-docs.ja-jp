---
title: N 層データセットに検証を追加 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: addcbd4640acd86cc40097742dcdfd515308f256
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="add-validation-to-an-n-tier-dataset"></a>N 層データセットに検証を追加します。
n 層ソリューションに分離されたデータセットへの検証の追加は、単一ファイルのデータセット (1 つのプロジェクト内のデータセット) に検証を追加するのと基本的には同じです。 データで検証を実行する位置として推奨されるのは、データ テーブルの <xref:System.Data.DataTable.ColumnChanging> イベントや <xref:System.Data.DataTable.RowChanging> イベントの発生時です。  
  
 データセットは、データセット内のデータ テーブルの列と行変更イベントにユーザー コードを追加する先部分クラスを作成する機能を提供します。 N 層ソリューション内のデータセットにコードを追加する方法の詳細については、次を参照してください。 [n 層アプリケーションのデータセットにコードを追加](../data-tools/add-code-to-datasets-in-n-tier-applications.md)、および[n 層アプリケーションの TableAdapters にコードを追加](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)です。 部分クラスの詳細については、次を参照してください。[する方法: クラスを部分クラス (クラス デザイナー) に分割](../ide/how-to-split-a-class-into-partial-classes-class-designer.md)または[部分クラスとメソッド](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)です。  
  
> [!NOTE]
>  データセットを Tableadapter から分離する場合 (設定して、 **DataSet プロジェクト**プロパティ)、プロジェクト内の既存のデータセット部分クラスを自動的に移動されません。 既存のデータセット部分クラスは、手動でデータセット プロジェクトに移動する必要があります。  
  
> [!NOTE]
>  データセット デザイナーでイベント ハンドラーが自動的に c# で作成されません、<xref:System.Data.DataTable.ColumnChanging>と<xref:System.Data.DataTable.RowChanging>イベント。 手動でイベント ハンドラーを作成し、基になるイベントのイベント ハンドラーをフックする必要があります。 次の手順では、Visual Basic と c# の両方で必要なイベント ハンドラーを作成する方法について説明します。  
  
## <a name="validate-changes-to-individual-columns"></a>個々 の列に対する変更を検証します。  
 個々の列の値は、<xref:System.Data.DataTable.ColumnChanging> イベントを処理することにより検証します。 <xref:System.Data.DataTable.ColumnChanging>イベントは、列の値が変更されたときに発生します。 イベント ハンドラーを作成、<xref:System.Data.DataTable.ColumnChanging>イベントには、該当する列をダブルクリックして、**データセット デザイナー**です。  
  
 最初に列をダブルクリックすると、デザイナーにより <xref:System.Data.DataTable.ColumnChanging> イベントのイベント ハンドラーが生成されます。 `If...Then`ステートメントは、特定の列をテストします。 たとえば、Northwind Orders テーブルの RequiredDate 列をダブルクリックすると、次のコードが生成されます。  
  
```vb  
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging  
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then  
        ' Add validation code here.  
    End If  
End Sub  
```  
  
> [!NOTE]
>  C# プロジェクトでは、データセットの部分クラスとデータセットの個々のテーブルのみがデータセット デザイナーにより作成されます。 C# では、Visual Basic と同様に <xref:System.Data.DataTable.ColumnChanging> イベントおよび <xref:System.Data.DataTable.RowChanging> イベントのイベント ハンドラーはデータセット デザイナーにより自動作成されません。 C# プロジェクトで、イベントを処理し、メソッドを基になるイベントをフックするためのメソッドを手動で構築するために必要があります。 次の手順では、必要なイベント ハンドラーを Visual Basic と C# の両方で作成する方法について説明します。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>個々の列値の変更時に検証を追加するには  
  
1.  ダブルクリックして、データセットを開き、 **.xsd**ファイル**ソリューション エクスプ ローラー**です。 詳細については、次を参照してください。[チュートリアル: データセット デザイナーでデータセットを作成する](walkthrough-creating-a-dataset-with-the-dataset-designer.md)です。  
  
2.  検証する列をダブルクリックします。 この操作によって <xref:System.Data.DataTable.ColumnChanging> イベント ハンドラーが作成されます。  
  
    > [!NOTE]
    >  データセット デザイナーでは、C# イベントのイベント ハンドラーは自動作成されません。 次のセクションでは、c# でイベントを処理するために必要なコードが含まれます。 `SampleColumnChangingEvent` 作成され、フックし、<xref:System.Data.DataTable.ColumnChanging>内のイベント、<xref:System.Data.DataTable.EndInit%2A>メソッドです。  
  
3.  アプリケーションの要件を満たすデータが `e.ProposedValue` に含まれていることを検証するコードを追加します。 指定された値が受け入れられない場合、エラーがあることを表すように該当する列を設定します。  
  
     次のコード例を検証する、**数量**列には、0 より大きい値が含まれています。 場合**数量**以下は、エラーに設定されている列を 0 にします。 `Else`場合、句が、エラーをクリア**数量**0 よりも高い設定です。 列変更イベント ハンドラー内のコードは、次のようになります。  
  
    ```vb  
    If (e.Column.ColumnName = Me.QuantityColumn.ColumnName) Then  
        If CType(e.ProposedValue, Short) <= 0 Then  
            e.Row.SetColumnError(e.Column, "Quantity must be greater than 0")  
        Else  
            e.Row.SetColumnError(e.Column, "")  
        End If  
    End If  
    ```    
    ```csharp  
    // Add this code to the DataTable partial class.  
  
    public override void EndInit()  
    {  
        base.EndInit();  
        // Hook up the ColumnChanging event  
        // to call the SampleColumnChangingEvent method.  
        ColumnChanging += SampleColumnChangingEvent;  
    }  
  
    public void SampleColumnChangingEvent(object sender, System.Data.DataColumnChangeEventArgs e)  
    {  
        if (e.Column.ColumnName == QuantityColumn.ColumnName)  
        {  
            if ((short)e.ProposedValue <= 0)  
            {  
                e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");  
            }  
            else  
            {  
                e.Row.SetColumnError("Quantity", "");  
            }  
        }  
    }  
    ```  
  
## <a name="validate-changes-to-whole-rows"></a>行全体に対する変更を検証します。  
 行全体の値は、<xref:System.Data.DataTable.RowChanging> イベントを処理することにより検証します。 <xref:System.Data.DataTable.RowChanging> イベントは、すべての列の値がコミットされたときに発生します。 ある列の値が別の列の値に依存している場合は、<xref:System.Data.DataTable.RowChanging> イベントで検証を行う必要があります。 たとえば、Northwind の Orders テーブルの OrderDate と RequiredDate について考えます。  
  
 注文が入力されると、RequiredDate が OrderDate と同じか、それより前の日付の注文が入力されていないかを検証します。 この例では、RequiredDate 列と OrderDate 列の両方を比較する必要があるため、個々の列の変更を検証しても意味がありません。  
  
 イベント ハンドラーを作成、<xref:System.Data.DataTable.RowChanging>イベントをテーブルのタイトル バー内のテーブル名をダブルクリックすると、**データセット デザイナー**です。  
  
#### <a name="to-add-validation-during-changes-to-whole-rows"></a>行全体の変更時に検証を追加するには  
  
1.  ダブルクリックして、データセットを開き、 **.xsd**ファイル**ソリューション エクスプ ローラー**です。 詳細については、次を参照してください。[チュートリアル: データセット デザイナーでデータセットを作成する](walkthrough-creating-a-dataset-with-the-dataset-designer.md)です。  
  
2.  デザイナーでデータ テーブルのタイトル バーをダブルクリックします。  
  
     `RowChanging` イベント ハンドラーを使用して部分クラスが作成され、コード エディターが開きます。  
  
    > [!NOTE]
    >  C# プロジェクトでは、<xref:System.Data.DataTable.RowChanging> イベントのイベント ハンドラーはデータセット デザイナーにより自動作成されません。 処理するメソッドを作成する必要がある、<xref:System.Data.DataTable.RowChanging>イベントと、テーブルの初期化メソッドでイベントをフックし、コードを実行します。  
  
3.  部分クラスの宣言内にユーザー コードを追加します。  
  
4.  次のコードを検証中にユーザー コードを追加する場所を示しています、<xref:System.Data.DataTable.RowChanging>イベント。 C# の例には、最大イベント ハンドラー メソッドをフックするコードも含まれています、`OrdersRowChanging`イベント。  
  
    ```vb  
    Partial Class OrdersDataTable  
        Private Sub OrdersDataTable_OrdersRowChanging(ByVal sender As System.Object, ByVal e As OrdersRowChangeEvent) Handles Me.OrdersRowChanging  
            ' Add logic to validate columns here.  
            If e.Row.RequiredDate <= e.Row.OrderDate Then  
                ' Set the RowError if validation fails.  
                e.Row.RowError = "Required Date cannot be on or before the OrderDate"  
            Else  
                ' Clear the RowError when validation passes.  
                e.Row.RowError = ""  
            End If  
        End Sub  
    End Class  
    ```  
    ```csharp  
    partial class OrdersDataTable  
    {  
        public override void EndInit()  
        {  
            base.EndInit();  
            // Hook up the event to the  
            // RowChangingEvent method.  
            OrdersRowChanging += RowChangingEvent;  
        }  
  
        public void RowChangingEvent(object sender, OrdersRowChangeEvent e)  
        {  
            // Perform the validation logic.  
            if (e.Row.RequiredDate <= e.Row.OrderDate)  
            {  
                // Set the row to an error when validation fails.  
                e.Row.RowError = "Required Date cannot be on or before the OrderDate";  
            }  
            else  
            {  
                // Clear the RowError if validation passes.  
                e.Row.RowError = "";  
            }  
        }  
    }  
    ```  
  
## <a name="see-also"></a>関連項目  
 [N 層データ アプリケーションの概要](../data-tools/n-tier-data-applications-overview.md)   
 [チュートリアル: N 層データ アプリケーションの作成](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [データセットのデータの検証](../data-tools/validate-data-in-datasets.md)