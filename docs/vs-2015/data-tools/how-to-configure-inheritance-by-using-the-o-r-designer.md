---
title: '方法: O/R デザイナーを使用して継承を構成する |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7a6c8e4b2da87185c41157b8d03bd59b37188a43
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222692"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>方法: O/R デザイナーを使用して継承を構成します。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) では、一般にリレーショナル システムで実装されている単一テーブル継承の概念がサポートされます。 単一テーブル継承には、親情報と子情報の両方のフィールドを含む単一のデータベース テーブルがあります。 リレーショナル データでは、判別用の列に、レコードが属するクラスを決定する値が含まれています。  
  
 たとえば、会社に採用されたすべての人を含む Persons テーブルについて考えます。 従業員の人もいれば、管理者の人もいます。 Persons テーブルには、管理者を表す値 1 と従業員を表す値 2 がある `EmployeeType` という名前の列が含まれています。これが判別用の列です。 このシナリオでは、従業員のサブクラスを作成して、そのクラスには `EmployeeType` の値が 2 のレコードだけを入れます。 適用されない列を各クラスから削除することもできます。  
  
 継承を使用する (およびリレーショナル データに対応する) オブジェクト モデルの作成は、わかりにくい場合があります。 次の手順では、O/R デザイナーで継承を設定するために必要な手順を概説します。 既存のテーブルと列を参照しないで汎用的な手順に従うのは難しい場合があるので、データを使用したチュートリアルが用意されています。 詳細な手順を使用して継承を構成するため、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]を参照してください[チュートリアル: LINQ to SQL クラスを使用して単一テーブル継承 (O/R デザイナー) に作成](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)です。  
  
### <a name="to-create-inherited-data-classes"></a>継承されたデータ クラスを作成するには  
  
1.  開く、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]を追加して、 **LINQ to SQL クラス**項目を既存の Visual Basic または c# プロジェクト。  
  
2.  基本クラスとして使用するテーブルを [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]にドラッグします。  
  
3.  上にテーブルの 2 番目のコピーをドラッグして、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]し名前を変更します。 これは、派生クラス、つまりサブクラスです。  
  
4.  クリックして**継承**で、**オブジェクト リレーショナル デザイナー**のタブ、**ツールボックス**サブクラス (名前を変更したテーブル) をクリックして、基底クラスに接続します。  
  
    > [!NOTE]
    >  をクリックして、**継承**内の項目、**ツールボックス**とリリースのマウス ボタンを手順 3. で作成したクラスの 2 つ目のコピー をクリックして、手順 2. で作成した最初のクラスをクリックします。 継承線の矢印は最初のクラスを指します。  
  
5.  各クラスで、関連付けに使用されていない、表示する必要のないオブジェクト プロパティを削除します。 関連付けに使用するオブジェクトのプロパティを削除しようとした場合、エラーが表示されます:[プロパティ\<プロパティ名 > の関連付けに関与しているために削除できません\<関連付けの名前 >](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).  
  
    > [!NOTE]
    >  派生クラスは基本クラスで定義されているプロパティを継承するため、各クラスに同じ列を定義することはできません  (列はプロパティとして実装されます)。基本クラスのプロパティに [Inheritance Modifier] を設定することで、派生クラスでの列の作成が可能になります。 詳細については、次を参照してください。[ビルド内にありません: オーバーライドするプロパティとメソッド](http://msdn.microsoft.com/en-us/2167e8f5-1225-4b13-9ebd-02591ba90213)します。  
  
6.  [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]で継承線を選択します。  
  
7.  **プロパティ**ウィンドウで、設定、**識別子プロパティ**クラス内のレコードを区別するために使用される列名にします。  
  
8.  設定、 **Derived Class Discriminator Value**プロパティを継承した型として、レコードを指定するデータベース内の値。 (これは判別用の列に格納される値で、継承されたクラスを示すために使用されます)。  
  
9. 設定、**基本 Class Discriminator Value**プロパティを基本データ型として、レコードを指定する値。 (これは判別用の列に格納される値で、基本クラスを示すために使用されます)。  
  
10. 必要に応じて、設定することも、 **Inheritance Default**継承コードが定義されているいずれかと一致しない行を読み込むときに使用される継承階層内の型を指定するプロパティ。 つまり、レコードに値がある場合は、判別用の列に一致しないいずれかの値、 **Derived Class Discriminator Value**または**Base Class Discriminator Value**プロパティと、レコードとして指定された型に読み込まれます、 **Inheritance Default**します。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to Visual Studio での SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [チュートリアル: LINQ to SQL クラス (O/R デザイナー) を作成します。](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Visual Studio 2012 でのデータ アプリケーションの開発の新 PAVE します。](http://msdn.microsoft.com/en-us/3d50d68f-5f44-4915-842f-6d42fce793f1)   
 [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [チュートリアル: 単一テーブル継承 (O/R デザイナー) を使用して LINQ to SQL クラスを作成します。](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
 [ビルド内にありません: Visual Basic の継承](http://msdn.microsoft.com/en-us/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [継承](http://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea)

