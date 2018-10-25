---
title: '方法: データセットにデータ |Microsoft Docs'
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
- TableAdapter.GetData
- TableAdapter.Fill
- datasets [Visual Basic], filling
- DataTable objects, loading
- data [Visual Basic], loading into datasets
ms.assetid: 7ab436d4-54ba-4621-902f-3f193279e18c
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: f36aa2dac656f6fd27b656d0ddfb58a758eb6487
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49295998"
---
# <a name="how-to-fill-a-dataset-with-data"></a>方法: データセットにデータ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

「データセットのデータの読み込み」という語句が個別にデータを読み込むことを指します<xref:System.Data.DataTable>データセットを作成するオブジェクト。 TableAdapter クエリを実行することによって、またはデータ アダプターを実行することによって、データ テーブルを入力する (たとえば、 <xref:System.Data.SqlClient.SqlDataAdapter>) コマンド。  
  
 Tableadapter またはデータ アダプターを使用するかどうかは、データセットの作成方法によって異なります。 デザイン ツールを使用している場合[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]など、[データ ソース構成ウィザード](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)Tableadapter がデータセットに含まれています。 Tableadapter の詳細については、次を参照してください。 [TableAdapter の概要](../data-tools/tableadapter-overview.md)します。 データセットをプログラムで作成した場合は、データ テーブルにデータを読み込むデータ アダプターを作成する必要が通常あります。  
  
> [!NOTE]
>  項目をドラッグしたときに、[データ ソース ウィンドウ](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)、フォームにデータをデータ テーブルを設定するコードが自動的に追加、`Form_Load`イベント ハンドラー。 特定のテーブルを入力する正確な構文を参照してください。 コード エディターでフォームを開きます。 フォームの読み込み時に、テーブルを入力しない場合は、このコードを他のメソッドに移動します。 または、完全に削除できます。  
  
## <a name="filling-a-dataset-using-a-tableadapter"></a>TableAdapter を使用してデータセットの読み込み  
 データセット内のデータ テーブルにデータを読み込む TableAdapter にクエリを呼び出すことができます。 渡す、 <xref:System.Data.DataTable> TableAdapter クエリを入力します。 クエリがパラメーターを受け取る場合も、メソッドに渡します。 データセットに複数のテーブルが含まれている場合は、テーブルごとに個別の Tableadapter が必要し、各テーブルを個別に入力する必要があります。  
  
> [!NOTE]
>  既定では、TableAdapter クエリを実行するたびに、テーブルに読み込まれているクエリの結果の前に、テーブル内のデータが消去します。 テーブルの既存のデータを保持し、結果を追加するには、TableAdapter のできます`ClearBeforeFill`プロパティを`false`します。  
  
#### <a name="to-fill-a-dataset-with-data-using-a-tableadapter"></a>データセットに TableAdapter を使用してデータを格納するには  
  
1.  フォームまたはコンポーネントで開く、**コード エディター**します。  
  
2.  任意の場所をデータ テーブルにデータを読み込む必要がある、アプリケーションでコードを追加します。 クエリがパラメーターを受け取らない場合を渡す、<xref:System.Data.DataTable>を格納します。 コードは、次のようになります。  
  
     [!code-csharp[VbRaddataFillingAndExecuting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#4)]
     [!code-vb[VbRaddataFillingAndExecuting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#4)]  
  
3.  クエリにパラメーターがある場合は、パラメーターを渡す、<xref:System.Data.DataTable>塗りつぶしをクエリで想定されているパラメーター。 クエリの実際のパラメーターに応じて、コードは次の例のようなになります。  
  
     [!code-csharp[VbRaddataFillingAndExecuting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#5)]
     [!code-vb[VbRaddataFillingAndExecuting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#5)]  
  
## <a name="filling-a-dataset-using-a-dataadapter"></a>DataAdapter を使用してデータセットの読み込み  
 データ アダプターの呼び出す`Fill`メソッド。 これが原因で SQL ステートメントを実行するアダプターまたはでストアド プロシージャが参照されているその`SelectCommand`プロパティと、データセット内のテーブルに、その結果を格納します。 データセットに複数のテーブルが含まれている場合は、テーブルごとに個別のデータ アダプターがおよび、各テーブルを個別に入力する必要があります。  
  
#### <a name="to-fill-a-dataset-with-data-using-a-dataadapter"></a>DataAdapter を使用してデータをデータセットに格納するには  
  
-   呼び出す、<xref:System.Data.Common.DataAdapter.Fill%2A>のメソッド、<xref:System.Data.Common.DataAdapter>で渡し、<xref:System.Data.DataSet>または<xref:System.Data.DataTable>にデータを読み込みます。 例えば:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#6)]
     [!code-vb[VbRaddataFillingAndExecuting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#6)]  
  
     通常の名前を指定する必要があります、<xref:System.Data.DataTable>にデータを読み込みます。 名前を渡す場合、 <xref:System.Data.DataSet> 、特定のデータ テーブルではなく、<xref:System.Data.DataTable>という名前の`Table1`がデータセットに追加され、データベースからの結果に読み込まれる (既存のデータの読み込みではなく<xref:System.Data.DataTable>データセットで)。 詳細については、次を参照してください。 [DataAdapter からの Dataset](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153)します。  
  
## <a name="see-also"></a>関連項目  
 [Tableadapter を使用してデータセットを入力します。](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [データを受信するアプリケーションを準備します。](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでデータの編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [データの保存](../data-tools/saving-data.md)