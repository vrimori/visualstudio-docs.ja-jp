---
title: "方法 : データセットにデータを読み込む | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "データ [Visual Basic], 読み込み (データセットへの)"
  - "データセット [Visual Basic], 塗りつぶし"
  - "DataTable オブジェクト, 読み込み"
  - "TableAdapter.Fill"
  - "TableAdapter.GetData"
ms.assetid: 7ab436d4-54ba-4621-902f-3f193279e18c
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 方法 : データセットにデータを読み込む
「データセットにデータを読み込む」という言い回しは、実際にはデータセットを構成する個々の <xref:System.Data.DataTable> オブジェクトにデータを読み込むことを意味します。  TableAdapter クエリを実行するか、またはデータ アダプター \(たとえば、<xref:System.Data.SqlClient.SqlDataAdapter>\) のコマンドを実行して、データ テーブルにデータを読み込みます。  
  
 データセットを作成した方法によって、TableAdapter とデータ アダプターのいずれを使用するかが決まります。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で[データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)などのデザイン ツールを使用した場合は、データセットに TableAdapter が含まれています。  TableAdapter の詳細については、「[TableAdapter の概要](../data-tools/tableadapter-overview.md)」を参照してください。  プログラムでデータセットを作成した場合は、通常、データ テーブルにデータを読み込むデータ アダプターを作成する必要があります。  
  
> [!NOTE]
>  [ウィンドウ](../Topic/Data%20Sources%20Window.md)からフォームに項目をドラッグすると、データ テーブルにデータを読み込むコードが `Form_Load` イベント ハンドラーに自動的に追加されます。  コード エディターでフォームを開くと、特定のテーブルにデータを読み込む構文が表示されます。  フォームの読み込み時にテーブルにデータを読み込まない場合は、このコードを別のメソッドに移動するか、またはこのコード全体を削除できます。  
  
## TableAdapter を使用したデータセットへのデータの読み込み  
 TableAdapter のクエリを呼び出し、データセットのデータ テーブルにデータを読み込むことができます。  データを読み込む <xref:System.Data.DataTable> を TableAdapter クエリに渡します。  クエリがパラメーターを使用する場合、パラメーターもメソッドに渡します。  データセットに複数のテーブルが格納されている場合は、各テーブルに対して個別に TableAdapter を用意し、各テーブルにデータを個別に読み込む必要があります。  
  
> [!NOTE]
>  既定では、TableAdapter クエリを実行するたびに、クエリの結果がテーブルに読み込まれる前にテーブル内のデータが消去されます。  TableAdapter の `ClearBeforeFill` プロパティを `false` に設定すると、テーブル内の既存のデータを保持したまま結果を追加できます。  
  
#### TableAdapter を使用してデータセットにデータを読み込むには  
  
1.  **コード エディター**でフォームまたはコンポーネントを開きます。  
  
2.  アプリケーション内で、データ テーブルにデータを読み込む必要のある場所にコードを追加します。  クエリでパラメーターを使用しない場合は、データを読み込む <xref:System.Data.DataTable> を渡します。  コードは次のようになります。  
  
     [!code-cs[VbRaddataFillingAndExecuting#4](../data-tools/codesnippet/CSharp/how-to-fill-a-dataset-with-data_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#4](../data-tools/codesnippet/VisualBasic/how-to-fill-a-dataset-with-data_1.vb)]  
  
3.  クエリでパラメーターを使用する場合は、データを読み込む <xref:System.Data.DataTable> とクエリに必要なパラメーターを渡します。  クエリの実際のパラメーターに応じて異なりますが、コードは次の例のようになります。  
  
     [!code-cs[VbRaddataFillingAndExecuting#5](../data-tools/codesnippet/CSharp/how-to-fill-a-dataset-with-data_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#5](../data-tools/codesnippet/VisualBasic/how-to-fill-a-dataset-with-data_2.vb)]  
  
## DataAdapter を使用したデータセットへのデータの読み込み  
 データ アダプターの `Fill` メソッドを呼び出すことができます。  これにより、アダプターは `SelectCommand` プロパティで参照されている SQL ステートメントまたはストアド プロシージャを実行し、その結果をデータセットのテーブルに格納します。  データセットに複数のテーブルが格納されている場合は、各テーブルに対して個別にデータ アダプターを用意し、各テーブルに個別にデータを読み込む必要があります。  
  
#### DataAdapter を使用してデータセットにデータを読み込むには  
  
-   <xref:System.Data.Common.DataAdapter> の <xref:System.Data.Common.DataAdapter.Fill%2A> メソッドを呼び出し、データを読み込む <xref:System.Data.DataSet> または <xref:System.Data.DataTable> を渡します。  次に例を示します。  
  
     [!code-cs[VbRaddataFillingAndExecuting#6](../data-tools/codesnippet/CSharp/how-to-fill-a-dataset-with-data_3.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#6](../data-tools/codesnippet/VisualBasic/how-to-fill-a-dataset-with-data_3.vb)]  
  
     通常は、データを読み込む <xref:System.Data.DataTable> の名前を指定します。  特定のデータ テーブルの代わりに <xref:System.Data.DataSet> の名前を渡す場合は、`Table1` という名前の <xref:System.Data.DataTable> をデータセットに追加し、データベースから結果を読み込みます \(これは、データセットの既存の <xref:System.Data.DataTable> にデータを読み込む場合と異なります\)。  詳細については、「[DataAdapter からの DataSet の読み込み](../Topic/Populating%20a%20DataSet%20from%20a%20DataAdapter.md)」を参照してください。  
  
## 参照  
 [データセットへのデータの読み込み](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)