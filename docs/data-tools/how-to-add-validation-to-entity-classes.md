---
title: '方法: エンティティ クラスに検証を追加する'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: a9e73fe476dbe323289e7ebe90508aec695b6bd2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53942555"
---
# <a name="how-to-add-validation-to-entity-classes"></a>方法: エンティティ クラスに検証を追加する
エンティティ クラスの "*検証*" とは、データ オブジェクトに入力された値が、アプリケーションに対して設定された規則に従っていること、およびオブジェクトのスキーマ内の制約に従っていることを確認するプロセスです。 基になるデータベースに更新を送信する前にデータを検証すると、エラーを減らすことができます。 アプリケーションとデータベースの間で生じる可能性のあるラウンド トリップの回数も減ります。

 [Visual Studio での LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)挿入、更新、中に実行し、完全なエンティティとも中と後の個々 の列を削除します。 デザイナーで生成されたコードを拡張するユーザーを有効にする部分メソッドを提供します。変更します。

> [!NOTE]
>  このトピックを使用してエンティティ クラスに検証を追加するための基本的な手順は、 **O/R デザイナー**します。 特定のエンティティ クラスを参照しないでこれらの汎用的な手順をたどるが難しい場合があります、ため、実際のデータを使用するチュートリアルが提供されます。

## <a name="add-validation-for-changes-to-the-value-in-a-specific-column"></a>特定の列の値に変更の検証を追加します。
 この手順では、列の値の変更時にデータを検証する方法を示します。 検証はユーザー インターフェイスではなくクラス定義の内部で実行されるため、値によって検証が失敗する場合は例外がスローされます。 列の値を変更しようとするアプリケーションのコードには、エラー処理を実装してください。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-validate-data-during-a-columns-value-change"></a>列の値の変更時にデータを検証するには

1.  開くか、新しい LINQ to SQL クラス ファイルの作成 (**.dbml**ファイル) で、 **O/R デザイナー**します。 (**ソリューション エクスプローラー**で **.dbml** ファイルをダブルクリックします。)

2.  **O/R デザイナー**で、検証を追加するクラスを右クリックして、**[コードの表示]** をクリックします。

     コード エディターが開き、選択したエンティティ クラスの部分クラスが表示されます。

3.  部分クラスにカーソルを置きます。

4.  Visual Basic プロジェクトの場合は、次の操作を行います。

    1.  **[メソッド名]** の一覧を展開します。

    2.  検証を追加する列の **OnCOLUMNNAMEChanging** メソッドを見つけます。

    3.  `OnCOLUMNNAMEChanging` メソッドが部分クラスに追加されます。

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

    C# プロジェクトはイベント ハンドラーが自動的に生成しないため、IntelliSense を使用して列変更部分メソッドを作成することができます。 「`partial`」に続けてスペースを入力して、使用可能な部分メソッドの一覧にアクセスします。 検証を追加する列の列変更メソッドをクリックします。 次のコードでは、コード列変更部分メソッドを選択するときに生成されるようになります。

    ```csharp
    partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)
        {
           throw new System.NotImplementedException();
        }
    ```

## <a name="add-validation-for-updates-to-an-entity-class"></a>エンティティ クラスへの更新の検証を追加します。
 変更時の値のチェックに加えて、エンティティ クラス全体の更新が試行されたときにデータを検証することもできます。 更新の試行時の検証では、ビジネス ルールにおける必要性に応じて複数の列の値を比較できます。 次の手順は、エンティティ クラス全体の更新が試行されたときに検証を行う方法を示しています。

> [!NOTE]
>  エンティティ クラス全体の更新に対する検証コードは、特定のエンティティ クラスの部分クラスではなく、部分 <xref:System.Data.Linq.DataContext> クラスで実行されます。

### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>エンティティ クラスの更新時にデータを検証するには

1.  開くか、新しい LINQ to SQL クラス ファイルの作成 (**.dbml**ファイル) で、 **O/R デザイナー**します。 (**ソリューション エクスプローラー**で **.dbml** ファイルをダブルクリックします。)

2.  **O/R デザイナー**で空の領域を右クリックし、**[コードの表示]** をクリックします。

     コード エディターが開き、`DataContext` の部分クラスが表示されます。

3.  `DataContext` の部分クラスにカーソルを置きます。

4.  Visual Basic プロジェクトの場合は、次の操作を行います。

    1.  **[メソッド名]** の一覧を展開します。

    2.  **[UpdateENTITYCLASSNAME]** をクリックします。

    3.  `UpdateENTITYCLASSNAME` メソッドが部分クラスに追加されます。

    4.  次のコードに示すように、`instance` 引数を使用して個々の列の値にアクセスします。

        ```vb
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then
            Dim ErrorMessage As String = "Invalid data!"
            Throw New Exception(ErrorMessage)
        End If
        ```

    C# プロジェクトの場合は、次の操作を行います。

    部分を作成する IntelliSense を使用して c# プロジェクトはイベント ハンドラーが自動的に生成しないため、`UpdateCLASSNAME`メソッド。 「`partial`」に続けてスペースを入力して、使用可能な部分メソッドの一覧にアクセスします。 検証を追加するクラスの update メソッドをクリックします。 次のコードを選択するときに生成されるコードと似ています、`UpdateCLASSNAME`部分メソッド。

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