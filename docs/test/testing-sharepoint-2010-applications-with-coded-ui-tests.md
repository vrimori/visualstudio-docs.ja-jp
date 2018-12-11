---
title: コード化された UI テストを使用して SharePoint アプリケーションをテストする
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 91d17857f1d20508041ad6c5daa90a962d6d30e6
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895445"
---
# <a name="test-sharepoint-applications-with-coded-ui-tests"></a>コード化された UI テストを使用して SharePoint アプリケーションをテストする

コード化された UI テストを SharePoint アプリケーションに含めると、UI コントロールを含むアプリケーション全体が正しく機能していることを検証できます。 コード化された UI テストでは、ユーザー インターフェイスの値とロジックも検証できます。

コード化された UI テストの長所については、「[UI オートメーションを使用してコードをテストする](../test/use-ui-automation-to-test-your-code.md)」を参照してください。

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**必要条件**

- Visual Studio Enterprise

## <a name="create-a-coded-ui-test-for-a-sharepoint-app"></a>SharePoint アプリのコード化された UI テストを作成する

SharePoint アプリケーションでの[コード化された UI テストの作成](../test/use-ui-automation-to-test-your-code.md)方法は、他の種類のアプリケーションでのテストの作成方法と同じです。 記録と再生は、**Web 編集**インターフェイス上のすべてのコントロールでサポートされています。 カテゴリと Web パーツを選択するためのインターフェイスは、すべてが標準 Web コントロールです。

![SharePoint Web パーツ](../test/media/cuit_sharepoint.png)

> [!NOTE]
> 操作を記録している場合は、コードを生成する前に操作を検証します。 マウス ホバーにはいくつかの動作が関連付けられているため、既定で有効になっています。 コード化された UI テストから冗長なホバーを削除するようにしてください。 そのためには、テスト用のコードを編集するか、 [コード化された UI テスト エディター](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)を使用します。

## <a name="test-office-controls-within-a-sharepoint-app"></a>SharePoint アプリ内で Office コントロールをテストする

SharePoint アプリでいくつかの Office Web パーツの自動化を有効にするには、コードを少し変更する必要があります。

> [!NOTE]
> SharePoint アプリケーションでは、Visio と PowerPoint のコントロールをテストできません。

### <a name="excel-cell-controls"></a>Excel のセル コントロール

Excel セル コントロールを含めるには、コード化された UI テストのコードを少し変更する必要があります。

> [!WARNING]
> Excel のセルにテキストを入力してから方向キーを操作すると、正しく記録されません。 セルの選択にはマウスを使用してください。

空のセルに対する操作を記録している場合は、セルをダブルクリックしてからテキスト設定操作を実行して、コードを変更する必要があります。 そうする必要があるのは、セルをクリックした後、キーボードを操作すると、セル内の `textarea` がアクティブになるためです。 単に空のセルで `setvalue` を記録すると、セルがクリックされるまでは存在しない `editbox` が検索されます。 例:

```csharp
Mouse.DoubliClick(uiItemCell,new Point(31,14));
uiGridKeyboardInputEdit.Text=value;
```

空でないセルに対する操作を記録している場合は、セルにテキストを追加したときに新しい \<div> コントロールがセルの子として追加されるため、記録はより複雑になります。 新しい \<div> コントロールには、入力したテキストが含まれます。 レコーダーは新しい \<div> コントロールに対する操作を記録する必要がありますが、新しい \<div> コントロールはテキストが入力されるまで存在しないため、記録できません。 この問題に対応するために、手動で次のようにコードを変更する必要があります。

1. セルの初期化に移動して、 `RowIndex` および `ColumnIndex` プライマリ プロパティを作成します。

    ```csharp
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";
    ```

2. セルの `HtmlDiv` 子を検索します。

    ```csharp
    private UITestControl getControlToDoubleClick(HtmlCell cell)
    {
         if (String.IsNullOrEmpty(cell.InnerText)) return cell;
         HtmlDiv pane = new HtmlDiv(cell);
         pane.FilterProperties[HtmlDiv.PropertyNames.InnerText] = cell.InnerText;
         // Class is an important property in finding pane
         pane.FilterProperties[HtmlDiv.PropertyNames.Class] = "cv-nwr";
         UITestControlCollection panes = pane.FindMatchingControls();
         return panes[0];
    }
    ```

3. `HtmlDiv`にマウスのダブルクリック操作のコードを追加します。

    ```csharp
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )
    ```

4. `TextArea`にテキストを設定するコードを追加します。

    ```csharp
    uIGridKeyboardInputEdit.Text = value; }
    ``

## See also

- [Use UI automation to test your code](../test/use-ui-automation-to-test-your-code.md)
- [Create SharePoint solutions](../sharepoint/create-sharepoint-solutions.md)
- [Verify and debug SharePoint code](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [Build and debug SharePoint solutions](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Profile the performance of SharePoint applications](../sharepoint/profiling-the-performance-of-sharepoint-applications.md)
