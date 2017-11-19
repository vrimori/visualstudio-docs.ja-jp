---
title: "方法: ストアド プロシージャおよび関数 (O R デザイナー) にマップされる DataContext メソッドを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: a162c9cb7cf7febf6e3b6e95e927a31b6591b027
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>方法: ストアド プロシージャおよび関数 (O/R デザイナー) にマップされる DataContext メソッドの作成
ストアド プロシージャおよび関数を追加することができます、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]として<xref:System.Data.Linq.DataContext>メソッドです。 データベースでストアド プロシージャまたは関数が実行メソッドを呼び出すと、必要なパラメーターを渡すこと、および戻り値の型のデータを返します、<xref:System.Data.Linq.DataContext>メソッドです。 詳細については<xref:System.Data.Linq.DataContext>メソッドを参照してください[DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)です。  
  
> [!NOTE]
>  ストアド プロシージャを使用して、エンティティ クラスからデータベースに変更が保存されたときに挿入、更新、および削除を実行する既定の [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] ランタイムの動作をオーバーライドすることもできます。 詳細については、次を参照してください。[する方法: 更新、挿入、および削除 (O/r デザイナー) を実行するストアド プロシージャを割り当てる](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)です。  
  
## <a name="creating-datacontext-methods"></a>DataContext メソッドの作成  
 作成することができます<xref:System.Data.Linq.DataContext>メソッドをドラッグしてストアド プロシージャまたは関数から**サーバー エクスプ ローラー/データベース エクスプ ローラー**上に、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]です。  
  
> [!NOTE]
>  生成される <xref:System.Data.Linq.DataContext> メソッドの戻り値の型は、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]でストアド プロシージャまたは関数をドロップする場所によって異なります。 既存のエンティティ クラスに項目を直接ドロップすると、そのエンティティ クラスを戻り値の型とする <xref:System.Data.Linq.DataContext> メソッドが作成されます。 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]の空の領域に項目をドロップすると、自動生成された型を返す <xref:System.Data.Linq.DataContext> メソッドが作成されます。 戻り値の型を変更することができます、<xref:System.Data.Linq.DataContext>メソッド ペインに追加した後のメソッドです。 検査または戻り値の型を変更する、<xref:System.Data.Linq.DataContext>メソッドを選択し、**戻り値の型**プロパティに、**プロパティ**ウィンドウです。 詳細については、次を参照してください。[する方法: DataContext メソッド (O/r デザイナー) の戻り値の型を変更する](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)です。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>自動生成された型を返す DataContext メソッドを作成するには  
  
1.  **サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、展開、 **Stored Procedures**で作業中のデータベースのノードです。  
  
2.  目的のストアド プロシージャを探し、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]の空の領域にドラッグします。  
  
     <xref:System.Data.Linq.DataContext>メソッドが自動的に生成された戻り値の型が作成されに表示されます、**メソッド**ウィンドウです。  
  
#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>エンティティ クラスを戻り値の型とする DataContext メソッドを作成するには  
  
1.  **サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、展開、 **Stored Procedures**で作業中のデータベースのノードです。  
  
2.  目的のストアド プロシージャを探し、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]の既存のエンティティ クラスにドラッグします。  
  
     <xref:System.Data.Linq.DataContext>メソッドは、選択したエンティティ クラスの戻り値の型が作成されに表示されます、**メソッド**ウィンドウです。  
  
> [!NOTE]
>  既存の戻り値の型を変更する方法について<xref:System.Data.Linq.DataContext>メソッドを参照してください[する方法: DataContext メソッド (O/R デザイナー) の戻り値の型を変更する](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)です。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to Visual Studio での SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)   
 [チュートリアル: LINQ to SQL クラスを作成します。](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
 [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
 [Visual Basic における LINQ の概要](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [方法: C# で LINQ クエリを作成する](http://msdn.microsoft.com/Library/45e47fcc-cfa1-4b72-b161-d038ae87bd23)