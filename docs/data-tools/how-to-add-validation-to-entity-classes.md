---
title: "How to: Add Validation to Entity Classes | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Add Validation to Entity Classes
エンティティ クラスの*検証*とは、データ オブジェクトに入力された値が、アプリケーションに対して設定された規則に従っていること、およびオブジェクトのスキーマ内の制約に従っていることを確認するプロセスです。基になるデータベースに更新を送信する前にデータを検証すると、エラーを減らすことができます。アプリケーションとデータベースの間で生じる可能性のあるラウンド トリップの回数も減ります。  
  
 [Object Relational Designer \(O\/R Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md) では、部分メソッドがサポートされており、これを使用することで、完全なエンティティの挿入、更新、および削除の処理中や、個々の列の変更中および変更後に実行される、デザイナーで生成されたコードをユーザーが拡張できます。  
  
> [!NOTE]
>  このトピックでは、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]を使用してエンティティ クラスに検証を追加する基本的な手順を示します。特定のエンティティ クラスを参照しないでこれらの汎用的な手順に従うのは難しい可能性があるため、実際のデータを使用するチュートリアルが用意されています。[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]を使用して検証を構成する詳細な手順については、「[Walkthrough: Adding Validation to Entity Classes](../Topic/Walkthrough:%20Adding%20Validation%20to%20Entity%20Classes.md)」を参照してください。  
  
## 特定の列の値の変更に対する検証の追加  
 この手順では、列の値の変更時にデータを検証する方法を示します。検証はユーザー インターフェイスではなくクラス定義の内部で実行されるため、値によって検証が失敗する場合は例外がスローされます。列の値を変更しようとするアプリケーションのコードには、エラー処理を実装してください。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### 列の値の変更時にデータを検証するには  
  
1.  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]で新しい LINQ to SQL クラス ファイル \(**.dbml** ファイル\) を開くか、新しく作成します \(**ソリューション エクスプローラー**で **.dbml** ファイルをダブルクリックします\)。  
  
2.  O\/R デザイナーで、検証を追加するクラスを右クリックし、**\[コードの表示\]** をクリックします。  
  
     コード エディターが開き、選択したエンティティ クラスの部分クラスが表示されます。  
  
3.  部分クラスにカーソルを置きます。  
  
4.  Visual Basic プロジェクトの場合は、次の操作を行います。  
  
    1.  **\[メソッド名\]** の一覧を展開します。  
  
    2.  検証を追加する列の **On***COLUMNNAME***Changing** メソッドを見つけます。  
  
    3.  `On` *COLUMNNAME* `Changing` メソッドが部分クラスに追加されます。  
  
    4.  次のコードを追加して、まず値が入力されたことを確認し、次に列に入力された値がアプリケーションで許容されることを確認します。入力された値は `value` 引数に含まれています。そこで、これが有効な値であることを確認するロジックを追加します。  
  
        ```vb#  
        If value.HasValue Then  
            ' Add code to ensure that the value is acceptable.  
            ' If value < 1 Then  
            '    Throw New Exception("Invalid data!")  
            ' End If  
        End If  
        ```  
  
     C\# プロジェクトの場合は、次の操作を行います。  
  
    1.  C\# プロジェクトでは、イベント ハンドラーの生成は自動的には行われないため、IntelliSense を使用して列変更部分メソッドを作成します。  
  
         「`partial`」に続けてスペースを入力して、使用可能な部分メソッドの一覧にアクセスします。検証を追加する列の列変更メソッドをクリックします。列変更部分メソッドを選択したときに生成されるコードは次のようになります。  
  
        ```c#  
        partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)  
            {  
               throw new System.NotImplementedException();  
            }  
  
        ```  
  
## エンティティ クラスの更新に対する検証の追加  
 変更時の値のチェックに加えて、エンティティ クラス全体の更新が試行されたときにデータを検証することもできます。更新の試行時の検証では、ビジネス ルールにおける必要性に応じて複数の列の値を比較できます。次の手順は、エンティティ クラス全体の更新が試行されたときに検証を行う方法を示しています。  
  
> [!NOTE]
>  エンティティ クラス全体の更新に対する検証コードは、特定のエンティティ クラスの部分クラスではなく、部分 <xref:System.Data.Linq.DataContext> クラスで実行されます。  
  
#### エンティティ クラスの更新時にデータを検証するには  
  
1.  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]で LINQ to SQL クラス ファイル \(**.dbml** ファイル\) を開くか、新しく作成します \(**ソリューション エクスプローラー**で **.dbml** ファイルをダブルクリックします\)。  
  
2.  O\/R デザイナーで空の領域を右クリックし、**\[コードの表示\]** をクリックします。  
  
     コード エディターが開き、`DataContext` の部分クラスが表示されます。  
  
3.  `DataContext` の部分クラスにカーソルを置きます。  
  
4.  Visual Basic プロジェクトの場合は、次の操作を行います。  
  
    1.  **\[メソッド名\]** の一覧を展開します。  
  
    2.  **\[更新\]** *ENTITYCLASSNAME* をクリックします。  
  
    3.  `Update` *ENTITYCLASSNAME* メソッドが部分クラスに追加されます。  
  
    4.  次のコードに示すように、`instance` 引数を使用して個々の列の値にアクセスします。  
  
        ```vb#  
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then  
            Dim ErrorMessage As String = "Invalid data!"  
            Throw New Exception(ErrorMessage)  
        End If  
        ```  
  
     C\# プロジェクトの場合は、次の操作を行います。  
  
    1.  C\# プロジェクトでは、イベント ハンドラーの生成は自動的には行われないため、IntelliSense を使用して部分 `Update`*CLASSNAME* メソッドを作成します。  
  
    2.  「`partial`」に続けてスペースを入力して、使用可能な部分メソッドの一覧にアクセスします。検証を追加するクラスの更新メソッドをクリックします。`Update`*CLASSNAME* 部分メソッドを選択したときに生成されるコードは次のようになります。  
  
        ```c#  
        partial void UpdateCLASSNAME(CLASSNAME instance)  
        {  
            if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))  
            {  
                string ErrorMessage = "Invalid data!";  
                throw new System.Exception(ErrorMessage);  
            }  
        }  
        ```  
  
## 参照  
 [Object Relational Designer \(O\/R Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [データの検証](../Topic/Validating%20Data.md)