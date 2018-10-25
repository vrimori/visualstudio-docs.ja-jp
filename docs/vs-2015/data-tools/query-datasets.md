---
title: データセットのクエリ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a6e1ff0cd6f77d2155ff4982ca02657a741c02d7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890570"
---
# <a name="query-datasets"></a>データセットのクエリ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
データセット内の特定のレコードを検索するに、DataTable の FindBy メソッドを使用して、テーブルの行のコレクションに対する独自の foreach ループを記述または使用[LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)します。 LINQ to DataSet。  
  
## <a name="dataset-case-sensitivity"></a>データセットの大文字と小文字の区別  
 データセット内にテーブルと列の名前は既定では大文字、つまり、"Customers"という名前のデータセット内のテーブルも参照できます"顧客"として。 SQL サーバーの SQL Server を含む、多数のデータベース内の名前付け規則と一致するこの、既定の動作は、大文字と小文字のデータ要素の名前を区別することはできません。  
  
> [!NOTE]
>  データセットとは異なりスキーマで定義されたデータ要素の名前は大文字小文字を区別するための XML ドキュメントが大文字小文字が区別されます。 たとえば、スキーマのプロトコルは"Customers"、"customers。"と呼ばれる別のテーブルと呼ばれるテーブルを定義するスキーマを使用できます。 これは、結果、大文字と小文字が異なるだけの要素を含むスキーマを使用して、dataset クラスを生成すると、名前が競合。  
  
 大文字小文字の区別、ただし、データセット内のデータを解釈する方法の要因ができます。 たとえば、データセット テーブル内のデータをフィルター処理する検索条件は、比較では大文字小文字を区別するかどうかによって異なる結果を返す可能性があります。 フィルター処理、検索、およびデータセットの並べ替えの大文字小文字の区別を制御する<xref:System.Data.DataSet.CaseSensitive%2A>プロパティ。 データセット内のすべてのテーブルは、既定では、このプロパティの値を継承します。 (個別のテーブルに対してこのプロパティをオーバーライドするには、テーブルの設定によって<xref:System.Data.DataTable.CaseSensitive%2A>プロパティです)。  
  
## <a name="locate-a-specific-row-in-a-data-table"></a>データ テーブル内で特定の行を検索します。  
  
#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>主キー値で指定されたデータセットの行を検索するには  
  
-   1 行を検索するには、厳密に型指定された呼び出し`FindBy`テーブルの主キーを使用するメソッド。  
  
     次の例では、`CustomerID`列が主キーの`Customers`テーブル。 これにより、生成された`FindBy`メソッドは`FindByCustomerID`します。 例では、特定の割り当て方法を示しています<xref:System.Data.DataRow>、生成されたを使用して変数に`FindBy`メソッド。  
  
     [!code-csharp[VbRaddataEditing#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#18)]
     [!code-vb[VbRaddataEditing#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#18)]  
  
#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>主キー値で、型指定されていないデータセットの行を検索するには  
  
-   呼び出す、<xref:System.Data.DataRowCollection.Find%2A>のメソッド、<xref:System.Data.DataRowCollection>コレクション、主キーのパラメーターとして渡します。  
  
     次の例と呼ばれる新しい行を宣言する方法を示しています。`foundRow`の戻り値を割り当てると、<xref:System.Data.DataRowCollection.Find%2A>メソッド。 主キーが見つかった場合は、メッセージ ボックスに列のインデックス 1 の内容が表示されます。  
  
     [!code-csharp[VbRaddataEditing#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#19)]
     [!code-vb[VbRaddataEditing#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#19)]  
  
## <a name="findrows-by-column-values"></a>列の値で Findrows  
  
#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>任意の列の値に基づいて行を検索するには  
  
-   データ テーブルを作成、<xref:System.Data.DataTable.Select%2A>の配列を返すメソッド<xref:System.Data.DataRow>に渡された式に基づく s、<xref:System.Data.DataTable.Select%2A>メソッド。 有効な式を作成する方法の詳細については、ページの「式の構文」セクションを参照してください。、<xref:System.Data.DataColumn.Expression%2A>プロパティ。  
  
     次の例は、使用する方法を示します、<xref:System.Data.DataTable.Select%2A>のメソッド、<xref:System.Data.DataTable>特定の行を検索します。  
  
     [!code-csharp[VbRaddataEditing#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#20)]
     [!code-vb[VbRaddataEditing#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#20)]  
  
## <a name="accessrelated-records"></a>Accessrelated レコード  
 データセット内のテーブルが関係するときに、<xref:System.Data.DataRelation>オブジェクトは、関連するレコードで使用できるように別のテーブル。 など、データセットを含む`Customers`と`Orders`テーブルを利用します。  
  
 使用することができます、<xref:System.Data.DataRelation>呼び出すことによって、関連レコードを検索するオブジェクト、<xref:System.Data.DataRow.GetChildRows%2A>のメソッド、<xref:System.Data.DataRow>親テーブルでします。このメソッドは、関連する子レコードの配列を返します。 呼び出すか、または、<xref:System.Data.DataRow.GetParentRow%2A>のメソッド、<xref:System.Data.DataRow>子テーブルにします。このメソッドは、1 つを返します<xref:System.Data.DataRow>親テーブルから。  
  
 このページは、型指定されたデータセットを使用した例を示します。 型指定されていないデータセットのリレーションシップを移動する方法の詳細については、次を参照してください。 [Datarelation の移動](http://msdn.microsoft.com/library/e5e673f4-9b44-45ae-aaea-c504d1cc5d3e)します。  
  
> [!NOTE]
>  Windows フォーム アプリケーションで作業しているし、データ バインド機能を使用してデータを表示する、デザイナーで生成されたフォームは、アプリケーションのための十分な機能を提供可能性があります。 詳細については、次を参照してください。 [Visual Studio でのデータ コントロールをバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)します。 具体的を参照してください[方法: Windows フォーム アプリケーションで関連データを表示](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md)と[チュートリアル: Windows フォーム上で関連データを表示する](../data-tools/walkthrough-displaying-related-data-on-a-windows-form.md)します。  
  
 次のコード例では、型指定されたデータセットのリレーションシップを上下に移動する方法を示します。 型指定されたコードの例として使用<xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) され、生成された`FindBy` *PrimaryKey* (`FindByCustomerID`) を目的の行を見つけて、関連レコードを返すメソッド。 例では、正しくコンパイルして実行した場合にのみ。  
  
- という名前のデータセットのインスタンス`NorthwindDataSet`で、`Customers`テーブル。  
  
- `Orders`テーブル。  
  
- という名前のリレーションシップ`FK_Orders_Customers`使用可能な 2 つのテーブルに関連する、コードのスコープ  
  
  さらに、両方のテーブルは、返されるレコードにデータを格納する必要があります。  
  
#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>選択した親レコードのレコードの子を取得するには  
  
-   呼び出す、<xref:System.Data.DataRow.GetChildRows%2A>メソッドは、特定の`Customers`データ行し、からの行の配列を返す、`Orders`テーブル。  
  
     [!code-csharp[VbRaddataDatasets#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDatasets#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#6)]  
  
#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>選択されている子レコードの親レコードを取得するには  
  
-   呼び出す、<xref:System.Data.DataRow.GetParentRow%2A>メソッドは、特定の`Orders`データ行、および戻り値の 1 つの行、`Customers`テーブル。  
  
     [!code-csharp[VbRaddataDatasets#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDatasets#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#7)]

