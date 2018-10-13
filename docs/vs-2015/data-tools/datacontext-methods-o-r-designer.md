---
title: DataContext メソッド (O/R デザイナー) |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2ccf32d4af0bd16032c4601b054be6407071753f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49200461"
---
# <a name="datacontext-methods-or-designer"></a>DataContext メソッド (O/R デザイナー)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
DataContext] (assetId:///T:System.Data.Linq.DataContext?qualifyHint=False & autoUpgrade = True) メソッド (のコンテキストで、 [LINQ to SQL ツール Visual Studio で](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) のメソッドは、<xref:System.Data.Linq.DataContext>ストアドを実行しているクラスプロシージャと、データベース内の関数。  
  
 <xref:System.Data.Linq.DataContext> クラスは、SQL Server データベースと、そのデータベースにマップされる [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] エンティティ クラスの間のパイプ役として機能する [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] クラスです。 <xref:System.Data.Linq.DataContext>クラスには、接続文字列の情報と、データベースに接続すると、データベース内のデータを操作するメソッドが含まれています。 既定で、<xref:System.Data.Linq.DataContext>クラスにはなど、呼び出すことのできるいくつかのメソッドが含まれています、<xref:System.Data.Linq.DataContext.SubmitChanges%2A>を送信するメソッドからのデータを更新する[!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]クラス、データベースにします。 作成することも追加<xref:System.Data.Linq.DataContext>ストアド プロシージャおよび関数にマップされるメソッド。 つまり、これらのカスタム メソッドを呼び出すと、<xref:System.Data.Linq.DataContext> メソッドのマップ先となっているデータベース内のストアド プロシージャまたは関数が実行されます。 メソッドを追加して任意のクラスを拡張するのと同じように、<xref:System.Data.Linq.DataContext> クラスに新しいメソッドを追加できます。 ただし、に関するディスカッションで<xref:System.Data.Linq.DataContext>メソッドのコンテキストで、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]は、<xref:System.Data.Linq.DataContext>ストアド プロシージャとは、説明されている関数にマップされるメソッド。  
  
## <a name="methods-pane"></a>メソッド ペイン  
 ストアド プロシージャおよび関数にマップされる <xref:System.Data.Linq.DataContext> メソッドは、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]のメソッド ペインに表示されます。 メソッド ペインは、ウィンドウの横に、**エンティティ**ウィンドウ (メインのデザイン画面)。 メソッド ペインには、すべて一覧表示<xref:System.Data.Linq.DataContext>メソッドを使用して作成した、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]します。 既定では、メソッド ペインは空です。ストアド プロシージャまたは関数からのドラッグ**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**上に、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]を作成する<xref:System.Data.Linq.DataContext>メソッド メソッド ペインを設定します。 詳細については、次を参照してください。[方法: ストアド プロシージャおよび関数 (O/r デザイナー) にマップされる DataContext の作成メソッド](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)します。  
  
> [!NOTE]
>  右クリックし、メソッド ペインを開いたり閉じたり、 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]  をクリックし、**メソッド ペインの非表示に**または**メソッド ペインの表示**、またはキーボード ショートカット CTRL + 1 を使用します。  
  
## <a name="two-types-of-datacontext-methods"></a>2 種類の DataContext メソッド  
 DataContext メソッドは、データベース内のストアド プロシージャおよび関数にマップされるメソッドです。 DataContext メソッドは、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]のメソッド ペインで作成および追加できます。 2 種類の区別がある<xref:System.Data.Linq.DataContext>メソッドはそうでないものと 1 つまたは複数の結果セットを返すもの。  
  
-   1 つ以上の結果セットを返す <xref:System.Data.Linq.DataContext> メソッド  
  
     この種類の <xref:System.Data.Linq.DataContext> メソッドは、アプリケーションでデータベース内のストアド プロシージャおよび関数を実行し、結果を返すことだけが必要な場合に作成します。 詳細については、次を参照してください。[方法: ストアド プロシージャおよび関数 (O/r デザイナー) にマップされる DataContext の作成メソッド](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)、System.Data.Linq.ISingleResult\<T >、および<xref:System.Data.Linq.IMultipleResults>します。  
  
-   結果セットを返さない <xref:System.Data.Linq.DataContext> メソッド (特定のエンティティ クラスの挿入、更新、削除など)  
  
     この種類の作成<xref:System.Data.Linq.DataContext>メソッド、アプリケーションがある既定値を使用する代わりにストアド プロシージャを実行する際に[!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]保存の動作は、エンティティ クラスとデータベース間でデータを変更します。 詳細については、次を参照してください。[方法: 更新、挿入、および削除 (O/r デザイナー) を実行するストアド プロシージャを割り当てる](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)します。  
  
## <a name="return-types-of-datacontext-methods"></a>DataContext メソッドの戻り値の型  
 ストアド プロシージャおよび関数からのドラッグと**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**上に、 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]、戻り値の型を生成された<xref:System.Data.Linq.DataContext>メソッドとは異なる項目をドロップする場所によって異なります。 作成、既存のエンティティ クラスに直接の項目をドロップする、<xref:System.Data.Linq.DataContext>エンティティ クラスの戻り値の型を持つメソッドは項目をドロップの空の領域、 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] (いずれかのウィンドウ) では、作成、<xref:System.Data.Linq.DataContext>を返すメソッド、型が自動的に生成されます。 作成される自動生成の型は、ストアド プロシージャ名または関数名に一致する名前と、そのストアド プロシージャまたは関数によって返される各フィールドにマップされるプロパティを持ちます。  
  
> [!NOTE]
>  <xref:System.Data.Linq.DataContext> メソッドをメソッド ペインに追加した後に、その戻り値の型を変更できます。 検査または戻り値の型を変更する、<xref:System.Data.Linq.DataContext>メソッドを選択し、検査、**戻り値の型**プロパティ、**プロパティ**ウィンドウ。 詳細については、次を参照してください。[方法: DataContext メソッド (O/r デザイナー) の戻り値の型を変更する](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)します。  
  
 データベースから O/R デザイナー画面にドラッグしたオブジェクトには、データベース内のオブジェクトの名前に基づいて自動的に名前が付けられます。 同じオブジェクトを複数回ドラッグすると、新しい名前の末尾に名前を区別する番号が付けられます。 データベース オブジェクト名にスペースや Visual Basic または C# でサポートされない文字が含まれている場合、そのスペースまたは無効な文字はアンダースコアに置き換えられます。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to Visual Studio での SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [ストアド プロシージャ](http://msdn.microsoft.com/library/4d23dd7a-a85f-44ff-a717-af7d0950c0fc)   
 [方法: ストアド プロシージャおよび関数 (O/R デザイナー) にマップされる DataContext メソッドの作成](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [方法: 更新、挿入、および削除 (O/R デザイナー) を実行するストアド プロシージャを割り当てる](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [チュートリアル: のカスタマイズ、挿入、更新、およびエンティティ クラスの動作を削除](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
 [チュートリアル: LINQ to SQL クラス (O/R デザイナー) を作成します。](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)

