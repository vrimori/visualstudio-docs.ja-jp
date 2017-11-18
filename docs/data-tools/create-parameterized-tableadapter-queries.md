---
title: "パラメーター化された TableAdapter クエリを作成 |Microsoft ドキュメント"
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
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 6b80f370f670f4dff4b65d7c0e7658f855d5e573
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="create-parameterized-tableadapter-queries"></a>パラメーター化された TableAdapter クエリを作成します。
パラメーター クエリは、クエリ内の WHERE 句の条件を満たすデータを返します。 たとえば、顧客リストをパラメーター化して、顧客のリストを戻す SQL ステートメントに `WHERE City = @City` を追加することで、特定の都市の顧客のみが表示されるようにできます。  
  
 パラメーター化された TableAdapter クエリを作成する、**データセット デザイナー**です。Windows アプリケーションを作成することも、**データ ソースのパラメーター化**コマンドを**データ**メニュー。 **データ ソースのパラメーター化**コマンドを入力パラメーターの値と、クエリを実行できるフォーム コントロールを作成します。  
  
> [!NOTE]
>  パラメーター化クエリを構築するときに、に対してコーディングを行っているデータベースに固有のパラメーター表記を使用します。 たとえば、Access データ ソースと OleDb データ ソースは疑問符 "?" を使用してパラメーターを表すため、WHERE 句は `WHERE City = ?` のようになります。  
  
> [!NOTE]
>  アクティブな設定または使用しているエディションによっては、ヘルプに記載されているダイアログ ボックスとメニュー コマンドが表示が異なる場合があります。 設定を変更するには、**ツール**メニュー**インポートおよびエクスポート設定**です。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="create-a-parameterized-tableadapter-query"></a>パラメーター化された TableAdapter クエリを作成します。  
  
#### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>データセット デザイナーでパラメーター クエリを作成するには  
  
-   新しい TableAdapter を作成し、目的のパラメーターを含む WHERE 句を SQL ステートメントに追加します。 詳細については、次を参照してください。[作成し、Tableadapter を構成](../data-tools/create-and-configure-tableadapters.md)です。  
  
     または  
  
-   既存の TableAdapter にクエリを追加し、目的のパラメーターを含む WHERE 句を SQL ステートメントに追加します。
  
#### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>データ バインド フォームの設計時にパラメーター クエリを作成するには  
  
1.  フォーム上の既にデータセットにバインドされているコントロールを選択します。 詳細については、次を参照してください。 [Visual Studio でのデータにコントロールを Windows フォームのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)です。  
  
2.  **データ**メニューの **クエリの追加**です。  
  
3.  完了、**検索条件ビルダー**ダイアログ ボックスで、SQL ステートメントに、目的のパラメーターを含む WHERE 句を追加します。  
  
### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>既存のデータ バインド フォームにクエリを追加するには  
  
1.  フォームを開いて、 **Windows フォーム デザイナー**です。  
  
2.  **データ**メニューの **クエリの追加**または**データ スマート タグ**です。  
  
    > [!NOTE]
    >  場合**クエリの追加**では使用できません、**データ**メニューで、データ ソース表示するフォーム上のコントロールが、パラメーターを追加するを選択します。 たとえば、フォームに <xref:System.Windows.Forms.DataGridView> コントロールのデータが表示される場合は、そのコントロールを選択します。 フォームに個々のコントロールのデータが表示される場合は、いずれかのデータ バインド コントロールを選択します。  
  
3.  **[データ ソース テーブル**] 領域にパラメーターの追加するテーブルを選択します。  
  
4.  名前を入力、**新しいクエリ名**新しいクエリを作成する場合します。  
  
     または  
  
     クエリを選択して、**既存のクエリ名**ボックス。  
  
5.  **クエリ テキスト**ボックスに、パラメーターを受け取るクエリを入力します。  
  
6.  **[OK]** を選択します。  
  
     パラメーターを入力するコントロールと**ロード**でフォームにボタンが追加されます、<xref:System.Windows.Forms.ToolStrip>コントロール。  
  
#### <a name="querying-for-null-values"></a>Null 値のクエリを実行します。  
現在の値を持たないレコードを照会する場合により、TableAdapter パラメーターに null 値を割り当てることができます。 たとえば、次のクエリを持つ、`ShippedDate`パラメーターにその`WHERE`句。  
  
 ```sql
SELECT CustomerID, OrderDate, ShippedDate  
FROM Orders  
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```  
  
 これは TableAdapter 上のクエリの場合、次のコードで出荷されていないすべての注文してクエリを可能性があります。  
  
 [!code-csharp[VbRaddataTableAdapters#8](../data-tools/codesnippet/CSharp/create-parameterized-tableadapter-queries_1.cs)]
 [!code-vb[VbRaddataTableAdapters#8](../data-tools/codesnippet/VisualBasic/create-parameterized-tableadapter-queries_1.vb)]  

 Null 値を使用するクエリを有効にします。

1.  **データセット デザイナー**、null のパラメーター値を許可する必要がある TableAdapter クエリを選択します。  
  
2.  **プロパティ**ウィンドウで、**パラメーター**、省略記号ボタンをクリックし、(**.**) を開く ボタン、**パラメーター コレクション エディター**です。  
  
3.  Null 値を許容するパラメーターを選択し、設定、 **AllowDbNull**プロパティを`true`です。  
  
## <a name="see-also"></a>関連項目  
 [TableAdapters を使用してデータセットを入力する](../data-tools/fill-datasets-by-using-tableadapters.md)