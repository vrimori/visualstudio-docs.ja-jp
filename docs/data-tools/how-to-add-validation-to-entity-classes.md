---
title: '方法: エンティティ クラスに検証を追加'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6adcdd2d1bead72c1ff615731aa26be664f1f455
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-add-validation-to-entity-classes"></a>方法: エンティティ クラスに検証を追加
*検証*エンティティ クラスは、データ オブジェクトに入力された値がオブジェクトのスキーマ、およびアプリケーションに対して設定された規則に制約に準拠していることを確認するプロセスです。 基になるデータベースに更新を送信する前にデータを検証すると、エラーを減らすことができます。 アプリケーションとデータベースの間で生じる可能性のあるラウンド トリップの回数も減ります。

 [LINQ to Visual Studio での SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)を挿入、更新、中に実行し、完全なエンティティとも中に、および削除個々 の列の後にデザイナーで生成されたコードを拡張するユーザーを有効にする部分的なメソッドを提供変更します。

> [!NOTE]
>  このトピックでは、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]を使用してエンティティ クラスに検証を追加する基本的な手順を示します。 難しい可能性がある手順に従う一般的な特定のエンティティ クラスを参照しなくても、ため実際のデータを使用するチュートリアルが用意されています。

## <a name="adding-validation-for-changes-to-the-value-in-a-specific-column"></a>特定の列の値の変更に対する検証の追加
 この手順では、列の値の変更時にデータを検証する方法を示します。 検証はユーザー インターフェイスではなくクラス定義の内部で実行されるため、値によって検証が失敗する場合は例外がスローされます。 列の値を変更しようとするアプリケーションのコードには、エラー処理を実装してください。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-validate-data-during-a-columns-value-change"></a>列の値の変更時にデータを検証するには

1.  開くか新しい LINQ to SQL クラス ファイルを作成 (**.dbml**ファイル) で、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]です。 (ダブルクリックして、 **.dbml**ファイル**ソリューション エクスプ ローラー**)。

2.  検証を追加しクラスを右クリックし、O/R デザイナーで**コードの表示**です。

     コード エディターが開き、選択したエンティティ クラスの部分クラスが表示されます。

3.  部分クラスにカーソルを置きます。

4.  Visual Basic プロジェクトの場合は、次の操作を行います。

    1.  展開して、**メソッド名** ボックスの一覧です。

    2.  検索、 **OnCOLUMNNAMEChanging**検証を追加する列のメソッドです。

    3.  `OnCOLUMNNAMEChanging`メソッドが部分クラスに追加します。

    4.  次のコードを追加して、まず値が入力されたことを確認し、次に列に入力された値がアプリケーションで許容されることを確認します。 入力された値は `value` 引数に含まれています。そこで、これが有効な値であることを確認するロジックを追加します。

        ```vb
        If value.HasValue Then
            ' Add code to ensure that the value is acceptable.
            ' If value < 1 Then
            '    Throw New Exception("Invalid data!")
            ' End If
        End If
        ```

    C# プロジェクトの場合は、次の操作を行います。

    C# プロジェクトは、自動的にイベント ハンドラーを生成しない、ために IntelliSense を使えば、列変更部分メソッドを作成できます。 「`partial`」に続けてスペースを入力して、使用可能な部分メソッドの一覧にアクセスします。 検証を追加する列の列変更メソッドをクリックします。 次のコードには、列変更部分メソッドを選択するときに生成されるコードがようになります。

    ```csharp
    partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)
        {
           throw new System.NotImplementedException();
        }
    ```

## <a name="adding-validation-for-updates-to-an-entity-class"></a>エンティティ クラスへの更新の検証の追加
 変更時の値のチェックに加えて、エンティティ クラス全体の更新が試行されたときにデータを検証することもできます。 更新の試行時の検証では、ビジネス ルールにおける必要性に応じて複数の列の値を比較できます。 次の手順は、エンティティ クラス全体の更新が試行されたときに検証を行う方法を示しています。

> [!NOTE]
>  エンティティ クラス全体の更新に対する検証コードは、特定のエンティティ クラスの部分クラスではなく、部分 <xref:System.Data.Linq.DataContext> クラスで実行されます。

#### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>エンティティ クラスの更新時にデータを検証するには

1.  開くか新しい LINQ to SQL クラス ファイルを作成 (**.dbml**ファイル) で、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]です。 (ダブルクリックして、 **.dbml**ファイル**ソリューション エクスプ ローラー**)。

2.  O/R デザイナーの空の領域を右クリックし、をクリックして**コードの表示**です。

     コード エディターが開き、`DataContext` の部分クラスが表示されます。

3.  `DataContext` の部分クラスにカーソルを置きます。

4.  Visual Basic プロジェクトの場合は、次の操作を行います。

    1.  展開して、**メソッド名** ボックスの一覧です。

    2.  をクリックして**UpdateENTITYCLASSNAME**です。

    3.  `UpdateENTITYCLASSNAME`メソッドが部分クラスに追加します。

    4.  次のコードに示すように、`instance` 引数を使用して個々の列の値にアクセスします。

        ```vb
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then
            Dim ErrorMessage As String = "Invalid data!"
            Throw New Exception(ErrorMessage)
        End If
        ```

    C# プロジェクトの場合は、次の操作を行います。

    部分を作成する IntelliSense を使用して c# プロジェクトは、自動的にイベント ハンドラーを生成しない、ため`UpdateCLASSNAME`メソッドです。 「`partial`」に続けてスペースを入力して、使用可能な部分メソッドの一覧にアクセスします。 検証を追加するクラスの更新メソッドをクリックします。 次のコードを選択するときに生成されるコードのような`UpdateCLASSNAME`部分メソッド。

    ```csharp
    partial void UpdateCLASSNAME(CLASSNAME instance)
    {
        if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))
        {
            string ErrorMessage = "Invalid data!";
            throw new System.Exception(ErrorMessage);
        }
    }
    ```

## <a name="see-also"></a>関連項目

- [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [データの検証](../data-tools/validate-data-in-datasets.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)