---
title: '方法: エンティティ クラスへの検証の追加 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f512a330a1253f0db9b0f7e75de5f0a6ca52658d
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2018
ms.locfileid: "47593007"
---
# <a name="how-to-add-validation-to-entity-classes"></a>方法: エンティティ クラスに検証を追加
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: エンティティ クラスに検証を追加](https://docs.microsoft.com/visualstudio/data-tools/how-to-add-validation-to-entity-classes)します。  
  
  
*検証*エンティティ クラスは、データ オブジェクトに入力された値がオブジェクトのスキーマ、およびアプリケーションの設定された規則の制約に準拠することを確認するプロセス。 基になるデータベースに更新を送信する前にデータを検証すると、エラーを減らすことができます。 アプリケーションとデータベースの間で生じる可能性のあるラウンド トリップの回数も減ります。  
  
 [LINQ to Visual Studio での SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)挿入、更新、中に実行し、完全なエンティティとも中と後の個々 の列を削除します。 デザイナーで生成されたコードを拡張するユーザーを有効にする部分メソッドを提供します。変更します。  
  
> [!NOTE]
>  このトピックでは、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]を使用してエンティティ クラスに検証を追加する基本的な手順を示します。 特定のエンティティ クラスを参照しないでこれらの汎用的な手順をたどるが難しい場合があります、ため、実際のデータを使用するチュートリアルが用意されています。  
  
## <a name="adding-validation-for-changes-to-the-value-in-a-specific-column"></a>特定の列の値の変更に対する検証の追加  
 この手順では、列の値の変更時にデータを検証する方法を示します。 検証はユーザー インターフェイスではなくクラス定義の内部で実行されるため、値によって検証が失敗する場合は例外がスローされます。 列の値を変更しようとするアプリケーションのコードには、エラー処理を実装してください。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-validate-data-during-a-columns-value-change"></a>列の値の変更時にデータを検証するには  
  
1.  開くか、新しい LINQ to SQL クラス ファイルの作成 (**.dbml**ファイル) で、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]します。 (ダブルクリックして、 **.dbml**ファイル**ソリューション エクスプ ローラー**)。  
  
2.  O/R デザイナーをクリックして検証を追加するクラスを右クリックして**コードの表示**します。  
  
     コード エディターが開き、選択したエンティティ クラスの部分クラスが表示されます。  
  
3.  部分クラスにカーソルを置きます。  
  
4.  Visual Basic プロジェクトの場合は、次の操作を行います。  
  
    1.  展開、**メソッド名**一覧。  
  
    2.  検索、**で**_COLUMNNAME_**Changing**検証を追加する列のメソッド。  
  
    3.  `On` *COLUMNNAME* `Changing`メソッドが部分クラスに追加されます。  
  
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
  
    1.  C# プロジェクトでは、イベント ハンドラーの生成は自動的には行われないため、IntelliSense を使用して列変更部分メソッドを作成します。  
  
         「`partial`」に続けてスペースを入力して、使用可能な部分メソッドの一覧にアクセスします。 検証を追加する列の列変更メソッドをクリックします。 列変更部分メソッドを選択したときに生成されるコードは次のようになります。  
  
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
  
1.  開くか、新しい LINQ to SQL クラス ファイルの作成 (**.dbml**ファイル) で、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]します。 (ダブルクリックして、 **.dbml**ファイル**ソリューション エクスプ ローラー**)。  
  
2.  O/R デザイナーの空の領域を右クリックし、をクリックして**コードの表示**します。  
  
     コード エディターが開き、`DataContext` の部分クラスが表示されます。  
  
3.  `DataContext` の部分クラスにカーソルを置きます。  
  
4.  Visual Basic プロジェクトの場合は、次の操作を行います。  
  
    1.  展開、**メソッド名**一覧。  
  
    2.  クリックして**Update**_ENTITYCLASSNAME_します。  
  
    3.  `Update` *ENTITYCLASSNAME*メソッドが部分クラスに追加されます。  
  
    4.  次のコードに示すように、`instance` 引数を使用して個々の列の値にアクセスします。  
  
        ```vb  
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then  
            Dim ErrorMessage As String = "Invalid data!"  
            Throw New Exception(ErrorMessage)  
        End If  
        ```  
  
     C# プロジェクトの場合は、次の操作を行います。  
  
    1.  部分を作成する IntelliSense を使用して c# プロジェクトは、イベント ハンドラーが自動的に生成しないため、 `Update` *CLASSNAME*メソッド。  
  
    2.  「`partial`」に続けてスペースを入力して、使用可能な部分メソッドの一覧にアクセスします。 検証を追加するクラスの更新メソッドをクリックします。 次のコードを選択するときに生成されるコードのような`Update` *CLASSNAME*部分メソッド。  
  
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
 [LINQ to Visual Studio での SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [データの検証](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)

