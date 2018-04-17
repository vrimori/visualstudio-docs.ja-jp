---
title: 'チュートリアル: 単一テーブル継承 (O R デザイナー) を使用して LINQ to SQL クラスを作成する |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8a0c6702a965ae2733d2461cf30f5fd91f27dba3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>チュートリアル : 単一テーブル継承を使用した LINQ to SQL クラスの作成 (O/R デザイナー)
[LINQ to Visual Studio での SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)通常リレーショナル システムで実装されている単一テーブル継承をサポートしています。 このチュートリアルで提供される汎用的な手順、[する方法: O/R デザイナーを使用して継承を構成する](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)トピックによって実際のデータでの継承の使用をデモを提供し、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]です。  
  
 このチュートリアルでは次のタスクを行います。  
  
-   データベース テーブルを作成し、データを追加します。  
  
-   Windows フォーム アプリケーションを作成します。  
  
-   [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] ファイルをプロジェクトに追加します。  
  
-   新しいエンティティ クラスを作成します。  
  
-   継承を使用するようにエンティティ クラスを構成します。  
  
-   継承されたクラスをクエリします。  
  
-   Windows フォームにデータを表示します。  
  
## <a name="create-a-table-to-inherit-from"></a>継承するテーブルの作成  
 継承の動作を確認するには、小さな Person テーブルを作成し、それをベース クラスとして使用して、そのテーブルから継承する Employee オブジェクトを作成します。  
  
#### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>ベース テーブルを作成して継承の動作を確認するには  
  
1.  **サーバー エクスプ ローラー**/**データベース エクスプ ローラー**を右クリックし、**テーブル**ノードとクリック**新しいテーブルの追加**です。  
  
    > [!NOTE]
    >  Northwind データベースを使用することも、テーブルを追加できる他の任意のデータベースを使用することもできます。  
  
2.  テーブル デザイナーで、次の列をテーブルに追加します。  
  
    |列名|データ型|Null を許容|  
    |-----------------|---------------|-----------------|  
    |**ID**|**int**|**False**|  
    |**Type**|**int**|**True**|  
    |**FirstName**|**nvarchar(200)**|**False**|  
    |**LastName**|**nvarchar(200)**|**False**|  
    |**マネージャー**|**int**|**True**|  
  
3.  ID 列を主キーとして設定します。  
  
4.  テーブルを保存し、名前を付けます**Person**です。  
  
## <a name="add-data-to-the-table"></a>テーブルへのデータの追加  
 継承が正しく構成されていることを確認できるように、単一テーブル継承のテーブルの各クラスにデータを入力する必要があります。  
  
#### <a name="to-add-data-to-the-table"></a>テーブルにデータを追加するには  
  
1.  データ ビューでテーブルを開きます  (を右クリックし、 **Person**テーブルに**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**  をクリック**テーブル データの表示**)。  
  
2.  テーブルに次のデータをコピーします。 (コピーして、結果ウィンドウで、行全体を選択して、テーブルに貼り付けます。)  
  
    ||||||  
    |-|-|-|-|-|  
    |**ID**|**Type**|**FirstName**|**LastName**|**マネージャー**|  
    |**1**|**1**|**Anne**|**ウォーレス**|**NULL**|  
    |**2**|**1**|**Carlos**|**Grilo**|**NULL**|  
    |**3**|**1**|**Yael**|**Peled**|**NULL**|  
    |**4**|**2**|**Gatis**|**Ozolins**|**1**|  
    |**5**|**2**|**Andreas**|**Hauser**|**1**|  
    |**6**|**2**|**Tiffany**|**Phuvasate**|**1**|  
    |**7**|**2**|**Alexey**|**Orekhov**|**2**|  
    |**8**|**2**|**Michał**|**Poliszkiewicz**|**2**|  
    |**9**|**2**|**末尾**|**Yee**|**2**|  
    |**10**|**2**|**Fabricio**|**Noriega**|**3**|  
    |**11**|**2**|**加山**|**Martin**|**3**|  
    |**12**|**2**|**Ken**|**Kwok の追加**|**3**|  
  
## <a name="create-a-new-project"></a>新しいプロジェクトの作成  
 これでテーブルが作成されたので、新しいプロジェクトを作成して継承の構成を実際に行います。  
  
#### <a name="to-create-the-new-windows-forms-application"></a>新しい Windows フォーム アプリケーションを作成するには  
  
1. Visual Studio での**ファイル**メニューの **新規**、**プロジェクト.**.  
  
2. いずれかを展開**Visual c#**または**Visual Basic**左側のペインでを選択し、 **Windows クラシック デスクトップ**です。  

3. 中央のペインで、 **Windows フォーム アプリ**プロジェクトの種類。  

4. プロジェクトに名前を**InheritanceWalkthrough**を選択し**OK**です。 
  
     **InheritanceWalkthrough**プロジェクトが作成され、追加する**ソリューション エクスプ ローラー**です。  
  
## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>LINQ to SQL クラス ファイルをプロジェクトに追加します。  
  
#### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>LINQ to SQL ファイルをプロジェクトに追加するには  
  
1.  **[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。  
  
2.  クリックして、 **LINQ to SQL クラス**テンプレートをクリックして**追加**です。  
  
     プロジェクトに .dbml ファイルが追加され、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]が開きます。  
  
## <a name="create-the-inheritance-by-using-the-or-designer"></a>O/R デザイナーを使用した継承の作成  
 ドラッグして、継承を構成、**継承**オブジェクトから、**ツールボックス**デザイン サーフェイスにします。  
  
#### <a name="to-create-the-inheritance"></a>継承を作成するには  
  
1.  **サーバー エクスプ ローラー**/**データベース エクスプ ローラー**に移動し、 **Person**先ほど作成したテーブル。  
  
