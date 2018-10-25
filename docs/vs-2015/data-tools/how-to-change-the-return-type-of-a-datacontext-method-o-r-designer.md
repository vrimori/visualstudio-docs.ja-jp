---
title: '方法: DataContext メソッド (O/R デザイナー) の戻り値の型の変更 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e4999c9fd273b78ff740e53c25bbe5a4b0a3017f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211745"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>方法: DataContext メソッド (O/R デザイナー) の戻り値の型を変更します。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
ストアド プロシージャまたは関数に基づいて作成された <xref:System.Data.Linq.DataContext> メソッドの戻り値の型は、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]でストアド プロシージャまたは関数をドロップした場所に応じて異なります。 既存のエンティティ クラスに項目を直接ドロップすると、そのエンティティ クラスを戻り値の型とする <xref:System.Data.Linq.DataContext> メソッドが作成されます (ストアド プロシージャまたは関数によって返されるデータのスキーマがエンティティ クラスの形状と一致する場合)。 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]の空の領域に項目をドロップすると、自動生成された型を返す <xref:System.Data.Linq.DataContext> メソッドが作成されます。 <xref:System.Data.Linq.DataContext> メソッドをメソッド ペインに追加した後に、その戻り値の型を変更できます。 検査または戻り値の型を変更する、<xref:System.Data.Linq.DataContext>メソッドを選択し、クリックして、**戻り値の型**プロパティ、**プロパティ**ウィンドウ。  
  
> [!NOTE]
>  元に戻すことはできません<xref:System.Data.Linq.DataContext>をエンティティ クラスに設定するを使用して、自動生成型を返す戻り値の型を持つメソッド、**プロパティ**ウィンドウ。 自動生成型を返すように <xref:System.Data.Linq.DataContext> メソッドを戻すには、元のデータベース オブジェクトをもう一度 O/R デザイナーにドラッグする必要があります。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>DataContext メソッドの戻り値の型を、自動生成型からエンティティ クラスに変更するには  
  
1.  メソッド ペインで <xref:System.Data.Linq.DataContext> メソッドを選択します。  
  
2.  選択**戻り値の型**で、**プロパティ**ウィンドウし、使用可能なエンティティ クラス、**戻り値の型**一覧。 一覧で目的のエンティティ クラスでない場合にそれを追加または作成、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]一覧に追加します。  
  
3.  .dbml ファイルを保存します。  
  
### <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>DataContext メソッドの戻り値の型を、エンティティ クラスから自動生成型に変更するには  
  
1.  メソッド ペインで <xref:System.Data.Linq.DataContext> メソッドを選択し、削除します。  
  
2.  データベース オブジェクトをドラッグして**サーバー エクスプ ローラー**/**データベース エクスプ ローラー** O/R デザイナーの空の領域にします。  
  
3.  .dbml ファイルを保存します。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to Visual Studio での SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)   
 [方法: ストアド プロシージャや関数にマップされる DataContext メソッドを作成する (O/R デザイナー)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)

