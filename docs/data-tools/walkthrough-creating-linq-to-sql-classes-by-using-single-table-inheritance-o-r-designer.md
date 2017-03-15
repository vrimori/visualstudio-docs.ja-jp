---
title: "Walkthrough: Creating LINQ to SQL Classes by Using Single-Table Inheritance (O/R Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: 4
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Walkthrough: Creating LINQ to SQL Classes by Using Single-Table Inheritance (O/R Designer)
[Object Relational Designer \(O\/R Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md) では、一般にリレーショナル システムに実装されている単一テーブル継承がサポートされます。このチュートリアルでは、「[How to: Configure Inheritance by Using the O\/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)」のトピックで示した汎用的な手順を拡張し、実際のデータを使用して [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]での継承の使用方法を示します。  
  
 このチュートリアルでは次のタスクを行います。  
  
-   データベース テーブルを作成し、データを追加します。  
  
-   Windows フォーム アプリケーションを作成します。  
  
-   [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] ファイルをプロジェクトに追加します。  
  
-   新しいエンティティ クラスを作成します。  
  
-   継承を使用するようにエンティティ クラスを構成します。  
  
-   継承されたクラスをクエリします。  
  
-   Windows フォームにデータを表示します。  
  
## 継承するテーブルの作成  
 継承の動作を確認するには、小さな Person テーブルを作成し、それをベース クラスとして使用して、そのテーブルから継承する Employee オブジェクトを作成します。  
  
#### ベース テーブルを作成して継承の動作を確認するには  
  
1.  **サーバー エクスプローラー**または**データベース エクスプローラー**で、**\[テーブル\]** ノードを右クリックし、**\[新しいテーブルの追加\]** をクリックします。  
  
    > [!NOTE]
    >  Northwind データベースを使用することも、テーブルを追加できる他の任意のデータベースを使用することもできます。  
  
2.  テーブル デザイナーで、次の列をテーブルに追加します。  
  
    |列名|データ型|Null を許容|  
    |--------|----------|--------------|  
    |ID|int|False|  
    |型|int|True|  
    |FirstName|nvarchar\(200\)|False|  
    |LastName|nvarchar\(200\)|False|  
    |Manager|int|True|  
  
3.  ID 列を主キーとして設定します。  
  
4.  テーブルを Person という名前で保存します。  
  
## テーブルへのデータの追加  
 継承が正しく構成されていることを確認できるように、単一テーブル継承のテーブルの各クラスにデータを入力する必要があります。  
  
#### テーブルにデータを追加するには  
  
1.  データ ビューでテーブルを開きます \(**サーバー エクスプローラー**または**データベース エクスプローラー**で **Person** テーブルを右クリックし、**\[テーブル データの表示\]** をクリックします\)。  
  
2.  テーブルに次のデータをコピーします \(コピーしてから、[Results Pane](http://msdn.microsoft.com/ja-jp/3c712f20-7c9f-4021-b1ac-fdc6f534c95a)で行全体を選択してテーブルに貼り付けることができます\)。  
  
    ||||||  
    |-|-|-|-|-|  
    |ID|型|FirstName|LastName|Manager|  
    |1|1|Anne|Wallace|NULL|  
    |2|1|Carlos|Grilo|NULL|  
    |3|1|Yael|Peled|NULL|  
    |4|2|Gatis|Ozolins|1|  
    |5|2|Andreas|Hauser|1|  
    |6|2|Tiffany|Phuvasate|1|  
    |7|2|Alexey|Orekhov|2|  
    |8|2|Michał|Poliszkiewicz|2|  
    |9|2|Tai|Yee|2|  
    |10|2|Fabricio|Noriega|3|  
    |11|2|Mindy|Martin|3|  
    |12|2|Ken|Kwok|3|  
  
## 新しいプロジェクトの作成  
 これでテーブルが作成されたので、新しいプロジェクトを作成して継承の構成を実際に行います。  
  
#### 新しい Windows アプリケーションを作成するには  
  
1.  **\[ファイル\]** メニューで新しいプロジェクトを作成します。  
  
2.  プロジェクトに「InheritanceWalkthrough」という名前を付けます。  
  
    > [!NOTE]
    >  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]は Visual Basic プロジェクトと C\# プロジェクトでサポートされています。新しいプロジェクトはこれらの言語のどちらかで作成してください。  
  
3.  **\[Windows フォーム アプリケーション\]** テンプレートをクリックし、**\[OK\]** をクリックします。詳細については、「[クライアント アプリケーション](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)」を参照してください。  
  
4.  InheritanceWalkthrough プロジェクトが作成されて**ソリューション エクスプローラー**に追加されます。  
  
## LINQ to SQL クラス ファイルをプロジェクトに追加します。  
  
#### LINQ to SQL ファイルをプロジェクトに追加するには  
  
1.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
2.  **LINQ to SQL クラス** テンプレートをクリックし、**\[追加\]** をクリックします。  
  
     .dbml ファイルがプロジェクトに追加され、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]が開きます。  
  
## O\/R デザイナーを使用した継承の作成  
 **ツールボックス**からデザイン サーフェイスに**継承**オブジェクトをドラッグして、継承を構成します。  
  
#### 継承を作成するには  
  
1.  **サーバー エクスプローラー**または**データベース エクスプローラー**で、以前に作成した **Person** テーブルに移動します。  
  
2.  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]のデザイン サーフェイスに **Person** テーブルをドラッグします。  
  
