---
title: N 層データセットに検証を追加する |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e7b9955cf71b1d8862274d4b3501cee35ddd080f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49212384"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>n 層データセットに検証を追加する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
n 層ソリューションに分離されたデータセットへの検証の追加は、単一ファイルのデータセット (1 つのプロジェクト内のデータセット) に検証を追加するのと基本的には同じです。 データで検証を実行する位置として推奨されるのは、データ テーブルの <xref:System.Data.DataTable.ColumnChanging> イベントや <xref:System.Data.DataTable.RowChanging> イベントの発生時です。  
  
 [の作成と型指定されたデータセットの編集](../data-tools/creating-and-editing-typed-datasets.md)する列のユーザー コードを追加することができます、部分クラスを作成する機能を提供します-行し、データセット内のデータ テーブルのイベントを変更します。 N 層ソリューション内のデータセットにコードを追加する方法の詳細については、次を参照してください。 [n 層アプリケーションでのデータセットにコードを追加](../data-tools/add-code-to-datasets-in-n-tier-applications.md)、および[n 層アプリケーションの TableAdapters にコードを追加](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)します。 部分クラスの詳細については、次を参照してください。[方法: クラスを部分クラス (クラス デザイナー) に分割](../ide/how-to-split-a-class-into-partial-classes-class-designer.md)または[部分クラスとメソッド](http://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1)します。  
  
> [!NOTE]
>  データセットを Tableadapter から分離する場合 (設定して、 **DataSet プロジェクト**プロパティ)、プロジェクト内の既存のデータセット部分クラスが自動的に移動しません。 既存のデータセット部分クラスは、手動でデータセット プロジェクトに移動する必要があります。  
  
> [!NOTE]
>  C# では、<xref:System.Data.DataTable.ColumnChanging> イベントおよび <xref:System.Data.DataTable.RowChanging> イベントのイベント ハンドラーはデータセット デザイナーにより自動作成されません。 手動でイベント ハンドラーを作成し、基になるイベントのイベント ハンドラーをフックする必要があります。 次の手順では、Visual Basic と c# の両方で必要なイベント ハンドラーを作成する方法について説明します。  
  
## <a name="validatechanges-to-individual-columns"></a>個々 の列に Validatechanges  
 個々の列の値は、<xref:System.Data.DataTable.ColumnChanging> イベントを処理することにより検証します。 <xref:System.Data.DataTable.ColumnChanging>列の値が変更されたときにイベントが発生します。 イベント ハンドラーを作成、<xref:System.Data.DataTable.ColumnChanging>必要な列をダブルクリックして、イベント、[の作成と型指定されたデータセットの編集](../data-tools/creating-and-editing-typed-datasets.md)します。  
  
 最初に列をダブルクリックすると、デザイナーにより <xref:System.Data.DataTable.ColumnChanging> イベントのイベント ハンドラーが生成されます。 `If…Then`明細書が作成、特定の列をテストすることもできます。 たとえば、Northwind の Orders テーブルの RequiredDate 列をダブルクリックすると、次のコードが生成されます。  
  
```vb  
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging  
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then  
        ' Add validation code here.  
    End If  
End Sub  
```  
  
> [!NOTE]
>  C# プロジェクトでは、データセットの部分クラスとデータセットの個々のテーブルのみがデータセット デザイナーにより作成されます。 C# では、Visual Basic と同様に <xref:System.Data.DataTable.ColumnChanging> イベントおよび <xref:System.Data.DataTable.RowChanging> イベントのイベント ハンドラーはデータセット デザイナーにより自動作成されません。 C# プロジェクトでは、イベントを処理し、メソッドは、基になるイベントをフックする方法を手動で作成する必要があります。 次の手順では、必要なイベント ハンドラーを Visual Basic と C# の両方で作成する方法について説明します。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>個々の列値の変更時に検証を追加するには  
  
1.  データセットを開き、[の作成と型指定されたデータセットの編集](../data-tools/creating-and-editing-typed-datasets.md)をダブルクリックして、 **.xsd**ファイル**ソリューション エクスプ ローラー**します。 詳細については、次を参照してください。[方法: データセット デザイナーでデータセットを開く](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)します。  
  
2.  検証する列をダブルクリックします。 この操作によって <xref:System.Data.DataTable.ColumnChanging> イベント ハンドラーが作成されます。  
  
    > [!NOTE]
    >  データセット デザイナーでは、C# イベントのイベント ハンドラーは自動作成されません。 次のセクションでは、c# でイベントを処理するために必要なコードが含まれます。 `SampleColumnChangingEvent` 作成され、フックし、<xref:System.Data.DataTable.ColumnChanging>内のイベント、<xref:System.Data.DataTable.EndInit%2A>メソッド。  
  
3.  アプリケーションの要件を満たすデータが `e.ProposedValue` に含まれていることを検証するコードを追加します。 指定された値が受け入れられない場合、エラーがあることを表すように該当する列を設定します。  
  
     次のコード例を検証する、**数量**列が 0 よりも多く含まれています。 場合**数量**は以下を 0 に、列はエラーに設定します。 `Else`場合、句は、エラーをクリアします。**数量**が 0 を超えています。 列変更イベント ハンドラー内のコードは、次のようになります。  
  
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
    // C#  
    // Add this code to the DataTable   
    // partial class.  
  
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
  
## <a name="validatechanges-to-whole-rows"></a>行全体を Validatechanges  
 行全体の値は、<xref:System.Data.DataTable.RowChanging> イベントを処理することにより検証します。 <xref:System.Data.DataTable.RowChanging> イベントは、すべての列の値がコミットされたときに発生します。 ある列の値が別の列の値に依存している場合は、<xref:System.Data.DataTable.RowChanging> イベントで検証を行う必要があります。 たとえば、Northwind の Orders テーブルの OrderDate と RequiredDate について考えます。  
  
 注文が入力されると、RequiredDate が OrderDate と同じか、それより前の日付の注文が入力されていないかを検証します。 この例では、RequiredDate 列と OrderDate 列の両方を比較する必要があるため、個々の列の変更を検証しても意味がありません。  
  
 イベント ハンドラーを作成、<xref:System.Data.DataTable.RowChanging>イベントで、テーブルのタイトル バー内のテーブル名をダブルクリックして、[の作成と型指定されたデータセットの編集](../data-tools/creating-and-editing-typed-datasets.md)します。  
  
#### <a name="to-add-validation-during-changes-to-whole-rows"></a>行全体の変更時に検証を追加するには  
  
1.  データセットを開き、[の作成と型指定されたデータセットの編集](../data-tools/creating-and-editing-typed-datasets.md)をダブルクリックして、 **.xsd**ファイル**ソリューション エクスプ ローラー**します。 詳細については、次を参照してください。[方法: データセット デザイナーでデータセットを開く](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)します。  
  
2.  デザイナーでデータ テーブルのタイトル バーをダブルクリックします。  
  
     `RowChanging` イベント ハンドラーを使用して部分クラスが作成され、コード エディターが開きます。  
  
    > [!NOTE]
    >  C# プロジェクトでは、<xref:System.Data.DataTable.RowChanging> イベントのイベント ハンドラーはデータセット デザイナーにより自動作成されません。 処理するメソッドを作成する必要がある、<xref:System.Data.DataTable.RowChanging>イベントと、テーブルの初期化メソッドでイベントにフックするコードを実行します。  
  
3.  部分クラスの宣言内にユーザー コードを追加します。  
  
4.  次のコードに、Visual Basic の <xref:System.Data.DataTable.RowChanging> イベント発生時に検証を行うユーザー コードを追加する場所を示します。  
  
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
  
5.  次のコードに、`RowChanging` イベント ハンドラーを作成する方法と、C# の <xref:System.Data.DataTable.RowChanging> イベント発生時に検証を行うユーザー コードを追加する場所を示します。  
  
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