2.  ドラッグ、 **Person**上の表に、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]デザイン サーフェイスです。  
  
3.  1 秒あたりのドラッグ**人**にテーブル、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]し、名前に変更**従業員**です。  
  
4.  削除、 **Manager**プロパティから、 **Person**オブジェクト。  
  
5.  削除、**型**、 **ID**、 **FirstName**、および**LastName**プロパティから、**従業員**オブジェクト。 (つまり、以外のすべてのプロパティを削除**Manager**)。  
  
6.  **オブジェクト リレーショナル デザイナー**のタブ、**ツールボックス**、作成、**継承**間、 **Person**と**従業員**オブジェクト。 これを行うをクリックして、**継承**内の項目、**ツールボックス**マウス ボタンを離します。 次に、をクリックして、**従業員**オブジェクトし、 **Person**内のオブジェクト、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]です。 継承線の矢印が指す、 **Person**オブジェクト。  
  
7.  クリックして、**継承**デザイン サーフェイス上の行。  
  
8.  設定、**識別子プロパティ**プロパティを**型**です。  
  
9. 設定、 **Derived Class Discriminator Value**プロパティを**2**です。  
  
10. 設定、 **Base Class Discriminator Value**プロパティを**1**です。  
  
11. 設定、 **Inheritance Default**プロパティを**Person**です。  
  
12. プロジェクトをビルドします。  
  
## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>継承されたクラスのクエリおよびフォームへのデータの表示  
 オブジェクト モデル内の特定のクラスを照会するコードをフォームに追加します。  
  
#### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>LINQ クエリを作成し、フォームに結果を表示するには  
  
1.  ドラッグ、 **ListBox**を Form1 にします。  
  
2.  フォームをダブルクリックして、`Form1_Load` イベント ハンドラーを作成します。  
  
3.  `Form1_Load` イベント ハンドラーに次のコードを追加します。  
  
    ```vb  
    Dim dc As New DataClasses1DataContext  
    Dim results = From emp In dc.Persons _  
        Where TypeOf emp Is Employee _  
        Select emp  
  
    For Each Emp As Employee In results  
        ListBox1.Items.Add(Emp.LastName)  
    Next  
    ```  
  
    ```csharp  
    NorthwindDataContext dc = new DataClasses1DataContext();  
    var results = from emp in dc.Persons  
                  where emp is Employee  
                  select emp;  
  
    foreach(Employee Emp in results)  
    {  
        listBox1.Items.Add(Emp.LastName)  
    }  
    ```  
  
## <a name="test-the-application"></a>アプリケーションのテスト  
 アプリケーションを実行し、リスト ボックスに表示されているレコードがすべて従業員 ([Type] 列の値が 2 のレコード) であることを確認します。  
  
#### <a name="to-test-the-application"></a>アプリケーションをテストするには  
  
1.  F5 キーを押します。  
  
2.  [Type] 列の値が 2 のレコードのみが表示されていることを確認します。  
  
3.  フォームを閉じます  (上、**デバッグ** メニューのをクリックして**デバッグの停止**)。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to Visual Studio での SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [チュートリアル: LINQ to SQL クラス (O R デザイナー) を作成します。](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
 [方法: 更新、挿入、および削除 (O/R デザイナー) を実行するストアド プロシージャを割り当てる](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
 [方法: Visual Basic または C# でオブジェクト モデルを生成する](/dotnet/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp)