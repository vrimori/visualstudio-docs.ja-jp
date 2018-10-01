---
title: '方法: O/R デザイナーによって生成されたコードを拡張 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8fe770e52a1557d577ef2536177321deb04c0128
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539928"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>方法 : O/R デザイナーで生成されたコードを拡張する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: O/R デザイナーでのコード生成の拡張](https://docs.microsoft.com/visualstudio/data-tools/how-to-extend-code-generated-by-the-o-r-designer)します。  
  
  
[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]で生成されたコードは、デザイナー サーフェイスでエンティティ クラスやその他のオブジェクトに変更を加えた場合に再生成されます。 このコードの再生成により、通常、生成されたコードに追加したコードは、デザイナーがコードを再生成するときに上書きされます。 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]には、上書きされないコードを追加できる部分クラス ファイルの生成機能が用意されています。 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]で生成されたコードに独自のコードを追加する例の 1 つとして、LINQ to SQL (エンティティ) クラスへのデータ検証の追加があります。 詳しくは、次を参照してください。[方法: エンティティ クラスに検証を追加](../data-tools/how-to-add-validation-to-entity-classes.md)します。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="adding-code-to-an-entity-class"></a>エンティティ クラスへのコードの追加  
  
#### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>部分クラスを作成し、エンティティ クラスにコードを追加するには  
  
1.  開くか、新しい LINQ to SQL クラス ファイルの作成 (**.dbml**ファイル) で、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]します。 (ダブルクリックして、 **.dbml**ファイル**ソリューション エクスプ ローラー**/**データベース エクスプ ローラー**)。  
  
2.  [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]をクリックして検証を追加するクラスを右クリックして**コードの表示**します。  
  
     コード エディターが開き、選択したエンティティ クラスの部分クラスが表示されます。  
  
3.  エンティティ クラスの部分クラス宣言内にコードを追加します。  
  
## <a name="adding-code-to-a-datacontext"></a>DataContext へのコードの追加  
  
#### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>部分クラスを作成し、DataContext にコードを追加するには  
  
1.  開くか、新しい LINQ to SQL クラス ファイルの作成 (**.dbml**ファイル) で、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]します。 (ダブルクリックして、 **.dbml**ファイル**ソリューション エクスプ ローラー**/**データベース エクスプ ローラー**)。  
  
2.  [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]デザイナーの空の領域を右クリックし、クリックして**コードの表示**します。  
  
     コード エディターが開き、DataContext の部分クラスが表示されます。  
  
3.  DataContext の部分クラス宣言内にコードを追加します。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to Visual Studio での SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [チュートリアル: LINQ to SQL クラス (O/R デザイナー) を作成します。](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [チュートリアル: エンティティ クラスに検証を追加します。](http://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)

