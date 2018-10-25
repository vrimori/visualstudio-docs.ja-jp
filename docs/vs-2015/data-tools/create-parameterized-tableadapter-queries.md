---
title: パラメーター化された TableAdapter クエリの作成 |Microsoft Docs
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
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 150105de459912716cd3cfccff9efb35927c7d49
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823503"
---
# <a name="create-parameterized-tableadapter-queries"></a>パラメーター付きの TableAdapter クエリを作成する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
パラメーター クエリは、クエリ内の WHERE 句の条件を満たすデータを返します。 たとえば、顧客リストをパラメーター化して、顧客のリストを戻す SQL ステートメントに `WHERE City = @City` を追加することで、特定の都市の顧客のみが表示されるようにできます。  
  
 パラメーター化された TableAdapter クエリを作成する、[データセット デザイナー](../data-tools/creating-and-editing-typed-datasets.md)します。Windows アプリケーションで作成することも、**データ ソースのパラメーター化**コマンドを**データ**メニュー。 **データ ソースのパラメーター化**コマンドは、パラメーター値を入力して、クエリを実行できますフォーム上のコントロールを作成します。  
  
> [!NOTE]
>  パラメーター化クエリを構築するときに、に対してコーディングをしているデータベースに固有のパラメーター表記を使用します。 たとえば、Access データ ソースと OleDb データ ソースは疑問符 "?" を使用してパラメーターを表すため、WHERE 句は `WHERE City = ?` のようになります。  
  
> [!NOTE]
>  アクティブな設定または使用しているエディションによって、ヘルプの記載されているダイアログ ボックスとメニュー コマンドが表示が異なる場合があります。 設定を変更するには、**ツール**メニュー選択し、**インポートおよびエクスポート設定**します。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## <a name="create-a-parameterized-tableadapter-query"></a>パラメーター化された TableAdapter クエリを作成します。  
  
#### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>データセット デザイナーでパラメーター クエリを作成するには  
  
-   新しい TableAdapter を作成し、目的のパラメーターを含む WHERE 句を SQL ステートメントに追加します。 詳細については、次を参照してください。[作成し、Tableadapter 構成](../data-tools/create-and-configure-tableadapters.md)します。  
  
     - または -  
  
-   既存の TableAdapter にクエリを追加し、目的のパラメーターを含む WHERE 句を SQL ステートメントに追加します。 詳細については、次を参照してください。[方法: TableAdapter クエリの作成](../data-tools/how-to-create-tableadapter-queries.md)です。  
  
#### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>データ バインド フォームの設計時にパラメーター クエリを作成するには  
  
1.  フォーム上の既にデータセットにバインドされているコントロールを選択します。 詳細については、次を参照してください。 [Visual Studio でのデータにコントロールを Windows フォームのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)します。  
  
2.  **データ**メニューの **クエリの追加**します。  
  
3.  完了、**検索条件ビルダー**  ダイアログ ボックスで、SQL ステートメントに、目的のパラメーターを含む WHERE 句を追加します。  
  
### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>既存のデータ バインド フォームにクエリを追加するには  
  
1. **Windows フォーム デザイナー**でフォームを開きます。  
  
2. **データ**メニューの **クエリの追加**または**データ スマート タグ**します。  
  
   > [!NOTE]
   >  場合**クエリの追加**では使用できません、**データ**メニューで、パラメーターの追加設定の表示、データ ソースにするフォームにコントロールを選択します。 たとえば、フォームに <xref:System.Windows.Forms.DataGridView> コントロールのデータが表示される場合は、そのコントロールを選択します。 フォームに個々のコントロールのデータが表示される場合は、いずれかのデータ バインド コントロールを選択します。  
  
3. **ソース テーブルのデータの選択**領域で、追加するパラメーター化を選択 tablethat します。  
  
4. 名前を入力、**新しいクエリ名**新しいクエリを作成する場合します。  
  
    - または -  
  
    クエリを選択、**既存のクエリ名**ボックス。  
  
5. **クエリ テキスト**ボックスに、パラメーターを受け取るクエリを入力します。  
  
6. 選択**OK**します。  
  
    パラメーターを入力するコントロールと**ロード**でフォームにボタンを追加、<xref:System.Windows.Forms.ToolStrip>コントロール。  
  
   現在の値を持たないレコードを照会するときに、TableAdapter のパラメーターが null 値を割り当てることできます。 たとえば、次のクエリを持つ、`ShippedDate`パラメーターでその`WHERE`句。  
  
   `SELECT CustomerID, OrderDate, ShippedDate`  
  
   `FROM Orders`  
  
   `WHERE (ShippedDate = @ShippedDate) OR`  
  
   `(ShippedDate IS NULL)`  
  
   これは TableAdapter 上のクエリの場合、次のコードにまだ配送されていないすべての注文のクエリを実行でした。  
  
   [!code-csharp[VbRaddataTableAdapters#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form2.cs#8)]
   [!code-vb[VbRaddataTableAdapters#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form2.vb#8)]  
  
#### <a name="to-enable-a-query-to-accept-null-values"></a>Null 値を使用するためのクエリを有効にするには  
  
1.  **データセット デザイナー**、null パラメーター値をそのまま使用する必要がある TableAdapter クエリを選択します。  
  
2.  **プロパティ**ウィンドウで、**パラメーター**します。省略記号ボタンを押します (**.**) ボタンをクリックする、**パラメーター コレクション エディター**します。  
  
3.  Null 値を許容するパラメーターを選択し、設定、 **AllowDbNull**プロパティを`true`します。  
  
## <a name="see-also"></a>関連項目  
 [TableAdapters を使用してデータセットを入力する](../data-tools/fill-datasets-by-using-tableadapters.md)

