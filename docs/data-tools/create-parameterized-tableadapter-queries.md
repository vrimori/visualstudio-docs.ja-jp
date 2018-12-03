---
title: パラメーター付きの TableAdapter クエリを作成する
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9d344fdd444a46b3e0434e70850946ef242864b0
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388479"
---
# <a name="create-parameterized-tableadapter-queries"></a>パラメーター付きの TableAdapter クエリを作成する

パラメーター クエリは、クエリ内の WHERE 句の条件を満たすデータを返します。 たとえば、顧客リストをパラメーター化して、顧客のリストを戻す SQL ステートメントに `WHERE City = @City` を追加することで、特定の都市の顧客のみが表示されるようにできます。

パラメーター化された TableAdapter クエリを作成する、**データセット デザイナー**します。Windows アプリケーションで作成することも、**データ ソースのパラメーター化**コマンドを**データ**メニュー。 **データ ソースのパラメーター化**コマンドは、パラメーター値を入力して、クエリを実行できますフォーム上のコントロールを作成します。

> [!NOTE]
> パラメーター化クエリを構築するときに、に対してコーディングをしているデータベースに固有のパラメーター表記を使用します。 たとえば、Access データ ソースと OleDb データ ソースは疑問符 "?" を使用してパラメーターを表すため、WHERE 句は `WHERE City = ?` のようになります。

## <a name="create-a-parameterized-tableadapter-query"></a>パラメーター化された TableAdapter クエリを作成します。

### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>データセット デザイナーでパラメーター クエリを作成するには

-   新しい TableAdapter を作成し、目的のパラメーターを含む WHERE 句を SQL ステートメントに追加します。 詳細については、次を参照してください。[作成し、Tableadapter 構成](../data-tools/create-and-configure-tableadapters.md)します。

     - または -

-   既存の TableAdapter にクエリを追加し、目的のパラメーターを含む WHERE 句を SQL ステートメントに追加します。

### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>データ バインド フォームの設計時にパラメーター クエリを作成するには

1.  フォーム上の既にデータセットにバインドされているコントロールを選択します。 詳細については、次を参照してください。 [Visual Studio でのデータにコントロールを Windows フォームのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)します。

2.  **データ**メニューの **クエリの追加**します。

3.  **[検索条件ビルダー]** ダイアログ ボックスの設定を完了し、目的のパラメーターを含む WHERE 句を SQL ステートメントに追加します。

### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>既存のデータ バインド フォームにクエリを追加するには

1.  **Windows フォーム デザイナー**でフォームを開きます。

2.  **データ**メニューの **クエリの追加**または**データ スマート タグ**します。

    > [!NOTE]
    > **[データ]** メニューの **[クエリの追加]** が使用できない場合は、パラメーターの追加先のデータ ソースを表示するフォーム上のコントロールを選択します。 たとえば、フォームに <xref:System.Windows.Forms.DataGridView> コントロールのデータが表示される場合は、そのコントロールを選択します。 フォームに個々のコントロールのデータが表示される場合は、いずれかのデータ バインド コントロールを選択します。

3.  **ソース テーブルのデータの選択**領域で、パラメーター化を追加するテーブルを選択します。

4.  新しいクエリを作成する場合は、**[新しいクエリ名]** ボックスに名前を入力します。

     - または -

     **[既存のクエリ名]** ボックスでクエリを選択します。

5.  **クエリ テキスト**ボックスに、パラメーターを受け取るクエリを入力します。

6.  **[OK]** を選択します。

     パラメーターを入力するコントロールと **[読み込み]** ボタンが、<xref:System.Windows.Forms.ToolStrip> コントロールのフォームに追加されます。

### <a name="query-for-null-values"></a>Null 値のクエリ

現在の値を持たないレコードを照会するときに、TableAdapter のパラメーターが null 値を割り当てることできます。 たとえば、次のクエリを持つ、`ShippedDate`パラメーターでその`WHERE`句。

 ```sql
SELECT CustomerID, OrderDate, ShippedDate
FROM Orders
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```

これは TableAdapter 上のクエリの場合、次のコードにまだ配送されていないすべての注文のクエリを実行でした。

[!code-csharp[VbRaddataTableAdapters#8](../data-tools/codesnippet/CSharp/create-parameterized-tableadapter-queries_1.cs)]
[!code-vb[VbRaddataTableAdapters#8](../data-tools/codesnippet/VisualBasic/create-parameterized-tableadapter-queries_1.vb)]

Null 値を使用するためのクエリを有効にします。

1.  **データセット デザイナー**、null パラメーター値をそのまま使用する必要がある TableAdapter クエリを選択します。

2.  **プロパティ**ウィンドウで、**パラメーター**、省略記号をクリックします (**.**) ボタンをクリックする、**パラメーター コレクション エディター**します。

3.  Null 値を許容するパラメーターを選択し、設定、 **AllowDbNull**プロパティを`true`します。

## <a name="see-also"></a>関連項目

- [TableAdapters を使用してデータセットを入力する](../data-tools/fill-datasets-by-using-tableadapters.md)