3.  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]に 2 つ目の **Person** テーブルをドラッグし、名前を「Employee」に変更します。  
  
4.  **Person** オブジェクトから **Manager** プロパティを削除します。  
  
5.  **Employee** オブジェクトから、**Type**、**ID**、**FirstName**、および **LastName** の各プロパティを削除します。つまり、**Manager** 以外のすべてのプロパティを削除します。  
  
6.  **ツールボックス**の **\[オブジェクト リレーショナル デザイナー\]** タブで、**Person** オブジェクトと **Employee** オブジェクトの間に**継承**を作成します。これを作成するには、**ツールボックス**の **\[継承\]** 項目をクリックします。次に、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]で **Employee** オブジェクトをクリックし、**Person** オブジェクトをクリックします。継承線の矢印は **Person** オブジェクトを指します。  
  
7.  デザイン サーフェイスで**継承**線をクリックします。  
  
8.  **"識別子のプロパティ"** プロパティを **Type** に設定します。  
  
9. **Derived Class Discriminator Value** プロパティを **2** に設定します。  
  
10. **基本クラスの識別子の値**プロパティを **1** に設定します。  
  
11. **Inheritance Default** プロパティを **Person** に設定します。  
  
12. プロジェクトをビルドします。  
  
## 継承されたクラスのクエリおよびフォームへのデータの表示  
 オブジェクト モデル内の特定のクラスを照会するコードをフォームに追加します。  
  
#### LINQ クエリを作成し、フォームに結果を表示するには  
  
1.  Form1 に **ListBox** をドラッグします。  
  
2.  フォームをダブルクリックして、`Form1_Load` イベント ハンドラーを作成します。  
  
3.  `Form1_Load` イベント ハンドラーに次のコードを追加します。  
  
    ```vb#  
    Dim dc As New DataClasses1DataContext  
    Dim results = From emp In dc.Persons _  
        Where TypeOf emp Is Employee _  
        Select emp  
  
    For Each Emp As Employee In results  
        ListBox1.Items.Add(Emp.LastName)  
    Next  
    ```  
  
    ```c#  
    NorthwindDataContext dc = new DataClasses1DataContext();  
    var results = from emp in dc.Persons  
                  where emp is Employee  
                  select emp;  
  
    foreach(Employee Emp in results)  
    {  
        listBox1.Items.Add(Emp.LastName)  
    }  
    ```  
  
## アプリケーションのテスト  
 アプリケーションを実行し、リスト ボックスに表示されているレコードがすべて従業員 \(\[Type\] 列の値が 2 のレコード\) であることを確認します。  
  
#### アプリケーションをテストするには  
  
1.  F5 キーを押します。  
  
2.  \[Type\] 列の値が 2 のレコードのみが表示されていることを確認します。  
  
3.  フォームを閉じます \(**\[デバッグ\]** メニューの **\[デバッグの停止\]** をクリックします\)。  
  
## 参照  
 [O\/R Designer Overview](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [How to: Add LINQ to SQL Classes to a Project \(O\/R Designer\)](../Topic/How%20to:%20Add%20LINQ%20to%20SQL%20Classes%20to%20a%20Project%20\(O-R%20Designer\).md)   
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [How to: Assign Stored Procedures to Perform Updates, Inserts, and Deletes \(O\/R Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [How to: Generate the Object Model in Visual Basic or C\#](../Topic/How%20to:%20Generate%20the%20Object%20Model%20in%20Visual%20Basic%20or%20C%23.md)