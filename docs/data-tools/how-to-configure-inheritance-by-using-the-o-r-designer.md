---
title: '方法: O R デザイナーを使用して継承の構成 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d55d91fb7275b37a1fc233377955ce0f17742f63
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>方法: O/R デザイナーを使用して継承を構成します。
[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]) では、一般にリレーショナル システムで実装されている単一テーブル継承の概念がサポートされます。 単一テーブル継承には、親情報と子情報の両方のフィールドを含む単一のデータベース テーブルがあります。 リレーショナル データでは、判別用の列に、レコードが属するクラスを決定する値が含まれています。  
  
たとえば、会社に採用されたすべての人を含む Persons テーブルについて考えます。 従業員の人もいれば、管理者の人もいます。 Persons テーブルには、管理者を表す値 1 と従業員を表す値 2 がある `EmployeeType` という名前の列が含まれています。これが判別用の列です。 このシナリオでは、従業員のサブクラスを作成して、そのクラスには `EmployeeType` の値が 2 のレコードだけを入れます。 適用されない列を各クラスから削除することもできます。  
  
継承を使用する (およびリレーショナル データに対応する) オブジェクト モデルの作成は、わかりにくい場合があります。 次の手順では、O/R デザイナーで継承を設定するために必要な手順を概説します。 既存のテーブルと列を参照しないで汎用的な手順に従うのは難しい場合があるので、データを使用したチュートリアルが用意されています。 詳細な手順を使用して継承を構成するための[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]を参照してください[チュートリアル: を作成する LINQ to SQL クラスを使用して単一テーブル継承 (O/R デザイナー) によって](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)です。  
  
## <a name="to-create-inherited-data-classes"></a>継承されたデータ クラスを作成するには
  
1.  開く、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]追加することによって、 **LINQ to SQL クラス**項目を既存の Visual Basic または c# プロジェクト。  
  
2.  基本クラスとして使用するテーブルを [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]にドラッグします。  
  
3.  上にテーブルの 2 番目のコピーをドラッグして、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]その名前を変更します。 これは、派生クラス、つまりサブクラスです。  
  
4.  をクリックして**継承**で、**オブジェクト リレーショナル デザイナー**のタブ、**ツールボックス**サブクラス (名前を変更したテーブル) をクリックして、基本クラスに接続します。  
  
    > [!NOTE]
    >  クリックして、**継承**内の項目、**ツールボックス**とマウスのボタンを離します手順 2. で作成した最初のクラスをクリックして、手順 3. で作成したクラスの 2 つ目のコピー をクリックします。 継承線の矢印は最初のクラスを指します。  
  
5.  各クラスで、関連付けに使用されていない、表示する必要のないオブジェクト プロパティを削除します。 関連付けに使用するオブジェクト プロパティを削除しようとすると、エラーが表示されます:[プロパティ\<プロパティ名 > の関連付けに関与しているために、削除できません\<association 名 >](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).  
  
    > [!NOTE]
    >  派生クラスは基本クラスで定義されているプロパティを継承するため、各クラスに同じ列を定義することはできません  (列はプロパティとして実装されます)。基本クラスのプロパティに [Inheritance Modifier] を設定することで、派生クラスでの列の作成が可能になります。 詳細については、次を参照してください。[継承の基礎 (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)です。  
  
6.  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]で継承線を選択します。  
  
7.  **プロパティ**ウィンドウで、設定、**識別子プロパティ**クラス内のレコードを区別するために使用される列名にします。  
  
8.  設定、 **Derived Class Discriminator Value**プロパティが継承された型のレコードを指定するデータベース内の値にします。 (これは判別用の列に格納される値で、継承されたクラスを示すために使用されます)。  
  
9. 設定、**基本 Class Discriminator Value**プロパティを基本型として、レコードを指定する値。 (これは判別用の列に格納される値で、基本クラスを示すために使用されます)。  
  
10. 必要に応じて、設定することも、 **Inheritance Default**継承コードが定義されているいずれかと一致しない行を読み込むときに使用される継承階層内の型を指定するプロパティです。 つまり、レコードに値がある場合は、判別用の列と一致しません いずれかの値、 **Derived Class Discriminator Value**または**Base Class Discriminator Value**プロパティ、レコードとして指定された型に読み込まれます、 **Inheritance Default**です。  
  
## <a name="see-also"></a>関連項目
[LINQ to Visual Studio での SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[チュートリアル: LINQ to SQL クラス (O R デザイナー) を作成します。](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
[Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)   
[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
[チュートリアル: 単一テーブル継承 (O/R デザイナー) を使用して LINQ to SQL クラスを作成します。](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
[継承の基礎 (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)  
[継承](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)