---
title: '方法: ストアド プロシージャおよび関数 (O/R デザイナー) にマップされる DataContext メソッドの作成 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 62d250946e634627c16dbd3b56fce370c11e1f3f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538519"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>方法: ストアド プロシージャおよび関数 (O/R デザイナー) にマップされる DataContext メソッドの作成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: ストアド プロシージャおよび関数 (O/R デザイナー) にマップされる DataContext の作成メソッド](https://docs.microsoft.com/visualstudio/data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer)します。  
  
  
ストアド プロシージャおよび関数に追加できる、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]として<xref:System.Data.Linq.DataContext>メソッド。 メソッドを呼び出すと、必要なパラメーターを渡すこと、データベースでストアド プロシージャまたは関数を実行し、戻り値の型のデータを返します、<xref:System.Data.Linq.DataContext>メソッド。 詳細については<xref:System.Data.Linq.DataContext>メソッドを参照してください[DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)します。  
  
> [!NOTE]
>  ストアド プロシージャを使用して、エンティティ クラスからデータベースに変更が保存されたときに挿入、更新、および削除を実行する既定の [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] ランタイムの動作をオーバーライドすることもできます。 詳細については、次を参照してください。[方法: 更新、挿入、および削除 (O/r デザイナー) を実行するストアド プロシージャを割り当てる](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)します。  
  
## <a name="creating-datacontext-methods"></a>DataContext メソッドの作成  
 作成することができます<xref:System.Data.Linq.DataContext>メソッドをドラッグしてストアド プロシージャまたは関数から**サーバー エクスプ ローラー/データベース エクスプ ローラー**上に、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]します。  
  
> [!NOTE]
>  生成される <xref:System.Data.Linq.DataContext> メソッドの戻り値の型は、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]でストアド プロシージャまたは関数をドロップする場所によって異なります。 既存のエンティティ クラスに項目を直接ドロップすると、そのエンティティ クラスを戻り値の型とする <xref:System.Data.Linq.DataContext> メソッドが作成されます。 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]の空の領域に項目をドロップすると、自動生成された型を返す <xref:System.Data.Linq.DataContext> メソッドが作成されます。 戻り値の型を変更することができます、<xref:System.Data.Linq.DataContext>メソッド ペインに追加したメソッド。 検査または戻り値の型を変更する、<xref:System.Data.Linq.DataContext>メソッドを選択し、検査、**戻り値の型**プロパティ、**プロパティ**ウィンドウ。 詳細については、次を参照してください。[方法: DataContext メソッド (O/r デザイナー) の戻り値の型を変更する](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)します。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>自動生成された型を返す DataContext メソッドを作成するには  
  
1.  **サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、展開、 **Stored Procedures**を使用するデータベースのノード。  
  
2.  目的のストアド プロシージャを探し、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]の空の領域にドラッグします。  
  
     <xref:System.Data.Linq.DataContext>メソッドが自動的に生成された戻り値の型で作成され、**メソッド**ウィンドウ。  
  
#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>エンティティ クラスを戻り値の型とする DataContext メソッドを作成するには  
  
1.  **サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、展開、 **Stored Procedures**を使用するデータベースのノード。  
  
2.  目的のストアド プロシージャを探し、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]の既存のエンティティ クラスにドラッグします。  
  
     <xref:System.Data.Linq.DataContext>メソッドが、選択したエンティティ クラスの戻り値の型で作成され、**メソッド**ウィンドウ。  
  
> [!NOTE]
>  既存の戻り値の型を変更する方法について<xref:System.Data.Linq.DataContext>メソッドを参照してください[方法: DataContext メソッド (O/R デザイナー) の戻り値の型を変更する](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)します。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to Visual Studio での SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)   
 [チュートリアル: LINQ to SQL クラス (O/R デザイナー) を作成します。](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Visual Basic における LINQ の概要](http://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984)   
 [方法: C# で LINQ クエリを作成する](http://msdn.microsoft.com/library/45e47fcc-cfa1-4b72-b161-d038ae87bd23)

