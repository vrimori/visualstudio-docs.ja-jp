---
title: '方法: O/R デザイナーを使用して継承を構成する'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 99f353da4b6269ebf9fac425a12dfce5b5917df6
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "53923758"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>方法: O/R デザイナーを使用して継承を構成する
**オブジェクト リレーショナル デザイナー** (**O/R デザイナー**) リレーショナル システムに実装されている多くの場合は、単一テーブル継承の概念をサポートしています。 単一テーブル継承には、親情報と子情報の両方のフィールドを含む単一のデータベース テーブルがあります。 リレーショナル データでは、判別用の列に、レコードが属するクラスを決定する値が含まれています。

たとえば、`Persons`企業で採用されているすべてのユーザーを含むテーブル。 従業員の人もいれば、管理者の人もいます。 `Persons`テーブルには、という名前の列が含まれています。`EmployeeType`従業員のマネージャーと 2 の値の 1 の値を持つ; 識別子の列になります。 このシナリオでは、従業員のサブクラスを作成して、そのクラスには `EmployeeType` の値が 2 のレコードだけを入れます。 適用されない列を各クラスから削除することもできます。

継承を使用する (およびリレーショナル データに対応する) オブジェクト モデルの作成は、わかりにくい場合があります。 次の手順では、**O/R デザイナー**で継承を設定するために必要な手順を概説します。 既存のテーブルと列を参照しないで汎用的な手順を次にくい可能性、データを使用するチュートリアルが提供されるようにします。 詳細な手順を使用して継承を構成するため、 **O/R デザイナー**を参照してください[チュートリアル: LINQ to SQL を作成するクラスの単一テーブル継承 (O/R デザイナー) を使用して](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)します。

## <a name="to-create-inherited-data-classes"></a>継承されたデータ クラスを作成するには

1.  開く、 **O/R デザイナー**を追加して、 **LINQ to SQL クラス**項目を既存の Visual Basic または c# プロジェクト。

2.  上に基本クラスとして使用するテーブルをドラッグして、 **O/R デザイナー**します。

3.  上にテーブルの 2 番目のコピーをドラッグして、 **O/R デザイナー**し名前を変更します。 これは、派生クラス、つまりサブクラスです。

4.  **ツールボックス**の **[オブジェクト リレーショナル デザイナー]** タブで **[継承]** をクリックし、サブクラス (名前を変更したテーブル) をクリックして、基本クラスに接続します。

    > [!NOTE]
    >  **ツールボックス**の **[継承]** 項目をクリックしてマウス ボタンを放し、手順 3 で作成したクラスの 2 番目のコピーをクリックしてから、手順 2 で作成した最初のクラスをクリックします。 継承線の矢印は、最初のクラスを指します。

5.  各クラスで、関連付けに使用されていない、表示する必要のないオブジェクト プロパティを削除します。 関連付けに使用するオブジェクトのプロパティを削除しようとした場合、エラーが表示されます。プロパティ [プロパティ名\< は関連付け \<関連付けの名前](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md) に関与しているため、削除できません

    > [!NOTE]
    >  派生クラスは基本クラスで定義されているプロパティを継承するため、各クラスに同じ列を定義することはできません  (列はプロパティとして実装されます)。基本クラスのプロパティに継承修飾子を設定することで、派生クラスでの列の作成が可能になります。 詳細については、次を参照してください。[継承の基本 (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)します。

6.  継承線を選択して、 **O/R デザイナー**します。

7.  **プロパティ**ウィンドウで、設定、**識別子プロパティ**クラス内のレコードを区別する、列名にします。

8.  **[派生クラスの識別子の値]** プロパティに、レコードが継承された型であることを示すデータベース内の値を設定します。 (これは、識別子の列に格納され、継承されたクラスを指定するために使用する値です)。

9. **[基本クラスの識別子の値]** プロパティに、レコードが基本型であることを示す値を設定します。 (これは、識別子の列に格納され、基本クラスを指定するために使用する値です)。

10. オプションとして、**[継承の既定値]** プロパティを設定することもできます。これは、定義済みの継承コードと一致しない行を読み込むときに使用される継承階層の型を示します。 つまり、レコードに値がある場合は、判別用の列に一致しないいずれかの値、 **Derived Class Discriminator Value**または**Base Class Discriminator Value**プロパティと、レコードとして指定された型に読み込み、 **Inheritance Default**します。

## <a name="see-also"></a>関連項目

- [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [チュートリアル: LINQ to SQL クラス (O/R デザイナー) を作成](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [チュートリアル: 単一テーブル継承を使用した LINQ to SQL クラスの作成 (O/R デザイナー)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [継承の基本 (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [継承](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)