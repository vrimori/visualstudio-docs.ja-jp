---
title: "How to: Configure Inheritance by Using the O/R Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
caps.latest.revision: 4
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Configure Inheritance by Using the O/R Designer
[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\) では、一般にリレーショナル システムで実装されている単一テーブル継承の概念がサポートされます。単一テーブル継承には、親情報と子情報の両方のフィールドを含む単一のデータベース テーブルがあります。リレーショナル データでは、判別用の列に、レコードが属するクラスを決定する値が含まれています。  
  
 たとえば、会社に採用されたすべての人を含む Persons テーブルについて考えます。従業員の人もいれば、管理者の人もいます。Persons テーブルには、管理者を表す値 1 と従業員を表す値 2 がある `EmployeeType` という名前の列が含まれています。これが判別用の列です。このシナリオでは、従業員のサブクラスを作成して、そのクラスには `EmployeeType` の値が 2 のレコードだけを入れます。適用されない列を各クラスから削除することもできます。  
  
 継承を使用する \(およびリレーショナル データに対応する\) オブジェクト モデルの作成は、わかりにくい場合があります。次の手順では、O\/R デザイナーで継承を設定するために必要な手順を概説します。既存のテーブルと列を参照しないで汎用的な手順に従うのは難しい場合があるので、データを使用したチュートリアルが用意されています。[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]を使用して継承を構成する詳細な手順については、「[Walkthrough: Creating LINQ to SQL Classes by Using Single\-Table Inheritance \(O\/R Designer\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)」を参照してください。  
  
### 継承されたデータ クラスを作成するには  
  
1.  既存の Visual Basic プロジェクトまたは C\# プロジェクトに **\[LINQ to SQL クラス\]** 項目を追加して、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]を開きます。  
  
2.  基本クラスとして使用するテーブルを [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]にドラッグします。  
  
3.  テーブルの 2 つ目のコピーを [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]にドラッグし、名前を変更します。これは、派生クラス、つまりサブクラスです。  
  
4.  **ツールボックス**の **\[オブジェクト リレーショナル デザイナー\]** タブで **\[継承\]** をクリックし、サブクラス \(名前変更したテーブル\) をクリックして、基本クラスに接続します。  
  
    > [!NOTE]
    >  **ツールボックス**の **\[継承\]** 項目をクリックしてマウス ボタンを離し、手順 3. で作成したクラスの 2 番目のコピーをクリックしてから、手順 2. で作成した最初のクラスをクリックします。継承線の矢印は最初のクラスを指します。  
  
5.  各クラスで、関連付けに使用されていない、表示する必要のないオブジェクト プロパティを削除します。関連付けに使用されているオブジェクト プロパティを削除しようとすると、"[The property \<property name\> cannot be deleted because it is participating in the association \<association name\>](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md)" というエラーが表示されます。  
  
    > [!NOTE]
    >  派生クラスは基本クラスで定義されているプロパティを継承するため、各クラスに同じ列を定義することはできません \(列はプロパティとして実装されます\)。基本クラスのプロパティに \[Inheritance Modifier\] を設定することで、派生クラスでの列の作成が可能になります。詳細については、「[NOT IN BUILD: Overriding Properties and Methods](http://msdn.microsoft.com/ja-jp/2167e8f5-1225-4b13-9ebd-02591ba90213)」を参照してください。  
  
6.  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]で継承線を選択します。  
  
7.  **\[プロパティ\]** ウィンドウで、**\[Discriminator Property\]** を、クラス内のレコードを区別するために使用する列の名前に設定します。  
  
8.  **\[派生クラスの識別子の値\]** プロパティを、レコードが継承された型であることを示すデータベース内の値に設定します \(これは判別用の列に格納される値で、継承されたクラスを示すために使用されます\)。  
  
9. **\[基本クラスの識別子の値\]** プロパティを、レコードが基本型であることを示す値に設定します \(これは判別用の列に格納される値で、基本クラスを示すために使用されます\)。  
  
10. オプションとして、**\[Inheritance Default\]** プロパティを設定することもできます。これは、定義済みの継承コードと一致しない行を読み込むときに使用される継承階層の型を示します。つまり、あるレコードの判別用の列に、**\[派生クラスの識別子の値\]** プロパティにも **\[基本クラスの識別子の値\]** プロパティにも一致しない値が含まれている場合、そのレコードは **\[継承の既定値\]** として指定された型に読み込まれます。  
  
## 参照  
 [O\/R Designer Overview](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [PAVE What's New for Data Application Development in Visual Studio 2012](http://msdn.microsoft.com/ja-jp/3d50d68f-5f44-4915-842f-6d42fce793f1)   
 [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Walkthrough: Creating LINQ to SQL Classes by Using Single\-Table Inheritance \(O\/R Designer\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
 [NOT IN BUILD: Inheritance in Visual Basic](http://msdn.microsoft.com/ja-jp/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [継承](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)