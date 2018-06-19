---
title: '方法: O R デザイナーによって生成されたコードを拡張'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 73431c09a4e9054d30ccaef3dd1d74ac401c17e7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31921787"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>方法 : O/R デザイナーで生成されたコードを拡張する
[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]で生成されたコードは、デザイナー サーフェイスでエンティティ クラスやその他のオブジェクトに変更を加えた場合に再生成されます。 このコードの再生成により、通常、生成されたコードに追加したコードは、デザイナーがコードを再生成するときに上書きされます。 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]には、上書きされないコードを追加できる部分クラス ファイルの生成機能が用意されています。 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]で生成されたコードに独自のコードを追加する例の 1 つとして、LINQ to SQL (エンティティ) クラスへのデータ検証の追加があります。 詳細については、次を参照してください。[する方法: エンティティ クラスに検証を追加](../data-tools/how-to-add-validation-to-entity-classes.md)です。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="adding-code-to-an-entity-class"></a>エンティティ クラスへのコードの追加

#### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>部分クラスを作成し、エンティティ クラスにコードを追加するには

1.  開くか新しい LINQ to SQL クラス ファイルを作成 (**.dbml**ファイル) で、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]です。 (ダブルクリックして、 **.dbml**ファイル**ソリューション エクスプ ローラー**/**データベース エクスプ ローラー**)。

2.  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]、検証を追加しクラスを右クリックして**コードの表示**です。

     コード エディターが開き、選択したエンティティ クラスの部分クラスが表示されます。

3.  エンティティ クラスの部分クラス宣言内にコードを追加します。

## <a name="adding-code-to-a-datacontext"></a>DataContext へのコードの追加

#### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>部分クラスを作成し、DataContext にコードを追加するには

1.  開くか新しい LINQ to SQL クラス ファイルを作成 (**.dbml**ファイル) で、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]です。 (ダブルクリックして、 **.dbml**ファイル**ソリューション エクスプ ローラー**/**データベース エクスプ ローラー**)。

2.  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]デザイナーの空の領域を右クリックし、クリックして**コードの表示**です。

     コード エディターが開き、DataContext の部分クラスが表示されます。

3.  DataContext の部分クラス宣言内にコードを追加します。

## <a name="see-also"></a>関連項目

- [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [チュートリアル: LINQ to SQL クラス (O R デザイナー) を作成します。](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)